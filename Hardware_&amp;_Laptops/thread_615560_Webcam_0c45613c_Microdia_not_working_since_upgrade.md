---
title: "Webcam 0c45:613c Microdia not working since upgrade to gutsy?"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by Ashrael on 2007-11-17
well my webcam used to work under feisty, but not so anymore... I realy dont know what is going wrong...
camstream doesnt see my cam, amsn same...

lsusb : Bus 002 Device 007: ID 0c45:613c Microdia 

lsmod:

Module                  Size  Used by
nls_cp437               6784  0 
isofs                  36412  0 
udf                    87204  0 
dv1394                 20824  0 
raw1394                31096  0 
ipv6                  273892  8 
af_packet              24840  2 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
button                  8976  0 
video                  18060  0 
sbs                    19592  0 
container               5504  0 
ac                      6148  0 
dock                   10656  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           137248  2 snd_emu10k1_synth
snd_ac97_codec        100644  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
sn9c102               120708  0 
joydev                 11328  0 
compat_ioctl32          2304  1 sn9c102
snd_seq_midi            9600  0 
gspca                 608336  0 
usbhid                 29536  0 
videodev               29312  2 sn9c102,gspca
v4l2_common            18432  2 sn9c102,videodev
v4l1_compat            15364  1 videodev
hid                    28928  1 usbhid
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
xpad                    9988  0 
serio_raw               8068  0 
snd                    54660  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
psmouse                39952  0 
emu10k1_gp              4736  0 
gameport               16776  2 emu10k1_gp
soundcore               8800  1 snd
shpchp                 34580  0 
i2c_sis96x              6404  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  1 i2c_sis96x
sis_agp                10116  1 
agpgart                35016  2 drm,sis_agp
evdev                  11136  3 
ext3                  133896  4 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  8 
ata_generic             8452  0 
floppy                 60004  0 
ohci1394               36528  1 dv1394
ieee1394               96312  4 dv1394,raw1394,sbp2,ohci1394
sis900                 24960  0 
mii                     6528  1 sis900
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  7 sn9c102,gspca,usbhid,xpad,ehci_hcd,ohci_hcd
pata_sis               15236  5 
libata                125168  2 ata_generic,pata_sis
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


anyone???

---

