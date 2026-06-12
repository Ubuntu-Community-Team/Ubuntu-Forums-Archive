---
title: "Going from 8.10 back to 8.04"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by dd000d on 2009-03-18
Ok once i installed 8.10 It didn't like any of my video or sound cards. I tried updating things and can't even log into my computer now. Think the best thing would be to go back to hardy heron. Any way how to do that in the root?

---

### Post by upchucky on 2009-03-18
use gparted to delete the partition, then recreate the partition, re-install 8.04

---

### Post by dd000d on 2009-03-19
Is there anyway I can save my settings and programs and stuff?

---

### Post by zvacet on 2009-03-19
Yes,you can save your settings if you have separate home partition.if you don´t have one make it following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.You can save packages with aptoncd (it is in synaptic).For more information about aptoncd read [this.]("http://aptoncd.sourceforge.net/")

---

### Post by adzik on 2009-03-19
As a quick note, the psychocats guide failed completely when I followed the instructions, which is not to say it doesn't work.
Here is another one that helped me through the process successfully for what I was trying to do, and should help with your situation. [**Link**]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html").
More information is better than less. Good luck.

---

### Post by dd000d on 2009-03-20
could I just pop the live cd in and copy the home folder onto a thumb drive or external hard drive then reinstall 8.04 and copy the old home folder back on?

---

### Post by 73ckn797 on 2009-03-20
I think if you have capacity to copy the contents to another storage device then do that and copy back over once you have completed the new installation. I have done that several times but only with the Documents folder. I would just reinstall other programs again.

---

### Post by Therion on 2009-03-20
I've never tried this but using -r option with a cp command (cp = copy, -r = recursive (sub folders etc.)) should work.  In theory anyway.

This is just an example, not actual code to *use*:

```
cp -r /home/you /media/*sda1*
```

With */sda1* being your thumb drive or wherever you want to put your backup copy of /home.  

I just question whether copying, even recursively, is a good way to make a backup.

I'm not saying it isn't, I'm saying I don't know.

**[COLOR="Red"]EDIT:[/COLOR]** Geez I'm slow tonight... You know what would be an easy solution for you?  Download **QuickStart**.  It'll backup your stuff for you real easy.

[http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop](http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop)

BE SURE you follow the install directions.

---

