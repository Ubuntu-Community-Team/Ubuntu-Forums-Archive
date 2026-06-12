---
title: "Texas Instruments 5-in-1 Card Reader"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by natehatewindows on 2007-10-30
I am running gusty and have been trying to get my TI 5-in-1 card reader to work. I have not found very much about this topic in gusty but have in edgy. I found [http://news.softpedia.com/news/Texas-Instruments-5-in-1-Card-Reader-under-Ubuntu-Edgy-43688.shtml](http://news.softpedia.com/news/Texas-Instruments-5-in-1-Card-Reader-under-Ubuntu-Edgy-43688.shtml)
 that says how to set it up in edgy but i guess gusty dose not have the TI firmware module built into the kernel.....so this is my question....how would i build this TIFW module into my kernel if its even possible. here is the out put to "lspci":

home@home-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)


Thanks for the help and ill keep this updated if i find a fix. :)

---

### Post by pismikrop on 2007-11-04
Same problem:

/var/log/kern.log messages:

```
Nov  4 12:59:17 minik kernel: [  563.788000] tifm_core: MemoryStick card detected in socket 0:0
Nov  4 12:59:17 minik kernel: [  563.792000] tifm_ms: Unknown symbol tifm_has_ms_pif

```

---

### Post by bailunrui on 2007-11-04
I, too, would be interested in learning how to build this into the kernel rather than having to enter the code every time I want to use my 5-in-1

---

### Post by nikoPSK on 2007-11-04
That's funny... I'm in gutsy and have Centrios 54 in 1 card reader. I plugged it in, shoved in a card and it worked....

---

### Post by pismikrop on 2007-11-04
is it a card of texas instruments?

---

### Post by nikoPSK on 2007-11-04
nooo... Just saying if it's USB it should work right away.

---

### Post by pismikrop on 2007-11-05
no it is pci

---

### Post by nikoPSK on 2007-11-05
well, if worse comes to worse ditch the pci one (who has a free slot anywyas...;)) and grab a usb reader.:)

---

### Post by speedisso on 2007-11-05
To test your card reader, open a terminal and type the following commands:

```
sudo modprobe tifm_7xx1
sudo modprobe tifm_core
sudo modprobe tifm_sd
```

Now insert a card and it should auto mount. If all went well and you see a Nautilus window with the contents of your card, you can make this permanent by editing the /etc/modules file:

```
sudo gedit /etc/modules
```

and add the following lines:

```
tifm_7xx1
tifm_core
tifm_sd
```

save and close the file (remember to leave a blank line after the last row).

Try this it should work.

---

### Post by pismikrop on 2007-11-05
i already tried all of them.

---

### Post by speedisso on 2007-11-05
> **pismikrop said:**
> i already tried all of them.

Can you type lspci and put the output here  so i can figure out ?

---

### Post by natehatewindows on 2007-11-07
i have also already tried all of those, none worked. here is my lspci for you to look at. without a card in of course,

Thanks! :)

home@home-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by natehatewindows on 2007-11-07
> **nikoPSK said:**
> well, if worse comes to worse ditch the pci one (who has a free slot anywyas...;)) and grab a usb reader.:)



its in a notebook so its not taking up any extra space....i would never put on of these in a tower.....really UBS card reader are the way to go but my lappy has a built in one so i would like it to work. ;)

---

### Post by pismikrop on 2007-11-07
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


