# pis-bot

![Travis (.com)](https://img.shields.io/travis/com/Sam1370/pis-bot)
![GitHub](https://img.shields.io/github/license/Sam1370/pis-bot)

This is a support bot for the [Pterodactyl Installation Script Discord](https://pterodactyl-installer.se/discord), but feel free to adapt it for your own uses. It is a simple bot that responds to commands, keywords or parsed image text and gives a response.

## Requirements

Nodejs v12.0.0 or newer is recommended. You can install that using:
(If you can't use Nodejs 12 or newer you can compile with a lower target version)

```bash
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs
```

## Installation

```bash
git clone https://github.com/Sam1370/pis-bot.git
```

```bash
npm i --production
```

## Configuration

Triggers are defined in `dist/config/triggers.js`.
For all the other things you will be prompted automatically.

## Running

One-time start: `npm start`

Encapsulated in while-true loop: `start-bot.sh`

As a system service: `install-service.sh && systemctl daemon-reload` then when you want to start: `systemctl start pis-bot`

## Staying updated

To stay updated with the latest versions, you can run a cronjob to automatically pull the latest version from the GitHub. Run `crontab -e` and add this at the end of the file:

```bash
*/1 * * * * su -s /bin/sh root -c 'cd /root/pis-bot/ && /usr/bin/git update-index --assume-unchanged auth.json && /usr/bin/git pull origin master'
```

If you are using the system service and want to restart it, use this instead:

```
*/1 * * * * su -s /bin/sh root -c 'cd /root/pis-bot/ && /usr/bin/git update-index --assume-unchanged auth.json && /usr/bin/git pull origin master && systemctl restart pis-bot'
```
