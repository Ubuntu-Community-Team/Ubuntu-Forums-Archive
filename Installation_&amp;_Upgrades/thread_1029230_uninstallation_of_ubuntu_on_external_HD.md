---
title: "uninstallation of ubuntu on external HD"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Jameshardy88 on 2009-01-03
Hi i recently installed ubuntu on my external hard drive believing that it would not affect the PC that it was installed with. However now when that computer is started it loads a linux boot system and requires the external hard drive in order to start even into its own windows operating system. As this is not my computer i need to unistall ubuntu in order to regain functionallity of this computer and was wondering how i might go about doing this. Thanks for any help

James

---

### Post by Pumalite on 2009-01-03
Fix your Windows MBR with the Installation CD or Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by Jameshardy88 on 2009-01-03
how do i do this?

---

### Post by caljohnsmith on 2009-01-03
How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
That will install a Windows equivalent MBR to your internal sda drive. Then to install Grub to the MBR of your external drive, try:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then you should be able to boot your external Ubuntu drive, but if you are using a Ubuntu version prior to Intrepid, you may not be able to boot Ubuntu from your Grub menu and will need to tweak the Grub menu a little. But see if you can get this far, or if not, let me know what problems you run into. We can work from there if you want.

---

