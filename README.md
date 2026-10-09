# ClickUp Personal Dashboard Preview 配布物

このリポジトリは、Windows用デスクトップアプリ「ClickUp Personal Dashboard Preview」の**配布物（インストーラーと更新用メタデータ）だけ**を置く場所です。

## 最初にお読みください

- **社内向けの未署名Preview**です。コード署名はしていません。
- **無保証**です。現状のまま提供し、動作・適合性・損害について一切保証しません。
- **再配布できません。** ライセンスは付与していません（All rights reserved）。このリポジトリの内容を第三者へ再配布・転載しないでください。
- **ソースコードは非公開**です。このリポジトリにはソースコード・ビルド手順・設定は含まれません。
- このリポジトリは**アプリ内更新の配布元**です。インストール済みのアプリ（0.1.8-preview.1以降）は、このリポジトリのReleasesから新しい版を確認・取得します。
- Issue・Pull Requestは受け付けていません。問い合わせは社内の配布担当者へお願いします。

## 配布物

各Releaseには次のファイルがあります（`<版>` は例: `0.1.8-preview.1`）。

| ファイル | 内容 |
| --- | --- |
| `ClickUp-Personal-Dashboard-Preview-Setup-<版>-x64.exe` | Windows x64用インストーラー（ユーザー単位・未署名） |
| `ClickUp-Personal-Dashboard-Preview-Setup-<版>-x64.exe.blockmap` | アプリ内更新用の差分情報 |
| `latest.yml` | アプリ内更新用のメタデータ（版・SHA-512・サイズ） |
| `ClickUp-Personal-Dashboard-Preview-Setup-<版>-x64.exe.sha256` | インストーラーのSHA256 |
| `build-info.json` | ビルド元の版・コミット識別子 |

## ダウンロードしたインストーラーの確認（SHA256）

PowerShellで次を実行し、表示された値が同じReleaseの `.sha256` ファイルの値と一致することを確認してください。

```powershell
Get-FileHash -Algorithm SHA256 .\ClickUp-Personal-Dashboard-Preview-Setup-<版>-x64.exe
Get-Content .\ClickUp-Personal-Dashboard-Preview-Setup-<版>-x64.exe.sha256
```

一致しない場合は実行せず、ファイルを削除して配布担当者へ連絡してください。SHA256の一致は破損や取り違えの確認であり、発行者の証明ではありません。

## 未署名のための警告（SmartScreen）

署名がないため、実行時に「WindowsによってPCが保護されました」と表示されることがあります。このリポジトリのReleaseから取得し、上記のSHA256が一致した場合に限り、「詳細情報」→「実行」で続行してください。セキュリティ製品や保護機能を無効化しないでください。

## アプリ内更新

- 0.1.8-preview.1以降のアプリは、起動後と一定間隔でこのリポジトリのReleasesを確認し、新しい版があれば取得します。
- 更新が適用されるのは、アプリの「終了して更新」を押した場合だけです。未保存の入力や保存中の操作がある場合は通常の終了確認が先に表示されます。
- 取得したインストーラーは `latest.yml` のSHA-512と照合されます（発行者の証明ではありません）。
- 更新後のアプリは自動では起動しません。スタートメニューから起動してください。
- 0.1.7-preview.1以前の版にはアプリ内更新がありません。0.1.8-preview.1へは手動で更新してください。
