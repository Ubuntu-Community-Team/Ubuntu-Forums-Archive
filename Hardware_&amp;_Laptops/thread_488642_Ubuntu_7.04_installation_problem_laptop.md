---
title: "Ubuntu 7.04 installation problem laptop"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by lavinia on 2007-06-30
Hello all.

I have Vestel Notebook 
-
Intel(R) 82566MC Gigabit Platform Lan Connect
Intel(R) Wireless WiFi Link 4965 AGN
---
FUJITSU MHW2160BH HDD 160GB SATA
---
TSSTcorp CD/DVDW SN-S082D ATA Device
---
Mobile Intel(R) 965 Express Chipset Family (Intel GMA X3100 graphics)
---
Intel® Centrino Core 2 Duo  T7300 (4MB Cache 2.0 GHz,800 Mhz FSB)
---
2048 RAM DDR II
---

But installation failed.

"Enter install" but black screen.(Wait 5 min.) Please help me. :(

---

### Post by lavinia on 2007-06-30
:-?

---

### Post by lavinia on 2007-07-01
please help me :-(

---

### Post by thierce on 2007-07-02
Maybe you could try to boot / install with the options noapic and lolapic by entering these in boot menu ;)

---

### Post by lavinia on 2007-07-04
thanks, I have done it too. But it is failed. :(

---

### Post by lavinia on 2007-07-05
waiting ubuntu 7.10  :(

---

### Post by talava on 2007-07-05
Tried the alternate installer yet?

---

### Post by ashaver on 2007-07-05
Can't even boot up with CD! Made new empty partitiion on laptop, downloaded Ubuntu 7.04, copied it to CD, tried to boot up from CD and after a bit of hesitation up comes Vista! Earlier I installed Ubuntu on my desktop and the whole procedure went flawlessly. I tried using the CD which worked successfully on my desktop on the laptop (after the newly minted CD failed to work) and it does not boot up the laptop either!
I have burned unrelated data on another CD and read it off the disk in order to test my burner/reader, and it works fine.  What on earth can the problem be? Thanks in advance.

---

### Post by lavinia on 2007-07-06
I understand. :( 
Ubuntu 7.04 does not support Santa Rosa platform(Centrino Pro).

(intel 956gm express chipset, Intel(R) Wireless WiFi Link 4965 AGN, Intel core 2 duo T7300 4 MB L2 2 GHz 800 MHz, Intel(R) 82566MC Gigabit Platform Lan Connect, FUJITSU MHW2160BH HDD 160GB SATA, Mobile Intel(R) 965 Express Chipset Family (Intel GMA X3100 graphics) ... )

---

### Post by Voland666 on 2007-07-07
It's easy to install feisty with the alternate cd. There are some good topics on how to accomplish this. Once installed, use NDISwrapper to get 4965 wireless (last build from source works fine, it even suspends/resumes without errors), and install this X3100 graphics driver package from here:

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

---

### Post by lavinia on 2007-07-08
Voland666 no no. because also yesterday I try alternate cd. But same problem. Not installed. :mad:
(black screen) . after noapic nolapic same problem. after desktop cd some problem.

----
understand.
Ubuntu 7.04 does not support Santa Rosa platform(Centrino Pro).

(intel 956gm express chipset, Intel(R) Wireless WiFi Link 4965 AGN, Intel core 2 duo T7300 4 MB L2 2 GHz 800 MHz, Intel(R) 82566MC Gigabit Platform Lan Connect, FUJITSU MHW2160BH HDD 160GB SATA, Mobile Intel(R) 965 Express Chipset Family (Intel GMA X3100 graphics) ... )
----
:(

---

### Post by Voland666 on 2007-07-08
That's very strange. My Dell Latitude D630 has a configuration very similar to yours (IWL 4965, CoreDuo T7300, GMA X3100) and installed without a glitch with the alternate CD. Please try to explain in greater detail your problem.
Some BIOS tweaking might resolve it, but I can't help you with this since I don't khow what options you have in the setup utility. Try, if availlable, to change those related to the SATA controller. BE CAREFUL however to TAKE NOTE of every option BEFORE committing any change, since they may prevent other operating system to work reliably or even boot!
Try also asking some people near you:
[http://www.ubuntu-tr.com/](http://www.ubuntu-tr.com/)
[https://launchpad.net/~ubuntu-tr](https://launchpad.net/~ubuntu-tr)

---

### Post by lavinia on 2007-07-09
Yes that's very strange. :(

Thanks for reply..

---

### Post by fredj on 2007-07-09
On the install screen one of the options runs a CD check try that to see if you have a good CD.

---

