---
title: "Issues with my AMD HD 6470M and More!"
date: 2017-01-06
forum: Hardware
---

### Post by arszilla on 2017-01-06
Hi all

I recently restarted Ubuntu (I quit after failing to get my AMD GPU to work in any Linux Distro)

I decided to try once again but in this forum instead of /r/linux_gaming (darn mods there), /r/linuxmasterrace, /r/linuxquestions etc (And Stackoverflow)

So I don't have any GPU options in my BIOS FYI.

I ran some commands to speed up this process:

[B]lspci -nn | grep VGA

[/B]```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760] (rev ff)
```

**lsmod**

```
Module                  Size  Used by
ipheth                 16384  0
rfcomm                 69632  0
bnep                   20480  2
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
btusb                  45056  0
snd_hda_codec_hdmi     53248  1
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
btrtl                  16384  1 btusb
intel_rapl             20480  0
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    77824  1 snd_hda_codec_idt
snd_hda_intel          40960  5
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
btbcm                  16384  1 btusb
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
btintel                16384  1 btusb
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
coretemp               16384  0
wl                   6365184  0
kvm                   540672  0
snd_pcm               106496  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mei_me                 36864  0
snd_timer              32768  2 snd_pcm,snd_seq
input_leds             16384  0
rtsx_pci_ms            20480  0
glue_helper            16384  1 aesni_intel
joydev                 20480  0
cfg80211              565248  1 wl
snd                    81920  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei                    98304  1 mei_me
ablk_helper            16384  1 aesni_intel
serio_raw              16384  0
memstick               20480  1 rtsx_pci_ms
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
soundcore              16384  1 snd
shpchp                 36864  0
lpc_ich                24576  0
hp_wireless            16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_generic,usbhid
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  1
rtsx_pci_sdmmc         24576  0
i915                 1208320  5
ttm                    94208  1 radeon
i2c_algo_bit           16384  2 i915,radeon
drm_kms_helper        155648  2 i915,radeon
psmouse               131072  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
ahci                   36864  2
fb_sys_fops            16384  1 drm_kms_helper
libahci                32768  1 ahci
drm                   364544  10 ttm,i915,drm_kms_helper,radeon
r8169                  81920  0
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    16384  1 r8169
wmi                    20480  1 hp_wmi
video                  40960  1 i915
fjes                   28672  0
```

**ubuntu-drivers devices **
```

== cpu-microcode.py ==
driver   : intel-microcode - distro non-free

== /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 ==
vendor   : Broadcom Corporation
modalias : pci:v000014E4d00004727sv0000103Csd00001795bc02sc80i00
model    : BCM4313 802.11bgn Wireless Network Adapter
driver   : bcmwl-kernel-source - distro non-free
```

I tried using DRIPRIME=1 in steam games to make them run better but that caused issues like screen tearing and freezes in games back in October when I gave up on this issue. Now I have freezes that happen randomly without DRIPRIME and somehow my desktop crashes, when I click on my launcher icons to change between programs.

So I will need assistance to fix 3 things in this thread:

1) How to get my AMD HD 6470M to run properly so I can game in peace? I quit Windows cause of the spyware, the bs updates, the ugliness of it.
2) How do I stop the freezes in games?
3) How do I stop the desktop crashes? I mean if you guys want a vid on how it happens I can record it to demonstrate it.

All the help will be really appreciated!

---

### Post by QIII on 2017-01-06
If you go around complaining about the moderators elsewhere (and using foul language to do so), what impression do you think you will make on the moderators here?

What release of Ubuntu are you using?

Is this a laptop with hybrid Intel/AMD graphics?

lsmod indicates that you have the open source Radeon driver and Intel's i915 driver loaded.

---

### Post by arszilla on 2017-01-06
I meant that the mods there in Discord server were rude; claiming they were the know-it-alls.

Doesnt matter.

I thought I stated it? Its Ubuntu 16.04.1 LTS.

I dont have any AMD options in my Additional Drivers. Only Intel CPU and Broadcom WiFi.

