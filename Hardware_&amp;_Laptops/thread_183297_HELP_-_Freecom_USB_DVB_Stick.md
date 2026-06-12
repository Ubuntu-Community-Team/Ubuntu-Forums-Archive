---
title: "HELP - Freecom USB DVB Stick"
date: 2006-05-27
forum: Hardware &amp; Laptops
---

### Post by strayduck_uk on 2006-05-27
HELP!

I'm a complete Linux newbie so I have no idea what I'm doing. I've tried using the instructions found on this forum and by using Google and no matter what I try, I can't get the Freecom USB DVB-T stick recognised on my laptop.

Can anyone point me to some definitive instructions that I can follow from start to finish which don't jump around from website to website? What do I need to view digital TV? And how do I "make" files??

Very confused

D:-?

---

### Post by The_Major on 2006-05-30
Strayduck, this is what I had to do to get my freecom working on Dapper....

First fire up a terminal and make sure you are in your home directory, then get the new firmware for the freecom:

```
wget http://thadathil.net:8000/dvb/fw/dvb-usb-wt220u-zl0353-01.fw
```

You need to copy this to the firmware directory:

```
sudo cp dvb-usb-wt220u-zl0353-01.fw /lib/firmware/$(uname -r)/
```

If you havent already done so you need to install the application to allow you to build the modular driver for the freecom. First:

```
sudo apt-get install build-essential
```

You will also need the tool to allow you to download the latest Video4Linux / DVB source:

```
sudo apt-get install mercurial
``` 

and then you need the kernel headers:

```
sudo apt-get install linux-headers-$(uname -r)
```

You will need to grab the v4l/dvb source:

```
hg clone http://linuxtv.org/hg/v4l-dvb
```

This will download the source to a new directory in your home folder, change to that directory:

```
cd v4l-dvb
```

Now for the 'make' part, you need to configure the source for compilation:

```
make config
```

You will then be asked  a list of questions on how to configure the source, answer as follows.

```
#
# using defaults found in .config
#
*
* Linux Kernel Configuration
*
*
* Multimedia devices
*
Video For Linux (VIDEO_DEV) [N/m/y/?] n
*
* Digital Video Broadcasting Devices
*
DVB For Linux (DVB) [Y/n/?] y
  DVB Core Support (DVB_CORE) [N/m/y/?] m
    *
    * Supported SAA7146 based PCI Adapters
    *
    *
    * Supported USB Adapters
    *
    Support for various USB DVB devices (DVB_USB) [N/m/?] (NEW) m
      Enable extended debug support for all DVB-USB devices (DVB_USB_DEBUG) [N/y/?] (NEW) n
      AVerMedia AverTV DVB-T USB 2.0 (A800) (DVB_USB_A800) [N/m/?] (NEW) n
      DiBcom USB DVB-T devices (based on the DiB3000M-B) (see help for device list) (DVB_USB_DIBUSB_MB) [N/m/?] (NEW) n
      DiBcom USB DVB-T devices (based on the DiB3000M-C/P) (see help for device list) (DVB_USB_DIBUSB_MC) [N/m/?] (NEW) n
      HanfTek UMT-010 DVB-T USB2.0 support (DVB_USB_UMT_010) [N/m/?] (NEW) n
      Conexant USB2.0 hybrid reference design support (DVB_USB_CXUSB) [N/m/?] (NEW) n
      Nebula Electronics uDigiTV DVB-T USB2.0 support (DVB_USB_DIGITV) [N/m/?] (NEW) n
      TwinhanDTV Alpha/MagicBoxII, DNTV tinyUSB2, Beetle USB2.0 support (DVB_USB_VP7045) [N/m/?] (NEW) n
      TwinhanDTV StarBox and clones DVB-S USB2.0 support (DVB_USB_VP702X) [N/m/?] (NEW) n
      GENPIX 8PSK->USB module support (DVB_USB_GP8PSK) [N/m/?] (NEW) n
      Hauppauge WinTV-NOVA-T usb2 DVB-T USB2.0 support (DVB_USB_NOVA_T_USB2) [N/m/?] (NEW) n
      WideView WT-200U and WT-220U (pen) DVB-T USB2.0 support (Yakumo/Hama/Typhoon/Yuan) (DVB_USB_DTT200U) [N/m/?] (NEW) m
    Technotrend/Hauppauge Nova-USB devices (DVB_TTUSB_BUDGET) [N/m/?] (NEW) n
    Technotrend/Hauppauge USB DEC devices (DVB_TTUSB_DEC) [N/m/?] (NEW) n
    Terratec CinergyT2/qanu USB2 DVB-T receiver (DVB_CINERGYT2) [N/m/?] (NEW) n
    *
    * Supported FlexCopII (B2C2) Adapters
    *
    Technisat/B2C2 FlexCopII(b) and FlexCopIII adapters (DVB_B2C2_FLEXCOP) [N/m/?] (NEW) n
    *
    * Supported BT878 Adapters
    *
    *
    * Supported Pluto2 Adapters
    *
    Pluto2 cards (DVB_PLUTO2) [N/m/?] (NEW) n
    *
    * Supported DVB Frontends
    *
    *
    * Customise DVB Frontends
    *
    *
    * DVB-S (satellite) frontends
    *
    ST STV0299 based (DVB_STV0299) [N/m/?] (NEW) n
    Conexant CX24110 based (DVB_CX24110) [N/m/?] (NEW) n
    Conexant CX24123 based (DVB_CX24123) [N/m/?] (NEW) n
    Philips TDA8083 based (DVB_TDA8083) [N/m/?] (NEW) n
    Zarlink VP310/MT312 based (DVB_MT312) [N/m/?] (NEW) n
    VLSI VES1893 or VES1993 based (DVB_VES1X93) [N/m/?] (NEW) n
    Samsung S5H1420 based (DVB_S5H1420) [N/m/?] (NEW) n
    *
    * DVB-T (terrestrial) frontends
    *
    Spase sp8870 based (DVB_SP8870) [N/m/?] (NEW) n
    Spase sp887x based (DVB_SP887X) [N/m/?] (NEW) n
    Conexant CX22700 based (DVB_CX22700) [N/m/?] (NEW) n
    Conexant cx22702 demodulator (OFDM) (DVB_CX22702) [N/m/?] (NEW) n
    LSI L64781 (DVB_L64781) [N/m/?] (NEW) n
    Philips TDA10045H/TDA10046H based (DVB_TDA1004X) [N/m/?] (NEW) n
    NxtWave Communications NXT6000 based (DVB_NXT6000) [M/?] (NEW) n
    Zarlink MT352 based (DVB_MT352) [M/?] (NEW) m
    Zarlink ZL10353 based (DVB_ZL10353) [N/m/?] (NEW) m
    DiBcom 3000M-B (DVB_DIB3000MB) [N/m/?] (NEW) n
    DiBcom 3000P/M-C (DVB_DIB3000MC) [N/m/?] (NEW) n
    *
    * DVB-C (cable) frontends
    *
    VLSI VES1820 based (DVB_VES1820) [N/m/?] (NEW) n
    Philips TDA10021 based (DVB_TDA10021) [N/m/?] (NEW) n
    ST STV0297 based (DVB_STV0297) [N/m/?] (NEW) n
    *
    * ATSC (North American/Korean Terrestrial/Cable DTV) frontends
    *
    NxtWave Communications NXT2002/NXT2004 based (DVB_NXT200X) [N/m/?] (NEW) n
    Oren OR51211 based (DVB_OR51211) [N/m/?] (NEW) n
    Oren OR51132 based (DVB_OR51132) [N/m/?] (NEW) n
    Broadcom BCM3510 (DVB_BCM3510) [N/m/?] (NEW) n
    LG Electronics LGDT3302/LGDT3303 based (DVB_LGDT330X) [N/m/?] (NEW) n
    *
    * Miscellaneous devices
    *
    LNBP21 SEC controller (DVB_LNBP21) [N/m/?] (NEW) n
    ISL6421 SEC controller (DVB_ISL6421) [N/m/?] (NEW) n
DABUSB driver (USB_DABUSB) [N/m/?] n
```

now we can build the kernel modules

```
make
```

and install them

```
make install
```

after this is done you should reboot the machine, plug in your freecom and you are ready to go. I used kaffine to test my card and it works pefectly. Im getting a strong signal from the SedburyB transmitter, even though Im in South Wales and using a cheapo aerial from B&Q in my loft!! (If anyone has proper frequency files for Wenvoe and Mendip I would be very grateful).

Hope this helps.

---

### Post by MikeyC on 2006-06-02
great post - thanks for the guide... you should put it in the Wiki for future reference!
I'm new to Ubuntu (ex Mandriva user) so still finding my way around.  I've not tried it yet, but it should save a few hours of messing about.

---

### Post by Gaijin on 2006-06-02
I'd like to second the above very helpful, most appreciated!

Also I can confirm that this method also works with the post february 06 revision of the DVB-t as long as you follow the steps below:

The stick will fail to scan if the frequency listed in tranmitter file is not an whole number but an off fraction e.g:
uk-Rowridge
from 489833333 (489.33333mhz) to 490000000 (490mhz)

The files to change are 
/usr/share/doc/dvb-utils/examples/scan/dvb-t uk-Rowridge  [COLOR="Red"](or whatever your transmitter file is called)[/COLOR] [COLOR="SeaGreen"](For use with DVB-utils)[/COLOR]

/home/dave/.kde/share/apps/kaffeine/dvb-t [COLOR="Red"](or whatever your transmitter file is called)[/COLOR] [COLOR="SeaGreen"](For use with Kaffeine)[/COLOR]

Now run the following in a terminal [COLOR="Blue"](as long as you have installed dvb-utils)[/COLOR]
code: scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Rowridge >                  channels.conf

This will generate a channels.conf file that you can place in 
/home/user/.xine
to get xine to (semi) work also


