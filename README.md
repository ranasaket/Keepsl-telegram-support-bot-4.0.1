# Keepsl-telegram-support-bot-4.0.1
<h3>Features:</h3>
When a user sends a message to the support chat it will create a ticket which will be forwarded to the staff group. Any admin in the staff group may answer that ticket by just replying to it. Salutation is added automatically. Photos will be forwared too.

<b>Currently the support chat offers these commands (staff commands):</b>

/open - lists all open tickets (messages where noone has replied yet)<br>
/close - close a ticket manually (in case someone writes 'thank you')<br>
/id - returns your telegram id and the group chat id (1234567 -1234567890)<br>
/ban - ban a person from writing to your chat<br>

<b>User commands:</b>

/start - tells the user how to use this bot<br>
/help - an overview over the commands or some explanation for the user<br>
/faq - shows the FAQ<br>

<b>Features:</b>

* File forwarding from and to user
* Database for handling open and closed tickets
* Restrict users
* Simple anti spam system
* Send tickets to different staff groups
* Private reply to user
* Anonymize users
* Auto reply based on keywords [beta]
* Web chat

1. To use the Telegram Bot API, you first have to get a bot account by chatting with BotFather. Write @botfather the /newbot command to create a bot. 
Then follow the process and copy the token you get at the end of the process. B
otFather will give you a token, something like 123456789:AbCdfGhIJKlmNoQQRsTUVwxyZ.

2. Create a group
Create a new group by opening the sidebar in Telegram then clicking on New Group.

3. Add the bot
After the group is created add the bot you created in the last step to it. Once added, click on the group name and you should see the group members. Long tap or right-click on the bot and make it an admin.

4. Get the group ID
To get the group ID you can add @bostrot_bot to your group and type /id. It should return two IDs. The first one is your USER ID, the second the GROUP ID. Remember both of them.

NOTE: If you get the group ID BEFORE adding another admin to your staff group keep in mind that you need to get the ID again with /id as it changes when a second admin is added. (Only one time)

5. Download and cd
Get the latest stable version of the bot from the releases page, e.g. with:

get https://github.com/bostrot/telegram-support-bot/archive/refs/tags/v4.0.1.zip
unzip v4.0.1.zip
cd telegram-support-bot-4.0.1

6. Edit config.yaml
For v2 or lower: Rename the config-sample.ts file in the config folder to config.ts.

For v3 and above: Rename the config-sample.yaml file in the config folder to config.yaml.

Now fill in the TOKEN, USER ID, GROUP ID:

bot_token: "TOKEN"
staffchat_id: "GROUP_ID"
owner_id: "USER:ID"
This should be the basic configuration. You can adjust the other settings depending on your needs.

<b>Installation</b>
If you want to deploy this with Docker you can directly go to the Docker section.

Install NodeJS 14.x using Debian, as root (for Ubuntu and others check out this):

curl -fsSL https://deb.nodesource.com/setup_lts.x | bash -
apt-get install -y nodejs
Install build-essential

apt-get install -y build-essential
Install npm dependencies

npm i
To run the bot in the background use pm2

pm2 start "npm run dev" --name bostrot
Docker
You can also run the bot with docker:

docker-compose:

docker-compose up -d
or without docker-compose:

docker build -t bostrot/telegram-support-bot:latest .
docker run bostrot/telegram-support-bot:latest -v /path/to/config_dir:/bot/config
Prebuild docker containers are also available for stable versions and the master branch. It is recommend to use the latest release instead of master.

e.g.

docker run bostrot/telegram-support-bot:v4.0.1 -v /path/to/config_dir:/bot/config