I dont see anything related to AMD (Catalyst Control Panel maybe? Not sure if AMD gave one for Linux) in my system apps etc.

---

### Post by QIII on 2017-01-06
With 16.04 and beyond, the landscape for AMD drivers has changed.

We are in a "be careful what you wish for" period right now.  For years we have begged AMD for a capable open source driver, which we have gotten in AMDGPU (and that is the basis for AMDGPU-PRO, which has a proprietary overlay.)  The cost of that was that AMD spent its resources on AMDGPU and not on keeping fglrx up with changes to X Server -- which Canonical moved on to with 16.04.

It's interesting to note, however, that the open source developers AMD was working with most closely were mostly from Canonical.  Canonical and AMD have had quite a romance going on for many years.  Things are a mess right now -- consider it road work.  Eventually AMDGPU will work with many HD 7000 and later GPUs.  Your HD 6000 will not be supported because the hardware technology is not sufficient.

Anyway.  The reason you see no options for AMD is that when 16.04 is installed, the installer determines if the open source Radeon driver or the open source AMDGPU driver is appropriate based on the hardware present.  Your hardware is not supported by AMDGPU, so the Radeon driver was installed.

Add to that the hybrid graphics situation and you have a bit of a problem.

If I wanted to game above all other things, I would install 14.04 or 14.04.1 (and no later) and install the fglrx driver from Canonical's repo.  You can follow the instructions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD").  By the time of 14.04, the fglrx driver was capable of allowing one to switch between the disparate GPUs.  You have to shut down between because it is not "on-the-fly", but it can be done.

Read carefully and also read down a bit.  When I was helping to maintain that wiki page, I put some stuff in there about getting hardware acceleration to work, etc.

---

### Post by arszilla on 2017-01-06
So i should downgrade to 14.04...

How will that change up the stuff I do? Like I got numix rocking, Got some stuff sorted out. I just hate the `transfering files popup`. Liked 16.10's hidden button better...

So 14.04 is where I will live?

Would you say 14.04 is `guaranteed` to work for me? So I can play Insurgency, CIV 5 etc without some crappy fps drops, freezes etc?

---

### Post by QIII on 2017-01-06
Whether or not you should downgrade is your decision.  And I can't guarantee that anything is going to work and certainly not how any particular game will perform.  

What I can guarantee is that the last release under which your card is supported by a proprietary AMD driver is 14.04.  (You may be able to use 14.04.2 or later in the series, but you might start running into issues with Hardware Enablement Stacks that have gone out of support.)  Ubuntu's 14.10, 15.04 and 15.10 releases are all out of support, so you can't use them.

---

### Post by arszilla on 2017-01-06
ELI5 Hardware Enablement Stacks? What do you mean that they are out of support? They didnt have LTS?

Also what about my other two issues?

I may give 14.04 a shot, since I got nothing to lose. Just gotta backup my games.

---

### Post by QIII on 2017-01-06
Have a look at [this]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") regarding HWE.

After you've finished the first bit of explanation, scroll down to the area that gives the support periods for the various kernel/HWE combinations.  You'll find that a number of those combinations are out of support.  

14.04.5 is supported and will be, but there may be issues there for you.  I don't know.

As for your other issues, they may all be related to how well the Radeon driver is working.  It's a great deal better than a few years ago, but not perfect by a long shot.

---

### Post by arszilla on 2017-01-06
So you are suggesting 14.04 instead of 14.04.5? What is the difference between them though?

---

### Post by QIII on 2017-01-06
14.04.5 has components brought in from 16.04, meaning you may run into the same issues with your driver as you are having now.

I'm not trying to be obtuse or to dodge the question.  I'm providing information.  I will tell you what you can do, but in this situation I can't tell you what you should do.  Too many variables.

---

### Post by arszilla on 2017-01-06
What about 14.04.2? I am asking cause of the previous link you provided.

---

### Post by QIII on 2017-01-06
The kernel/HWE for 14.02.2 is out of support as are .3 and .4

---

### Post by arszilla on 2017-01-06
I still dont get what to do/install...

