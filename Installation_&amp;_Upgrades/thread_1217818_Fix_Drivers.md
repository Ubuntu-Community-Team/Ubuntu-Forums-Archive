---
title: "Fix Drivers?"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by kn1ghtus on 2009-07-20
Hello I have a new system build, if a i7 2.66 chip, asus MOBO, 12 GB of ram 2 sapphire 4890 video cards .  I thought this would be a good time to try ubuntu for the first time.  

I first installed windows 7, everything works great.

I then downloaded the latest iso of ubuntu (9.04) installed it and it seemed to be working fine.  It then said I should update my graphic drivers.  I did and now it only boots to a command prompt.  Myself thinking like a windows guy, thought to reinstall it.  So I ran the disk again.  now I have two copies of Ubuntu and windows 7.  Both copies of ubuntu will not boot up after it updated the graphics cards...  So I guess my questions are...

1.  How can I downgrade to the graphic's card that is installed by default?

2. If I use the default graphics card, and I use 3 monitors?

3. How do I uninstall one version of Ubuntu? (as I now have two)

4. How do I set it to automatically boot into windows 7 if I don't push a key in the first 10 seconds (instead of ubuntu)

did I really make a mess of things, or what?!?!

---

### Post by pastalavista on 2009-07-20
When booting Ubuntu, choose 'recovery mode' from the menu and when it's loaded, select the last item, 'repair x' and try again.

To remove the extra installation, boot from the live CD, and when the desktop is loaded, type alt-f2 and enter 'gparted'. this will let you delete the second Ubuntu partition.

---

### Post by Mark Phelps on 2009-07-20
> **kn1ghtus said:**
> 4. How do I set it to automatically boot into windows 7 if I don't push a key in the first 10 seconds (instead of ubuntu)

Open a terminal and edit your menu.lst file as follows: "gksudo gedit /boot/grub/menu.lst".

You will find a line that says "default 0".  Count the number of "title" lines in your menu.lst file, starting with the first title line being zero.  Then, change the number on the "default" line to the number matching your Windows 7 title line count.

When you reboot, it will choose that entry by default.

---

### Post by Azyl on 2009-07-20
if u use nvidia or ati download and install a driver for your card if you have nvidia go on their site chose linux and your card and you`ll see a download, take the adress you can download the file from the command line using: wget [http://yourlink.com](http://yourlink.com) or any other download manager and then run the installer, the instructions are on the website and are verry simple. The installer does everything so you don`t have to know a lot about linux

---

### Post by kn1ghtus on 2009-07-20
Pastalavista,

thank you for the advice on what to try, however it did not work, it is still trying to boot me to my desktop shell account.  any other thoughts on how I can get this working again?  


I am going to try to delete the second partition now.

---

### Post by kn1ghtus on 2009-07-20
it says I cannot run gparted off of the CD because it requires root access...

---

### Post by kn1ghtus on 2009-07-20
should I just install a third version, and delete the old two?

---

### Post by cariboo on 2009-07-20
To run gparted as root, press Alt-F2 and type:

```
gksu gparted
```

---

### Post by kn1ghtus on 2009-07-20
I cannot-- I cannot log into ubuntu at all through the graphical interface, can I run that command logged into the shell desktop?

---

### Post by pastalavista on 2009-07-20
Booting from the live CD, you won't need to log in. I forgot, you do need to use sudo or gksu to run gparted but there is no password involved, just the command

boot the live CD to the desktop.. go to System > Administration > Partition Editor (gparted). it shouldn't need a password on the live cd. There you can delete all the ext3 partitions and reformat. (you'll need to right-click on the partition and unmount it before you can make any changes to it)

just a tip... I would delete all of the Ubuntu installs and make the space one large extended (logical) partition and inside of that create a / partition of about 20-50 GB and a /home partition as large as you'll need for all your data and settings and reinstall. that way, you won't need to reformat the /home partition every time you want or need to upgrade or re-install... just the / partition. also make a swap partition as large as your amount of memory, if you plan on using suspend or hibernate.

---

