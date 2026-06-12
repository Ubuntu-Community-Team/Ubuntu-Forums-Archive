---
title: "Windows7  ate my Ubuntu partition"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by beanie0610 on 2009-09-01
So I installed Windows 7 to replace my XP partition. But whenever I start my computer, I never get the option on whether I can choose Ubuntu or Windows. How do I get this option back so I can use Ubuntu again?

---

### Post by rcayea on 2009-09-01
you have to do the reinstall grub thing. Here is the link:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by rcayea on 2009-09-01
Also, once you reinstall grub you should see both Losedows7 and Ubuntu as an option at bootup. 

Good Luck, I hope this info helps.

---

### Post by moofang on 2009-09-01
If you install (any) Windows after Linux, Windows will basically 'eat' up grub and replace it with its own booter. So you basically need to put grub back. There are tonnes of tutorials on how to do this. Here's one off the top of a quick googling:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by presence1960 on 2009-09-01
> **rcayea said:**
> you have to do the reinstall grub thing. Here is the link:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

stick with this how to as it will find the partition with stage 1 on it in case you aren't sure where it is. I kind of wrote my own based on that one: here it is fyi:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In #6 most will want to install GRUB to MBR unless chainloading a linux install off another installed GRUB, in which case you want to put GRUB on the first sector of that distros partition.

---

### Post by beanie0610 on 2009-09-01
I tried your method Presence, but it still has my Windows XP partition listed, and has problems with booting up Windows 7. Would anyone happen to be able to help me with this?

---

### Post by presence1960 on 2009-09-01
that is not my method but it is the method to restore GRUB. The name does not matter on the windows. You can edit that name in menu.lst. if windows won't boot then you have another problem.

I should have done what I always do but this seemed straightforward, but obviously it is more involved. So do this :

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

This script will reveal much about your setup and boot process.

---

### Post by beanie0610 on 2009-09-02
After running in safe mode a few times and running chkdsk, I finally was able to boot my windows 7 partition through GRUB. It seems to work fine, I just need to rename it in GRUB from XP to 7. Could you walk me through that, if it's not too much trouble? 

Much oblige.

---

### Post by presence1960 on 2009-09-02
> **beanie0610 said:**
> After running in safe mode a few times and running chkdsk, I finally was able to boot my windows 7 partition through GRUB. It seems to work fine, I just need to rename it in GRUB from XP to 7. Could you walk me through that, if it's not too much trouble? 

Much oblige.

boot into Ubuntu and open a terminal, run this command ```
gksu gedit /boot/grub/menu.lst
```
Scroll down to the windows entry and edit the title line. 
Example:
> title  Windows 7 RC
rootnoverify etc


Click save on the top toolbar and close the file. next time you boot it will say what you input for title.

---

### Post by beanie0610 on 2009-09-02
That worked to perfection. Thanks so very much.


But is there a way for Ubuntu to recognize that my windows partition actually changed files? It's still showing up as my xp partition when I try to browse my Windows 7 files.

---

### Post by presence1960 on 2009-09-02
> **beanie0610 said:**
> That worked to perfection. Thanks so very much.


But is there a way for Ubuntu to recognize that my windows partition actually changed files? It's still showing up as my xp partition when I try to browse my Windows 7 files.

Do you mean in the left pane of your file browser under places? see pic below.

if so you can change the label of the partition in gparted. Boot from the Live Cd and choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
gksu gparted
```
or go System > Administration > Partition Editor. When gparted loads right click on the windows partition and choose Label. Then edit the label name. Whatever you enter is how that partition will show in File Browser and other functions in Ubuntu. see 2nd pic below.

---

### Post by beanie0610 on 2009-09-03
Actually no. When I try to browse my hard drive that Windows is partitioned on, it shows the folders from XP instead of the files and folder from Windows 7. I don't know how to make ubuntu update its indexing so that I can actually browse my Windows 7 file system.

---

### Post by presence1960 on 2009-09-03
> **beanie0610 said:**
> Actually no. When I try to browse my hard drive that Windows is partitioned on, it shows the folders from XP instead of the files and folder from Windows 7. I don't know how to make ubuntu update its indexing so that I can actually browse my Windows 7 file system.

Ok then I need to see exactly how your machine is setup. can you download & run the boot info script I asked you to do in post # 7.

---

### Post by beanie0610 on 2009-09-03
I'm sorry for wasting your time but I'm just stupid. Everything was just indexed differently so of course I wouldn't be able to find it in the same indexes that XP had them in. Thanks so much for all your help.

---

### Post by presence1960 on 2009-09-03
> **beanie0610 said:**
> I'm sorry for wasting your time but I'm just stupid. Everything was just indexed differently so of course I wouldn't be able to find it in the same indexes that XP had them in. Thanks so much for all your help.

No problem. The only "dumb" question is the one you don't ask. Enjoy Ubuntu!

---

