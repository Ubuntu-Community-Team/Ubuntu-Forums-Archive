---
title: "Having problems with suspend on my laptop"
date: 2011-11-11
forum: Hardware
---

### Post by VY5E on 2011-11-11
I have a HP Pavilion DV 9000 Series laptop running Ubuntu 11.10. When I close the screen or suspend Ubuntu and wake it up/open the screen it just shows something similar to snow on a tv screen minus the animatedness of it. I have had no luck when trying to google/search the forums for this kinda problem.

---

### Post by northd_tech on 2011-11-11
Let's figure out what kind of video hardware you have.  Can you open a terminal (by pressing Ctrl-Alt-T) and copy/pasting the results of the following terminal command here on this thread:

```
sudo lshw -C display
```You could also use System > Preferences > Power Management to turn off or disable suspend (to blank screen, hibernate, or shutdown) if suspend is causing the problem.

FYI- I am also running an HP DV9xxx series laptop, but with Ubuntu Lucid Lynx 10.04.3 LTS running this kind of video/display adapter onboard:

> **sudo lshw -short**
H/W path        Device      Class    Description
===================================================
/0/12                                       display     C67 [GeForce 7150M / nForce 630M]

---

### Post by VY5E on 2011-11-11
Here is what you asked for

 *-display               
       description: VGA compatible controller
       product: G86 [GeForce 8600M GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ce000000-ceffffff memory:d0000000-dfffffff memory:cc000000-cdffffff ioport:2000(size=128)

---

### Post by northd_tech on 2011-11-11
Let's also see the output of these terminal commands:

```
lsmod
locate powersave-policy
cat /etc/lsb-release
uname -a

```There appear to have been some problems with that NVIDA GeForce 8600M video adapter with the older versions of Ubuntu:

[https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting/Feedback](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting/Feedback)

**Suspend broken on SERP3 + 10.04 Lucid**
[http://ubuntuforums.org/showthread.php?t=1476350](http://ubuntuforums.org/showthread.php?t=1476350)

**No Suspend-To-RAM after upgrade to Intrepid (amd64)**
[http://ubuntuforums.org/showthread.php?t=1118535](http://ubuntuforums.org/showthread.php?t=1118535)

It is possible that this "old" NVIDIA problem is back in the "new"-er Ubuntu 11.10.

---

### Post by VY5E on 2011-11-11
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
snd_hda_codec_si3054    13008  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
hp_wmi                 18092  0 
v4l2_compat_ioctl32    17083  1 videodev
sparse_keymap          13890  1 hp_wmi
snd_rawmidi            30547  1 snd_seq_midi
nvidia               8107305  41 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
r852                   18277  0 
sm_common              16865  1 r852
nand                   54966  2 r852,sm_common
snd_timer              29991  2 snd_pcm,snd_seq
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
mtd                    33181  2 sm_common,nand
iwl4965               132375  0 
serio_raw              13166  0 
iwl_legacy             83487  1 iwl4965
binfmt_misc            17540  1 
mac80211              310872  2 iwl4965,iwl_legacy
video                  19412  0 
snd                    68266  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  3 iwl4965,iwl_legacy,mac80211
wmi                    19256  1 hp_wmi
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
ahci                   26002  1 
libahci                26861  1 ahci

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"


Linux Pooty 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


and i'll check out those post's and see what they say

---

### Post by VY5E on 2011-11-11
Fixed it i changed the nvidia driver from version 173 to "currect version" and it works fine now thank you for your help =D

Edit: it is version 280:13

---

### Post by northd_tech on 2011-11-11
> **VY5E said:**
> 
***Module                  Size  Used by***
[COLOR=Red]**vesafb                 13809  1 **[/COLOR]
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
**nvidia               8107305  41 **
video                  19412  0 

Those kernel modules are all video related, and I'm not sure that you really need that '[COLOR=Red]**vesafb**[/COLOR]' module (which is a VESA driver I believe).  I'm not sure if it is interfering with that **nvidia** module though.  

Most of those threads that I linked to earlier were pretty old- they may or may not apply under your much newer Oneiric 11.10 Ubuntu.

If you'd like to try blacklisting that '[COLOR=Red]**vesafb**[/COLOR]' module, this terminal command should accomplish that:

```
echo 'blacklist vesafb' | sudo tee -a /etc/modprobe.d/blacklist.conf 
```Then restart and see if you are having the same troubles.  Undoing that blacklist command is also a very easy operation, so I wouldn't worry too much about trying it out.

Edit:  I see you got it fixed by using the newer NVIDIA driver.  If everything is installed properly, you should be able to verify your NVIDIA Driver Version with this terminal command:

```
nvidia-settings
```

Your NVIDIA driver should be listed under the first 'tab': X Server Information.

Also, it is good to mark this thread as [SOLVED] using the Thread Tools at the top of your first post for the benefit of other forum members.

---

