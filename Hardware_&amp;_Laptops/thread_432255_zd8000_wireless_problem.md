---
title: "zd8000 wireless problem"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by mamood on 2007-05-03
i know a hell of a lot of people are having roughly the same problems with the hp pavilion zd8000 laptop and its wireless. however, i cant seem to find a correct, complete method to sort it out.
Iv tried so many ways to get it working but to no avail, iv managed to get the firmware working (through the synaptic package manager) but nothing else. 

iv got feisty fawn installed and Id be unbelievably greatful if anyone could give me a run through of how to get the wireless working. Im only just beginning to experience the joys of ubuntu n I really dont want to have to go back to shitty xp because of this.

Cheers evryone and anyone :)

---

### Post by zeller on 2007-07-26
Same here. I've tried multiple How-To's on the Ubuntu forums here, yet none seem to work for me. After entering in each line of command, they just return errors I don't understand or say something like the directory/file does not exist. I'm in the right directory using the terminal and I know I have the correct files, I'm looking right at them. No dice. I have a Broadcom BCM4318 chipset.

I've followed [this guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29"), and my wireless seems to be working, but I can not connect.

---

### Post by soadownz on 2007-07-29
Same problem here. Although the wirless appears to be installed and working fine - it is actually non responsive and unable to find / connect to any networks.

---

### Post by hankjw on 2008-02-23
Try this command, in a terminal window

sudo ifup --force ath1

It worked for me. The command forces the configuration of the wireless card.

Hank

---

