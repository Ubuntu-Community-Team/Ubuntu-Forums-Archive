---
title: "Installing KDE"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by oakdeveloper on 2009-05-17
Hi,

I have installed Ubuntu 9.04 and Kubuntu 9.04 on separate partitions in my computer. Because of which my GRUB menu has dual entries for Ubuntu 9.04, one for Ubuntu and another for Kubuntu. I would like to install KDE on the same partition in which Ubuntu 9.04 resides and remove Kubuntu 9.04 partition and add it to the Ubuntu 9.04 partition. How can I achieve this ? Please help.. 

I remember, a couple of years ago while using Fedora, there was an option in the login screen to specify if we want a KDE session or a GNOME session. Is it possible to have such an option with Ubuntu?

Thanks & Regards,
Babu

---

### Post by kpkeerthi on 2009-05-17
Boot into Ubuntu 9.04 and run this command
```
sudo apt-get install kubuntu-desktop
```

At the login screen, select Options/Session and choose KDE.

=-=-=-=-=
**To delete kubuntu 9.04:**
(Assuming kubuntu 9.04 is installed onto /dev/sda2 and Ubuntu 9.04 is on /dev/sda1)

1. Boot with Ubuntu **Live CD** (yes, live CD). 
2. Press ALT+F2 and enter **gparted**. 
3. Right-click on /dev/sda2 (where kubuntu is installed) and select **Delete**. This will create 'unallocated space'.
4. Now, drag /dev/sda1 (where Ubuntu 9.04 is installed) and expand it to fill the 'unallocated space' you just created.
5. Click **Apply**.

**Warning:** Backup your stuffs before messing with your partitions.
You can refer to gparted documentation for more info: [http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")

6. Reboot and select Ubuntu 9.04 from your GRUB menu. You are no longer in Live CD anymore.

5. ```
gksudo gedit /boot/grub/menu.lst
```
Open this file, scroll to the bottom and remove the Kubuntu boot lines. If you are not sure, post the contents of the file and we will tell exactly which lines are to be removed.

---

### Post by oakdeveloper on 2009-05-17
Thanks kpkeerthi!

I have successfully installed KDE and deleted Kubuntu and also expanded my partition with GParted. But after modifying the partition, I was unable to boot via Hard Disk as I was getting GRUB error 22. Then I booted again with the Live CD and googled for the error and found the solution here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

This is what I did to get my GRUB menu back:

ubuntu@ubuntu~$sudo grub

         [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>find /boot/grub/stage1
(hd0,5)

grub>root (hd0,5)

grub>setup (hd0)

grub>quit

ubuntu@ubuntu~$sudo reboot

[FONT=Verdana]After reboot my GRUB menu listed just one entry for Ubuntu and I didn't have to edit the menu.lst file.

Thanks again!

[/FONT]

---

