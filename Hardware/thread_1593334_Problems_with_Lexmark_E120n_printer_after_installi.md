---
title: "Problems with Lexmark E120n printer after installing Ubuntu 10.10"
date: 2010-10-11
forum: Hardware
---

### Post by ChiVampir on 2010-10-11
I got a very unpleasant surprise today when I tried to print out some work today:

As always Ubuntu found E120n's drivers when I turned on the printer, but when I try to pint something the printer tries to print, but don't grab the paper at all.

I thought that maybe it were broken or something, but it worked yesterday with Ubuntu 10.04 and today when I tested it with Peppermint Ice from my netbook

So anyone that's experiencing the same problems? Have someone found a way to fix this? I really need to be able to use my printer without having to use my netbook all the time.
[B]
Edit: [/B]I did a fresh install of Ubuntu 10.10.

---

### Post by ChiVampir on 2010-10-11
I just realised that it's possible to edit the printers .ppd file manually :redface:


[LIST=1]
[*]Download [**lex120n.txt**]("http://www.linuxquestions.org/questions/attachment.php?attachmentid=4823&d=1286819200") (it's an old .ppd file, I just had to change the file name to be able to upload it)
[*]Open Nautilus as root (*gksudo nautilus*)
[*]Goto **/etc/cups/ppd**
[*]Open the file named **Lexmark-E120n.ppd**
[*]Copy all the text from **lex120n.txt** and paste it into **Lexmark-E120n.ppd** (after removing all the text of course)
[*]Restart and voilà, the printer works properly again ^^
[/LIST]


You can also rename **lex120n.txt** into **Lexmark-E120n.ppd** and move it to **/etc/cups/ppd** instead of copying and pasting.

---

### Post by Hedley on 2010-11-11
> **ChiVampir said:**
> 
[*]Download **lex120n.txt**


Download from *where*, ChiVampir?

Thanks!

---

### Post by ChiVampir on 2010-11-12
You find the file here: [http://www.linuxquestions.org/questions/attachment.php?attachmentid=4823&d=1286819200](http://www.linuxquestions.org/questions/attachment.php?attachmentid=4823&d=1286819200)

I thought I had added the link, but seems like I forgot :oops:

---

### Post by Hedley on 2010-11-12
> **ChiVampir said:**
> You find the file here: [http://www.linuxquestions.org/questions/attachment.php?attachmentid=4823&d=1286819200](http://www.linuxquestions.org/questions/attachment.php?attachmentid=4823&d=1286819200)

I thought I had added the link, but seems like I forgot :oops:


Thanks!

---

