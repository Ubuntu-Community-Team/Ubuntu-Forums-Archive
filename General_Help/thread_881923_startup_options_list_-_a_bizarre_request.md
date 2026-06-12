---
title: "startup options list - a bizarre request"
date: 2008-08-06
forum: General Help
---

### Post by waphlish on 2008-08-06
Hello! I'm a new user to Ubuntu, very happy that you've created "Linux for humans" for people who are sick and tired of Vista. xD

But, I do have one strange request. I hope someone would be kind enough to help me out! :)

After one installs Ubuntu, when the PC is loading up, there appears a screen that allows you to choose your OS.

Microsoft Windows Vista
Ubuntu

I love that. Options are great. :) 
But, I had accidentally installed Ubuntu on the wrong drive of my computer! So, I removed Ubuntu, and reinstalled it on the correct drive.

Now, the only problem is that on my choose-your-OS-page, there are three choices.

Microsoft Windows Vista
Ubuntu
Ubuntu

The first "Ubuntu" was from my first installation, and it doesn't work, of course. The second "Ubuntu" was my reinstallation on the correct drive, and works fine.

However, is it possible to remove the first "Ubuntu" from this list, since it doesn't work anyways? As a person with OCD, I can't help having two Ubuntu options on my screen.. xD

:) Please reply if any of you hold any knowledge on how to solve this problem whatsoever! Thank you =)

---

### Post by geirha on 2008-08-06
Try this: 
[https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?")

---

### Post by mb_webguy on 2008-08-06
Did you reformat the partition on which you initially installed Ubuntu?  Are you sure that the first installation of Ubuntu is no longer there?

If so, then typing "sudo update-grub" in the terminal should remove the old Ubuntu installation from the list.  If not, you might need to manually edit the GRUB menu by typing "sudo gedit /boot/grub/menu.lst" and delete the entry for the first Ubuntu installation.  You can tell which one you need to delete by looking at the "root" line of the entry.  The old Ubuntu installation should have the same hard drive (something like hd0) as the entry for Windows.

---

### Post by ajgreeny on 2008-08-06
I am confused.  Did you install the two ubuntus using wubi or did you go through a full install on formatted partitions?  If the latter, the first installation should still be there unless you have deleted that partition somehow.

Using you running ubuntu install open up a terminal Applications>>Accessories>>Terminal and enter the command ```
sudo fdisk -l
```Now hot enter and then copy and paste the output to this thread.  It will tell us more about your system and its current partitions, and let us give you detailed info about how to proceed.

---

### Post by waphlish on 2008-08-06
Ooh, so many helpful answers! Thank you guys so much for all your help! EasyBCD managed to fix the problem in two seconds. :)

Thanks again for all the help!

---