```

---

### Post by natehatewindows on 2007-11-07
pismikrop....

do you have sound in gusty? whats the model of toshiba you have? bios version? i have no sound in gusty i *think* because of a bug....but im not to sure.

thanks

---

### Post by natehatewindows on 2007-11-07
almost forgot....

here is my dmsg when i put in a MMS pro.

last few lines:

[ 3869.096000] tifm_core: MemoryStick card detected in socket 0:0
[ 3869.180000] tifm_ms: Unknown symbol tifm_has_ms_pif

---

### Post by speedisso on 2007-11-07
> **natehatewindows said:**
> almost forgot....

here is my dmsg when i put in a MMS pro.

last few lines:

[ 3869.096000] tifm_core: MemoryStick card detected in socket 0:0
[ 3869.180000] tifm_ms: Unknown symbol tifm_has_ms_pif


The Ubuntu 7.10 don't include the tifm (Texas Instruments Firmware) module into the default kernel so you have or to recompile the kernel mannualy or ask the geeks of this forums..because i don´t have any solutions for you...sorry

---

### Post by natehatewindows on 2007-11-07
ok well i have a few things to say.....

fiesty came with the TI firmware right? if so then why did they not include it in gusty (i dont expect you to have an answer :) ) 

ok im using a winmodem from linuxant (yes i paid for it), and i got the modem from ubuntu 2.6.22.14-Generic ...if i recompile the kernel will my modem still work? right now i have no sounds and it seems i might need to recompile to get sound also.

---

### Post by pismikrop on 2007-11-07
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159951](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159951)

i report this.

toshiba tablet pc m400

---

### Post by asiersar on 2007-11-07
I have been two years waiting for Memory Stick support in Linux. The driver is under development, you can see it here:

[http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver](http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver)

"Currently in development:
* tifm_ms - driver for MemoryStick cards (beta)"

If you want to try the latest SVN development, you can follow these instructions, taken from [here]("http://www.micropctalk.com/forums/showthread.php?p=24340") (at your own risk): 

At a terminal type

```
svn co http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/
```

then

```
cd driver
```

```
make
```

```
sudo make install
```

restart.

I tried it, now I have this errors in dmesg:

```
[  102.168000] tifm_core: MemoryStick card detected in socket 0:2
[  102.208000] memstick0: could not switch to parallel interface
[  102.208000] memstick0: physical block 2 is disabled
[  102.208000] memstick0: physical block 9 is disabled
[  102.208000] memstick0: physical block 1122 is disabled
[  102.840000]  msblk0: unknown partition table
```

I am afraid I have screwed my card up...

---

### Post by natehatewindows on 2007-11-08
> I think i have screwed up my card

can you reformat it? or is it SCREWED UP???

---

### Post by asiersar on 2007-11-08
False alarm, it still works in Windows.:)

---

### Post by natehatewindows on 2007-11-09
well i guess for now im just going to wait for a patch or something to come along. i only use my MMS for my camera and i can plug it in via USB.....
it would be really nice for everything to work but i guess ubuntu is just not there yet....strange because from what i have read the card reader would work in mandriva fine (it has the tifw from what i read). So basically my ubuntu has everything working, printer, external HD and DVD-R (so i can copy dvds from here in Ukraine....stupid region settings!), and winmodem.  everything works except my sound :( (a bug) and my wonderful little card reader. i hope my sound bug will be fixed soon but it looks like it wont be :(

---

### Post by somolinosfg on 2007-11-17
Hi!

I have a HP Pavilion dv1000 laptop running Gutsy Gibbon. Althought the SD reader is working fine, the xD reader is not.

I've done a lot of research and could not find a solution to this issue. The card reader is exactly the "infamous" Texas Instruments 5-in-1 Card Reader.

Any idea of what is going on with my xD Card Reader? I read in some forums that there is not support for this device yet. Is it true?

Thanks.

---

### Post by asiersar on 2007-11-19
Look [here]("http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver").

"Early stages of development:

    * tifm_xd - driver for xD/SmartMedia cards"

---

### Post by somolinosfg on 2007-11-19
Thanks! But it seems that I'll need to wait a lot until being able to use my xD card reader. It's still in early stages of development...

I'll keep using Windows to download my photos from the xD card by now...

---

### Post by natehatewindows on 2007-11-20
i think a USB card rader would work i have not tried but i have read a lot of posts where people are using them fine and you can get them from pretty cheap. I wish my memory stick worked but i can just plug my camera in and get the pictures off the memory stick. so maybe you could do the same if the xd card goes in a camera....just plug the camera in a USB port. :)

---

### Post by somolinosfg on 2007-11-20
Thanks! The wired solution just worked! :)

---

### Post by natehatewindows on 2007-11-20
thought it would. ubuntu is pretty good with cameras now. :)

---

### Post by nikoPSK on 2007-11-20
so it works? good for you!:)

---

### Post by Kralizec on 2007-12-27
After trying for a long while to get my card reader working fully (it worked with some cards, but not others) my TI 5-in-1 card reader seems to read all cards after I followed asiersar's advice and installed the current svn release.

---

### Post by integr8e on 2008-01-02
How did you get MS cards to work?  I installed the svn drivers according to asiersar's instructions, and rebooted; my SD card works well, but not my MS card.  It is apparently detected because dmesg reports:
> [   171.444017]   msblk0: unknown partition table
[   215.906150]   tifm0 : demand removing card from socket 0:0
[   275.913296]   tifm_core: MemoryStick card detected in socket 0:0
[   275.922503]   memstick0: physical block 2 is disabled
[   275.922511]   memstick0: physical block 1022 is disabled
[   275.922515]   memstick0: physical block 1023 is disabled
[   275.922520]   memstick0: physical block 8190 is disabled
[   275.922524]   memstick0: physical block 8191 is disabled

Edit: The card reader on my desktop detects my MS card fine, so I don't think the problem is with the memory stick (I don't "think").

Another Edit: I guess asiersar had a similar problem:
> [  102.168000] tifm_core: MemoryStick card detected in socket 0:2
[  102.208000] memstick0: could not switch to parallel interface
[  102.208000] memstick0: physical block 2 is disabled
[  102.208000] memstick0: physical block 9 is disabled
[  102.208000] memstick0: physical block 1122 is disabled
[  102.840000]  msblk0: unknown partition table

Has anybody figured out how to fix this?

---

### Post by Kralizec on 2008-01-02
I believe what I had to do was remove the previous modules first:

```

