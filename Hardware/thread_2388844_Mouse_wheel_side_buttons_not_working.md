---
title: "Mouse wheel side buttons not working"
date: 2018-04-08
forum: Hardware
---

### Post by LastStarDust on 2018-04-08
[COLOR=#111111][FONT=Ubuntu]I am trying to get the side buttons of the wheel of my mouse (Logitech Bluetooth mouse V470) to work in Ubuntu 17.10. It used to work on Ubuntu 16.04 under imwheel (on another machine).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is my current configuration:[/FONT][/COLOR]
```
$ cat .imwheelrc 
".*" 
None, Left, Alt_L|Left 
None, Right, Alt_L|Right

```
```
$ cat /etc/X11/imwheel/startup.conf
IMWHEEL_START=0
IMWHEEL_PARAMS='-b "6 7"'
```
[COLOR=#111111][FONT=Ubuntu]What is wrong with it?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you[/FONT][/COLOR]

---

### Post by LastStarDust on 2018-04-09
[COLOR=#111111][FONT=Ubuntu]I solved by following [this procedure]("https://askubuntu.com/questions/236529/binding-back-forward-to-mouse-buttons?rq=1").[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Still would like to know why imwheel doesn't work...[/FONT][/COLOR]

---

