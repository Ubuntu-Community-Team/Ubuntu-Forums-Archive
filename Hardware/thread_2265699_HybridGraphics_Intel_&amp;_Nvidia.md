---
title: "HybridGraphics Intel &amp; Nvidia"
date: 2015-02-17
forum: Hardware
---

### Post by lister171254 on 2015-02-17
Installed 14.10 on my recently purchase laptop (Metabox) and everything went weel until I started a game in Steam and saw a message thast my graphicsa card 'isn't up to it'

Given that the laptop comes with a GeForce GTX 970M I thought that was weird.

I then found that the card that was in use was the on board Intel card.


I found a few links to HybridCards and managed in the process to render my Laptop useless (at least from a graphics perspective); all I have right now is terminal access.

Amongst other things I followd this link, but that doesn't work for me 
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

My questions are:
[LIST=1]
[*]How do I get the graphics back to the stage before I screwed it up (i.e. how to I get back to using the Intel card).
[*]Is there a way of disabling the Intel Card altogether
[/LIST]

Thanks

---

### Post by lister171254 on 2015-02-17
ok. I fixed issue 1 by removing all nvidia packages.

That leaves a solution to either disable the Intel card (can't it be blacklisted?) or making the Nvidia card the primary 

Thanks

---

### Post by kc1di on 2015-02-17
I don't know if you've seen[ this page]("http://askubuntu.com/questions/455124/how-do-i-get-switchable-graphics-to-work-on-my-samsung-rf711-with-intel-hd-gef") yet , but it may be of help.

---

### Post by efflandt on 2015-02-17
You did not say exactly what you tried. Did installing **nvidia-331-updates** not work with that new chip? In that case you may want to try **nvidia-346** from xorg-edgers ppa.```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346
```I have a year old laptop with older GTX 765m (and Intel HD 4600), so nvidia-331-updates worked fine for that. It defaulted to Nvidia graphics and NVIDIA X Server Settings has an option to switch between Nvidia and Intel graphics.

---

### Post by lister171254 on 2015-02-17
Sorry for being so vague in my problem description

Following are the steps so far:
1) removed all nvidia drivers and reboot. This get's me my desktop back
2) looked at syslog, which indicated that 331 was the wrong driver
3) looked on the NVIDIA website and foind that the correct drivers for a GTX 970M are 343 & 346
4) added the xorg-edgers ppa
5) installed the nvidia-346 drivers
6) installed nvidia-prime
7) rebooted

I must be very close as I can hear the (login) drum, but cannot see the mouse cursor or the Login screen

A snippet of the syslog follows

```
=====================
Feb 18 10:22:30 LeosGameLaptop kernel: [   30.874766] nvidia: module license 'NVIDIA' taints kernel.
Feb 18 10:22:30 LeosGameLaptop kernel: [   30.874769] Disabling lock debugging due to kernel taint
Feb 18 10:22:30 LeosGameLaptop kernel: [   30.876825] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
Feb 18 10:22:30 LeosGameLaptop kernel: [   30.879997] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Feb 18 10:22:30 LeosGameLaptop kernel: [   30.880276] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 1
Feb 18 10:22:30 LeosGameLaptop kernel: [   30.880281] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.35  Sat Jan 10 21:27:15 PST 2015
Feb 18 10:22:30 LeosGameLaptop kernel: [   41.656674] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
Feb 18 10:22:30 LeosGameLaptop kernel: [   41.717284] init: Error while reading from descriptor: Broken pipe
Feb 18 10:22:30 LeosGameLaptop kernel: [   41.718034] init: failsafe main process (1132) killed by TERM signal
Feb 18 10:22:31 LeosGameLaptop rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Feb 18 10:22:31 LeosGameLaptop kernel: [   42.621414] audit_printk_skb: 6 callbacks suppressed
Feb 18 10:22:31 LeosGameLaptop kernel: [   42.621416] audit: type=1400 audit(1424215351.317:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/{usr/,}bin/ping" pid=1301 comm="apparmor_parser"
Feb 18 10:22:31 LeosGameLaptop kernel: [   42.726337] audit: type=1400 audit(1424215351.421:15): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1301 comm="apparmor_parser"
Feb 18 10:22:31 LeosGameLaptop kernel: [   42.726343] audit: type=1400 audit(1424215351.421:16): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1301 comm="apparmor_parser"
Feb 18 10:22:31 LeosGameLaptop kernel: [   42.727584] audit: type=1400 audit(1424215351.421:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1301 comm="apparmor_parser"

===================
```

