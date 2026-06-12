---
title: "Keyboard Layout Settings won't stick after reboot"
date: 2009-11-10
forum: Hardware
---

### Post by taamir on 2009-11-10
I run Ubuntu 9.10 and I got the problem:
Keyboard Layout Settings won't stick after reboot

It was solved in:
[http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap](http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap)

however this solution doesn't work for me, I dont know why, please help..
when i type in the Terminal:

```
setxkbmap -display
```

I get the following message: 

```
No X display specified on the command line
```

---

### Post by Dale Gerdemann on 2009-11-10
I've had a similar problem ever since the upgrade to 9.10. I go to Preferences->Keyboard->Layout and delete the unwanted "USA Alternative international (former us_intl)" leaving the two layouts that I do want. But after rebooting, the pretty worthless "USA Alternative ..." always comes back. I tried the trick with setxkbmap, but it didn't help. This is very irritating, making Ubuntu less attractive for international users.


> **taamir said:**
> I run Ubuntu 9.10 and I got the problem:
Keyboard Layout Settings won't stick after reboot

It was solved in:
[http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap](http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap)

however this solution doesn't work for me, I dont know why, please help..
when i type in the Terminal:

```
setxkbmap -display
```

I get the following message: 

```
No X display specified on the command line
```

---

### Post by taamir on 2009-11-11
my problem is something like that I need both Hebrew and English layouts, but when I restart only one of them appear, when i push the Reset to Defaults button both of them appear. I then Apply System-Wide but it wont stick past the next restart. 
PLEASE HELP

---

### Post by yourlonglostpal on 2009-11-11
I'm not sure about taamir's problem but I think I can help with Dale Gerdemann's.  Try Preferences > Keyboard>Layout and look in the white box headed Layout. If one of the options in here is USA, click on it and then click Remove. On thinking about it,  taamir's problem may be similar.

---

### Post by taamir on 2009-11-11
Unfortunately this does not solve my problem.

---

### Post by taamir on 2009-11-14
Bump.
Please help me with this problem...

---

### Post by taamir on 2009-11-18
Sorry this is the last time I bump it..
But this problem is really severe however only people how use more than one language can relate to it.
Please tell me, what can i do to solve it?

---

### Post by taamir on 2009-11-20
Is there a bug report about it? 
i found this line in the help section-
"Click Reset to Defaults to restore all keyboard layout settings to their initial state for your system and locale."
and as i said after i Click Reset to Defaults everything works alright its just somehow doesn't happen on startup..

maybe any one can help me create a script to Reset to Defaults that i can add to startup programs ??

---

### Post by 666porcondissaum on 2009-11-25
same here...

---

### Post by mie_ite on 2009-12-12
Hi. I encountered this same problem. Even when deleting the US keyboard layout and applying Finnish layout system wide it would still revert back to US on every boot.

However I figured a way around this. Seeing as 'env | grep GDM' returned thusly

> 
hpr@gargamel:~$ env | grep GDM
GDM_KEYBOARD_LAYOUT=en
GDM_LANG=en_US.UTF-8
GDMSESSION=gnome


it seems that the keyboard setting from System/Preferences/Keyboard/Layout didn't change gdm's keyboard layout. So, I added this to .bashrc:

> 
set GDM_KEYBOARD_LAYOUT fi


And voila, now my keyboard layout list doesn't revert back to US keyboard on start up even though it is still listed in the layouts.

---

