---
title: "Firefox 3.5 Update"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by feb3 on 2009-07-09
Received the FF 3.5 update last night but not sure that it has actually updated - version number is still 3.0.11.
Please could someone tell me if I have to do anything to install it properly or will it occur automatically at a later date?
(Am a complete novice with Linux).

---

### Post by aysiu on 2009-07-09
Close all instances of Firefox.

Then, does Alt-F2 ```
firefox-3.5
``` still launch 3.0.11?

---

### Post by caco on 2009-07-09
Run ls -l `which firefox` in a terminal to determine if the firefox link is actually pointing to the firefox 3.5, if not correct it.

[[IMG]http://brainstorm.ubuntu.com/idea/20470/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20470/)

---

### Post by feb3 on 2009-07-09
Thank you for advice. Have checked in the terminal and I am given two options - FF3 and FF3.5. 
I select the latter (option 2), press Enter and nothing happens - still on the old version.
Next I tried the Alt/F2 combination and run firefox-3.5 and it came up with Shiretoko which is Firefox 3.5. I'm a bit puzzled now. 
Is there anthing else that I should do please?

---

### Post by kiwimenace on 2009-07-09
yer what is this sheritoko and why isnt it just firefox? the blue circle is not familiar to me.

---

### Post by feb3 on 2009-07-09
Just to add that I have done some more research and discovered that  Shiretoko is Firefox 3.5. It runs alongside 3.0, which is not removed. As I understand it FF 3.5 will not be rebranded as Firefox until the next Ubuntu version.Thanks to aysiu for the clue.

---

### Post by aysiu on 2009-07-09
I don't think *ls -l 'which firefox'* does anything. Maybe I'm not inputting the command correctly.

[/I]Running ```
ls -l /usr/bin/firefox
``` should tell you which Firefox (3.0 or 3.5) the Firefox launcher is currently pointing to, though.

---

### Post by caco on 2009-07-13
Sorry I'm guessing you ran 

ls -l 'which firefox'

which resulted in ls: cannot access which firefox: No such file or directory
but the command to run was

ls -l `which firefox`

which should display something similar to 
lrwxrwxrwx 1 root root 11 2009-07-01 11:09 /usr/bin/firefox -> firefox-3.5

Anyway ` is a back tick not '

The idea is that you need to link firefox to the firefox 3.5 not firefox 3.0
;)

[[IMG]http://brainstorm.ubuntu.com/idea/20470/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/20470/)

---

### Post by JohnLau on 2009-07-13
Are you sure you have recieved it as an update? It won't happen if you are using 9.04. [Click here to install firefox 3.5 (or double-check)]("apt:firefox-3.5") You can [follow my guide]("http://compustorm.no-ip.org/2009/07/howto-install-firefox-3-5-on-ubuntu-jaunty/") if you want to set it as your default browser
John

---

