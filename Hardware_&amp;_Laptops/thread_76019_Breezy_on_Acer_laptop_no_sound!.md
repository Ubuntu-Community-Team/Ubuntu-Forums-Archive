---
title: "Breezy on Acer laptop no sound!"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by iNerdSure on 2005-10-14
Breezy is the best distro I have installed so far. Have tried Mandriva 9.0 and 10.2 LE with many devices not detected. Then I experimented with Knoppix 4.0.2 LiveCD, Ubuntu 5.10rc LiveCD. And, now Breezy Badger 5.10 .. the best experience so far on my Acer 4061. Have decided to throw out WinXP.

However, the sound of silence is a let down. I hope someone has a simple explanation and an easy solution for a newbie Linux convert to fix this bug.

My :~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller ( rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definiti on Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controlle r
0000:06:04.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)


And     :~$ lsmod
Module                  Size  Used by
usbhid                 30688  0
nls_utf8                2176  0
nls_cp437               5888  0
vfat                   12288  0
fat                    46492  1 vfat
sd_mod                 17424  0
usb_storage            64704  0
scsi_mod              124872  2 sd_mod,usb_storage
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
i915                   17920  1
drm                    58004  2 i915
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  8
af_packet              20232  2
rtc                    11832  0
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
snd_hda_intel          15872  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
dm_mod                 50364  4
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  5 usbhid,usb_storage,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,piix
unix                   24624  849
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

Thanks in advance.

---

### Post by Muffe on 2005-10-14
I have the same problem on a Travelmate 3000. I have already posted a thread here: [http://ubuntuforums.org/showthread.php?t=75979](http://ubuntuforums.org/showthread.php?t=75979) It is probably something with the drivers... I wonder about upgrading to the 2.6.13 kernel...

---

### Post by spooky-mac on 2005-10-14
Have you checked if everything got unmuted? Have you run alsaconf already from a terminal as superuser or root?

---

### Post by Muffe on 2005-10-14
Here is the message I get when I try to run amixer as root:

```
amixer: Mixer attach default error: No such file or directory
```

and when I run alsamixer:

```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

Guess it's not unmuted channels...

---

### Post by shenki on 2005-10-14
see [URL="http://ubuntuforums.org/showthread.php?p=412151#post412151"]http://ubuntuforums.org/showthread.php?p=412151#post412151
[/URL]
This is about the 5th post thismorning I've read on the Intel HD Audio (ICH6) sound not working. It seems the issue is much more widespread than previously thought, and should have been fixed before releasing breezy.

---

### Post by iNerdSure on 2005-10-15
[QUOTE=spooky-mac]Have you checked if everything got unmuted? Have you run alsaconf already from a terminal as superuser or root?[/QUOTE]

Yes, I have un-mute all settings via alsamixer. Anyway, on Breezy, there is no superuser or root access by default. The first "user" is the "admin" as well. And there's no "alsaconf" command in Breezy.

Can you please elaborate. Thanks.

---

### Post by kingsidy on 2005-10-15
i installed it on an acer aspire 1680 and everything run fine just as it did in hoary.

---

### Post by iNerdSure on 2005-10-15
Any special setting that you used on Acer 1680?

---

### Post by er-ku on 2005-10-28
Hello, iNerdSure,
have you resolved your problem or not? I'm now having exactly the same problem with a TravelMate 4061NLMi, and I want it solved. If you are already able to play music in Linux on your laptop, i'd really appreciate if you told us what you've done to achieve that... :)

regards,
newly registered RQ :)

---

### Post by Muffe on 2005-10-28
I still have this problem too, but the only thing I've tried to do to solve it is to download and recompile the 2.6.13 kernel, all settings as in the 2.6.12 kernel shipped with Breezy as default.

I've heard rumours about a bug related to Intel HDA controllers in the ALSA 1.0.9b package (the one that comes with Breezy), so maybe an upgrade to 1.0.10rc2 may do the trick... I don't know.

If someone get this soundcard to work, please post a walkthrough or something to let us others know.

---

### Post by Muffe on 2005-10-28
OK: I've searched thorugh the ALSA 1.0.10rc1 [changelog]("http://www.alsa-project.org/changes/v1-0-9b--v1-0-10rc1.txt") and I found this intresting:

>  + HDA Intel driver
    - hda-codec - Add support of more models with ALC codecs
    - hda-codec - More fix of ALC880 codec support
    - hda: enable unsolicited responses
    - hda-intel - Add SiS966 support
    - hda-intel: Suspend/resume fixes for PCM devices
  + HDA generic driver
    - hda-codec - Print all AMP IN values
    - hda-codec - More fix of ALC880 codec support
    - Summar: hda-codec - MFG support
    - hda-codec - support for Si3054/5 HDA modems

> + HDA Intel driver
    - Summary: hda-codec - Add support of more models with ALC codecs
      Merged the work of pshou <pshou@realtek.com.tw> for the support of
      more models with ALC codecs: ALC880 ASUS, Uniwill, FSC1734, generic 6-stack,
      and ALC260 HP.  Tests with the real hardwares are appreciated.
      The codec patch is cleaned up:  The preset configuration of codecs are
      stored in the table and copied to the spec instance.
      Added/fixed comments.
    - Summary: hda-codec - More fix of ALC880 codec support
      - Fix some invalid configurations, typos in the last patch
      - Make init_verbs chainable, so that different configs can share the same
        init_verbs
      - Reorder and clean up the source codes in patch_realtek.c
      - Add the pin default configuration parser, used commonly in cmedia
        and realtek patch codes.
      - Add "auto" model to ALC880 for auto-configuration from BIOS
        Use this model as default, and 3-stack as fallback
    - Summary: hda: enable unsolicited responses
      Patch enables unsolicited responses on the HDA controller. Without
      the UREN bit set, the controller will not place unsolicited responses
      in a RIRB.
      Signed-off-by: Matt <matt@embeddedalley.com>
    - Summary: hda-intel - Add SiS966 support
      Added SiS966 pci id to snd-hda-intel driver.
    - Summary: hda-intel: Suspend/resume fixes for PCM devices
      - removed SNDRV_PCM_INFO_RESUME (the driver cannot do PCM resume at the time)
      - fixed chip->pcm_devs initialization
  + HDA generic driver
    - Summary: hda-codec - Print all AMP IN values
      Print all AMP IN values when multiple nodes are connected.
    - Summary: hda-codec - More fix of ALC880 codec support
      - Fix some invalid configurations, typos in the last patch
      - Make init_verbs chainable, so that different configs can share the same
        init_verbs
      - Reorder and clean up the source codes in patch_realtek.c
      - Add the pin default configuration parser, used commonly in cmedia
        and realtek patch codes.
      - Add "auto" model to ALC880 for auto-configuration from BIOS
        Use this model as default, and 3-stack as fallback
    - Summar: hda-codec - MFG support
      This adds Modem Functional Group (MFG) support and option for 9600
      sample rate.
      Signed-off-by: Sasha Khapyorsky <sashak@smlink.com>
    - Summary: hda-codec - support for Si3054/5 HDA modems
      Support for Si3054/5 HDA modem codecs.
      Signed-off-by: Sasha Khapyorsky <sashak@smlink.com>

So I guess the 1.0.10 has some changes that *may* fix the Intel HDA cards.... But I have not read everything, so I cannot sayanything for sure.

---

### Post by athem on 2005-10-29
I'm running Breezy on an Acer Travelmate 8104WLMi, with Intel HDA sound.  I struggled to get it working for a week.  ALSA was installed by default, but no sound.  Then I accidentally did this from the main panel menu:

Applications-->Sound & Video-->Volume Control

Then, in the Volume Control application menu I changed the device:

 File-->Change Device-->Realtek ALC880 (OSS Mixer)

and got sound for the first time.  I'm not sure why the ALSA device didn't work, but the Realtek one seems to work OK.  I'm curious what others' experience has been with this.

:D

---

### Post by er-ku on 2005-10-29
[QUOTE=athem]I'm running Breezy on an Acer Travelmate 8104WLMi, with Intel HDA sound.  I struggled to get it working for a week.  ALSA was installed by default, but no sound.  Then I accidentally did this from the main panel menu:

Applications-->Sound & Video-->Volume Control

Then, in the Volume Control application menu I changed the device:

 File-->Change Device-->Realtek ALC880 (OSS Mixer)

and got sound for the first time.  I'm not sure why the ALSA device didn't work, but the Realtek one seems to work OK.  I'm curious what others' experience has been with this.

:D[/QUOTE]

At least for me, it doesn't seem to help :( BTW, it's ALC260 in my case, not ALC880.

ALso, there are three more problems with this laptop:
* Gnome battery plugin always says the system is running on AC power, and battery is always at zero.  And I'm constantly getting this in the syslog:
```
[4295598.080000] search_node dffe5fc0 start_node dffe5fc0 return_node 00000000
[4295598.080000]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node dffe5ec0), AE_NOT_FOUND
[4295628.084000]     ACPI-0362: *** Error: Looking up [Z00A] in namespace, AE_NOT_FOUND
[4295628.084000] search_node dffe5fc0 start_node dffe5fc0 return_node 00000000
[4295628.084000]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node dffe5ec0), AE_NOT_FOUND
[4295658.089000]     ACPI-0362: *** Error: Looking up [Z00A] in namespace, AE_NOT_FOUND
```

* Wireless and bluetooth leds are always off, even when I turn WLAN ant BT on. That's kinda konfusing, as I never know if the transmitter/reciever is actually on or off.

* Some of the keystrokes seem to be ignored. This applies to Fn+F2 (Acer eSettings), Fn+F3 (Acer ePower Management), Fn+F4 (Sleep), and additional Euro and $ (bottom right corner of the keyboard).

---

### Post by Muffe on 2005-10-29
[QUOTE=athem]I'm running Breezy on an Acer Travelmate 8104WLMi, with Intel HDA sound.  I struggled to get it working for a week.  ALSA was installed by default, but no sound.  Then I accidentally did this from the main panel menu:

Applications-->Sound & Video-->Volume Control

Then, in the Volume Control application menu I changed the device:

 File-->Change Device-->Realtek ALC880 (OSS Mixer)

and got sound for the first time.  I'm not sure why the ALSA device didn't work, but the Realtek one seems to work OK.  I'm curious what others' experience has been with this.

:D[/QUOTE]

That does not help me very much, because I cannot open the volume control.It's just telling me a unch of errors.

---

### Post by er-ku on 2005-11-04
[QUOTE=er-ku]Some of the keystrokes seem to be ignored. This applies to Fn+F2 (Acer eSettings), Fn+F3 (Acer ePower Management), Fn+F4 (Sleep), and additional Euro and $ (bottom right corner of the keyboard).[/QUOTE]

Wooo! At least I've managed to get Suspend To RAM working. Now I can press Fn+F4, and I get a suspended system in less than 5 seconds. After pressing "any key", I get it back in less than 10 secs.

Tweaking that, I became aware of a **dmidecode** command, and here's something interesting it told me:

```

Handle 0x000D
        DMI type 10, 6 bytes.
        On Board Device Information
                Type: Sound
                Status: Disabled
                Description: ADI

```

Could the sound issue be related to the **disabled** status of the device?

---

### Post by iNerdSure on 2005-11-13
[QUOTE=er-ku]Wooo! At least I've managed to get Suspend To RAM working. Now I can press Fn+F4, and I get a suspended system in less than 5 seconds. After pressing "any key", I get it back in less than 10 secs.

Tweaking that, I became aware of a **dmidecode** command, and here's something interesting it told me:

```

Handle 0x000D
        DMI type 10, 6 bytes.
        On Board Device Information
                Type: Sound
                Status: Disabled
                Description: ADI

```
Could the sound issue be related to the **disabled** status of the device?[/QUOTE]
Hi, sorry I did not respond your query earlier. I hope you've solved the "No Sound" bug by now. I am still struggling with mine.
My Acer 4061 laptop has the same sympton"
> 
Handle 0x000D
        DMI type 10, 6 bytes.
        On Board Device Information
                Type: Sound
                Status: Disabled
                Description: ADI

I wonder is you a solution by now, or at least a better understanding of the problem.

---

### Post by Muffe on 2005-11-13
My dmidecode output is mostly the same as the two last posts, and I have not solved the problem either... Really frustrating.

---

### Post by er-ku on 2005-11-14
[QUOTE=iNerdSure]Hi, sorry I did not respond your query earlier. I hope you've solved the "No Sound" bug by now. I am still struggling with mine.
My Acer 4061 laptop has the same sympton"

I wonder is you a solution by now, or at least a better understanding of the problem.[/QUOTE]

Nope, the sound is still off. And the [ALSA bugreport]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1517") is still silent.

Maybe we should try ubuntu-users mailing list instead of this forum?

---

### Post by iNerdSure on 2005-11-14
[QUOTE=er-ku]Nope, the sound is still off. And the [ALSA bugreport]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1517") is still silent.

Maybe we should try ubuntu-users mailing list instead of this forum?[/QUOTE]
Have not tried the unbutu users mailing list yet. But from the numerous sound problems posted on this forum, and others, I get a sense that the problem is quite widespread. Our laptops may besilent. But we are certainly not a silent majority!

I do hope the minority who have solved the sound problems share their solutions on this forum.  :rolleyes:

---

### Post by Moebius on 2005-11-14
Hi guys, Acer owner here as well.

I have a 1712 SMI, and as for sound problems I had a few, but was able to sort them out.

All was well in Hoary, but had some problems with Breezy. Sound worked from the get go, but was unable to have multiple sounds. After 1001 changes to asound.conf and esd.conf, I still could only get sound for 1 program at the time.

After searching for my soundcard in these forums (it's a Intel ICH5 bwt) it seemed to be a kernel problem in 2.6.12, but as I'm still new to many aspects in linux, I didn't dare to compile a more advanced kernel.

Yesterday, I managed to finnaly put my system playing multiple sounds, by instaling **polypaudio** package. Sound is working great now.

One other thing that I recomend is to look in to the **alsamixer** for muted sounds. I had that once without knowing and was cursing on the asound.conf and esd.conf without reason.

Hope you guys can fix your problems, if you want I can place here a copy of my esd.conf and asound.conf 

Best of luck,

Moe

---

### Post by er-ku on 2005-11-14
[QUOTE=Moebius]
After searching for my soundcard in these forums (it's a Intel ICH5 bwt) it seemed to be a kernel problem in 2.6.12, but as I'm still new to many aspects in linux, I didn't dare to compile a more advanced kernel.
[/QUOTE]

Hi, Moebius,

Our particular problem is a bit different. Our hardware is based on ICH6, not ICH5, and a different (and quite fresh, btw) ALSA driver is responsible for our sound...

[QUOTE=Moebius]
Yesterday, I managed to finnaly put my system playing multiple sounds, by instaling **polypaudio** package. Sound is working great now.
[/QUOTE]

being a bit advanced user, I'm not sure it's a good idea. :) polypaudio is just a replacement for ESD. Now you're having four layers of sound processing. First, your application decodes, say, an mp3 file, then it tells something to Gstreamer, which in turn tells something to polypaudio, which in turn tells something to ALSA (or maybe even to ALSA's OSS emulation layer). I would prefer Gstreamer speaking directly to ALSA+dmix.

Furthermore, the low-level driver still remains the same. In our case it wouldn't work anyways...  :(

[QUOTE=Moebius]
One other thing that I recomend is to look in to the **alsamixer** for muted sounds. I had that once without knowing and was cursing on the asound.conf and esd.conf without reason.
[/QUOTE]

We've done that already. At least I have. :) It's a different problem, as I said...

[QUOTE=Moebius]
Hope you guys can fix your problems, if you want I can place here a copy of my esd.conf and asound.conf 
[/QUOTE]

Thank you so much for your care. :) But in this case, it won't help, IMHO... :(

---

### Post by mistergq on 2005-11-28
I am wondering if there has been a solution to this problem.  I am running a Gateway 4520.  I have an Intel 82801db-ch4 audio adapter.  No sound.  I recompiled to 2.6.14 vanilla kernile, but that did not solve the problem.  Any other suggestions?

---

### Post by iNerdSure on 2005-11-28
[QUOTE=mistergq]I am wondering if there has been a solution to this problem.  I am running a Gateway 4520.  I have an Intel 82801db-ch4 audio adapter.  No sound.  I recompiled to 2.6.14 vanilla kernile, but that did not solve the problem.  Any other suggestions?[/QUOTE]
Unfortunately, I have not found any solution yet. I've been searching other forums for similar "no sound" and "Intel 915 GM" integrated chipset postings. So far, I have not come across any definitive solution.  :(

---

### Post by er-ku on 2005-12-04
I've just installed the latest self-compiled alsa-modules. Still nothing. :( The module loads and unloads nicely, but there's still total silence.

Good, but irrelevant news are that I've found out how to make the WLAN led work:

```

sudo echo "options ipw2200 led=1" >> /etc/modprobe.d/ipw2200.modprobe

```

**Edit: this line is bad, look below**

After reloading the ipw2200 module, the led stards to blink. ;)

---

### Post by iNerdSure on 2005-12-04
[QUOTE=er-ku]I've just installed the latest self-compiled alsa-modules. Still nothing. :( The module loads and unloads nicely, but there's still total silence.

Good, but irrelevant news are that I've found out how to make the WLAN led work:

```

sudo echo "options ipw2200 led=1" >> /etc/modprobe.d/ipw2200.modprobe

