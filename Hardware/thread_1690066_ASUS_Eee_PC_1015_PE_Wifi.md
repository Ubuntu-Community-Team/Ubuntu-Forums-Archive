---
title: "ASUS Eee PC 1015 PE Wifi"
date: 2011-02-17
forum: Hardware
---

### Post by jeff_osu on 2011-02-17
Hi, I purchased an ASUS Eee PC 1015 PE. It came installed with Windows 7 Starter. I installed Ubuntu 10.10. During the partition phase of the installation, I moved all free space to Ubuntu. I assumed this would leave Windows 7 in case I had any problem, but I'm not sure how to check to see if it is still there.
 
Anyways, Ubuntu 10.10 runs fine until I try and connect to the wireless. I enabled Wifi in the BIOS screen, and the browser will connect to a website with no problems....for about 5-10 seconds. The system becomes unstable and freezes. Is there a way to fix this?  If I turn Wifi off in the BIOS and plug in an ethernet connection, it works fine, but requiring an ethernet cable defeats the purpose of even having a netbook.
 
I've looked through the forums and come across people with similar problems, but I have yet fo find a way to correct this. I would really like to stick with Ubuntu and not have to buy a $50 W7Starter recovery disk for an OS I despise.
 
Thanks!
Jeff

---

### Post by jeff_osu on 2011-02-21
bump

---

### Post by jeff_osu on 2011-03-01
bump

---

### Post by Ashwall on 2011-03-02
I think that model also requires a certain proprietary wireless driver for the wireless to work. Can anyone here or you confirm that? And if so, do you have it installed?
Also, as far as Windows 7 goes, I believe the Eee PCs also have a recovery partition built in, don't they? Does a Windows 7 entry appear in GRUB? If not, you can install gparted and look at your partition table. Apart from that, you can try running this:
sudo update-grub

Sorry if this isn't helpful, but it might be better than what you were getting!

---

### Post by linux_one on 2011-05-20
the problem is with the kernel in 11.04, seems to include all newer asus eeepc's and is solved in latest kernel.
 to solve that you can download the latest kernel and install it very easily;
 go to 
http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/
and download the files; 

linux-headers-2.6.39-999_2.6.39-999.201105191210_all.deb
linux-headers-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb
linux-image-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb

(or different versions depending on time) then install them in exactly same order by the command;

sudo dpkg -i filename

one after the other, then restart the netbook. it worked perfectly for me.

---

### Post by alcenpu on 2011-05-29
> **linux_one said:**
> the problem is with the kernel in 11.04, seems to include all newer asus eeepc's and is solved in latest kernel.
 to solve that you can download the latest kernel and install it very easily;
 go to 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)
and download the files; 

linux-headers-2.6.39-999_2.6.39-999.201105191210_all.deb
linux-headers-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb
linux-image-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb

(or different versions depending on time) then install them in exactly same order by the command;

sudo dpkg -i filename

one after the other, then restart the netbook. it worked perfectly for me.

Hello, everybody. I have the same problem as the original poster. And I did all that is quoted above; I got those three files, but I am new (very new) to this OS and I don't know how I am supposed to install this files. Could anybody help me in this respect?
Thanks

---

### Post by alcenpu on 2011-05-30
also, my version is 11.04.

when I was running the OS from the USB stick, it actually showed that the computer was connected to the wireless network at my house. so it did when I first tried installing ubuntu with wubi. I haven't tried to plug it into the modem. I don't think that wireless modem is the issue, since other computers in my house are connected, like the one I am writing this message with. 

any help will be appreciated.

---

### Post by linux_one on 2011-05-30
Hi open a terminal and use the comand 'cd' to go to the folder that you have downloaded these files.
e.g. 
cd Downloads
then use the command
sudo dpkg -i filename
and in this command replace the filename by the name of the files you have downloaded, so you have to use this command three times and the order of installing files is important.
at the end, restart.

---

