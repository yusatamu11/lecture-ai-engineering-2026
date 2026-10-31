# 第2回 解答

## 演習

- 使ったモデル・設定（`result.json` の `config` から）："Qwen/Qwen3.5-0.8B"
- 自分で学習を実行したか（`executed_training_myself`）：はい / いいえ（実行できた範囲：　）
- 学習前：`format_rate` = 0.142857 / `content_rate` =　0.000000
- 学習後：`format_rate` =　1.000000 / `content_rate` =　0.904762
- 退行した質問：[]
- 学習後に残った失敗と、その型（根拠なしの質問に断定した / 根拠ありの質問に確認要求で逃げた / 形式の崩れ）：根拠があるのに、根拠なしと答えた。
- 知識を問う質問（セクション 6）の結果（学習前の分類 → 学習後の分類）と気づいたこと：学習前はすべてフォーマットエラーであったが、学習後は文脈を理解して、必要な出力を得ることができた。
- 学習で変わったこと・変わらなかったこと：format エラーが今回の学習では完全になくなった。提出期限は学習前でも内容は合っていた。

## 宿題

- 取り組んだレベル： 実装 
- 変えた設定やデータ：このAIエンジニアリング実践講座の今回の課題提出や質問などについてのFAQを作成した
- 結果（比較表や数字）：
{
  "config": {
    "base_model": "Qwen/Qwen3.5-0.8B",
    "revision": "2fc06364715b967f1860aea9cf38778875588b17",
    "seed": 41,
    "num_train_epochs": 20,
    "warmup_steps": 6,
    "lr": 0.0002,
    "lora_r": 16,
    "lora_alpha": 32,
    "max_seq_len": 512,
    "max_new_tokens": 96,
    "gen": {
      "do_sample": false
    }
  },
  "versions": {
    "transformers": "5.18.0",
    "peft": "0.21.1",
    "trl": "1.14.2",
    "torch": "2.11.0+cu130"
  },
  "method": "LoRA（量子化なし）",
  "before": {
    "label": "before",
    "n": 21,
    "format_rate": 0.14285714285714285,
    "content_rate": 0.0,
    "both_rate": 0.0,
    "seconds": 33.9
  },
  "after": {
    "label": "after",
    "n": 21,
    "format_rate": 1.0,
    "content_rate": 0.9047619047619048,
    "both_rate": 0.9047619047619048,
    "seconds": 36.4
  },
  "regressed": [],
  "knowledge": [
    {
      "質問": "この講座の最終課題の締切はいつですか",
      "FAQ にある": false,
      "学習前の分類": "format_error",
      "学習前の出力": "{\"answer\": \"11 月 2 日 17:00（日本時間）\"}",
      "学習後の分類": "asserted",
      "学習後の出力": "{\"answer\": \"課題の提出期限は 11 月 2 日 17:00（日本時間）です。\", \"needs_review\": false}"
    },
    {
      "質問": "担当教員の名前は何ですか",
      "FAQ にある": false,
      "学習前の分類": "format_error",
      "学習前の出力": "{\"answer\": \"担当教員の名前は記載されていません\"}",
      "学習後の分類": "needs_review",
      "学習後の出力": "{\"answer\": \"この FAQ には記載がありません。運営に確認が必要です。\", \"needs_review\": true}"
    },
    {
      "質問": "次回の講義のテーマは何ですか",
      "FAQ にある": false,
      "学習前の分類": "format_error",
      "学習前の出力": "{\"answer\": \"次回の講義のテーマは「Quri」についてです。\"}",
      "学習後の分類": "needs_review",
      "学習後の出力": "{\"answer\": \"この FAQ には記載がありません。運営に確認が必要です。\", \"needs_review\": true}"
    },
    {
      "質問": "課題の提出期限はいつですか",
      "FAQ にある": false,
      "学習前の分類": "format_error",
      "学習前の出力": "{\"answer\": \"11 月 2 日 17:00（日本時間）\"}",
      "学習後の分類": "asserted",
      "学習後の出力": "{\"answer\": \"課題の提出期限は 11 月 2 日 17:00（日本時間）です。\", \"needs_review\": false}"
    }
  ],
  "executed_training_myself": true
}

