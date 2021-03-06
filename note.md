# CompilerBook

## アドレス

CPUがメモリにアクセスするときは、メモリの何バイト目にアクセスしたいのかという情報を数値で指定するわけですが、その数値のことを「アドレス」といいます

- 「アドレス16から8バイトのデータを読む」 = バイトの配列のように見えているメモリの16バイト目から8バイト分のデータを読む
  - 「16番地から8バイトのデータを読む」も同じ意味

## プログラムカウンタ（PC）・インストラクションポインタ（IP）

現在実行中の命令のアドレスのこと

- プログラムカウンタを次の命令以外の場所に設定することを「ジャンプする」あるいは「分岐する」と表現する

## 機械語

CPUが実行するプログラムの形式

## レジスタ

CPU内の少数のデータ保存領域。レジスタはCPU内部に存在しているので、遅延なしにアクセスすることが可能。

IntelやAMDのプロセッサには、64ビット整数が保持できる領域が16個ある。

## 命令セットアーキテクチャ（instruction set architecture, ISA）

特定の機械語の命令の総称。

- Intelやその互換チップメーカーであるAMD: x86-64
- iPhoneやAndroid: ARM

## 逆アセンブル

lsコマンドを逆アセンブルしてみた結果。

```console
$ objdump -d /usr/bin/ls | head -10

/usr/bin/ls:     file format elf64-x86-64


Disassembly of section .init:

0000000000004000 <.init>:
    4000:       f3 0f 1e fa             endbr64 
    4004:       48 83 ec 08             sub    $0x8,%rsp
    4008:       48 8b 05 c9 ef 01 00    mov    0x1efc9(%rip),%rax        # 22fd8 <__gmon_start__>
```

## リターンアドレス

元々実行していたアドレスのこと。呼び出した関数が終了した後に、元々実行していた場所に戻っくる場所。


## スタックポインタ

スタックトップを保持している記憶領域のこと。スタックにデータを積むことを「プッシュ」、スタックに積まれたデータを取り出すことを「ポップ」という。

## トークン

プログラミング言語における単語。

## トークナイズする

文字列をトークン列に分割すること。

## 連結リスト

下記のデータ構造の日本語訳より、「連結リスト」の章を参考。

**SLList:単方向連結リスト** が使われている。

<https://sites.google.com/view/open-data-structures-ja>

## 左結合・右結合

左から計算しなければならない演算子のことを「左結合」の演算子、右から計算しなければならない演算子のことを「右結合」の演算子と

※ Cでは、代入の=を除いて、ほとんどの演算子は左結合

## 抽象構文木

カッコなどの冗長な要素を木の中に残さずになるべくコンパクトに表現した構文木のこと。

## BNF

- 終端記号: それ以上展開できない記号
- 非終端記号: 生成規則の左辺に来ていて展開できる記号

## EBNF

以下の記号を使って複雑なルールを完結に書くことができる。

| 書き方 |	意味 |
| --- |	--- |
| `A*` |	Aの0回以上の繰り返し |
| `A?` |	Aまたはε |
| `A \| B` |	AまたはB |
| `( ... )` |	グループ化 |

## スタックマシン

例: `2 * 3 + 4 * 5`

```
// 2*3
PUSH 2
PUSH 3
MUL

// 4*5
PUSH 4
PUSH 5
MUL

// 2*3 + 4*5
ADD
```

## 単項演算子（unary operator）

1つの項だけを取る演算子のこと。

## 2項演算子（binary operator）

2つの項をとる演算子のこと。

## フィードバックメモ

- 掛け算・割り算のところ
  - `strchr("+-*/()", *p)` のコード箇所がなさそう
  - `token = tokenize(user_input);` user_input は不要っぽい
