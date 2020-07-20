## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|integer|null: false, foreign_key: true|
|group|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false,unique: true|
|group_user|string|null: false,unique: true|
### Association
- has_many :messages
- has_many :groups, through: :group_users


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|integer|null: false, foreign_key: true|
### Association
has_many :groups_users
has_many :users, through: groups_users
has_many :messages


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user