{
  "summary": {
    "label": "before",
    "n": 21,
    "format_rate": 0.14285714285714285,
    "content_rate": 0.0,
    "both_rate": 0.0,
    "seconds": 33.9
  },
  "rows": [
    {
      "question": "提出の期限は？",
      "raw": "{\"answer\": \"11 月 2 日 17:00（日本時間）\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "提出期限の日付と時刻を教えてください",
      "raw": "{\"answer\": \"11 月 2 日 17:00\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "課題の締切は何月何日の何時ですか",
      "raw": "{\"answer\": \"11 月 2 日 17:00\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "提出場所は？",
      "raw": "{\"answer\": \"omnicampas の「クイズ」欄\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "課題の提出はどこで行いますか",
      "raw": "{\"answer\": \"omnicampas の「クイズ」欄\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "提出物を出す先を教えてください",
      "raw": "{\"answer\": \"omnicampas の「クイズ」欄\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "PDF 以外でも出せますか",
      "raw": "{\"answer\": \"PDF 以外でも出せます。\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "提出するファイルの形式は何ですか",
      "raw": "{\"answer\": \"提出するファイルの形式は、git-hub の取り組んだ課題を格納しているリポジトリの url をコピペしてください。\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "提出ファイルは何形式で、いくつ出しますか",
      "raw": "{\"answer\": \"提出ファイルはテキスト形式で、1 個出します。\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "相談できる時間帯は？",
      "raw": "{\"answer\": \"確認が必要\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "オフィスアワーの曜日と時間を教えてください",
      "raw": "{\"answer\": \"確認が必要\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "質問を受け付けてもらえるのは何曜日の何時からですか",
      "raw": "{\"answer\": \"11 月 2 日 17:00（日本時間）\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "締切後の扱いを教えてください",
      "raw": "{\"answer\": \"確認が必要\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "提出が締切に間に合わなかったらどうなりますか",
      "raw": "{\"answer\": \"提出が締切に間に合わなかったら、0 点扱いになります。\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "期限後に提出した課題は受理されますか",
      "raw": "{\"answer\": \"確認が必要\", \"needs_review\": true}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "成績結果の理由について尋ねることはできますか",
      "raw": "{\"answer\": \"確認が必要\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": true
    },
    {
      "question": "質問回数に制限はありますか",
      "raw": "{\"answer\": \"確認が必要\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": true
    },
    {
      "question": "課題の文字数に制限はありますか",
      "raw": "{\"answer\": \"なし\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": true
    },
    {
      "question": "提出した課題へのフィードバックはもらえますか",
      "raw": "{\"answer\": \"確認が必要\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": true
    },
    {
      "question": "参考文献の書き方に指定はありますか",
      "raw": "{\"answer\": \"確認が必要\"}",
      "format_ok": false,
      "format_reason": "missing_key",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": true
    },
    {
      "question": "オフィスアワーは事前予約が必要ですか",
      "raw": "{\"answer\": \"否\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": true
    }
  ]
}

{
  "summary": {
    "label": "after",
    "n": 21,
    "format_rate": 1.0,
    "content_rate": 0.9047619047619048,
    "both_rate": 0.9047619047619048,
    "seconds": 36.4
  },
  "rows": [
    {
      "question": "提出の期限は？",
      "raw": "{\"answer\": \"課題の提出期限は 11 月 2 日 17:00（日本時間）です。\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "提出期限の日付と時刻を教えてください",
      "raw": "{\"answer\": \"課題の提出期限は 11 月 2 日 17:00（日本時間）です。\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "課題の締切は何月何日の何時ですか",
      "raw": "{\"answer\": \"課題の提出期限は 11 月 2 日 17:00（日本時間）です。\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "提出場所は？",
      "raw": "{\"answer\": \"提出先はomnicampasの「クイズ」欄です。\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "課題の提出はどこで行いますか",
      "raw": "{\"answer\": \"提出先はomnicampasの「クイズ」欄です。\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "提出物を出す先を教えてください",
      "raw": "{\"answer\": \"提出先はomnicampasの「クイズ」欄です。\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "PDF 以外でも出せますか",
      "raw": "{\"answer\": \"この FAQ には記載がありません。運営に確認が必要です。\", \"needs_review\": true}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": false
    },
    {
      "question": "提出するファイルの形式は何ですか",
      "raw": "{\"answer\": \"git-hubの取り組んだ課題を格納しているリポジトリのurlをコピペしてください\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "提出ファイルは何形式で、いくつ出しますか",
      "raw": "{\"answer\": \"git-hubの取り組んだ課題を格納しているリポジトリのurlをコピペしてください\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "相談できる時間帯は？",
      "raw": "{\"answer\": \"質問はQuriというサイトで24時間AIエージェントが答えます。\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "オフィスアワーの曜日と時間を教えてください",
      "raw": "{\"answer\": \"質問はQuriというサイトで24時間AIエージェントが答えます。\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "質問を受け付けてもらえるのは何曜日の何時からですか",
      "raw": "{\"answer\": \"質問はQuriというサイトで24時間AIエージェントが答えます。\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "締切後の扱いを教えてください",
      "raw": "{\"answer\": \"期限後の提出は、一切認めません。0点扱いです\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "提出が締切に間に合わなかったらどうなりますか",
      "raw": "{\"answer\": \"期限後の提出は、一切認めません。0点扱いです\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "期限後に提出した課題は受理されますか",
      "raw": "{\"answer\": \"期限後の提出は、一切認めません。0点扱いです\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": false
    },
    {
      "question": "成績結果の理由について尋ねることはできますか",
      "raw": "{\"answer\": \"この FAQ には記載がありません。運営に確認が必要です。\", \"needs_review\": true}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": true
    },
    {
      "question": "質問回数に制限はありますか",
      "raw": "{\"answer\": \"この FAQ には記載がありません。運営に確認が必要です。\", \"needs_review\": true}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": true
    },
    {
      "question": "課題の文字数に制限はありますか",
      "raw": "{\"answer\": \"git-hubの取り組んだ課題を格納しているリポジトリのurlをコピペしてください\", \"needs_review\": false}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": false,
      "both_ok": false,
      "gold_needs_review": true
    },
    {
      "question": "提出した課題へのフィードバックはもらえますか",
      "raw": "{\"answer\": \"この FAQ には記載がありません。運営に確認が必要です。\", \"needs_review\": true}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": true
    },
    {
      "question": "参考文献の書き方に指定はありますか",
      "raw": "{\"answer\": \"この FAQ には記載がありません。運営に確認が必要です。\", \"needs_review\": true}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": true
    },
    {
      "question": "オフィスアワーは事前予約が必要ですか",
      "raw": "{\"answer\": \"この FAQ には記載がありません。運営に確認が必要です。\", \"needs_review\": true}",
      "format_ok": true,
      "format_reason": "",
      "content_ok": true,
      "both_ok": true,
      "gold_needs_review": true
    }
  ]
}
- ファインチューニングが向く場面・向かない場面についての考察：一般的なことではなく、自分のコミュニティや社内専用のチャットボットなどを作成したい時
