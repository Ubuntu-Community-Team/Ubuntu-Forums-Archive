---
title: "Too Many Installs"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by CrystalMoth on 2009-08-26
I'm an utter n00b. I have a computer with a C drive of 500GB and a D drive with about 500GB. I then tried to install Ubuntu. I screwed it up somehow and so I installed it again. But I screwed that one up too. When I turn on my computer it says:
    VindowsVista
    Ubuntu
    Ubuntu

I for some reason have two Ubuntus and I don't know how to get rid of them. When I select one it loads but not with a graphical user interface/GNOME. I wanted to Install Mint over top the Ubuntus, but instead selected to boot side-by-side with Windows. Now a Mint menu appears when I turn on my computer, and I can either chose Mint or Windows. When I go to Mint it doesn't work. When I go to Windows it takes me back to the Windows boot loader where it still displays:
    WindowsVista
    Ubuntu
    Ubuntu

I was able to boot Windows when I then went to delete the partitions with Ubuntu on it and start over. So I did that, and now when I start my computer it says Grub Error 22. I tried to use the super grub disk to fix it but have been unsuccessful. I am currently using a live cd to access the internet and write this post.

If its of any relevance, I have an Acer Aspire Desktop computer running Windows Vista 64-bit home premium, or not running in this case, with an added internal TB hard drive. I have 8GB of ram.

I hope someone can please help me.

---

### Post by Bartender on 2009-08-26
Wow, Crystal, you gotta slow down, my friend.  The GRUB error is exactly what should happen if you installed Linux in the usual method then removed it.  There are a million posts on how to fix the Windows MBR, which is what you need to do to get Windows running again.  It's not hard to do, you just have to pick a method depending on whether you have a genuine Windows CD or need to download something like a Super Grub Disc or etc..  I've seen posts where guys claim they fixed the Windows MBR with a Linux install disc but I've never done it.

So, get Windows running again first, OK?

---

### Post by CrystalMoth on 2009-08-26
I've tried the Super Grub Disk and I don't have a Windows Install Disk. What should I do?

---

### Post by stlsaint on 2009-08-26
dont worry all is well use the livecd to erase the patition that you installed ubuntu onto... that will give MBR back to windows...and research on how to dual boot before you try again...MAINLY DO NOT SELECT TO INSTALL SIDE BY SIDE WITH WINDWOS!!!...its good that you did this tho...great learning experience...if you need more help please post here before you really screw something up bad!!

---

### Post by raymondh on 2009-08-26
> **CrystalMoth said:**
> I've tried the Super Grub Disk and I don't have a Windows Install Disk. What should I do?

Try this:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

What happened is that when you installed Ubuntu (and later on Mint), it installed GRUB on the MBR overwriting windows .... an experience you know now.

bootrec.exe/fixmbr

is a common command to fix the MBR for Vista.  If not, try bootrec.exe/fixboot (which writes a new boot sector).

With Vista back on, decide on how you want to install (automated or manual) Ubuntu and Mint.  Then, defrag Vista (2x if you have the time) as well as make a back-up of your files.

We'll go from there.

---

