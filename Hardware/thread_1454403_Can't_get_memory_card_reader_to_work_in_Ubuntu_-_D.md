---
title: "Can't get memory card reader to work in Ubuntu - Dell Studio 1535"
date: 2010-04-14
forum: Hardware
---

### Post by Jammanuser on 2010-04-14
Hello,
I have the Dell 1535 laptop, and am running two versions of Ubuntu (8.10 and 9.10). On both, the memory card reader doesn't appear to be working. 
I put in an SD card adapter with a micro SD card inserted in it, and the micro SD card does not show up in the Computer section, and so I can't access it to put stuff on/take stuff off.

Please help.

Thanks in advance.

-Jam Man

:guitar:

P.S. Here is the link to the micro sd card and adapter which I have:
[http://www.cellphoneshop.net/2gbtrmsdmeca.html](http://www.cellphoneshop.net/2gbtrmsdmeca.html)

---

### Post by Jammanuser on 2010-04-14
And here is the lspci output:

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


---

### Post by ambient007 on 2010-04-19
I'm bumping this thread because I have a very similar problem:

I just installed 9.10 on an acer aspire 3680 laptop and the XD card reader that takes the card from my digital camera does not appear to be 'there' at all. - That I can tell anyway.

:confused:

---

### Post by Shenachie on 2010-04-19
Odd that the gurus on here are ignoring this thread as my lappie, Acer Aspire 7720G also does not have recognition of  it's card reader. 

Seems to be an ongoing issue with the Ubuntu OS.

Shenachie

---

### Post by Jammanuser on 2010-04-19
Ok, I installed the driver, but my printer still does not work. :(
Am open to any further suggestions.

-Jam Man

:guitar:

---

### Post by ambient007 on 2010-04-21
bump
 
 
:P

---

### Post by AndresPeralta on 2010-05-03
i have the same problem! help :popcorn:

---

### Post by Ellio-pc on 2010-07-31
I have a Dell Inspiron 1525 and the following worked for me. I got this information from: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490/+activity](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490/+activity)

I then got the file: [http://launchpadlibrarian.net/44373795/ricoh_xd_3.tar.bz2](http://launchpadlibrarian.net/44373795/ricoh_xd_3.tar.bz2)


First, extract the file in Nautilus in your home directory (right click, select extract here)

Open a terminal then: cd ricoh_xd_3

Then to install please do: make && sudo make install && sudo make load

This work wonderfully for me!

---

### Post by niziris on 2010-08-24
> **Ellio-pc said:**
> I have a Dell Inspiron 1525 and the following worked for me. I got this information from: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490/+activity](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490/+activity)

I then got the file: [http://launchpadlibrarian.net/44373795/ricoh_xd_3.tar.bz2](http://launchpadlibrarian.net/44373795/ricoh_xd_3.tar.bz2)


First, extract the file in Nautilus in your home directory (right click, select extract here)

Open a terminal then: [COLOR=Red]cd ricoh_xd_3[/COLOR]

Then to install please do: make && sudo make install && sudo make load

This work wonderfully for me!

I tried this but didnt work for me, [COLOR=Black]terminal inform me that there is no file or folder with that name
[/COLOR]  any hint how you do it

I have Dell vostro and memory car is not working either

---

### Post by Ellio-pc on 2010-08-27
You have probably extracted the file to your downloads directory. Cut and paste the file ricoh_xd_3.tar.bz2 to your home directory and then extract as in my original instructions. You should now see the directory: ricoh_xd_3. in your home directory. Try again, I hope it works for you. 

P.S. You may need to install the 'build-essential' package from the repositories to build anything from source.

---

### Post by Ellio-pc on 2010-09-18
Update -- My Xd card reader on my Dell Inspiron 1525 now works fine with the beta version of Ubuntu 10.10. Didn't have to load up anything, worked straight away.

---

### Post by mj2kubun2 on 2011-07-20
> **Ellio-pc said:**
> I have a Dell Inspiron 1525 and the following worked for me. I got this information from: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490/+activity](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490/+activity)

I then got the file: [http://launchpadlibrarian.net/44373795/ricoh_xd_3.tar.bz2](http://launchpadlibrarian.net/44373795/ricoh_xd_3.tar.bz2)


First, extract the file in Nautilus in your home directory (right click, select extract here)

Open a terminal then: cd ricoh_xd_3

Then to install please do: make && sudo make install && sudo make load

This work wonderfully for me!

Hi when i typed "make" and pressed Enter it showed me this

make -C /lib/modules/2.6.38-8-generic/build M=/home/mike/ricoh_xd_3
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/mike/ricoh_xd_3/nand/nand_base.o
In file included from /home/mike/ricoh_xd_3/nand/nand_base.c:42:0:
/home/mike/ricoh_xd_3/include/linux/mtd/mtd.h:16:33: fatal error: linux/mtd/compatmac.h: No such file or directory
compilation terminated.
make[3]: *** [/home/mike/ricoh_xd_3/nand/nand_base.o] Error 1
make[2]: *** [/home/mike/ricoh_xd_3/nand] Error 2
make[1]: *** [_module_/home/mike/ricoh_xd_3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [build] Error 2

what shud i do... thx in advance :confused:

---

### Post by grungedoobie on 2012-02-04
Cannot be certain this will work for your make and model, but here is what worked for me.

Ubuntu 11.10 -- HP Pavilion DV6000 series w/ internal no-name card reader with sticker label "SD*MS/Pro*MMC*XD"

My camera is an Olympus sport model that uses an XD card.

1. Get "testdisk" from repo with downloader of your choice, or paste the following into a console.   (In KDE it's K -> Applications -> System -> Konsole)

sudo apt-get install testdisk

2. Insert the XD card into the reader.  Don't worry too much about the indicator.  On mine, sometimes it stays on, sometimes it just blinks, and sometimes it does nothing.

3. Run photorec by use of the following command.  (photorec is a tool from the testdisk package)

sudo photorec /dev/smblka

4.  After you've entered your password, photorec will start.  You should see your XD card highlighted.  If nothing is there, this did not work, and chose quit from the lower portion of the console.

5.  If you see your XD card highlighted, then chose quit from the lower portion of the console.

6.  Go to your file browser.  And open your XD card.  Mine labels it by the name of the card rather than the device.

This works for me every time, but I do not know if it will work for you.  I seriously doubt it will work if you have turned off the autodiscovery option in your system settings.

Never forget to use "eject" on the card before pulling.  Ejecting makes sure all connections to the card are properly closed.


The Grunge

---