```

After reloading the ipw2200 module, the led stards to blink. ;)[/QUOTE]
This is great news. I haven't been able to get the WLAN working from the beginning. . I ran the command:
 [PHP]sudo echo "options ipw2200 led=1" >> /etc/modprobe.d/ipw2200.modprobe[/PHP] and got:

[PHP]bash: /etc/modprobe.d/ipw2200.modprobe: Permission denied
[/PHP]
Can you please help with the step-by-step details. 
(The continued silence no sound barrier is really deafening!)

---

### Post by er-ku on 2005-12-05
> **iNerdSure]This is great news. I haven't been able to get the WLAN working from the beginning. .[/QUOTE]

Actually, WLAN was working. Just the led wasn't 

> 
 I ran the command:
 [PHP]sudo echo "options ipw2200 led=1" >> /etc/modprobe.d/ipw2200.modprobe[/PHP] and got:

[PHP]bash: /etc/modprobe.d/ipw2200.modprobe: Permission denied
[/PHP]
Can you please help with the step-by-step details. 

OK, sorry.  said:**
> 
(The continued silence no sound barrier is really deafening!)


Same here... :/

---

### Post by mohitcool_buddy on 2005-12-05
hello..what is this breezy..idont understad a bit

---

### Post by Kallewoof on 2005-12-05
[QUOTE=er-ku]Actually, WLAN was working. Just the led wasn't [/QUOTE]

Sweet. Your fix did it for my Fujitsu-Siemens Amilo Pro as well. Thanks! :)

-Kalle.

p.s. To clarify, the fix = getting the LED to show. Wireless was working fine always. d.s.

---

### Post by er-ku on 2005-12-05
[QUOTE=mohitcool_buddy]hello..what is this breezy..idont understad a bit[/QUOTE]

Breezy is the latest stable release of Ubuntu.

You said sound is working for you? Which version of Ubuntu are you using? Would you please post outputs of "lspci -vv", "lsmod", "sudo dmidecode" and "uname -a" to here? 

Thanks!

---

### Post by er-ku on 2005-12-05
[QUOTE=Kallewoof]Sweet. Your fix did it for my Fujitsu-Siemens Amilo Pro as well. Thanks! :)

-Kalle.

p.s. To clarify, the fix = getting the LED to show. Wireless was working fine always. d.s.[/QUOTE]

Actually, I don't understand why this feature is not used in the ipw2200 driver by default (you have to explicitly enable it). If anyone asked me, I'd swap this behaviour. Maybe it's at least worth to suggest that to Ubuntu developers? :)

---

### Post by iNerdSure on 2005-12-05
Er-ku, fantastic. First time I see wireless LED blinking on front of my Acer 4061 TM4061 NWLMi for the first time since Breezy was installed on Oct 15th. Many thanks. :D 

I'm going to try getting connected at my usual cafe hotspots over the next couple of days to see if my wireless network is working ok.

One more big challenge is the SOUND. I read in other forums that upgrading the ALSA driver may work. But, I can't follow the steps, from the very technical description. I'd rather live with a SILENT laptop than a non-working laptop for the time being.

Many thanks, again.

---

### Post by er-ku on 2005-12-06
[QUOTE=iNerdSure]Er-ku, fantastic. First time I see wireless LED blinking on front of my Acer 4061 TM4061 NWLMi for the first time since Breezy was installed on Oct 15th. Many thanks. :D
[/QUOTE]
Your welcome! :)

> 
One more big challenge is the SOUND. I read in other forums that upgrading the ALSA driver may work. But, I can't follow the steps, from the very technical description. I'd rather live with a SILENT laptop than a non-working laptop for the time being.


We've got [one report](http://ubuntuforums.org/showthread.php?t=99222) from **mohitcool_buddy** that sound is working on a similar laptop. Isn't that cool? :) Now we just have to figure out what's different in his setup.

---

### Post by mohitcool_buddy on 2005-12-06
hey....er-ku...regarding your mail.....let me confirm that after pasting these commands...all is working absolutely fine on my acer 4061..i dunno why urs is giving problems..anyway....take care

---

### Post by er-ku on 2005-12-06
[QUOTE=mohitcool_buddy]hey....er-ku...regarding your mail.....let me confirm that after pasting these commands...all is working absolutely fine on my acer 4061..i dunno why urs is giving problems..anyway....take care[/QUOTE]

Noo... I wanted you to paste what those commands say, not to just execute them...

Please!

---

### Post by iNerdSure on 2005-12-06
Er-ku, Like the wireless LED, is there a similar command to turn on the bluetooth LED as well? Many thanks.

---

### Post by er-ku on 2005-12-07
[QUOTE=iNerdSure]Er-ku, Like the wireless LED, is there a similar command to turn on the bluetooth LED as well? Many thanks.[/QUOTE]

I wish I knew... 

I'm not sure (and I have no Bluetooth-equiped devices), but I think the light will light up itself when the Bluetooth is configured correctly and powered on. Now you need a generic Bluetooth configuration guide/HOWTO to do that.

You should probably try packages like *gnome-bluetooth* and/or *bluez-utils* here. Also, try searching the forums for questions and answers about bluetooth and apply the solutions to your case. Let me know if that succeeds. :)

---

### Post by iNerdSure on 2005-12-07
Er-ku, thank you. I haven't explored the bluetooth yet, as my priority was to get the sound working. Bluetooth was for connecting via my mobile phone GPRS service when I have no access to wireless hotspots. But first things first, SOUND. Unless I stumble across others while searching for sound.

---

### Post by mentat on 2005-12-09
Hi. I'm running Breezy (just upgraded from Hoary) on an Acer 4002WLMi, and sound was not working either, until I did the same thing (Applications --> Sound&Video --> Volume Control; File -->Change Device, then I chose "Conexant id30 (OSS mixer)" instead of "Intel 82801DB-ICH4 (Alsa Mixer)", et voilá, sound is working fine! Here is what I think are the relevant bits of the output of lsmod:


Module                  Size     Used by
...
snd_intel8x0           30144  2
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

Good luck,

Pedro

---

### Post by crichell on 2005-12-09
I solved the sound problem by upgrading to Alsa 1.0.10.  This is on a notebook with Intel HDA and the Realtek ALC 880 chipset.  May work if you have a different chipset as well.

The How To - [http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy](http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy)

---

### Post by Shinkan on 2005-12-09
I there !

I have and Acer Aspire 1641 WLMi, and I've had many problems :

- Battery charge detection doesn't work
> Solved by corecting myself my dumped DSDT. Can send it to somebody.

- Resolution is bad @ 1024x768, I need 1280x800 !!
> Solved by using 915resolution tool. Ask google, works fine.

- Leds-buttons (Wifi, Bluetooth) or special keys doesn't work.
> Solved by using acerhk module. Ask google, works fine but it's gadget.

One problem remains :

- Can't have any dB of sound with my Intel High Definition Audio (HDA) sound system. I have the Realtek ALC260 Codec.
What I've done ?
Downloading and installing alsa-driver, lib and utils 1.0.10.
Leveling sounds channel up, unmuting channels.
That doesn't work ...
I really don't know how to do.
The Realtek code ALC880 seems to work with many users (with or without efforts), but ALC260 doesn't, and I have no info on this chip ... google is quiet.

Any help would be greatly appreciated.
Sorry for my english, I'm french and it's 4 am here ... :confused:

---

### Post by iNerdSure on 2005-12-09
[QUOTE=crichell]I solved the sound problem by upgrading to Alsa 1.0.10.  This is on a notebook with Intel HDA and the Realtek ALC 880 chipset.  May work if you have a different chipset as well.

The How To - [http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy](http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy)[/QUOTE]
Thanks. Followed steps in link till the end at: sudo alsaconf , and got these error messages:
[PHP]
Running update-modules...
Loading driver...
FATAL: Error inserting snd_pcm (/lib/modules/2.6.12-10-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.12-10-386/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.12-10-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.12-10-386/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.12-10-386/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_hda_intel
Setting default volumes...
[/PHP]
What should I do to get these errors fixed?  :confused:   Thanks.

---

### Post by er-ku on 2005-12-10
[QUOTE=iNerdSure]Thanks. Followed steps in link till the end at: sudo alsaconf , and got these error messages:
[PHP]
Running update-modules...
Loading driver...
FATAL: Error inserting snd_pcm (/lib/modules/2.6.12-10-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
<...>
[/PHP]
What should I do to get these errors fixed?  :confused:   Thanks.[/QUOTE]


I've just took a quick look at that manual. Not very clean, IMHO. ;)

As I mentioned, I had alsa 1.0.10 running Ubuntu way (installed everything with dpkg/apt-get), and it didn't help indeed. Maybe I missed something though...

And the Ubuntu way (IMHO) is:
[LIST]
[*]Getting and installing the packages:
[LIST][*][http://packages.ubuntu.com/dapper/source/alsa-driver](http://packages.ubuntu.com/dapper/source/alsa-driver)
[*][http://packages.ubuntu.com/dapper/source/alsa-oss](http://packages.ubuntu.com/dapper/source/alsa-oss)
[*][http://packages.ubuntu.com/dapper/source/alsa-utils](http://packages.ubuntu.com/dapper/source/alsa-utils)
[/LIST]
[*]Getting and installing linux-headers for your kernel:
```
$ sudo apt-get install linux-headers-`uname -r`
```
Note the backticks. This means you'll install linux-headers-something-something, where "something-something" is the output of "uname -r".
[*]Getthing and installing other packages that are required to build those sources,
[*]Compiling the sources and installing the freshly-made packages,
[*]Compiling alsa-modules (from newly-installed alsa-source),
[*]installing it.
[/LIST]

This info isn't full. As I said, the Acer laptop is my mothers, so I cannot access it every day. **crichell**, you may have more info about what packages you need to install in order to compile alsa. You may also want to update your HOWTO a little...

However, as I said, installing alsa 1.0.10 didn't help me somewhy. Maybe I missed something...

---

### Post by crichell on 2005-12-10
[QUOTE=iNerdSure]What should I do to get these errors fixed? Thanks.[/QUOTE]

This was tested on a clean install - it's always easier when their clean although it is a luxury.  Did everything compile and install for you?  I've been looking for the alsaconf errors but the threads are sparse - If we can get that to run you should be in business.

---

### Post by crichell on 2005-12-10
[QUOTE=er-ku]**crichell**, you may have more info about what packages you need to install in order to compile alsa. You may also want to update your HOWTO a little...[/QUOTE]

The packages needed to compile alsa, libs, plugins, and utils are build-essential gcc-3.4 libjack0.80.0-dev linux-source-2.6.12 - They're in the Install Dependencies section.  I'll update the how to as we work through this.  I'd like it to work for everyone - these forums help with that.

---

### Post by er-ku on 2005-12-10
[QUOTE=crichell]The packages needed to compile alsa, libs, plugins, and utils are build-essential gcc-3.4 libjack0.80.0-dev linux-source-2.6.12 - They're in the Install Dependencies section.  I'll update the how to as we work through this.  I'd like it to work for everyone - these forums help with that.[/QUOTE]

Explicitly stating specific version of linux-source isn't very good, imho. :)  Plus, linux-source is not needed at all if you have linux-headers installed, is it? :)

Presuming that we're having High Definition Audio only on new Pentium motherboards, I guess the best solution would be to suggest installing linux-image-686 and linux-headers-686 packages (without diving into version numbers). They're there to take care that you always have latest kernel and headers available from ubuntu for your release version.

Also, i guess it's worth mentioning that after a kernel upgrade one will probably need to recompile and reinstall the ALSA modules.

---

### Post by crichell on 2005-12-10
[QUOTE=er-ku]Explicitly stating specific version of linux-source isn't very good, imho. :)  Plus, linux-source is not needed at all if you have linux-headers installed, is it? :)[/QUOTE]

we need linux-source and linux-headers to compile

> Presuming that we're having High Definition Audio only on new Pentium motherboards, I guess the best solution would be to suggest installing linux-image-686 and linux-headers-686 packages (without diving into version numbers). They're there to take care that you always have latest kernel and headers available from ubuntu for your release version.

Good point.  I think it's a good idea to split these task up - a how to for ALSA upgrade and a how to for Kernel upgrade to 686.

> Also, i guess it's worth mentioning that after a kernel upgrade one will probably need to recompile and reinstall the ALSA modules.

This is the problem with work arounds like this.  I like to stick with the base system as closely as possible.  I'll add this note.

BTW - Another way to get the sound working is to upgrade to the 2.6.14 kernel.  This, however, had a few undesirable effects including killing ipw2200 wireless.  Your mileage may very.

Here's the Vanilla 2.6.14 kernel how to [http://www.ubuntuforums.org/showthread.php?t=84174&highlight=kernel+2.6.14+upgrade](http://www.ubuntuforums.org/showthread.php?t=84174&highlight=kernel+2.6.14+upgrade)

---

### Post by iNerdSure on 2005-12-10
[QUOTE=Shinkan]I there !

I have and Acer Aspire 1641 WLMi, and I've had many problems :

- Battery charge detection doesn't work
> Solved by corecting myself my dumped DSDT. Can send it to somebody.

- Resolution is bad @ 1024x768, I need 1280x800 !!
> Solved by using 915resolution tool. Ask google, works fine.

- Leds-buttons (Wifi, Bluetooth) or special keys doesn't work.
> Solved by using acerhk module. Ask google, works fine but it's gadget.

One problem remains :

- Can't have any dB of sound with my Intel High Definition Audio (HDA) sound system. I have the Realtek ALC260 Codec.
What I've done ?
Downloading and installing alsa-driver, lib and utils 1.0.10.
Leveling sounds channel up, unmuting channels.
That doesn't work ...
I really don't know how to do.
The Realtek code ALC880 seems to work with many users (with or without efforts), but ALC260 doesn't, and I have no info on this chip ... google is quiet.

Any help would be greatly appreciated.
Sorry for my english, I'm french and it's 4 am here ... :confused:[/QUOTE]
Thanks for the input regarding the Realtek ALC880 and ALC260. My laptop comes with the ALC260. So, perhaps this is the root cause of our silent no sound problem. I hope some Ubuntu Breezy users out there in the community who have had success with this ALC260 can share their solution or workaround with us.

---

### Post by iNerdSure on 2005-12-10
[QUOTE=crichell]This was tested on a clean install - it's always easier when their clean although it is a luxury.  Did everything compile and install for you?  I've been looking for the alsaconf errors but the threads are sparse - If we can get that to run you should be in business.[/QUOTE]
Thanks, Crichell. My laptop was a "clean install" when I initially loaded Ubuntu Breezy and erasing previous data on the hard disk. I've repeated the steps and still get these errors:
[PHP]
:~/alsa$ sudo alsaconf
Unloading ALSA sound driver modules: snd-hda-intel snd-hda-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-seq-dummy snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device).
Building card database...


Running update-modules...
Loading driver...
FATAL: Error inserting snd_pcm (/lib/modules/2.6.12-10-686/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.12-10-686/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.12-10-686/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.12-10-686/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.12-10-686/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_hda_intel
Setting default volumes...
[/PHP]
The messages suggest checking dmesg. So I ran dmesg and got:
[PHP]
:~$ dmesg
t 2, code 0xaa on isa0060/serio0).
[4296171.362000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296171.462000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296171.462000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296171.552000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296171.552000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296171.658000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296171.658000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296171.742000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296171.742000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296171.848000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296171.848000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296327.941000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296327.941000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296328.041000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296328.041000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296328.126000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296328.126000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296328.242000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296328.242000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296328.286000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296328.286000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296328.402000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296328.402000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296328.416000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296328.416000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296329.383000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296329.383000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296329.517000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296329.517000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296329.617000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296329.617000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296329.687000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296329.687000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296329.793000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296329.793000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296329.864000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296329.864000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296329.954000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296329.954000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296330.025000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296330.025000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296330.119000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296330.119000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296330.189000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296330.189000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296330.284000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296330.284000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296330.359000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296330.359000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296330.465000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296330.465000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296330.535000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296330.535000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296330.655000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296330.655000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296357.184000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[4296384.016000] snd_pcm: disagrees about version of symbol snd_info_register
[4296384.016000] snd_pcm: Unknown symbol snd_info_register
[4296384.016000] snd_pcm: disagrees about version of symbol snd_info_create_module_entry
[4296384.016000] snd_pcm: Unknown symbol snd_info_create_module_entry
[4296384.016000] snd_pcm: disagrees about version of symbol snd_timer_notify
[4296384.016000] snd_pcm: Unknown symbol snd_timer_notify
[4296384.016000] snd_pcm: disagrees about version of symbol snd_timer_interrupt
[4296384.017000] snd_pcm: Unknown symbol snd_timer_interrupt
[4296384.017000] snd_pcm: disagrees about version of symbol snd_info_free_entry
[4296384.017000] snd_pcm: Unknown symbol snd_info_free_entry
[4296384.017000] snd_pcm: Unknown symbol snd_verbose_printk
[4296384.017000] snd_pcm: disagrees about version of symbol snd_ctl_register_ioctl
[4296384.017000] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[4296384.017000] snd_pcm: disagrees about version of symbol snd_card_file_add
[4296384.017000] snd_pcm: Unknown symbol snd_card_file_add
[4296384.017000] snd_pcm: Unknown symbol snd_compat_kzalloc
[4296384.017000] snd_pcm: disagrees about version of symbol snd_unregister_device
[4296384.017000] snd_pcm: Unknown symbol snd_unregister_device
[4296384.018000] snd_pcm: disagrees about version of symbol snd_timer_new
[4296384.018000] snd_pcm: Unknown symbol snd_timer_new
[4296384.018000] snd_pcm: disagrees about version of symbol snd_device_new
[4296384.018000] snd_pcm: Unknown symbol snd_device_new
[4296384.018000] snd_pcm: disagrees about version of symbol snd_ctl_unregister_ioctl
[4296384.018000] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[4296384.018000] snd_pcm: disagrees about version of symbol snd_info_create_card_entry
[4296384.018000] snd_pcm: Unknown symbol snd_info_create_card_entry
[4296384.018000] snd_pcm: disagrees about version of symbol snd_power_wait
[4296384.018000] snd_pcm: Unknown symbol snd_power_wait
[4296384.018000] snd_pcm: disagrees about version of symbol snd_device_free
[4296384.018000] snd_pcm: Unknown symbol snd_device_free
[4296384.018000] snd_pcm: disagrees about version of symbol snd_card_file_remove[4296384.018000] snd_pcm: Unknown symbol snd_card_file_remove
[4296384.018000] snd_pcm: disagrees about version of symbol snd_info_unregister
[4296384.018000] snd_pcm: Unknown symbol snd_info_unregister
[4296384.018000] snd_pcm: disagrees about version of symbol snd_device_register
[4296384.018000] snd_pcm: Unknown symbol snd_device_register
[4296384.018000] snd_pcm: disagrees about version of symbol snd_register_device
[4296384.018000] snd_pcm: Unknown symbol snd_register_device
[4296384.050000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[4296384.050000] snd_hda_codec: Unknown symbol snd_ctl_add
[4296384.050000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[4296384.050000] snd_hda_codec: Unknown symbol snd_card_proc_new
[4296384.050000] snd_hda_codec: Unknown symbol snd_compat_kstrdup
[4296384.050000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[4296384.050000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[4296384.050000] snd_hda_codec: Unknown symbol snd_verbose_printk
[4296384.050000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[4296384.051000] snd_hda_codec: Unknown symbol snd_ctl_new1
[4296384.051000] snd_hda_codec: disagrees about version of symbol snd_component_add
[4296384.051000] snd_hda_codec: Unknown symbol snd_component_add
[4296384.051000] snd_hda_codec: Unknown symbol snd_compat_kzalloc
[4296384.051000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_read
[4296384.051000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[4296384.051000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_write
[4296384.051000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[4296384.051000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[4296384.051000] snd_hda_codec: disagrees about version of symbol snd_device_new[4296384.051000] snd_hda_codec: Unknown symbol snd_device_new
[4296384.051000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[4296384.051000] snd_hda_codec: Unknown symbol snd_pcm_format_width
[4296384.109000] snd_pcm: disagrees about version of symbol snd_info_register
[4296384.109000] snd_pcm: Unknown symbol snd_info_register
[4296384.109000] snd_pcm: disagrees about version of symbol snd_info_create_module_entry
[4296384.110000] snd_pcm: Unknown symbol snd_info_create_module_entry
[4296384.110000] snd_pcm: disagrees about version of symbol snd_timer_notify
[4296384.110000] snd_pcm: Unknown symbol snd_timer_notify
[4296384.110000] snd_pcm: disagrees about version of symbol snd_timer_interrupt
[4296384.110000] snd_pcm: Unknown symbol snd_timer_interrupt
[4296384.110000] snd_pcm: disagrees about version of symbol snd_info_free_entry
[4296384.110000] snd_pcm: Unknown symbol snd_info_free_entry
[4296384.110000] snd_pcm: Unknown symbol snd_verbose_printk
[4296384.110000] snd_pcm: disagrees about version of symbol snd_ctl_register_ioctl
[4296384.110000] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[4296384.110000] snd_pcm: disagrees about version of symbol snd_card_file_add
[4296384.110000] snd_pcm: Unknown symbol snd_card_file_add
[4296384.110000] snd_pcm: Unknown symbol snd_compat_kzalloc
[4296384.111000] snd_pcm: disagrees about version of symbol snd_unregister_device
[4296384.111000] snd_pcm: Unknown symbol snd_unregister_device
[4296384.111000] snd_pcm: disagrees about version of symbol snd_timer_new
[4296384.111000] snd_pcm: Unknown symbol snd_timer_new
[4296384.111000] snd_pcm: disagrees about version of symbol snd_device_new
[4296384.111000] snd_pcm: Unknown symbol snd_device_new
[4296384.111000] snd_pcm: disagrees about version of symbol snd_ctl_unregister_ioctl
[4296384.111000] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[4296384.111000] snd_pcm: disagrees about version of symbol snd_info_create_card_entry
[4296384.111000] snd_pcm: Unknown symbol snd_info_create_card_entry
[4296384.111000] snd_pcm: disagrees about version of symbol snd_power_wait
[4296384.111000] snd_pcm: Unknown symbol snd_power_wait
[4296384.111000] snd_pcm: disagrees about version of symbol snd_device_free
[4296384.111000] snd_pcm: Unknown symbol snd_device_free
[4296384.111000] snd_pcm: disagrees about version of symbol snd_card_file_remove[4296384.111000] snd_pcm: Unknown symbol snd_card_file_remove
[4296384.111000] snd_pcm: disagrees about version of symbol snd_info_unregister
[4296384.111000] snd_pcm: Unknown symbol snd_info_unregister
[4296384.111000] snd_pcm: disagrees about version of symbol snd_device_register
[4296384.112000] snd_pcm: Unknown symbol snd_device_register
[4296384.112000] snd_pcm: disagrees about version of symbol snd_register_device
[4296384.112000] snd_pcm: Unknown symbol snd_register_device
[4296384.120000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[4296384.120000] snd_hda_codec: Unknown symbol snd_ctl_add
[4296384.120000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[4296384.120000] snd_hda_codec: Unknown symbol snd_card_proc_new
[4296384.120000] snd_hda_codec: Unknown symbol snd_compat_kstrdup
[4296384.120000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[4296384.120000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[4296384.120000] snd_hda_codec: Unknown symbol snd_verbose_printk
[4296384.120000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[4296384.121000] snd_hda_codec: Unknown symbol snd_ctl_new1
[4296384.121000] snd_hda_codec: disagrees about version of symbol snd_component_add
[4296384.121000] snd_hda_codec: Unknown symbol snd_component_add
[4296384.121000] snd_hda_codec: Unknown symbol snd_compat_kzalloc
[4296384.121000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_read
[4296384.121000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[4296384.121000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_write
[4296384.121000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[4296384.121000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[4296384.121000] snd_hda_codec: disagrees about version of symbol snd_device_new[4296384.121000] snd_hda_codec: Unknown symbol snd_device_new
[4296384.121000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[4296384.121000] snd_hda_codec: Unknown symbol snd_pcm_format_width
[4296384.150000] snd_hda_intel: Unknown symbol snd_pcm_new
[4296384.150000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[4296384.150000] snd_hda_intel: disagrees about version of symbol snd_card_register
[4296384.150000] snd_hda_intel: Unknown symbol snd_card_register
[4296384.150000] snd_hda_intel: disagrees about version of symbol snd_card_free
[4296384.151000] snd_hda_intel: Unknown symbol snd_card_free
[4296384.151000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[4296384.151000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[4296384.151000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[4296384.151000] snd_hda_intel: Unknown symbol snd_verbose_printk
[4296384.151000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[4296384.151000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[4296384.151000] snd_hda_intel: Unknown symbol snd_compat_kzalloc
[4296384.151000] snd_hda_intel: disagrees about version of symbol snd_card_new
[4296384.151000] snd_hda_intel: Unknown symbol snd_card_new
[4296384.151000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[4296384.152000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[4296384.152000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[4296384.152000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[4296384.152000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[4296384.152000] snd_hda_intel: disagrees about version of symbol snd_card_set_pm_callback
[4296384.152000] snd_hda_intel: Unknown symbol snd_card_set_pm_callback
[4296384.152000] snd_hda_intel: Unknown symbol snd_hda_suspend
[4296384.152000] snd_hda_intel: disagrees about version of symbol snd_device_new[4296384.152000] snd_hda_intel: Unknown symbol snd_device_new
[4296384.152000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[4296384.152000] snd_hda_intel: Unknown symbol snd_hda_resume
[4296384.152000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[4296384.152000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[4296384.153000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[4296679.011000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296679.011000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296679.141000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296679.141000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[/PHP]
I'm not sure how serious the error messages imply. Being a Linux newbie, I have no clue what I should do to get out of this mess. :confused: 

Anyway, I suppose it is the "no pain, no gain" Linux learning experience! :(

---

### Post by iNerdSure on 2005-12-14
Anyone discovered a solution or workaround? Or, experience with the 2.6.14 kernel to share? The continued SILENCE on my laptop and on this forum is becoming rather disconcerting.

---

### Post by LiquidIQ on 2005-12-14
[QUOTE=iNerdSure]Anyone discovered a solution or workaround? Or, experience with the 2.6.14 kernel to share? The continued SILENCE on my laptop and on this forum is becoming rather disconcerting.[/QUOTE]

So you're still getting no sound with 1.0.10? From the look of the changelog, there seems to be a lot of changes for Realtek codecs...

---

### Post by crichell on 2005-12-14
[QUOTE=iNerdSure]Anyone discovered a solution or workaround? Or, experience with the 2.6.14 kernel to share? The continued SILENCE on my laptop and on this forum is becoming rather disconcerting.[/QUOTE]

I've also used the 2.6.14 kernel which did work with the Intel HDA and the Realtek ALC880.  The only issue I encountered was that the wireless card was no longer recognized by the kernel.  Ultimately I upgraded to ALSA 1.0.10 instead.

When you open volume control and click File > Change Device do you have Intel HDA and Realtek ALC260 in there?  It seems as though ALSA doesn't see your sound card.

As you probably know Realtek doesn't have Linux drivers fo the Realtek260 (as far as I can find.)

---

### Post by iNerdSure on 2005-12-14
[QUOTE=LiquidIQ]So you're still getting no sound with 1.0.10? From the look of the changelog, there seems to be a lot of changes for Realtek codecs...[/QUOTE]
Yes. Still no sound. I'm not aware of changes for Realtek codecs. Any suggestions on what I can try? (Being a Linux convert newbie, I'm still trying to learn as much and as quickly as I can. But so far, this NO SOUND - SILENCE is really bugging me :mad: )

---

### Post by iNerdSure on 2005-12-14
[QUOTE=crichell]I've also used the 2.6.14 kernel which did work with the Intel HDA and the Realtek ALC880.  The only issue I encountered was that the wireless card was no longer recognized by the kernel.  Ultimately I upgraded to ALSA 1.0.10 instead.

When you open volume control and click File > Change Device do you have Intel HDA and Realtek ALC260 in there?  It seems as though ALSA doesn't see your sound card.

As you probably know Realtek doesn't have Linux drivers fo the Realtek260 (as far as I can find.)[/QUOTE]
I'm contemplating upgrading to the 2.6.14 kernel. How did you restore the working of your wireless card? 

When I open volume control, I have both HDA Intel (Alsa Mixer) and Realtek ALC260 (OSS Mixer). I am not aware that Realtek260 has no Linux drivers. So, is this a hopeless situation, or there are other alternatives for me to try? Thanks for your help.

---

### Post by crichell on 2005-12-14
[QUOTE=iNerdSure]I'm contemplating upgrading to the 2.6.14 kernel. How did you restore the working of your wireless card?[/QUOTE]

I didn't - rather than mess with it I thought the ALSA upgrade was a better solution

> When I open volume control, I have both HDA Intel (Alsa Mixer) and Realtek ALC260 (OSS Mixer). I am not aware that Realtek260 has no Linux drivers. So, is this a hopeless situation, or there are other alternatives for me to try? Thanks for your help.

Realtek not posting a Linux driver isn't a show stopper at all.  Try to recompile alsa 1.0.10 with the following options
[LIST]
[*]./configure --with-oss=yes --with-kernel=/usr/src/linux-headers-2.6.12-10-386/
[*]make
[*]sudo make install
[*]sudo alsaconf
[/LIST]

Let me know what happens.  ALSA isn't upgraded until we get alsaconf to run.

---

### Post by iNerdSure on 2005-12-14
[QUOTE=crichell]I didn't - rather than mess with it I thought the ALSA upgrade was a better solution



Realtek not posting a Linux driver isn't a show stopper at all.  Try to recompile alsa 1.0.10 with the following options
[LIST]
[*]./configure --with-oss=yes --with-kernel=/usr/src/linux-headers-2.6.12-10-386/
[*]make
[*]sudo make install
[*]sudo alsaconf
[/LIST]

Let me know what happens.  ALSA isn't upgraded until we get alsaconf to run.[/QUOTE]
Ok. I recompiled with the above steps. No error messages showed up. Great. But still no sound from laptop. Checked all controls with Alsamixer to ensure all unmuted as well. Still silence. Am I missing some steps? Or, what else should I try?  :confused:   Thanks.

---

### Post by crichell on 2005-12-14
[QUOTE=iNerdSure]Ok. I recompiled with the above steps. No error messages showed up. Great. But still no sound from laptop. Checked all controls with Alsamixer to ensure all unmuted as well. Still silence. Am I missing some steps? Or, what else should I try?  :confused:   Thanks.[/QUOTE]

Were you able to use alsaconf to setup the Intel HDA card?  You should have gotten a blue screen in the terminal and four or five questions from the configurator.

Give this a swing - Go to Applications > Sound and Video > Volume Control then click Edit > Preferences and tick the checkbox next to front. Increase the volume to 100%.  Make sure Master and PCM (If you have it) are all the way up.  Make sure Front, Master, and PCM are not muted.

Alsamixer essentially does the same thing but I haven't used it.

---

### Post by iNerdSure on 2005-12-15
[QUOTE=crichell]Were you able to use alsaconf to setup the Intel HDA card?  You should have gotten a blue screen in the terminal and four or five questions from the configurator.

Give this a swing - Go to Applications > Sound and Video > Volume Control then click Edit > Preferences and tick the checkbox next to front. Increase the volume to 100%.  Make sure Master and PCM (If you have it) are all the way up.  Make sure Front, Master, and PCM are not muted.

Alsamixer essentially does the same thing but I haven't used it.[/QUOTE]
Ok. Tried Volume Control. PCM-2 is available, not PCM. "Master" is missing. My laptop has: for Playback: Volume, Speaker, PCM-2 and In-gain; and Capture: Line-in, Microphone, CD. Anyway, the are all set to "un-muted" and Max Volume.

But no success. Still no sound. Silence. :(   :confused: 

Any other setting or drivers I could experiement with?  Thanks.

---

### Post by er-ku on 2005-12-15
[QUOTE=iNerdSure]Ok. Tried Volume Control. PCM-2 is available, not PCM. "Master" is missing. My laptop has: for Playback: Volume, Speaker, PCM-2 and In-gain; and Capture: Line-in, Microphone, CD. Anyway, the are all set to "un-muted" and Max Volume.

But no success. Still no sound. Silence. :(   :confused: 

Any other setting or drivers I could experiement with?  Thanks.[/QUOTE]

Visit Edit > Preferences (or whatever the name), and check all the ticks there. :)

---

### Post by iNerdSure on 2005-12-15
[QUOTE=er-ku]Visit Edit > Preferences (or whatever the name), and check all the ticks there. :)[/QUOTE]
Yep, tried that as well. Selected ALL items. No success. What about your side? Any success with your laptop?

---

### Post by er-ku on 2005-12-15
[QUOTE=iNerdSure]Yep, tried that as well. Selected ALL items. No success. What about your side? Any success with your laptop?[/QUOTE]
Nothing, yet.

I'm thinking about trying a Dapper LiveCD. If sound works there, it's OK with me.
Also, it's a pity that **mohitcool_buddy** is a too-nontechnical person, so he cannot even understand what I've been wanting from him... :( On the other hand, the fact, that the sound DOES work for him, inspires a little. ;)

---

### Post by iNerdSure on 2005-12-15
[QUOTE=er-ku]Nothing, yet.

I'm thinking about trying a Dapper LiveCD. If sound works there, it's OK with me.
Also, it's a pity that **mohitcool_buddy** is a too-nontechnical person, so he cannot even understand what I've been wanting from him... :( On the other hand, the fact, that the sound DOES work for him, inspires a little. ;)[/QUOTE]
Yes, I am also optimistic that if another Acer 4061 has sound running Breezy, then we should be able to replicate similar sound drivers, settings, patches etc. Maybe we can post a list of commands for Mohitcool to run, and copy and paste the results to share with everyone.

I am not sure what are the useful "diagnostic" commands similar to "Device Manager" in WinXp, but I suppose you are much more experience in Linux. 

Anyway, if you try Dapper LiveCD, let me know how well it runs on your Acer4061. Thanks.

---

### Post by LiquidIQ on 2005-12-15
Not sure how the Realtek driver works, but manufacturers are supposed to put "verb tables" in their BIOS for the HDA audio so that a driver (like the Linux driver) can read the verb table to setup the codec correctly (ports, etc). It's kinda like an "INF" file in Windows, but in the BIOS. I'm outta ideas, unless you can email Acer, but I doubt that will do much good unfortunately.

---

### Post by iNerdSure on 2005-12-15
[QUOTE=LiquidIQ]Not sure how the Realtek driver works, but manufacturers are supposed to put "verb tables" in their BIOS for the HDA audio so that a driver (like the Linux driver) can read the verb table to setup the codec correctly (ports, etc). It's kinda like an "INF" file in Windows, but in the BIOS. I'm outta ideas, unless you can email Acer, but I doubt that will do much good unfortunately.[/QUOTE]
I suppose the alternatives are to try other distros, or M$WinXp. I doubt Acer's commitment extends to ensuring the laptop runs on Breezy or other distros. The retail off-the-shelf options available for this model was WinXP Home Edition, or XP Pro, or Linpus Linux Basic Edition.

Anyway, I'm optimistic that some Linux users or experts out in the community will respond with a solution or workaround. :D

---

### Post by er-ku on 2005-12-17
[QUOTE=iNerdSure]Yes, I am also optimistic that if another Acer 4061 has sound running Breezy, then we should be able to replicate similar sound drivers, settings, patches etc. Maybe we can post a list of commands for Mohitcool to run, and copy and paste the results to share with everyone.

I am not sure what are the useful "diagnostic" commands similar to "Device Manager" in WinXp, but I suppose you are much more experience in Linux. 
[/QUOTE]
I've already mentioned those commands before, but he didn't realize that their output is what I wanted, not just a confirmation of "successful execution". Maybe we should ask once again?..

> 
Anyway, if you try Dapper LiveCD, let me know how well it runs on your Acer4061. Thanks.

Yeah, sure. I'll try it when I have an opportunity..

Have you fixed the battery meter issues? Probably, that would solve the sound problems too, or sth... I'm gonna try it too, when I can..

---

### Post by er-ku on 2005-12-19
I got an email from alsa bugtrack today. Someone replied to my bugreport with this:
>  Please test the latest ALSA release (1.0.11-rc1), this should be fixed.

**iNerdSure**, wanna test some fresh alsa modules? If you're willing to, just compile and install them as you did before. I'll try my Ubuntu way too, when I get my hands to the Acer.

---

### Post by jezjones on 2005-12-20
I have been having problems with the intel sound chip with Hoary and then with Breezy.

I can only confirm that everyone on here is right, and the sound does not seem to work in a standard way... e.g. what fixes it for one cannot fix it for the other.

I was very impressed with Breezy's hardware detection, but i am not happy about the lack of sound.
Even getting the latest alsa, 1.0.10 did not fix my problem nor did a recompile of the kernel.

I am willing to keep looking into it, but having spent 3 solid weekends searching the internet etc, I had to revert windoze. If i had been charging for my time it would have cost me the same as the laptop!

I have been using linux for about 3 years now, and on the whole it has improved. But there is a really big problem with linux that does not seem to go away..... new hardware!

If you can find a list of supported hardware, then that stuff is probably not in the shops anymore... rule of thumb.. if it is well known for being supported, it is old.

The other main issue is that if your base install does not detect it, then you are suddenly in a world of pain.... especially as a newbie.
I have been compiling modules and editing config files for some time, so i dont mind... but adding new hardware or installing hardware that is not detected is a very little documented and very fragile process.
I know that hardware support is down to manufacturers being more open, which may or may not come in time... but the process of installing that hardware is troublesome and messy business which in itself drives many people away from linux.

As for me, i am waiting for the next version of distro's which come with a later alsa driver. 
I cannot afford not to be working on paid work while i go through a process of trial and error for several months!!
I would even go as far as to say that installing new hardware is harder than recompiling the kernel!!!! 

More people using linux on the desktop? Make it easier to install and manage hardware. We all hate windoze but at least you have a device manager from where you can manage all aspects of your devices!!!

---

### Post by Alessio on 2005-12-21
[QUOTE=jezjones]I have been having problems with the intel sound chip with Hoary and then with Breezy.

I can only confirm that everyone on here is right, and the sound does not seem to work in a standard way... e.g. what fixes it for one cannot fix it for the other.

I was very impressed with Breezy's hardware detection, but i am not happy about the lack of sound.
Even getting the latest alsa, 1.0.10 did not fix my problem nor did a recompile of the kernel.

I am willing to keep looking into it, but having spent 3 solid weekends searching the internet etc, I had to revert windoze. If i had been charging for my time it would have cost me the same as the laptop!

I have been using linux for about 3 years now, and on the whole it has improved. But there is a really big problem with linux that does not seem to go away..... new hardware!

If you can find a list of supported hardware, then that stuff is probably not in the shops anymore... rule of thumb.. if it is well known for being supported, it is old.

The other main issue is that if your base install does not detect it, then you are suddenly in a world of pain.... especially as a newbie.
I have been compiling modules and editing config files for some time, so i dont mind... but adding new hardware or installing hardware that is not detected is a very little documented and very fragile process.
I know that hardware support is down to manufacturers being more open, which may or may not come in time... but the process of installing that hardware is troublesome and messy business which in itself drives many people away from linux.

As for me, i am waiting for the next version of distro's which come with a later alsa driver. 
I cannot afford not to be working on paid work while i go through a process of trial and error for several months!!
I would even go as far as to say that installing new hardware is harder than recompiling the kernel!!!! 

More people using linux on the desktop? Make it easier to install and manage hardware. We all hate windoze but at least you have a device manager from where you can manage all aspects of your devices!!![/QUOTE]
Same situation..
I'm on Ubuntu from one year, but ubuntu hate my laptop Asus a6va
my sound intel isn't recognize!! I spend 1 week for this problem! A lot of howto, package, ecc..
What can i do????????
Who can contact for this??

---

### Post by pgf on 2005-12-23
[QUOTE=er-ku]I got an email from alsa bugtrack today. Someone replied to my bugreport with this:


**iNerdSure**, wanna test some fresh alsa modules? If you're willing to, just compile and install them as you did before. I'll try my Ubuntu way too, when I get my hands to the Acer.[/QUOTE]

i had no sound on our asus z33a with breezy, and alsa 1.0.9.

i built the 1.0.11rc1 and installed it, and now sound works fine.

just one data point...

---

### Post by viridis on 2005-12-23
[QUOTE=pgf]i had no sound on our asus z33a with breezy, and alsa 1.0.9.

i built the 1.0.11rc1 and installed it, and now sound works fine.

just one data point...[/QUOTE]

Hi,

Is it alc880 or alc260? I tried alsa-driver-1.0.011rc1 with no success yesterday. Maybe i did something wrong, but it didn't work...

Giedrius

---

### Post by pgf on 2005-12-23
it's an ALC880.

i noticed that playing a CD doesn't seem to work.  but playing mp3
files, and desktop sounds, and movies (via ogle) all seem to work.

paul
p.s. good luck!!

---

### Post by iNerdSure on 2005-12-26
[QUOTE=er-ku]I got an email from alsa bugtrack today. Someone replied to my bugreport with this:


**iNerdSure**, wanna test some fresh alsa modules? If you're willing to, just compile and install them as you did before. I'll try my Ubuntu way too, when I get my hands to the Acer.[/QUOTE]
Sorry for the late reply. I've been travelling without my laptop. I would certainly like to try the new Alsa modules over the next few days. (Need to clear up some work backlog first). And also the battery meter.

---

### Post by er-ku on 2005-12-26
**Fixing Battery State Indicator**

I've attached an archive with the following files in it:
[LIST]
[*]dsdt.dsl - fixed dsdt source file, it's only provided for a case you want to see what's inside.
[*]DSDT.aml - the DSDT compiled into AML - this is the file you'll need. :)
[/LIST]

Now to use it, you do the following:
```
$ tar -jxvf DSDT.tar.bz2
$ sudo cp DSDT.aml /etc/mkinitramfs/
$ sudo dpkg-reconfigure linux-image-$(uname -r)
```

Reboot your computer at this point. I think the battery indicator should work now. It's a little weird though, that even a fully charged battery only claims to be suitable for two hours... Also, the indicator is a little slow, i.e., it doesn't immediately reflect the power state changes...

If something goes wrong (i.e., the situation hasn't changed or is worse), consider the following commands:
```
$ sudo rm /etc/mkinitramfs/DSDT.aml
$ sudo dpkg-reconfigure linux-image-$(uname -r)
```
and then rebooting.

If you customize your DSDT this way, the battery meter should also work after your next kernel upgrade too.

*This mini fix tutorial is written thanks to numerous resources on the internet, and the mkinitramfs part of it is written after [this](http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html#acpi) tutorial.*

---

### Post by flujan on 2005-12-28
Any news about this issue? I look in the alsa changelog, but with the 1.0.11rc1 the problem remains. My card is detected but continues muted. 

Thanks in advance.

---

### Post by er-ku on 2005-12-29
[QUOTE=flujan]Any news about this issue? I look in the alsa changelog, but with the 1.0.11rc1 the problem remains. My card is detected but continues muted. 

Thanks in advance.[/QUOTE]

I'm afraid this isn't really an ALSA issue, but maybe something buggy with the BIOS of our Acers.
I have an idea i'll probably try out. I'm thinking of installing Windows XP to the Swap partition of Linux, just to look at what Acers CD offers. I'd like to check the eSettings tool, to be exact (what a pity Windows doesn't have a LiveCD :rolleyes:). Or, probably, the windows drivers provided with the laptop would simply "enable" the sound device in BIOS...
That's just a theory, however...

---

### Post by flujan on 2005-12-29
I don't think so. I tried Slackware-current and compile and install the new alsa drivers, libs and utils.

I got a error message when I try to load the snd-hda-intel module. 

Something about incorrect parameters or IRQ. I will post it here tonight.

And the bug was assigned:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1517](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1517)

---

### Post by iNerdSure on 2005-12-30
[QUOTE=er-ku]**Fixing Battery State Indicator**

I've attached an archive with the following files in it:
[LIST]
[*]dsdt.dsl - fixed dsdt source file, it's only provided for a case you want to see what's inside.
[*]DSDT.aml - the DSDT compiled into AML - this is the file you'll need. :)
[/LIST]

Now to use it, you do the following:
```
$ tar -jxvf DSDT.tar.bz2
$ sudo cp DSDT.aml /etc/mkinitramfs/
$ sudo dpkg-reconfigure linux-image-`uname -r`
```

Reboot your computer at this point. I think the battery indicator should work now. It's a little weird though, that even a fully charged battery only claims to be suitable for two hours... Also, the indicator is a little slow, i.e., it doesn't immediately reflects the power state changes...

If something goes wrong (i.e., the situation hasn't changed or is worse), consider the following commands:
```
$ sudo rm /etc/mkinitramfs/DSDT.aml
$ sudo dpkg-reconfigure linux-image-`uname -r`
```
and then rebooting.

If you customize your DSDT this way, the battery meter should also work after your next kernel upgrade too.

*This mini fix tutorial is written thanks to numerous resources on the internet, and the mkinitramfs part of it is written after [this](http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html#acpi) tutorial.*[/QUOTE]
Many thanks, Er-ku. Tried the first part of your solution, rebooted, and IT WORKS :smile: Simply GREAT. Now, I don't have to worry when working without AC power, that the laptop will "drop-dead" and shutdown on me.

Btw, I have not tried the modem before, but recently when I had problems with my router at home, I tried dialing up, and I get error message that modem not detected. Strange, I wonder what's the cause of this problem.

Of course, the main irritation has been unable to get any SOUND from this Acer 4060 running on Breezy.

Best wishes for 2006.

---

### Post by lobstaj on 2005-12-31
Hi everybody,

I have got an Acer Extensa 6700 and have the same sound problem with Breezy... The driver (hda-intel) loads perfectly, mixer controls as well, but no sound. If I believe the GNOME mixer applet, then I have an ALC260. Like others, I've also tried to get alsa-lib 1.0.10 and 1.0.11rc1 without success.

[QUOTE=iNerdSure]Btw, I have not tried the modem before, but recently when I had problems with my router at home, I tried dialing up, and I get error message that modem not detected. Strange, I wonder what's the cause of this problem.[/QUOTE]

I think that these days, modems are not much more than sound devices which can output sounds onto a phone line. So if the sound doesn't work, it is not so unlikely that the modem doesn't work neither. I'm not totally sure, but I couldn't get my modem to work neither...

I hope something will happen soon. It would be nice to get rid of XP finally... :)

Happy new year!

---

### Post by iNerdSure on 2006-01-01
[QUOTE=lobstaj]Hi everybody,

I have got an Acer Extensa 6700 and have the same sound problem with Breezy... The driver (hda-intel) loads perfectly, mixer controls as well, but no sound. If I believe the GNOME mixer applet, then I have an ALC260. Like others, I've also tried to get alsa-lib 1.0.10 and 1.0.11rc1 without success.



I think that these days, modems are not much more than sound devices which can output sounds onto a phone line. So if the sound doesn't work, it is not so unlikely that the modem doesn't work neither. I'm not totally sure, but I couldn't get my modem to work neither...

I hope something will happen soon. It would be nice to get rid of XP finally... :)

Happy new year![/QUOTE]
Thanks for the input. I hardly use a dialup modem these days, hence the late discovery, after 2 months! Given my intermittent router problem, I should fix the modem problem. Otherwise, I have to hunt around for wireless hotspots for internet access.

Anyway, like you, I'd like to solve the NO SOUND problem, so that I need not fall back on my other XP laptop. The Breezy laptop (Acer 4060) that I'm using is a clean install (not dual boot).

Hopefully, we could fix this NO SOUND problem before the next Ubuntu version release! Otherwise, we would have lived through 6 months of SILENCE, and many hours of googling and yahooing.

---

### Post by er-ku on 2006-01-01
> **lobstaj]Hi everybody,

I have got an Acer Extensa 6700 and have the same sound problem with Breezy... The driver (hda-intel) loads perfectly, mixer controls as well, but no sound. If I believe the GNOME mixer applet, then I have an ALC260. Like others, I've also tried to get alsa-lib 1.0.10 and 1.0.11rc1 without success.[/QUOTE]

Same here. Do you **have** Windows XP on that computer? Does sound work there? (Rhetoric question, i guess...)

Also, do you have the "Status: Disabled" line for the sound device in dmidecode output?

> 
I think that these days, modems are not much more than sound devices which can output sounds onto a phone line.

Nah, i don't think so.

> So if the sound doesn't work, it is not so unlikely that the modem doesn't work neither. I'm not totally sure, but I couldn't get my modem to work neither...

I never tried to awaken that modem, actually. If it's a software modem (a.k.a. winmodem said:**
> 
I hope something will happen soon. It would be nice to get rid of XP finally... :)

Aha, so you **do** have XP, right?

Happy new year everyone! I wish we all get sound working this year! :D

---

### Post by Franckito on 2006-01-01
Hi everybody.
First and foremost, I wish you a very happy new year. Hope that bloody sound problem will be fixed before 2007 ;) 
I have the same problem on a 1641WLMI with a ALC260 sound chip. The dmidecode gives me the same result : disabled.
Just like Er-ku, I think it's an Acer problem because my sister-in-law installed Ubuntu Breezy on a Sony Laptop and got the sound after havind demuted the lines-out in alsamixer. She has a ALC260 chip as well and it works ! I could hear sounds with her laptop but on my girlfriend's, nothing. She had a look at it but didn't manage to make it work. If you want, I can ask her to give us the output of some commands. She completely erased Windows, because everything works on hers with linux.
It can't be a trick to prevent people from using linux, can it ?

Best wishes !

Frankito

---

### Post by lobstaj on 2006-01-02
Hi again,

[QUOTE=er-ku]Same here. Do you **have** Windows XP on that computer? Does sound work there? (Rhetoric question, i guess...)[/QUOTE]
Yes, I got XP home and sound works just fine...

[QUOTE=er-ku]Also, do you have the "Status: Disabled" line for the sound device in dmidecode output?[/QUOTE]
It's the same output as was shown before:

Handle 0x000D
        DMI type 10, 6 bytes.
        On Board Device Information
                Type: Sound
                Status: Disabled
                Description: ADI

[QUOTE=er-ku]Aha, so you **do** have XP, right?[/QUOTE]
Is there a way to buy a laptop without paying the windows tax..? ;-)

How could that "Status: Disabled" be changed... It cannot be so difficult to change some flag somewhere... Hopefully. :-)

Until later!

---

### Post by jakub on 2006-01-02
I had the same problem on Fujitsu-Simens AmiloPro v2040.
I did everething from Alsa Setup  HOWTO, but it didn't work. Then I realized that I have Centrino so I can use 686 kernel. I upgraded the kernel, and did the Alsa setup process once again but with alsa 1.0.11rc1. Now after doing alsaconf I have sound, but if I only touch the volume it disappears (sound that is:) ).
Also there is sound when Breezy is starting, but after I log in it disappears in the middle of the theme.

Maybe someone knows what is going on?

---

### Post by whiterussian on 2006-01-02
Hello world, 

Got the same issue, ive tried various fixes, to no avail.

Ive got the intel 'ICH6 family' card in an acer 4101WLMI, Ive had suse10 installed, however the internal wireless card isnt 'supported' by novell, so it gets marked as tained and i cant use it... so i went back to ubuntu.

Did everything perfectly, practically out of the box, and sound works when the login screen comes up... except it plays the drums 4 times, then nothing else works.

Anyways, if anyones come up with a fix other than installing the new alsa, because id rather stick with whats nicely supported, let me know!

---

### Post by iNerdSure on 2006-01-03
Tried the latest version of ALSA 1.0.11rc1 driver. Still NO SOUND. Rather disappointing and frustrating. :mad: 

Checked dmidecode and found:
[PHP]
Handle 0x000D
        DMI type 10, 6 bytes.
        On Board Device Information
                Type: Sound
                Status: Disabled
                Description: ADI
[/PHP]
On Board Device still "Disabled". I tend to agree with Er-Ku's earlier posting, that there should be some simple way or switch to "Enable" the On Board sound device.

(This Acer 4060 laptop has a simple LED/switch to turn on/off the wireless ethernet device. Perhaps, there's something similar that can turn on the sound device? that we are yet to discover)

Tried calling Acer service centre. Was told "Sorry, we are not able to support notebook PCs running on Linux! Well, I suppose M$ commands better customer service than Linu$. 

I hope some expert in the Ubuntu community can help us out here.

---

### Post by whiterussian on 2006-01-03
Ive got some c compiler porblem... the configure file for the new alsa... and i think everything else now... tells me gcc cannot create executables... help!

./configure --with-oss=yes --with-kernel=/usr/src/linux-headers-2.6.12-10-386/

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Config.log hasnt got any more information then that...

SOS!:confused:

EDIT: Ive got the newest gcc synaptic is offering me...

gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

---

### Post by whiterussian on 2006-01-03
Ok, fixed that...

New problem... i cant find alsaconf... no errors occured during installation, at least none that i saw...

i have alsactl, which i thought may be similar, but doesnt sound like it.

Alsa-utils seems installed...

Help!

---

### Post by jakub on 2006-01-03
Hi!

> On Board Device still "Disabled". I tend to agree with Er-Ku's earlier posting, that there should be some simple way or switch to "Enable" the On Board sound device.

As I wrote before, after running alsaconf I can hear music but still dmidecode gives:

> 
Handle 0x0011
        DMI type 10, 8 bytes.
        On Board Device 1 Information
                Type: Video
                Status: Disabled
                Description: NV43M
        On Board Device 2 Information
                Type: Sound
                Status: Disabled
                Description: ADI


My card is also HDA Intel ICH6 Family, so I guess this is not the case.

---

### Post by iNerdSure on 2006-01-03
[QUOTE=jakub]Hi!



As I wrote before, after running alsaconf I can hear music but still dmidecode gives:



My card is also HDA Intel ICH6 Family, so I guess this is not the case.[/QUOTE]
Interesting. Are you also having the same sound card Realtek ALC260 as well? If it works on your PC, then perhaps, the rest of us can remain optimistic that we will have light (or sound in this case :) ) at the end of the tunnel.

---

### Post by whiterussian on 2006-01-04
After running alsaconf, sound is still ALMOST working, i hear the drums... except 4 times, and thats it.

a killall aplay will fix it, until a sound tries to play anywhere, then it plays 4 times and stops. 

I may have a completely different error.:confused: 

Ive got the intel ICH6 family card too...

---

### Post by er-ku on 2006-01-04
[QUOTE=whiterussian]After running alsaconf, sound is still ALMOST working, i hear the drums... except 4 times, and thats it.

a killall aplay will fix it, until a sound tries to play anywhere, then it plays 4 times and stops. 

I may have a completely different error.:confused: 

Ive got the intel ICH6 family card too...[/QUOTE]

ICH6 isn't a very distinct description. It can still be AC97 or HDA or something else. What does lspci say about your sound card, and how does gnome mixer call both of the available mixer devices?

And your sound issue may very well be related to some bug in aplay. Try killing aplay, and playing some audio file with a different player. Rhythmbox, for example.

And if you run it from terminal, it may output some interesting info if it just dies like aplay.

---

### Post by jakub on 2006-01-04
Hi!

> Are you also having the same sound card Realtek ALC260 as well?

I don't know if I have the same. I don't know where to find that information.
All I can tell you that Volume Control has in File/Change Device:
0: HDA Intel (Alsa Mixer)
1: Analog Devices AD1986A (OSS Mixer)
Is that it ?

And back to my original question:
does someone know what is the reason for sound turning off just after login?

---

### Post by er-ku on 2006-01-05
[QUOTE=jakub]Hi!

> Are you also having the same sound card Realtek ALC260 as well?

I don't know if I have the same. I don't know where to find that information.
All I can tell you that Volume Control has in File/Change Device:
0: HDA Intel (Alsa Mixer)
1: Analog Devices AD1986A (OSS Mixer)
Is that it ?
[/QUOTE]

Yup. So it's "Analog Devices AD1986A" , not "Realtek ALC260" in your case.

> 
And back to my original question:
does someone know what is the reason for sound turning off just after login?

As I said, there might be issues with some particular binary/library. Maybe not. I don't know...

---

### Post by iNerdSure on 2006-01-11
Rather SILENT on this NO SOUND topic ;)  Anyone tried anything new? I've tried the ALSA 1.0.11rc driver and utils, but still SILENT, NO SOUND.

I've also come across in a separate forum that the new Kernel 2.6.14 would include fixes for the ALC260. Hopefully, that is indeed the case.

---

### Post by lobstaj on 2006-01-11
There is SOUND! Take a look at this entry of another forum: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1618%3E#7453]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1618%3E#7453")

At least now there is sound on line-out... Neither the internal speakers nor the headphone out work, but there is SOUND! :D 

Hopefully this means that the rest'll work soon as well!

---

### Post by ys4_sinau on 2006-01-11
hello all,

i use acer 2350 nlci.
there is no problem with my sound. sound going properly and i didn't set up anything.

---

### Post by er-ku on 2006-01-12
[QUOTE=lobstaj]There is SOUND! Take a look at this entry of another forum: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1618%3E#7453]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1618%3E#7453")

At least now there is sound on line-out... Neither the internal speakers nor the headphone out work, but there is SOUND! :D 

Hopefully this means that the rest'll work soon as well![/QUOTE]
Woohoo! Good news. :) I guess i should dupe my bugreport against #1618. 
I hope the internal speakers will also work in the next release version of ALSA... :)

---

### Post by lobstaj on 2006-01-12
[QUOTE=ys4_sinau]i use acer 2350 nlci.
there is no problem with my sound. sound going properly and i didn't set up anything.[/QUOTE]
Do you have a Realtek ALC260 chipset? Find out by opening the GNOME mixer, then select File->Change Device from the menu. There you should find "Intel HDA" and something else. That something else should be your chipset.

Actually the name of this thread is maybe misleading. It should rather be called "Intel HDA and Realtek ALC260 - no sound"...

---

### Post by er-ku on 2006-01-12
[QUOTE=lobstaj]Actually the name of this thread is maybe misleading. It should rather be called "Intel HDA and Realtek ALC260 - no sound"...[/QUOTE]

I'm afraid this is Acer- (and probably Fujitsu-) specific...

---

### Post by Chris Tucker on 2006-01-12
hm, i have the acer aspire 3000 (cant remember the order of the letters after it off hand) and my sound worked out of the box.. i cant see why manufacturers cant stick with using the same chip for something in all models of a specific timeperiod of maufacture.
allthough i do have some gripes with my aspire's sound, in windows anyway, recording with audacity makes *clicks* , and the chip, or its pathways, travel too close to the HD . i get very faint chirps on the output jack from the hd head.

---

### Post by iNerdSure on 2006-01-12
I'm the person who initiated this thread. As a non-technical person, and a Linux newbie trying to convert from WinXP, I had no clue as to the cause of a brand new laptop, with a new installation of Ubuntu Breezy, remain mutedly silent inspite of various attempts at fixing. Hence the choice of words for the title.

From the gist of the ALSA bugtracking discussion, I infer that there is indeed light at the end of the tunnel, or, in this silent case, sound at the end of the tunnel. Franky, I don't quite understand less than half the technical jargon. My main interest is to break the sound barrier, or rather to break the silent barrier that has deafened me since the release of Breezy in October.

I hope an expert, or experts, can help put the fixes in "newbie" step-by-step language, so that we (I believe we are more than a silent minority) can attempt to put some sound and music into our work and leisure. Many thanks to everyone who has been trying to help. :)

---

### Post by iNerdSure on 2006-01-12
I'm the person who initiated this thread. As a non-technical person, and a Linux newbie trying to convert from WinXP, I had no clue as to the cause of a brand new laptop, with a new installation of Ubuntu Breezy, remain mutedly silent inspite of various attempts at fixing. Hence the choice of words for the title: Breezy on Acer Laptop NO SOUND.

From the gist of the ALSA bugtracking discussion, I infer that there is indeed light at the end of the tunnel, or, in this silent case, sound at the end of the tunnel. Franky, I don't quite understand less than half the technical jargon. My main interest is to break the sound barrier, or rather to break the silent barrier that has deafened me since the release of Breezy in October.

I hope an expert, or experts, can help put the fixes in "newbie" step-by-step language, so that we (I believe we are more than a silent minority) can attempt to put some sound and music into our work and leisure. Many thanks to everyone who has been trying to help. :)

---

### Post by eudoxos on 2006-01-13
I filed this bug as [http://bugzilla.ubuntu.com/show_bug.cgi?id=22358](http://bugzilla.ubuntu.com/show_bug.cgi?id=22358) to track upstream.

---

### Post by iNerdSure on 2006-01-13
[QUOTE=eudoxos]I filed this bug as [http://bugzilla.ubuntu.com/show_bug.cgi?id=22358](http://bugzilla.ubuntu.com/show_bug.cgi?id=22358) to track upstream.[/QUOTE]
Many thanks, Eudoxos, for your help. I wouldn't have been able to define the problem nor identify the possible causes with such a precision and the right language.

I do hope someone could come to our rescue soon.

---

### Post by grattemedi on 2006-01-13
Hy , in this topic Shinkan says that he resolved the battery status problem.
He modified his dsdt tables and he gave me this url to download his dsdt for acer 1641 : [http://shinkan.info/](http://shinkan.info/)
Now it works !! :D

---

### Post by iNerdSure on 2006-01-13
[QUOTE=grattemedi]Hy , in this topic Shinkan says that he resolved the battery status problem.
He modified his dsdt tables and he gave me this url to download his dsdt for acer 1641 : [http://shinkan.info/](http://shinkan.info/)
Now it works !! :D[/QUOTE]
Many thanks. I've fixed the battery meter problem earlier with Er-ku's help. I really hope for a SOUND solution soon. Not able to use Skype on this laptop is making it very inconvenient in my work. I have to switch PCs each time I need to make or receive Skype calls. :(

---

### Post by Muffe on 2006-01-16
What is the status with the sound problem at the monent? Has anyone found a solution? If not, has anyone tried Dapper Drake on their machines and tried to get it working?

I have an Acer Travelmate 3000 and the soundcard has not been working since the Windows-days right after I bought it. Now I want sound.

I have not read the entire thread, and I ask for apologize if this question has been raised by someone else beofore me.

BTW; thanks for all help and thanks for a great support forum. That's what really matters every time it's time to reconsider and look after new distros.

---

### Post by iNerdSure on 2006-01-19
[QUOTE=Muffe]What is the status with the sound problem at the monent? Has anyone found a solution? If not, has anyone tried Dapper Drake on their machines and tried to get it working?

I have an Acer Travelmate 3000 and the soundcard has not been working since the Windows-days right after I bought it. Now I want sound.

I have not read the entire thread, and I ask for apologize if this question has been raised by someone else beofore me.

BTW; thanks for all help and thanks for a great support forum. That's what really matters every time it's time to reconsider and look after new distros.[/QUOTE]
Someone did report that his Acer 4060 or (4061?) had sound but he did not continue the discussion on this forum, and he did not post the details of his "success". So, for the time being, unfortunately, we are all sadly muted in a SILENT barrier. :(

---

### Post by GrannyTux on 2006-01-19
I just booted Breezy 5.10 live on my new acer 3613 I used vga=771 and the noacpi thing in the boot arguements and all went well I have sound off the live cd..
these are my specs
ubuntu@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller ( rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH 6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 03)
0000:06:05.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 0 1)

---

### Post by breakdown on 2006-01-19
hi to all
i've also got an acer aspire 1641 wlmi
now i can hear sound from line-jack only (with headphones), after editing file patch_realtek.c in alsa-driver 1.0.11rc2 sources
i follow this report on alsa-bug:

[https://bugtrack.alsa-project.org/alsa-bug/print_bug_page.php?bug_id=1618]("https://bugtrack.alsa-project.org/alsa-bug/print_bug_page.php?bug_id=1618")

i hope this can help somebody
bye

---

### Post by erganondorf on 2006-01-24
Hi. I have a Mitac model 8050Q. Very similar to Acer ( audio ICH6 family, etc.). Just followed [http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy](http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy). Success!!! Now my laptop is not silent anymore.
Regards,
Eric.

---

### Post by iNerdSure on 2006-01-25
That's encouraging news. Does your laptop have the Realtel ALC260 chip as well? There was a similar posting some time back on the success of following the link you provided. But apparently the solution works only for the ALC880 and not ALC260.

---

### Post by viridis on 2006-01-26
I found some interesting things:

cat /var/log/messages | grep ACPI :

ACPI: PCI interrupt for device 0000:00:1b.0 disabled
ACPI: PCI Interrupt 0000:00:1b.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
    ACPI-0768: *** Warning: Thread 8F7 could not acquire Mutex [<NULL>] AE_BAD_PARAMETER
    ACPI-0768: *** Warning: Thread 93E could not acquire Mutex [<NULL>] AE_BAD_PARAMETER
    ACPI-0768: *** Warning: Thread 944 could not acquire Mutex [<NULL>] AE_BAD_PARAMETER

lspci:

00:1b.0 Class 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

Interrupt for sound card is disabled, so maybe this explains why dmidecode shows:

Handle 0x000D
        DMI type 10, 6 bytes.
        On Board Device Information
                Type: Sound
                Status: Disabled
                Description: ADI

So it seams that ACPI settings is causing the problem, now we should find a solution, how to fix that.

---

### Post by jakub on 2006-01-27
Finally I have sound on my Fujitsu-Siemens. It was a surround problem in alsa. I've manually patched hda_codec.c in alsa-driver-1.0.11rc1/pci/hda with code shown in here:
[http://sq5bpm.sp5zcc.waw.pl/v2040/hda_codec.diff]("http://sq5bpm.sp5zcc.waw.pl/v2040/hda_codec.diff")
(switches off sorround channels)

and installed everything again following:
[http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy]("http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy")

and now I am very happy \\:D/ 

Maybe it will work for you.

---

### Post by iNerdSure on 2006-01-28
Will like to try, but could you please elaborate on the steps involved. Especially the "manually patched" codec. Thanks in adavnce.

---

### Post by jakub on 2006-01-30
OK. In the link to hda_codec.diff you have a fragment of the file hda_codec.c. So after you extract alsa_driver (this is described in the "Alsa 1.0.10 Setup on Ubuntu Breezy" Howto) you have to find this file, find the fragment shown in hda_codec.diff and:
1. remove or comment the lines marked with ' - '
2.  add line marked with ' + '

I used alsa-driver-1.0.11rc1 - so the hda-codec.c file was located in alsa-driver-1.0.11rc1/pci/hda. 
I guess the patch process can be done automatically with some command, but I don't know wich one, so I did it manually as described.

After this, you may continue with steps described in Howto.

I hope this explanation is understandable, because english is not my native language.

---

### Post by viridis on 2006-01-30
You can apply this patch with the command patch(1), it is quite simple, read man page if you are interested. Unfortunately this patch didn't solve the problem with my laptop (Acer TravelMate 4062).

I'm going to try the new version of alsa-driver, I hope someday we will breake the silence. :)

Good luck for everybody.
Giedrius

---

### Post by viridis on 2006-01-30
Finally I got the sound working :)

I use fujitsu as a model for alc260 and the sound is playing from line-in jack. It is quite weird, but it works. The problem is that acer don't use default pin mappings and we need to fix that, it can be done by editing patch_realtek.c file. Maybe I will try to do that later.

---

### Post by ez3kiel on 2006-01-30
Could you please do a Step by step process of this?
I too own an Acer notebook (acer 1640 series) and have everything working flawlessly except for the sound.
Much appreciated!

---

### Post by iNerdSure on 2006-02-01
[QUOTE=viridis]Finally I got the sound working :)

I use fujitsu as a model for alc260 and the sound is playing from line-in jack. It is quite weird, but it works. The problem is that acer don't use default pin mappings and we need to fix that, it can be done by editing patch_realtek.c file. Maybe I will try to do that later.[/QUOTE]
I am very keen to try fixing the "default pin mappings" you descibed. Can you please help with a step-by-step edit of patch_realtek.c file ?

Many thanks in advance.

---

### Post by er-ku on 2006-02-01
[QUOTE=viridis]Finally I got the sound working :)

I use fujitsu as a model for alc260 and the sound is playing from line-in jack. It is quite weird, but it works. The problem is that acer don't use default pin mappings and we need to fix that, it can be done by editing patch_realtek.c file. Maybe I will try to do that later.[/QUOTE]

interesting. Maybe if you live in Vilnius, we could meet and errr...... TRY to make an appropriate patch for the Acer? Alone, i doubt i'd be able to.. :-| 


Btw either someone has stolen my password, or I had an unfinished browser session connected to the forums... :-k

---

### Post by iNerdSure on 2006-02-01
[QUOTE=er-ku]interesting. Maybe if you live in Vilnius, we could meet and errr...... TRY to make an appropriate patch for the Acer? Alone, i doubt i'd be able to.. :-| 


Btw either someone has stolen my password, or I had an unfinished browser session connected to the forums... :-k[/QUOTE]
This certainly sounds promising. I wish I could help, but being a Linux newbie, and from a non-tech background, I could only offer feedback on whether the "Acer patch" solution works on my laptop (Acer 4060)

So far, I've tried without any squeak of success the various ALSA latest version drivers. Not sure what the "default pins mapping" entails and the complexity, but whatever it takes, sound and VOIP on Skype are crucial for my work, and switching completely over from WinXP.

---

### Post by viridis on 2006-02-01
[QUOTE=ez3kiel]Could you please do a Step by step process of this?
I too own an Acer notebook (acer 1640 series) and have everything working flawlessly except for the sound.
Much appreciated![/QUOTE]

I'm not sure if this works for your laptop, because it is a little different from mine, but you can try. When loading sound modules set the model=fujitsu option. I don't use ubuntu, so I can't tell how to do this, you can try to edit /etc/modprobe.d/sound file, it works for me. After that restart the sound system and plug your headphones in the line-in jack, the sound should come. Also make sure that your mixer settings are alright. I hope this will help you.

Giedrius

---

### Post by viridis on 2006-02-01
[QUOTE=er-ku]interesting. Maybe if you live in Vilnius, we could meet and errr...... TRY to make an appropriate patch for the Acer? Alone, i doubt i'd be able to.. :-|[/QUOTE]

I would be very happy to fix that problem, but unfortunately I don't get the idea how patch_realtek.c works. I know what part of the code needs to be fixed, but I don't think I could do this without the help of expert. Maybe we should ask for help those people who fixed this file, or maybe alsa devs. When I have some extra time I will try find some information how to fix that problem.

Giedrius

---

### Post by iNerdSure on 2006-02-03
Looks like this posting has not neen read by expert/s who could help us out. Hopefully someone can pick up this thread and show us the way to break the NO SOUND SILENT barrier soon. Or, maybe the new Dapper Drake release will come with the appropriate patches built-in.

---

### Post by iNerdSure on 2006-02-03
Anyone experimented with the latest ALSA drivers in 1.0.11rc3 releases? If yes, hope you would share the experience, good or bad. Thanks in advance.

---

### Post by er-ku on 2006-02-04
> I would be very happy to fix that problem, but unfortunately I don't get the idea how patch_realtek.c works. I know what part of the code needs to be fixed, but I don't think I could do this without the help of expert. Maybe we should ask for help those people who fixed this file, or maybe alsa devs. When I have some extra time I will try find some information how to fix that problem.

I'm not a dev either, that's why i thought experimenting in company is less boring. ;)

And a mini-tutorial on all this is at [https://bugtrack.alsa-project.org/alsa-bug/print_bug_page.php?bug_id=1618](https://bugtrack.alsa-project.org/alsa-bug/print_bug_page.php?bug_id=1618)

> Anyone experimented with the latest ALSA drivers in 1.0.11rc3 releases?

Nope.

---

### Post by ryuko2002 on 2006-02-12
I managed to have sound in my computer using this forum. I have a fujitsu-siemens amilo pro 2040.
I used these 2 sites:[http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy](http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy)
[http://student.fiit.stuba.sk/~kotuc04/suse/](http://student.fiit.stuba.sk/~kotuc04/suse/)

1)Download the files from the 1st site and uncompress the two tgz files.
2)Patch using the file from the 2nd site: patch -i hda_codec-diff.txt
3)Follow the steps from the 1st site.
IMPORTANT:You also need to install GCC 3.4 (use synaptic, its easy) to build the alsa files. (there is one previus reply in this thread of a guy that was having errors building the files... he was missing GCC 3.4).

Good luck and thanks to all ubuntu comunity!!

---

### Post by ryuko2002 on 2006-02-12
I followed Er-Ku batery tutorial for my fujitsu but something went wrong. When booting up the kubuntu screen appears instead of ubuntu's and kernel 12-10 doesnt work. 12-9 did and try to reinstall the 12-10 kernel but the soundcard isnt recognised. I format the laptop and im starting from scratch.
I guess i had bad luck or installed something not suitable for my computer.

---

### Post by iNerdSure on 2006-02-12
Experimented with ALSA 1.10.11rc3 drivers today. Still NO SOUND! Absolute SILENCE :( 

The dmidecode output still shows "Disable" status:
[PHP]
Handle 0x000D
        DMI type 10, 6 bytes.
        On Board Device Information
                Type: Sound
                Status: Disabled
                Description: ADI
[/PHP]
So, perhaps, the cause isn't with the ALSA drivers, but rather that of the BIOS? Anyway, I'm just not technically competent enough to figure out.

---

### Post by er-ku on 2006-02-12
[QUOTE=ryuko2002]I managed to have sound in my computer using this forum. I have a fujitsu-siemens amilo pro 2040....[/QUOTE]

Dear ryuko2002, thank you for your support. But this topic is about Acer laptops, not about Fujitsu-Siemens. I don't think they are the same or act identically in this case, so the patch that works with Fujitsu may or may not work with Acer, and vice-versa. Same applies for the battery. I hope you didn't use the DSDT that I supplied, because it is designed for an Acer Travelmate 4061WLMi, not for Fujitsu-Siemens... If the battery meter doesn't work out-of-the-box (without additional DSDT supplied) for you, you'll have to either find a DSDT designed, or at least suitable, for your model, or to fix yourself what Fujitsu-Siemens has provided you with (I think I left some useful links in my posting).

[QUOTE=iNerdSure]Experimented with ALSA 1.10.11rc3 drivers today. Still NO SOUND! Absolute SILENCE[/QUOTE]
SNIP!
> So, perhaps, the cause isn't with the ALSA drivers, but rather that of the BIOS? Anyway, I'm just not technically competent enough to figure out.

No, it's not. That was my wrong guess. Now, with some explanations from ALSA guys, I know what the exact problem is. And it's just sooo simple - our sound IS indeed technically working, but it's just redirected to a wrong pin on the chip. This results in it either getting literally lost in space, or being output to a wrong jack. You may probably even get the sound in some jack, by simply trying out all the built-in settings for these model names (you may try these by simply passing a "model=MODELNAME" line to the module):
[LIST]
[*]basic
[*]hp
[*]fujitsu
[/LIST]

This may, for example, result in sound playing from the earphones connected to the mic or line in jacks, or something like that.

However, I've subscribed to the alsa-dev mailing list, and asked guys there to implement a "test" model for ALC260, which would allow you to use ALSA mixer for virtually anything that can theoretically be done with this codec. I've checked - the patch by Jonathan Woithe is already integrated into the upstream snd_hda_intel driver. That's good news.

This week we'll have a long weekend in Lithuania, so I'm going to meet my mom, borrow her notebook, try to compile and install ALSA from the CVS there, and test the things. If things go well (I hope they do), there'll probably be an "acer" model in ALSA 1.0.11, which would end our problems. Or, if we're not so lucky, we would have it in the next version, hopefully. So, again hopefully, there's not much left to wait.

If you want, feel free to play with the "test" model yourselves. But I don't feel like giving a tutorial on compiling a CVS version of ALSA here today.

G'nite

---

### Post by iNerdSure on 2006-02-13
Dear Er-ku, many thanks for the insight. I have no clue how to compile a CVS version. But it's comforting to know that we are very close to breaking the NO SOUND barrier. I'm quite busy with work over the next 2 days. Perhaps, Thursday or Friday, I may find some time to google "CVS how to" and give it a try.

---

### Post by er-ku on 2006-02-13
[QUOTE=iNerdSure]Dear Er-ku, many thanks for the insight. I have no clue how to compile a CVS version. But it's comforting to know that we are very close to breaking the NO SOUND barrier. I'm quite busy with work over the next 2 days. Perhaps, Thursday or Friday, I may find some time to google "CVS how to" and give it a try.[/QUOTE]

Then just wait. Additional few days won't change anything.

---

### Post by iNerdSure on 2006-02-13
Yes, I think I'll wait for a couple of days. Today, a friend requested me to install Breezy on his IBM T40, dual boot with Win XP. Surprisingly, the installation was a breeze, and sound and video, after installing codecs via Automatix, was all working. Now, I know what music and African drum beats I have been missing all this while :( 

Well, I now eagerly look forward to the CVS compile over this long weekend. :-D

---

### Post by rverrips on 2006-02-13
Hiyee

I am currently experiencing the same issues with an Acer Aspire 1642 WLMi (1640 series with Celeron 1.7 Ghz and 512MB ram) 

This model of Aspire laptop also has the Intel HDA sound card with Realtek ALC260 Chipset.

Firstly, I've loved and started using Debian 4 years now - The move to Ubuntu last year has been a good one.  I've installed Ubuntu on 4 or 5 different hardware configurations and never had any major problems with hardware, aside from a few DMA issues with a CD-Rom drive once, and the usualy NVidia driver issues which are now SO easy to repair with Automatix!

Anyway - I had same BIOS / Battery issues showing no battery status, and resolved with a new DSDT - Howto I found on this posting thread :-)

Needed 855resolution BIOS Fix to get crisp LCD resolution of 1280x800 to better the default 1024x768 default

Also installed Acerhk, even though I wasn't too bothered 'bout Fn+keys not working 100%

I've also tried upgrading ALSA to 1.0.10 and still don't have sound working on my laptop, although all else is pretty peachy at the moment.

For a kick I tried Dapper Flight release 2, but same overall experience (except I couldn't get Automatix for Dapper to work, so lost interest and reverted back to Breezy)

Please let me know once this issue is resolved

Yours for the 'cause of open-source

Roy

---

### Post by er-ku on 2006-02-14
Hey, rverrips,

It's good to see Acer users gathering around this thread. The sound issue will probably have a fix by next monday (no promises though), so just follow this thread, I'd like to see at least a few people confirming what I may find out.

P.S. Anyone is free to contact me when i'm online. ;)

Happy Valentine! ;)

---

### Post by iNerdSure on 2006-02-14
Shared learning and shared experiences with Breezy on Acer (and other brands, models) will certainly contribute to more converts and a stronger community. Best wishes and many thanks to Er-ku and everyone on this forum/thread.

---

### Post by ryuko2002 on 2006-02-14
I know this thread treat issues with acer laptops, but in it i found the solution for my fujitsu, thats why i wanted to share it with you. Good luck !

---

### Post by er-ku on 2006-02-14
[QUOTE=ryuko2002]I know this thread treat issues with acer laptops, but in it i found the solution for my fujitsu, thats why i wanted to share it with you. Good luck ![/QUOTE]

That's OK. I didn't mean to sound angry. ;)

---

### Post by SimonWalker on 2006-02-14
I have been following this thread with interest

I too have a Acer Travelmate 4060

No Sound or Battery indicator.

I tried  the latest release of Dapper, this too fails to give sound. The FN keys and battery indicators seem to work. However after "playing"  it failed to reboot. I have reverted back to breezy. Looking  forward to hearing the distant drums

---

### Post by er-ku on 2006-02-15
OK, I have the laptop. I've compiled the drivers from CVS, installed and loaded them. There is sound. Not from the integrated speakers though. Not even from the headphones jack. :D I get the sound from Line In and Mic jacks. I don't like it yet. :)

Still searching for more...

---

### Post by iNerdSure on 2006-02-16
Wow, great news. Not quite at the end of the (sound) tunnel yet, but at least youn have broken the silence barrier. Hopefully, we get light and sound at the end of the tunnel very soon. Best of luck. :)

---

### Post by er-ku on 2006-02-16
Thanks. However, i seem to have stuck a little. I got the internal microphone working (when i set the channel type to Microphone instead of Line Out/Headphones). :) However, I still cannot get neither the internal speakers, nor the headphone jack to do what they're intended to. Also, when I play a CD (with an old cd-player, that presumably doesn't try to use the PCM channel to play it), i don't hear it too.

I'm discussing it on the ALSA mailing list though. I'm still in hope to find the solution, and, in the worst case, we could simply use the Line In jack for Line out. ;)

Btw, I didn't manage to make a nice deb with alsa yesterday, so I did it the bad way - ./configure, make, sudo make install...

---

### Post by micvm on 2006-02-16
Hey to all!

I have an ACER Aspire 1641WLMi. Just wanted to post that I did as er-ku said: just took alsa-drivers (1.0.11rc2) and alsa-lib from the website compiled them, and took as model parameter fujitsu. Now from the line-in jack finally I got sound. So thanks to all for their efforts in the meantime. Hope the alsafix for the internal speakers, microphone etc. will come soon :)

---

### Post by iNerdSure on 2006-02-17
Hi Er-ku, looks like you made some progress, even though it wasn't up to your expectation. I'm quite happy to get sound out of any jack, so long as I could use Skype in my work. Right now, each time I need sound, I need to find a Win PC. Will you be able to share your "work-in-progress" steps? 

Many thanks in advance.

---

### Post by er-ku on 2006-02-17
Hi,
instead of compiling and installing why don't you try this temporary solution:

Add the following line to the top of /etc/modprobe.d/snd_hda_intel.modprobe (note you need root access to do this):
```
options snd-hda-intel model=fujitsu
```

Then issue the following command:
```
sudo /etc/init.d/alsa force-reload
```

After this, go to your mixer. If appropriate controls exist, ensure that "Mic/Line Jack Mode" is "Mic 50pc" or "Mic 80pc", and that "Headphone Jack Mode" is "Line Out" or "Headphones". The master volume slider should be called "Headphone Playback Volume", I think. Now, connect external speakers to the Line In jack on your laptop. Try playing some sound. If you hear something, congratulations. Adjust the rest of the sliders the way you want. But remember, that this is just a temporary workaround. Don't get used to it. ;)

Btw, I haven't tested this myself, so please post your comment on whether this workaround works or not. ;)

---

### Post by iNerdSure on 2006-02-18
Thanks, Er-ku. My system has no " /etc/modprobe.d/snd_hda_intel.modprobe " file. The only similar file I found was: " /etc/modprobe.d/sound ". The contents show: 
[PHP]
options snd  device_mode=0666
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
[/PHP]
Do I create the file, or is there something else I should attempt first? Thanks, again.

---

### Post by er-ku on 2006-02-18
[QUOTE=iNerdSure]Thanks, Er-ku. My system has no " /etc/modprobe.d/snd_hda_intel.modprobe " file. The only similar file I found was: " /etc/modprobe.d/sound ". The contents show: 
[PHP]
options snd  device_mode=0666
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
[/PHP]
Do I create the file, or is there something else I should attempt first? Thanks, again.[/QUOTE]
It doesn't matter indeed, but for a sake of tidiness, just create it. :) Make sure its owner/group and permissions are same as those of other files in that directory.

---

### Post by iNerdSure on 2006-02-18
Well, created the file and followed by: sudo /etc/init.d/alsa force-reload. Still no sound. Looks like my sound card has "disappeared" and is no longer detected by the system! Wonder where have I gone wrong ?

---

### Post by poter on 2006-02-18
Thanks to the people of this forum. Now I have batery state indicator and sound from line-in on my Acer TM4062LMi with intel hda and ALC260. Perhaps is the alsa team coming soon with a true solution for all of us?.
iNerdSure, I just added "options snd-hda-intel model=fujitsu" line to my /etc/modprobe.d/sound file and, after reloading alsa, the sound is coming out from line-in jack to my headphones. Good luck to all.

---

### Post by iNerdSure on 2006-02-19
Many thanks, Er-ku. Finally, I have sound. Silence barrier is broken. :-D  Even though, it's only from the headset plugged into the line-in socket! And the speakers are still silent.

But it's fantastic progress! First sound since October 2005 Breezy release on this Acer 4060. Now, I don't have to buy an M$WinXP licence to install a dual-boot setup.

---

### Post by rverrips on 2006-02-23
[QUOTE=er-ku]Hey, rverrips,

It's good to see Acer users gathering around this thread. The sound issue will probably have a fix by next monday (no promises though), so just follow this thread, I'd like to see at least a few people confirming what I may find out.
[/QUOTE]

Hey Er-ku

When you say a fix will be available, are you referring to the "sound works though the line-in port, but no internal speaks" or an actual fix where the internal speakers, line-in, mic and earphone jacks all function as expected?

Yours for the cause of open-source

Roy

---

### Post by er-ku on 2006-02-23
hi all,

the fact that for the time being i'm not posting any news here actually means that there are none. The way to make internal speakers/headphone jack work has not yet been discovered, but I hope we on the ALSA mailing list will find a way to make them work. As for the meantime, just use the fujitsu option. I don't see much point in adding an Acer model for now, while it's not yet working. On the other hand, it might be useful (irregular sound setup is still better than no sound), so i'll probably advice the devs to make ALSA automatically detect Acers and set them up appropriately (maybe by simply loading Fujitsu settings for them).

However, i'll be busy until this weekend, and probably even on the weekend too (got some boring and tricky webmastering to do), so I can't promise any updates in the meantime. But I'm watching the ALSA list, so if there will be news on it, I'll post them here.

Bye.

---

### Post by er-ku on 2006-02-24
Hi everybody,

take your seats. Relax. Smile.

A [solution](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1618) to our problem has finally been discovered on ALSA mailing list/bug tracking system. For two Acer users out of two who have already tested it, it worked. I'm gonna test it too. Maybe tomorrow. And I'm somehow very sure it will work. ;)

I think you can finally expect Acer sound to work without any tweaking in the next release of ALSA. Also, I'll probably ask you all to execute a few commands in order to realise this automotion. Stay tuned! :)

---

### Post by iNerdSure on 2006-02-25
Hi Er-ku, thanks for the great news. \\:D/  I look forward eagerly to testing the solution on my Acer 4060. In the meantime, have been helping friends install  Ubuntu Breezy (dual-boot with existing WinXP and 98) on an IBM T43, Acer 430, and a few couple of desktops. All without any hitch.

Somehow, I have a sense that the Acer 4060 is simply not suitable for Breezy. But it has been a great learning experience for me. A nice feature is the ability to mount Win partitions automatically, and also run clamscan to clean out Win partitions that were virus infected previously.

Well, it's really a great community of sharing learning and experience.

---

### Post by er-ku on 2006-02-25
[QUOTE=iNerdSure]Somehow, I have a sense that the Acer 4060 is simply not suitable for Breezy.[/QUOTE]

how come? :confused:

---

### Post by iNerdSure on 2006-02-25
Well, compared with IBM T43, for example, Breezy was installed with almost all "default" selections, and wireless network, sound, battery meter, keyboard shortcut keys, etc work straight "out-of-the-box". 

Whereas with Acer 4060, we've had wireless network, battery meter, and most daunting of all, sound card problems.

I've also installed on 2 older Acer laptops, TM403 and another I can't remember the model number, they were also working straight "out-of-the-box".

Anyway, I'm eagerly optimistic we can find a solution real soon. :D

---

### Post by er-ku on 2006-02-25
Maybe that's just because the Acer is a relatively new model? :) This doesn't mean it's not "designed for Linux" at all.

---

### Post by iNerdSure on 2006-02-25
Well, you may be right. My comment was based on the comparison with IBM T43, which is a relatively new model as well. Anyway, I'm quite happy with the learning experience.

If the Acer 4060 had worked "out-of-the-box" with Breezy, then I would not have been "forced" to learn more of CLI codes, compiling drivers, etc .. And many thanks to the Ubuntu community, especially expert users like you.

Sometimes, the journey is as important, if not more, than the destination. :D

---

### Post by er-ku on 2006-02-26
:) learning is good, especially when you have time and will for that. :)

I've tested the fix on my mom's laptop. It works. I got sound from the internal speakers! ;) Headphone jack works too &#8211; they're interchangeable (speakers are automatically muted when you plug something into the headphones jack). I've sent a preliminary patch, adding Acer support, to ALSA developer mailing list. They have a few more uncommitted patches to the same file at the moment, and are going to commit everything at once. That's very likely to happen this week, so the next version of ALSA (1.0.11) should support Acer notebooks out of the box.

So far there are only two problems left. One is that I cannot use an old CD player to play an audio CD (it plays, but there's silence; this doesn't matter for GNOME, though), and the second is that the computer doesn't do beeps (I don't even know if it should). I hope we on ALSA mailing list/BTS will find a solution at least for the CD problem, but it's not a big deal even if we don't (I'll just remove relevant controls from the mixer in that case).

I'll post here again when the patches hit CVS. I'll want some Acer users to test the driver, and report successes or failures here. Also, I'll want your soundcard subsystem ID numbers in order to make the driver auitomatically recognise Acer laptops.

---

### Post by Sanglob on 2006-02-27
Hi!

Thanks a lot to all the people in this forum that has been working in conquering new Acer laptops for Linux! I have an Acer 1640 and now I have sound... from the line out but sound.

As an absolutely newbie I was not able to help, but I will be happy to collaborate given er-ku my soundcard subsystem ID numbers if somebody explains me how to do it.

Also, I know this is not the correct post, but as it is populated by some 1640 users that claims that ubuntu is working flawless (apart from the now solved sound problem) I would like to ask for some help with the DSDT to get my battery metter and hybernation working. I get some errors compiling it, and after editing the code and compiling without errors my computer crash on startup   :( any ideas of what can I do?

Thanks a lot again!

---

### Post by iNerdSure on 2006-02-27
[PHP]
I'll want some Acer users to test the driver, and report successes or failures here. Also, I'll want your soundcard subsystem ID numbers in order to make the driver auitomatically recognise Acer laptops.
[/PHP]

Hi Er-ku, let me know what I need to do to participate in the test. Many thanks for the breakthrough, in breaking the silence barrier. \\:D/  I eagerly await the new driver files and patches.

---

### Post by poter on 2006-02-27
**Sanglob,** you can download a fixed DSDT for your laptop at [http://acpi.sourceforge.net/dsdt/view.php?id=577]("http://acpi.sourceforge.net/dsdt/view.php?id=577")   and get instructions to load it in your initrd at [http://gaugusch.at/kernel.shtml]("http://gaugusch.at/kernel.shtml").
Another way is to decompile and recompile the fixed dsdt (with iasl) in order to get the DSDT.hex. Rename it to dsdt_table.h and move or copy it to /usr/src/ and add the lines:
#define CONFIG_ACPI_CUSTOM_DSDT
#define CONFIG_ACPI_CUSTOM_DSDT_FILE "/usr/src/dsdt_table.h"
to /usr/src/linux/drivers/acpi/osl.c
Recompile the kernel, install it and reboot, and you are done. This worked for me on Acer TM 4062 with 2.6.15 kernel. Hope this helps you.
**er-ku,** I am anxious to become a tester for those patches we are yearning for.

---

### Post by er-ku on 2006-03-04
Hello all,

first, **Sanglob**, you should just read through the thread ([here](http://ubuntuforums.org/showpost.php?p=604504&postcount=72)). I've uploaded an already compiled DSDT table, and a small tutorial on how to make it work without recompiling the kernel or any other scary stuff. ;) THe DSDT itself is now also uploaded to [http://acpi.sourceforge.net/dsdt/view.php?id=579](http://acpi.sourceforge.net/dsdt/view.php?id=579)

---

### Post by er-ku on 2006-03-04
Hi again,

now the sound instructions. This won't be so much like it should be in Ubuntu (generation of a .deb package), but nevermind. ;) At least, it works. Anyone can feel free to improve this HOWTO. :)

[LIST=1]
[*] First, some preparation steps. Run the terminal and get the cvs, building tools and kernel headers (if you don't have them yet). Run the following command to the terminal:
```
sudo apt-get install autoconf automake build-essential cvs linux-headers-$(uname -r |cut -f3 -d-)
```
Now, let's create a /usr/src/linux symlink pointing to our kernel headers:
```
sudo ln -s linux-headers-$(uname -r) /usr/src/linux
```
After all this is done, we can continue with ALSA.

[*] First, run terminal and cd to anywhere you like (or stay in your homedir):
Create an empty directory there and cd to it:
```
mkdir alsa
cd alsa/
```

[*] Log onto the anonymous CVS repository of ALSA project:
```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/alsa login
```
Press Enter when CVS asks for a password

[*] Get the latest CVS repository:
```
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/alsa co .
```
Don't forget the trailing slash!

[*] cd to alsa-driver directory:
```
cd alsa-driver/
```

[*] Compile your drivers. Because we only have problems with one particular soundcard model, and this happens on a notebook, we won't compile ALL the drivers, but just a minimal set. We'll use the "cvscompile" script because this is the cvs version:
```
./cvscompile --with-debug=full --with-cards=hda-intel
sudo make install
```

This step takes a few minutes.

[*] Ensure you're not using any "model=" options for snd-hda-intel. If you followed my previous instructions on enabling sound on line-in, edit /etc/modprobe.d/snd-hda-intel.modprobe, and comment out the "options snd-hda-intel model=fujitsu" line.

[*] Leave the terminal and restart your computer.
[/LIST]

If you're using an Acer, you should get sweet Ubuntu drums from the integrated speaker after restarting. However, if you don't, please check your mixer - maybe some channels are muted or so?..

If you still don't get any sound, edit /etc/modprobe.d/snd-hda-intel.modprobe again, this time adding a line "options snd-hda-intel model=acer", and reboot after that. However, I don't think you're likely to need it.

The numbers I wanted from Acer users are easy to find out. Just run a terminal and issue the command:
```
lspci -nvd 8086:2668
```
Then paste the first two lines of the output here, as a comment to this post, like this:
```
0000:00:1b.0 0403: 8086:2668 (rev 04)
    Subsystem: 1025:008f
