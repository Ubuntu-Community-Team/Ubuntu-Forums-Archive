---
title: "Trouble installing Ubuntu/GRUB"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by CrazeDIzzleD on 2009-01-05
I want to dual-boot Ubuntu with my XP. I have 3 hard drives. XP is on one all by itself, and the other 2 are storage drives. I made a 20GB partition on one of the storage drives to house Ubuntu.

I downloaded the latest 8.10 AMD64 release and booted off it, made an ext3 partition and a swap partition, and then installed Ubuntu. Upon completion, I rebooted and got a GRUB ERROR 22. I did some Googleing and learned what it meant, and how to fix it with the terminal on the LiveCD (the sudo grub, find /boot/grub/stage1 blah blah). I tried that, and it did nothing. I tried setup (hdx) with my main drive and my Ubuntu drive, wasn't sure which one to use but neither worked. I got frustrated and fixed my XP boot loader and booted into that.

I decided maybe the install was bad or something, so I tried repartitioning/reinstalling Ubuntu, and same deal. Tried the terminal fix again and no worky. I've done a lot of Googleing and searching and I can't seem to find anything the same as my case, and in all other cases that I find it is fixed with the terminal commands.

Can anyone help me please?

---

### Post by Pumalite on 2009-01-05
You have to find out what hard drive is first in the boot order in your BIOS and install Grub in that hard drive.
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by caljohnsmith on 2009-01-05
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

