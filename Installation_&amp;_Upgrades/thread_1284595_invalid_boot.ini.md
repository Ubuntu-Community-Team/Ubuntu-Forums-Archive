---
title: "invalid boot.ini"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by oneshot22 on 2009-10-06
I have XP and Ubuntu both on my pc but I think Ubuntu crashed or something. I tried to install it again. when I restarted my computer it says "invalid boot.ini." It boots XP fine but I don't know what to do about Ubuntu?:confused:

---

### Post by friv_livs on 2009-10-06
Does the "Grub stage 1" text ever come up before this error?

Are you able to get into the grub menu?

---

### Post by rreese6 on 2009-10-07
+1 Friv-Livs

Yes it does seem like Grub got messed up.


1. Boot up with LiveCD. Once you are on the Desktop, go to this link and download:
```
[Download Boot Information Script]("http://sourceforge.net/projects/bootinfoscript/")
```
This Script will gather your current configuration and make a report.
This gives us a better idea of what your problem is and how to fix it.

2. Open up terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will make a file called "Readme.txt" on your desktop.

3. Post the contents of that file here.

---

### Post by oneshot22 on 2009-10-08
do I just save it?

---

### Post by friv_livs on 2009-10-09
@ oneshot22:

If you're referring to what rreese6 wants, attach the readme.txt with a reply to the thread.

Otherwise, please clarify your most recent post.

---

### Post by oneshot22 on 2009-10-09
sorry i cant run it. it only opens in firefox is there a program i can run it in?

---

### Post by friv_livs on 2009-10-09
oneshot22:

What I meant by my last reply was edit your "do I just save it?" reply and include what you were refering to. Your OP was clear enough.

---

### Post by rreese6 on 2009-10-09
I wanted you to download the script, then run it.
once that script is done you will see a new file called Readme.txt on your Desktop.
open that file, hit CTRL A to select all, then CTRL C to copy it.
then open this "post"(Thread) Click on Reply.
the Click on "#" in menu above then Press CTRL V.
hope that helps
once we have more information from the script you ran we will be able to start working on your problem.

---

### Post by oneshot22 on 2009-10-19
do I use a program? to open it?

---

### Post by Mark Phelps on 2009-10-21
Post #3 tells you what you need to do -- open a terminal and type the command as indicated there.  Then, follow the rest of the directions in post #3.

---

