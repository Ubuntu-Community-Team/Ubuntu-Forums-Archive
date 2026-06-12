---
title: "RAM to ext2 Drive Creating Script"
date: 2009-03-27
forum: Hardware
---

### Post by schmidtbag on 2009-03-27
My old script was not only out of date but ineffective.  This is just an easy RAMFS or TMPFS generator script so you can make temporary filesystems out of your RAM.  This script is very effective compared to my old one, and more advanced.  I would recommend this to anyone who wants high-performance disk read/write speeds.


Download the rt-fs.sh script for the main program.  Run in terminal like: "bash rt-fs.sh"

For those of you who are running Ubuntu version 8.10 or older and want to make your RAM become EXT2, download the ram2ext2.sh script.


Please help promote this as much as you can!
If you have any questions, comments, or suggestions, e-mail me at [email]zicronsoft@yahoo.com[/email]

---

### Post by schmidtbag on 2009-03-30
There is only one known glitch, and that is sometimes the maximum size won't work.  If that is the case, drop the size by about 2MB and you should be fine.  The math in it isn't perfect and I didn't get to test this on a whole lot of systems.

---

### Post by Exacerbate on 2009-03-30
Wow this is pretty awesome. I personally find a lot of use in this.

---

### Post by lacs on 2010-03-07
now you need to make a program to do this and unmount:KS;):):o:D:p:P

---

### Post by schmidtbag on 2010-03-07
it does, it generates an unmount script.  check your home folder

---

### Post by lacs on 2010-03-14
i mean without using the console anualy and it being in the softarecenter and btw whit is one of my fav progs i have i love my ram lol

---

### Post by schmidtbag on 2010-03-14
well all a graphical interface will do is have a question pop up to ask if you're sure you want to unmount, then have something pop up to ask you for a password and another popup to tell you that its unmounted.  its slower to code, slower to work with, and slower performance on the system if i make a gui for this.  by doing a command line theres much less work involved.  you can always create a launcher with the command:
bash -c "cd ~/ && bash unmount.sh"
and have it run in terminal.

If you think it should be in the software center you can help me promote it.  Considering that it isn't the most user friendly tool, I'm not sure if they'll bother with it.

---

