---
title: "X on Inspiron 1100 / 8.10 intrepid - SOLVED"
date: 2008-12-30
forum: Hardware
---

### Post by jermz on 2008-12-30
After much hair pulling, I have solved the problem of getting X to work on an Inspiron 1100 with Intrepid Ibex (8.10)!

Once the system is installed, boot to single user and remove all the compiz packages:

apt-get remove compiz compiz*

Apparently, the interaction between the intel(4) driver and compiz is causing the lockups and other problems. 

I also added the following kernel boot options to /boot/grub/menu.lst to get full-screen text consoles:

kernel      /boot/vmlinuz-2.6.27-7-generic root=UUID={gibberish) ro quiet nosplash vga=792

There is hope, 1100 owners. Running 8.10 can be done!

---

### Post by candtalan on 2008-12-30
I am looking forward to trying it, thanks for this!

---

### Post by LRTIMKEN on 2008-12-30
Content's nice and I support you![FAG](http://www.nskcn.com/product/ShowClass.asp?ClassID=26) [fag](http://www.nskcn.com/product/ShowClass.asp?ClassID=26) [FAG](http://www.9skf.cn/product/ShowClass.asp?ClassID=26) [fag](http://www.9skf.cn/product/ShowClass.asp?ClassID=26)

---

### Post by dstark on 2009-01-10
Thanks so much, jermz. Sorry if this is a silly question from a newbie, but how exactly did you get Intrepid to boot so you could make the changes you mentioned to the compiz packages? I've tried booting several times (including in safe graphics mode), and my 1100's display is blank each time.

Thanks, again.

---

### Post by thorMX on 2009-01-31
dstark, 
I've been struggling to get 8.10 running on an old 1100 for the last few hours. Here's the exact steps that I followed to finally get the liveCD up and running:

First enter BIOS setup to check revision (mine had A32, this is the most recent, I think). then make sure that the UMA was set to 8MB of RAM to video (this one took me way too long to figure out)

Then boot from 8.10 live CD
hit F6, add "ro nosplash vga=773" to boot options

hit enter, wait a few minutes until screen switches to GNOME startup (starts loading xorg...)

Quickly hit ctrl-alt-f2, before compiz loads

then wait until you hear the ubuntu startup noise.

then run "sudo apt-get remove compiz compiz*", as jermz stated above.

then restart gdm ("sudo /etc/init.d/gdm stop", then "sudo etc/init.d/gdm start" )

Hope this helps!

---

