---
title: "How Do I Install Ubuntu..."
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by aprashanth on 2009-09-09
I am installing a new Ubuntu OS in my Pc..
The size of the hardisk is 500 Gb..How do I partition the Drive, 
so that I can have a separation drive just for Back up..
Please Help...

---

### Post by luctor on 2009-09-09
Gparted (partition editor) is included on the live cd.
Just run gparted from the livecd and after partitioning run the installer.

---

### Post by lisati on 2009-09-09
You might want to follow luctor's suggestion of using the partition editor (gParted) to set up a backup partition, with a suitable amount of empty space on the disk drive to install Ubuntu. Then tell the Ubuntu installer to use the largest continuous free space.

Don't forget to make a backup of your important data first!

---

### Post by tommcd on 2009-09-09
Will Ubuntu be the only operating system on the computer? Or are you dual booting with Windows?
Ideally, you should choose manual partitioning and set up 3 partitions:
a 12-14GB root partition
a swap partition of 1GB
the rest of the drive will be a home partition.
This keeps your data on a separate partition, so if you ever reinstall Ubuntu your data is safe on a separate partition. Here are some resources to get you started:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[http://howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://howtoforge.com/the-perfect-desktop-ubuntu-9.04)

---

### Post by aprashanth on 2009-09-09
Let me be more clear..I am installing ubuntu (on another P.C)...
Right now in front of me there is a window.. opened called.. prepare disk space..
there are two options in front of me now.. 
1) I use..the entire space. if I use this then.. it would install on entire Disk..
2) specify partition Maunually (Advanced),, I dont know how to use, this,,, 

All I need is one more partion so that I can place Back Up files...Please help..

---

### Post by aprashanth on 2009-09-09
tommcd I got what you are saying.. but how do I do that.. 
Please help..

---

### Post by tommcd on 2009-09-09
So you want to create a separate home partition for you data? Is that correct?
If so, then you will need to use manual partitioning. See this tutorial:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Write back if you need more help.

---

### Post by aprashanth on 2009-09-09
Thank tommcd.. the link was very useful..
it worked..

---

