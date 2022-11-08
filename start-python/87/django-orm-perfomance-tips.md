---
theme: "night"
transition: "slide"
slideNumber: false
title: "production-freeze-lt"
output: revealjs::revealjs_presentation
customTheme: my-theme
---


## Django ORM パフォーマンスTips

LAPRAS, Inc. 増川武志  
@takeaship

---

### 自己紹介
- LAPRAS株式会社(2022/01~)
    - Djangoアプリケーション(LAPRAS)開発
    - データアナリスト
- 医療者向けプロトタイピングスクール「もいせん」の講師
- Windows, WSL, VSCode, NeoVim
- Nizキーボード
- 前職でAzure, C#, .Netをやっていた名残で、MS系への親しみが深い

---

## はじめに

--

### 話すこと
- よくある問題のあるクエリの類型とその解決策
- 問題のあるクエリの見つけ方
- Django ORMの限界

--

### 話さないこと
- DBのインデックス作成
- DBのチューニング
- DB固有のTips

--

### こんな人に役立つかも

- Pythonは書けて、これからDjangoで開発を始める人
- Djangoで開発をしていて、ORMが裏でしていることを詳しく知らない人

ORMにある程度精通している人には、物足りない内容かも。

---

## ORMの超基礎的な解説

## ORMの問題のあるクエリの類型
- DBとのやりとりの回数が無駄に多い
- DBから取得するデータ量が無駄に多い
- 発行されるSQLが重い
- モデルへの変換コストが重い

## DBとのやりとりの回数が多い
### N+1問題
- select_relatedで回避する
- prefetch_relatedで回避する
- annotateで回避する

### N+1は知らないうちに紛れ込む
みんな悪いのはわかっているけど、開発していると知らないうちに
気づける仕組みを作っておくのが大切

## DBから取得するデータ量が多い
### valuesで列を絞り込む
### countを使う


## 発行されるSQLが重い
### countではなくexistsを使う
### JOINするときの注意

## モデルへの変換コストが重い

## 可読性とパフォーマンスのジレンマ


## 生SQLを書くべき場面

## Django ORMの限界