More DVB information here For further information look here:
[http://www.carfax.org.uk/docs/DVB/](http://www.carfax.org.uk/docs/DVB/)

Look here to discover your local transmitter
[http://www.ukfree.tv/txlist.php](http://www.ukfree.tv/txlist.php)

Hope this is of some use!

---

### Post by lost_newbie on 2006-06-05
Hi,

I have managed to get my DVB stick working without touching the command line

I used add/Remove applications and downlaoded Kaffeine which let me see the Video but not hear the sound.  One of the next two things I did sorted everything:
* Downloded the Xine Plugins for Kaffeine
* Went into the lsa Mixer volume control and then selected all the audio devices it found and then selected Edit>Preferences and selected all the options then made sure they were all turned up

Worked for me anyway... and I agree with a post I read somewhere else, for some reason the Dvb picture looks better in Ubuntu than it does in XP

Oh using Dapper 6.06

---

### Post by patwack on 2006-06-07
I got my stick recognised using the howto above but my transmitter isn't listed in the dropdown menu in kaffeine and i have no idea how to create the config file for it.

Any help would be greatly appreciated.

My closest transmitter is Divis (Belfast) [http://www.ukfree.tv/notethat.php?d=IJ287750](http://www.ukfree.tv/notethat.php?d=IJ287750)

Thanks, Paddy

---

### Post by Gaijin on 2006-06-07
Paddy,

I think what you might do is open one of the simple transmitter files as listed above and save a copy of it as Ni-Divis for example, then change the reqd information to suit your transmitter with the info from ukfree (I don't know ifit lists everything you need?)

Looking at the Info for your transmitter it looks as if the modified uk-Rowridge file might work for you anyway as the frequency starts at the same point eg 490mhz, try both approaches.

Additionally for laptop users I have discovered that whereas my DVB-T stick would not function correctly on my laptop before once I added a generic USB-CARDBUS card that also took additional power from the usb 1.1 port the stick would function.
this leads me to believe that the problem may not have just been the slower speed of the port but that the laptop could not supply enough power from the usb port alone, I recommend that anyone with a laptop having problems not solved by the above methods should try connecting the stick via a powered hub or cardbus adaptor as I did...

The card came from Micro Direct and contains an NEC chipset which worked straight out of the box even though it's a generic card costing only £10!
Here's the link for the 2 port version (tested):  [http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=11522&GroupID=0](http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=11522&GroupID=0)
And the 4 port version (untested):  [http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=11521&GroupID=0](http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=11521&GroupID=0)

---

### Post by EnglishRob on 2006-06-08
Hi folks,

I've borrowed a Freecom DVB-T USB stick from my dad to see if it would work before buying one (I previously had a K-World PCI card which would only tune in BBC1).

I've followed the steps above, got the kernel modules compiled and installed and now the usb stick is detected (seems the firmware had to go in /usr/lib/hotplug/firmware/

Anyway, so far so good, USB stick is detected fine, firmware is loaded, but then I go and look for /dev/dvb* and nothing is found.

I've been tearing my hair out all evening (didn't help with my dad saying "It works fine in Windows").  I can't seem to get udev or whatever it is to create the device nodes for the usb device.

Can anyone explain how I can create these device nodes?!?

If it's any help, I'm running Ubuntu Breezy 5.10 with kernel 2.6.12-10-k7 on an Athlon 64 (nForce3 motherboard).

Ta,

Rob

---

### Post by The_Major on 2006-06-09
[QUOTE=EnglishRob]Hi folks,

I've borrowed a Freecom DVB-T USB stick from my dad to see if it would work before buying one (I previously had a K-World PCI card which would only tune in BBC1).

I've followed the steps above, got the kernel modules compiled and installed and now the usb stick is detected (seems the firmware had to go in /usr/lib/hotplug/firmware/

Anyway, so far so good, USB stick is detected fine, firmware is loaded, but then I go and look for /dev/dvb* and nothing is found.

I've been tearing my hair out all evening (didn't help with my dad saying "It works fine in Windows").  I can't seem to get udev or whatever it is to create the device nodes for the usb device.

Can anyone explain how I can create these device nodes?!?

If it's any help, I'm running Ubuntu Breezy 5.10 with kernel 2.6.12-10-k7 on an Athlon 64 (nForce3 motherboard).

Ta,

Rob[/QUOTE]

Did you try placing the firmware in /lib/firmware/2.6.12-10-k7/

What is the output of lsmod, do you see

dvb_usb_dtt200u        
dvb_usb                
dvb_core             
dvb_pll  
12c_core

Have you rebooted with the card plugged in?

---

### Post by EnglishRob on 2006-06-09
[QUOTE=The_Major]Did you try placing the firmware in /lib/firmware/2.6.12-10-k7/
[/QUOTE]

Yep, I did try that but it was complaining that it couldn't find the firmware file.

[QUOTE=The_Major]
What is the output of lsmod, do you see

dvb_usb_dtt200u        
dvb_usb                
dvb_core             
dvb_pll  
12c_core
[/QUOTE]

I recall seeing dvb_usb_dtt200u and dvb_usb in the output of lsmod.  Not sure about the other modules though.
[QUOTE=The_Major]
Have you rebooted with the card plugged in?[/QUOTE]

Yep, rebooted a couple of times.

I'll have a look later.  I have a spare PC which I am planning on using as my MythTV box so I'll reinstall Ubuntu on that (possibly 6.06) and see if I have any more luck with that.

I dare say it's something really simple that I've missed, I just can't work out what :confused: 


Rob

---

### Post by Numpty on 2006-06-13
[QUOTE=The_Major]Strayduck, this is what I had to do to get my freecom working on Dapper....

First fire up a terminal and make sure you are in your home directory, then get the new firmware for the freecom:

[CODE]wget http://thadathil.net:8000/dvb/fw/dvb-usb-wt220u-zl0353-01.fw

This site doesn't appear to be working.  I get either a "404 not found" or a corrupted file if I try to download from the websitesite.  :confused: 

Do you know of another source for this file please?

---

### Post by The_Major on 2006-06-13
[QUOTE=Numpty][QUOTE=The_Major]Strayduck, this is what I had to do to get my freecom working on Dapper....

First fire up a terminal and make sure you are in your home directory, then get the new firmware for the freecom:

```
wget http://thadathil.net:8000/dvb/fw/dvb-usb-wt220u-zl0353-01.fw

This site doesn't appear to be working.  I get either a "404 not found" or a corrupted file if I try to download from the websitesite.  :confused: 

Do you know of another source for this file please?[/QUOTE]

Try here

[CODE]http://thadathil.net:8000/dvb/fw/dvb-usb/dvb-usb-wt220u-zl0353-01.fw
```

---

### Post by Numpty on 2006-06-14
[QUOTE=The_Major]

Try here

```
http://thadathil.net:8000/dvb/fw/dvb-usb/dvb-usb-wt220u-zl0353-01.fw
```[/QUOTE]

Many thanks - that will do nicely.  Stick installed, now to sort out the sound:confused:

---

### Post by zi99y on 2006-06-14
What can I say lads, except, wow!

Thanks so much for putting this info together, I didn't really think I could get this tv stick working in linux when I bought it but not only is it working, but the signal is a hell of a lot stronger than running in windows - as in the picture doesn't stutter every now and again. 

Kaffeine is a little buggy, I wonder if there are any other apps that support DVB?

Even the remote control that comes with it works to some extent, the CH buttons operate the master volume, and the numbers allow channel change, but no channel up/down control - not to worry though.

Thanks again, it's folks like you who make Ubuntu an enjoyable experience :)

---

### Post by dpicker on 2006-06-15
I just bought a freecom usb dvb stick.

I followed your guide and everything worked up until I had to scan for channels. I live under the Lancaster transmitter and it wasnt listed in Kaffeine. So I did a seach and found this: [http://linvdr.org/mailinglists/vdr/2004/10/msg00236.html](http://linvdr.org/mailinglists/vdr/2004/10/msg00236.html)
If you search within the document you will find 

# Granada Television Lancaster
# T 476000000 8MHz 3/4 NONE QAM16 2K 1/32 NONE

So i put that into a new text file, uncommented the main line and saved it as uk-Lancaster in the kaffeine settings directory. Once I did this, I chose uk-Lancaster in Kaffeine and started the search for channels. None showed up. It is plugged into a roof aerial and I find all the channels with good reception in windows.

Could this be because I have the wrong firmware file? I didnt see any error messages in dmesg but March 2006 is written on the stick and I have never seen anyone else with one of that date.

---

### Post by zi99y on 2006-06-15
hey dpicker,

I've checked my stick and it says march 2006 also, so you should have no trouble there.

I might suggest you Gaijin's instructions carefully- update the 2 files with the correct frequency, and then run the scan program. I was puzzling about this for a while before I read his post a few times and then it made sense! :rolleyes:

---

### Post by dpicker on 2006-06-15
I'm sorry but I'm still having trouble :( 

I don't know what the correct frequency is for Lancaster.
It seems that all the frequencies here [http://linvdr.org/mailinglists/vdr/2004/10/msg00236.html](http://linvdr.org/mailinglists/vdr/2004/10/msg00236.html) are wrong and are completely different to the ones listed in the dvb-t folder. And all the correct ones are fractions of a frequency.

Anyway, I get this output from the terminal when I do any scan:

```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 754166670 0 3 0 1 0 0 0
>>> tune to: 754166670:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 754166670:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.
```

Is this normal if you are using the incorrect frequency?

---

### Post by zi99y on 2006-06-15
From that output it looks like you haven't converted the frequencies to whole numbers, as mentioned above. 

You will need to update the file 
```
/usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill 
```
And alter the line that looks like 
```
T 754166670 8MHz 3/4 NONE QAM16 2k 1/32 NONE
```
to something like
```
T 750000000 8MHz 3/4 NONE QAM16 2k 1/32 NONE
```

---

### Post by dpicker on 2006-06-15
I still get the same error in the terminal.

Besides, I was only using WinterHill as an example. I still need the right frequency for the Lancaster transmitter. It seems to be too small for anyone to know it.

---

### Post by zi99y on 2006-06-16
Sorry I must not have read your previous post correctly.

Is this the Lancaster transmitter you mean?

[http://www.ukfree.tv/txdetail.php?a=SD490662](http://www.ukfree.tv/txdetail.php?a=SD490662)

use the link to "Click here for details of the channels transmitted." and then click the "Show Channels" links to find each frequency - but be warned the page doesn't work in Firefox - I used IE on a windows machine but you might be ok in another browser.

Ok I've copied the lancaster page here, in case you have bother

```
Your cables, connectors and aerial may need upgrading to get all the Freeview channels. 

* Power graph Rating Watts 

1  Maximum 200 
 (show channels)
BBC 2 W, BBC NEWS 24, BBC ONE, BBC Radio Cymru, BBC Radio Foyle, BBC Radio nan Gaidheal, BBC Radio Scotland, BBC Radio Ulster, BBC Radio Wales, BBC THREE, BBC TWO, BBCi, CBBC Channel, on C28 (530MHz) 

2  Maximum 200 
 (show channels)
Channel 4, CITV, E4, ITV1, ITV2, ITV3, ITV4, More4, TeleG, Teletext, Teletext Holidays, Teletext on 4, Teletext TV Guide, on C22 (482MHz) 

A  Below average 100 
 BBC Radio 1, BBC Radio 2, BBC Radio 3, BBC Radio 4, Bid TV, five, Heat Radio, price-drop tv, QVC, S4C, S4C~2, on C25 (506MHz) 

B  Maximum 200 
 (show channels)
1Xtra BBC, BBC 6 Music, BBC 7, BBC Asian Network, BBC FOUR, BBC Parliament, BBC Radio 5 Live, BBC Radio 5 Live Sports Extra, BBCi 301-303, Cbeebies, Community, on C32 (562MHz) 

C  Maximum 200 
 (show channels)
E4+1, More4+1, Sky News, Sky Sports News, Sky Three, UKTV History, on C34 (578MHz) 

D  Maximum 200 
 (show channels)
BBC World Service, F2P Games, ftn, Ideal World, ITV Play, Kerrang! Radio, KISS 100, Magic, Oneword, Q Radio, Smash Hits! Radio, smooth fm, The Hits, The Hits Radio, TMF, UKTV Bright Ideas, on C30 (546MHz) 
```

Hope this helps :)

---

### Post by dpicker on 2006-06-16
Ok I fixed the problem. It was my fault, when i was configuring v4l-dvb, I missed the two "m"'s next to:

Zarlink MT352 based (DVB_MT352) [M/?] (NEW) m
Zarlink ZL10353 based (DVB_ZL10353) [N/m/?] (NEW) m

:( Sorry about all that. Thanks for the help anyway. I'm really happy i got it working.

---

### Post by walkerx on 2006-06-25
Having problems trying to get this to install - please can anyone advise where i'm going wrong - this is first time using Ubuntu

followed instructions upto the make section without any problems

make config
```
make -C /home/walkerx/v4l-dvb/v4l config
make[1]: Entering directory `/home/walkerx/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-25-amd64-k8/build
creating symbolic links...
./scripts/make_kconfig.pl /lib/modules/2.6.15-25-amd64-k8/build
Preparing to compile for kernel version 2.6.15
VIDEO_PLANB requires version 2.6.99
VIDEO_VINO requires version 2.6.16
VIDEO_ZORAN_AVS6EYES requires version 2.6.16
VIDEO_ZR36120 requires version 2.6.99
VIDEO_M32R_AR_M64278 requires version 2.6.16
VIDEO_TLV320AIC23B requires version 2.6.16
VIDEO_USBVIDEO requires version 2.6.16
USB_VICAM requires version 2.6.16
USB_IBMCAM requires version 2.6.16
USB_KONICAWC requires version 2.6.16
USB_QUICKCAM_MESSENGER requires version 2.6.16
USB_ET61X251 requires version 2.6.16
USB_ZC0301 requires version 2.6.16
USB_PWC requires version 2.6.16
USB_PWC_DEBUG requires version 2.6.16
RADIO_MIROPCM20: /lib/modules/2.6.15-25-amd64-k8/build/sound/oss/aci.h is missing.

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source is required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

DVB_AV7110_FIRMWARE: Driver is incompatible with  'STANDALONE'
VIDEO_MEYE: Required kernel opt 'SONYPI' is not present
RADIO_ZOLTRIX: Required kernel opt 'ISA' is not present
RADIO_GEMTEK: Required kernel opt 'ISA' is not present
RADIO_RTRACK2: Required kernel opt 'ISA' is not present
VIDEO_M32R_AR: Required kernel opt 'M32R' is not present
VIDEO_M32R_AR_M64278: Required kernel opt 'VIDEO_M32R_AR' is not present
VIDEO_M32R_AR_M64278: Required kernel opt 'PLAT_M32700UT' is not present
RADIO_SF16FMI: Required kernel opt 'ISA' is not present
RADIO_AZTECH: Required kernel opt 'ISA' is not present
RADIO_TERRATEC: Required kernel opt 'ISA' is not present
RADIO_TRUST: Required kernel opt 'ISA' is not present
RADIO_CADET: Required kernel opt 'ISA' is not present
VIDEO_VINO: Required kernel opt 'I2C_ALGO_SGI' is not present
VIDEO_PMS: Required kernel opt 'ISA' is not present
RADIO_MIROPCM20_RDS: Required kernel opt 'RADIO_MIROPCM20' is not present
RADIO_TYPHOON: Required kernel opt 'ISA' is not present
RADIO_SF16FMR2: Required kernel opt 'ISA' is not present
VIDEO_PLANB: Required kernel opt 'PPC_PMAC' is not present
RADIO_RTRACK: Required kernel opt 'ISA' is not present
/lib/modules/2.6.15-25-amd64-k8/build/scripts/kconfig/conf Kconfig
```

running make
```
make -C /home/walkerx/v4l-dvb/v4l
make[1]: Entering directory `/home/walkerx/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-25-amd64-k8/build
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/walkerx/v4l-dvb/v4l'
make[1]: Entering directory `/home/walkerx/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-25-amd64-k8/build
creating symbolic links...
echo srcdir
srcdir
make -C /lib/modules/2.6.15-25-amd64-k8/build SUBDIRS=/home/walkerx/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-25-amd64-k8'
  CC [M]  /home/walkerx/v4l-dvb/v4l/tvmixer.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvbdev.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dmxdev.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb_demux.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb_filter.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb_ca_en50221.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb_frontend.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb_net.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb_ringbuffer.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb_math.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dtt200u.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dtt200u-fe.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb-usb-firmware.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb-usb-init.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb-usb-urb.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb-usb-i2c.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb-usb-dvb.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb-usb-remote.o
  LD [M]  /home/walkerx/v4l-dvb/v4l/dvb-core.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/dvb-pll.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/mt352.o
  CC [M]  /home/walkerx/v4l-dvb/v4l/zl10353.o
  LD [M]  /home/walkerx/v4l-dvb/v4l/dvb-usb.o
  LD [M]  /home/walkerx/v4l-dvb/v4l/dvb-usb-dtt200u.o
  Building modules, stage 2.
  MODPOST
  CC      /home/walkerx/v4l-dvb/v4l/dvb-core.mod.o
  LD [M]  /home/walkerx/v4l-dvb/v4l/dvb-core.ko
  CC      /home/walkerx/v4l-dvb/v4l/dvb-pll.mod.o
  LD [M]  /home/walkerx/v4l-dvb/v4l/dvb-pll.ko
  CC      /home/walkerx/v4l-dvb/v4l/dvb-usb-dtt200u.mod.o
  LD [M]  /home/walkerx/v4l-dvb/v4l/dvb-usb-dtt200u.ko
  CC      /home/walkerx/v4l-dvb/v4l/dvb-usb.mod.o
  LD [M]  /home/walkerx/v4l-dvb/v4l/dvb-usb.ko
  CC      /home/walkerx/v4l-dvb/v4l/mt352.mod.o
  LD [M]  /home/walkerx/v4l-dvb/v4l/mt352.ko
  CC      /home/walkerx/v4l-dvb/v4l/tvmixer.mod.o
  LD [M]  /home/walkerx/v4l-dvb/v4l/tvmixer.ko
  CC      /home/walkerx/v4l-dvb/v4l/zl10353.mod.o
  LD [M]  /home/walkerx/v4l-dvb/v4l/zl10353.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-25-amd64-k8'
make[1]: Leaving directory `/home/walkerx/v4l-dvb/v4l'
```

then got following when done 'make install'

```
make -C /home/walkerx/v4l-dvb/v4l install
make[1]: Entering directory `/home/walkerx/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-25-amd64-k8/build
Stripping debug info from files:

Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/dvb-usb files:
dvb-usb.ko install: cannot remove `/lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/dvb-usb/dvb- usb.ko': Permission denied
dvb-usb-dtt200u.ko install: cannot remove `/lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/dvb- usb/dvb-usb-dtt200u.ko': Permission denied


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/ttpci files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/et61x251 files:
install: cannot create directory `/lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/et61x251': Permission denied
make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/home/walkerx/v4l-dvb/v4l'
make: *** [install] Error 2
```

appreciate any help or advice on this

---

### Post by walkerx on 2006-06-25
I've rebooted and when checking dmesg, i get the following

[   48.516160] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Free com)' in cold state, will try to load a firmware
[   49.392407] dvb-usb: did not find the firmware file. (dvb-usb-wt220u-01.fw) P lease see linux/Documentation/dvb/ for more details on firmware-problems.
[   49.392414] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) erro r while loading driver (-2)
[   49.392423] usbcore: registered new driver dvb_usb_dtt200u

does this mean its installed or not ??

---

### Post by walkerx on 2006-06-25
ok stage further

clicked all the sources i could think of for my kernel

rebooted everything - also renamed the firmware file which now loads in dmesg

re-ran the install stuff, had to use 'sudo make install', and got the following results

```
walkerx@walkerx-ubuntu:~/v4l-dvb$ sudo make install
make -C /home/walkerx/v4l-dvb/v4l install
make[1]: Entering directory `/home/walkerx/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-25-amd64-k8/build
Stripping debug info from files:

Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/dvb-usb files:
dvb-usb.ko dvb-usb-dtt200u.ko

Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/ttpci files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/et61x251 files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/cpia2 files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/cinergyT2 files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/b2c2 files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/frontends files:
dvb-pll.ko mt352.ko zl10353.ko

Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/bt8xx files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/cx88 files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/pluto2 files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/usbvideo files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/sn9c102 files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/dvb-core files:
dvb-core.ko

Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video files:
tvmixer.ko

Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/common files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/em28xx files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/pvrusb2 files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/radio files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/bt8xx files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/cx25840 files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/ttusb-dec files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/dvb/ttusb-budget files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/pwc files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/ovcamchip files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/saa7134 files:


Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/zc0301 files:

/sbin/depmod -a 2.6.15-25-amd64-k8

Installing /lib/modules/2.6.15-25-amd64-k8/kernel/drivers/media/video/ivtv files:

/sbin/depmod -a 2.6.15-25-amd64-k8
make[1]: Leaving directory `/home/walkerx/v4l-dvb/v4l'
```

i'm hoping on reboot it will work - before running the make i tried kaffiene but it didn't see the stick at all

Rebooted and green light on dvb-t is flashing 

lsmod returns the following

dvb_usb_dtt200u        15236  0
dvb_usb                21960  1 dvb_usb_dtt200u
dvb_core               95788  1 dvb_usb
dvb_pll                16772  1 dvb_usb
i2c_core               26048  5 dvb_usb,dvb_pll,i2c_acpi_ec,nvidia,i2c_nforce2
usbcore               146428  8 dvb_usb_dtt200u,dvb_usb,rt2570,usb_storage,usbhi

not sure why listed as nforce2 as using nforce3 mobo

lsusb reports
Bus 003 Device 005: ID 14aa:0222 AVerMedia (again) or C&E

and dmesg reports the following
[  130.510043] usb 3-5: new high speed USB device using ehci_hcd and address 5
[  130.692917] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a firmware
[  130.717380] dvb-usb: downloading firmware from file 'dvb-usb-wt220u-02.fw'
[  130.746647] usbcore: registered new driver dvb_usb_dtt200u

but when scan get an error saying device not found

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-EmleyMoor > channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-EmleyMoor
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1884: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

---

### Post by walkerx on 2006-06-26
got working after downloading a different firmware

[size="1"][   58.008844] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Free com)' in warm state.
[   58.008853] dvb-usb: will use the device's hardware PID filter (table count: 15).
[   58.010277] DVB: registering new adapter (WideView WT-220U PenType Receiver ( Typhoon/Freecom)).
[   58.010373] DVB: registering frontend 0 (WideView USB DVB-T)...
[   58.010433] input: IR-receiver inside an USB DVB receiver as /class/input/inp ut4
[   58.010456] dvb-usb: schedule remote query interval to 300 msecs.
[   58.010459] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) succ essfully initialized and connected.
[   58.010469] usbcore: registered new driver dvb_usb_dtt200u
[   58.061973] idVendor = 0x2001, idProduct = 0x3c00
[   58.062088] INIT bRadio=1[/size]

so depending on which freecom card you have you may need the old firmware like i did

---

### Post by The_Major on 2006-06-26
[QUOTE=walkerx]got working after downloading a different firmware

[size="1"][   58.008844] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Free com)' in warm state.
[   58.008853] dvb-usb: will use the device's hardware PID filter (table count: 15).
[   58.010277] DVB: registering new adapter (WideView WT-220U PenType Receiver ( Typhoon/Freecom)).
[   58.010373] DVB: registering frontend 0 (WideView USB DVB-T)...
[   58.010433] input: IR-receiver inside an USB DVB receiver as /class/input/inp ut4
[   58.010456] dvb-usb: schedule remote query interval to 300 msecs.
[   58.010459] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) succ essfully initialized and connected.
[   58.010469] usbcore: registered new driver dvb_usb_dtt200u
[   58.061973] idVendor = 0x2001, idProduct = 0x3c00
[   58.062088] INIT bRadio=1[/size]