```

Also, please state what laptop model you've got.

Actually, so far, autodetection of an Acer only works when Subsystem string is 1025:008f (my mothers notebook). ;)

Hope to hear your comments soon.

P.S.: CD and Beep controls seem not to work so far, so don't report that. Instead, report if they DO work (ie if muting the CD channel in the mixer actually mutes the sound going from the CD, and so on). ;)

---

### Post by iNerdSure on 2006-03-04
Many thanks, Er-Ku. But unable to proceed, with such error messages:
[PHP]
1:~$ sudo apt-get install linux-headers-2.6.12-10-686 -r |cut -f3 -d-
Password:
E: Command line option 'r' [from -r] is not known.
[/PHP]
[PHP]
:~/alsa$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/alsa login
bash: cvs: command not found
[/PHP]
Am I missing some steps or keying in wrong commands? :confused:

---

### Post by iNerdSure on 2006-03-04
Hi again, Er-Ku. I managed to install "CVS" and "Autoconf" from Synaptic Package Manager. But the installation ran into error at:
[PHP]
./configure --with-debug=full --with-cards=hda-intel
[/PHP]
error message:
[PHP]
config.status: error: cannot find input file: toplevel.config.in
[/PHP]
What am I missing this time? :confused:

---

### Post by iNerdSure on 2006-03-04
This is the complete ouput:
[PHP]
:~/alsa/alsa-driver$ ./configure --with-debug=full --with-cards=hda-i ntel
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/ptc/alsa/alsa-driver
./configure: line 3115: ALSA_TOPLEVEL_INIT: command not found
checking cross compile...
checking for directory with kernel source... /lib/modules/2.6.12-10-686/build
checking for directory with kernel build...
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.12-10-686
checking for GCC version... Kernel compiler: gcc 3.4.5 20050809 (prerelease) (Ub untu 3.4.4-6ubuntu8) Used compiler: gcc (GCC) 4.0.2 20050808 (prerelease) (Ubunt u 4.0.1-4ubuntu9)
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... yes
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... no
Creating <linux/platform_device.h>...
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... no
Creating <linux/mutex.h>...
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... module
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.12-10-686/ker nel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... full
checking for ISA support in kernel... yes
checking for processor type... i686
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... no
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... no
checking for driver version... 1.0.11rc3
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... may be buggy, skipped
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... yes
checking for old driver suspend/resume callbacks... yes
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... yes
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
./configure: line 9769: ALSA_TOPLEVEL_SELECT: command not found
./configure: line 9779: ALSA_TOPLEVEL_OUTPUT: command not found
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: error: cannot find input file: toplevel.config.in
ptc@sgc9711:~/alsa/alsa-driver$ ./configure --with-debug=full --with-cards=hda-i ntel
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/ptc/alsa/alsa-driver
./configure: line 3115: ALSA_TOPLEVEL_INIT: command not found
checking cross compile...
checking for directory with kernel source... /lib/modules/2.6.12-10-686/build
checking for directory with kernel build...
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.12-10-686
checking for GCC version... Kernel compiler: gcc 3.4.5 20050809 (prerelease) (Ub untu 3.4.4-6ubuntu8) Used compiler: gcc (GCC) 4.0.2 20050808 (prerelease) (Ubunt u 4.0.1-4ubuntu9)
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... yes
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... no
Creating <linux/platform_device.h>...
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... no
Creating <linux/mutex.h>...
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... module
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.12-10-686/ker nel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... full
checking for ISA support in kernel... yes
checking for processor type... i686
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... no
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... no
checking for driver version... 1.0.11rc3
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... may be buggy, skipped
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... yes
checking for old driver suspend/resume callbacks... yes
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... yes
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
./configure: line 9769: ALSA_TOPLEVEL_SELECT: command not found
./configure: line 9779: ALSA_TOPLEVEL_OUTPUT: command not found
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: error: cannot find input file: toplevel.config.in
ptc@sgc9711:~/alsa/alsa-driver$ clear

ptc@sgc9711:~/alsa/alsa-driver$ ./configure --with-debug=full --with-cards=hda-i ntel
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/ptc/alsa/alsa-driver
./configure: line 3115: ALSA_TOPLEVEL_INIT: command not found
checking cross compile...
checking for directory with kernel source... /lib/modules/2.6.12-10-686/build
checking for directory with kernel build...
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.12-10-686
checking for GCC version... Kernel compiler: gcc 3.4.5 20050809 (prerelease) (Ub untu 3.4.4-6ubuntu8) Used compiler: gcc (GCC) 4.0.2 20050808 (prerelease) (Ubunt u 4.0.1-4ubuntu9)
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... yes
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... no
Creating <linux/platform_device.h>...
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... no
Creating <linux/mutex.h>...
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... module
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.12-10-686/ker nel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... full
checking for ISA support in kernel... yes
checking for processor type... i686
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... no
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... no
checking for driver version... 1.0.11rc3
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... may be buggy, skipped
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... yes
checking for old driver suspend/resume callbacks... yes
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... yes
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
./configure: line 9769: ALSA_TOPLEVEL_SELECT: command not found
./configure: line 9779: ALSA_TOPLEVEL_OUTPUT: command not found
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: error: cannot find input file: toplevel.config.in
     :~/alsa/alsa-driver$
[/PHP]
Looks like the last 10 lines
[PHP]
./configure: line 9769: ALSA_TOPLEVEL_SELECT: command not found
./configure: line 9779: ALSA_TOPLEVEL_OUTPUT: command not found
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: error: cannot find input file: toplevel.config.
[/PHP]
of ouput suggest that I'm either missing something or not doing something correctly. :confused:  Please help. Many thanks.

---

### Post by gargameljura on 2006-03-04
Hi!

First of all thanks for the patch, er-ku, also thanks for the patch for battery level status display, they both work for me quite nicely!

however there is an error in your instructions on how to build latest ALSA driver from CVS source - when building, **cvscompile** script should probably be used instead of **configure** as those files that iNerdSure reports as missing (toplevel.config, toplevel.config.in) are created by **cvscompile** script.

thanks again for patches!

---

### Post by er-ku on 2006-03-04
> **gargameljura]however there is an error in your instructions on how to build latest ALSA driver from CVS source - when building, **cvscompile** script should probably be used instead of **configure** as those files that iNerdSure reports as missing (toplevel.config, toplevel.config.in) are created by **cvscompile** script.[/QUOTE]

You're right... :) Before running autoconf and stuff, I actually ran cvscompile for a few seconds, then aborted it as I assumed it would compile everything for me....

I've edited my post right now.  said:**
> thanks again for patches!

You're welcome! :)

---

### Post by iNerdSure on 2006-03-04
Hi, I've repeated the steps from the very beginning. Encountered similar error when I reached the step:
[PHP]
./cvscompile --with-debug=full --with-cards=hda-intel
[/PHP]
The output (first 6 lines): 
[PHP]
Makefile:24: toplevel.config: No such file or directory
find: /home/inerdsure/alsa/alsa-driver/alsa-kernel/: No such file or directory
find: /home/inerdsure/alsa/alsa-driver/alsa-kernel/: No such file or directory
find: /home/inerdsure/alsa/alsa-driver/alsa-kernel/: No such file or directory
make: *** No rule to make target `toplevel.config'.  Stop.
./cvscompile: line 42: aclocal: command not found
[/PHP]
and the last 9 lines:
[PHP]
./configure: line 9769: ALSA_TOPLEVEL_SELECT: command not found
./configure: line 9779: ALSA_TOPLEVEL_OUTPUT: command not found
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: error: cannot find input file: toplevel.config.in
[/PHP]
Lokks like this time I'm still missing:
[PHP]
Makefile:24: toplevel.config: No such file or directory
[/PHP]
and:
[PHP]
./configure: line 9769: ALSA_TOPLEVEL_SELECT: command not found
./configure: line 9779: ALSA_TOPLEVEL_OUTPUT: command not found

