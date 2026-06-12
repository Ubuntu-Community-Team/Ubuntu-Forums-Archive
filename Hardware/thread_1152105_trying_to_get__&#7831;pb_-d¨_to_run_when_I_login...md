---
title: "trying to get  &#7831;pb -d¨ to run when I login...... thinkpad buttons"
date: 2009-05-07
forum: Hardware
---

### Post by setherd on 2009-05-07
I&#7743; trying to get the thinkpad buttons program to run at login.  right now I have to open a shell and type ¨sudo tpb-d¨ this is on a T43  how can I get it to run when someone logs in?  any help is appreciated!

---

### Post by Headbanger2510 on 2009-05-07
go to System-> Preferences -> Startup Applications and choose add then put the name you want to this app and in the line where command is written write:
gksu tpb-d

---

### Post by emeraldgirl08 on 2009-06-23
I'm on the T30 and will try this out!

---

### Post by emeraldgirl08 on 2009-06-23
Didn't work for me.

I looked on Thinkwiki and upon reading decided to F2+alt. I keyed in /etc/tpbrc to look at the xorg file. I don't know if I should add something to it and save or not.

Any ideas?

---

### Post by Headbanger2510 on 2009-09-05
You cann add > tpb -d to "/etc/rc.local" before the line "exit 0"

---

### Post by setherd on 2009-09-07
thanks. I added it but it doesn't run.
if I run sh /etc/rc.local after getting to my desktop it works. but I'm not sure why.

---

