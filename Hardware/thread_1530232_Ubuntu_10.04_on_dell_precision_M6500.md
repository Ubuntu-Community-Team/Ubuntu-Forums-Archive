---
title: "Ubuntu 10.04 on dell precision M6500"
date: 2010-07-13
forum: Hardware
---

### Post by Gargoulf on 2010-07-13
Dear all,

I'm starting a new thread after that of [http://ubuntuforums.org/showthread.php?t=1445821](http://ubuntuforums.org/showthread.php?t=1445821) which 
concerned ubuntu 9.10 on the dell precision M6500.

I have recently fresh-installed ubuntu 10.04 32-bit on my laptop, so I would like to share some impression and report some problems, hoping other people will be able to solve.

First, installation was easily done. The only regret is that the mounting options were not automatically optimized for SSD drive. After googleing, I found that the best for SSD is to mount with option 'relatime', which seems to be like 'noatime' but without the problems it involves for mails.

After first boot, I am proposed to use proprietary drivers for wireless broadcom and NVIDIA card. There i not much help here and for each device, I have two options. I choose the most up-to-date. (STA for broadcom and "version current" for NVIDIA (instead of version 173).

Now, let's see what is NOT working:

- internal microphone: searched in different posts, bugs reports, etc. But I' still unable to make it work. [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/519066](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/519066)
The strange thing is that sometimes I have no sound at all. Then, I reinstall alsa-backport modules and output works back.
Also, it seems it worked on 9.10 after some updates (see [http://ubuntuforums.org/showthread.php?t=1445821](http://ubuntuforums.org/showthread.php?t=1445821)) but I heard about nobody having the internal microphone working on ubuntu 10.04. This is a very important bug since we cannot use widely-used softwares like skype, for example.

- logout/restart: sometimes (seems that after reinstalling alsa), the logout/restart does not work properly. Instead, I am just logged out. However, 'sudo shutdown -r now' in a terminal works.

- I had also some experience with freezing at boot / shutdown. I solved this by removing the ubuntu-provided graphic card driver, and keeping only the proprietary one.
Have a look at [https://wiki.ubuntu.com/X/Troubleshooting/Nouveau#Disabling%20nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau#Disabling%20nouveau) 
What I actually did, was to use synaptics (when hard re-booting), searched for nouveau, and removed it.

- fingerprint reader: ok, this is not that useful, but since my laptop came with this, why not using it. 
It seems there are two drivers: thinkfinger and fprint. fprint is the most recent one. Anyway, none of them works and simply do not find device (swipe fingerprint broadcom USH).

- touchpad: under windows 7 (removed completely one hour after I got the laptop), I had lots of possibilities, including pinch zoom, etc. I even had some light in the touchpad when touching a particular zone. None of this is working under ubuntu. Touchpad is a very simple mouse without any "two fingers" options. I also experienced some problems with the touchpad getting crazy and the mouse always going to the left of my screen. It seems synaptics has developped something for this ([http://www.synaptics.com/solutions/technology/gestures/touchpad-linux)...but](http://www.synaptics.com/solutions/technology/gestures/touchpad-linux)...but) it is not implemented on ubuntu 10.04 and I found no way to download/install these drivers.

All the rest seems working fine. Please report is you experienced similar problems and/or found a SOLUTION!

---

### Post by tahu363 on 2010-07-21
Thanks, I'm glad that someone finaly paid attention to this. Unfortunately, the link you provided for the synaptics fix/explanation is dead. Is there another one? Im eager to try to fix the touchpad.

---

### Post by Gargoulf on 2010-07-23
[http://www.synaptics.com/solutions/technology/gestures/touchpad-linux](http://www.synaptics.com/solutions/technology/gestures/touchpad-linux)

---

### Post by tahu363 on 2010-07-23
Thanks. Unfortunately, I fail to see any resources for binaries or source. I read that distros are beginning to incorperate this software and that it should be available in the later versions of some distros, Does that mean we'll have to wait till Ubuntu 10.10 for a fix? :(

---

### Post by Gargoulf on 2010-07-29
Concerning touchpad, yes, I guess we'll have to wait (at least) 10.10.

Did you manage to make the internal mic work? It seems this is a very common 
problem with DELL laptops with ubuntu. I tried tons of solutions that worked for others 
on other laptops / distributions but it seems that until now, no one has been able 
to fix the microphone pb on M6500 under ubuntu 10.04.

---

### Post by tahu363 on 2010-07-30
Unfortunately, I'm with you on that one. No working internal mic. I've tried pretty much everything, and I have no idea why it wouldnt work when I applied others workarounds. :( Concerning the hefty price I paid for this machine ($5,139) I'm a little dissappointed, I assumed that if everything was working on 9.10 that it would also apply to 10.04, I suppose that was my bad though. I'll keep snooping around for fixes to other common issues, and I'll post back if I get anything, I also hope you'll do the same. Sorry that i couldn't help with the Mic issues, oh well, I'll keep searching around... :\

---

### Post by Gargoulf on 2010-07-30
Yep. I'm continuing with searching for a solution. I'll post if I get solution.
At least the bug has been validated and people seem to work on it.
[https://bugs.launchpad.net/bugs/519066](https://bugs.launchpad.net/bugs/519066)

---

### Post by atkaper on 2010-07-31
Hi there,

My M6500 with 10.04 on it also gave me problems with reading a 4gb micro sdhc card. Inserting the card did not mount it, and no /dev/* entry appeared. dmesg showed "tifm_core: MMC/SD card detected in socket 0:1" and "mmc1: error -110 whilst initialising SD card". Some googling around gave me a fix:
```
sudo setpci -s `lspci | grep -i "card reader" | awk '{ print $1; }'` 4c.b=0x22
```
Might help someone else also hopefully :-)

Now still waiting for a fix for the internal mic... doesn't work, whatever I try...

Greetings,
  Thijs.

---

### Post by Gargoulf on 2010-08-10
Hi!

Actually, I also have pb reading smart card (XD). I tried your fix (just copy paste since I don't really understand what it does) then dmesg gives: 
 tifm_core: SmartMedia/xD card detected in socket 0:0

but nothing happens. Is the card not mounted? How can I see where it is?
Thanks for your help!


> **atkaper said:**
> Hi there,

My M6500 with 10.04 on it also gave me problems with reading a 4gb micro sdhc card. Inserting the card did not mount it, and no /dev/* entry appeared. dmesg showed "tifm_core: MMC/SD card detected in socket 0:1" and "mmc1: error -110 whilst initialising SD card". Some googling around gave me a fix:
```
sudo setpci -s `lspci | grep -i "card reader" | awk '{ print $1; }'` 4c.b=0x22
```Might help someone else also hopefully :-)

Now still waiting for a fix for the internal mic... doesn't work, whatever I try...

Greetings,
  Thijs.

---

### Post by nataraj88 on 2010-08-15
Can anyone running Ubuntu on an M6500 confirm which SATA driver is loaded? Is it AHCI?  Does the driver or lspci tell you what the chipset is?

Thanks,
Nataraj

---

### Post by atkaper on 2010-08-16
Hi Gargoulf,

> **Gargoulf said:**
> 
Actually, I also have pb reading smart card (XD). I tried your fix (just copy paste since I don't really understand what it does) then dmesg gives: 
 tifm_core: SmartMedia/xD card detected in socket 0:0
but nothing happens.

Hmmm... sorry, I don't understand the kernel actions resulting from the suggested code also ;-)
I have just googled around, and found many suggestions, from which for me I seemded only to need this specific one-liner (I did construct the one-liner from some separate actions). Perhaps your SD reader gives you another identification string, or perhaps you need some of the other tips about removing/reloading some modules.

Let's try some things:

If I type this (command after the dollar), it shows me my card reader:
[PHP]
$ lspci | grep -i "card reader"
03:01.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
[/PHP]

Does that work for you ? If not, try typing just "lspci" by itself, and look for your card reader. If you find it, change the "card reader" in the grep into something which identifies your card reader. In that case retry the one-liner with the new string ;-)

String OK, but no success ? Try it like this (use the grep string that works for you):
[PHP]
sudo rmmod tifm_sd
sudo rmmod mmc_block
sudo rmmod sdhci
sudo rmmod tifm_7xx1
sudo rmmod tifm_core
sudo modprobe tifm_sd
sudo modprobe tifm_7xx1
sudo modprobe tifm_core
sudo modprobe mmc_core
sudo modprobe mmc_block
sudo setpci -s `lspci | grep -i "card reader" | awk '{ print $1; }'` 4c.b=0x22
sudo modprobe -v sdhci
[/PHP]

This is a combination of most tips I found, and if I execute this, it gives me these errors, but it functions OK:
[PHP]
ERROR: Module mmc_block does not exist in /proc/modules
ERROR: Module sdhci is in use by sdhci_pci
[/PHP]

I also would make sure to try this when you just booted the machine, and without a card in the reader, and only stick in the card after executing this script.

Hope this works for you... For me it does, and just pops up an auto-mounted folder view of the inserted card.

Greetings,
      Thijs.

---

### Post by atkaper on 2010-08-16
Hi Nataraj,

> **nataraj88 said:**
> Can anyone running Ubuntu on an M6500 confirm which SATA driver is loaded? Is it AHCI?  Does the driver or lspci tell you what the chipset is?

Thanks,
Nataraj

Sure, no problem, is this what you need?

[PHP]$ lspci | grep -i sata
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
[/PHP]

Not sure where to find the used driver. Does this help ?
[PHP]
$ dmesg | grep "SATA"
[    1.941176] ata1: SATA max UDMA/133 cmd 0x6e70 ctl 0x6e78 bmdma 0x6ea0 irq 19
[    1.941186] ata2: SATA max UDMA/133 cmd 0x6e80 ctl 0x6e88 bmdma 0x6ea8 irq 19
[    1.941494] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 19
[    1.941498] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 19
[    2.293101] ata4: SATA link down (SStatus 0 SControl 300)
[    2.308337] ata3: SATA link down (SStatus 0 SControl 300)
[    2.800929] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.800948] ata2.01: SATA link down (SStatus 0 SControl 300)
[    2.801162] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.801179] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[/PHP]

Just let me know if you need my to type another check command ;-)

Greetings,
   Thijs.

---

### Post by nataraj88 on 2010-08-16
The lspci identifies the chipset correctly. Thank you.  For the driver, you could try "lsmod | grep -i ahci".  If that doesn't produce anything, you could post the output from lsmod and I could figure out which driver is loaded.

For example on my older macbook, fedora 10 is using the ata_generic driver (as shown with lsmod).  The generic driver won't give very good disk performance.

I'm referencing this page for info on the better performing SATA drivers:  [https://ata.wiki.kernel.org/index.php/Hardware,_driver_status]("https://ata.wiki.kernel.org/index.php/Hardware,_driver_status")

Hopefully the M6500 uses the AHCI driver.  But if it's not using it, there's still hope.  I believe that the bios has to be set for AHCI instead of legacy.

Nataraj

---

### Post by Gargoulf on 2010-08-16
HI aktaper,

Here is what I get (the grep stuff on lspci gives exactly same message as yours)

[COLOR=#000000][COLOR=#0000BB]sudo rmmod tifm_sd 
ERROR: Module tifm_sd does not exist in /proc/modules

sudo rmmod mmc_block 
ERROR: Module mmc_block does not exist in /proc/modules

sudo rmmod sdhci 
ERROR: Module sdhci is in use by sdhci_pci

sudo rmmod tifm_7xx1 
ERROR: Module tifm_7xx1 does not exist in /proc/modules

sudo rmmod tifm_core 
ERROR: Module tifm_core does not exist in /proc/modules


sudo modprobe tifm_sd 
FATAL: Error inserting tifm_sd (/lib/modules/2.6.32-24-generic-pae/kernel/drivers/mmc/host/tifm_sd.ko): Unknown symbol in module, or unknown parameter (see dmesg)


sudo modprobe tifm_7xx1 
FATAL: Module tifm_7xx1 not found.

sudo modprobe tifm_core 
FATAL: Module tifm_core not found.

For the last 4 commands, no error:
sudo modprobe mmc_core 
sudo modprobe mmc_block 
sudo setpci [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]s [/COLOR][COLOR=#007700]`[/COLOR][COLOR=#0000BB]lspci | grep -i "card reader" | awk '{ print $1; }'[/COLOR][COLOR=#007700]` [/COLOR][COLOR=#0000BB]4c[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]b[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]0x22 
sudo modprobe [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]v sdhci  [/COLOR][/COLOR]


The card reader still doesn't work. And now dmseg gives:
  193.725209] tifm_sd: Unknown symbol tifm_eject
  193.725300] tifm_sd: Unknown symbol tifm_register_driver
  193.725570] tifm_sd: Unknown symbol tifm_unmap_sg
  193.725665] tifm_sd: Unknown symbol tifm_map_sg
  193.725770] tifm_sd: Unknown symbol tifm_unregister_driver


Any hint?
Thanks,

---

### Post by tahu363 on 2010-08-16
Well, as promising as this looks : [http://www.omgubuntu.co.uk/2010/08/multi-touch-comes-to-ubuntu-1010.html](http://www.omgubuntu.co.uk/2010/08/multi-touch-comes-to-ubuntu-1010.html),
It DOES mean we will need to wait for 10.10 for a trackpad fix. :(

---

### Post by Gargoulf on 2010-08-16
Thanks tahu363 for the info about touchpad. It's two months from now only.
I hope internal mic and card reader pb will also be fixed in next release.

---

### Post by atkaper on 2010-08-18
Hi Nataraj,

> **nataraj88 said:**
> If that doesn't produce anything, you could post the output from lsmod and I could figure out which driver is loaded.

Here are the modules loaded on my system, if there's any speed improvements possible, I'm of course interested to hear about them ;-)
[PHP]
$ lsmod
Module                  Size  Used by
ipt_REDIRECT            1269  3 
xt_tcpudp               2667  7 
iptable_nat             5219  1 
nf_nat                 19501  2 ipt_REDIRECT,iptable_nat
nf_conntrack_ipv4      12980  3 iptable_nat,nf_nat
nf_conntrack           73966  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
ip_tables              18358  1 iptable_nat
x_tables               22461  4 ipt_REDIRECT,xt_tcpudp,iptable_nat,ip_tables
binfmt_misc             7960  1 
ppdev                   6375  0 
rfcomm                 40214  4 
sco                     9473  2 
bridge                 53184  0 
stp                     2171  1 bridge
bnep                   11852  2 
l2cap                  34596  16 rfcomm,bnep
vboxnetadp              5235  0 
vboxnetflt             12242  1 
vboxdrv              1768311  4 vboxnetadp,vboxnetflt
deflate                 2181  0 
zlib_deflate           21834  1 deflate
ctr                     4029  0 
camellia               19220  0 
cast5                  15208  0 
rmd160                  8120  0 
sha1_generic            2231  0 
crypto_null             2950  0 
ccm                     8670  0 
serpent                18453  0 
blowfish                7882  0 
twofish                 5899  0 
twofish_common         14631  1 twofish
xcbc                    2847  0 
sha256_generic         10327  0 
sha512_generic          4972  0 
des_generic            16599  0 
cryptd                  8116  0 
aes_x86_64              7912  0 
aes_generic            27607  1 aes_x86_64
xfrm_user              21932  0 
ah6                     5035  0 
ah4                     4548  0 
esp6                    5376  0 
esp4                    5589  0 
xfrm4_mode_beet         2131  0 
xfrm4_tunnel            1979  0 
tunnel4                 2909  1 xfrm4_tunnel
xfrm4_mode_tunnel       2000  0 
xfrm4_mode_transport     1511  0 
xfrm6_mode_transport     1575  0 
xfrm6_mode_ro           1380  0 
xfrm6_mode_beet         2082  0 
xfrm6_mode_tunnel       1904  0 
ipcomp                  2212  0 
ipcomp6                 2214  0 
xfrm_ipcomp             5148  2 ipcomp,ipcomp6
xfrm6_tunnel            7935  1 ipcomp6
tunnel6                 2712  1 xfrm6_tunnel
af_key                 27834  0 
joydev                 10976  0 
btusb                  12969  2 
bluetooth              58557  9 rfcomm,sco,bnep,l2cap,btusb
snd_hda_codec_atihdmi     3055  1 
pcmcia                 35548  0 
snd_hda_codec_idt      63628  1 
dell_wmi                2177  0 
snd_hda_intel          23832  4 
arc4                    1473  2 
snd_hda_codec          99515  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6938  1 snd_hda_codec
snd_pcm_oss            40377  0 
snd_mixer_oss          16314  1 snd_pcm_oss
snd_pcm                87757  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1910  0 
snd_seq_oss            31714  0 
snd_seq_midi            5797  0 
snd_rawmidi            23161  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
fbcon                  39270  71 
snd_seq                57972  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tileblit                2487  1 fbcon
iwlagn                121641  0 
font                    8053  1 fbcon
iwlcore               124955  1 iwlagn
snd_timer              23085  2 snd_pcm,snd_seq
tifm_sd                 9628  0 
fglrx                2353166  44 
uvcvideo               62467  0 
videodev               40518  1 uvcvideo
yenta_socket           22901  1 
dell_laptop             7941  0 
v4l1_compat            15495  2 uvcvideo,videodev
tifm_7xx1               4674  0 
v4l2_compat_ioctl32    10811  1 videodev
tifm_core               7654  2 tifm_sd,tifm_7xx1
bitblit                 5811  1 fbcon
snd_seq_device          7176  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                64576  0 
softcursor              1565  1 bitblit
mac80211              238416  2 iwlagn,iwlcore
rsrc_nonstatic          9830  1 yenta_socket
sdhci_pci               6700  0 
dcdbas                  6886  1 dell_laptop
sdhci                  17928  1 sdhci_pci
led_class               3764  2 iwlcore,sdhci
snd                    72455  21 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                12757  1 
serio_raw               4950  0 
vgastate                9857  1 vga16fb
pcmcia_core            38176  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               8052  1 snd
cfg80211              148546  3 iwlagn,iwlcore,mac80211
snd_page_alloc          8692  2 snd_hda_intel,snd_pcm
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41084  0 
hid                    83408  1 usbhid
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
tg3                   122382  0 
[/PHP]

Greetings,
      Thijs

---

### Post by atkaper on 2010-08-18
Hi Gargoulf,

> **Gargoulf said:**
> 
The card reader still doesn't work.
Any hint?


Hmmm, no, sorry... Perhaps there's more info for you in this thread ( but of course you probably already found that one... :-) ):

[http://ubuntuforums.org/showthread.php?t=420721&page=3]("http://ubuntuforums.org/showthread.php?t=420721&page=3")

Hope it helps. By the way, did you try an SD card in there (with/without the tricks) ? It's possible that an XD card needs a different hack, some readers actually have two different reader devices in them...

Greetings,
     Thijs.

---

### Post by Gargoulf on 2010-08-23
Hi guys, 

Good news: Internal mic pb is SOLVED!

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/519066](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/519066)

---

### Post by atkaper on 2010-08-24
@Gargoulf; any luck with fixing your XD card?
Greetings, Thijs.

---

### Post by Gargoulf on 2010-08-25
No, no progress about XD card. 
Finally, I feel that 10.04 has many bugs and is not able to deal with the latest hardwares (fingerprint, touchpad, card reader, etc...). Hope this will be corrected in next release.

Cheers,
G.

---

### Post by Gargoulf on 2010-08-25
Dear all, 

I copy-paste here the description of a pb on boot that also affects me somethimes. Do you get same kind of freezing and has one of you find any solution? Seems its not only on M6500 but all PC under ubuntu 10.04.

"Occasionally my Ubuntu 10.04 PC won't boot properly.  It gets past  Grub and then stops at a blank screen and blinking cursor.  From what  I've read, this blinking cursor screen is presented by Ubuntu itself and  not Grub, so I assume the boot process gets halted for some reason.   Has anyone any guidance on how to diagnose this issue or what the cause  is likely to be?  Normally I need to press the reset button to reboot  the PC and often it will reboot fine.  The fact that it is intermittent  is what confuses me."

Thanks very much!
G.

---

### Post by atkaper on 2010-08-26
> **Gargoulf said:**
> Do you get same kind of freezing and has one of you find any solution? Seems its not only on M6500 but all PC under ubuntu 10.04.

I have had this kind of freezing a couple of times, but not in the last couple of weeks (or even months?) anymore... My guess is that it's some kind of hardware initialization timing issue. I have not searched for a fix, as it doesn't happen that often.

Greetings,
        Thijs.

---

### Post by nataraj88 on 2010-09-01
> **atkaper said:**
> Hi Nataraj,



Here are the modules loaded on my system, if there's any speed improvements possible, I'm of course interested to hear about them ;-)


Greetings,
      Thijs

I don't see any of the SATA drivers that are on the kernel.org website loaded on your system.  I'm sure there's a driver loaded, I just don't recognize it.

  My understanding is that there is a way to change the bios on the m6500 to use the native Intel device instead of generic emulation.  I would definitely backup my disks before changing this setting.

[https://ata.wiki.kernel.org/index.php/Hardware,_driver_status](https://ata.wiki.kernel.org/index.php/Hardware,_driver_status)



Nataraj

---

### Post by Maurizio_Giunti on 2010-09-16
Hi,

I run Ubuntu 10.4 64 bit on a Dell Precision M6500.
Everything works great on my system but the Standby: once it goes in standby it cannot wake up.
Wake up process starts but stop after few seconds. I can see a line of coloured dots at the top of the screen but the laptop is freezed and I have to switch it off.

In few (very rare) cases, it happened to work well, but usually it freezes.

Do your M6500 standby function work well?

Cheers,
Maurizio

---

### Post by tahu363 on 2010-10-11
Hey guys. Just did a clean install of 10.10 and am sad to report that I am having the SAME EXACT issues :( CD/DVD drive wont detect blank DVDs, touchpad is erratic, all the issues present in 10.04 seem to have carried over. Still testing stuff out, and I'll keep you updated, but its not looking good :(

---

### Post by Gargoulf on 2010-10-12
Hi,
Upgraded from 10.04 32bits to 10.10. At least one good news: microphone bug is solved without need of ppa alsa versions.
Haven't tested other stuff yet

---

### Post by Gargoulf on 2010-10-12
Hi again,
Lot's of noise about [COLOR=Red]multitouch[/COLOR] in ubuntu 10.10....but how to enable/test it? Installed utouch (not by default) but then??? Serious lack of info here!!

---

### Post by tahu363 on 2010-10-14
Have you tested out you CD/DVD drive? Its never worked for me... Also, I would also like the info on enabling multitouch - my trackpad is still buggy :( Anyone?

---

### Post by @xi0m on 2010-10-16
Subscribed.

How is the video performance in 10.10 with an ATI M7740?

I have a M6500 with
Core i7 Q820
12 GB RAM
ATI M7740

Thanks!

---

### Post by smarts53 on 2010-10-28
I tried installing ubuntu 10.10 on my precision 6500 today and when the ubuntu splash screen starts for the live cd, I get a very messed up screen. The screen rapidly flickers many different colored bands across the screen distorting the entire video image. It looks like almost colored static. I connected the laptop to an external monitor which worked fine. I then tried installing 9.04 which worked perfectly. I updated this to 9.10 which also worked perfectly. I then updated again to 10.04. This time I got the strange video problem. I then tried booting into recovery mode with failsafe graphics settings. The video then appears to work but my mouse and keyboard do nothing. The laptop has an ATI FirePro M7820 graphics card. 

I have no idea what to do, any help is hugely appreciated!

Ian

---

### Post by jblaze on 2010-11-04
> **smarts53 said:**
> I tried installing ubuntu 10.10 on my precision 6500 today and when the ubuntu splash screen starts for the live cd, I get a very messed up screen. The screen rapidly flickers many different colored bands across the screen distorting the entire video image. It looks like almost colored static. I connected the laptop to an external monitor which worked fine. I then tried installing 9.04 which worked perfectly. I updated this to 9.10 which also worked perfectly. I then updated again to 10.04. This time I got the strange video problem. I then tried booting into recovery mode with failsafe graphics settings. The video then appears to work but my mouse and keyboard do nothing. The laptop has an ATI FirePro M7820 graphics card. 

I have no idea what to do, any help is hugely appreciated!

Ian

Same issue here with same graphics card. Just tried 10.10 64bit with distorted video out after boot.  Switching login screens (via alt-F1) doesn't fix anything either.  I tried removing splash quiet from the boot options and do see the normal boot messages up to the point where X11 attempts to start. Must be something up with this M7820 / video drivers.  No clue as to what to try next so I may just have to go back to one of the pre 10.04, LTS releases for now. Anyone have any other suggestions?

---

### Post by johanhp on 2010-11-07
I had the same issue.

Fixed it by adding: radeon.new_pll=0 to my kernel boot commands.

---

### Post by @xi0m on 2010-11-07
I finally took the plunge and installed 10.10 on my 6500.  Everything is working fine including the 3D acceleration and my RAID1 array.

I have WINE installed and are running EVE Online and Team Fortress 2 perfectly.

---

### Post by jblaze on 2010-11-07
> **johanhp said:**
> I had the same issue.

Fixed it by adding: radeon.new_pll=0 to my kernel boot commands.

That worked like a charm! Typing this post from my 10.10 install.  I was even able to install the proprietary driver afterwards (totally expecting that to bonk out and cause me to have to reinstall) which worked as well. Thanks alot!

---

### Post by @xi0m on 2010-11-09
> **jblaze said:**
> That worked like a charm! Typing this post from my 10.10 install.  I was even able to install the proprietary driver afterwards (totally expecting that to bonk out and cause me to have to reinstall) which worked as well. Thanks alot!

Agreed. I was completely expecting the ATI drivers to bomb but they're actually working quite well.

---

### Post by cbrinegar on 2011-01-21
I have a work laptop that is a Dell Precision M6500 with the Intel i5 Core processor (kernel 2.6.32-27).  It runs Ubuntu Linux 10.04 64-bit, and I cannot burn a CD or DVD with it.  It seems not to recognize the blank disk in the drive.  I know the disk is fine, because the same disk put into my desktop or IBM Thinkpad behaves normally (Nautilus asks what to do).

I have seen some posts implying the firmware for the DVDRW drive may not be playing nicely.  I'm curious if anyone has figured out a fix for this problem.

---

### Post by jisaac on 2011-03-10
Did someone test:
[http://www.ubuntu.com/certification/hardware/201004-5601](http://www.ubuntu.com/certification/hardware/201004-5601)

I mean, did someone ask to DELL the special image of Ubuntu?

---

### Post by CedricFR on 2011-03-29
Hello,

I called Dell for my Dell Precision M6500 because I had screen bug when I want to install Ubuntu 10.04 32 Bits LTS.
They reply that image is only for pre installed system and that they can't give me this system image.
They said me that the computer can use Ubuntu 9.04 without problem.

So I had installed an Ubuntu 9.04, next upgrade to 9.10 and add the amd proprietary driver for my ATI FirePro M7740, and next I upgrade to 10.04 LTS.

The computer is now using Ubuntu 10.04 without screen problem. :popcorn:

Cédric

(Excuse me for my poor english :rolleyes:)

---

### Post by jisaac on 2011-03-30
Hi CedricFR,

You're probably interested by testing this image too (It's supposed to be ok with the M6500):
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=08W&l=en&s=bsdv&releaseid=R284592&SystemID=LAT2120&servicetag=&os=WN104&osl=en&deviceid=26290&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=0&libid=58&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=421648](http://support.dell.com/support/downloads/download.aspx?c=us&cs=08W&l=en&s=bsdv&releaseid=R284592&SystemID=LAT2120&servicetag=&os=WN104&osl=en&deviceid=26290&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=0&libid=58&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=421648)

See also this thread:
[http://ubuntuforums.org/showthread.php?t=1141757&page=21](http://ubuntuforums.org/showthread.php?t=1141757&page=21)

Or if you want to make your own iso see this link:
[http://en.community.dell.com/support-forums/software-os/w/linux/building-base-ubuntu-factory-iso.aspx](http://en.community.dell.com/support-forums/software-os/w/linux/building-base-ubuntu-factory-iso.aspx)

---

### Post by CedricFR on 2011-03-30
Hi Jisaac

Thanks for links, I try to use 10.04 in all my company computer, it's more easy to my team.

I'll look for a canonical image, but now I had give the M6500 to the user which need it.

If we bought another one I'll try to build an iso with ATI drivers.

Thanks for your help

Cédric

---

### Post by robisaks on 2011-08-31
Has any one tried using Virtual Box on these? I've been struggling off and on trying to get it to work for a few months. I've tinkered with the settings a million times and toyed with the BIOS too.

I started a thread on the virtual box forums (not much help):
[http://forums.virtualbox.org/viewtopic.php?f=7&t=36753](http://forums.virtualbox.org/viewtopic.php?f=7&t=36753)

And I opened a ticket with virtual box (also not much help):
[http://www.virtualbox.org/ticket/8487](http://www.virtualbox.org/ticket/8487)

(on a side note, when I disabled hyper threading in the bios, ubuntu's system monitor only displayed 2 CPUs, but virtualbox saw 4)

---