config.status: error: cannot find input file: toplevel.config.in
[/PHP]
What am I missing?  :confused:  Many thanks in advance.

---

### Post by gargameljura on 2006-03-05
Hi!

INerdSure, I think you should do the following: remove whole alsa source tree you have downloaded (rm -R alsa) and repeat the process but in step 6. also execute command "autoconf":

autoconf
./cvscompile --with-debug=full --with-cards=hda-intel
sudo make install

That should be it!

Enjoy the music :D

---

### Post by iNerdSure on 2006-03-05
[QUOTE=gargameljura]Hi!

INerdSure, I think you should do the following: remove whole alsa source tree you have downloaded (rm -R alsa) and repeat the process but in step 6. also execute command "autoconf":

autoconf
./cvscompile --with-debug=full --with-cards=hda-intel
sudo make install

That should be it!

Enjoy the music :D[/QUOTE]
Thanks. :)   Will try and see what results I get.

---

### Post by iNerdSure on 2006-03-05
Quite a surprise, indeed! An unpleasant one. The sound is completely gone!  :confused: Tried running Alsamixer, but encountered:
[PHP]
alsamixer: function snd_ctl_open failed for default: No such device
[/PHP]
And tried:
[PHP]
Application > Sound & Video > Volume Control
[/PHP]
and got:
[PHP]
No volume control elements and/or devices found.
[/PHP]
Now, it's back to the beginning when there is ABSOLUTE SILENCE :( 
Any suggestions, anyone?

