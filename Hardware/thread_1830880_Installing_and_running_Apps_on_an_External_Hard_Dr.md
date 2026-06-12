---
title: "Installing and running Apps on an External Hard Drive"
date: 2011-08-22
forum: Hardware
---

### Post by Moglagh on 2011-08-22
Hello Ubuntu Community,

     I am a total Newbie just joining the Ubuntu/lLinux Community. I am running Ubuntu 11.04 on an HP Mini 1010nr Netbook computer. These computers as you probably already know Have no Optical drives. It has 2 usb ports and a built in 8Gb Solid State Hard Drive or SSD. I also have a 1TB external iomega Hard Drive. Everything seems to work fine. I can access and read from my external Hard Drive. What I want to be able to do since I have very limited space on my SSD is to Install and run apps using my External. Is this possible and what do I need to do to accomplish this. Thank You in advance for any help.

---

### Post by mikewhatever on 2011-08-22
You can't choose where to install applications in Linux.
Technically, you could move the '/usr' to a separate partition on the external hard drive, but then the system wouldn't work at all without that hard drive connected.
An SD card would probably be a better approach.
The default Ubuntu installation takes about 4GB. What applications do you want installed on a netbook that take 4GB?

---

### Post by aloksethi on 2011-08-22
not sure is there any way if u are installing apps using apt-get
if u r building from source, then u can provide PREFIX option to configure n choose ur external drive as path to install

---

### Post by RoyLongbottom on 2011-08-23
[FONT=Verdana]Assuming that you can boot from USB (as I can on my MSI Netbook), install Ubuntu on the external drive with a setting to boot from there when plugged in. Again as I can, you could connect the disk to other PCs and run the applications from there.[/FONT]

---

