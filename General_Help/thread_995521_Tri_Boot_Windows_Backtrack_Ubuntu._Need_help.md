---
title: "Tri Boot: Windows Backtrack Ubuntu. Need help"
date: 2008-11-27
forum: General Help
---

### Post by Knuffle on 2008-11-27
I have never done a tri boot before, but I would like to be able to boot Backtrack3 by default with the option to boot Windows XP and Ubuntu. I have no idea what I am doing and have not been able to find any tutorials. Any help you have to offer is greatly appreciated.

---

### Post by zwygart on 2008-11-28
It's very easy to multiboot with GRUB, I boot UbuntuLiveCD, GentooLiveCD, Puppy, RescueCD, sometimes others, and try now ArchLinux from and on my USB flash drive.

You can find tutorials for dual boot. If you use GRUB it will be very easy. If not I suggest you to install it.
Install the OS each on a other partition. Take care to install Windows first if it's not already done. Then install the two others by taking care that you DON'T install GRUB during Ubuntu installation since you want backtrack to be main. If all is installed and GRUB works, you only have to edit the file /boot/grub/menu.lst
[Here]("http://www.gnu.org/software/grub/manual/grub.html") is the manual that will help you.

Essentially you have to add these lines to boot Ubuntu or backtrack
```
title *title you will see in the menu*
root (hdX,Y)
kernel /path/to/the/kernel
initrd /path/to/initxxxx
boot
```
X,Y are the letters identifing your partition. (GRUB don't count the same way than Linux)
/path/to/the/kernel should point to the kernel depending on your OS and the same thing with initxxxx.
For more help post the out put of 
fdisk -l
the partition where you install what.

---

### Post by Knuffle on 2008-12-01
Thanks. I have Windows XP Home installed now, but I can't figure out how to install Backtrack3. All the tutorials I have found are for BT2 and don't work with BT3.

---

### Post by gTinker on 2008-12-02
I'm purplexed at your question. BackTrack is a system crafted for penetration testing and forensic analysis. I just can't see any use for such a system for someone who doesn't know how to triple boot. I don't mean you any insult, it's just that BackTrack isn't likely to be of much use to you at your level of knowledge. 

However, if you choose to continue, the howto on the developers site does detail how to install BackTrack3 in a multiboot configuration.
[http://backtrack.offensive-security.com/index.php?title=Howto](http://backtrack.offensive-security.com/index.php?title=Howto)

---

### Post by Knuffle on 2008-12-02
Hahaha. I have never done a dual boot before, I do penetration testing all the time. I am fairly fluent with Linux, but have severe trouble with Windows.

---

