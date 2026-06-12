---
title: "I need help disabling Kernel Mode Setting!"
date: 2010-11-26
forum: Hardware
---

### Post by Jazzmaster94 on 2010-11-26
First, I would like to say thank you to all those who reply to this. Now then, I really need to have an up-to-date installation guide for installing Ubuntu with the "nomodeset" GRUB/Kernel boot argument. I have an ATI Radeon X1350 Pro that has always caused me trouble regardless of which distro I use (I have used Ubuntu 10.04 as well as OpenSUSE 11.3 on the machine in question). Over at the OpenSUSE forums, I was informed that the issue I had experienced, which was a blank screen at boot up, was caused by my graphics card's incompatibility with Kernel Mode Setting. So OpenSUSE 11.4 is out, and after using OpenSUSE and KDE for a while I kind of want to go back to GNOME and Ubuntu. However, the KMS issues that I was having are still a problem. So I was wondering if anyone has an installation guide for Ubuntu 10.10 that includes steps to disable KMS, since OpenSUSE has a graphical tool for changing the Kernel Parameters I'm not exactly sure how to add "nomodeset" to my Kernel Parameters. Once again, any and all help is greatly appreciated!

---

### Post by conradin on 2010-11-26
You can add your kernel module at /etc/modprobe.d/blacklist
or this link might help..
[http://calebflynn.com/node/4](http://calebflynn.com/node/4)
it would be good to back up your originals before making changes.
maybe make a live cd before hand too. From what Ive read, it seems like 
not booting is what happens when this doesn't go right.

---

### Post by drs305 on 2010-11-26
If all you want to do is add "nomodeset" to the kernel options at boot, edit the Grub2 configuration /etc/default/grub file ( gksu gedit /etc/default/grub ) and add ***nomodeset*** to the end of the following:

> *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [I][COLOR="DarkRed"]nomodeset[/COLOR]*"[/I]

Save the file, then update grub:
```
sudo update-grub
```

---

### Post by Jazzmaster94 on 2010-11-26
Thank you drs305!   Just one more question, how do I apply "nomodeset" temporarily?  I know how to apply it on the Live CD, just not on GRUB2.  I just need to know that so I can ensure that after I uninstall Vi$ta and OpenSUSE, I can install Ubuntu, then log in to make the "nomodeset" permanent.

---

### Post by drs305 on 2010-11-26
> **Jazzmaster94 said:**
> Thank you drs305!   Just one more question, how do I apply "nomodeset" temporarily?  

From the Grub2 menu on boot, highlight the entry you want to boot, press "e" to enter the Edit mode. 

Go to the "linux" line and add the "nomodeset" option to the end of the line. 

Press CTRL-x to boot.

Changes made by editing the menu in this fashion during boot are non-persistent. It's a great way to experiment with boot options. You just have to remember what you typed so you can add it to the settings after booting to make them permanent.

When you don't have any more questions/issues, please mark the thread 'SOLVED' via the 'Thread Tools' link near the top right of the first post.

---