### Post by dannns on 2007-11-17
Maybe this post can help
[http://ubuntuforums.org/showthread.php?t=611816](http://ubuntuforums.org/showthread.php?t=611816)

---

### Post by Ashrael on 2007-11-17
THX! dannns, but i already solved it, another way by the way... i&#314;l explain...

first i blacklisted the v4l1_comapt module in /etc/modprobe.d/blacklist file by adding this: 
blacklist v4l1_compat      at the end of the file, in some cases this might already solve your problem, so reboot and try... Then amsn still did not want to see the camera, so i dug around a bit and installed : dov4l. when i started dov4l it gave me an error permission denied, made me think, so checked if i had execute rights for dov4l which i  had. then i did : ls -l/dev/video0 and found out that i had no rights to video0, which is usefull if you want to use it... so changed that with: sudo gpasswd -a USERNAME video. 

et voila! problem solved!

life can be so much fun!

---

### Post by RavanH on 2007-11-21
> **Ashrael said:**
> THX! dannns, but i already solved it, another way by the way... i&#314;l explain...

first i blacklisted the v4l1_comapt module in /etc/modprobe.d/blacklist file by adding this: 
blacklist v4l1_compat      at the end of the file, in some cases this might already solve your problem, so reboot and try... Then amsn still did not want to see the camera, so i dug around a bit and installed : dov4l. when i started dov4l it gave me an error permission denied, made me think, so checked if i had execute rights for dov4l which i  had. then i did : ls -l/dev/video0 and found out that i had no rights to video0, which is usefull if you want to use it... so changed that with: sudo gpasswd -a USERNAME video. 

et voila! problem solved!

life can be so much fun!

Hi, I have exactly the same issue. My X-Gear Easyglow ( == Microdia) webcam used to work on Feisty, but no longer on Gutsy. And I found the same permission denied error using camorama ... but following your steps to ad myself to the video group did not make a difference :(

```
ravanhagen@ravan-laptop:~$ dov4l
dov4l v0.9, (C) 2003-2006 by folkert@vanheusden.com

cannot open device /dev/video0! (Permission denied)
ravanhagen@ravan-laptop:~$ sudo gpasswd -a ravanhagen video
Gebruiker 'ravanhagen' wordt toegevoegd aan groep 'video'
ravanhagen@ravan-laptop:~$ dov4l
dov4l v0.9, (C) 2003-2006 by folkert@vanheusden.com

cannot open device /dev/video0! (Permission denied)
```

Is there any other way to resolve this permissions issue?

UPDATE: after reboot the response has changed a little:
```
$ dov4l
dov4l v0.9, (C) 2003-2006 by folkert@vanheusden.com

cannot open device /dev/video0! (No space left on device)
```

---

### Post by QuinnStorm on 2007-11-28
It looks like you need linux-ubuntu-modules-`uname -r` installed to make it work, after that & a depmod, mine works (the depmod should happen on reboot too)

Basically it needs to load the gspca driver and isn't

---

### Post by RavanH on 2007-11-30
> **QuinnStorm said:**
> It looks like you need linux-ubuntu-modules-`uname -r` installed to make it work, after that & a depmod, mine works (the depmod should happen on reboot too)

Basically it needs to load the gspca driver and isn't

So I did ```
 sudo apt-get install linux-ubuntu-modules-`uname -r`
``` in terminal but got a message about it already being installed and being the latest version...

Or do I misunderstand you here?

If I do ```
$ lsmod |grep gspca
``` I get response ```
gspca                 617808  0 
videodev               31360  3 uvcvideo,gspca,sn9c102
usbcore               161584  8 uvcvideo,gspca,acecad,sn9c102,usbhid,ehci_hcd,ohci_hcd
```

Does that not mean the gspca driver gets loaded? Or maybe the other drivers interfere?

---

### Post by Koppie on 2007-12-02
> **RavanH said:**
> So I did ```
 sudo apt-get install linux-ubuntu-modules-`uname -r`
``` in terminal but got a message about it already being installed and being the latest version...

Or do I misunderstand you here?

If I do ```
$ lsmod |grep gspca
``` I get response ```
gspca                 617808  0 
videodev               31360  3 uvcvideo,gspca,sn9c102
usbcore               161584  8 uvcvideo,gspca,acecad,sn9c102,usbhid,ehci_hcd,ohci_hcd
```

Does that not mean the gspca driver gets loaded? Or maybe the other drivers interfere?

I'm having the same problem.  Webcam worked fine under Feisty but under Gutsy the video is green.  It's also been discussed in this thread:  [http://ubuntuforums.org/showthread.php?t=621815](http://ubuntuforums.org/showthread.php?t=621815)

That thread claims that sn9c102 will be a "no go" under Gutsy.  But it worked under Feisty!  Should I just give up and buy a new webcam?

---

### Post by RavanH on 2007-12-13
UPDATE:

I managed to get the Macrodia cam working (but sadly with a REALLY dark image only) by blacklisting the sn9c102 driver and removing the uvcvideo driver .ko file... So only the gspca driver remains active.

Read more on [http://ubuntuforums.org/showthread.php?p=3941436#post3941436](http://ubuntuforums.org/showthread.php?p=3941436#post3941436)

---

### Post by vivalant on 2008-01-05
Try the Generic SN9CXXX driver, which is not the same as the sn9c102:
[http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by RavanH on 2008-01-07
> **vivalant said:**
> Try the Generic SN9CXXX driver, which is not the same as the sn9c102:
[http://www.linux-projects.org](http://www.linux-projects.org)

No 64bit version ? :(

---

### Post by gijsterbeek on 2008-02-22
Hi,

Blacklisting both v4l1_compat AND sn9c102 did the trick for me.

---

### Post by gijsterbeek on 2008-02-22
> **RavanH said:**
> 
cannot open device /dev/video0! (No space left on device)

I had the same thing. First I read some posts about the usb hub being too crowded, so I ventured into solving this problem. Long story short: it didn't help. 

Then I saw this post, and did the following:

1. In /etc/X11/xorg.conf I added ```
 Load "v4l2" 
``` in the Modules section 
2. I blacklisted both v4l1_compat and sn9c102 in /etc/modprobe.d/blacklist
3. Rebooted. camera worked

Earlier, when the camera didn't work, the camera-LED was on all the time. Now, with the changes mentioned above, it's only on when the camera is activated. 

Also, my built-in TV card (another video capture source) still works fine.

---

### Post by Koppie on 2008-02-23
I found another solution: install PCLinuxOS.  I was a loyal Kubuntu user for a full year, but I've discovered PCLinuxOS (for my desktop and old webcam) and Mandriva (for my laptop) both have better hardware support.  With these distros I didn't have to blacklist anything; my hardware Just Worked.

---

