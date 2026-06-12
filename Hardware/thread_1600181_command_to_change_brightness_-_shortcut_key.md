---
title: "command to change brightness - shortcut key"
date: 2010-10-18
forum: Hardware
---

### Post by lesmunchiz on 2010-10-18
[SIZE=4][FONT=Comic Sans MS]hi, I just got my brightness settings working with a workaround using a sudo command in the terminal witch go's like this[/FONT][/SIZE][FONT=Comic Sans MS][SIZE=3] 

  [/SIZE][/FONT]   [FONT=Comic Sans MS][SIZE=3]sudo setpci -s 00:02.0 F4.B=70[/SIZE][/FONT]
 
[SIZE=4][FONT=Comic Sans MS]I change the setting by changing the value after B= to the intensity I want from scale 0 to 100 

thats a great workaround but I'd like to add a shortcut key with the fn key on my keyboard but when I go in system - preferences - keyboard shortcut and click add it says to type the command but the command is a sudo so I'd need a password to make it work ... but I can't right a password from a shortcut key 

So I was wondering if there would be a command that I could use instead of the sudo or if I could mod that command to make it root always 

if anyone have any idea's I'm open to trying them 

ThX 
[/FONT][/SIZE]

---

### Post by KillYou on 2010-12-12
if you'd like to share your password with any one you could do

```
[SIZE=2]echo PASSWORD | sudo -S [/SIZE][FONT=Arial][SIZE=2]setpci -s 00:02.0 F4.B=70[/SIZE][/FONT]
```

---