Thanks

---

### Post by lister171254 on 2015-02-17
Do I need to blacklist as this post suggests?

[http://ubuntuforums.org/showthread.php?t=2263316&highlight=GTX+970](http://ubuntuforums.org/showthread.php?t=2263316&highlight=GTX+970)

---

### Post by kc1di on 2015-02-18
You should blacklist any nouveau modules. 

what does the output of lsmod look like?

---

### Post by lister171254 on 2015-02-18
Here is the output of lsmod

```
llist@LeosGameLaptop:~$ lsmod
Module                  Size  Used by
ctr                    13049  2 
ccm                    17731  2 
rfcomm                 69509  8 
bnep                   19543  2 
binfmt_misc            17468  1 
uvcvideo               81065  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15682  1 videobuf2_core
videodev              149725  3 uvcvideo,v4l2_common,videobuf2_core
media                  21963  2 uvcvideo,videodev
arc4                   12608  2 
iwlmvm                217797  0 
mac80211              660592  1 iwlmvm
snd_hda_codec_hdmi     47547  1 
snd_hda_codec_realtek    77185  1 
snd_hda_codec_generic    68914  1 snd_hda_codec_realtek
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18786  0 
coretemp               13441  0 
kvm_intel             143592  0 
snd_hda_intel          30420  5 
snd_hda_controller     35152  1 snd_hda_intel
kvm                   459835  1 kvm_intel
snd_hda_codec         139675  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104102  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17344  0 
snd_rawmidi            30876  1 snd_seq_midi
btusb                  32448  0 
serio_raw              13434  0 
iwlwifi               183038  1 iwlmvm
bluetooth             446190  22 bnep,btusb,rfcomm
cfg80211              510218  3 iwlwifi,mac80211,iwlmvm
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                21093  0 
rtsx_pci_ms            18168  0 
6lowpan_iphc           18702  1 bluetooth
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
memstick               16966  1 rtsx_pci_ms
snd_timer              29513  2 snd_pcm,snd_seq
mei_me                 19742  0 
mei                    87931  1 mei_me
snd                    87611  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              15052  2 snd,snd_hda_codec
shpchp                 37040  0 
tpm_infineon           17131  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
dm_crypt               23172  3 
hid_logitech_dj        18469  0 
usbhid                 52566  0 
hid                   110426  3 usbhid,hid_logitech_dj
rtsx_pci_sdmmc         23043  0 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
nouveau              1234956  0 
aesni_intel           152552  11 
i915                  917814  6 
aes_x86_64             17131  1 aesni_intel
lrw                    13287  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13944  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20360  6 ghash_clmulni_intel,aesni_intel,ablk_helper
mxm_wmi                13021  1 nouveau
ttm                    97680  1 nouveau
firewire_ohci          44323  0 
i2c_algo_bit           13406  2 i915,nouveau
psmouse               106593  0 
drm_kms_helper         61627  2 i915,nouveau
ahci                   34062  4 
firewire_core          68671  1 firewire_ohci
r8169                  71471  0 
drm                   310919  7 ttm,i915,drm_kms_helper,nouveau
rtsx_pci               46301  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                32424  1 ahci
crc_itu_t              12707  1 firewire_core
mii                    13934  1 r8169
video                  20128  2 i915,nouveau
wmi                    19193  2 mxm_wmi,nouveau
======================================
```

Thanks

---

### Post by kc1di on 2015-02-18
you definitely need to black list nouveau or uninstall it one or the other or both.

---

### Post by lister171254 on 2015-02-19
ok. Entered the following into /etc/modprobe.d/blacklist.conf
#
blacklist nouveau
options nouveau modset=0
alias nouveau off
========================

I'm a real nob at this so not sure if this correct; I got this from some other posts.


The result unfortunately is still the same; the screen goes black after a reboot, I can hear the default ubuntu drum, but cannot get a login screen/our mouse.

The log shows the following:

==============
Feb 20 13:48:40 LeosGameLaptop kernel: [   29.600876] nvidia: module license 'NVIDIA' taints kernel.
Feb 20 13:48:40 LeosGameLaptop kernel: [   29.600879] Disabling lock debugging due to kernel taint
Feb 20 13:48:40 LeosGameLaptop kernel: [   29.602943] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
Feb 20 13:48:40 LeosGameLaptop kernel: [   29.605664] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
Feb 20 13:48:40 LeosGameLaptop kernel: [   29.605721] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Feb 20 13:48:40 LeosGameLaptop kernel: [   29.605951] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 1
Feb 20 13:48:40 LeosGameLaptop kernel: [   29.605955] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.35  Sat Jan 10 21:27:15 PST 2015
Feb 20 13:48:40 LeosGameLaptop kernel: [   40.055479] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)