---

### Post by er-ku on 2006-03-05
**iNerdSure:** The error that I see is:
```
./cvscompile: line 42: aclocal: command not found
```

try this:
```
sudo apt-get install automake
```
(note: it installs automake1.4 for me instead. That's OK).

Then repeat my steps. Sorry for these caveats, I usually forget that one needs some development files to do all this... I install and forget them... :) I've slightly edited my manual again. If you find any more missing packages, please tell me - I'll add them to the list.

One more thing. Previously, you've pasted your command to here, and it looked like this:
```
./configure --with-debug=full --with-cards=hda-i ntel
```

Where the hell does that space come from? Please make sure you're not adding unneeded characters to your commands. It's probably simpliest to just copy-paste them from the browser to the terminal.

**gargameljura:** I've removed the autoconf step from the instruction, as cvscompile scripts invokes it by itself.

---

### Post by iNerdSure on 2006-03-05
Hi Er-Ku, many thanks :D  for the quick response. I will try again and post the results.

---

### Post by iNerdSure on 2006-03-05
Hi Er-Ku, I think installing the "automake" solved the problem. Now I have SOUND!! Simply FANTASTIC. \\:D/  We've been trying various solutions for almost 5 months.

Anyway, the lspci -nvd 8086:2668:
[PHP]
1:~$ lspci -nvd 8086:2668
0000:00:1b.0 0403: 8086:2668 (rev 04)
        Subsystem: 1025:008f
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d000c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>
[/PHP]
Many, many thanks to you and all others who researched and contributed to solving this no sound problem.

