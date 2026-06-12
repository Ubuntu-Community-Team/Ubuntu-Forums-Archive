---
title: "Configuring X server"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by ollijav on 2006-02-02
I installed ubuntu but something went wrong with the graphic interface.
After booting I get a message telling thet the X server is disabled and that I should restart GDM when it is configured correctly.

How to configure it? And what is GDM and how to restart it?

My graphics card is:
ET6000	manuf.:Tseng Labs Inc	driver:Card:ET6000(generic)   muisti 2 MHz

I am quite new to Ubuntu and would appreciate help!

---

### Post by invalid on 2006-02-02
```
sudo dpkg-reconfigure xserver-xorg
```
then```
sudo gdm
```

---

### Post by ollijav on 2006-02-02
Thanks! It worked!

---

### Post by jindosept on 2007-09-30
> **invalid said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```
then```
sudo gdm
```

I have the same problem with my X server.  when I typed that in the terminal I am going through the process of reconfiguring my graphical interface.  However, when I got to the part about which color bit I want and I chose 24, I'm asked to backup my files in /etc/X11/xorg.conf.20070930101749

I can't proceed from this step of re-configuring without typing something in the terminal which just popped up.  I assume I need to back my configuration file because that is what it is telling me to backup into that directory.  Only problem being I don't know how to backup at all.  Can someone please tell me how to backup in that directory?  




thanks,

ps. sorry for restarting this thread, but it seemed like a good place to start.

---

### Post by eggdeng on 2007-09-30
```
sudo cp /etc/X11/name_of_file  /etc/X11/name_of_file.bkp
``` The .bkp doesn't stand for anything special, just to remind you it's a backup file.

---

### Post by jindosept on 2007-09-30
what should the name of the file be? sorry for being so completely stupid.  but when I try to type what you said in I got something saying "missing destination file operand after (whatever I wrote)"   can you give me a name of a folder with the "file operand" please?

---

### Post by PmDematagoda on 2007-09-30
The name of the file is xorg.conf

---

### Post by jindosept on 2007-09-30
I type in "sudo cp /etc/X11/xorg.conf" to backup but the terminal still says that I am missing the operand.  do you know what's up?

---

### Post by Pumalite on 2007-09-30
sudo cp /etc/X11/xorg.conf /etcX11/xorg.conf.back

---

### Post by jindosept on 2007-09-30
> **Pumalite said:**
> sudo cp /etc/X11/xorg.conf /etcX11/xorg.conf.back


I typed in that, but I get a message saying cp: missing destination file operand after "sudo cp /etc/X11/xorg.conf /etcX11/xorg.conf.back"   

Is there a way to skip this step in the reconfiguring?  because this file operand definitely has me stumped.

---

### Post by kellemes on 2007-09-30
> **jindosept said:**
> I typed in that, but I get a message saying cp: missing destination file operand after "sudo cp /etc/X11/xorg.conf /etcX11/xorg.conf.back"   

Is there a way to skip this step in the reconfiguring?  because this file operand definitely has me stumped.

Typo.. it should be "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back"

---

### Post by Pumalite on 2007-09-30
Thank you.

---

### Post by jindosept on 2007-09-30
I still get the same message.  ie. "cp: missing destination file operand"  would a new monitor solve this?

---

### Post by Pumalite on 2007-09-30
You are probably missing a space somewhere. Better copy and paste command:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back

---

### Post by kellemes on 2007-09-30
I guess you missed the space in between? Am I right?
Try to understand what's happening here..
You need to copy path/filename to path/filename.mybackup

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back

Edit: sorry for the duplicate answer.

---

### Post by jindosept on 2007-09-30
can't copy and paste, I'm on this forum with a different computer and typing these commands into the computer next to me. I put in a space in the middle of the line, I was missing that but instead of an error message, I get nothing and just a new line in the terminal with my name@ubuntu:`$

---

### Post by kellemes on 2007-09-30
type "ls /etc/X11" and you'll see a list of files, if you also see "xorg.conf.backup" your copy-action succeeded.

---

### Post by jindosept on 2007-09-30
I typed "ls /etc/X11" and I get a list.  the word "cursor" is in blue, and to the right of it in gray is xirg.conf.back  
there are two columns, I really don't understand what the computer wants me to do.  have I backed up the x server if I saw this and why can't I continue in reconfiguing?  sorry for these probably-vague questions.

---

### Post by PmDematagoda on 2007-10-01
That is the list of the stuff in your X11 folder, I'm saying stuff because everything is listed, folders and files. Just read through the produced list and see if the file you wanted to create is there.

---

### Post by kellemes on 2007-10-01
Well, cursor is in blue because it's a directory.. I guess.. I have another system so it's different at my end.
Just check if *xorg.conf.backup* is there, it's the name of the file you created.

---

