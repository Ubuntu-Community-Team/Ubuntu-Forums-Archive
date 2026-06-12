---
title: "Having 2 4CE-SDI cards installed ports detected randomly"
date: 2013-04-03
forum: Hardware
---

### Post by yoelson on 2013-04-03
[COLOR=#444444][FONT=Lucida Grande]Hi guys,[/FONT][/COLOR]

[COLOR=#444444][FONT=Lucida Grande]I have two 4CE-SDI (Quad SDI) cards installed ([/FONT][/COLOR]Blackmagic Design Desktop Video 9.5 - Driver and Utilities[COLOR=#444444][FONT=Lucida Grande]) on my Ubuntu server - Ubuntu 12.04.1 LTS[/FONT][/COLOR]
[COLOR=#444444][FONT=Lucida Grande]The cards pci slots are set by 20-blackmagic.rules persistent file.[/FONT][/COLOR]
[COLOR=#444444][FONT=Lucida Grande]The 20-blackmagic.rules are as follows:[/FONT][/COLOR]
[COLOR=#444444][FONT=Lucida Grande]KERNEL=="blackmagic[0-9]*", SYMLINK+="blackmagic/card%n", MODE="0666", RUN+="/usr/lib/blackmagic/BlackmagicPreferencesStartup %n 99", OPTIONS="last_rule"[/FONT][/COLOR]
[COLOR=#444444][FONT=Lucida Grande]KERNEL=="blackmagic_serial[0-9]*", SYMLINK+="blackmagic/serial%n", MODE="0666", OPTIONS="last_rule"[/FONT][/COLOR]

[COLOR=#444444][FONT=Lucida Grande]After rebooting the server the cards flip between card0 and card1 which confuses the application. When trying to access port 0 (card0) could be port 7 or port 7 could be port 0.[/FONT][/COLOR]
[COLOR=#444444][FONT=Lucida Grande]Is there any unique BM slot identifier I can use to set the persistent names for each slot manually? Something like ATTR{unique}=="xyz"?[/FONT][/COLOR]

[COLOR=#444444][FONT=Lucida Grande]Thanks in advance.[/FONT][/COLOR]

---