---

### Post by rverrips on 2006-03-05
***RQ*** - You are [SIZE="4"]THE MAN![/SIZE]:KS 

I tried the instructions yesterday with no luck - As I've messed around a lot with my ubuntu setup and various hacks to alsa I figured best to start fresh.

needed ```
sudo apt-get install autoconf automake cvs gcc-3.4 libc6-dev
``` on a fresh install of Ubuntu Breezy 5.10 before anything else, and then followed the instructions (postcount 164) and resulted in total success:  Sound works great out of internal speakers (haven't tried with headphones, or CD-sound yet - Bell is not working, as expected)

My Laptop is an **Acer Aspire 1642 WLMi**

lspci -nvd 8086:2668 gives same output as you mom's, i.e. 
```
0000:00:1b.0: 0403: 8086:2668 (rev 04)
            Subsystem: 1025:008f
```

[SIZE="3"]Thanks again![/SIZE]

---

### Post by iNerdSure on 2006-03-05
Hi everyone, I've tried making calls on Skype. Sounds work fine on built-in speakers and mic. Also tested with plugged in headset, works great.

Tested with music CD and DVD. Works great as well. For a long while, I now know what I have been missing when the African drum beats.
> 
- Bell is not working, as expected

Not sure what "Bell" sounds are being referred to. But checked:
System > Preferences > Sound
and found "Sound Events" working, even though the "General" Tab shows no "Default Soundcard".

Many thanks, again, everyone. :)

---

### Post by er-ku on 2006-03-05
Everybody owes me a beer now, LOL. :twisted: I think, viridis will be the first one to repay his debt (he lives closest to me). :mrgreen:

I think I'll submit a patch to ALSA that will remove all Beep controls from the mixer (on the mailing list, I was told ALSA doesn't do beeps at all), and **maybe** will do the same to everything related to CD. We'll end up with Mic+Line+PCM+Master in the mixer after all. But I want to check a few things on my mom's lappy before that - I want to know if recording from "Capture 1" channel works. If it doesn't, I'll remove Capture 1 from the mixer too... ;)

Also, I'll probably try to load the module with "model=test" argument, and find out if there's ANY channel that influences CD playback volume in classic apps (those that actually tell the CD-drive to play the disk instead of reading raw data and interpreting it by themselves). On the other hand, there are a few reasons why this might be considered useless, so maybe i'll just remove the CD controls and forget it.

However, if someone is in mood, you can help me by trying it out yourselves and submitting the results here.

---

### Post by gargameljura on 2006-03-05
[QUOTE=er-ku]Everybody owes me a beer now, LOL. :twisted: [/QUOTE]

No problem next time you're in Slovenia just give me a shout :)

Tnx again!

---

### Post by phyrex on 2006-03-05
I have SOUND!...

I've been watching this thread since i bought my Acer two months ago, now finally a working solution! :)

I followed er-ku's howto and 10 minutes later Ubuntu made a sound for the first time.

My specs:
Acer Aspire 1642wlmi:

$ sudo lspci -nvd 8086:2668
```

0000:00:1b.0 0403: 8086:2668 (rev 04)
        Subsystem: 1025:008f
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d000c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] #10 [0091]

```

---

### Post by iNerdSure on 2006-03-06
Hi Er-Ku,  
> 
Everybody owes me a beer now, LOL.  I think, viridis will be the first one to repay his debt (he lives closest to me). 

It'll be a pleasure indeed. If you are travelling ten thousand kilometres over here any time in the future. :)

---

### Post by poter on 2006-03-06
**Fantastic advance.** Sound on internal speakers and external headphones, recording from internal mic and external mic and from line in. All the programs I use seem to work with audio.

The laptop is: Acer Travelmate 4062LMi
$ sudo lspci -nvd 8086:2668
0000:00:1b.0 0403: 8086:2668 (rev 04)
       Subsystem: 1025:008f
       Flags: bus master, fast devsel, latency 0, IRQ 177
       Memory at d000c000 (64-bit, non-prefetchable) [size=16K]
       Capabilities: [50] Power Management version 2
       Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
       Capabilities: [70] #10 [0091]

Not working: usb-audio
I tryed: ./cvscompile --with-debug=full --with-cards=hda-intel,usb-audio
but I get this errors when loading modules:
/alsa-driver/usb/usbaudio.c:1252: current rate 0 is different from the runtime rate 48000
/alsa-driver/usb/usbaudio.c:829: cannot submit datapipe for urb 5, err = -28

I need usb-audio for usb speakers and usb MIDI interface.

"Mic jack mode" works on all three options
"Line jack mode" works for Line in and Headphone out. The two Mic modes don't work. Line in not probed.

We don't need all those modes at all, but I say it for debuging (if needed). Now we are the right way.

er-ku, we are all in debt with you. Thanks so much.

---

### Post by earth_walker on 2006-03-06
I haven't read throught all the pages of this post, but in case anyone else is still having problems getting sound to work on an Acer laptop, here's my experience:

I have an Acer Aspire 1692 WLMI. This laptop freezes unless you boot breezy with an extra 'option'. Searching the forum, there is conflicting advice - many posts suggest booting with 'acpi=off'. However, this boots fine, but without wireless, sound or hotkeys.

Instead, boot it with the 'noapic' option. Sound, wireless, and many of the hotkeys will now work. This does not, however, fix the battery indicator, and the sleep function is a little wonky.

I hope this saves someone lots of aggro!

---

### Post by Sanglob on 2006-03-06
Er-Ku : Congratulations! I've followed your tutorial and in less than 10 minutes my computer was finally speaking! Thanks a lot, I am sure you made many people very happy, at least for me this is the greatest news of the day at least :)

However the DSDT apparentely is not working for my laptop, it is an ACER ASPIRE 1640, not the same as your mother's... 

poter: thanks for your help. I tried your first solution but I get compilation errors while trying to compile the downloaded dsdt, I tried to fix it following the instructions of [https://wiki.ubuntu.com/ACPIBattery](https://wiki.ubuntu.com/ACPIBattery) but after I manage to get a dsdt file that compiles without errors it makes the computer crash while booting :( The second approach is too difficult for a newby like me... Does anybody has a 1640 with ACPI working properly?? If somebody does, some clues will be appreciated...



Thanks to everybody in this forum, I will be running window$ if it wasn't for you, you have saved a soul! :)


$ sudo lspci -nvd 8086:2668
Password:
0000:00:1b.0 0403: 8086:2668 (rev 04)
        Subsystem: 1025:008f
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d000c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable -
        Capabilities: [70] #10 [0091]


[https://wiki.ubuntu.com/ACPIBattery](https://wiki.ubuntu.com/ACPIBattery)

---

### Post by s|k on 2006-03-07
[QUOTE=athem]I'm running Breezy on an Acer Travelmate 8104WLMi, with Intel HDA sound.  I struggled to get it working for a week.  ALSA was installed by default, but no sound.  Then I accidentally did this from the main panel menu:

Applications-->Sound & Video-->Volume Control

Then, in the Volume Control application menu I changed the device:

 File-->Change Device-->Realtek ALC880 (OSS Mixer)

and got sound for the first time.  I'm not sure why the ALSA device didn't work, but the Realtek one seems to work OK.  I'm curious what others' experience has been with this.

:D[/QUOTE]
This worked for me. :)

---

### Post by ffadmraven on 2006-03-07
Hey, just in case you are still trying to get your sound to work, I tried this link, and now my sound is working just fine.  Hope this helps some of the rest of you.

[http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True)

---

### Post by er-ku on 2006-03-07
Thanks to everyone who compliments me. ;) It's a pleasure to know people appreciate you.

**poter**: what about recording quality? Is it good enough? And does recording work from both Capture and Capture 1? I haven't tested that yet. Probably because I was too blind to see that "Recording Source" (or whatever the name) countrol is available right in the main interface (at least it is there in Ubuntu Dapper).

Also, what do you mean by saying "Line jack mode" doesn't work as mic? Did you try to plug an external microphone to it and found out it didn't work? 

Talking about those "jack mode" controls themselves - I left them intact mainly because Jonathan Woithe (who helped me a lot (or maybe it was actually me helping him), and who made up the "test" model; everyone of you owes him two beers/cups of tea, actually ;)) has recently added them to "Fujitsu" model in order for people to have more control over what their hardware does. Maybe someone would want to do four-way recording (i'm not sure what it means, but I guess it's two independent stereo streams), or maybe they would want to connect even more speakers to Line In/Mic ports. Who knows? :) Users not in a need for such functionality can simply hide those controls in their mixer app.

usb-audio. I never touched it. I guess you should wait for next RC or Release version of ALSA in order to fix it. You can also report your problem to ALSA bugtracker. 

**Sanglob**: uh, I didn't notice the model (even though i've heard a theory that Aspire is exactly the same as TravelMate). Did you try any DSDT's from [here]("http://acpi.sourceforge.net/dsdt/view.php?manufacturer=ACER")? I can see even four DSDT's of your family there. Btw, when I was working on DSDT, I at first didn't even manage to compile the Intel's DSDT compiler itself, so I guess I ended up with getting a compiler binary (or older sources) from somewhere... :)

**ffadmraven**: the original Realtek drivers didn't give sound in our case (I tested them). Plus, they're old. What is in official ALSA now, is actually a result of continued development efforts on these drivers.

---

### Post by poter on 2006-03-07
**er-ku**, recording quality is very good. I have recorded from mic and from line in from 44100 to 96000 Hz sample rates and it sounds great on my AKG K100 headphones.

Recording works **only from the first Capture** (left one). Kmix labels both the same: "Capture". I don't see "Capture1" anywhere. You need the second capture source if you want to record from both mic and line in at the same time. I could not get anything from CD Input source in the first Capture, but who records from CD audio input source when you can extract the digital signal directly from CD tracks?.

"Line jack mode" doesn't work as mic means just what you say. I pluged an external microphone in "Line in" jack and selected "Mic 50pc bias" and "Mic 80pc bias" in "Line jack mode" and only low level noise is recorded. But plugin an external line signal source to the line in jack with this configuration does work. The other hand, plugin an external line signal source to the mic jack and selecting "Line in" in "Mic jack mode" gets sound but with high distortion, even adjusting the Capture level to its lowest position. This means that any signal pluged to Line in jack never reaches the mic preamplifier and any signal pluged to Mic jack always reaches the mic preamplifier. So, what are these functions for?. In addition I can not appreciate any difference between "Line out" and "Headphone out" in "Line jack mode" when I plug the headphones in line in jack (this does not turn off internal speakers). The signal that reaches this jack is always amplified with the same level. But it is a very good feature that you can switch the line in jack function between input and output.

I will wait for next ALSA release for usb support.

Anyway we are now very very near from heaven. Only second capture needed. Thank you very much, again.

Some questions to Acer: Why this non-standard function of sound chip?, why this non-standard DSDT? I think all of you know the answers, so why don't we suggest Acer a litle change in laptop model name?: TravelMate=TroubleMate.

---

### Post by er-ku on 2006-03-07
Dear **poter**,
thank you for your quite extensive report. Recording is one thing I almost haven't tested at all. I'll try to test it once again though, when I have time, to confirm what you've found.

I guess you're right about the CD source. ;) It's probably unneeded.

On ALSA mailing list I was told headphones and line out modes differ a little, but it's hardly noticable in most cases (the difference is only effective when you plug in earbuds, or sth). I didn't test the difference too much aswell. For me, it looked the same too. But I was using an external amplifier and I was told to expect very little to no difference in my case.

I think USB audio is having a series of patches applied now, maybe that is the reason it doesn't work for you. I'm not reading all of the mails in alsa-devel, but I think I saw some patches related to usb-audio.

Talking about Acer: yeah, I was thinking about writing them a letter today with all my concerns. Starting with the fact that what they call "Bootable Linux" (Linpus Linux minimal edition, or so) is actually a disgrace, not a full-featured OS. I was thinking to suggest them use FreeDOS if they only want free command-prompt, or Ubuntu, if they want Linux. Furthermore, I wanted to write them about this ALSA story, and make them ashamed. Maybe I'll do that another day... Or maybe we could all do that together and send it as a collective letter...

---

### Post by ffadmraven on 2006-03-07
Hi, I understand that the original drivers don't work, according to the site that link goes to, it has the drivers for the updated 64bit architecture, so I thought they might help.  I'm running an Alienware Area-51 M7700 laptop, and it fixed mine, so I thought it might help some others, too.  If I'm wrong, sorry, just trying to help.

---

### Post by iNerdSure on 2006-03-08
Imho, a collective letter may be more effective. It's almost like a "class action", but short of a legal action. I suspect Acer used the Linpus marketing approach to sell their laptops to expert Linux users. And in turn get "free" testing and debugging bu expert users worldwide.

A few important features and funtionalities did not work "out-of-the box". Wireless LAN, bluetooth, sound and battery meter. There may be others that I am not aware of (yet?).

