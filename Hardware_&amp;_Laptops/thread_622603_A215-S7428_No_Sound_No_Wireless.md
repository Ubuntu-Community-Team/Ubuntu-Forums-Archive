---
title: "A215-S7428 No Sound No Wireless"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by drcantrell on 2007-11-24
I just got a Toshiba Satellite A215-S7428 and loaded 7.10 AMD64 and cannot get wireless or sound.  please help

---

### Post by jcsteele on 2007-11-25
Please post the output of an "lspci" command below so we may help you further.

//jcs

---

### Post by drcantrell on 2007-11-25
Here is the lscpi:
steve@steve-Toshiba:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

Again, no sound or wireless.  Please help.  Thanks.

---

### Post by jcsteele on 2007-11-25
Have a look at [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) which explains various methods for trying to fix your issue.

On my Toshiba notebook, its a simple fix...might work for you, worth a try.  You can find my instructions at [http://ww2.coastal.edu/jcsteele/gutsy-S4134.html](http://ww2.coastal.edu/jcsteele/gutsy-S4134.html) - its a simple fix, so if it doesn't work, just remove the line and try some of the methods above....

As for your wireless problem, it doesn't appear to be even detected.  Do you know what type/chipset/etc. it is using?

//jcs

---

### Post by wa3fae on 2007-12-07
Don't forget to check if the wireless switch on the left front of the laptop is turned on.

---

### Post by HandyAndyShortStack on 2007-12-29
I have the same computer and am also having a hll of a time getting the internal wireless working.  I tried this guy's [hacked drivers]("http://www.datanorth.net/%7Ecuervo/rtl8187b/"), but iwlist shows all networks at a 0% signal and dhclient can never get an ip.  Has anyone else had this experience with the S7428?  Others seem to have had success with similar computers, how about this one?

---

### Post by swat007 on 2007-12-30
@drcantrell

I am having the same... i have toshiba satellite a215-7422.... sound wireless not working... plz let me know if you found any solution to your problem! thanks

---

### Post by HandyAndyShortStack on 2007-12-30
I haven't tried this sound fix, but if anyone has with a s7428, please let us know if it works!
[http://ubuntuforums.org/showthread.php?t=620724&page=10]("http://ubuntuforums.org/showthread.php?t=620724&page=10")

Our computers have a [Realtek rtl8187b]("http://rtl-wifi.sourceforge.net/wiki/Main_Page") wireless card.  Some people on these threads have been able to get wireless using this card, but I can't seem to:
[http://ubuntuforums.org/showthread.php?t=619955]("http://ubuntuforums.org/showthread.php?t=619955")
[http://ubuntuforums.org/showthread.php?t=571046]("http://ubuntuforums.org/showthread.php?t=571046")

I'm going to keep battling and post any success I have here.

---

### Post by HandyAndyShortStack on 2007-12-31
I stand corrected! I am now posting using the internal Realtek USB in a (nonpersistant)  live USB Gutsy Xubuntu install.  Those hacked drivers are now working for me both in iwconfig and network-manager!:)

... now to tackle that sound issue...

---

### Post by SnackMaster511 on 2008-01-09
No luck with the acer sound fix on the A215-S7428

However, the Volume Control screen's playback tab is now accessible, It does offer the options for headphone, PCM, Front Mic Boost & Line In Boost. However, there is no sound output.

---

### Post by fissionmailed on 2008-01-10
What I had to do was to do this
[http://ubuntuforums.org/showthread.php?t=568463&highlight=satellite+sound](http://ubuntuforums.org/showthread.php?t=568463&highlight=satellite+sound)

and then 

[http://ubuntuforums.org/showthread.php?t=568463&highlight=satellite+sound&page=4](http://ubuntuforums.org/showthread.php?t=568463&highlight=satellite+sound&page=4)
squirage 's first post on that page. 

I have an A215-S5818 and did the first post and then the second and it worked and was too scared after 6 hours of trying to see if just the second would work. 

Sadly I still haven't gotten my wireless to work. :\

---

### Post by HandyAndyShortStack on 2008-01-20
Sweet.  Well, I guess my toshiba is going to be a vista lappy until better native support is available for it in linux.  I love ubuntu to death, but sound needs to work correctly for the kind of work I do on it.  I would need to keep vista around anyway for sibelius even if ubuntu worked perfectly.  *sigh*  at least I still have my desktop for ubuntuing.  If I have some time to tinker I will post anyting I figure out here:roll:

---

### Post by HandyAndyShortStack on 2008-03-23
New developments!:):):)
Hardy Beta is out and it natively supports the sound card just fine!!
Wireless is not native, though:(
and the hacked driver I used before does not seem to work:(:(
I wish I had some extra hours to try other workarounds.  Maybe one of these weekends...

---

### Post by onewithnature83 on 2008-05-12
just sharing my experience with the RTL8187b Wi-Fi.

I saw mention of the use of patched drivers and for a newbie it can be quite confusing was for me anyways. Here is my step-by-step how to for you all... I did this in Ubuntu 8.04.

Download rtl8187b-modified-dist.tar.gz and 2.6.24.patch 

from [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

Extract rtl8187b-modified-dist.tar.gz to desktop

*there are 12 entries into terminal and 2 files to edit.. make sure your files look EXACTLY like the ones shown*
*each line that contains "sudo" will require your password enter it each time.*
*You may need to isntall "patch" a friend had to do this... I did not.  "sudo apt-get install patch"

In terminal:

1	"cd Desktop"
2	"cp 2.6.24.patch rtl8187b-modified/"
3	"cd /"
4	"sudo mkdir /wifi"
5	"cd /home/yourusername/Desktop/rtl8187b-modified"
6	"sudo cp -r * /wifi"
7	"cd /wifi"
8	"sudo patch -p1 < 2.6.24.patch"
9	"sudo ./makedrv"
10	"sudo ./wlan0up"
11	"sudo nano /etc/rc.local"

*************************************************
add these 3 lines as shown below

/wifi/wlan0up
ifconfig wlan0 up
dhclient wlan0

**************************************************
*(should look like this)*
**************************************************
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/wifi/wlan0up
ifconfig wlan0 up
dhclient wlan0

exit 0
*****************************************************

press Ctrl+x then y to save and enter to exit saving the file

12	"sudo nano /etc/network/interfaces"

add these 2 lines as shown below.

pre-up		/wifi/wlan0up
post-down	/wifi/wlan0down


******************************************************
*(should look like this)*
******************************************************

auto lo
iface lo inet loopback

pre-up          /wifi/wlan0up
post-down       /wifi/wlan0down

**************************************************

press Ctrl+x then y to save and enter to exit saving the file

Restart your machine log in and if you click the network icon once it should show you all the available networks! 

Only thing is that it wont give you a real signal strenth just one bar always.. I think you can live with that.

---