I get that 14.04/,2/,3/,4 are out of support? But what does that suppose to mean? I cant use them properly? I skimmed the link you gave but I am still confused.

---

### Post by QIII on 2017-01-06
I did say what I would do were I you.

There are often things I can suggest that people should or should not do. Unfortunately, for this one I can really only say what I would do.

Again, I'm not trying to avoid your question.

---

### Post by arszilla on 2017-01-06
I never said you were avoid my question :P

Thanks for sticking by and helping me btw.

I guess I will download 14.04.1. But after download: What do I do in [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) ? I have no idea what to follow? Do I start from `Introduction`?

**EDIT**

I cant seem to find 14.04.1 in ubuntu's official download page. only .5. Where should I look?

And I found some older stuff like 12.1. There seems to be PC and 64-Bit PC. Which one do I choose? I just want 64 Bit like in Windows?

---

### Post by QIII on 2017-01-06
On cell. Busy train.  Sorry short.

Sec 3.1 and 5

AMD64.  Don't worry about name.

---

### Post by QIII on 2017-01-06
Scroll down to 14.04.1

[http://old-releases.ubuntu.com/releases/trusty/](http://old-releases.ubuntu.com/releases/trusty/)

---

### Post by arszilla on 2017-01-06
Getting AMD64 of 14.04.1.iso.torrent.

Will post later tmrw when I wake up.

---

### Post by arszilla on 2017-01-07
Ok. Rocking 14.04.1 and I have this now:

[http://imgur.com/a/kx3O7](http://imgur.com/a/kx3O7)

Which one do I choose?

Also a side question: How do I get the scroller to feel like 16.x's? The 14.04 is ugly and bulky af

---

### Post by QIII on 2017-01-07
The best way to do it is via the command line in my opinion.  Using the instructions in section 3.1 of the link I gave you, I would install fglrx-updates, which should update to the latest available version of fglrx available for 14.04.

As for the other question, please start a new thread.  Things get confusing when trying to answer more than one subject at a time in a thread.

Let us know how the installation of fglrx goes and we'll see if there is anything else we'll need to do to get things working just right for you.

---

### Post by arszilla on 2017-01-07
Does the steps in 3.1 install the fglrx-updates? From what I skimmed it looks like its reinstalling/installing a fresh fglrx?

Also what happens if something goes sour? Like fails? How do I restore that Xorg backup?

**EDIT**

The guide you gave me says to follow this if I have Intel/AMD switchables (Which I do)

[https://ubuntuforums.org/showthread.php?t=1930450](https://ubuntuforums.org/showthread.php?t=1930450)

What then? Do I follow that?

---

### Post by arszilla on 2017-01-08
[http://imgur.com/a/cUBW8](http://imgur.com/a/cUBW8)

I got this during [https://ubuntuforums.org/showthread.php?t=1930450](https://ubuntuforums.org/showthread.php?t=1930450)

What do I do?

---

### Post by QIII on 2017-01-08
In Post #4 I said:

"If I wanted to game above all other things, I would install 14.04 or 14.04.1 (and no later) and install the fglrx driver from Canonical's repo. You can follow the instructions here. **By the time of 14.04, the fglrx driver was capable of allowing one to switch between the disparate GPUs.** You have to shut down between because it is not "on-the-fly", but it can be done."

The instructions you followed, ca. 2012, were no longer needed by that time.

There should be instructions with the .run file you downloaded from AMD that tell how to un-install the driver installed that way.  See if you can get it un-installed using those instructions and just use the fglrx driver included in 14.04.

Something to bear in mind that you may not realize:  AMD and Canonical have had a long romance going back many years.  There is little need to use anything from the AMD website since AMD has for years made sure that anything available there is available to Canonical before it is available to the general public.  That gives Canonical the time to package and test all the best stuff.

---

### Post by arszilla on 2017-01-08
I am at 14.04.1.

I asked in Post #21 whether to follow it and no one replied. Its not your fault btw, I took a leap and stuff went sour. Now how do I reverse the commands etc done there?

How do I get fglrx from Carnonical's repo?

**EDIT**

Can I reverse the commands I entered with sudo apt-get install with sudo apt-get remove and then sudo apt-get purge?

---

### Post by QIII on 2017-01-08
Did you use dpkg to install it?
[I][B]
If you used dpkg to install it,
[/B][/I]

```
sudo dpkg -r fglrx
```

should remove it.

If you used a .run file directly, there should be an uninstall.sh file in the installation directory.

You will also want to "get rid of" xorg.conf (which was created by the driver when installed) by renaming it (you can remove it later if you want to)

```
sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
```

That will keep the OS from trying to follow instructions it can't follow after the driver is removed.  By default, no xorg.conf is used in Ubuntu any longer.  It is added by drivers if needed.

---

### Post by arszilla on 2017-01-08
I ran the commands in the forumpost:

[SIZE=2]     ```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6
sudo apt-get install dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install linux-headers-generic xserver-xorg-core libgcc1
[FONT=Arial][SIZE=2]
sudo apt-get install ia32-libs lib32gcc1 libc6-i386
cd /usr ; sudo ln -svT lib /usr/lib64
[FONT=Arial][SIZE=2]
cd ~/; mkdir catalyst12.4; cd catalyst12.4/
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run
chmod +x amd-driver-installer-12-4-x86.x86_64.run
[FONT=Arial][SIZE=2]
sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise[SIZE=2]
```[/SIZE]

But the last 4 commands didnt work well, like I found the .catalyst12.4 folder, it had a text file and an empty folder. Deleted it. The last commands gave errors etc.

The others were successful; except the 4th one from the top, it didnt install anything. Still...

What do I do to remove them?

Then I will do fglrx from additional drivers
[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE]

---

### Post by arszilla on 2017-01-08
So I just choose FGLRX-Update in additional drivers and I am done?

I hope understood it right, cause I reinstalled 14.04.1 due to some issues

---

### Post by QIII on 2017-01-08
For best results, follow the terminal instructions in section 3.1.

If you choose to install from the additional drivers GUI, you still must make sure you run 

```
sudo amdconfig --initial
``` in the terminal *before* you reboot.

---

### Post by arszilla on 2017-01-08
> **QIII said:**
> For best results, follow the terminal instructions in section 3.1.

If you choose to install from the additional drivers GUI, you still must make sure you run 

```
sudo amdconfig --initial
``` in the terminal *before* you reboot.

I mean what is the difference between the Terminal VS Additional Drivers?

---

### Post by arszilla on 2017-01-08
I was checking my Ubuntu Software Updater before I do anything and I saw these in Ubuntu Base:

[http://imgur.com/a/N8JGW](http://imgur.com/a/N8JGW)

Should I update and do the S3.1? Or just opt these out?

---

### Post by QIII on 2017-01-08
The driver is the same.

---

### Post by arszilla on 2017-01-09
[http://imgur.com/a/vEYNN](http://imgur.com/a/vEYNN)

I fear somethings may go wrong, so imma do the additional drivers instead. And I will do that sudo thing before I reboot.

---

### Post by arszilla on 2017-01-09
I tried the Additional Drivers and ran the AMDCONFIG command and got this:

[http://imgur.com/a/vEYNN](http://imgur.com/a/vEYNN)

[http://imgur.com/a/fG5he](http://imgur.com/a/fG5he)

I wont reboot till you or someone replies about what do I do

---

### Post by arszilla on 2017-01-09
Turns out Ubuntu Software Updates make 14.04.1 to 14.04.5.

Not gonna update anything related to the base I suppose. Imma run the additonal drivers again now.

**EDIT**

[http://imgur.com/a/nRx8S](http://imgur.com/a/nRx8S)

Still the same issue
[B]
EDIT 2[/B]

I rebooted and did

```
sudo amdconfig --inital
```

and it worked!: [http://imgur.com/a/QZsZ7](http://imgur.com/a/QZsZ7)

But now my launcher is like this: how do I fix this? [http://imgur.com/a/2aWg1](http://imgur.com/a/2aWg1)

It might be slightly off topic but its caused by the update... So...

---