Anyway, I'm of the view that Acer should _not_ sell their laptops, simply loaded with Linpus, and "abandon" their customers to figure out how to get their laptops in working order. At the least, Acer must disclose the potential issues with different distros, lack of drivers etc. They can't just adopt an attitude of caveat emptor. :(

---

### Post by er-ku on 2006-03-08
The thing is that Linux on Acer is "Unsupported". I think they sell it with Linpus just because in some countries (like here, in Lithuania) if a customer buys a computer with a legally installed OS, they get some advantage (i.e., here they return part of the taxes collected from the customer). So a computer with Linpus is **technically** a computer with an OS. I don't mind that, except that I wish in that case they sold it with FreeDOS instead. There wouldn't be much difference, and this would even be better for Acer - they woudn't need a Linux partition on their preloaded drive.

Anyways, we'll see what we come up with. I think this should be a separate discussion in order not to clutter this topic.

---

### Post by iNerdSure on 2006-03-09
[QUOTE=er-ku]The thing is that Linux on Acer is "Unsupported". I think they sell it with Linpus just because in some countries (like here, in Lithuania) if a customer buys a computer with a legally installed OS, they get some advantage (i.e., here they return part of the taxes collected from the customer). So a computer with Linpus is **technically** a computer with an OS. I don't mind that, except that I wish in that case they sold it with FreeDOS instead. There wouldn't be much difference, and this would even be better for Acer - they woudn't need a Linux partition on their preloaded drive.

Anyways, we'll see what we come up with. I think this should be a separate discussion in order not to clutter this topic.[/QUOTE]
Ok. I will start a new thread. We need some "problem definition" or definition of the scope of issues. 

[http://www.ubuntuforums.org/showthread.php?p=806467#post806467]("http://www.ubuntuforums.org/showthread.php?p=806467#post806467")

I hope more users will post their experiences and findings and we can then raise a collective letter to Acer.

---

### Post by double_v on 2006-03-09
[QUOTE=er-ku]Everybody owes me a beer now, LOL. :twisted: I think, viridis will be the first one to repay his debt (he lives closest to me). :mrgreen:
[/QUOTE]
No problem :D

Just wanted to say thank you. I've got Acer TM 4061NLMI for several months now and today I found out it can produce a sound and battery is not allways empty when AC is offline ;) *Labai tau d&#279;kui, Rimai* ;)

Good luck
Vitalijus

---

### Post by er-ku on 2006-03-12
Hi **poter**,

I don't have an external microphone or headphones to test jack modes extensively now, so i'm asking you (or anyone else).

Would you please test the patch I've attached here with the latest CVS?

What concerns me is how recording and jack modes work. It sounds very strange for me that the preamplifier always works for Mic jack, and never works for Line In jack. Maybe you need to reboot the notebook in order for required changes to take effect or something? I'll show your post to Jonathan though, maybe he'll have an idea...

As I promised, I've removed all CD and Beep related controls/options from the mixer.

About capture: on my home computer with Dapper, GNOME's Sound Recorder has a drop-down menu to choose the capture source. On this computer though (Breezy) this control is not available. I'll leave both captures for now, maybe they DO really work...

---

### Post by poter on 2006-03-13
Ok, er-ku, I have applyed, compiled and installed the patch. I will probe it in depth and send the report tonight.

---

### Post by jam'ez on 2006-03-13
Hey everyone.
i cant seem to get my sound working at all.
I have a Packard Bell A8202 [http://www.packardbell.co.uk/products/live/on-the-go/notebooks/easynote-a/easynote-a8202/productsheet-pb30s00001-51.html]("http://www.packardbell.co.uk/products/live/on-the-go/notebooks/easynote-a/easynote-a8202/productsheet-pb30s00001-51.html")
It says an Intel ICH6 on searches on the laptop for devices etc even tho PB say Realtek.
I have it now on dapper but still no sound. alsa has the Intel ICH6 card selected and volume up.
the only sound i get is clicks when i mute or unmute the sound. THATS IT :(

ANY HELP?

THANKS ALOT!

---

### Post by er-ku on 2006-03-14
Hi, **jam'ez**,
PackardBell website says it's AC'97, not HDA, so it's an absolutely different problem. Try filing it on ALSA bugtracker: [https://bugtrack.alsa-project.org/alsa-bug/](https://bugtrack.alsa-project.org/alsa-bug/). Folks there should help you with it.

---

### Post by poter on 2006-03-14
Well, here we are:

**For [Headphone Jack Mode]**
->Mic 50 bias or Mic 80 bias: you can not select them at all. They apear in the drop down list but when you try to select one it changes automatically to "Line in" option.
->"Line in": it doesn't work. In fact it can't work since you haven't got a "Headphone" option in Input source.
->"Line out" or "Headphone out": work ok but without any difference on their output level (1 volt RMS).

**For [Line Jack Mode]**
->"Mic 50 bias" or "Mic 80 bias" or "Line in": work ok when you plug a line signal without any difference on their recording level. Plugging a mic here only records background noise.
->"Line out" and "Headphone out" work ok in stereo with just the same output level in both cases (1.2 volts).

**For [Mic Jack Mode]**
->"Mic 50 bias" or "Mic 80 bias" or "Line in": plugging a mic you record with first and second options just with the same level.With "Line in" you only record noise. Plugin a line signal you get just the same recording level in the three cases.
->"Line out" and "Headphone out" work ok but in mono (only outputs the mixed two stereo channels to left channel) with just the same output level in both cases (1.2 volts).

I followed this procedure for testing: I genereted a five minutes fixed tone of 440 Hz and maximun amplitud without distortion (0 dB), then saved it as wav and recorded to audio CD. Then I playback the CD with external device plugging a mic or a stereo cable to the computer according to each case and write down the recording level obtained. For output I used a voltimeter in 10 volts AC scale (the lowest one my tester arranges) atached to the corresponding jack and playing the same fixed tone (I got values over 1.0 - 1.2 volts RMS).

Beep output control has disappeared but I didn't know what it was for. I only know that it increased the background noise level when you turned it on.
CD input source has also dissapeared but probably it has no utility.
Second Input source does nothing. You only record silence if you select only the second Input source.

That is it.

---

### Post by er-ku on 2006-03-19
(Hi all, my reply notification is screwed up. Is anyone else having that problem too?)

**poter**,
> ->"Line in": it doesn't work. In fact it can't work since you haven't got a "Headphone" option in Input source.
oops, my bad. :)
Would you please find this in patch_realtek.c:
```

 static struct hda_input_mux alc260_acer_capture_source = {
	.num_items = 2,
 	.items = {
 		{ "Mic", 0x0 },
 		{ "Line", 0x2 },
 	},
 };

```

And replace it with this:
```

 static struct hda_input_mux alc260_acer_capture_source = {
	.num_items = 4,
 	.items = {
 		{ "Mic", 0x0 },
 		{ "Line", 0x2 },
		{ "Headphone (ADC1)", 0x5 },
		{ "Headphone (ADC2)", 0x6 },
 	},
 };

```

Then test whether recording from the Headphone jack works. "Headphone (ADC1)" option should only work with the first Capture control, and "Headphone (ADC2)" with only the second one.

---

### Post by poter on 2006-03-20
Hi, er-ku, I have tested these changes with no success. I plugged a line signal into Headphone jack and selected "Line in" in "Headphone jack mode". Then I tested different options for first and second "Input source" controls activating first Capture, second or both. There is no recording signal in any of the combinations: 
first capture with Headphone (ADC1),
first capture with Headphone (ADC2),
second capture with Headphone (ADC1) and
second capture with Headphone (ADC1).
¿does it work for you?

---

### Post by er-ku on 2006-03-21
**poter**, I haven't tried that actually. Thanks, I'll remove the headphone type switch and Headphone jack from the list o capture devices. I'll make it always act as an output. I guess there's no use to make it an input that can only be played back.

---

### Post by chibo on 2006-03-22
Hi all! Thanks for good advice, but it didn't work for me :( I followed the instructions but I can't get any sounds... It seems that it doesn't find the sound card at all.
lspci -nvd 8086:2668 gives
0000:00:1b.0 0403: 8086:2668 (rev 04)
        Subsystem: 1025:0067
I'm using Acer TravelMate 3004. I'd be grateful for any additional advice.

---

### Post by er-ku on 2006-03-23
Hi, **chibo**, 
would you please attach a copy of your /proc/asound/card0/codec#0 file to here? Just to make sure it is ALC260, not something else.

If it is ALC260, and you've followed my previous instructions on compiling and installing the drivers, please try passing a model argument to the relevant module, by adding a line:
```
options snd-hda-intel model=acer
``` to */etc/modprobe.d/snd_hda_intel.modprobe* (create a file if it doesn't exist), and rebooting your computer. If tuning the mixer still has no effect, change the model name to *test* and try tweaking the mixer then.

Please submit your detailed findings in any case. You can mail them to me privately if you want.

---

### Post by chibo on 2006-03-24
I'm not sure if I can post any detailed findings 'cause /proc/asound/card0/codec#0 doesn't exist. The one which is closest is /proc/asound/cards that has only line: --- no soundcards --- and that doesn't look too good... (And yes, I followed your instructions)

---

### Post by er-ku on 2006-03-24
**chibo**, if the situation is that serious, I suppose you should report a bug to alsa bugtracker: [https://bugtrack.alsa-project.org/](https://bugtrack.alsa-project.org/).

---

### Post by eudoxos on 2006-03-26
Hello,

please try the latest kerne 2.6.15-19, it has ALSA fix for acers backported from ALSA CVS. It works on my TravelMate 4060. If there are any troubles, post a follow-up / reopen the relevant bug in malone. There you find relevant links to ALSA bugtrack etc. 

[https://launchpad.net/distros/ubuntu/+source/alsa-driver/+bug/28443/+index](https://launchpad.net/distros/ubuntu/+source/alsa-driver/+bug/28443/+index)

Best regards,

Vaclav

---

### Post by er-ku on 2006-03-27
That's great news, **eudoxos**!

---

### Post by JLCarneiro on 2006-05-05
> **er-ku]Hi again,

now the sound instructions. This won't be so much like it should be in Ubuntu (generation of a .deb package), but nevermind.  said:**
> 
Hi, **er-ku**!

I don't use an Acer computer (it's a Toshiba) but, since it has the same chipset I think it could work.

At this moment (after a few unsuccessful atempts), my Volume Control does not show my soundcard, only shows "HDA Intel (alsa mixer)". I have Alsa 1.0.10 installed (through .deb packages). Can I still implement you tutorial?

If so, I'd like to know if there is already a .deb package to implement these steps... I searched a lot for an Alsa 1.0.11 .deb package but I couldn't manage to find it. Is there one? If not, could you confirm what steps should I make (since **INerdSure**) had some problems...

Thanks in advance,
JL

---

### Post by er-ku on 2006-05-05
Hi [b]JLCaneiro[b],
[QUOTE=JLCarneiro]I don't use an Acer computer (it's a Toshiba) but, since it has the same chipset I think it could work.[/QUOTE]

Chipset is not a problem. The problem is pinout (i.e. which jacks are connected to which pins of the chip). Acer settings may work for you, but they may just as well not.

> At this moment (after a few unsuccessful atempts), my Volume Control does not show my soundcard, only shows "HDA Intel (alsa mixer)". I have Alsa 1.0.10 installed (through .deb packages). Can I still implement you tutorial?

If so, I'd like to know if there is already a .deb package to implement these steps... I searched a lot for an Alsa 1.0.11 .deb package but I couldn't manage to find it. Is there one? If not, could you confirm what steps should I make (since **INerdSure**) had some problems...

I suggest that you try the Dapper LiveCD first. At least to see if your problem still exists in it. If it doesn't, you can choose between installing Dapper now, or waiting till June when it's released officially.

However, if in dapper there's still no sound for you, you'll have to debug further. First, you'll need to find out which chipset your Toshiba has (look in /proc/asound/card0/codec#0 for it), then act accordingly.

You may also try looking for info on your exact laptop model on the internet. Maybe somebody has already solved your problems. If they haven't, don't get upset - just contact ALSA guys (i.e. by filing a bugreport in their bugtracker).

---

### Post by JLCarneiro on 2006-05-06
[QUOTE=er-ku][...]
I suggest that you try the Dapper LiveCD first. At least to see if your problem still exists in it. If it doesn't, you can choose between installing Dapper now, or waiting till June when it's released officially.
[...][/QUOTE]
I ran a Live Dapper CD and it worked well, except for the sound... :( 

[QUOTE=er-ku][...]
However, if in dapper there's still no sound for you, you'll have to debug further. First, you'll need to find out which chipset your Toshiba has (look in /proc/asound/card0/codec#0 for it), then act accordingly.[/QUOTE]
This is the contents of my [COLOR="Blue"]/proc/asound/card0/codec#0[/COLOR]:
[PHP]Codec: Realtek ALC260
Address: 0
Vendor Id: 0x10ec0260
Subsystem Id: 0x2600000
Revision Id: 0x100400
Default PCM: rates 0x560, bits 0x0e, types 0x1
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  PCM: rates 0x560, bits 0x0e, types 0x1
Node 0x03 [Audio Output] wcaps 0x211: Stereo Digital
  PCM: rates 0x560, bits 0x1e, types 0x1
Node 0x04 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  Amp-In vals:  [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23]
  PCM: rates 0x160, bits 0x06, types 0x1
  Connection: 7
     0x12* 0x13 0x14 0x15 0x16 0x0f 0x10
Node 0x05 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  PCM: rates 0x160, bits 0x06, types 0x1
  Connection: 8
     0x12* 0x13 0x14 0x15 0x16 0x07 0x0f 0x10
Node 0x06 [Audio Input] wcaps 0x100391: Stereo Digital
  PCM: rates 0x160, bits 0x1e, types 0x1
  Connection: 1
     0x19
Node 0x07 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x23, nsteps=0x41, stepsize=0x03, mute=1
  Amp-In vals:  [0x41 0x41] [0x41 0x41] [0x41 0x41] [0x41 0x41] [0x41 0x41] [0xa3 0xa3] [0xa3 0xa3] [0xa3 0xa3]
  Connection: 8
     0x12 0x13 0x14 0x15 0x16 0x17 0x0f 0x10
Node 0x08 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x02 0x07
Node 0x09 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x07
Node 0x0a [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Amp-Out caps: ofs=0x23, nsteps=0x41, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00]
  Connection: 2
     0x02 0x07
Node 0x0b [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x08* 0x09
Node 0x0c [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x08* 0x09
Node 0x0d [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x08* 0x09
Node 0x0e [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x08* 0x09
Node 0x0f [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x081003f: IN OUT HP
  Pin Default 0x01014000: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
  Pin-ctls: 0x20: IN
  Connection: 1
     0x08
Node 0x10 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081003f: IN OUT HP
  Pin Default 0x02214000: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x09
Node 0x11 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x0810: OUT
  Pin Default 0x50171000: [N/A] Speaker at Int N/A
    Conn = Analog, Color = Black
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0a
Node 0x12 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08133f: IN OUT HP
  Pin Default 0x01a19000: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x24: IN
  Connection: 1
     0x0b
Node 0x13 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08133f: IN OUT HP
  Pin Default 0x02a19000: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x24: IN
  Connection: 1
     0x0c
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08133f: IN OUT HP
  Pin Default 0x01813000: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0d
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08133f: IN OUT HP
  Pin Default 0x99931000: [Fixed] Aux at Int ATAPI
    Conn = ATAPI, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0e
Node 0x16 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x99331000: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Black
  Pin-ctls: 0x00:
Node 0x17 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x0820: IN
  Pin Default 0x90f71000: [Fixed] Other at Int N/A
    Conn = Analog, Color = Black
  Pin-ctls: 0x00:
Node 0x18 [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x0814: OUT
  Pin Default 0x01446000: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Orange
  Pin-ctls: 0x00:
  Connection: 1
     0x03
Node 0x19 [Pin Complex] wcaps 0x400280: Mono Digital
  Pincap 0x0824: IN
  Pin Default 0x01c41000: [Jack] SPDIF In at Ext Rear
    Conn = RCA, Color = Black
  Pin-ctls: 0x00:
Node 0x1a [Vendor Defined Widget] wcaps 0xf00040: Mono
Node 0x1b [Volume Knob Widget] wcaps 0x600080: Mono
[/PHP]
[QUOTE=er-ku][...]
You may also try looking for info on your exact laptop model on the internet. Maybe somebody has already solved your problems. If they haven't, don't get upset - just contact ALSA guys (i.e. by filing a bugreport in their bugtracker).
[/QUOTE]
I tried this to no avail... :sad:
Toshiba site has nothing that works, I even installed a driver they offer but it forced me to reinstall Ubuntu 5.10 (it really messed up my installation). Besides, it seems everyone in the world prefer Acer... ;) 

What are my next steps?

---

### Post by er-ku on 2006-05-06
[QUOTE=JLCarneiro]I ran a Live Dapper CD and it worked well, except for the sound... :(
[/QUOTE]
uh!

> This is the contents of my [COLOR="Blue"]/proc/asound/card0/codec#0[/COLOR]:
[PHP]Codec: Realtek ALC260[/PHP]
At least we know it's really ALC260

> I tried this to no avail... :sad:
Toshiba site has nothing that works, I even installed a driver they offer but it forced me to reinstall Ubuntu 5.10 (it really messed up my installation). Besides, it seems everyone in the world prefer Acer... ;) 

What are my next steps?

Try the "test" model. I'm not sure if it's available in Dapper, but you may follow my instruction to compile your own ALSA drivers. just use "test" instead of "acer" where needed. With test model, you can tweak virtually any setting of your sound chipset. It should help you find the way to get the sound working.

Afterwards, don't forget to contact ALSA guys with detailed info on how to make the sound work for future owners of notebooks like yours. They'll tell you what info they need and how to get it. ;)

---

### Post by iNerdSure on 2006-05-17
Recent updates to Breezy 5.10 have created strange characteristics in the sound that is recorded through the laptop microphone or headset microphone. The sound is like a super low bass version of Darth Vader in Star Wars!

Sound when played from music CDs, or DVDs, sounds perfectly ok. Problem occurs only recording voice from laptop mic or headset mic, or during Skype calls, listeners thought they are listening to some deep voice "monster"!

Anyone encountered similar problems or have suggestions on how to rectify this monster sounding voice. Thank you.

---

### Post by Dirkomatic on 2006-05-26
I encountered this thread last week when I was getting no sound with Breezy on my Acer TravelMate 4062.  I just wanted to let everyone know that I upgraded to the Dapper release candidate and the sound appears to work fine.  I haven't done full testing (recording, external speakers) yet, but I was just glad to hear the bongos when I started up...

---

### Post by iNerdSure on 2006-05-26
Well, I wasn't prepared to try out Dapper Drake 6.06rc yet. Recompiled ALSA 1.0.11 drivers from downloading files from ALSA website. Now, the sound is back to normal. However, there's occasional or intermittent sound / recording device error when using Skype, and then switching to other apps that require sound.

Hopefully, Dapper Drake 6.06 final version will solve this problem. (Or, perhaps this is a problem with Skype?) Looking forward to receiving the disks soon.

---

### Post by er-ku on 2006-05-28
[QUOTE=iNerdSure]Well, I wasn't prepared to try out Dapper Drake 6.06rc yet. Recompiled ALSA 1.0.11 drivers from downloading files from ALSA website. Now, the sound is back to normal. However, there's occasional or intermittent sound / recording device error when using Skype, and then switching to other apps that require sound.

Hopefully, Dapper Drake 6.06 final version will solve this problem. (Or, perhaps this is a problem with Skype?) Looking forward to receiving the disks soon.[/QUOTE]

I hope you're using aoss wrapper for skype, aren't you? ;)

---

Damn! I don't get notifications from this thread. How come?

---

### Post by iNerdSure on 2006-05-28
[QUOTE=er-ku]I hope you're using aoss wrapper for skype, aren't you? ;)

---

Damn! I don't get notifications from this thread. How come?[/QUOTE]
I'm not sure. But when I checked Synaptic Package Manager, I found AOSS is already installed. Not sure if this is what you are referring to. Anyway, Skype is working ok now. Except when I try opening up other app that requires sound. 

In that situation, when I go back to Skype, I will encounter device error.

---

### Post by er-ku on 2006-05-29
[QUOTE=iNerdSure]I'm not sure. But when I checked Synaptic Package Manager, I found AOSS is already installed. Not sure if this is what you are referring to. Anyway, Skype is working ok now. Except when I try opening up other app that requires sound. 

In that situation, when I go back to Skype, I will encounter device error.[/QUOTE]

Skype does not natively support ALSA, so you must run it using an OSS wrapper for ALSA.

Quot Skype, run terminal, and run the following command in it:
```
aoss skype
```

If this solves your problem, you can add this command to gnome's autostart list: System > Preferences > Sessions > Startup programs (these strings are inexact, as always, as my gnome speaks Lithuanian).

---

### Post by sinecure on 2006-05-29
er-ku: I noticed that you seem to be leading the way with troubleshooting sound for these chipsets, and thought you might be able to help me.  According to my laptop's page[1], sound should 'just work' on my Acer TravelMate 8103, however, I can't seem to get it working.  I've tried everything you suggested in this thread, and a few others, with no luck.  The sticking point seems to be the file /proc/asound/cards - every time I install install Ubuntu (breezy or dapper) I have the following in that file:

```
--- no soundcards ---
```

This prevents me from getting anywhere with ALSA, OSS, etc.

I don't know where to go from here, and would appreciate any suggestions.  Also, I'll provide any information you'd need.

Any advice? ](*,) 

[1]: [https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelMate8103WLMi](https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelMate8103WLMi)

---

### Post by er-ku on 2006-05-29
[QUOTE=sinecure]er-ku: I noticed that you seem to be leading the way with troubleshooting sound for these chipsets, and thought you might be able to help me.  According to my laptop's page[1], sound should 'just work' on my Acer TravelMate 8103, however, I can't seem to get it working.  I've tried everything you suggested in this thread, and a few others, with no luck.  The sticking point seems to be the file /proc/asound/cards - every time I install install Ubuntu (breezy or dapper) I have the following in that file:

```
--- no soundcards ---
```

This prevents me from getting anywhere with ALSA, OSS, etc.
[/QUOTE]

This means that your soundcard is not detected at all.

Did you try contacting Tormod Volden[2]?

> 
I don't know where to go from here, and would appreciate any suggestions.  Also, I'll provide any information you'd need.

Any advice? ](*,) 

First: Try contacting Tormod.
Second: paste lspci -vvv here (and if I don't answer, drop me a mail to my mailbox, or send me a message via any of the IM services you can see me using).
Third: we'll see... ;)

[1]: [https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelMate8103WLMi](https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelMate8103WLMi)
[2]: [https://wiki.ubuntu.com/TormodVolden](https://wiki.ubuntu.com/TormodVolden)

---

### Post by sinecure on 2006-05-29
[QUOTE=er-ku]This means that your soundcard is not detected at all.[/QUOTE]

That's what I was afraid of... :-k 

[QUOTE=er-ku]Did you try contacting Tormod Volden[2]?

First: Try contacting Tormod.[/QUOTE]

Actually, I started to email him, but figured I'd try the forums first.  I'll send him an email tonight.

[QUOTE=er-ku]Second: paste lspci -vvv here (and if I don't answer, drop me a mail to my mailbox, or send me a message via any of the IM services you can see me using).[/QUOTE]

I'll do that if I can't get in touch with Tormod.  Even if I do, I'll keep the forum posted with any progress.

[QUOTE=er-ku]Third: we'll see... ;)[/QUOTE]

Isn't that always the case? ;) Thanks for the tips, I'll let you know what I find out.

---

### Post by iNerdSure on 2006-05-30
Er-ku,

Thanks for the tip. When I tried running aoss skype, I get this error mesage:

read error, res = -1 , handle = 33

I must be missing something. Any clue?

---

### Post by er-ku on 2006-05-30
[QUOTE=iNerdSure]Er-ku,

Thanks for the tip. When I tried running aoss skype, I get this error mesage:

read error, res = -1 , handle = 33

I must be missing something. Any clue?[/QUOTE]

No clues, indeed. For me it just works (under dapper, uh).

Go upgrade! ;) Dapper rocks!

---

### Post by iNerdSure on 2006-06-05
Looking forward to upgrading to Dapper. Waiting for the CDs to arrive in the mail. In the meantime, I'll just bear with the intermittent problem.

By the way, did you do a clean install of Dapper or an upgrade via the "alternate CD"?

---

### Post by JLCarneiro on 2006-06-05
When I installed it using the "alternate CD", I got a blank (black) screen. I waited for a couple hours with no response until I decided to hit "Enter". Then it finished the installation... :P
It worked fine, but I also installed using the Desktop CD. That is the one I'm using now.

---

### Post by er-ku on 2006-06-05
[QUOTE=iNerdSure]Looking forward to upgrading to Dapper. Waiting for the CDs to arrive in the mail. In the meantime, I'll just bear with the intermittent problem.

By the way, did you do a clean install of Dapper or an upgrade via the "alternate CD"?[/QUOTE]

I've been using dapper for the past few months, so I didn't go with either of your options.

What I did was edit /etc/apt/sources.list, replaced "breezy" with "dapper" everywhere in it, and ran:
```

$ sudo apt-get update
$ sudo apt-get -u dist-upgrade

```

Just look carefully at what it's removing. ;)

---

### Post by JLCarneiro on 2006-06-05
**er-ku**,

Any news, on that sound? :-\"

---

### Post by er-ku on 2006-06-05
[QUOTE=JLCarneiro]**er-ku**,

Any news, on that sound? :-\"[/QUOTE]

what sound? It should be working in Dapper, doesn't it? (bah! I haven't upgraded my mommas lappy yet)

---

### Post by JLCarneiro on 2006-06-05
:D
First, laptop's sound (Toshiba IS1421) HDA Intel.
Second, it still does NOT play any sound... :(

---

### Post by er-ku on 2006-06-05
[QUOTE=JLCarneiro]:D
First, laptop's sound (Toshiba IS1421) HDA Intel.
Second, it still does NOT play any sound... :([/QUOTE]
ah, right, Toshiba... :rolleyes: 

Did you try the test model like I told you in my comment #213 (and described it in detail previously)? :-k

---

### Post by iNerdSure on 2006-06-10
[QUOTE=er-ku]I've been using dapper for the past few months, so I didn't go with either of your options.

What I did was edit /etc/apt/sources.list, replaced "breezy" with "dapper" everywhere in it, and ran:
```

$ sudo apt-get update
$ sudo apt-get -u dist-upgrade

```

Just look carefully at what it's removing. ;)[/QUOTE]
I tried and ended up with some disastrous results! :mad: Now I when I power up, I get no GUI login and the text still shows Breezy. Tried re-config Xserver setttings but still can't get GUI login in screen to start. 

Anyone has suggestions on how to go backwards to Breezy to recover before trying upgrade again?

---

### Post by er-ku on 2006-06-10
[QUOTE=iNerdSure]I tried and ended up with some disastrous results! :mad: Now I when I power up, I get no GUI login and the text still shows Breezy. Tried re-config Xserver setttings but still can't get GUI login in screen to start. 

Anyone has suggestions on how to go backwards to Breezy to recover before trying upgrade again?[/QUOTE]

Oops! :-k 

But you don't need that.

Look at /var/log/Xorg.0.log (or any newer file /var/log/Xorg.*.log). If the GUI tries to start up and then fails,  you'll find lines beginning with (EE) in that file. Paste them here if they give you no clue about how to fix them.

You may also try to _apt-get install ubuntu-desktop_, or check if there are no packages that still need upgrading.

---

### Post by iNerdSure on 2006-06-10
[QUOTE=er-ku]Oops! :-k 

But you don't need that.

Look at /var/log/Xorg.0.log (or any newer file /var/log/Xorg.*.log). If the GUI tries to start up and then fails,  you'll find lines beginning with (EE) in that file. Paste them here if they give you no clue about how to fix them.

You may also try to _apt-get install ubuntu-desktop_, or check if there are no packages that still need upgrading.[/QUOTE]
The Xorg.0.log file contains a long list of text. I'm not able to "copy and paste" as I have no GUI login, only access to terminal commands.

Also tried apt-get install ubuntu-desktop. Got results showing package is not available. So, now it seems that I'm in quite a mess. Unable to access my data via GUI, only terminal commands. :(

---

### Post by er-ku on 2006-06-10
[QUOTE=iNerdSure]The Xorg.0.log file contains a long list of text. I'm not able to "copy and paste" as I have no GUI login, only access to terminal commands.[/QUOTE]

Ah, right... Can you attach it to your message then?

> Also tried apt-get install ubuntu-desktop. Got results showing package is not available. So, now it seems that I'm in quite a mess. Unable to access my data via GUI, only terminal commands. :(

bah! I suspect you messed up your /etc/apt/sources.list file. Could you check it for typing errors and if you find none, attach it to your message too?

---

### Post by iNerdSure on 2006-06-10
[QUOTE=er-ku]Ah, right... Can you attach it to your message then?



bah! I suspect you messed up your /etc/apt/sources.list file. Could you check it for typing errors and if you find none, attach it to your message too?[/QUOTE]
Don't know how to, in a Terminal screen without any GUI, get or save either the Xorg.0.log file or sources.list and transfer to another PC to post in this forum. 

Anyway, when I run apt-get update, there were quite a number of errors. So, apart from typing every text I see on the "pure" terminal screen, is there any other alternative of communicating the errors? :confused:

---

### Post by er-ku on 2006-06-11
[QUOTE=iNerdSure]Don't know how to, in a Terminal screen without any GUI, get or save either the Xorg.0.log file or sources.list and transfer to another PC to post in this forum. 

Anyway, when I run apt-get update, there were quite a number of errors. So, apart from typing every text I see on the "pure" terminal screen, is there any other alternative of communicating the errors? :confused:[/QUOTE]

OK, here's a quick guide for you. Type everything exactly as you see it here in that broken PC:

First, you login (enter your password in the console).
Then, you become root:
```
$ sudo -s
```
Enter your password when asked. The prompt should then say "root" instead of your username (and the "$" sign will change to the "#" sign). ;)

Now, execute the following:
```
# cd /etc/apt
# mv sources.list sources.list.broken
# wget http://tinyurl.com/p6bg4
```
The last command will retrieve you a fresh sources.list I made for you. But you'll still have the backup of your broken file, so that you can fix and re-use it after you have your GUI again.

Now it's just as before:
```
# apt-get update
# apt-get dist-upgrade
# apt-get install ubuntu-desktop
```

and then, if the GUI still doesn't start, run:
```
/etc/init.d/gdm restart
```

Let me know how it goes.
bye!

---

### Post by iNerdSure on 2006-06-11
Many thanks, Er-Ku. Running the recommended solution right now. It's taking quite a while.

Will let you know the result when completed.

---

### Post by iNerdSure on 2006-06-12
Hi Er-Ku, many thanks for the solution. It works great. I managed to get upgraded to Dapper 6.06 and got back the GUI login screen. However, I lost the wide-screen and high res display. And sound is lost too.

Anyway, it's enough for me to run backups and start installing Dapper into a fresh hard disk. 

Will post results later when my PCs work out ok for you.

---

### Post by iNerdSure on 2006-06-14
Hi Er-Ku, fresh installation of Dapper 6.06 went very well. I like the new look and features.
A few missing features:
o   Wide screen display is not working
o   LED for wireless ethernet not working even though network is working.
Any suggestions on how to get these two working on our Acer laptop model?

---

### Post by JLCarneiro on 2006-06-14
About Widescreen resolution, I suggest 915resolution (it worked on my Toshiba).

What about the sound? I'm already using 6.06 and still have no sound. :(

---

### Post by er-ku on 2006-06-14
[QUOTE=iNerdSure]Hi Er-Ku, fresh installation of Dapper 6.06 went very well. I like the new look and features.
A few missing features:
o   Wide screen display is not working
o   LED for wireless ethernet not working even though network is working.
Any suggestions on how to get these two working on our Acer laptop model?[/QUOTE]

Widescreen: try searching the forums. You should find the solutions. The package is called 915resolution, i think. ;)

LED: did you follow the steps from [here](http://ubuntuforums.org/showpost.php?p=545771&postcount=26)?

---

### Post by er-ku on 2006-06-14
[QUOTE=JLCarneiro]What about the sound? I'm already using 6.06 and still have no sound. :([/QUOTE]

Nobody's working on it, if you're only **asking** and only **here**.

Do you expect me to buy a Toshiba just to help you, or what? I've asked you the question about "test" model a few times. If you're not answering, i'm not helping. [-X

---

### Post by JLCarneiro on 2006-06-14
[QUOTE=er-ku]Nobody's working on it, if you're only **asking** and only **here**.[/QUOTE]
Sorry. I asked here because some of you had success with notebooks similar to ours. I mean, similar chipset, since the brand (Acer) is different... :confused:

[QUOTE=er-ku]Do you expect me to buy a Toshiba just to help you, or what?[/QUOTE]
Of course not! Sorry if it seemed like this. I asked you because I followed this whole thread and you seem to be the person with best knowledge of this problem (e.g. [here](http://ubuntuforums.org/showpost.php?p=773803&postcount=159) and [here](http://ubuntuforums.org/showpost.php?p=794772&postcount=179)).

[QUOTE=er-ku]I've asked you the question about "test" model a few times. If you're not answering, i'm not helping. [-X[/QUOTE]
That's true. I didn't answer. :oops:
But a friend of mine (he also owns a Toshiba like mine) did test the "test" model and it did not work. :(
*Although if he pumps the sound to the maximum he can _barely_ hear something on the headphones...* :-k

---

### Post by JLCarneiro on 2006-06-15
I found what appears to be Alsa 1.0.11 .deb packages:
[list][*][Musix](https://lists.ourproject.org/pipermail/musix-usuarios/2006-May/000262.html) [1]
[*][Debian packages](http://packages.debian.org/testing/sound/alsa-base) [2][/list]

But I also found what seems to be problems:
[list][*][Warning](http://www.cs.vassar.edu/~priestdo/emacspeak/msg00418.html)  [3][/list]

If I read correctly, **iNerdSure** used Alsa 1.0.11 to _recover_ his sound, but he had sound working correctly first.

Has anyone had success with Alsa 1.0.11 to fix HDA-Intel sound problem?
_____________
[1]: [https://lists.ourproject.org/pipermail/musix-usuarios/2006-May/000262.html](https://lists.ourproject.org/pipermail/musix-usuarios/2006-May/000262.html)
[2]: [http://packages.debian.org/testing/sound/alsa-base](http://packages.debian.org/testing/sound/alsa-base)
[3]: [http://www.cs.vassar.edu/~priestdo/emacspeak/msg00418.html](http://www.cs.vassar.edu/~priestdo/emacspeak/msg00418.html)

---

### Post by er-ku on 2006-06-15
> **JLCarneiro]Has anyone had success with Alsa 1.0.11 to fix HDA-Intel sound problem?
[/QUOTE]

OK, once again:  this is not a "HDA-Intel sound problem". It's a problem with unknown pinout. This varies between models, hance, having sound with HDA-Intel on an Acer does not mean at all you'll have sound on the Toshiba just because chipset is the same.

> I asked you because I followed this whole thread and you seem to be the person with best knowledge of this problem (e.g. [here](http://ubuntuforums.org/showpost.php?p=773803&postcount=159) and [here](http://ubuntuforums.org/showpost.php?p=794772&postcount=179)).

That wasn't knowledge indeed, but rather just hacking (in the sense that you try something and see if it works or not). However, I cannot do that remotely (compile and install alsa and figure out WHEN the sound actually works and which mixer control influences what). You must understand this.

I could help YOU do that, though.  said:**
> But a friend of mine (he also owns a Toshiba like mine) did test the "test" model and it did not work. :(
*Although if he pumps the sound to the maximum he can _barely_ hear something on the headphones...* :-k

Actually, this makes a lot of sense to me. The "test" model has only appeared in version 1.0.11 of ALSA. Ubuntu, so far, only has 1.0.10. And the fix, that is included into the Ubuntu kernel, most probably only adds "acer" model, not "test". BTW, there's a way to see if passing the parameter actually works or not. You should have asked me about that. :P

However, Debian already has ALSA 1.0.11 in their "testing" and "unstable" repositories. Hence, it should not be hard to package it for dapper too. I'll probably try that today (warning: that's not a promise! :P). With 1.0.11, you **should** get the "test" model and be able to test it/find out which control affects which channel. For the time being, this may be quite enough.
After you test things, you could have "toshiba" model included in upstream ALSA and/or in Ubuntu.

---

### Post by iNerdSure on 2006-06-15
> **er-ku]Widescreen: try searching the forums. You should find the solutions. The package is called 915resolution, i think.  said:**
> here[/url]?
Many thanks, Er-Ku. I installed the 915resolution, re-booted and widescreen 1280 x 800 resolution is now available. :D 

As for the wireless network, I followed your solution, and it's now back working just fine. 

You have been fantastic!  :KS  Many thanks again

---

### Post by er-ku on 2006-06-15
**JLCarneiro:** let's move your Toshiba discussion to [another thread here](http://ubuntuforums.org/showthread.php?t=197224)

---

### Post by lodp on 2006-06-15
hi there,

i'm running kubuntu dapper on a new acer aspire 1652ZWlmi (HDA Intel Realtek ALC883), and i haven't got any sound. 

i followed the instructions on page 17 of this thread - compiled and installed the newest CVS of alsa, but it still isn't working. nothing on the internal speakers or the headphone jack, only the int. microphone and microphone jack *seem* to get some input (i'll have to verify this).

here's what "lspci -nvd 8086:2668" turns up:

```

0000:00:1b.0 0403: 8086:2668 (rev 04)
        Subsystem: 1025:009e
```

I tried to put the line ```
options snd-hda-intel model=acer
``` into /etc/modprobe.d/snd-hda-intel.modprobe, but that didn't make any difference. I also triple- and quadruple-checked whether there was anything wrong with the alsamixer settings.

just some quick additional remarks (may be irrelevant): 

- i had a deb package of alsa-base 11-2 installed before i compiled the CVS. should i have de-installed that before?

- when going through the steps on page 17, somebody suggested executing "autoconf" before the following step:```
./cvscompile --with-debug=full --with-cards=hda-intel
sudo make install
``` , so i did that.


thanks for your time!

---

### Post by er-ku on 2006-06-16
[QUOTE=lodp]hi there,

i'm running kubuntu dapper on a new acer aspire 1652ZWlmi (HDA Intel Realtek ALC883), and i haven't got any sound.
[/QUOTE]

Everything that relates to sound in this thread, only applies to Acer notebooks with ALC260. ALC883 is a different codec, and it has to be solved separately.

I suggest that you file a bug in ALSA bugtracker and describe your problem there. You may also explicitly suggest them to add "test" model for ALC883, if it's not yet present. Be prepared for a lot of compiling/installing etc. That's just what I overwent with ALC260 before.

Good luck!

---

### Post by lodp on 2006-06-17
> Everything that relates to sound in this thread, only applies to Acer notebooks with ALC260

oh damnit, i didn't realize that.
> 
ALC883 is a different codec, and it has to be solved separately.

the alsa-project [changelog]("http://www.alsa-project.org/changes/v1-0-10--v1-0-11rc1.txt") (1.0.10 - 1.0.11RC1) actually says that they added support for ALC883.

well, i guess i'll file a bug then. never done that before - any guidance? what do they need to know except the things you asked from people who tested the alc260 patch?

---

### Post by lodp on 2006-06-17
i  just searched the alsa bugtracker for "alc883" - turned up only 2 issues.

anyway, i saw that the guys there posted the results of "cat /proc/asound/version" so i tried that for myself. this is what turns up:

```

Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21                 2005 UTC).

```

wtf? i thought i installed the newest CVS! are there inconsistencies in the sourceforge CVS-repositories (i've experienced such with other projects recently)? or did i just screw up compiling and installing the driver?

anyway, i'll have a try now and compile/instal the 1.0.11 release.

EDIT: i tried to install the 1.0.11 release, but "cat /proc/asound/version" still says that 1.0.10rc3 is installed. i must have done something wrong, please somebody point out to me what it is - i'm not so much into this whole compiling, installing business yet..

what i did was:

 - download and unpack alsa 1.0.11
 - run the following:


```
./configure --with-debug=full --with-cards=hda-intel
make
sudo make install
```

c-compiler, kernel headers and such are installed, i got no error messages.

then i ran alsaconf. the alsa installations instructions talk about editing /etc/conf.modules or /etc/modules.conf, neither of which exist on my setup.. there's only a /etc/modules file, but even after running alsaconf there's nothing in there pertaining to the sound card.

the next thing i did, as suggested by the install docs, was

```
 sudo modprobe snd-hda-intel
```

then i restarted. still no sound, and still "cat /proc/asound/version" as well as KDEinfo tell me i've got 10.0.10rc3 running. where am i wrong?

---

### Post by er-ku on 2006-06-18
[QUOTE=lodp]well, i guess i'll file a bug then. never done that before - any guidance? what do they need to know except the things you asked from people who tested the alc260 patch?[/QUOTE]

They'll tell you.

> ```

Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21                 2005 UTC).

```

wtf? i thought i installed the newest CVS! are there inconsistencies in the sourceforge CVS-repositories (i've experienced such with other projects recently)? or did i just screw up compiling and installing the driver?


I guess you did something improperly, that's all. Or maybe you just installed the modules for old kernel, or so. It's hard to tell remotely.

> EDIT: i tried to install the 1.0.11 release, but "cat /proc/asound/version" still says that 1.0.10rc3 is installed. i must have done something wrong, please somebody point out to me what it is - i'm not so much into this whole compiling, installing business yet..

what i did was:

 - download and unpack alsa 1.0.11
 - run the following:


ALSA comprises ALSA kernel drivers, ALSA tools and ALSA libraries. Which ones did you compile?

> 
```
./configure --with-debug=full --with-cards=hda-intel
make
sudo make install
```

c-compiler, kernel headers and such are installed, i got no error messages.

then i ran alsaconf. the alsa installations instructions talk about editing /etc/conf.modules or /etc/modules.conf, neither of which exist on my setup.. there's only a /etc/modules file, but even after running alsaconf there's nothing in there pertaining to the sound card.

the next thing i did, as suggested by the install docs, was

```
 sudo modprobe snd-hda-intel
```

then i restarted. still no sound, and still "cat /proc/asound/version" as well as KDEinfo tell me i've got 10.0.10rc3 running. where am i wrong?

Dunno. Something is appearantly going wrong way there.

I'm still going to try to make a 1.0.11 package for Ubuntu Dapper, if it doesn't arrive there before me. Actually, I tried that on Thursday, but it failed to compile for some weird reason, and I was too tired and it was late enough for me to go to sleep. I may find some time to try again though.

---

### Post by lodp on 2006-06-20
> ALSA comprises ALSA kernel drivers, ALSA tools and ALSA libraries. Which ones did you compile?

The drivers. Should i have compiled the other things as well?

Anyway, I tried again and re-installed the drivers, pretty much like I did last time, only that I ran the snddevices script this time (didn't think that was necessary last time). This time it worked, "cat /proc/asound/version" says ALSA 1.0.11 now.

Still no sound though. I'm not comfortable filing a bug yet - is there any way of determining 100% sure that the drivers are installed correctly?

what I did was:

./configure --with-debug=full --with-cards=hda-intel
make
make install
./snddevices
sudo modprobe snd-hda-intel

I didn't find the /etc/modules.conf or /etc/conf.modules file, which is supposed to be edited (at least the ALSA-driver installation instructions say so) - does that matter?

> 
'm still going to try to make a 1.0.11 package for Ubuntu Dapper

That would be wonderful! I guess I'm not the only person struggling to get this thing installed..

---

### Post by liviucen on 2006-06-30
Hello.

I have a problem, it is not a linux problem but it is a little bit like you's.

I have an Acer Aspire 1642 ZWLMi an i made un update to BIOS from 1A13 to 1A20 (3A06 - from [www.acer.com)](www.acer.com)).

After the update the sound is not working !!! with old BIOS version even if i was in BIOS utility setup, if i had pressed a wrong key , let's say "F2" a bip sound would be hear in the speakers, with the new vbersion, in the same condition, the "bip" sound is mising. I played a game in DOS, the game's sound des'n hear. I tryed win xp media center, win xp home ed. The interesting thing is that in windows, the sound card has installed drivers, it si found be windows, the drivers, are working (that's what windows said), the sliders from the mixer are movind with mouse, but still no sound, not in the speakers, not in the head phones (if pluged in), the laptop, doesn't receive analogic signal from internal mic, or external, neither lin in. The sound is deth,  whatever the OS, windows, DOS, or BIOS setup.

Anotrhe interesting thing is that after the falsh, after reboot, when windows started, it reinstaled some drivers, from video card, usb, sound, i belive it just changed some addresses, becouse, the drivers are the same like before update.

I made a BIOS update becouse in the older version my video memory was set to 64 MB and grayed - in the new version i can choose from 64/128 or max (192 for a 512 sodiMM))

I canot downgrade to previos bios version becouse the dysplay resolution will become 1024*768 insted of 1280*800 (image moved in the uper rleft cornet - even the screen from BIOS setup utility.

PLEASE TELL ME if u have any ideea what can i do, or at list i please U (thouse who have the same laptop) to make a back up of your BIOS files and please send it to me, so i can try it, maibe an older version will work.

(please don't give me answers like: unmute, or unplug headphones becouse  :) it is not the case :) (with the same conditions, with old BIOS ver sound works fine, with new, dowsn't)

OR
PLEASE MAKE A BACK UP  of you're BIOS , you can do it without falsh with "WINPHLAS" founded here: [http://support.acer-euro.com/drivers/ftp/ftp.html](http://support.acer-euro.com/drivers/ftp/ftp.html) (any zip. - 3A06 is the one flashed by me)

Please send it to me at: [email]liviucen@gmail.com[/email] 

Thank you.

PS: is here someone extremly good brilinat expert who can combine the two BIOS version, and make one good for me? (the sound part from firs, and the rest from the new version) . 10x ;)

---

### Post by er-ku on 2006-06-30
hi liviucen,

I suggest that you:
1) ensure you have downloaded the right bios image for YOUR laptop model, and if you have, and the sound still ain't working;
2) check the BIOS, maybe, sound can now be muted in it, and if the sound still doesn't work;
3) contact Acer or your local reseller/representative.

bye,

---

### Post by liviucen on 2006-06-30
Thank you for respons

but the good news is: IT WORKS !!!
the bios version downloadet was from acer.com, and it was the good version, but: they mixt them up, becouse may lapt has a "z" in its name, and i searched on other ftp from acer, somwere in US i think, and there it was another bios file for the same laptop... i put that version and now its ok

about conacting acer support, i did, and after a week , and after i sent them 5 mails, they respond finaly, and told me to download  latest drivers, although i told them that i allready puted last drivers from the link they provided...

eny way the good news for me is that is working..

see U

---

### Post by j_riley on 2006-08-03
I have a Acer TravelMate 2420, and my volume control has dissapeared and im not getting sound.

I have to search for volume control and when i do find it i get this message

"There are no active mixer devices available, to install mixer devices go to control panel,click printers and hardware and add hardware"

Im on Windows XP and haven't changed the laptop at all (original soundcard etc)

Also since ive had this problem music isn't playing through I-Tunes.

I noticed this happen after i installed Counter Strike Anthology the other day.

Any help would be appreciated!

---

### Post by er-ku on 2006-08-04
> **j_riley said:**
> I have a Acer TravelMate 2420, and my volume control has dissapeared and im not getting sound.

I have to search for volume control and when i do find it i get this message

"There are no active mixer devices available, to install mixer devices go to control panel,click printers and hardware and add hardware"

Im on Windows XP and haven't changed the laptop at all (original soundcard etc)

Also since ive had this problem music isn't playing through I-Tunes.

I noticed this happen after i installed Counter Strike Anthology the other day.

Any help would be appreciated!
This is not a Windows support forum, but whatever...

Try this:[LIST]
[*] Right-click "My Computer"
[*] Select "Manage" 
[*] When the management interface pops up, go to the hardware section and REMOVE all the devices that are marked with a "!" or similar icon. Then reboot your computer.[/LIST]

Once again, this isn't a windows support forum, so please don't post your questions with Windows issues here anymore. Thanks.

---

### Post by lodp on 2006-08-05
so you guys solved all the problems with the ALC260 chip -- is that right?

up till now i was pretty sure i was using the ALC883 chip, but it turns out it might be ill-detected. somebody with the same machine (who also happened to think he had the ALC883 chip) said that acer told him he was actually running the ALC260 chip.

i tried the model=acer option when loading the module, but it didn't change anything.

how do i find out exactly what chip is in there?

all i got now is the output of > cat /proc/asound/card0/codec#0 which says ALC883, and alsamixer, which says the same..

i sent a request to acer, but they're dragging their feet..

---

### Post by er-ku on 2006-08-05
> **lodp said:**
> how do i find out exactly what chip is in there?

Dunno. Ask that in an ALSA mailing list.

---

### Post by lodp on 2006-08-06
and the ALC260 chip is now fully supported? can you confirm that?

---

### Post by er-ku on 2006-08-06
> **lodp said:**
> and the ALC260 chip is now fully supported? can you confirm that?

As a chipset, yes. However, whether you have sound, depends on the hardware configuration of your notebook.

I've just checked - your subsystem ID (1025:009e) is different than that I had been working with (1025:008f). This may mean a different codec, or a different configuration of the same codec, I can't say anything for sure.

Btw, you can check it in windows. Run a dxdiag command, and look for something like this under sound devices:
>             Description: Realtek HD Audio output
            Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0260&SUBSYS_1025160D&REV_1004
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: RtkHDAud.sys
         Driver Version: 5.10.0000.5148 (English)
      Driver Attributes: Final Retail

As you can see, the Hardware ID line says VEN_10EC&DEV_0260. Wonder what it says in your case?

If you still don't have ALSA 1.0.11 installed, you may try following my [instructions on making a nice .deb](http://ubuntuforums.org/showthread.php?p=1339688#post1339688) file.

If nothing helps, I suggest that you subscribe to alsa-user, or maybe even alsa-devel [mailing lists](http://www.alsa-project.org/mailing-lists.php) and seek the solution together with the developers.

---

### Post by Petey on 2006-08-08
Hey

Today i turned on my acer travelmate 4060, running windows xp
never had any major problems before today, and now i have no sounds and no battery icons, i am quite a novice so would someone be able to give me step by step instructions from the begining!! thanks alot

Pete ! :D

---

### Post by er-ku on 2006-08-08
> **Petey said:**
> Hey

Today i turned on my acer travelmate 4060, running windows xp
never had any major problems before today, and now i have no sounds and no battery icons, i am quite a novice so would someone be able to give me step by step instructions from the begining!! thanks alot

Pete ! :D

You should install Ubuntu Dapper on it. Dapper already supports sound on this notebook.

As for the battery indicator, please take a look [here](http://ubuntuforums.org/showthread.php?p=604504#post604504).

---

### Post by Petey on 2006-08-08
thanks alot but what does that do, installing a new operating system? will that scrap windows xp??

---

### Post by er-ku on 2006-08-08
> **Petey said:**
> thanks alot but what does that do, installing a new operating system? will that scrap windows xp??
depends on your choices.

Anyhow, I thought you had this problem with Linux, not with windows. If you have it with Windows, take a look a few posts above. If that doesn't help, contact your support line. This message board is for Linux, not Windows users.

---

### Post by Petey on 2006-08-08
oh sorry to bother you then! 
thanks for you time

---

### Post by er-ku on 2006-08-08
No prob.

BTW, "Few posts above" means [here](http://ubuntuforums.org/showthread.php?p=1339369#post1339369).

---

### Post by Stan83 on 2006-08-08
> **lodp said:**
> 
up till now i was pretty sure i was using the ALC883 chip, but it turns out it might be ill-detected. somebody with the same machine (who also happened to think he had the ALC883 chip) said that acer told him he was actually running the ALC260 chip.


Hi LODP,
I am not sure if you write about me using the same machine.
I have an Acer, but it is TM4072, not Acer 1652 Z (that what you wrote here: [http://www.ubuntuforums.org/showthread.php?t=202555](http://www.ubuntuforums.org/showthread.php?t=202555) ), just to avoid confusion :)
However lspci gives the same results (as for sound), as you have posted.

So it might not be the case that your chip is ill-detected, but still it might :)
Please tell us what ACER support has answered you, maybe they screw up some more of the machines as well :D

---

### Post by lodp on 2006-08-08
> **er-ku said:**
> 
Btw, you can check it in windows. Run a dxdiag command, and look for something like this under sound devices:

thanks for the tip -- i can't post the full line here, but the part that matters is: DEV_0883 -- so windows says ALC883 as well.

anyway, i'm a little confused about the response that i got from acer. they say (my translation):

> there's a realtek audio chip in your laptop. the chipset has the following exact designation: Conexant 20468-31

is that just another denomination for some ALC??? chip?

> **er-ku said:**
> If you still don't have ALSA 1.0.11 installed, you may try following my [instructions on making a nice .deb](http://ubuntuforums.org/showthread.php?p=1339688#post1339688) file.

i compiled the hg version. however, alsa-lib failed to compile, the error i got is the following:
[QUOTE]
libtool: link: `cards.lo' is not a valid libtool object
make[2]: *** [libcontrol.la] Error 1
make[2]: Leaving directory `/home/martin/Drivers/alsa-hg/alsa-lib/src/control'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/martin/Drivers/alsa-hg/alsa-lib/src'
make: *** [all-recursive] Error 1

i probably better post this to the alsa-user mailing list.

> If nothing helps, I suggest that you subscribe to alsa-user, or maybe even alsa-devel [mailing lists](http://www.alsa-project.org/mailing-lists.php) and seek the solution together with the developers.

thanks, i already registered there, and i also filed a detailed bugreport at the alsa-project. i hope for a quick resolution to the issue.

> **Stan83 said:**
> Hi LODP,
I am not sure if you write about me using the same machine.

yeah, i was writing about you. didn't realize it wasn't the exact same machine. we'll probably stay in touch for a while ;)

---

### Post by er-ku on 2006-08-08
> **lodp said:**
> [QUOTE=er-ku;1345374]
Btw, you can check it in windows. Run a dxdiag command, and look for something like this under sound devices:
thanks for the tip -- i can't post the full line here, but the part that matters is: DEV_0883 -- so windows says ALC883 as well.
[/QUOTE]
Then it is indeed ALC883.
> anyway, i'm a little confused about the response that i got from acer. they say (my translation):
[QUOTE]there's a realtek audio chip in your laptop. the chipset has the following exact designation: Conexant 20468-31
is that just another denomination for some ALC??? chip?[/QUOTE]
Well, how should I know for sure? You can google for that. :) From googling, it doesn't seem so...
> [QUOTE]If you still don't have ALSA 1.0.11 installed, you may try following my instructions on making a nice .deb file.
i compiled the hg version. however, alsa-lib failed to compile, the error i got is the following:[/QUOTE]
My tutorial isn't about compiling the version from hg. :P

---

### Post by Stan83 on 2006-08-09
> **lodp said:**
> 
[QUOTE=er-ku;1345374]
Btw, you can check it in windows. Run a dxdiag command, and look for something like this under sound devices:

thanks for the tip -- i can't post the full line here, but the part that matters is: DEV_0883 -- so windows says ALC883 as well.[/QUOTE]

Well I just checked what would dxiag tell me, and now I am even more confused :\
I got: HDAUDIO\FUNC_01VEN_10ECDEV0883SUBSYS_1
so I guess Widows thinks ALC883 is the sound codec (am I right?)

So now, both OS'es claim it is ALC883, and Acer support that it is ALC260, it starts to be a bit funny :D

> **lodp said:**
> 
yeah, i was writing about you. didn't realize it wasn't the exact same machine. we'll probably stay in touch for a while ;)

I am not going any ware for a while :D (not changing a laptop), so probably we will ;)

> **er-ku said:**
> 
Well, how should I know for sure? You can google for that.  From googling, it doesn't seem so...


Conexant 20468-31 AC'97 audio codec ????

> **er-ku said:**
> 

If you still don't have ALSA 1.0.11 installed, you may try following my [instructions on making a nice .deb](http://ubuntuforums.org/showthread.php?p=1339688#post1339688) file.


But you know, there is a nice .deb file already :)
[http://packages.ubuntu.com/edgy/sound/alsa-base](http://packages.ubuntu.com/edgy/sound/alsa-base)

---

### Post by er-ku on 2006-08-09
> **Stan83 said:**
> But you know, there is a nice .deb file already :)
[http://packages.ubuntu.com/edgy/sound/alsa-base](http://packages.ubuntu.com/edgy/sound/alsa-base)

That's in Edgy. If you're using Dapper, you need a package compiled for Dapper, IMHO.

---

### Post by Stan83 on 2006-08-09
> **er-ku said:**
> That's in Edgy. If you're using Dapper, you need a package compiled for Dapper, IMHO.

Well yes, but it installs through dpkg with no problem :)
(doesn't work for me though :) )

---

### Post by lodp on 2006-08-09
> **Stan83 said:**
> 
So now, both OS'es claim it is ALC883, and Acer support that it is ALC260, it starts to be a bit funny :D


i'm beginning to think that the info from acer support is all a bunch of bull. i just wrote them back and told them about the output of dxdiag.

---

### Post by Stan83 on 2006-08-09
> **lodp said:**
> i'm beginning to think that the info from acer support is all a bunch of bull. i just wrote them back and told them about the output of dxdiag.

I asked them today, about dxdiag, and the right chipset, the guy said he only knows what he has in the manuals :) but was surprised at the output of dxdiag, and alsamixer.
He proposed that maybe updating the BIOS might help, he has send me the new BIOS, but i am a bit unwilling to install it... I don't think it would really help, and I don't wont to be left with non-bootable laptop.

Anyway from what I have in an e-mail from him this BIOS:
> 
BIOS v.3A19 Product Line: Notebook Model Name: Aspire 1640Z, Aspire 1650Z, TravelMate 4070, TravelMate 4080 

So Lodp could you checked what version of BIOS you have installed? I have 3A18, and the new one is marked 3A19, so if yours is 3A19, I am not changing anything :)

---

### Post by er-ku on 2006-08-10
> **Stan83 said:**
> Well yes, but it installs through dpkg with no problem :)
(doesn't work for me though :) )

First, what you need is alsa-modules-*, not alsa-base.
Second, even if you install alsa-modules from edgy, it doesn't necessary have to work. :)

Furthermore, it doesn't seem like Ubuntu is providing precompiled alsa-modules ever since Breezy.

---

### Post by lodp on 2006-08-10
> what version of BIOS you have installed

i've got 3A15. you're probably right, it won't change anything about our problem, but i don't think you're likely to end up with a non-bootable notebook if you installed it ..

---