so depending on which freecom card you have you may need the old firmware like i did[/QUOTE]

Glad you got it sorted, when I get five minutes I will do a wiki on this and post a link for the various firmwares.

Your device is a 14aa:0222, mine was a 14aa:022b. It might be helpful if people posted if they have a different device id (output of lsusb, the avermedia line) and which firmware they are using so I can tie it all up.

---

### Post by walkerx on 2006-07-01
Had to  reinstall everything so could get drives working how I wanted with the other operating systems.

One thing I've noticed after getting everything to work is that the lsusb reports diferently

Previous
Bus 003 Device 005: ID 14aa:0222 AVerMedia (again) or C&E

Now
Bus 003 Device 006: ID 14aa:0221 AVerMedia (again) or C&E

I think also that if you put firmware into the firmware folder 1st before running the rest of the setup you have problems.

ie. I put new firmware in the folder, the light would then start flashing on startup, so put in old firmware - this caused it not to flash but still wouldn't load. Ran the rest of the setup and when rebooted it was looked for 02.fw so copied file across and renamed to 02.fw and it worked without problems

So not sure if it is best to set everything up first before copying firmware across and connecting the dvb-t, as I had my dvb-t connected at all times

and yes I agree that picture quality is a lot better under ubuntu.

---

### Post by dpicker on 2006-07-27
Hmmm It has worked fine for me in the past however when i started to compile v4l-dvb this time I got an error:

```
dave@mesh:~/v4l-dvb$ make
make -C /home/dave/v4l-dvb/v4l
make[1]: Entering directory `/home/dave/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-26-386/build
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/dave/v4l-dvb/v4l'
make[1]: Entering directory `/home/dave/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-26-386/build
creating symbolic links...
echo srcdir
srcdir
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/dave/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /home/dave/v4l-dvb/v4l/tvmixer.o
/home/dave/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_ioctl':
/home/dave/v4l-dvb/v4l/tvmixer.c:90: error: storage size of 'va' isn't known
/home/dave/v4l-dvb/v4l/tvmixer.c:126: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/dave/v4l-dvb/v4l/tvmixer.c:126: error: (Each undeclared identifier is reported only once
/home/dave/v4l-dvb/v4l/tvmixer.c:126: error: for each function it appears in.)
/home/dave/v4l-dvb/v4l/tvmixer.c:141: error: 'VIDEO_AUDIO_BASS' undeclared (first use in this function)
/home/dave/v4l-dvb/v4l/tvmixer.c:143: error: 'VIDEO_AUDIO_TREBLE' undeclared (first use in this function)
/home/dave/v4l-dvb/v4l/tvmixer.c:154: error: 'VIDEO_AUDIO_MUTE' undeclared (first use in this function)
/home/dave/v4l-dvb/v4l/tvmixer.c:155: error: 'VIDIOCSAUDIO' undeclared (first use in this function)
/home/dave/v4l-dvb/v4l/tvmixer.c:159: warning: type defaults to 'int' in declaration of '_x'
/home/dave/v4l-dvb/v4l/tvmixer.c:161: warning: type defaults to 'int' in declaration of '_x'
/home/dave/v4l-dvb/v4l/tvmixer.c:161: warning: comparison of distinct pointer types lacks a cast
/home/dave/v4l-dvb/v4l/tvmixer.c:90: warning: unused variable 'va'
/home/dave/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_clients':
/home/dave/v4l-dvb/v4l/tvmixer.c:297: error: storage size of 'va' isn't known
/home/dave/v4l-dvb/v4l/tvmixer.c:343: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/dave/v4l-dvb/v4l/tvmixer.c:345: error: 'VIDEO_AUDIO_VOLUME' undeclared (first use in this function)
/home/dave/v4l-dvb/v4l/tvmixer.c:297: warning: unused variable 'va'
make[3]: *** [/home/dave/v4l-dvb/v4l/tvmixer.o] Error 1
make[2]: *** [_module_/home/dave/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dave/v4l-dvb/v4l'
make: *** [all] Error 2
```

I have done everything the same way I did before. Could this be because the source code has changed?

---

### Post by popper on 2006-07-29
it would appear theres an error in the current source, anyone able to give advace or show the command line to download the last known working version?.
 heres my ppc attempt at compiling reference.

```
make
make -C /home/pop/v4l-dvb/v4l
make[1]: Entering directory `/home/pop/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-23-powerpc/build
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/pop/v4l-dvb/v4l'
make[1]: Entering directory `/home/pop/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-23-powerpc/build
creating symbolic links...
echo srcdir
srcdir
make -C /lib/modules/2.6.15-23-powerpc/build SUBDIRS=/home/pop/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-23-powerpc'
  CC [M]  /home/pop/v4l-dvb/v4l/tvmixer.o
/home/pop/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_ioctl':
/home/pop/v4l-dvb/v4l/tvmixer.c:90: error: storage size of 'va' isn't known
/home/pop/v4l-dvb/v4l/tvmixer.c:126: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/pop/v4l-dvb/v4l/tvmixer.c:126: error: (Each undeclared identifier is reported only once
/home/pop/v4l-dvb/v4l/tvmixer.c:126: error: for each function it appears in.)
/home/pop/v4l-dvb/v4l/tvmixer.c:141: error: 'VIDEO_AUDIO_BASS' undeclared (first use in this function)
/home/pop/v4l-dvb/v4l/tvmixer.c:143: error: 'VIDEO_AUDIO_TREBLE' undeclared (first use in this function)
/home/pop/v4l-dvb/v4l/tvmixer.c:154: error: 'VIDEO_AUDIO_MUTE' undeclared (first use in this function)
/home/pop/v4l-dvb/v4l/tvmixer.c:155: error: 'VIDIOCSAUDIO' undeclared (first use in this function)
/home/pop/v4l-dvb/v4l/tvmixer.c:159: warning: type defaults to 'int' in declaration of '_x'
/home/pop/v4l-dvb/v4l/tvmixer.c:161: warning: type defaults to 'int' in declaration of '_x'
/home/pop/v4l-dvb/v4l/tvmixer.c:161: warning: comparison of distinct pointer types lacks a cast
/home/pop/v4l-dvb/v4l/tvmixer.c:90: warning: unused variable 'va'
/home/pop/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_clients':
/home/pop/v4l-dvb/v4l/tvmixer.c:297: error: storage size of 'va' isn't known
/home/pop/v4l-dvb/v4l/tvmixer.c:343: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/pop/v4l-dvb/v4l/tvmixer.c:345: error: 'VIDEO_AUDIO_VOLUME' undeclared (first use in this function)
/home/pop/v4l-dvb/v4l/tvmixer.c:297: warning: unused variable 'va'
make[3]: *** [/home/pop/v4l-dvb/v4l/tvmixer.o] Error 1
make[2]: *** [_module_/home/pop/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-23-powerpc'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/pop/v4l-dvb/v4l'
make: *** [all] Error 2
```---------------------------
heres the current linuxtv firmwares
[http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)