Feb 20 13:48:50 LeosGameLaptop kernel: [   50.767726] init: lightdm main process (1920) terminated with status 1
Feb 20 13:48:50 LeosGameLaptop kernel: [   50.767734] init: lightdm main process ended, respawning
Feb 20 13:48:51 LeosGameLaptop kernel: [   51.859000] nvidia 0000:01:00.0: irq 54 for MSI/MSI-X
Feb 20 13:48:51 LeosGameLaptop kernel: [   51.861096] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
Feb 20 13:48:51 LeosGameLaptop kernel: [   51.861143] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)





===============

Thanks

---

### Post by kc1di on 2015-02-21
Only thing I see is that, that nvidia driver does not seem to be compatible with that kernel.  Try a older or new driver and or kernel.

---

### Post by lister171254 on 2015-02-21
Thanks, but where can I see which driver is compatible for which kernel.

I know that nvidia-331 doesn't work, hence the installation of the 346 drivers. These drivers seem to work with the 14.10 kernel for other cards.

Thanks,

Leo

---

### Post by Keith_Helms on 2015-02-25
I haven't figured out how to get Nvidia optimus working using Prime, but I have got the nvidia card working selectively using Bumblebee.

Some observations:

1. The Nvidia drivers (I tried 331, 340, and 346) do NOT work in 14.04 in an optimus hardware setting (dual Intel and Nvidia cards), at least not without some additional configuration tweaking.   The result for me was a black screen instead of a login screen.

2. Installing bumblebee and bumblebee-nvidia along with the nvidia drivers gets you back to a working gui.  Bumblebee blacklists the Nvidia driver and it can then be loaded for a specific application using the optirun command.

3. Bumblebee doesn't know about or hasn't been updated for the nvidia 340 and 346 drivers.   Therefore, if you use one of those, you have to "gksudo gedit /etc/modprobe.d/bumblebee.conf" and clone one of the blocks of lines for various nvidia drivers and change the numbers to 340, 346, or both.   Without this change and using the 340 or 346 drivers, you're back to the black screen instead of login problem.

4. As far as blacklisting the Nouveau drivers, apparently the nvidia drivers ALREADY do that.  If you'll look in /etc/modprobe.d/nvidia-346_hybrid.conf (or whichever version you have installed), you'll see the Nouveau driver blacklisted there.  Additional drivers seems to think the nouveau driver is in use, but my system appears to be using the i915 Intel driver instead.

At this point, I can use the Nvidia GPU for an application by running it with the optirun command, i.e. "optirun vmplayer".  My Nvidia X Server Settings does not have a Prime Profiles option, which means I can't switch to using the Nvidia card by default for everything.   I'm still reading the hundreds of postings to try and figure that out.

---

### Post by kc1di on 2015-02-26
Glad you were able to sort it out, good work :)

---

### Post by Keith_Helms on 2015-02-26
Here's the weird thing.  I was not able to get Nvidia Prime working on Xubuntu 14.04, which is currently using the 3.13 kernel.  I set up Ubuntu 14.04 with the Metacity Flashback desktop to dual boot on my laptop.  Ubuntu is using the 3.16 kernel.  When I installed the Nvidia 346 driver from the xorg-edgers ppa on Ubuntu 14.04, Nvidia Prime worked just fine, other than the known bug where the mouse and desktop sometimes freeze up.  Doing ctrl-alt-f1 to go to a command line and then ctrl-alt-f7 to go back to the gui seems to "unfreeze" things.  I haven't run long enough using the Nvidia drivers to see how frequently that problem occurs.

So, the Prime problem appears to be related to kernel version.  Both systems are using the lightdm display manager and I can't imagine that a different window manager would cause that kind of issue.

---