sudo rmmod tifm_7xx1; sudo rmmod tifm_core; sudo rmmod tifm_sd

```

then installed from source.
So what you may want to do is uninstall the source-installed modules, remove the pre-installed modules, then re-install the source modules as you did before. I don't know if you tried this before or not, but I hope it works for you.

---

### Post by integr8e on 2008-01-04
I dunno', I still can't get it to work (connecting the camera to the USB port does work, though).  Did you get your's to read MS cards?  Mine is an old Memory Stick (not Pro, Duo, or anything else).  Maybe it's just the fact that the driver's still in beta form???

---

### Post by Timokl on 2008-01-06
> **integr8e said:**
> I dunno', I still can't get it to work (connecting the camera to the USB port does work, though).  Did you get your's to read MS cards?  Mine is an old Memory Stick (not Pro, Duo, or anything else).  Maybe it's just the fact that the driver's still in beta form???

MemorySticks don't work yet under Linux. :-(

See [this post]("http://ubuntuforums.org/showpost.php?p=4039759&postcount=13").

---

### Post by integr8e on 2008-01-07
I was trying to use the beta tifm_ms driver as described by @asiersar in [**_this post_**](http://ubuntuforums.org/showpost.php?p=3726886&postcount=20), but I'm thinking plain ol' MS cards aren't supported by the beta driver either.  Thanks for the reply :)

---

### Post by scorpio_oz on 2008-04-09
Hmm I am confused by some of these postings. People are saying that the MemoryStick is not supported under Linux. Well I had it working fine on Gutsy and had copied off many a photos from the card. I since had to reinstall and never managed to get it working again. Adding the 3 tifm entries into my modules file worked before. 

I am new to Linux and am bewildered how the same base install and changes to that file produces different results??

Can anyone explain this?

---

### Post by integr8e on 2008-04-09
You probably have a newer model MS card (mine is one of the original ones).  Many of the newer models are supported - such as the MS Duo and MS Pro - but the one I have is just a plain ol' MS card...

Edit: I just checked out the link to the drivers main website, and they now have an alpha version driver for legacy MS cards, so maybe I'll be rockin' and rollin' sooner than I thought :)

---

