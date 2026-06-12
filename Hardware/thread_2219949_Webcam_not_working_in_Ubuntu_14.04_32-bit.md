---
title: "Webcam not working in Ubuntu 14.04 32-bit"
date: 2014-04-26
forum: Hardware
---

### Post by James_Gascoyne on 2014-04-26
Hi everyone,

I have recently acquired an older laptop from a friend of mine. I have installed Ubuntu 14.04, however, the webcam does not work and finding additional drivers is proving difficult.

I followed the webcam page on the Ubuntu wiki just to make sure I wasnt being stupid. However Cheese and vlc cannot find the webcam.

There are two "video" devices listed in /dev/video*, but neither option works

It is a built in webcam. lspci returns the following:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G84M [GeForce 8600M GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

The model of the laptop is a Sony Vaio PCG-8Y2M. It also has alot of other buttons etc that dont work but for now just getting the webcam to work would be a great start.

It would also be great to get this working as I plan to do some gaming on linux videos for youtube and I may need to use the webcam at some stage.

Thanks,

James :(

---

### Post by James_Gascoyne on 2014-04-26
To add an extra layer of confusion the webcam works in skype but in nothing else.

---

### Post by SeijiSensei on 2014-04-26
Sony makes some of the least Linux-compatible equipment in my experience.  Your comment about the buttons is another piece of evidence for that claim.

If I were you, I'd just buy an outboard USB webcam and use that.  [Logitech cameras]("http://www.newegg.com/Web-Cams/BrandSubCat/ID-1080-152?Order=PRICE") are well supported in Linux.  I have a 9000 which is discontinued in favor of the [C920](http://www.newegg.com/Product/Product.aspx?Item=N82E16826104635), but that may be overkill for your application.

The fact that the Sony works in Skype probably has to do with the fact that Skype is distributed as a proprietary binary blob and likely has an appropriate driver built in.  The last time I looked at Skype it was compiled "statically" meaning it contained all the code it needed and didn't use the Linux libraries and drivers on the machine.  That's pretty much the way most proprietary software for Linux is configured.

I also found [this suggestion]("http://askubuntu.com/questions/241965/ubuntu-does-not-detect-my-vaio-webcam") for a way to build a driver for Sony webcams in Linux.  You need to compile it from source by entering these commands at a terminal ([adapted from this article]("https://bitbucket.org/ahixon/r5u87x")):.  
```

cd ~
mkdir build
cd build
sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
hg clone http://bitbucket.org/ahixon/r5u87x/
cd r5u87x
make
sudo make install
sudo r5u87x-loader --reload

```

There's no mention about which webcams it supports, but the implication from the article is that it supports any that use the Ricoh R5U87x chipsets.

---

### Post by dannyboy79 on 2014-12-30
i have the C260 and C920 and both work out of the box. C920 is the best, it has a built in hardware encoder for 1080p video. ;)

---

### Post by juan-valeroch on 2015-03-28
Thank you very much, it really worked after trying so many methods! I have a Sony Vaio VGN-FZ240E and Ubuntu 14.04 64 Bits, and my web can was not recognized after reinstalling Ubuntu 14.04. Now it works. I hope other users can see this. I refer to the following solution by SeijiSensei; April 26th, 2014 at 05:01 PM.:


cd ~
mkdir build
cd build
sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
cd r5u87x
make
sudo make install
sudo r5u87x-loader --reload

---

### Post by noone606 on 2015-10-31
Error: Failed to find any supported webcams.
Get this response after trying the above on my sony vaio pro 13 svp13219PGB
Any one got an idea how to get the webcam working on one of these, or what webcam it actually contains 
Im running ubuntu 14.04 lts if that makes any difference???

please help

---

### Post by mörgæs on 2015-11-01
Yes, it's likely that 14.04 is too old for such new gear. I recommend a fresh install of 15.10 as a first attempt.

---

### Post by noone606 on 2015-11-01
Surely its just a matter of adding a repository or some such ? you reallly think this is the best way?

---

