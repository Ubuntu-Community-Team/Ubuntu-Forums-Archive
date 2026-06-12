---
title: "How Can I Update 7.04 Feisty Fawn To Jackalope Without CD?"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by Codix121 on 2009-07-10
How Can I Update 7.04 Feisty Fawn To Jackalope Without CD?
Is that possible?
I'm out of CD's and too lazy to go buy some at the store,
any easier alternative?

---

### Post by 0pul3nce on 2009-07-10
Boot from alternative source. Usb ect

However I thought you could just download and it would automatically update.

---

### Post by Codix121 on 2009-07-10
You can boot from USB? Ohh that might work, I have a 2 gig flash drive.
I'll look into that.

---

### Post by hansdown on 2009-07-10
Hi Codix121.

Here is a tutorial on bootable usb.

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-create-a-bootable-live-ubuntu-904-usb-drive/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-create-a-bootable-live-ubuntu-904-usb-drive/)

---

### Post by JOHNNYG713 on 2009-07-10
In a terminal type

sudo apt-get dist-upgrade

Try that OR get off your lazy @#$ and get more cd's:lolflag: Good luck

---

### Post by svenskmand on 2009-07-10
You could also go to: System -> Administration -> Software souces -> Updates (tab) and under Release upgrade select "Normal releases" then open System -> Administration -> Update Manager, and select upgrade in the top of the new window :)

---

### Post by raymondh on 2009-07-10
Remember that if you upgrade thru the network,  you have to upgrade  sequentially ... all the way until you get to jaunty.  That takes time as you have to make sure you are updated in each version before upgrading.  That being the case, better to do a fresh install thru the USB.  It'll also give you a chance to try the Live Session to see how it (jaunty) relates to your system specs' and hardware.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you decide to do a network upgrade ... see this "end-of-life" documentation...

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Back-up your files.  Good luck.

---

