---
title: "Digital TV Tuner - cannot watch TV - DVB-T rtl2832u"
date: 2013-01-28
forum: Hardware
---

### Post by vector.kerr on 2013-01-28
Hi all,

I have a Realtek rtl2832u digital television usb adapter (branded as an "EZCap"). I know the device works - I have used it on an (old) windows machine and it functions very well. 

I have spent a considerable amount of time getting it to work, with varying degrees of success. The main issue seems to be the kernel driver, however I'm not sure if this is the only cause of the issues I'm experiencing.

I have tried drivers from a [number](http://blog.delouw.ch/2012/09/16/how-to-get-a-rtl2832u-based-dvb-t-stick-working-on-fedora-17/) [of](http://linbay.blogspot.com.au/2012/05/hassle-almost-free-rtl2832u-linux.html) [sources](http://ubuntuforums.org/showthread.php?t=1905057). Most of these end up giving me a /dev/dvb/adapter0/* device to play with, but I don't seem to be able to do anything useful with it - even pick up channels.

My most recent attempt has involved following the instructions [here](http://www.dfragos.me/2012/11/installation-of-rtl2832u-chip-based-dvb-t-usb-stick.html), which include getting the media build from linuxtv ([http://www.dfragos.me/2012/11/installation-of-rtl2832u-chip-based-dvb-t-usb-stick.html](http://www.dfragos.me/2012/11/installation-of-rtl2832u-chip-based-dvb-t-usb-stick.html)), modifying it to include the product id for my device (0bda:2838), then running make and make install.

The device appears under /dev/dvb/adapter0/*.
The closest dvb-t scan file for me is au-Devonport.

Running "dvbscan /usr/share/dvb/dvb-t/au-Devonport" results in the error message "Unable to query frontend status".

Running w_scan results in some promising output:
> 
<<snip>>

774500: (time: 04:34) (time: 04:35) 
774625: (time: 04:36) (time: 04:37) signal ok:
	QAM_AUTO f = 774625 kHz I999B7C999D999T999G999Y999
Info: NIT(actual) filter timeout
781500: (time: 04:52) (time: 04:53) signal ok:
	QAM_AUTO f = 781500 kHz I999B7C999D999T999G999Y999
Info: NIT(actual) filter timeout
781625: skipped (already known transponder)
788500: (time: 05:08) 
788625: (time: 05:11) (time: 05:12) signal ok:
	QAM_AUTO f = 788625 kHz I999B7C999D999T999G999Y999
Info: NIT(actual) filter timeout
795500: (time: 05:26) (time: 05:27) signal ok:
	QAM_AUTO f = 795500 kHz I999B7C999D999T999G999Y999
Info: NIT(actual) filter timeout
795625: skipped (already known transponder)

<<snip>>

tune to: QAM_AUTO f = 774625 kHz I999B7C999D999T999G999Y999 
(time: 05:58) ----------no signal----------
tune to: QAM_AUTO f = 774625 kHz I999B7C999D999T999G999Y999  (no signal)
(time: 05:59) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 781500 kHz I999B7C999D999T999G999Y999 
(time: 06:14) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 788625 kHz I999B7C999D999T999G999Y999 
(time: 06:29) ----------no signal----------
tune to: QAM_AUTO f = 788625 kHz I999B7C999D999T999G999Y999  (no signal)
(time: 06:30) ----------no signal----------
tune to: QAM_AUTO f = 795500 kHz I999B7C999D999T999G999Y999 
(time: 06:31) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
dumping lists (0 services)
Done.

Where before I couldn't pick up anything, I now seem to be able to scan for channels.

Running "dvbsnoop -s signal" reports:
> Error(11): frontend ioctl: Resource temporarily unavailable
This message comes up regardless of whether I am running as root.

Running "vlc dvb-t://frequency=795500000:bandwidth=0" does not display any errors, but it also displays no image.

Running "vlc dvb-t://frequency=900000000:bandwidth=0" results in an error, which I suspect that it should as it's probably out of the frequency range of the device.

Some general information:
```

vector@vector-media:~$ uname -a
Linux vector-media 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux

vector@vector-media:~$ lsusb
<<snip>>
Bus 006 Device 002: ID 0bda:2838 Realtek Semiconductor Corp. 

root@vector-media:/home/vector# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

root@vector-media:/home/vector# lsmod | grep dvb
dvb_usb_rtl28xxu       18948  0 
dvb_usb_v2             22916  1 dvb_usb_rtl28xxu
rc_core                21177  3 dvb_usb_rtl28xxu,dvb_usb_v2
rtl2830                13511  1 dvb_usb_rtl28xxu
dvb_core               90208  3 rtl2832,dvb_usb_v2,rtl2830

```

Any help you might be able to offer is greatly appreciated!

---

### Post by TazX on 2013-03-04
Heya!  I've got the same card.  Does your head in, no?  I kept hitting brick walls in that all the how-tos are out of date.  But I am about to make your day, as it's easier than you might think.  Enter these commands:
```
[INDENT]git clone git://linuxtv.org/media_build.git 
cd media_build 
./build 
make install[/INDENT]

```

Done!  That's it.  Our card is now in the official LinuxTV media_build, so it 'just works'.  I just added a couple of lines to the RLT-2832u page on the wiki to let people like us know.  Hope it helps.  Congrats on getting so close.  I didn't get anywhere near the results you seem to have gotten.

---

### Post by collieindigo on 2013-03-18
Thank you very much TazX for the build. It works form me on my Ubuntu x86_64 12.04.2   LTS with kernel 3.2.0-39.

---

### Post by mgt2000 on 2013-05-12
[COLOR=#333333][FONT=Arial]And here is the repository

sudo apt-add-repository ppa:chrisfu/rt2832u-dkms[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]sudo apt-get install rtl2832u-dkms[/FONT][/COLOR]

---