and heres the current cards it works with, notice how my YUAN card can use one of 2 driver firmwares depending on which one you have, in my case its the dvb-usb-wt220u-01.fw for the YUAN PD300 DVB-T mini not the dvb-usb-dtt200u-01.fw Yuan DVB2GO UB300, you cant just rename them and swap them about as (if im reading the older posts right) the impresssion seems to be above.
[http://www.linuxtv.org/wiki/index.php/DVB_USB#WideView.2FYakumo.2FHama.2FTyphoon.2FYuan_Boxes_and_Pens](http://www.linuxtv.org/wiki/index.php/DVB_USB#WideView.2FYakumo.2FHama.2FTyphoon.2FYuan_Boxes_and_Pens)

---

### Post by jm2003uk on 2006-07-29
I've got the same problem on my laptop. Followed the guide on the first page and everything has gone fine until i run the 'make' command. Here's what i get:

make
make -C /home/james/v4l-dvb/v4l
make[1]: Entering directory `/home/james/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-23-386/build
creating symbolic links...
echo srcdir
srcdir
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/james/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /home/james/v4l-dvb/v4l/tvmixer.o
/home/james/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_ioctl':
/home/james/v4l-dvb/v4l/tvmixer.c:90: error: storage size of 'va' isn't known
/home/james/v4l-dvb/v4l/tvmixer.c:126: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/james/v4l-dvb/v4l/tvmixer.c:126: error: (Each undeclared identifier is reported only once
/home/james/v4l-dvb/v4l/tvmixer.c:126: error: for each function it appears in.)
/home/james/v4l-dvb/v4l/tvmixer.c:141: error: 'VIDEO_AUDIO_BASS' undeclared (first use in this function)
/home/james/v4l-dvb/v4l/tvmixer.c:143: error: 'VIDEO_AUDIO_TREBLE' undeclared (first use in this function)
/home/james/v4l-dvb/v4l/tvmixer.c:154: error: 'VIDEO_AUDIO_MUTE' undeclared (first use in this function)
/home/james/v4l-dvb/v4l/tvmixer.c:155: error: 'VIDIOCSAUDIO' undeclared (first use in this function)
/home/james/v4l-dvb/v4l/tvmixer.c:159: warning: type defaults to 'int' in declaration of '_x'
/home/james/v4l-dvb/v4l/tvmixer.c:161: warning: type defaults to 'int' in declaration of '_x'
/home/james/v4l-dvb/v4l/tvmixer.c:161: warning: comparison of distinct pointer types lacks a cast
/home/james/v4l-dvb/v4l/tvmixer.c:90: warning: unused variable 'va'
/home/james/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_clients':
/home/james/v4l-dvb/v4l/tvmixer.c:297: error: storage size of 'va' isn't known
/home/james/v4l-dvb/v4l/tvmixer.c:343: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/james/v4l-dvb/v4l/tvmixer.c:345: error: 'VIDEO_AUDIO_VOLUME' undeclared (first use in this function)
/home/james/v4l-dvb/v4l/tvmixer.c:297: warning: unused variable 'va'
make[3]: *** [/home/james/v4l-dvb/v4l/tvmixer.o] Error 1
make[2]: *** [_module_/home/james/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/james/v4l-dvb/v4l'
make: *** [all] Error 2

---

### Post by popper on 2006-07-29
hmmm, we need some help here 8(
i may be wrong (as im not that good at this stuff) but it seems that perhaps these sources need 2.6.16 rather than what we appear to be using.

i went and got the last two snapshots from here [http://www.linuxtv.org/downloads/snapshots/](http://www.linuxtv.org/downloads/snapshots/)
made a test dir and unpacked v4l-dvb-20060715.tar.gz there.

ran **make clean** to be sure and this came back

```
"
~/test$ make clean
make -C /home/pop/test/v4l clean
make[1]: Entering directory `/home/pop/test/v4l'
No version yet.
scripts/make_makefile.pl /lib/modules/2.6.15-26-386/build
Creating Makefile.media.
Preparing to compile for kernel version 2.6.15
VIDEO_PLANB requires version 2.6.99
VIDEO_VINO requires version 2.6.16
VIDEO_ZORAN_AVS6EYES requires version 2.6.16
VIDEO_ZR36120 requires version 2.6.99
VIDEO_M32R_AR_M64278 requires version 2.6.16
VIDEO_TLV320AIC23B requires version 2.6.16
VIDEO_USBVIDEO requires version 2.6.16
USB_VICAM requires version 2.6.16
USB_IBMCAM requires version 2.6.16
USB_KONICAWC requires version 2.6.16
USB_QUICKCAM_MESSENGER requires version 2.6.16
USB_ET61X251 requires version 2.6.16
USB_ZC0301 requires version 2.6.16
USB_PWC requires version 2.6.16
USB_PWC_DEBUG requires version 2.6.16
RADIO_MIROPCM20: /lib/modules/2.6.15-26-386/build/sound/oss/aci.h is missing.

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source is required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at [http://kernel.org](http://kernel.org).
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

DVB_AV7110_FIRMWARE: Driver is incompatible with  'STANDALONE'
VIDEO_M32R_AR: Required kernel opt 'M32R' is not present
VIDEO_M32R_AR_M64278: Required kernel opt 'VIDEO_M32R_AR' is not present
VIDEO_M32R_AR_M64278: Required kernel opt 'PLAT_M32700UT' is not present
VIDEO_VINO: Required kernel opt 'I2C_ALGO_SGI' is not present
RADIO_MIROPCM20_RDS: Required kernel opt 'RADIO_MIROPCM20' is not present
VIDEO_PLANB: Required kernel opt 'PPC_PMAC' is not present
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/pop/test/v4l'
make[1]: Entering directory `/home/pop/test/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-26-386/build
rm -f *~ *.o *.ko .*.o.cmd .*.ko.cmd *.mod.c av7110_firm.h fdump \
                ivtv-svnversion.h config-compat.h
make[1]: Leaving directory `/home/pop/test/v4l'
"
---------------------------
```
does this mean we now need to learn how to compile and install a new 2.6.16 kernel just to use and compile to a usable state these sources?.

the above came from the vmware 606 386 iso i setup to run beside the PPC mac im also trying ot get going with this dvb so ill need to make a ppc kernel as well and install that there too i imagine id it is a case of we need to use 2.6.16 just to make these DVB-T sticks work with ubuntu?.

please someone tell me we dont or give us a step by step pritty please 8)

---

### Post by popper on 2006-07-31
hmm noone know the answer to our problem?, 


did anyone try setting up a vmware 4gig image from scratch
and got the DVB-T cards working with that following the OP instuctions to the letter ?.

should we go and try another linux distro , instead?.

---

### Post by popper on 2006-08-02
> **popper said:**
> hmm noone know the answer to our problem?, 


did anyone try setting up a vmware 4gig image from scratch
and got the DVB-T cards working with that following the OP instuctions to the letter ?.

should we go and try another linux distro , instead?.

