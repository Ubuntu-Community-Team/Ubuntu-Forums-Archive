---
title: "Vx Revolution installed but Btnx Loads new config"
date: 2009-07-24
forum: Hardware
---

### Post by Foxdelta-mods on 2009-07-24
After a long nite i finally got my VX revolution to work. But now i have a different problem. I use BTNX for my mousebuttons and i have 12 of them. in the Tut that i read the guy said download the attachment en rename it to .Xbindkeyrc but there was no attachment. So i just opened text editor copy pasted this :
 
[FONT=Courier New]"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""[/FONT]
[FONT=Courier New]m:0x0 + b:8[/FONT]
[FONT=Courier New]"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""[/FONT]
[FONT=Courier New]m:0x0 + b:9[/FONT]
[FONT=Courier New]"/usr/bin/xvkbd -xsendevent -text "\C+""[/FONT]
[FONT=Courier New]m:0x0 + b:13[/FONT]
[FONT=Courier New]"/usr/bin/xvkbd -xsendevent -text "\C-""[/FONT]
[FONT=Courier New]m:0x0 + b:14[/FONT]

[FONT=Courier New]And renamed it. [/FONT]
[FONT=Courier New]I made sure it would boot up by opening System>Preferences>Session and i added "xbindkey" as a new command to run at boot.[/FONT]

[FONT=Courier New]But when i load Ubuntu (jaunty jackalope) and i go to BTNX i has created a new Config. And every time i reboot it makes a new one. [/FONT]
[FONT=Courier New]So [/FONT]
[FONT=Courier New]Old_config[/FONT]
[FONT=Courier New]Old_config1[/FONT]
[FONT=Courier New]Old_config2[/FONT]

[FONT=Courier New]And so on. Anybody an idea ? [/FONT]

[FONT=Courier New]Ps sorry for my sometimes bad english. Im a dutch man ;)[/FONT]

---