i thought id keep trying to work this out and it appears that they have just now sorted out a quick fix so as to make it compile now 
[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
"description	MASTER v4l-dvb development repository
owner	Mauro Carvalho Chehab
changes
4 hours ago	Trent Piepho 	Quick fix to make building work again	tree	b66c01bd2d00
4 hours ago	Trent Piepho 	Fix minor errors in build files	tree	7862f53d3562"

i still have a problem though in that it seems theres a problem with the replacment for the old hotplug stuff (Udev is it?) in that while it can see my DVB-T usb card, it doesnt seem to be trying to coldboot/load any firmware.

is it because of a problem with ubuntu 606 or a problem with the VMWare workstation build 13124 ?.

```
"
cd d4l-dvb
make install
cut upto the error
Installing /lib/modules/2.6.15-26-386/kernel/drivers/media/video/saa7134 files:
saa7134.ko saa7134-empress.ko saa7134-alsa.ko saa7134-oss.ko

Installing /lib/modules/2.6.15-26-386/kernel/drivers/media/video/zc0301 files:
zc0301.ko
/sbin/depmod -a 2.6.15-26-386
WARNING: Module /lib/modules/2.6.15-26-386/kernel/drivers/media/dvb/bt8xx/dst_ca.ko ignored, due to loop
WARNING: Loop detected: /lib/modules/2.6.15-26-386/kernel/drivers/media/dvb/bt8xx/dst.ko needs dst_ca.ko which needs dst.ko again!
WARNING: Module /lib/modules/2.6.15-26-386/kernel/drivers/media/dvb/bt8xx/dst.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.15-26-386/kernel/drivers/media/dvb/bt8xx/dvb-bt8xx.ko ignored, due to loop

Installing /lib/modules/2.6.15-26-386/kernel/drivers/media/video/ivtv files:

/sbin/depmod -a 2.6.15-26-386
WARNING: Module /lib/modules/2.6.15-26-386/kernel/drivers/media/dvb/bt8xx/dst_ca.ko ignored, due to loop
WARNING: Loop detected: /lib/modules/2.6.15-26-386/kernel/drivers/media/dvb/bt8xx/dst.ko needs dst_ca.ko which needs dst.ko again!
WARNING: Module /lib/modules/2.6.15-26-386/kernel/drivers/media/dvb/bt8xx/dst.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.15-26-386/kernel/drivers/media/dvb/bt8xx/dvb-bt8xx.ko ignored, due to loop
make[1]: Leaving directory `/home/pop/v4l-dvb/v4l'
root@pop-desktop:/home/pop/v4l-dvb#"

whats this loop and does it refer to the loop device not being in the 606 iso? , i forget how to check just now lol.

"
lsmod
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
vmhgfs                 42028  4
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
ipv6                  265728  6
af_packet              22920  2
snd_ens1371            24672  1
gameport               15496  1 snd_ens1371
snd_rawmidi            25504  1 snd_ens1371
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         93088  1 snd_ens1371
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
tsdev                   8000  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
snd                    55268  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  1 snd_pcm
floppy                 62148  0
snd_ac97_bus            2304  1 snd_ac97_codec
psmouse                36100  0
serio_raw               7300  0
rtc                    13492  0
pcnet32                30084  0
mii                     5888  1 pcnet32
i2c_piix4               9104  0
i2c_core               21904  2 i2c_acpi_ec,i2c_piix4
intel_agp              22940  1
shpchp                 45632  0
agpgart                34888  1 intel_agp
pci_hotplug            29236  1 shpchp
evdev                   9856  1
sg                     37920  0
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  2 uhci_hcd
sd_mod                 19984  3
BusLogic               78868  4
scsi_mod              139496  3 sg,sd_mod,BusLogic
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
root@pop-desktop:/home/pop/v4l-dvb#"

" lsusb -v

Bus 001 Device 003: ID 14aa:0220 AVerMedia (again) or C&E
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x14aa AVerMedia (again) or C&E
  idProduct          0x0220
  bcdDevice            0.00
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          171
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-26-386 uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:07.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x38
  PortPwrCtrlMask    0xc1
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered
root@pop-desktop:/home/pop/v4l-dvb#"

unluged the usb yuan DVB-T mini twice and get this from  dmesg
(works with the yakumo bda drivers in windows(wideviewer wt-220u)
"
snip most of it
[17179661.176000] Bluetooth: RFCOMM ver 1.7
[17181769.368000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17193489.340000] usb 1-1: USB disconnect, address 2
[17194774.204000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17198183.288000] usb 1-1: USB disconnect, address 3
[17198186.168000] usb 1-1: new full speed USB device using uhci_hcd and address 4
root@pop-desktop:/home/pop/v4l-dvb#"
```

i do intend to move this Ubuntu 606 over to a real cpu after iv got the DVB-T vlc, and a few other things installed and working but for know i have to work within the VMware WS.

is anyone reading this thread that can help give some advice please?, i really dont want to have to setup a windows machine just for this DVB tv lan serving is i can help it.

---

### Post by popper on 2006-08-06
the odd thing i cant seem to get my head around is i should be seeing at least this
cut from someone elses output
"dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Free com)' in cold state, will try to load a firmware
[ 49.392407] dvb-usb: did not find the firmware file. (dvb-usb-wt220u-01.fw) P lease see linux/Documentation/dvb/ for more details on firmware-problems.
[ 49.392414] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) erro r while loading driver (-2)
[ 49.392423] usbcore: registered new driver dvb_usb_dtt200u"

but i cant even get that far, why is it that when i plug the yuan dvb2go mini into the usb it doesnt even try and load something?.

the card does work but only if i boot to windows, plug the yuan in so as to load the working bda driver (not the non bda driver that came witht he card) i use the yakumo windows bda driver to good effect [http://www.yakumodriver.wz.cz/download.html](http://www.yakumodriver.wz.cz/download.html)


once thats loaded i can then take any working linux livecd such as kanotix 2006 easter-rc4 cd and as long as i dont unplug the dvb-T stick it will work and tune just fine so im at a loss as to were i go now, is the linuxtv code broken and wont load the driver or am i missing something so simple that people havent posted about it for me to read?.

how do i make the ubuntu at least try and load the firmware into the card **from cold **so the thing works as it did when warm booting after windows loaded the firmware ?, can anyone help guide me please.

the one thing that seems strange is that from cold the lsusb gives 'ID 14aa:0220 AVerMedia (again) or C&E' so it seems that once the firmware is loaded it changes it to 0221, alas i cant get it to even try and load to that point without booting wondows every time 8(

heres the output from the warm booted (ie got windows to load the firmware first) kanotix livecd
lsusb
```
"
Bus 001 Device 003: ID 14aa:0221 AVerMedia (again) or C&E 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x14aa AVerMedia (again) or C&E
  idProduct          0x0221 
  bcdDevice            5.21
  iManufacturer           1 Digital TV Receiver
  iProduct                2 Digital TV Receiver
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           64
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      48
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.16.16-kanotix-1 ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:03.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0000
   Port 5: 0000.0503 highspeed power enable connect
   Port 6: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 003 Device 003: ID 05dc:0080 Lexar Media, Inc. Jumpdrive Secure 64MB
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05dc Lexar Media, Inc.
  idProduct          0x0080 Jumpdrive Secure 64MB
  bcdDevice            0.01
  iManufacturer           1 LEXR PLUG DRIVE
  iProduct                1 LEXR PLUG DRIVE
  iSerial                 2 L304320525100317AA  0000000000000000000000000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               90mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              1 LEXR PLUG DRIVE
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered

Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x9254 Hub
  bcdDevice            3.12
  iManufacturer           1 ALCOR
  iProduct                2 Generic USB Hub
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
  bPwrOn2PwrGood       22 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0103 power enable connect
   Port 4: 0000.0303 lowspeed power enable connect
Device Status:     0x0001
  Self Powered

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.16.16-kanotix-1 ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:03.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
   Port 3: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 003 Device 004: ID 1241:1111 Belkin Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1241 Belkin
  idProduct          0x1111 Mouse
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               8
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.16.16-kanotix-1 ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:03.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled "
-----------------------------
```

---

### Post by popper on 2006-08-06
```
dmesg
"
>CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
Checking 'hlt' instruction... OK.
checking if image is initramfs...it isn't (no cpio magic); looks like an initrd
Freeing initrd memory: 1407k freed
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
CPU0: AMD Athlon(tm) XP 2400+ stepping 01
Total of 1 processors activated (4004.54 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Brought up 1 CPUs
migration_cost=0
NET: Registered protocol family 16
EISA bus registered
ACPI: bus type pci registered
PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
PCI: Using configuration type 1
ACPI: Subsystem revision 20060127
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Probing PCI hardware (bus 00)
Uncovering SIS963 that hid as a SIS503 (compatible=0)
Boot video device is 0000:01:00.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: Power Resource [URP1] (off)
ACPI: Power Resource [URP2] (off)
ACPI: Power Resource [FDDP] (off)
ACPI: Power Resource [LPTP] (off)
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 11 devices
Generic PHY: Registered new driver
SCSI subsystem initialized
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
TC classifier action (bugs to [email]netdev@vger.kernel.org[/email] cc [email]hadi@cyberus.ca[/email])
PCI: Bridge: 0000:00:01.0
  IO window: disabled.
  MEM window: cdd00000-cfefffff
  PREFETCH window: c5a00000-cdbfffff
Machine check exception polling timer started.
highmem bounce pool size: 64 pages
Total HugeTLB memory allocated, 0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Squashfs 2.2-r2 (released 2005/09/08) (C) 2002-2005 Phillip Lougher
SGI XFS with ACLs, security attributes, realtime, no debug enabled
SGI XFS Quota Management subsystem
Initializing Cryptographic API
io scheduler noop registered
io scheduler anticipatory registered (default)
io scheduler deadline registered
io scheduler cfq registered
vesafb: framebuffer at 0xc8000000, mapped to 0xf8880000, using 6144k, total 65536k
vesafb: mode is 1024x768x16, linelength=2048, pages=1
vesafb: protected mode interface info at c000:e4c0
vesafb: scrolling: redraw
vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
bootsplash 3.1.6-2004/03/31: looking for picture...<6>...no good signature found.
Console: switching to colour frame buffer device 128x48
fb0: VESA VGA frame buffer device
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Real Time Clock Driver v1.12ac
PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
PNP: PS/2 controller doesn't have AUX irq; using default 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
RAMDISK driver initialized: 16 RAM disks of 100000K size 1024 blocksize
loop: loaded (max 8 devices)
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:02.5
SIS5513: chipset revision 0
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
    ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: HDS722580VLAT20, ATA DISK drive
hdb: Maxtor 6Y080L0, ATA DISK drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdc: HDS728080PLAT20, ATA DISK drive
hdd: PHILIPS PBDV1640P, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 512KiB
hda: 160836480 sectors (82348 MB) w/1794KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 hda: hda1 hda2 hda3
hdb: max request size: 128KiB
hdb: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
hdb: cache flushes supported
 hdb: hdb1 hdb3
hdc: max request size: 512KiB
hdc: 160836480 sectors (82348 MB) w/1719KiB Cache, CHS=16383/255/63, UDMA(133)
hdc: cache flushes supported
 hdc: hdc1 hdc2 hdc4
hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
3ware Storage Controller device driver for Linux v1.26.02.001.
3ware 9000 Storage Controller device driver for Linux v2.26.02.007.
libata version 1.20 loaded.
mice: PS/2 mouse device common for all mice
md: linear personality registered for level -1
md: raid0 personality registered for level 0
md: raid1 personality registered for level 1
md: raid10 personality registered for level 10
md: raid5 personality registered for level 5
md: raid4 personality registered for level 4
raid5: automatically using best checksumming function: pIII_sse
   pIII_sse  :  4443.000 MB/sec
raid5: using function: pIII_sse (4443.000 MB/sec)
raid6: int32x1    755 MB/s
raid6: int32x2    683 MB/s
raid6: int32x4    611 MB/s
raid6: int32x8    547 MB/s
raid6: mmxx1     1558 MB/s
raid6: mmxx2     2501 MB/s
raid6: sse1x1    1511 MB/s
raid6: sse1x2    2473 MB/s
raid6: using algorithm sse1x2 (2473 MB/s)
md: raid6 personality registered for level 6
md: multipath personality registered for level -4
md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
md: bitmap version 4.39
device-mapper: 4.5.0-ioctl (2005-10-04) initialised: [email]dm-devel@redhat.com[/email]
device-mapper: dm-multipath version 1.0.4 loaded
device-mapper: dm-round-robin version 1.0.0 loaded
device-mapper: dm-emc version 0.0.3 loaded
MC: drivers/edac/edac_mc.c version edac_mc  Ver: 2.0.0 May 13 2006
EISA: Probing bus 0 at eisa.0
EISA: Detected 0 cards.
NET: Registered protocol family 2
input: AT Translated Set 2 keyboard as /class/input/input0
IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
TCP established hash table entries: 262144 (order: 9, 3145728 bytes)
TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
TCP: Hash tables configured (established 262144 bind 65536)
TCP reno registered
NET: Registered protocol family 1
Using IPI Shortcut mode
md: Autodetecting RAID arrays.
md: autorun ...
md: ... autorun DONE.
RAMDISK: Compressed image found at block 0
VFS: Mounted root (ext2 filesystem).
NTFS driver 2.1.26 [Flags: R/W MODULE].
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
Freeing unused kernel memory: 320k freed
Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected SiS 746 chipset
agpgart: AGP aperture is 64M @ 0xd0000000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 169
ehci_hcd 0000:00:03.2: EHCI Host Controller
PCI: cache line size of 64 is not supported by device 0000:00:03.2
ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:03.2: irq 169, io mem 0xcffff000
ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 6 ports detected
r8169 Gigabit Ethernet driver 2.2LK loaded
ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 177
eth0: Identified chip type is 'RTL8169s/8110s'.
eth0: RTL8169 at 0xf8850f00, 00:40:f4:96:fa:5c, IRQ 177
ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 185
ohci_hcd 0000:00:03.0: OHCI Host Controller
ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
ohci_hcd 0000:00:03.0: irq 185, io mem 0xcfffd000
input: PC Speaker as /class/input/input1
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
usb 1-5: new high speed USB device using ehci_hcd and address 3
ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 193
ohci_hcd 0000:00:03.1: OHCI Host Controller
ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
ohci_hcd 0000:00:03.1: irq 193, io mem 0xcfffe000
usb 1-5: configuration #1 chosen from 1 choice
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 3 ports detected
usb 3-2: new full speed USB device using ohci_hcd and address 2
usb 3-2: configuration #1 chosen from 1 choice
hub 3-2:1.0: USB hub found
hub 3-2:1.0: 4 ports detected
sis900.c: v1.08.09 Sep. 19 2005
ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 177
0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
0000:00:04.0: Using transceiver found at address 1 as default
eth1: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 177, 00:0b:6a:13:dd:03.
usb 3-2.3: new full speed USB device using ohci_hcd and address 3
usb 3-2.3: configuration #1 chosen from 1 choice
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing disabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
usb 3-2.4: new low speed USB device using ohci_hcd and address 4
usb 3-2.4: configuration #1 chosen from 1 choice
ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 201
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
ieee80211_crypt: registered algorithm 'NULL'
ieee80211-r8180: loading with WEP enabled.
intel8x0_measure_ac97_clock: measured 58893 usecs
intel8x0: clocking to 48000
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
Copyright (c) 2004-2005, Andrea Merello
rtl8180: Initializing module
rtl8180: Wireless extensions version 19
rtl8180: Initializing proc filesystem
rtl8180: Configuring chip resources
ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 209
rtl8180: Memory mapped space @ 0xcfffbe00 
rtl8180: Hardware frame sequence numbers disabled
rtl8180: MAC controller is a RTL8180 (v. F)
rtl8180: This is a PCI NIC
rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
rtl8180: Card MAC address is 00:40:f4:a3:e2:8c
rtl8180: EEPROM version 102
rtl8180: RfParam: 5
rtl8180: Card reports RF frontend by Philips.
rtl8180: OK! Philips SA2400 radio chipset is supported.
rtl8180: Analog PHY found
rtl8180: Energy threshold: b
rtl8180: PAPE from CONFIG2: 1
rtl8180: Antenna A is default antenna
rtl8180: Antenna diversity is disabled
rtl8180: Carrier sense 1
rtl8180: 40-bit WEP is NOT supported in hardware
rtl8180: 104-bit WEP is NOT supported in hardware
rtl8180: IRQ 209
rtl8180: Driver probe completed

Linux video capture interface: v1.00
bttv: driver version 0.9.16 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 217
bttv0: Bt878 (rev 17) at 0000:00:0d.0, irq: 217, latency: 32, mmio: 0xcdcfe000
bttv0: detected: AVerMedia TVCapture 98 [card=13], PCI subsystem ID is 1461:0004
bttv0: using: AVerMedia TVCapture 98 [card=13,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00f4fff3 [init]
bttv0: Hauppauge/Voodoo msp34xx: reset line init [11]
bttv0: Avermedia eeprom[0x4031]: tuner=5 radio:no remote control:yes
bttv0: using tuner=5
bttv0: i2c: checking for MSP34xx @ 0x80... not found
bttv0: i2c: checking for MSP34xx (alternate address) @ 0x88... not found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
dvb-usb: will use the device's hardware PID filter (table count: 15).
DVB: registering new adapter (WideView WT-220U PenType Receiver (Typhoon/Freecom)).
DVB: registering frontend 0 (WideView USB DVB-T)...
input: IR-receiver inside an USB DVB receiver as /class/input/input2
dvb-usb: schedule remote query interval to 300 msecs.
dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
dvb-usb: will use the device's hardware PID filter (table count: 15).
DVB: registering new adapter (WideView WT-220U PenType Receiver (Typhoon/Freecom)).
DVB: registering frontend 1 (WideView USB DVB-T)...
input: IR-receiver inside an USB DVB receiver as /class/input/input3
dvb-usb: schedule remote query interval to 300 msecs.
dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
usbcore: registered new driver dvb_usb_dtt200u
bttv0: i2c: checking for TDA9887 @ 0x86... not found
tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: PLL: 28636363 => 35468950 .. ok
input: bttv IR (card=13) as /class/input/input4
bttv-input: bttv IR (card=13) detected at pci-0000:00:0d.0/ir0
usbcore: registered new driver hiddev
input: HID 1241:1111 as /class/input/input5
input: USB HID v1.00 Mouse [HID 1241:1111] on usb-0000:00:03.1-2.4
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
bt878: AUDIO driver version 0.0.0 loaded
bt878: Bt878 AUDIO function found (0).
ACPI: PCI Interrupt 0000:00:0d.1[A] -> GSI 17 (level, low) -> IRQ 217
bt878_probe: card id=[0x41461], Unknown card.
Exiting..
ACPI: PCI interrupt for device 0000:00:0d.1 disabled
bt878: probe of 0000:00:0d.1 failed with error -22
usbcore: registered new driver libusual
ts: Compaq touchscreen protocol output
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
dvb-usb: recv bulk message failed: -110
Capability LSM initialized
  Vendor: LEXAR     Model: DIGITAL FILM      Rev: /W1.
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sda: 125952 512-byte hdwr sectors (64 MB)
sda: Write Protect is off
sda: Mode Sense: 23 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 125952 512-byte hdwr sectors (64 MB)
sda: Write Protect is off
sda: Mode Sense: 23 00 00 00
sda: assuming drive cache: write through
 sda: sda1
sd 0:0:0:0: Attached scsi removable disk sda
sd 0:0:0:0: Attached scsi generic sg0 type 0
usb-storage: device scan complete
wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
ACPI: Power Button (FF) [PWRF]
ACPI: Power Button (CM) [PWRB]
Using specific hotkey driver
fuse init (API version 7.6)
NET: Registered protocol family 17
r8169: eth0: link down
APIC error on CPU0: 00(02)
eth1: Media Link On 100mbps full-duplex 
eth1: Media Link On 100mbps full-duplex  "
```

---

### Post by popper on 2006-08-06
lsmod
```
"
Module                  Size  Used by
cryptoloop              3968  0 
aes                    33192  0 
af_packet              18312  0 
fuse                   33296  0 
psmouse                34952  0 
pcmcia                 31676  0 
yenta_socket           23180  0 
rsrc_nonstatic         11648  1 yenta_socket
pcmcia_core            34584  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  14084  0 
thermal                11400  0 
processor              19176  1 thermal
fan                     4228  0 
container               4096  0 
button                  5776  0 
battery                 8452  0 
ac                      4356  0 
capability              4232  0 
commoncap               6144  1 capability
usb_storage            65216  0 
tsdev                   6976  0 
libusual               14864  1 usb_storage
bt878                   9660  0 
usbhid                 45920  0 
tuner                  50220  0 
tvaudio                22300  0 
dvb_usb_dtt200u         8708  0 
dvb_usb                16136  1 dvb_usb_dtt200u
dvb_core               73792  1 dvb_usb
dvb_pll                10372  1 dvb_usb
parport_pc             36208  0 
parport                31560  1 parport_pc
bttv                  163132  1 bt878
video_buf              17796  1 bttv
compat_ioctl32          2048  1 bttv
v4l2_common             7552  2 tuner,bttv
btcx_risc               5000  1 bttv
ir_common               8964  1 bttv
tveeprom               13968  1 bttv
videodev                8192  1 bttv
r8180                  57740  0 
ieee80211_r8180        32132  1 r8180
ieee80211_crypt_r8180     5252  1 ieee80211_r8180
shpchp                 40544  0 
pci_hotplug            24772  1 shpchp
snd_intel8x0           28828  1 
snd_ac97_codec         87200  1 snd_intel8x0
snd_ac97_bus            2944  1 snd_ac97_codec
snd_pcm_oss            45728  0 
snd_mixer_oss          15616  1 snd_pcm_oss
snd_pcm                73604  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              20100  1 snd_pcm
snd                    44384  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
8250_pnp                9216  0 
8250                   21812  1 8250_pnp
serial_core            17536  1 8250
sis900                 20608  0 
evdev                   8448  2 
pcspkr                  3588  0 
analog                 10656  0 
gameport               12168  1 analog
ohci_hcd               18948  0 
r8169                  25480  0 
ehci_hcd               29320  0 
usbcore               107936  8 usb_storage,libusual,usbhid,dvb_usb_dtt200u,dvb_usb,ohci_hcd,ehci_hcd
soundcore               8160  1 snd
snd_page_alloc          8840  2 snd_intel8x0,snd_pcm
mii                     5504  1 sis900
sis_agp                 7044  1 
agpgart                26316  1 sis_agp
ntfs                  216332  0
```

---

### Post by walkerx on 2006-08-06
firstly follow the freecom installation thread

ensure you have the firmware downloaded 
ensure you have the kernel sources ,and any other stuff you need

all these instructions are in the installation help thread and should get it working

---

### Post by fogster74 on 2006-08-06
Hey guys,

Have been following this post and am still trying to get my Freecom stick to work. I'm really new to Ubuntu (running 6.06)  but am doing my best to hang in there - the system is now (nearly) usable and to have my DVB stick working would be then icing on the cake.

I actually installed Kaffeine and it found ym USB stick without doing anything - but the scan button just went from "0%" to "100%" with no channels found. I then downloaded the new firmware - from that point on, on booting the green led on the stick stayed off and I got an RNG failure in my dmesg file. I read the dmesg file, trying to make sense of it, and realised it was looking for dvb-usb-wt220u-01.fw, not dvb-usb-wt220u-zl0353-01.fw, so I renamed the new firmware file as dvb-usb-wt220u-01.fw

On reboot the green light started flashing (hurrah!) - these are the relevant contents of dmesg / lsusb / lsmod output:

lsusb:
```

Bus 004 Device 002: ID 14aa:0222 AVerMedia (again) or C&E
```


lsmod:
```

usbcore               130692  9 ndiswrapper,
                                dvb_usb_dtt200u,
                                dvb_usb,
                                usbhid,
                                usblp,
                                hci_usb,
                                ehci_hcd,
                                uhci_hcd
```


dmesg:
```

[17179586.868000] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a firmware
[17179587.560000] dvb-usb: downloading firmware from file 'dvb-usb-wt220u-01.fw' to the 'Cypress FX2'
[17179587.724000] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[17179587.724000] usbcore: registered new driver dvb_usb_dtt200u
```


So it seems that the stick is being initialised and the firmware is loading

A few comments
Running "make" I get:

```
make -C /home/steve/v4l-dvb/v4l
make[1]: Entering directory `/home/steve/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-26-386/build
creating symbolic links...
echo srcdir
srcdir
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/steve/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /home/steve/v4l-dvb/v4l/tvmixer.o
/home/steve/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_ioctl':
/home/steve/v4l-dvb/v4l/tvmixer.c:90: error: storage size of 'va' isn't known
/home/steve/v4l-dvb/v4l/tvmixer.c:126: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/steve/v4l-dvb/v4l/tvmixer.c:126: error: (Each undeclared identifier is reported only once
/home/steve/v4l-dvb/v4l/tvmixer.c:126: error: for each function it appears in.)
/home/steve/v4l-dvb/v4l/tvmixer.c:141: error: 'VIDEO_AUDIO_BASS' undeclared (first use in this function)
/home/steve/v4l-dvb/v4l/tvmixer.c:143: error: 'VIDEO_AUDIO_TREBLE' undeclared (first use in this function)
/home/steve/v4l-dvb/v4l/tvmixer.c:154: error: 'VIDEO_AUDIO_MUTE' undeclared (first use in this function)
/home/steve/v4l-dvb/v4l/tvmixer.c:155: error: 'VIDIOCSAUDIO' undeclared (first use in this function)
/home/steve/v4l-dvb/v4l/tvmixer.c:159: warning: type defaults to 'int' in declaration of '_x'
/home/steve/v4l-dvb/v4l/tvmixer.c:161: warning: type defaults to 'int' in declaration of '_x'
/home/steve/v4l-dvb/v4l/tvmixer.c:161: warning: comparison of distinct pointer types lacks a cast
/home/steve/v4l-dvb/v4l/tvmixer.c:90: warning: unused variable 'va'
/home/steve/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_clients':
/home/steve/v4l-dvb/v4l/tvmixer.c:297: error: storage size of 'va' isn't known
/home/steve/v4l-dvb/v4l/tvmixer.c:343: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/steve/v4l-dvb/v4l/tvmixer.c:345: error: 'VIDEO_AUDIO_VOLUME' undeclared (first use in this function)
/home/steve/v4l-dvb/v4l/tvmixer.c:297: warning: unused variable 'va'
make[3]: *** [/home/steve/v4l-dvb/v4l/tvmixer.o] Error 1
make[2]: *** [_module_/home/steve/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/steve/v4l-dvb/v4l'
make: *** [all] Error 2
```

Finally, on running "make install", if I don't run this as root (i.e. sudo make install) I get (on the final few lines)

```
FATAL: Could not open /lib/modules/2.6.15-26-386/modules.dep.temp for writing: Permission denied
make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/home/steve/v4l-dvb/v4l'
make: *** [install] Error 2
```


Running it as sudo seems to do the make install successfully, with no error messages that I can see.

People have made various suggestions here (e.g. to do with the order of the install, whether the pen is plugged in or not, whether the original firmware should be used) but I'm really now at the stage where I'm just pressing buttons and pulling levers without any clue of what I'm doing...

When I intially loaded kaffeine at least the stick showed up (without downloading any firware whatasoever) - now I've got the green light blinking constantly on the stick, and the stick is not visible in kaffeine (the DVB option is greyed out).

Any suggestions would be gratefully appreciated!

---

### Post by fogster74 on 2006-08-07
I'm getting somewhere - whereas for the last 24 hours the green LED has been flashing like crazy on the stick, for some reason unknown to me it's suddenly started behaving - the LED has gone Orange (to show "untuned") and stopped flashing, and now DVB is ungreyed in Kaffeine... a step forward!!

Kaffeine wouldn't scan so I changed the Kaffeine frequency from 505833333 to 505000000 - still no good, the scan button goes from 0 to 100% with no steps in-between (I know it can work as if I pick Adelaide it at elast goes through the scan process!).

I then tried to scan DVB-Utils from the command line. At first I got the same error message as posted earlier in this post - Scanning Failed. I realised the scan frequency for DVB-Utils was somewhere else (as it still stated 505833333); I found the relevant file in the DVB-Utils directory and  also changed it to 500000000. I tried to scan from the command line this time I simply get:

```

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 505000000 0 3 0 1 0 0 0
>>> tune to: 505000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_16:
TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 505000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_16:
TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.
```

I've also tried setting the frequency to 500000000, with exactly the same result. If I set the tuner to Dover, at least Kaffeine goes through the process of trying to find channels (i.e. 0%, 10%, 20% etc), rather than just 0% -> 100% with no scanning in between currently).

Any thoughts? ](*,)

---

### Post by popper on 2006-08-08
im not sure it will help you get anywere but i just did a search on [http://search.ntlworld.com/ntlworld/search.php?q=linux+dvb+CrystalPalace&cr=](http://search.ntlworld.com/ntlworld/search.php?q=linux+dvb+CrystalPalace&cr=)

and found these bits
[http://linux.mikeasoft.com/dvb.php](http://linux.mikeasoft.com/dvb.php)
and this place has downloadable lists
"Digital television transmitters in the UK generally have 6 multiplexes; each multiplex caries a group of channels. A scan list gives frequencies and basic parameters for all the multiplexes on a specific transmitter. The scan program (available as part of the linuxtv-dvb-apps package at [http://www.linuxtv.org](http://www.linuxtv.org)) takes this list and scans all the frequencies in it to produce a list of channel settings for that transmitter, which can then be used with media players such as xine or mplayer.

If you create any channel lists from scan lists currently lacking channel lists, please e-mail them to me for inclusion in this table."


[http://www.ethics-gradient.net/myth/mythdvb.html](http://www.ethics-gradient.net/myth/mythdvb.html)
"Now you need to install some utilities to tune your card. These are not required by MythTV but are needed to get you going.

We'll be using a program called scan in combination with tzap. For DVB-S or DVB-C the programs are szap and czap respectively.

To add some confusion these applications are not shipped with the dvb-kernel driver. You will need to check out the DVB module (from the same place as before) and build that software.

Now change to the apps/scan directory under where the package was compiled. Run the scan utility like this:

# ./scan dvb-t/uk-CrystalPalace > channels.conf
If there is no frequency file for your area then you can easily create one. In the UK a list of DVB-T transmitter frequencies can be found at the BBC Reception website.

If everything is ok then the channels.conf file will contain the list of channels the card found by scanning what's been transmitted. If there is a predefined list for your transmitter then compare it to the output you got from the above command.

Once you have a good channels .conf create a directory under your home directory called .tzap, .szap or .czap and copy the channels.conf file there. This is also the information you'll need later to configure MythTV so you may want to print it out for reference.
"

[http://www.linuxtv.org/mailinglists/linux-dvb/2003/06-2003/msg00472.html](http://www.linuxtv.org/mailinglists/linux-dvb/2003/06-2003/msg00472.html)

---

### Post by popper on 2006-08-08
> **walkerx said:**
> firstly follow the freecom installation thread

ensure you have the firmware downloaded 
ensure you have the kernel sources ,and any other stuff you need

all these instructions are in the installation help thread and should get it working

thanks for replying walker.

if you mean follow
 the instructions as for instance the very first post to this thread and its like, then i have indeed done that on many vmware, real x86 and indeed all the mac PPC livecds i could find in the last few weeks.

theres an error in the first post in that the firmware that it refers to appears to have moved to [http://thadathil.net:8000/dvb/fw/dvb-usb/](http://thadathil.net:8000/dvb/fw/dvb-usb/)

it seems as i said that i **can warm boot **any livecd that has the dvb-usb-dtt200u on it and have it work.

it **will not cold boot load **the firmware

the problem is i cant keep booting to windows just to have that load the cold boot firmware, and indeed its not an option for eather vmware or the PPC machine as is obvious.

so the problem remains, is there any coders here than can fix/patch the right code , weather thats in the linuxtv code or the hotplug/Udev? linux code that ubuntu (and perhaps all the linux use?) use?.

iv asked on IRC last night and everyone seems to agree that it should be an easy fix, but noones given me any clue as to how or what that might be, keeping in mind it works great if its warm booted from windows, but will not even attempt to load any firmware that i can see (looked in dmesg,sylog etc) were might i look and post to get some help with this yuan dvb2go mini, aka pd300 mini [http://linuxtv.org/wiki/index.php/User:Woodsb02](http://linuxtv.org/wiki/index.php/User:Woodsb02)

i even started to wonder if the windows inf loader for linux
ndiswrapper might work even though it seems to refer to only wireless drivers ?.

if i were to try it what might i try for ubuntu 606 and change for dvb-t use?.

---

### Post by popper on 2006-08-17
with many thanks to jochen over on the linux-dvb mailing list, i have now been able to get my DVB2GO Mini Yuan usb card to function in the x86 606 unbuntu, if your card reports " Bus 004 Device 002: ID 14aa:0220 AVerMedia (again) or C&E" when you cold plug it in and do an **lsusb** , you might be able to get yours working too. 

"
I finally got it working on my kubuntu machine! It seems like that my stick 
has a different USB cold ID, than older/other versions with this chip.

Here is how I did it:
I edited linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h
changed USB_PID_WT220U_COLD from 0x0222 to 0x0220
and everything worked fine.

Although this was just a hack, I think a clean version should be integrated 
into the kernel module. Should I send a patch to this list or can you tell 
me, where I shall send it to?

Best Regards,

jochen "

essentially , in my case after makeing that change from 0x0222 to 0x0220 and re-compiling any of the snapshots or hg, my card can now try and load a firmware in my case dmesg reports its looking for "downloading firmware from file 'dvb-usb-wt220u-02.fw'", your card might ask for another firmware and in that case just place that firmware in the /lib/firmware/$(uname -r)/ dir as per the first post.

also ill remind you that since that OP the dir for the refered firmware has moved to the **dvb-usb** sub dir
[http://thadathil.net:8000/dvb/fw/dvb-usb/](http://thadathil.net:8000/dvb/fw/dvb-usb/)
 
check the [http://thadathil.net:8000/dvb/fw/](http://thadathil.net:8000/dvb/fw/) or linuxtv firmware dirs [http://linuxtv.org/downloads/firmware/](http://linuxtv.org/downloads/firmware/) for your dmesg asked for firmware and you should be set.

if for any reason when you plug in your usb DVB-T card it reports yours as anything other than " Bus 004 Device 002: ID 14aa:**0220** AVerMedia (again) or C&E" then change the coresponding **cold boot **line in that hg made home v4l-dvb linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h file inthe hg dir to your reported No. then see if dmesg will then ask for the right firmware for your card etc.

people that already have a card that report 222 on cold boot dont need to change anything currently, but it seems that the 222 entry is a long standing typo because there are far more products that report 220 on cold pluging.

it seems any reported "AVerMedia (again) or C&E" card will first use
[http://thadathil.net:8000/dvb/fw/dvb-usb/dvb-usb-dtt200u-01.fw](http://thadathil.net:8000/dvb/fw/dvb-usb/dvb-usb-dtt200u-01.fw)
firmware to then load the real (in my case 'dvb-usb-**wt**220u-**02**.fw') firmware for your card that 
dmesg will try and load afterwards so you seem to need both firmwares in the /firmware dir to have it work.

i hope this helps some readers that have given up trying to get their reported " Bus 004 Device 002: ID 14aa:**0220** AVerMedia (again) or C&E" cards working and usable.....

remember to check that dvb-usb-ids.h file for your reported cold boot card and make your changes there , then recompile,

i didnt bother to mess about with **make config **stage and just used **make** , then **make install **so as to just make all the cards to simplyfy the options, try it if your not bothered about the small extra space it takes up on your drive.


PS.
 is there a simple GUI app/script (rebol view?)thats in the unbuntu repositry that can convert my fully tuned UK winterhill kaffeine /home/ubuntu/.kde/share/apps/kaffeine/**channels.dvb **file to something vlc can use so i can try and use vlc to multicast my dvb selections over the network as i do now in windows please?.

---

### Post by koootzz on 2006-09-13
Hi
Total noob to this, I have got the freecom stick and I would like to be able to get it to run from the bootable dvd, so I can use the stick on various pc's without having to install the software. Can anyone with a lot of patience to talk me through this if it is possible.
Thanks

---

### Post by apoth on 2006-09-16
Getting v4l-dvb and running make didn't work for me with the instructions from this thread. Getting it from cvs did compile though:

```
cvs -d :pserver:anonymous@cvs.linuxtv.org:/cvs/video4linux co -P v4l-dvb
```

---

### Post by apoth on 2006-09-16
Ugh I've been debugging C code trying to get the latest revision of the freecom stick working.

I'm stuck now at having my it apparently working - the light's on and orange. But scanning the same transmitter that my freeview box uses just produces:

> rich@france:~$ scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-EmleyMoor scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-EmleyMoor
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 673000000 0 3 3 1 0 0 0
>>> tune to: 673000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 673000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

Any suggestions? Thanks.

---

### Post by apoth on 2006-09-16
I've also got this in dmesg:

```
[17179594.308000] dvb-usb: recv bulk message failed: -110
```

---

### Post by apoth on 2006-09-16
I just had the wrong frequencies. I'll try and remember to post some more information that isn't here but might be useful for others later.

---

### Post by apoth on 2006-09-17
Ok, these are just the differences to the second post in the thread that I had to do, so anyone following this will need to reference that. I had to patch the CVS version of v4l-dvb to get it working with my stick:

```
$ lsusb
Bus 003 Device 006: ID [COLOR="Red"]14aa:0225[/COLOR] AVerMedia (again) or C&E
```

The patched v4l-dvb is [here](http://richm.getmyip.com/v4l-dvb-freecom-0225.zip).

Unzip it, descend into the v4l-dvb directory and type:
```
make
sudo make install
```

You'll also need the firmware from [here](http://richm.getmyip.com/dvb-usb-wt220u-fc03.fw) put into /lib/firmware/{kernel-verson}

Reboot and you should have an orange light. Check /var/log/messages and dmesg otherwise.

Finding UK frequencies. [Use the ofcom site](http://www.ofcom.org.uk/static/reception_advice/index.asp.html). Browse into your region and then choose digital transmitter information. You need to pick the transmitter that covers you - you might be able to get this from an existing freeview box most easily or from just googling where these things are and picking the closest.

Select your transmitter and note down the channel numbers - there are probably six. Then you'll need to scan against the frequencies ('scan filename' in /usr/share/doc/dvb-utils/examples/scan/dvb-t/ having edited a file in there to put the frequency in) for those channel numbers. This is a list of channel numbers and their corresponding frequencies:

(Add 000000 to the end of the frequency)

```
Channel Frequency
21		474
22		482
23		490
24		498
25		506
26		514
27		522
28		530
29		538
30		546
31		554
32		562
33		570
34		578
35		586
36		594
37		602
38		610
39		618
40		626
41		634
42		642
43		650
44		658
45		666
46		674
47		682
48		690
49		698
50		706
51		714
52		722
53		730
54		738
55		746
56		754
57		762
58		770
59		778
60		786
61		794
62		802
63		810
64		818
65		826
66		834
67		842
68		850
```[COLOR="Red"][/COLOR]

---

### Post by puccaso on 2006-09-17
> **popper said:**
> im not sure it will help you get anywere but i just did a search on [http://search.ntlworld.com/ntlworld/search.php?q=linux+dvb+CrystalPalace&cr=](http://search.ntlworld.com/ntlworld/search.php?q=linux+dvb+CrystalPalace&cr=)

and found these bits
[http://linux.mikeasoft.com/dvb.php](http://linux.mikeasoft.com/dvb.php)
and this place has downloadable lists
"Digital television transmitters in the UK generally have 6 multiplexes; each multiplex caries a group of channels. A scan list gives frequencies and basic parameters for all the multiplexes on a specific transmitter. The scan program (available as part of the linuxtv-dvb-apps package at [http://www.linuxtv.org](http://www.linuxtv.org)) takes this list and scans all the frequencies in it to produce a list of channel settings for that transmitter, which can then be used with media players such as xine or mplayer.

If you create any channel lists from scan lists currently lacking channel lists, please e-mail them to me for inclusion in this table."


[http://www.ethics-gradient.net/myth/mythdvb.html](http://www.ethics-gradient.net/myth/mythdvb.html)
"Now you need to install some utilities to tune your card. These are not required by MythTV but are needed to get you going.

We'll be using a program called scan in combination with tzap. For DVB-S or DVB-C the programs are szap and czap respectively.

To add some confusion these applications are not shipped with the dvb-kernel driver. You will need to check out the DVB module (from the same place as before) and build that software.

Now change to the apps/scan directory under where the package was compiled. Run the scan utility like this:

# ./scan dvb-t/uk-CrystalPalace > channels.conf
If there is no frequency file for your area then you can easily create one. In the UK a list of DVB-T transmitter frequencies can be found at the BBC Reception website.

If everything is ok then the channels.conf file will contain the list of channels the card found by scanning what's been transmitted. If there is a predefined list for your transmitter then compare it to the output you got from the above command.

Once you have a good channels .conf create a directory under your home directory called .tzap, .szap or .czap and copy the channels.conf file there. This is also the information you'll need later to configure MythTV so you may want to print it out for reference.
"

[http://www.linuxtv.org/mailinglists/linux-dvb/2003/06-2003/msg00472.html](http://www.linuxtv.org/mailinglists/linux-dvb/2003/06-2003/msg00472.html)







```
 mahir@jt:~$ scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace -nv
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 505833333 0 3 9 1 0 0 0
>>> tune to: 505833333:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
WARNING: >>> tuning failed!!!
>>> tune to: 505833333:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
>>> tuning status == 0x20
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.
 
```



thats what i get
whats going on?? i get NOTHING.. this thing is supposed to handle analogue too - i would be happy with that for now..

---

### Post by puccaso on 2006-09-17
hi

im having the same issue as u
did you fix it?>?




> **fogster74 said:**
> I'm getting somewhere - whereas for the last 24 hours the green LED has been flashing like crazy on the stick, for some reason unknown to me it's suddenly started behaving - the LED has gone Orange (to show "untuned") and stopped flashing, and now DVB is ungreyed in Kaffeine... a step forward!!

Kaffeine wouldn't scan so I changed the Kaffeine frequency from 505833333 to 505000000 - still no good, the scan button goes from 0 to 100% with no steps in-between (I know it can work as if I pick Adelaide it at elast goes through the scan process!).

I then tried to scan DVB-Utils from the command line. At first I got the same error message as posted earlier in this post - Scanning Failed. I realised the scan frequency for DVB-Utils was somewhere else (as it still stated 505833333); I found the relevant file in the DVB-Utils directory and  also changed it to 500000000. I tried to scan from the command line this time I simply get:

```

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 505000000 0 3 0 1 0 0 0
>>> tune to: 505000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_16:
TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 505000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_16:
TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.
``` 
I've also tried setting the frequency to 500000000, with exactly the same result. If I set the tuner to Dover, at least Kaffeine goes through the process of trying to find channels (i.e. 0%, 10%, 20% etc), rather than just 0% -> 100% with no scanning in between currently).

Any thoughts? ](*,)

---

### Post by puccaso on 2006-09-17
ok, i got some ideas from somewhere else
and when i do

```
 mahir@jt:~$ tzap -r "BBC TWO"
 
```

i get this ...

```
 mahir@jt:~$ tzap -r "BBC TWO"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 505833333 Hz
video pid 0x0262, audio pid 0x0263
status 20 | signal ffff | snr ffff | ber 00000000 | unc 00000000 | 
status 20 | signal ffff | snr ffff | ber 00000000 | unc 00000000 | 
status 20 | signal ffff | snr ffff | ber 00000000 | unc 00000000 | 
status 20 | signal ffff | snr ffff | ber 00000000 | unc 00000000 | 
  
```


what does this mean???

---

### Post by puccaso on 2006-09-27
ok
... so i use kaffiene to watch... because the dvb-utils stuff just doesnt seem to want to work for me.. 

i edited the crystal-palace freqs to whole numbers, 
and i get about 8 channels...

however, if i run it in windows, i get about 15 channels (these are all video, im not couting db radio)

however, i installed vista to see if it would work in that, 
and, now well although the dvb-t usb stick doesnt seem to want all alow me to watch anything (complains there is no signal) it finds around 44 channels!! like all of them really that i can be bothered about - more then my digital tv does downstairs!!

now, what method does MCE/vista use to find/scan all these files as apposed to kaffiene/linux.. 


what do i need to do?

---

### Post by gary101 on 2006-11-03
Hi All

I have been following this thread with interest and have found the instructions quite easy to follow, thanks! :) 

I created a tuning file for my transmitter and have picked up all of the channels I would expect when I did a scan.

Problem is Kaffeine keeps freezing on me! At first it locked up the whole computer, so I uninstalled and then re-installed kaffeine now it just seems to lock up kaffeine with the message: The window "2 - BBC TWO - Kaffeine Player" is not responding.

I am pretty sure the freecom stick is installed correctly, here is the output of dmesg:

~$ cat /var/log/dmesg | grep dvb
[17179602.636000] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
[17179602.636000] dvb-usb: will use the device's hardware PID filter (table count: 15).
[17179602.640000] dvb-usb: schedule remote query interval to 300 msecs.
[17179602.640000] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[17179602.640000] usbcore: registered new driver dvb_usb_dtt200u
[17179604.940000] dvb-usb: recv bulk message failed: -110


I am not quite happy with the recv bulk message failed: -110, however I see this in some other peoples posts and they seem to be having no troubles.

When Kaffeine starts I get a can't bind info socket error message, not sure what that is about!?

Can anyone shed any light on this? as it is about the only thing I have to go back to windows for, I much prefer Ubuntu ](*,) 

Any help appreciated!

Gary

---

### Post by gary101 on 2006-11-04
Hi All

Figured out where my problems were!

Had built this computer out of bits laying around, totally forgot to check the spec of the USB ports on the mainboard. Turns out they are USB 1.1 and while the freecom DVB was installed and recognised I had problems with freezing/crashing while using it.

Installed a USB 2 PCI board I found in a cupboard and tuning and playback are fine.

Just goes to show how when you get stuck into complexities you can easily overlook the simple solutions. :-D 

Hope this oversight will stop anyone else having the trouble that I have had.

Gary

---

### Post by gary101 on 2006-11-24
Moved

---

### Post by daller on 2006-12-17
**A simple google search: [http://www.dvhardware.net/review82_freecom_dvb-t.html](http://www.dvhardware.net/review82_freecom_dvb-t.html) which gave me the following links:**

Try this:

[http://www.acaciaclose.co.uk/16253/index.html](http://www.acaciaclose.co.uk/16253/index.html)

...and if that's not it, see if you can find it on [http://linuxtv.org](http://linuxtv.org)

---

### Post by mosedavid on 2006-12-18
[LEFT]hi,
I have found 2 firmware updates on linuxtv.org -  the links to the file in this thread dont work.  the firmware links are to - dvb-usb-wt220u-01.fw and dvb-usb-wt220u-02.fw.  I have checked my windows software cd and files in the driver folder are for 'capture' 2X0, and loader 2X1.  I want to be sure that i am installing the correct firmware.

Also is the fimware installed onto the dvb stick as normal or is it installed onto the hard drive?

[/LEFT]

---

### Post by Matt Volatile on 2007-02-20
To save anyone else the hunt I just went on - the firmware you need for the earlier models is at [http://www.linuxtv.org/downloads/firmware/dvb-usb-wt220u-02.fw](http://www.linuxtv.org/downloads/firmware/dvb-usb-wt220u-02.fw)

If you plug in the device and still have no luck, run "dmesg" which will tell you the name of the firmware file expected. Chances are its available here:

[http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)

-------------------------

---

### Post by HilliBilly on 2007-02-23
i don't understand why i get this error message. what do i have to do?

xxx@xxx-ubuntu-laptop:~/v4l-dvb$ sudo apt-get install linux-headers-2.6.17-11-386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-11-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

perfect ... but then:

xxx@xxx-ubuntu-laptop:~/v4l-dvb$ make
make -C /home/xxx/v4l-dvb/v4l 
make[1]: Entering directory `/home/xxx/v4l-dvb/v4l'
creating symbolic links...
make -C /lib/modules/2.6.15-26-686/build SUBDIRS=/home/xxx/v4l-dvb/v4l  modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-26-686/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/xxx/v4l-dvb/v4l'
make: *** [all] Error 2
xxx@xxx-ubuntu-laptop:~/v4l-dvb$

---

### Post by deeppurple on 2007-02-25
I'm too a newbie to linux.

This forums is just brilliant. In a short time I've learnt a lot and managed to get wireless and other things workling well.

Then there is the freecom DVB stick !

I tried the suggestion one of the members made about Kaffiene but when I run up Kaffeine the DVB icon is greyed out..

How can I tell if the stick has been recognised by Ubunut ?

There seems lots of different solutions on the forum which make it quite difficult for a newbie.

The wireless adaptor is plugged into the USB so I know all is well with the USB but it just will not see the DVB..

Any help would be really appreciated 

Peter

---

### Post by puccaso on 2007-03-11
ok


kaffeine wont find my device in user
but will find it fine in root

why is that?

---

### Post by gerv on 2007-04-24
In case it helps anyone: my Freecom USB DVB-T stick is working fine on Feisty. On Edgy I needed to compile some drivers but on Feisty, all I needed to do was to put the firmware in /lib/firmware/`uname -r`.

The firmware file I have, which works for my stick, is called dvb-usb-dib0700-01.fw. I'm sure a Google search will find a copy. Email me at gerv at gerv dot net if you get stuck.

Gerv

---

### Post by MagnusL on 2007-04-24
Hi!

I have a brand new Freecom USB DVB-stick, and a brand new feisty-installation. Copied in the fw you mention (found it at [http://www.omskakas.se/2007/01/howto-hauppauge-nova-t-500-pci-under-linux.html/firmware-files-for-various-tv-tuners-under-linux/](http://www.omskakas.se/2007/01/howto-hauppauge-nova-t-500-pci-under-linux.html/firmware-files-for-various-tv-tuners-under-linux/))

But there seems to be no firmware loaded, and no /dev/dvb-folder at all. 

dmesg says: 
[17189067.028000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[17189067.552000] usb 4-1: configuration #1 chosen from 1 choice

Any ideas?

Magnus L

---

### Post by sark3441 on 2007-06-08
hi have just brought a Freecom usb dvb-t stick thing and i am having problems with the 'make config' portion of this thread. can any body help me out as i have more things to say n/m to than was given at the start.

the list i get is:-

ark@sark-desktop:~/v4l-dvb$ make config
make -C /home/sark/v4l-dvb/v4l config
make[1]: Entering directory `/home/sark/v4l-dvb/v4l'
/lib/modules/2.6.20-16-generic/build/scripts/kconfig/conf ./Kconfig
*
* Linux Kernel Configuration
*
Enable drivers not supported by this kernel (VIDEO_KERNEL_VERSION) [Y/n/?]
*
* Multimedia devices
*
Video For Linux (VIDEO_DEV) [N/m/y/?] n
DVB for Linux (DVB_CORE) [M/n/y/?] y
  Load and attach frontend modules as needed (DVB_CORE_ATTACH) [Y/n/?]
  *
  * DVB/ATSC adapters
  *
  DVB/ATSC adapters (DVB_CAPTURE_DRIVERS) [Y/n/?]
    *
    * Supported SAA7146 based PCI Adapters
    *
    *
    * Supported USB Adapters
    *
    Support for various USB DVB devices (DVB_USB) [M/n/?] m
      Enable extended debug support for all DVB-USB devices (DVB_USB_DEBUG) [N/y/?]
      AVerMedia AverTV DVB-T USB 2.0 (A800) (DVB_USB_A800) [N/m/?] n
      DiBcom USB DVB-T devices (based on the DiB3000M-B) (see help for device list) (DVB_USB_DIBUSB_MB) [N/m/?] n
      DiBcom USB DVB-T devices (based on the DiB3000M-C/P) (see help for device list) (DVB_USB_DIBUSB_MC) [N/m/?] n
      DiBcom DiB0700 USB DVB devices (see help for supported devices) (DVB_USB_DIB0700) [N/m/?] n
      HanfTek UMT-010 DVB-T USB2.0 support (DVB_USB_UMT_010) [N/m/?] n
      Conexant USB2.0 hybrid reference design support (DVB_USB_CXUSB) [N/m/?] n
      Uli m920x DVB-T USB2.0 support (DVB_USB_M920X) [N/m/?] n
      Genesys Logic GL861 USB2.0 support (DVB_USB_GL861) [N/m/?] n
      Alcor Micro AU6610 USB2.0 support (DVB_USB_AU6610) [N/m/?] n
      Nebula Electronics uDigiTV DVB-T USB2.0 support (DVB_USB_DIGITV) [N/m/?] n
      TwinhanDTV Alpha/MagicBoxII, DNTV tinyUSB2, Beetle USB2.0 support (DVB_USB_VP7045) [N/m/?] n
      TwinhanDTV StarBox and clones DVB-S USB2.0 support (DVB_USB_VP702X) [N/m/?] n
      GENPIX 8PSK->USB module support (DVB_USB_GP8PSK) [N/m/?] n
      Hauppauge WinTV-NOVA-T usb2 DVB-T USB2.0 support (DVB_USB_NOVA_T_USB2) [N/m/?] n
      Pinnacle 400e DVB-S USB2.0 support (DVB_USB_TTUSB2) [N/m/?] n
      WideView WT-200U and WT-220U (pen) DVB-T USB2.0 support (Yakumo/Hama/Typhoon/Yuan) (DVB_USB_DTT200U) [M/n/?] m
      Opera1 DVB-S USB2.0 receiver (DVB_USB_OPERA1) [N/m/?] n
      Afatech AF9005 DVB-T USB1.1 support (DVB_USB_AF9005) [N/m/?] n
    Technotrend/Hauppauge Nova-USB devices (DVB_TTUSB_BUDGET) [N/m/?] n
    Technotrend/Hauppauge USB DEC devices (DVB_TTUSB_DEC) [N/m/?] n
    Terratec CinergyT2/qanu USB2 DVB-T receiver (DVB_CINERGYT2) [N/m/?] n
    *
    * Supported FlexCopII (B2C2) Adapters
    *
    Technisat/B2C2 FlexCopII(b) and FlexCopIII adapters (DVB_B2C2_FLEXCOP) [N/m/?] n
    *
    * Supported BT878 Adapters
    *
    *
    * Supported Pluto2 Adapters
    *
    Pluto2 cards (DVB_PLUTO2) [N/m/?] n
    *
    * Supported DVB Frontends
    *
    *
    * Customise DVB Frontends
    *
    Customise the frontend modules to build (DVB_FE_CUSTOMISE) [N/y/?]
    *
    * DVB-S (satellite) frontends
    *
    ST STV0299 based (DVB_STV0299) [N/m/?] n
    Conexant CX24110 based (DVB_CX24110) [N/m/?] n
    Conexant CX24123 based (DVB_CX24123) [N/m/?] n
    Philips TDA8083 based (DVB_TDA8083) [N/m/?] n
    Zarlink VP310/MT312 based (DVB_MT312) [N/m/?] n
    VLSI VES1893 or VES1993 based (DVB_VES1X93) [N/m/?] n
    Samsung S5H1420 based (DVB_S5H1420) [N/m/?] n
    Philips TDA10086 based (DVB_TDA10086) [N/m/?] n
    *
    * DVB-T (terrestrial) frontends
    *
    Spase sp8870 based (DVB_SP8870) [N/m/?] n
    Spase sp887x based (DVB_SP887X) [N/m/?] n
    Conexant CX22700 based (DVB_CX22700) [N/m/?] n
    Conexant cx22702 demodulator (OFDM) (DVB_CX22702) [N/m/?] n
    LSI L64781 (DVB_L64781) [N/m/?] n
    Philips TDA10045H/TDA10046H based (DVB_TDA1004X) [N/m/?] n
    NxtWave Communications NXT6000 based (DVB_NXT6000) [N/m/?] n
    Zarlink MT352 based (DVB_MT352) [M/n/?] m
    Zarlink ZL10353 based (DVB_ZL10353) [M/n/?] m
    DiBcom 3000M-B (DVB_DIB3000MB) [N/m/?] n
    DiBcom 3000P/M-C (DVB_DIB3000MC) [N/m/?] n
    DiBcom 7000MA/MB/PA/PB/MC (DVB_DIB7000M) [N/m/?] n
    DiBcom 7000PC (DVB_DIB7000P) [N/m/?] n
    *
    * DVB-C (cable) frontends
    *
    VLSI VES1820 based (DVB_VES1820) [N/m/?] n
    Philips TDA10021 based (DVB_TDA10021) [N/m/?] n
    Philips TDA10023 based (DVB_TDA10023) [N/m/?] n
    ST STV0297 based (DVB_STV0297) [N/m/?] n
    *
    * ATSC (North American/Korean Terrestrial/Cable DTV) frontends
    *
    NxtWave Communications NXT2002/NXT2004 based (DVB_NXT200X) [N/m/?] n
    Oren OR51211 based (DVB_OR51211) [N/m/?] n
    Oren OR51132 based (DVB_OR51132) [N/m/?] n
    Broadcom BCM3510 (DVB_BCM3510) [N/m/?] n
    LG Electronics LGDT3302/LGDT3303 based (DVB_LGDT330X) [N/m/?] n
    *
    * Tuners/PLL support
    *
    Generic I2C PLL based tuners (DVB_PLL) [M/?] m
    Philips TDA826X silicon tuner (DVB_TDA826X) [N/m/?]
    Philips TDA827X silicon tuner (DVB_TDA827X) [N/m/?]
    Quantek QT1010 silicon tuner (DVB_TUNER_QT1010) [N/m/?]
    Microtune MT2060 silicon IF tuner (DVB_TUNER_MT2060) [N/m/?]
    *
    * Miscellaneous devices
    *
    LNBP21 SEC controller (DVB_LNBP21) [N/m/?] n
    ISL6421 SEC controller (DVB_ISL6421) [N/m/?] n
    TUA6100 PLL (DVB_TUA6100) [N/m/?] n
DAB adapters (DAB) [N/y/?] n
*
* Audio devices for multimedia
*
*
* ALSA sound
*
Bt87x Audio Capture (SND_BT87X) [M/n/?]
  Bt87x Audio overclocking (SND_BT87X_OVERCLOCK) [N/y/?]
*
* OSS sound
*
BT878 audio dma (SOUND_BT878) [M/n/?]
ACI mixer (miroSOUND PCM1-pro/PCM12/PCM20) (SOUND_ACI_MIXER) [M/n/?]
#
# configuration written to .config
#

*** Error during writing of the kernel configuration.

make[1]: *** [config] Error 1
make[1]: Leaving directory `/home/sark/v4l-dvb/v4l'
make: *** [config] Error 2
sark@sark-desktop:~/v4l-dvb$    

thanks

---

### Post by Ultra Magnus on 2007-07-13
*Bump* - I get exactly the same error message after doing make config.

---

### Post by sark3441 on 2007-07-15
managed to get the orange light to come on now, by using a different website (let me know if anyone wants the link)

but can't get it to pick up any tv signal in kaffanie

what am i doing wrong? and is there anything eles out there?

---

### Post by Nanoboy on 2007-07-22
I used to be able to pick up signal and watched some really good quality TV with my freecom dvb-t.  I suspect that it might have been some package update (e.g. xine), after that I could never scan for any channels.  The orange light is till on, and it flickers to green sometimes when i click on some rare channels like Sky THREE.  

Need help :(

---

### Post by Tiggzz on 2007-08-10
Hi Guys, 

I'm very noob to ubuntu, but I think I'm learning quick, but my DVB-T stick is giving me right headaches.

I get the same results as sark, and magnus above. The extra options in the make, followed by the error at the end. No /dev/dvb folder 

and the same old

[ 4383.033515] usb 5-3: new high speed USB device using ehci_hcd and address 7
[ 4383.564429] usb 5-3: configuration #1 chosen from 1 choice

when I do a lsusb, I get a different device number, not 0221 etc but

Bus 005 Device 007: ID 14aa:0620 AVerMedia (again) or C&E 

I just want to use this. I've changed from XP to ubuntu becuase teh PVR in windows is dire, this is the main task I want out of this PC, this has had me here for 2 solid days.

PLEASE HELP!!!!

Thanks v much, 

Tiggzz :)

---

### Post by Tetenterre on 2007-08-19
> **Ultra Magnus said:**
> *Bump* - I get exactly the same error message after doing make config.

*Bump* -- ditto here.  (Very new Ubuntu/Linux user). Has anyone solved this yet?

---

### Post by alexisj on 2007-10-19
To Tiggz (and others)

If the usb id is also  **14aa:0620**, we have the same probleme.
This devices is *"Freecom DVB-T & Analog TV USB Stick"*  (art no: 27442). 
(This is the "hybrid" version and not dvb-t  only; this is why we can't use it easily like somes others freecom cards)
This device uses a ** TM6000 chipset.**

Check this: [http://www.linuxtv.org/v4lwiki/index.php/Trident_TM6000](http://www.linuxtv.org/v4lwiki/index.php/Trident_TM6000)

It is possible to try the experimental driver, who still in developpement...
I've tried compilation and extraction of the original windows firmware (on cd), but at final, a can't show anything and the gree led dont lights.

A "good point", now dmesg talk me about dvb or firware, but it return me errors like:

$ dmesg | grep dvb
[  245.891913] /home/alexis/v4l-dvb/v4l/tm6000.c: tm6000: error -71 has occurred whilst sending a USB control message with request 16, value 10946 and index 0
[  255.058463] /home/alexis/v4l-dvb/v4l/tm6000.c: tm6000: error -71 has occurred whilst sending a USB control message with request 16, value 10946 and index 0

$ dmesg | grep firmware
[  255.058469] tm6000: could not send firmware
[  274.938364] tm6000: firmware1 transmitted
[  282.977534] tm6000: firmware2 transmitted
[  396.977027] tm6000: firmware1 transmitted
[  405.016198] tm6000: firmware2 transmitted
[ 1491.187481] tm6000: could not send firmware
[ 1500.169967] tm6000: firmware1 transmitted
[ 1508.209132] tm6000: firmware2 transmitted

Great! :-)

So if you want to try or help me..
This would be pleased

---

### Post by Tiggzz on 2007-10-19
I'm afraid that the option I took was to pu thte freecom on ebay, and buy a hauppague, which works an absolute treat.

Tiggzz :)

---

### Post by Ashrael on 2007-11-28
Haven't read the thread completely, but during install you must sometimes be root/admin so make sure that the user using the device has rights to group video.... try:                usermod -a -G USER video                if i'm correct..

HTH

---

### Post by nyyyy on 2008-01-26
At some point in the last few weeks, this has stopped working for me.  This is what is shown when I plug in:

> Jan 26 16:35:53 dan-desktop kernel: [  151.115652] dvb_usb: Unknown symbol dvb_frontend_detach
Jan 26 16:35:53 dan-desktop kernel: [  151.115753] dvb_usb: disagrees about version of symbol dvb_unregister_frontend
Jan 26 16:35:53 dan-desktop kernel: [  151.115756] dvb_usb: Unknown symbol dvb_unregister_frontend
Jan 26 16:35:53 dan-desktop kernel: [  151.115867] dvb_usb: disagrees about version of symbol dvb_register_frontend
Jan 26 16:35:53 dan-desktop kernel: [  151.115869] dvb_usb: Unknown symbol dvb_register_frontend
Jan 26 16:35:53 dan-desktop kernel: [  151.118286] dvb_usb_dtt200u: Unknown symbol dvb_usb_nec_rc_key_to_event
Jan 26 16:35:53 dan-desktop kernel: [  151.118585] dvb_usb_dtt200u: Unknown symbol dvb_usb_generic_rw
Jan 26 16:35:53 dan-desktop kernel: [  151.118687] dvb_usb_dtt200u: Unknown symbol dvb_usb_device_init
Jan 26 16:35:53 dan-desktop kernel: [  151.118733] dvb_usb_dtt200u: Unknown symbol dvb_usb_device_exit
Jan 26 16:35:53 dan-desktop kernel: [  151.118782] dvb_usb_dtt200u: Unknown symbol dvb_usb_generic_write

Has anyone got any ideas?  I've tried make/make install again on the drivers but still got nowhere.  Thanks in advance.

---

### Post by nyyyy on 2008-01-28
sorry to bump this up, but does anyone have any ideas?  I've tried google and the only similar problems seem to be reported in foreign languages.  If someone could point me in the right direction I'd appreciate it.

---

