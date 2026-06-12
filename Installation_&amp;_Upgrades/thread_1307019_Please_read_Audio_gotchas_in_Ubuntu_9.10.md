---
title: "Please read: Audio gotchas in Ubuntu 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by crimsun on 2009-10-30
I've put together a list of common pitfalls when upgrading to Ubuntu 9.10. It's located at [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html).

Briefly,
    * Use Karmic's kernel, not Jaunty's.
    * Check that slmodemd is not running if you're seeing a dummy/null sink in the volume control applet.
    * Install linux-backports-modules-alsa-karmic (then reboot) if you have a very new computer.
    * Use a temporary alternate channel mapping for PulseAudio if you have an ice17xx-based sound card.
    * Configure PulseAudio to ignore your sound driver's misreported dB information if you experience "overdriven" sound.
    * Attach a verbose PulseAudio runtime log to your PulseAudio bug report.
    * Attach an ALSA codec dump to your linux bug report if jack sense (e.g., connecting headphones mutes internal laptop speakers) does not seem to function properly.

---

### Post by geoffm on 2009-11-01
I have to boot kernel 2.6.28 because I experience a severe kernel crash when I suspend/hibernate with 2.6.31
But audio doesn't work on 2.6.28.
Nothing appears in Sound Preferences/Hardware.
Is there a way to make the audio hardware work in the older kernel?

EDIT:
Actually, I reinstalled karmic from scratch and now all works fine with kernel 2.6.31

---

### Post by efflandt on 2009-11-01
Where did you find kernel 2.6.31-15?

Kernel 2.6.31-14 from 9.04 to 9.10 upgrade works fine on my 32-bit laptop.  I did hear some clicks and pops probably, from the powersave issue, but not that noticeable on small speakers.

But 64-bit 2.6.31-14 on my upgraded desktop throws kernel oops due to something that is really just a warning, not fatal.  Booting alternate older kernel 2.6.28-16 gets no oops, but seems to have killed all sound, even when I tried booting back into 2.6.31-14.  Although, I am sure that it worked at first when I got 64-bit flash working in Firefox.  Update Manager says there are no updates available.

I get sound booting to a live system on an install CD, which has 2.6.31-14, but I also get the kernel oops (bug 422536).  Posting this from there with a music CD running.

I am new to Ubuntu, so not sure where to get a fix, even if the status of a bug is "fixed".

PS: Strange.  After running the 9.10 live CD (which got the oops) I booted back to 2.6.31-14 on my hard drive and no oops, and sound works (including Firefox audio/video).  Internal Audio shows up in Sound Preferences for Input, Mic, and Output instead of blank entries and Dummy Stereo output.

---

### Post by BRPSA on 2009-11-02
Hi I am having the same problem, kernel 2.6.31.14, when it starts the screen turns all black, and it stays like that. But if I boot with kernel 2.6.28-16 I don't have audio, and if I try to see a video the computer automatically re-starts. When It is booting in kernel 2.6.28-16 it appears for a few seconds a warning that says something like there is hardware that couldn't be mount in fstab and is giving me the option to press esc and start in the recovery mode.

I ll be waiting for your help!! 
Thanks!!!!
bye

---

### Post by willemto on 2009-11-02
I upgraded to 9.10, and can start 2.6.28-16. (No audio as well) Can not boot from 2.6.3-14. 

Tried grup2. Problem still there.

---

### Post by Ian Sinclair on 2009-11-02
Upgraded to 9.10 with the bug 422536. Cannot print photos from F-spot or Photoprint, cannot use Grisbi (accounts program) because of segmentation fault. You would think this would have been sorted out by Beta stage.

---

### Post by andrewabc on 2009-11-02
Add [crackling sound](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12) solution to first post. Many people have this problem.

---

### Post by ttguy on 2009-11-02
I upgraded to 9.10 and then found web browsing stopped. ( I am not sure if audio was working on this upgraded version. )

I restored a cloned image of my  /dev/sda1 partition. (My /home is on /dev/sda3).

After restoring back to  9.04 my browsing works but my audio is gone. I used to have the master volume control in the menu bar at the top. But this has disappeared. 

So this is major suckyness. :(

I guess the upgrade changed some audio configuration in  /home. 

I bet a windows 7 upgrade would work !!! ;)

Any suggestions.

edit: Fixed the missing Volume Control after restoring 9.04 - Right click on menu bar and choose add to panel. Choose Volume Applet.
After restoring the volume control I was able to unmute the audio. 

Still want to know what the fix for my browsing problems in 9.10 though!

---

### Post by David Starling on 2009-11-02
I have the "overdriven sound" problem after upgrading to 9.10 from 9.04. I'm using an inspiron 9400 laptop. The link above mentions this problem, but there doesn't seem to be a detailed "fix" for it. 

Any suggestions for a newb? Thanks.

---

### Post by psidrum on 2009-11-03
> **willemto said:**
> I upgraded to 9.10, and can start 2.6.28-16. (No audio as well) Can not boot from 2.6.3-14. 

Tried grup2. Problem still there.

try installing grub-pc,

was not able to install the latest kernel but after installing grub-pc, new kernel is working now, and also read my audio card.

---

### Post by ratcheer on 2009-11-03
> **crimsun said:**
> I've put together a list of common pitfalls when upgrading to Ubuntu 9.10. It's located at [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html).



Thank you.

Tim

---

### Post by crimsun on 2009-11-03
> **andrewabc said:**
> Add [crackling sound](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12) solution to first post. Many people have this problem.

That's not a solution; that's a workaround. The solution is to fix sound/pci/hda/patch_*.c.

---

### Post by crimsun on 2009-11-03
> **David Starling said:**
> I have the "overdriven sound" problem after upgrading to 9.10 from 9.04. I'm using an inspiron 9400 laptop. The link above mentions this problem, but there doesn't seem to be a detailed "fix" for it. 

Any suggestions for a newb? Thanks.

The bug report links to a blog post where I spell out precisely what to add (ignore_dB=1 to the module-udev-detect line) to which file (/etc/pulse/default.pa or ~/.pulse/default.pa). Alternately, you can edit the same file and pass control=foo to module-alsa-sink (where foo is the name of the amixer control element).

---

### Post by SpotTheWonderDog on 2009-11-03
After banging my head against the wall for two solid days trying to recover from upgrading to Koala from
Jaunty, I just about ready to throw in the towel.

I've got a desktop with built in audio on the MB.  Ubuntu is on a separate hard disk.  If I boot up in Windows, 
audio works fine.

I can't boot up in 2.6.31-14 without the system crashing.  I can boot up in 2.6.28-15.
I entered every command that someone mentioned in the forums and posted the results here.

Why can't I get audio?
Why can't I boot up in 2.6.31-14?
Is it possible to downgrade to Jaunty without having to wipe the disk and reload?  I spent months configuring the system.



[FONT=Courier New]$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 22


$ fuser -v /dev/dsp* /dev/snd/*
(no output)

$ alsa force-reload
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

$ aplay -l
aplay: device_list:223: no soundcards found...

During bootup, I noticed this: 'PulseAudio configured for per-user sessions'  Is this good or bad or 
neither?

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

$ lspci -v | less

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Device 81ec
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 
        
Sound preferences->Output->Choose a device for sound output:
"Dummy output"

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.

$ ls /etc/asound*
ls: cannot access /etc/asound*: No such file or directory


$ strace -eopen alsamixer
open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/lib/libncurses.so.5", O_RDONLY)  = 3
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/librt.so.1", O_RDONLY) = 3
open("/dev/urandom", O_RDONLY)          = 3
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
open("/usr/share/alsa/pulse.conf", O_RDONLY) = 3
open("/usr/share/alsa/bluetooth.conf", O_RDONLY) = 3
open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/usr/lib/alsa-lib/libasound_module_conf_pulse.so", O_RDONLY) = 3
open("/usr/lib/libpulse.so.0", O_RDONLY) = 3
open("/usr/lib/libpulsecommon-0.9.19.so", O_RDONLY) = 3
open("/usr/lib/libX11.so.6", O_RDONLY)  = 3
open("/usr/lib/libICE.so.6", O_RDONLY)  = 3
open("/usr/lib/libSM.so.6", O_RDONLY)   = 3
open("/usr/lib/libXtst.so.6", O_RDONLY) = 3
open("/lib/libwrap.so.0", O_RDONLY)     = 3
open("/usr/lib/libsndfile.so.1", O_RDONLY) = 3
open("/lib/libdbus-1.so.3", O_RDONLY)   = 3
open("/usr/lib/libxcb.so.1", O_RDONLY)  = 3
open("/lib/libuuid.so.1", O_RDONLY)     = 3
open("/usr/lib/libXext.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 3
open("/usr/lib/libFLAC.so.8", O_RDONLY) = 3
open("/usr/lib/libvorbisenc.so.2", O_RDONLY) = 3
open("/usr/lib/libvorbis.so.0", O_RDONLY) = 3
open("/usr/lib/libogg.so.0", O_RDONLY)  = 3
open("/usr/lib/libXau.so.6", O_RDONLY)  = 3
open("/usr/lib/libXdmcp.so.6", O_RDONLY) = 3
open("/dev/snd/controlC0", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC0", O_RDONLY)          = -1 ENOENT (No such file or directory)
alsamixer: function snd_ctl_open failed for default: No such file or directory

$ lsmod
Module                  Size  Used by
snd_hda_intel         435252  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
sha1_generic           10368  0 
arc4                    9856  0 
ecb                    10752  0 
ppp_mppe               14724  0 
ppp_async              16896  0 
crc_ccitt              10112  1 ppp_async
binfmt_misc            16776  1 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
usblp                  20224  0 
x_tables               23044  1 ip_tables
nvidia               9594120  26 
sbp2                   30476  0 
usbhid                 42336  0 
intel_agp              34108  0 
ppdev                  15620  0 
parport_pc             40100  1 
lp                     17156  0 
agpgart                42696  2 nvidia,intel_agp
parport                42220  3 ppdev,parport_pc,lp
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
floppy                 64324  0 
atl1                   40584  0 
mii                    13312  1 atl1
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

$ asoundconf list
Names of available sound cards:
Intel

$ cat /proc/interrupts
           CPU0       CPU1       
  0:        165          0   IO-APIC-edge      timer
  1:       1449          0   IO-APIC-edge      i8042
  4:          6          0   IO-APIC-edge    
  6:          5          0   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 16:     727510          0   IO-APIC-fasteoi   ahci, uhci_hcd:usb3, nvidia
 17:     293821          0   IO-APIC-fasteoi   pata_jmicron, uhci_hcd:usb4
 18:          0          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7
 19:         32          0   IO-APIC-fasteoi   uhci_hcd:usb6
 21:          3          0   IO-APIC-fasteoi   ohci1394
 22:      11445          0   IO-APIC-fasteoi   HDA Intel
 23:      35756          0   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5, ohci1394
2298:      25728          0   PCI-MSI-edge      eth0
2299:      41924          0   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:     387855    1037249   Local timer interrupts
RES:       3377       4995   Rescheduling interrupts
CAL:        166        607   Function call interrupts
TLB:        922       2323   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

$ lspci -s 00:1b.0 -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 81ec
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

$ cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

$ update-grub
Searching for GRUB installation directory ... found: /boot/grub
findfs: unable to resolve 'UUID=31038fcb-b7d2-45e7-80fc-ebf9ee8b3bd2'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done



$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 4CD4E2E9D4E2D3EC -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 54A4B449A4B42F7C -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 80980CBF980CB5A6 -> ../../sda9
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 A86C2B146C2ADD36 -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 B4A000F8A000C2BA -> ../../sda8
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 bb28d2a4-9763-4627-97dc-fe98a51b98c4 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 d31384db-7522-4340-8fa3-819eaa6d758e -> ../../sdd5


after changing uuid in fstab to bb28d2a4-9763-4627-97dc-fe98a51b98c4

$ update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

$ cat /boot/grub/menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bb28d2a4-9763-4627-97dc-fe98a51b98c4

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##


### I had to manually move 2.6.28-15-generic to the top of the list or the system wouldn't boot
### (file not found)

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        bb28d2a4-9763-4627-97dc-fe98a51b98c4
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04-new, kernel 2.6.28-15-generic (recovery mode)
uuid        bb28d2a4-9763-4627-97dc-fe98a51b98c4
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

### 2.6.31-14 results in 'mountall General Error Mounting filesystems'
### and 'file not found'  ( referring to: /boot/vvmlinuz-2.6.31-14  ??)


title        Ubuntu 9.04new, kernel 2.6.31-14-generic
uuid        bb28d2a4-9763-4627-97dc-fe98a51b98c4
kernel        /boot/vvmlinuz-2.6.31-14-generic root=UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        bb28d2a4-9763-4627-97dc-fe98a51b98c4
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

### memtest can't be found
title        Ubuntu 9.04, memtest86+
uuid        bb28d2a4-9763-4627-97dc-fe98a51b98c4
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



$ ls -l /boot
total 51352
-rw-r--r-- 1 root root  508385 2009-04-01 18:46 abi-2.6.27-11-generic
-rw-r--r-- 1 root root  528128 2009-06-30 17:56 abi-2.6.28-13-generic
-rw-r--r-- 1 root root  528310 2009-09-09 08:56 abi-2.6.28-15-generic
-rw-r--r-- 1 root root  629174 2009-10-16 14:03 abi-2.6.31-14-generic
-rw-r--r-- 1 root root   91358 2009-04-01 18:46 config-2.6.27-11-generic
-rw-r--r-- 1 root root   96768 2009-06-30 17:56 config-2.6.28-13-generic
-rw-r--r-- 1 root root   96804 2009-09-09 08:56 config-2.6.28-15-generic
-rw-r--r-- 1 root root  111371 2009-10-16 14:03 config-2.6.31-14-generic
drwxr-xr-x 2 root root    4096 2009-11-03 17:19 grub
-rw-r--r-- 1 root root 8227661 2009-05-03 12:25 initrd.img-2.6.27-11-generic
-rw-r--r-- 1 root root 7548196 2009-07-17 10:04 initrd.img-2.6.28-13-generic
-rw-r--r-- 1 root root 7549168 2009-09-29 10:15 initrd.img-2.6.28-15-generic
-rw-r--r-- 1 root root 7645225 2009-11-02 11:29 initrd.img-2.6.31-14-generic
-rw-r--r-- 1 root root  128796 2009-10-23 12:11 memtest86+.bin
-rw-r--r-- 1 root root 1031799 2009-04-01 18:46 System.map-2.6.27-11-generic
-rw-r--r-- 1 root root 1449810 2009-06-30 17:56 System.map-2.6.28-13-generic
-rw-r--r-- 1 root root 1450680 2009-09-09 08:56 System.map-2.6.28-15-generic
-rw-r--r-- 1 root root 1664737 2009-10-16 14:03 System.map-2.6.31-14-generic
-rw-r--r-- 1 root root    1074 2009-04-01 18:48 vmcoreinfo-2.6.27-11-generic
-rw-r--r-- 1 root root    1074 2009-06-30 17:58 vmcoreinfo-2.6.28-13-generic
-rw-r--r-- 1 root root    1074 2009-09-09 08:58 vmcoreinfo-2.6.28-15-generic
-rw-r--r-- 1 root root    1196 2009-10-16 14:06 vmcoreinfo-2.6.31-14-generic
-rw-r--r-- 1 root root 2249232 2009-04-01 18:46 vmlinuz-2.6.27-11-generic
-rw-r--r-- 1 root root 3488208 2009-06-30 17:56 vmlinuz-2.6.28-13-generic
-rw-r--r-- 1 root root 3491312 2009-09-09 08:56 vmlinuz-2.6.28-15-generic
-rw-r--r-- 1 root root 3890400 2009-10-16 14:03 vmlinuz-2.6.31-14-generic


# uname -a
Linux joe-desktop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

[/FONT]

---

### Post by SpotTheWonderDog on 2009-11-03
Not related to sound, but I just found out that 'Suspend' no longer works.

---

### Post by andrewabc on 2009-11-03
> **crimsun said:**
> That's not a solution; that's a workaround. The solution is to fix sound/pci/hda/patch_*.c.

It's a solution until a patch is released via updates.
Until then it stops the problem for users. I doubt users want to wait for an update. ;)

---

### Post by Magnesium on 2009-11-04
> **andrewabc said:**
> It's a solution until a patch is released via updates.
Until then it stops the problem for users. I doubt users want to wait for an update. ;)

I would have to agree with Andrew. Yes, a permanent solution would be better, but for now, a workaround will allow those of us with this problem an option to get rid of the the annoying static buzz. I only saw his post by accident scrolling around, but am glad I did! :D

Crimsun, I would hope that you could add this workaround to your first post.

Thanks,
Mg

---

### Post by dazer26 on 2009-11-04
My external mic isn't working with 9.10.  It worked fine in 9.04.  I have messed with all the settings in the mixer.  If I turn the mic volume all the way up, unmute the mic boost and turn my speakers up I can hear some static, if I mute the mic the static goes away...i'd expect to hear this if I had nothing plugged in the mic jack.  I tried plugging in my mic in a bunch of the audio jacks (line-in ect) in case it had gotten them mixed up, but no luck.  I even tried pluging the mic into the line-in jack then changing the capture to line-in, nothing.  So I guess the line-in jack doesn't work either, or maybe the entire capture process. I'm going to try the alsa-backports and see if that helps.  

I'm using Kubuntu 9.10.  My sound is onboard, Nvidia CK804 AC'97 7.1 surround.  Besides the mic and line-in, everying else seems to work that had worked before (get sound out of 4 speakers and the sub, never been able to get sound out of the center speaker tho, it's a 5.1 setup).

---

### Post by fantan on 2009-11-04
And how to fix this:

" Originally Posted by crimsun  View Post
That's not a solution; that's a workaround. The solution is to fix sound/pci/hda/patch_*.c."

---

### Post by marwayusuf on 2009-11-04
> **crimsun said:**
> That's not a solution; that's a workaround. The solution is to fix sound/pci/hda/patch_*.c.

I've tried the workaround but it doesn't work.
Also, how can I fix it?

[EDIT]It's solved now

---

### Post by linuxmart on 2009-11-04
I currently run Ubuntu 9.04 and my sound works fine, but when I boot with the 9.10 liveCD, I get a high pitched noise coming from the speakers. I can hardly hear Ubuntu's boot up sound. It sounds like an FM radio not tuned to a station. The noise is the same regardless of high or low volume or even when muted.
Is is safe to install 9.10 on my computer or will I have the same problem I have with the liveCD? I would do a clean install, not an upgrade.

This is my integrated sound card:
Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

Thanks.

---

### Post by jal on 2009-11-04
> **David Starling said:**
> I have the "overdriven sound" problem after upgrading to 9.10 from 9.04. I'm using an inspiron 9400 laptop. The link above mentions this problem, but there doesn't seem to be a detailed "fix" for it. 

Any suggestions for a newb? Thanks.

I had "overdriven sound" (really mangled unless run at very low volumes) on my Lenovo R61e after upgrading to 9.04. After several months I discovered that dialing back "PCM" on the HDA Intel (Alsa mixer) applet  fixed the problem.

I note above someone mentioned "incorrect dB values" being reported by the sound card, and wonder if this is connected.

---

### Post by ColJep on 2009-11-04
I have done a fresh install of 9.10 on an intel G43 motherboard. The sound chip is recognised but I can only get very low volume. Alsamixer works and I was able to un-mute the master, still no sound though.

I have the same problem of no sound on a fresh install on another computer with Nvidia chipset but Have not had the time to look into it.

Any ideas?

---

### Post by running_rabbit07 on 2009-11-05
> **SpotTheWonderDog said:**
> After banging my head against the wall for two solid days trying to recover from upgrading to Koala from
Jaunty, I just about ready to throw in the towel.

I've got a desktop with built in audio on the MB.  Ubuntu is on a separate hard disk.  If I boot up in Windows, 
audio works fine.

I can't boot up in 2.6.31-14 without the system crashing.  I can boot up in 2.6.28-15.
I entered every command that someone mentioned in the forums and posted the results here.

Why can't I get audio?
Why can't I boot up in 2.6.31-14?
Is it possible to downgrade to Jaunty without having to wipe the disk and reload?  I spent months configuring the system.[FONT=Courier New]
[/FONT]

Do a clean install. That seems to be fixing a lot of issues for a lot of people. Upgrading seems to not be doing the job for some people.

---

### Post by ColJep on 2009-11-05
I read some other suggestions and ended up running the audio tests in System > Admin > System Testing. This suggested reporting a bug which I did and soon had a suggestion to install linux-backports-modules-alsa-karmic-generic and reboot.

This I did and now Alsamixer works and I have very good sound.

---

### Post by ColJep on 2009-11-05
After my monitor shut down and I woke the system the sound had gone again!

So back to the beginning. Another fault I have is that if the monitor is shut down for about 2-3 hours the computer will not wake up and I have to press the reset button. Maybe they are related. I have never had the refusal to wake problem on any Linux before.

Motherboard is Asus P5QL-CM with Intel G43 chipset and integrated video.

---

### Post by amisaka on 2009-11-05
> **andrewabc said:**
> Add [crackling sound](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12) solution to first post. Many people have this problem.

Thanks that really worked in my case! Toshiba with HDA Intel.

---

### Post by airtac on 2009-11-05
Have problem with no sound after upgrading to 9.10 The system see the sound card.

I try to reinstall the driver and asound. 

Any help would be great!!!


*****-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff4000 irq 22

******-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
[COLOR=Red]0**0:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)**[/COLOR]
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)

******-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...

---

### Post by crimsun on 2009-11-06
> **dazer26 said:**
> My external mic isn't working with 9.10.  It worked fine in 9.04.  I have messed with all the settings in the mixer.  If I turn the mic volume all the way up, unmute the mic boost and turn my speakers up I can hear some static, if I mute the mic the static goes away...i'd expect to hear this if I had nothing plugged in the mic jack.  I tried plugging in my mic in a bunch of the audio jacks (line-in ect) in case it had gotten them mixed up, but no luck.  I even tried pluging the mic into the line-in jack then changing the capture to line-in, nothing.  So I guess the line-in jack doesn't work either, or maybe the entire capture process. I'm going to try the alsa-backports and see if that helps.  

I'm using Kubuntu 9.10.  My sound is onboard, Nvidia CK804 AC'97 7.1 surround.  Besides the mic and line-in, everying else seems to work that had worked before (get sound out of 4 speakers and the sub, never been able to get sound out of the center speaker tho, it's a 5.1 setup).

Diagnosing these sorts of descriptions is futile. Bug reports do better -- use "ubuntu-bug alsa-base".

---

### Post by crimsun on 2009-11-06
> **fantan said:**
> And how to fix this:

" Originally Posted by crimsun  View Post
That's not a solution; that's a workaround. The solution is to fix sound/pci/hda/patch_*.c."

Honestly: read the data sheets and submit patches.

---

### Post by crimsun on 2009-11-06
> **linuxmart said:**
> I currently run Ubuntu 9.04 and my sound works fine, but when I boot with the 9.10 liveCD, I get a high pitched noise coming from the speakers. I can hardly hear Ubuntu's boot up sound. It sounds like an FM radio not tuned to a station. The noise is the same regardless of high or low volume or even when muted.
Is is safe to install 9.10 on my computer or will I have the same problem I have with the liveCD? I would do a clean install, not an upgrade.

This is my integrated sound card:
Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

Thanks.

If you use the live/desktop cd, make sure the universe repository is enabled, install the linux-backports-modules-alsa-karmic-generic package, disable PA autospawn, sudo alsa force-unload && sudo modprobe snd-hda-intel, and reenable autospawn.

Those sequence of steps approximate installing a fresh 9.10 and linux-backports-modules-alsa-karmic-generic. (They also presume your sound driver is hda-intel, which isn't necessarily true. See /proc/asound/modules .)

---

### Post by crimsun on 2009-11-06
> **jal said:**
> I had "overdriven sound" (really mangled unless run at very low volumes) on my Lenovo R61e after upgrading to 9.04. After several months I discovered that dialing back "PCM" on the HDA Intel (Alsa mixer) applet  fixed the problem.

I note above someone mentioned "incorrect dB values" being reported by the sound card, and wonder if this is connected.

Yes, it is. I blogged about it. There are at least two workarounds mentioned.

---

### Post by crimsun on 2009-11-06
> **ColJep said:**
> I read some other suggestions and ended up running the audio tests in System > Admin > System Testing. This suggested reporting a bug which I did and soon had a suggestion to install linux-backports-modules-alsa-karmic-generic and reboot.

This I did and now Alsamixer works and I have very good sound.

linux-backports-modules-alsa-karmic-generic really only helps three classes of hda-intel users, those being Realtek, IDT, and VIA. See your /proc/asound/card*/codec*

---

### Post by crimsun on 2009-11-06
> **airtac said:**
> Have problem with no sound after upgrading to 9.10 The system see the sound card.

I try to reinstall the driver and asound. 

Any help would be great!!!


*****-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff4000 irq 22

******-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
[COLOR=Red]0**0:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)**[/COLOR]
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)

******-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...

File a bug using "ubuntu-bug alsa-base". This thread isn't technical support.

---

### Post by PippoFranco on 2009-11-06
I have just installed 9.10 on my ACER TravelMate8200. lspci shows:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Audio stops working when I enable the proprietary SmartLink modem daemon (the application part of the driver for recent modems produced by Smart Link Ltd.). The audio works again if I disable the modem driver.

Franco (Linux counter 5224)

---

### Post by running_rabbit07 on 2009-11-06
> **PippoFranco said:**
> I have just installed 9.10 on my ACER TravelMate8200. lspci shows:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Audio stops working when I enable the proprietary SmartLink modem daemon (the application part of the driver for recent modems produced by Smart Link Ltd.). The audio works again if I disable the modem driver.

Franco (Linux counter 5224)

You aren't going to get much help in this thread. Should open a help thead.

---

### Post by audiomick on 2009-11-06
> > **dazer26 said:**
> My external mic isn't working with 9.10.  It worked fine in 9.04.  ... unmute the mic boost and turn my speakers up I can hear some static, if I mute the mic the static goes away...i'd expect to hear this if I had nothing plugged in the mic jack..

Hallo. I really don't want to sound like a smartarse, but...

I am a sound engineer with more than 20 years experience, and I use a lot of digital gear these days.

Your description indicates that the machine is "hearing" the input.

[QUOTE]if I mute the mic the static goes away

Are you totally sure that your mic and cable are still good? I don't know how often I and my colleagues have spent frustrating time looking for the digital problem that turned out to be a broken or unplugged cable ;-)

Sorry I can't help more
Michael

---

### Post by audiomick on 2009-11-06
took this back out again, someone had already made a better suggestion...

---

### Post by senseworld on 2009-11-06
Thank-you for the fixes, been a week without sound on my Ubuntu htpc.  Evidently I needed the backport.  Much appreciated.

---

### Post by Lido on 2009-11-07
I've looked through this thread, tried backports, tried the Ubuntu sound troubleshooting procedures and quite a few other threads here and elsewhere and I've still got no sound. I upgraded 9.04 to 9.10 a few days ago and that's when this started. I'd do a clean install, but I don't want to lose my MythTV database and other configurations. Any ideas?
```
lspci
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)

```

in /var/log/messages:
```
pulseaudio[2486]: sink-input.c: Failed to create sink input: sink is suspended.
```
and
```
pulseaudio[2486]: ratelimit.c: 7 events suppressed
```

I'd submit a bug report, but I don't know what info to provide.

---

### Post by running_rabbit07 on 2009-11-07
> **Lido said:**
> I've looked through this thread, tried backports, tried the Ubuntu sound troubleshooting procedures and quite a few other threads here and elsewhere and I've still got no sound. I upgraded 9.04 to 9.10 a few days ago and that's when this started. I'd do a clean install, but I don't want to lose my MythTV database and other configurations. Any ideas?
```
lspci
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)

```in /var/log/messages:
```
pulseaudio[2486]: sink-input.c: Failed to create sink input: sink is suspended.
```and
```
pulseaudio[2486]: ratelimit.c: 7 events suppressed
```I'd submit a bug report, but I don't know what info to provide.

If you made the /home partition, all of your config file will be safe.

---

### Post by Acradon on 2009-11-08
Hi, 

I also just upgraded and experience problems with my audio. However, Amarok works fine and playback is OK. Online videos and Skype do not work. I think this has to do with the settings, as those are set to pulse (I think). In skype I have tried all the nvidia settings, with no luck. Although one of the settings says it is working fine, but no sound comes out. Any idea on how to change this issue? My mic seems to be working, at least Skype shows reactions on the volume indicator. 

soundcard:HDA nVidia, Realtek ALC 662 rev1

Greets

Acradon

---

### Post by shaunehunter on 2009-11-09
After upgrading I had the issue with no sound and speaker pops as well. My machine has the Intel chip set that most of you have mentioned.

After checking that my hardware was recognized and proper diver loaded I ran alsamixer. It seemed the upgrade turned the volume of my left and right channels down. I cranked them back up and they are fine.

Give it a try, it's easy. I looked over a couple suggestions on these forums before that. They either didn't make sense to me or did nothing like when I tried the sleep mode edit.

If your card is recognized and has the right driver this is probably the way. 

This was my only glitch in my upgrade to karmic on two machines. Much better than earlier version upgrades.

---

### Post by joshua neff on 2009-11-10
I've got a Dell Inspiron 1420. After upgrading to Karmic, I get no sound at all, not from my speakers, not with headphones. I did a system test & reported a bug to Launchpad, but so far have gotten no response. I've used alsamixer & pushed the volume up to the max, but I still get no sound at all. I really don't know what else to do.

---

### Post by musarraf172 on 2009-11-11
> **joshua neff said:**
> I've got a Dell Inspiron 1420. After upgrading to Karmic, I get no sound at all, not from my speakers, not with headphones. I did a system test & reported a bug to Launchpad, but so far have gotten no response. I've used alsamixer & pushed the volume up to the max, but I still get no sound at all. I really don't know what else to do.

In which kernel u are booting? Check with "uname -r". If it is not 2.6.31-14 then audio will not work..

If you can not boot with 2.6.31-14 then u may have to do a fresh install..
In my IBM R51 upgrades were never smooth. I did a fresh install..

Good luck...:popcorn:

---

### Post by Lido on 2009-11-11
> **running_rabbit07 said:**
> If you made the /home partition, all of your config file will be safe.

Unfortunately I did not make a /home partition. I did make a /mythtv partition, but that won't help for anything but videos, music and recordings (and the recordings files might be useless without the mythconverge db etc.

---

### Post by joshua neff on 2009-11-11
> **musarraf172 said:**
> In which kernel u are booting? Check with "uname -r". If it is not 2.6.31-14 then audio will not work..

If you can not boot with 2.6.31-14 then u may have to do a fresh install..
In my IBM R51 upgrades were never smooth. I did a fresh install..

Good luck...:popcorn:

Yes, I'm booting with 2.6.31-14.

---

### Post by running_rabbit07 on 2009-11-11
> **Lido said:**
> Unfortunately I did not make a /home partition. I did make a /mythtv partition, but that won't help for anything but videos, music and recordings (and the recordings files might be useless without the mythconverge db etc.

Check out this[ link]("http://www.psychocats.net/ubuntu/separatehome"), it may be helpful to you.

---

### Post by StKunze on 2009-11-11
Not sure if this is the right place for this but here goes anyway...

I've just upgraded from 9.04 (worked great, no problems) to 9.10, and now have two key usability problems.

Now, I have no sound in any app (sound preferences shows no device in the hardware tab, though I didn't notice any errors at boot time)

And *everything* is slow (I completely uninstalled compiz, suspecting issues with display refresh primarily, but it made no difference). Screen refresh, application responses, everything. It could all be related to a display issue (but I'm mentioning it here in case it is related to the audio problem), but I can't tell (don't know where to start with that one!). Running Top doesn't show anything hogging the processor, and that's about as far as my technical knowledge goes. It's so slow, it's barely usable, especially switching workspaces where the screen takes between 10-20 seconds to refresh!

Any help or direction would be appreciated.

Oh yeah, it's a Toshiba Satellite, dual boot, and win xp still runs fine including sound.

---

### Post by elzorroviejo on 2009-11-14
Hi, I upgraded from Jaunty to Karmic a day after Karmic was released, and I had a number of issues. The most important (for me) was the lack of sound. I have called up the upgrade manager twice since then, and I did all the available upgrades. This has solved all but the sound issue as far as I can tell. When I turn the laptop on, I have no sound, but, if I go to the terminal and enter > sudo alsa force-reload, I get my sound back. Admittedly, this is a workaround that a typical Windows user will not be comfortable with, but it works for me (so far). 

I am running Karmic over 2.6.31-14 and it is the best Ubuntu yet. I can now watch video on the laptop (Gateway MX 8738) and the wireless connection is much stronger. Now all I have to do is learn how to network Linux boxes with a legacy XP desktop, and I'll be all set. As it is, I share files via Dropbox...also a workaround but it suffices. If and when the sound issue is fixed, I'll be blissfully happy!

---

### Post by SurferGTO on 2009-11-16
sadly i did not read this prior to upgrading, and during upgrade i opted to "keep the local version currently installed" of the menu.lst rather than "install the package maintainer's version" so now im running the older kernel rather than the correct current one. this is effecting my audio clearly, but its also effecting my graphics card apparently and i can not activate the nvidia drivers.

anyone know how i could upgrade the kernel or fix this problem?

---

### Post by rich1939 on 2009-11-16
I did a fresh install of Karmic, since the upgrade didn't work, and everything seems to work _except_ the sound.

In my case, the volume control at the top of the screen either provides no sound at all, or full volume. There is no in-between, regardless of the setting of the volume slider.

Any suggestions?

---

### Post by Magnesium on 2009-11-16
> **SurferGTO said:**
> sadly i did not read this prior to upgrading, and during upgrade i opted to "keep the local version currently installed" of the menu.lst rather than "install the package maintainer's version" so now im running the older kernel rather than the correct current one. this is effecting my audio clearly, but its also effecting my graphics card apparently and i can not activate the nvidia drivers.

anyone know how i could upgrade the kernel or fix this problem?

Hi there,

When you upgraded, the new kernel was most likely installed, but since you kept the old menu.lst, your computer is just not using it. If you want, you can just post your /boot/grub/menu.lst, and I can fix it for you.

Or if you'd rather, I can describe how to fix it...whichever you want.

Mg

---

### Post by SurferGTO on 2009-11-16
i would really appreciate it!! 

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro  single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.10, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, kernel 2.6.24-20-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro  single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro  single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.10, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro  single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b16b3065-ded8-4196-aac5-f380325a542b ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by SurferGTO on 2009-11-16
also, how can i get rid of the older kernels? i know someone said i can do it thru package manager, but does that remove the headers too?

---

### Post by Magnesium on 2009-11-16
> **SurferGTO said:**
> i would really appreciate it!!

Here you go my friend...first just check that you *do* have the new kernel...execute

```
ls /boot/vmlinuz*
```

and make sure that one of the files is named ```
/boot/vmlinuz-2.6.31-14-generic
```

If there is one there with that name, save the attached file somewhere on your computer (e.g., ~/Downloads), and then execute

```
sudo cp ~/Downloads/menu.txt /boot/grub/menu.lst
```

(Of course, if you save it somewhere different change the ~/Downloads/menu.lst part accordingly.)

Then reboot, make sure that the 2.6.31-14-generic entry is selected in grub, and you should be rockin' the new kernel! \\:D/ You can always check what kernel version you are running by executing
```
uname -r
```

Hope this helps,
Mg

P.S. In the future, if you want to post a long file like that, it's always better to do so as an attachment...posting it inline makes for a lot of scrolling for everyone...and sometimes the forum will render some things funny. Hence the 8) at the beginning of it in your post...or was that you being a cool Surfer Dude (or Girl)? ;)

---

### Post by SurferGTO on 2009-11-16
lmao ill keep that in mind about the attachment! isnt there a way to add a quote inside the post with scroll bars so it doesnt make the over all post longer???

back on topic: 

im showing:  /boot/vmlinuz-2.6.31-15-generic

not 14-generic...

---

### Post by Magnesium on 2009-11-16
> **SurferGTO said:**
> lmao ill keep that in mind about the attachment! isnt there a way to add a quote inside the post with scroll bars so it doesnt make the over all post longer???

back on topic: 

im showing:  /boot/vmlinuz-2.6.31-15-generic

not 14-generic...

Don't know about the scroll bars...there probably is, but I've never used it.

And you are on a little newer kernel than me...so use this menu.txt  with the same method as above...

Mg

---

### Post by SurferGTO on 2009-11-16
prolly stupid question, but if i have that file in my documents folder, what specifically do i type?? ~/Documents/menu.txt?

---

### Post by Magnesium on 2009-11-16
> **SurferGTO said:**
> prolly stupid question, but if i have that file in my documents folder, what specifically do i type?? ~/Documents/menu.txt?

You got it.

---

### Post by SurferGTO on 2009-11-16
> sudo cp ~/Documents/menu.txt /boot/grub/menu.lst
sudo: unable to resolve host master-laptop
[sudo] password for master: 


it then returns to terminal prompt after inputing the password and nothing happens....is something supposed to happen lol

---

### Post by Magnesium on 2009-11-17
> **SurferGTO said:**
> it then returns to terminal prompt after inputing the password and nothing happens....is something supposed to happen lol

Well, something did happen...the file I gave you overwrote your existing file. You just won't see anything in the terminal when that happens. You have to reboot to use the new kernel.

---

### Post by SurferGTO on 2009-11-17
black screen into nothingness after grub attempts to load. had grub go into safe mode for the newest kernel, didnt fix anything. loaded grub in old kernel, loads ok still with same old problems. unable to load current kernel...

---

### Post by Magnesium on 2009-11-17
> **SurferGTO said:**
> black screen into nothingness after grub attempts to load. had grub go into safe mode for the newest kernel, didnt fix anything. loaded grub in old kernel, loads ok still with same old problems. unable to load current kernel...

And if you press Escape, and select the new kernel, nothing happens at all? No error of any kind?

---

### Post by SurferGTO on 2009-11-17
if i allow it to boot on its own, it does the same thing as if i select the new kernel from the grub list after pressing escape. no error, nothing happens, just sits at a black screen. no mouse, no sounds, notta. i have to reboot and hit escape to select the older kernel

---

### Post by Magnesium on 2009-11-17
> **SurferGTO said:**
> if i allow it to boot on its own, it does the same thing as if i select the new kernel from the grub list after pressing escape. no error, nothing happens, just sits at a black screen. no mouse, no sounds, notta. i have to reboot and hit escape to select the older kernel

Hmmm...well then we've got a bigger problem here...if it couldn't find the kernel, it would have given you an error, but just a black screen...strange.

Something you might try is booting into your old kernel, and running

```
sudo update-initramfs -k 2.6.31-15-generic -c
```

and then

```
sudo update-initramfs -k 2.6.31-15-generic -u
```

This may help with your problem. But at the moment I'm off to sleep...it is late where I am.

Mg

---

### Post by SurferGTO on 2009-11-17
i ran it in recovery mode for the new kernel and its now booting to the newest version so thanks!!! that def. fixed the sound problem!!  

dont think its fixing the graphics card problem tho, but at least i have sound now!!!!

---

### Post by SurferGTO on 2009-11-17
fixed both sound and graphics card!! thanks so much!!

---

### Post by Magnesium on 2009-11-17
> **SurferGTO said:**
> fixed both sound and graphics card!! thanks so much!!
 
Hooray! :D I'm glad you got everything fixed.

---

### Post by thehud on 2009-11-20
@Magnesium: You mentioned using kernel version 2.6.31-15-generic - Where can we find this? Has it been released yet, because I can't find it in the repos.

Anyone else who can't see any hardware devices listed in Sound Preferences - Try deleting your ~/.pulse directory and ~/.pulse-cookie file. That should let the device get listed, but you'll likely still have the above popping / distortion issue.

Hud

[Edit]

I've ended up removing pulse and alsa, in favour of OSS - mostly followed [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound), restarted many times, and played copiously with settings of "ossxmix". Turning down PCM helped mainly, but not before I'd played and restarted once. Hope this helps someone.

---

### Post by Magnesium on 2009-11-20
> **thehud said:**
> @Magnesium: You mentioned using kernel version 2.6.31-15-generic - Where can we find this? Has it been released yet, because I can't find it in the repos.

Hud

Hey Hud,

Actually, I am running 2.6.31-14...it was SurferGTO, who I was helping out, that was running 15. I don't know how or where they got it from, but you're right...it's not in the standard repos. Perhaps he/she had some experimental repo activated.

SurferGTO, are you still listening? Do you know where you got this version of the kernel?

Mg

---

### Post by thehud on 2009-11-20
Not too much of a problem if not - I've fixed sound by using OSS - I have no specific requirements for Pulse. Shame about it though. It's always been a little funky anyway - before my upgrade none of the mixer channels did what they were labelled to do. Same again, but no distortion anymore. perhaps I can put pulse back over OSS one day, but for now, I have code and reports to write :-({|=

Ta for now

Hud

---

### Post by SurferGTO on 2009-11-20
hud, that is the new kernel installed with 9.10. so long as you opted to not use the existing menu.lst during the installation, it should be installed. if you chose to use the menu.lst currently on your machine, ubuntu installed 9.10 but loads the olders kernel at grub boot.

---

### Post by Magnesium on 2009-11-20
> **SurferGTO said:**
> hud, that is the new kernel installed with 9.10. so long as you opted to not use the existing menu.lst during the installation, it should be installed. if you chose to use the menu.lst currently on your machine, ubuntu installed 9.10 but loads the olders kernel at grub boot.

Hey again my surfer friend...the deal is that both Hud and I got 2.6.31-14 on our Karmic installs, while you got 2.6.31-15.

There must be some difference between our installations then. I am using the 64-bit version of Kubuntu, and I upgraded from Jaunty. How about y'all?

Mg

---

### Post by SurferGTO on 2009-11-20
well. when this thread started, i was running off an upgrade from jaunty, i have no idea how i had 15. i have just recently did a fresh install of Intrepid then upgraded up to Karmic and im now running 14?? no clue how that happend. (I did a fresh install after having problems with Cairo-Dock post upgrade)

Everything works smooooooth now...

---

### Post by Magnesium on 2009-11-20
> **SurferGTO said:**
> well. when this thread started, i was running off an upgrade from jaunty, i have no idea how i had 15. i have just recently did a fresh install of Intrepid then upgraded up to Karmic and im now running 14?? no clue how that happend. (I did a fresh install after having problems with Cairo-Dock post upgrade)

Everything works smooooooth now...

Very strange...I just talked to another 32-bit upgrader on IRC, who had the 14 revision.

I have no idea at all how you got the 15 version. Heck, maybe that was the source of your problem! Some stray cosmic ray changed it from 14 to 15.... :-k

---

### Post by musarraf172 on 2009-11-21
> **thehud said:**
> @Magnesium: You mentioned using kernel version 2.6.31-15-generic - Where can we find this? Has it been released yet, because I can't find it in the repos.

Anyone else who can't see any hardware devices listed in Sound Preferences - Try deleting your ~/.pulse directory and ~/.pulse-cookie file. That should let the device get listed, but you'll likely still have the above popping / distortion issue.

Hud

[Edit]

I've ended up removing pulse and alsa, in favour of OSS - mostly followed [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound), restarted many times, and played copiously with settings of "ossxmix". Turning down PCM helped mainly, but not before I'd played and restarted once. Hope this helps someone.




Just enable the " Proposed update for KK" in your Software sources.

---

### Post by thehud on 2009-11-21
Ahh! I knew it existed... [http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html](http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html). Thanks musarraf, although I'll probably wait for it to land in the recommended updates. If it 'aint broke (too badly)...

---

### Post by Magnesium on 2009-11-21
> **thehud said:**
> Ahh! I knew it existed... [http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html](http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html). Thanks musarraf, although I'll probably wait for it to land in the recommended updates. If it 'aint broke (too badly)...

I'm glad you found that...I also had a gut feeling that something like that must have existed. The question now is, how come SurferGTO's installation had that repo enabled, after a fresh installation? :???:

Mg

---

### Post by SurferGTO on 2009-11-21
yes very confusing, as far as i recall i didnt do anything out of the norm as far as upgrading went. 

like i said tho it seems that a lot of people are using the older kernel and that is the source of most of their problems. after my fresh install from CD, and upgraded my way up, no problems at all now (none that i want to hijack this post with).

---

### Post by thehud on 2009-11-21
Perhaps you had proposed updates enabled from your Jaunty install, as musarraf mentioned? Seems the most likely explanation. Whoever else lands here with this problem - try enabling proposed and install the new kernel.

---

### Post by Eyore15 on 2009-11-21
Let me start by saying I'm relatively new to Ubuntu.  I AM NOT a power user.

Like just about everyone else it seems, I have no sound after doing the upgrade to 9.10.  I've read through all 80 replies to this thread and a bunch of other stuff after google searches, and most every thing is over my head. For example, I have no idea how to implement suggestions dealing with things like use a different kernel. 

I know next to nothing about working with the CLI.

Is there some place I haven't looked yet where there are some "entry level" instructions on what to do to get sound back?  I'm looking for something written in non-tech speak, perhaps a simple check list of instructions pulled together in one place? 

Thanks in advance for bailing me out.  I kinda miss watching Hulu; even miss You-Tube.

Regards

mcm

---

### Post by thehud on 2009-11-21
I know there's a bunch of general info aimed at new users, but I've never really read it and can't point you towards that. However, if some of the above mentions of kernels fixing the problem are correct, maybe this will help. (Naively, the kernel is like the master program that makes the whole of Ubuntu work)

[LIST]
[*]In the main menu, click Applications => Accessories => Terminal.
[/LIST]

[LIST]
[*]When it opens, type "uname -r" and press enter. It will say something like "2.6.31-14-generic", but the 31 and 14 could be different.
[/LIST]
If it does not start "2.6.31..." you probably have the older kernel. If it starts "2.6.31-14" then there is also a newer kernel you can try to use, by doing the following:

[LIST]
[*]In the main menu, click System => Administration => Software Sources, and enter your password when asked.
[*]When it opens, click the Updates tab at the top of the window, and select the check box that has the text "Proposed updates (karmic-proposed)" next to it.
[/LIST]

[LIST]
[*]You should then be prompted to Reload the information about software. Do this, and...
[*]When it is complete, go back to the menu, and navigate to System => Administration => Update Manager. When it opens, click Install Updates.
[/LIST]
This list of updates contains the updated kernel mentioned above, and will hopefully solve your problem. If not - come right back here and see if we can do anything else.

Ta, Hud.

[Edit:] Don't forget to re-start your computer when the updates prompt you to!

---

### Post by Eyore15 on 2009-11-21
> **thehud said:**
> I know there's a bunch of general info aimed at new users, but I've never really read it and can't point you towards that. However, if some of the above mentions of kernels fixing the problem are correct, maybe this will help. (Naively, the kernel is like the master program that makes the whole of Ubuntu work)

[LIST]
[*]In the main menu, click Applications => Accessories => Terminal.
[/LIST]

[LIST]
[*]When it opens, type "uname -r" and press enter. It will say something like "2.6.31-14-generic", but the 31 and 14 could be different.
[/LIST]
If it does not start "2.6.31..." you probably have the older kernel. If it starts "2.6.31-14" then there is also a newer kernel you can try to use, by doing the following:

[LIST]
[*]In the main menu, click System => Administration => Software Sources, and enter your password when asked.
[*]When it opens, click the Updates tab at the top of the window, and select the check box that has the text "Proposed updates (karmic-proposed)" next to it.
[/LIST]

[LIST]
[*]You should then be prompted to Reload the information about software. Do this, and...
[*]When it is complete, go back to the menu, and navigate to System => Administration => Update Manager. When it opens, click Install Updates.
[/LIST]
This list of updates contains the updated kernel mentioned above, and will hopefully solve your problem. If not - come right back here and see if we can do anything else.

Ta, Hud.

[Edit:] Don't forget to re-start your computer when the updates prompt you to!

Well, I took all those (very painless) steps, but to no avail.  Still no audio.  Got another set of instructions I can try?  The system I am working with is an HP Compaq P4 3.0 HT with 1 gig of RAM.

thnx

mcm

---

### Post by thehud on 2009-11-21
Not many I'm afraid, you could try typing this in the terminal:

[LIST]
[*]"rm -r ~/.pulse ~/.pulse-cookie"
[/LIST]
I did have a problem with my old Pulse audio configuration after I upgraded. (Pulse is the application that deals with sound, in a round about sort of way). It first gave me no sound, then after this, I got some sound out of it, albeit rather distorted.

Someone else might be able to help if they know more about your system - specifically your sound card. To get this, try pasting the following into the terminal:

[LIST]
[*]"lspci | grep audio"
[/LIST]
and post the info back. I imagine only a selection of sound cards are playing up, and this might help anyone more familiar with the problem.

Also, it's probably worth double checking all speaker connections, and opening the volume control (System => Preferences => Volume Control) and ensuring nothing is turned way down or muted.

---

### Post by Eyore15 on 2009-11-21
> **thehud said:**
> Not many I'm afraid, you could try typing this in the terminal:

[LIST]
[*]"rm -r ~/.pulse ~/.pulse-cookie"
[/LIST]
I did have a problem with my old Pulse audio configuration after I upgraded. (Pulse is the application that deals with sound, in a round about sort of way). It first gave me no sound, then after this, I got some sound out of it, albeit rather distorted.

Someone else might be able to help if they know more about your system - specifically your sound card. To get this, try pasting the following into the terminal:

[LIST]
[*]"lspci | grep audio"
[/LIST]
and post the info back. I imagine only a selection of sound cards are playing up, and this might help anyone more familiar with the problem.

Also, it's probably worth double checking all speaker connections, and opening the volume control (System => Preferences => Volume Control) and ensuring nothing is turned way down or muted.

Still no luck ...

I deleted the .pulse and .pulse-cookie file as instructed.

Here's the results of the lspci | grep audio command:

eyore15@eyore:~$ lspci | grep audio
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

Nothing is muted anywhere,double checked "system" "preferences" "sound", and didn't get any kind of a prompt.  A "starting sound" box opened on the bottom panel, but that was it.  It closed out in about 30 seconds.

I'm working with the internal speaker on the box.  It worked just fine in 9.04.

Thanks for your suggestions.

Thanks in advance for any additional suggestions.

mcm

---

### Post by thehud on 2009-11-21
I think I'm all out. All I can say is try plugging speakers or headphones into the various speaker ports, front / back and see what you can hear while you've got something playing audio, like MPlayer. I wouldn't hold your breath though.

You could search on launchpad ([https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)) to see if anyone has posted a bug similar to yours? If so, there might be more info there. If you do find anything, could you post a link(s) back here?

Sorry you're still in silence :(

Hud

---

### Post by HeadHunter00 on 2009-11-22
download pulseaudio equalizer from this thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Magnesium on 2009-11-22
> **Eyore15 said:**
> Still no luck ...

I deleted the .pulse and .pulse-cookie file as instructed.

Here's the results of the lspci | grep audio command:

eyore15@eyore:~$ lspci | grep audio
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

Nothing is muted anywhere,double checked "system" "preferences" "sound", and didn't get any kind of a prompt.  A "starting sound" box opened on the bottom panel, but that was it.  It closed out in about 30 seconds.

I'm working with the internal speaker on the box.  It worked just fine in 9.04.

Thanks for your suggestions.

Thanks in advance for any additional suggestions.

mcm

Hey Eyore,

Couple of things to try:

In your terminal, run ```
alsamixer
``` and make sure that all the bars are all the way up (use your left/right arrow keys to move between bars, and up to increase them).

If that doesn't work, in your terminal, try running ```
speaker-test
``` Tell us if you hear anything, and post the output of the command.

Finally, several links that people have found useful...YMMV though:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) (This is written for Jaunty, but some folks have said that it helped them.)

[*][http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html) (A good overview...also for Jaunty, but perhaps still applicable.)

[*][http://blog.christophersmart.com/2009/11/09/karmic-upgrade-broken-sound-work-around/](http://blog.christophersmart.com/2009/11/09/karmic-upgrade-broken-sound-work-around/) (Very much a workaround here)

[*][https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/411574?comments=all](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/411574?comments=all) (This card seems quite similar to yours...most is just bug reports, but some of the comments have solutions...e.g., runnning sudo alsa force-reload)
[/LIST]

Mg

---

### Post by Syncan on 2009-11-23
Hi, I have read all of this and I too have no sound since installing the kernel 10 version.
I tried what theHud proposed:
> 
[LIST]
[*]In the main menu, click Applications => Accessories => Terminal.
[/LIST]

[LIST]
[*]When it opens, type "uname -r" and press enter. It will say something like "2.6.31-14-generic", but the 31 and 14 could be different.
[/LIST]
If it does not start "2.6.31..." you probably have the older kernel. If it starts "2.6.31-14" then there is also a newer kernel you can try to use, by doing the following:

[LIST]
[*]In the main menu, click System => Administration => Software Sources, and enter your password when asked.
[*]When it opens, click the Updates tab at the top of the window, and select the check box that has the text "Proposed updates (karmic-proposed)" next to it.
[/LIST]

[LIST]
[*]You should then be prompted to Reload the information about software. Do this, and...
[*]When it is complete, go back to the menu, and navigate to System => Administration => Update Manager. When it opens, click Install Updates.
[/LIST]
but all my updates were already installed.
At uname -r it returns:
2.6.28-15-generic

I have to say that during the upgrade 2 or 3 times the question was if I wanted to keep menu-lst and I choosed to do so.

I also tried what Magnesium said about Alsamixer and I got this as output:
> alsamixer: function snd_ctl_open failed for default: No such file or directory
  Speaker-test returned this:
> speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 28,348528
 0 - Front Left
Time per period = 28,350966
 0 - Front Left
Time per period = 28,350445
 0 - Front Left
Time per period = 28,349930
 0 - Front Left
Time per period = 28,350091
 0 - Front Left
Time per period = 28,349521
 0 - Front Left
Time per period = 28,351412
 0 - Front Left
Time per period = 28,348566
 0 - Front Left
Time per period = 28,350316
 0 - Front Left
Time per period = 28,350039
 0 - Front Left
Time per period = 28,351367
 0 - Front Left
Time per period = 28,349185
 0 - Front Left
Time per period = 28,348874

I did not hear any sound.

In the sound-preferences at the right-top of my desktop the output said: 
> Dummy output
StereoI have on-board sound chip on my asus P5B-E mobo: ADI 1988 8 channel High Definition Audio CODEC which is probably not found.

I have the feeling something is wrong ;)
Can somebody help me out? Like eyeore15 I am NOT a power-user, more a beginner, so hopefully you guys can tell me in simple words what to do....

---

### Post by Magnesium on 2009-11-23
Hey there Syncan,

You've got the exact problem I did when I upgraded to Karmic, and a very similar problem to my surfer friend earlier. Here's what's going on: first of all, 

> **Syncan said:**
> 
At uname -r it returns:
2.6.28-15-generic

I have to say that during the upgrade 2 or 3 times the question was if I wanted to keep menu-lst and I choosed to do so.


2.6.28 is the old (Jaunty) kernel...Karmic uses 2.6.31. When you upgraded, it installed the new kernel, but what's happening is that Ubuntu isn't *using* it; it's booting into the old kernel because you kept the old menu.lst. Here's how I can help: if you can post (as an attachment) the file "/boot/grub/menu.lst", I can fix it for you, and then you should be able to boot into the new kernel!

Also, just to make sure, can you post the output of

```
ls -al /boot/vmlinuz-2.6.31*
```

as well?

> **Syncan said:**
> 
I also tried what Magnesium said about Alsamixer and I got this as output:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```


This is basically telling you that since you are using the old kernel, Linux can't find your sound card...the "file or directory" it's referring to is the virtual file "/dev/dsp" (the /dev/ directory contains all the virtual files for each piece of hardware on your system).

Mg

---

### Post by thehud on 2009-11-23
Sorry - I completely overlooked actually ensuring the new kernel is used. :$

You might also like to try HeadHunters solution. I had a read, and it looks well written and quite easy to follow, but haven't tried it personally.

> **HeadHunter00 said:**
> download pulseaudio equalizer from this thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

But definitely post your menu.lst for Mg.

---

### Post by smeuse on 2009-11-25
FWIW, after the 9.10 upgrade I had the squishy, undersampled, audio issue. I found that if I changed my settings in System->Preferences->Sound->Hardware to "Analog Surround 7.1 Output" the issue went away (even though I'm only using 5.1). 

I'm using an Intel HDA card on a Dell Studio XPS 435. 

smeuse@dalek:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf73f8000 irq 22

---

### Post by Syncan on 2009-11-26
> **Magnesium said:**
> Hey there Syncan,

You've got the exact problem I did when I upgraded to Karmic, and a very similar problem to my surfer friend earlier. Here's what's going on: first of all, 



2.6.28 is the old (Jaunty) kernel...Karmic uses 2.6.31. When you upgraded, it installed the new kernel, but what's happening is that Ubuntu isn't *using* it; it's booting into the old kernel because you kept the old menu.lst. Here's how I can help: if you can post (as an attachment) the file "/boot/grub/menu.lst", I can fix it for you, and then you should be able to boot into the new kernel!

Also, just to make sure, can you post the output of

```
ls -al /boot/vmlinuz-2.6.31*
```as well?



This is basically telling you that since you are using the old kernel, Linux can't find your sound card...the "file or directory" it's referring to is the virtual file "/dev/dsp" (the /dev/ directory contains all the virtual files for each piece of hardware on your system).

Mg

Thanks, sorry for not posting my reply soon enough but I got the flu and was unable to do this. I will take a look this afternoon and posting my answers/next questions then :)

---

### Post by Syncan on 2009-11-26
Okay Magnesium, 

Here is the output from the ls -al command you asked:
ls -al /boot/vmlinuz-2.6.31*
-rw-r--r-- 1 root root 3890400 2009-10-16 20:03 /boot/vmlinuz-2.6.31-14-generic
-rw-r--r-- 1 root root 3892224 2009-11-10 19:52 /boot/vmlinuz-2.6.31-15-generic

I also added the /boot/grub/menu.lst in this post.
I renamed it to menu.txt to get it uploaded to the forum.

Thanks in advance ;)

---

### Post by Robertjm on 2009-11-26
For all those wondering about the -15 kernel, it appeared in my Synaptic Upgrade manager just yesterday sometime so you might want to check for updates if you've been waiting for that.

There were some notes of problems after people upgrading, but I checked today and haven't seen any new ones today. Perhaps good news?

Later,

Robert

---

### Post by tips72 on 2009-11-26
I have tried every suggestion in this thread and a dozen other threads trying to get my sound back. I gave up on 9.10 and went back to 9.0.4, all audio function correctly now. I backed up my files then used a 9.0.4 installation disk to boot into demo mode and verified that solved the audio bug and installed from there and selecting to remove 9.10.

---

### Post by zbrukas on 2009-11-27
Hi to all.

Tried everything in this list. But my problem is a bit different.

Besides audio doesnt work, my audio/video apps don't initialize... tried every one of them... songbird, rhythmbox, totem, mplayer... 

i'm using karmic upgrade, the latest kernel, alsa is working (i've made a test, alsamixer sounds great, played the test sounds in the preferences >> sound tab), it's not muted =), pulseaudio seems like working too...

thanks in advance for your time... really going nutz without music

EDIT: sound works on firefox (what the...?)

EDIT2: alsaplayer plays music... --" but i still can't open all media players...

EDIT3: made a clean install... it's not worth the time... at the same time erasaed all the s**t i did when i installed it a year ago for the first time =) thanks for your time btw

---

### Post by Magnesium on 2009-11-27
> **Syncan said:**
> Okay Magnesium, 

Here is the output from the ls -al command you asked:
ls -al /boot/vmlinuz-2.6.31*
-rw-r--r-- 1 root root 3890400 2009-10-16 20:03 /boot/vmlinuz-2.6.31-14-generic
-rw-r--r-- 1 root root 3892224 2009-11-10 19:52 /boot/vmlinuz-2.6.31-15-generic

I also added the /boot/grub/menu.lst in this post.
I renamed it to menu.txt to get it uploaded to the forum.

Thanks in advance ;)

So now it's my turn to apologize about not getting back sooner...I was waiting for a notification email about your second post, but since I didn't visit the forum after your first one, it never came ! #-o

Anyway, attached is a new menu.txt...save it somewhere on your computer (e.g., ~/Downloads), and then execute

```

sudo cp ~/Downloads/menu.txt /boot/grub/menu.lst

```

(Of course, if you save it somewhere different change the ~/Downloads/menu.lst part accordingly.) Then reboot and make sure that the 2.6.31-15-generic entry is selected in grub, and you'll be good to go, I hope! :D

Post back about how it goes.

Mg

---

### Post by Magnesium on 2009-11-27
> **Robertjm said:**
> For all those wondering about the -15 kernel, it appeared in my Synaptic Upgrade manager just yesterday sometime so you might want to check for updates if you've been waiting for that.

There were some notes of problems after people upgrading, but I checked today and haven't seen any new ones today. Perhaps good news?

Later,

Robert

Yep, I got upgraded also. I think that earlier SurferGTO had been on the "proposed updates" repo, which is why he got it earlier than everyone else. But now it's in the official repos.

Mg

---

### Post by Syncan on 2009-11-28
> **Magnesium said:**
> So now it's my turn to apologize about not getting back sooner...I was waiting for a notification email about your second post, but since I didn't visit the forum after your first one, it never came ! #-o

Anyway, attached is a new menu.txt...save it somewhere on your computer (e.g., ~/Downloads), and then execute

```

sudo cp ~/Downloads/menu.txt /boot/grub/menu.lst

```(Of course, if you save it somewhere different change the ~/Downloads/menu.lst part accordingly.) Then reboot and make sure that the 2.6.31-15-generic entry is selected in grub, and you'll be good to go, I hope! :D

Post back about how it goes.

Mg

Hi Magnesium,

Sorry, but I made a blunder a day ago. I lost grub boot loader and was unable to boot linux again :(
I decided to clean-install with Linux 9.10.
The problem now is that there is no menu.lst anymore in this version!  I was forced to install boot-manager ( opstart-manager in Dutch ) and create the boot-order.

So now I think installing menu.lst will be useless, as menu.lst is not used anymore.

After clean install, Ubuntu 9.10 ( 2.6.31.15 ) still has no sound :(
Please can you help me out again? Thank you.

---

### Post by jean noel on 2009-11-29
I don't know if this may help, but i get the idea that 9.10 is too clever. 
Upon fresh installation, i got loud clicking noise in my speakers (creative 4.1 on soundblaster audigy zs). 
I the found the problem to be in => system =>preferences => sound. I then chose the adequate setting in profile.
The sound now is absolutely perfect, even better that 9.04.
Hope this helps.

---

### Post by Syncan on 2009-11-29
Yes! It works :D
Only question is what hardware setting is best....

Under hardware I have more choice: My setting now says:
Internel sound, one output, 1 input, Analog Stereo Duplex.

My sound comes from asus P5B-E mobo: ADI 1988 8 channel High Definition Audio CODEC. So it is a soundchip on-board from my motherboard.
Anyone who can tell what the best setting is for this chip?

---

### Post by Magnesium on 2009-11-29
> **Syncan]Hi Magnesium,

Sorry, but I made a blunder a day ago. I lost grub boot loader and was unable to boot linux again 
I decided to clean-install with Linux 9.10.
The problem now is that there is no menu.lst anymore in this version! I was forced to install boot-manager ( opstart-manager in Dutch ) and create the boot-order.

So now I think installing menu.lst will be useless, as menu.lst is not used anymore.

After clean install, Ubuntu 9.10 ( 2.6.31.15 ) still has no sound 
Please can you help me out again? Thank you.[/QUOTE]

[QUOTE=Syncan said:**
> Yes! It works :D
Only question is what hardware setting is best....

Under hardware I have more choice: My setting now says:
Internel sound, one output, 1 input, Analog Stereo Duplex.

My sound comes from asus P5B-E mobo: ADI 1988 8 channel High Definition Audio CODEC. So it is a soundchip on-board from my motherboard.
Anyone who can tell what the best setting is for this chip?

Hi Syncan,

I had Thanksgiving with my family yesterday, so I couldn't get back to you quickly...but it looks like with Jean's help you've got sound now! Better start \\:D/ to the music...

You're right, starting with clean installs of Karmic, we are using Grub2, which replaces the menu.lst with grub.cfg. But you shouldn't modify that one manually, there is a tool to use to modify it. If you want, you can read about it [here]("https://wiki.ubuntu.com/Grub2").

I'm not sure exactly what you meant by your last post...do you have multiple entries like

[LIST]
[*]ADI 1988 8 channel High Definition Audio
[*]PulseAudio
[*]etc.
[/LIST]

or something? I just don't quite understand what your screen looks like.

Basically though, my suggestion is: if you are not having any problems, you can just leave it alone. After all, *[COLOR="Green"]if it ain't broke, don't fix it![/COLOR]* ;)

Mg

---

### Post by Syncan on 2009-12-01
> **Magnesium said:**
> Hi Syncan,

I had Thanksgiving with my family yesterday, so I couldn't get back to you quickly...but it looks like with Jean's help you've got sound now! Better start \\:D/ to the music...

You're right, starting with clean installs of Karmic, we are using Grub2, which replaces the menu.lst with grub.cfg. But you shouldn't modify that one manually, there is a tool to use to modify it. If you want, you can read about it [here]("https://wiki.ubuntu.com/Grub2").

I'm not sure exactly what you meant by your last post...do you have multiple entries like

[LIST]
[*]ADI 1988 8 channel High Definition Audio
[*]PulseAudio
[*]etc.
[/LIST]

or something? I just don't quite understand what your screen looks like.

Basically though, my suggestion is: if you are not having any problems, you can just leave it alone. After all, *[COLOR=Green]if it ain't broke, don't fix it![/COLOR]* ;)

Mg
I was trying to say that I have multiple hardware-profiles, varying from Analog surround output 7.1 ( and other versions, like 5.1 ) until digital stereo duplex .
In all there are 23 settings....
But I agree with you... it works fine now so maybe no need to change it again :)

---

### Post by Magnesium on 2009-12-01
> **Syncan said:**
> I was trying to say that I have multiple hardware-profiles, varying from Analog surround output 7.1 ( and other versions, like 5.1 ) until digital stereo duplex .
In all there are 23 settings....
But I agree with you... it works fine now so maybe no need to change it again :)

Alright, I see. I thought you were referring to something different.

What physical speakers do you have connected to your computer? That is, do you have a surround sound system (with 4 to 8 speakers), or just 2 speakers? Just pick which setting matches your set up. (If you are using speakers in your monitor or something, pick the stereo setting.)

Mg

---

### Post by Syncan on 2009-12-01
> **Magnesium said:**
> Alright, I see. I thought you were referring to something different.

What physical speakers do you have connected to your computer? That is, do you have a surround sound system (with 4 to 8 speakers), or just 2 speakers? Just pick which setting matches your set up. (If you are using speakers in your monitor or something, pick the stereo setting.)

Mg
Okay, thank you again :)

---

### Post by Magnesium on 2009-12-04
> **Magnesium said:**
> What physical speakers do you have connected to your computer? That is, do you have a surround sound system (with 4 to 8 speakers), or just 2 speakers? Just pick which setting matches your set up. (If you are using speakers in your monitor or something, pick the stereo setting.)

Mg

> **thudsjhsj said:**
> What physical speakers do you have connected to your computer? That is, do you have a surround sound system (with 4 to 8 speakers), or just 2 speakers? Just pick which setting matches your set up. (If you are using speakers in your monitor or something, pick the stereo setting.)
_____________________
[COLOR=#000000][FONT=Times New Roman][FONT=Arial]**[SIZE=2][**[URL="http://comparatifmutuelle.org/%5DDevis"]**[SIZE=2]http://comparatifmutuelle.org/]Devis[/SIZE]**]([/SIZE)**[SIZE=2] comparatif mutuelle sante | [/url][**[URL="http://comparatifmutuelle.org/%5DComparateur"]**[SIZE=2]http://comparatifmutuelle.org/]Comparateur[/SIZE]**]([/SIZE)**[SIZE=2] mutuelles sante | [/url][**[URL="http://comparatifmutuelle.org/%5DComparer"]**[SIZE=2]http://comparatifmutuelle.org/]Comparer[/SIZE]**]([/SIZE)**[SIZE=2] comparatif mutuel[/url][/SIZE]**[/FONT][/FONT][/COLOR]

I see similarities here, and a rather strange sig and username...what's going on with thudsjhsj? (Looks kinda like spam, IMHO).

Mg

---

### Post by eryngium on 2009-12-08
Lost Sound

I am completely baffled. Had full sound and video playback. When booting a pop-up informed me of a problem. Something to do with something. I dunno. Now I don't have the usual functionality in the top panel.

Top right, should show user logged in (me) and icons for sound, ethernet etc. I thought this might have been because I uninstalled Empathy and Evolution (noticed that Ubuntu-desktop was missing in Synaptic and re-installed,[no joy there]).

Any suggestions welcome.


[Aside: I'm not impressed with the rigid adherence to a 6 month release schedule if the package is not ready, glum]

---

### Post by phishbone on 2009-12-11
Updated karmic this morning and lost all sounds. My sound have been working since 8.04 without any problems at all but after todays update the speakers are dead... sound shows as active in pavucontrol and alsamixer but the speakers... dead.. :(

I have no clue what to do.

VIA vt82xx sound.

Any advice!?

:cry:

---

### Post by Magnesium on 2009-12-11
> **phishbone said:**
> Updated karmic this morning and lost all sounds. My sound have been working since 8.04 without any problems at all but after todays update the speakers are dead... sound shows as active in pavucontrol and alsamixer but the speakers... dead.. :(

I have no clue what to do.

VIA vt82xx sound.

Any advice!?

:cry:

Hmm...let's try the steps that have helped the others. Can you post the output from ```
uname -r
```

---

### Post by phishbone on 2009-12-12
kernel is 2.6.31-16-generic

---

### Post by Magnesium on 2009-12-12
> **phishbone said:**
> kernel is 2.6.31-16-generic

OK, so you're using the new kernel already...that's been the problem for a lot of people here, and the solution has been to just add the necessary lines to menu.lst.

Can you run ```
speaker-test
``` and tell us if you hear any sound, and also post the output? Also, can you post the output of ```
lspci | grep audio
``` (or ```
lspci | grep Audio
``` if you don't get anything from the lowercase one) and the output of ```
sudo lshw -class multimedia
``` We'll see if we can get this figured out.:)

Mg

---

### Post by phishbone on 2009-12-12
> **Magnesium said:**
> OK, so you're using the new kernel already...that's been the problem for a lot of people here, and the solution has been to just add the necessary lines to menu.lst.

Can you run ```
speaker-test
``` and tell us if you hear any sound, and also post the output? Also, can you post the output of ```
lspci | grep audio
``` (or ```
lspci | grep Audio
``` if you don't get anything from the lowercase one) and the output of ```
sudo lshw -class multimedia
``` We'll see if we can get this figured out.:)

Mg

Thanks for taking your time but i wiped the root parition and installed a new system with my old home partition and now its working splendid... i guess it was time to do that because ive been upgrading since 7.xx :)

---

### Post by ojosunday2 on 2009-12-12
I have similar issue and I have gone through few of the steps illustrated in this thread to no avail. I will indeed appreciate getting someone helping out with this sound issue resulting from upgrade to 9.10 from 9.4

---

### Post by Magnesium on 2009-12-14
> **ojosunday2 said:**
> I have similar issue and I have gone through few of the steps illustrated in this thread to no avail. I will indeed appreciate getting someone helping out with this sound issue resulting from upgrade to 9.10 from 9.4

Can you give us some more info? If you could post the output of the following commands, we can try to help:

```
uname -r
```

```
speaker-test
```
Do you hear any sound (static/white noise) with the speaker-test command?

```
lspci | grep audio
```
(or
```
lspci | grep Audio
```
if you don't get anything from the lowercase one.)

Finally,
```
sudo lshw -class multimedia
```

You might need to install lshw for this one:

```
sudo apt-get update && sudo apt-get install lshw -y
```

Mg

---

### Post by pwishney on 2009-12-15
Hi-
I also have 2.6.31-16, so I ran the same tests you recommended above.  I have attached a file with the results of the tests.  The speaker test did produce sounds.

I get sound from everything but when I play a DVD.  I get the video, but not the audio.

Hope you can help.

Thank you:KS

---

### Post by pwishney on 2009-12-17
:KS
Hi-
I've just solved my problem.

Thanks anyway.

---

### Post by Magnesium on 2009-12-17
> **pwishney said:**
> :KS
Hi-
I've just solved my problem.

Thanks anyway.
:popcorn:

I'm glad you've fixed it...once I saw it was just DVD playback, I didn't think it was too serious, but you had already fixed it by the time I could reply.

Could you share how you fixed your problem so that other people who come here for help can try your method?

Mg

---

### Post by grokk on 2009-12-20
Just two glitches in my upgrade to 9.10

1. No sound -  had to use alsamixer to unmute my SPDIF sound as the upgrade had muted it.

2. No DNS - I could ping sites IP's but not open webpages unless I browsed to the IP address.   Not sure why this happened but I just added my ISP's DNS into a manual IPV4 configuration, and was back to normal straight away.

Other than that its fully functional and the upgrade was much quicker than setting up the box again after a clean install.

---

### Post by phishbone on 2009-12-25
I have problems with gaming and VT1708/A [Azalia HDAC] onboard sound. I can play games for a few minutes then it starts to sound weird from the hdd drive and the games run really slow. The sound from the hdd and the slow framerates wears off if i change sound profile from duplex to stereo but starts again after a few mins. Theres nothing taking resources, the hdd drive is two days old and this only happends when i upgrade to 9.10. Never had any problems with this before!

Does anyone know what i can do to fix this? Ive digged thru the forums but found no sollution...

---

### Post by paragonconcept on 2009-12-27
This is what i get after updating to 9.04 from 8.10 

> jackmurphy@boxee:/boot$ speaker-test

speaker-test 1.0.22

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory

---

### Post by joshua neff on 2010-01-01
Hi, I'm still having problems with my sound. Ran a speaker test & heard nothing. The results from

```
lspci | grep Audio
```

are: 

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

The results from 

```
sudo lshw -class multimedia
```

are:

description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:21 memory:fe9fc000-fe9fffff

Does that tell anyone anything? What should I do now?

---

### Post by Magnesium on 2010-01-02
> **joshua neff said:**
> Hi, I'm still having problems with my sound. Ran a speaker test & heard nothing. The results from

```
lspci | grep Audio
```

are: 

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

The results from 

```
sudo lshw -class multimedia
```

are:

description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:21 memory:fe9fc000-fe9fffff

Does that tell anyone anything? What should I do now?

Joshua, the only things I can suggest are: make sure```
uname -r
```returns something starting with 2.6.31, not 2.6.28. If you get something starting with 2.6.31, try running```
alsamixer
```in terminal and making sure all the sliders are up (keep pressing the right arrow key past the right edge, sometimes there are more sliders you can't see). If *that* doesn't work, you can try installing the alsa backports:```
sudo apt-get update && sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

Mg

EDIT: Wait, you are on Karmic, right? Your profile still shows you are on Edgy...if you are on Edgy, then I would suggest you upgrade ;). Otherwise, you should maybe change that in your profile....

---

### Post by joshua neff on 2010-01-02
Thanks for reminding me to change my profile. :P Yes, I'm using Karmic. It was upgrading to Karmic that killed my sound.

I'm definitely using 2.6.31. I tried everything you said, but I still have no sound. Rats!

> **Magnesium said:**
> Joshua, the only things I can suggest are: make sure```
uname -r
```returns something starting with 2.6.31, not 2.6.28. If you get something starting with 2.6.31, try running```
alsamixer
```in terminal and making sure all the sliders are up (keep pressing the right arrow key past the right edge, sometimes there are more sliders you can't see). If *that* doesn't work, you can try installing the alsa backports:```
sudo apt-get update && sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

Mg

EDIT: Wait, you are on Karmic, right? Your profile still shows you are on Edgy...if you are on Edgy, then I would suggest you upgrade ;). Otherwise, you should maybe change that in your profile....

---

### Post by fjleal on 2010-01-04
> **joshua neff said:**
> Thanks for reminding me to change my profile. :P Yes, I'm using Karmic. It was upgrading to Karmic that killed my sound.

I'm definitely using 2.6.31. I tried everything you said, but I still have no sound. Rats!

Similar issue here, card is "Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)". After logging in, I must do "sudo alsa force-reload" -- Gnome volume application gets killed, it restarts, "speaker-test" can then produce noise and sound works fine. But only after reloading alsa, every since time the machine boots... :(

---

### Post by howl at the moon on 2010-01-10
> **ColJep said:**
> I read some other suggestions and ended up running the audio tests in System > Admin > System Testing. This suggested reporting a bug which I did and soon had a suggestion to install linux-backports-modules-alsa-karmic-generic and reboot.

This I did and now Alsamixer works and I have very good sound.
Thanks!!  Perfect - I've suffered for 2months with no sound - now I can't decide if I want to stream my fave radio station or listen to my collection....

---

### Post by SR_ELPIRATA on 2010-01-16
Hey Mag, think you can help me?

I did a clean install. I have sound but as an added bonus I got a screechy sound that keeps going on no matter the volume. I have an ATI onboard audio (Asus M3A78-T) and I'm using the analogs. I read in a thread that if I changed from 5.1 to 7.1 (which is what I really have hardware wise) then the sound would be eliminated but.... I got no 7.1 option.

9.04 and 8.10 detected my soundcard as HDA-ATI-SB but in 9.10 Im now HDA-Intel. Im guessing this is the problem but I have no idea how to force the driver. I tried also the linux-backports thing but as it was mentioned... it is not a fix for my sound card.

I keep looking around on how to force the driver back to HDA-ATI-SB but can't find the info (yet, I keep looking).

Any suggestions?

ELP

PS: This is my /proc/asound/cards
```
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe7f4000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe9e8000 irq 27
```

---

### Post by dmrdavyd on 2010-01-16
I have no sound issue on my wife's computer - she unfortunately upgraded her stable 9.04 to 9.10 (without asking me first! ;)) and got no sound (this is an Athlon 64/BioStar motherboard/Realtek soundcard computer). The worst is that the applet System->Administration->Volume control does not open at all (just hung forever at opening).  In addition, computer became incredibly slow - it takes ~40 seconds to open Mozilla, for instance. IS THERE ANY SIMPLE WAY TO ROLL BACK TO 9.04 (other than fresh install) ??  I do not have any spare 3-4 hours (at least - to my previous experience) to spend on solving this issue! Please, advice!

---

### Post by Magnesium on 2010-01-17
> **dmrdavyd said:**
> I have no sound issue on my wife's computer - she unfortunately upgraded her stable 9.04 to 9.10 (without asking me first! ;)) and got no sound (this is an Athlon 64/BioStar motherboard/Realtek soundcard computer). The worst is that the applet System->Administration->Volume control does not open at all (just hung forever at opening).  In addition, computer became incredibly slow - it takes ~40 seconds to open Mozilla, for instance. IS THERE ANY SIMPLE WAY TO ROLL BACK TO 9.04 (other than fresh install) ??  I do not have any spare 3-4 hours (at least - to my previous experience) to spend on solving this issue! Please, advice!

Howdy friend,

Yes, you *can* downgrade:

[http://virtually-a-machine.blogspot.com/2009/09/howto-downgrade-ubuntu-karmic-to-jaunty.html]("http://virtually-a-machine.blogspot.com/2009/09/howto-downgrade-ubuntu-karmic-to-jaunty.html")

I would read the whole blog post before you do anything.

Downgrading like this should work for you, but it might be easier just to reinstall Jaunty. Depends on how many customizations and additional programs you had. But whatever you do, **back up your home folder first!** If you downgrade and something gets screwed up, you'll have a backup of your settings and data. If you do a clean install...you'll have your settings and data. Also, if you do a clean install, the following command is very helpful:

```
dpkg -l | awk '{print $2}' > installed_packages.txt
```

It will export all the packages installed on your computer, so you can reinstall everything very easily.

HTH,
Mg

---

### Post by Magnesium on 2010-01-17
> **SR_ELPIRATA said:**
> Hey Mag, think you can help me?

I did a clean install. I have sound but as an added bonus I got a screechy sound that keeps going on no matter the volume. I have an ATI onboard audio (Asus M3A78-T) and I'm using the analogs. I read in a thread that if I changed from 5.1 to 7.1 (which is what I really have hardware wise) then the sound would be eliminated but.... I got no 7.1 option.

9.04 and 8.10 detected my soundcard as HDA-ATI-SB but in 9.10 Im now HDA-Intel. Im guessing this is the problem but I have no idea how to force the driver. I tried also the linux-backports thing but as it was mentioned... it is not a fix for my sound card.

I keep looking around on how to force the driver back to HDA-ATI-SB but can't find the info (yet, I keep looking).

Any suggestions?

ELP

PS: This is my /proc/asound/cards
```
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe7f4000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe9e8000 irq 27
```

Hmmm...is it happening continuously? Or does it start after a certain period of time after a sound is played? Maybe you could run ```
cat /etc/modprobe.d/alsa-base.conf | grep power_save
```

Also try this (to get the latest version of ALSA, the version in Ubuntu has that bug sometimes):

```
sudo add-apt-repository ppa:stesind/stesind-alsa-21
sudo apt-get update
sudo apt-get upgrade
```

And reboot...if it's still not fixed, do

```
apt-get install linux-backports-modules-alsa-karmic-generic
```

reboot, and try once more. If it's still not fixed, we'll try something else.

Mg

---

### Post by SR_ELPIRATA on 2010-01-17
Hey Mag:

Thanks for the help! Well, the sound starts playing after playing a sound it looks. At some points of the volume scale it stops, like at 42% and 66% (its too loud to test the other). Also, I've noticed that sometimes when I adjust any of the sliders in the volume control applet that it stops for some time, but it returns as you adjust the volume again.

This is the result of the cat command you gave me:

```
options snd-hda-intel power_save=10 power_save_controller=N
```

Commented the line to disable it.

Trying right now the alsa sound upgrade...

Oh boy... lol, no sound :( nothing at all.

Doing the linux-backports thingie now, but I already had this and I remember a dev saying that this didnt affect nvidia or ati hardware at all.

After the restart no sound still. I tried the re-install of this module via synaptic and at least I have sound again, but the horrible thingie returned.

BTW, Im adding here the link to my question in launchpad, maybe you can see more details there, including the pulseaudio log:

[https://answers.launchpad.net/ubuntu/+question/97279](https://answers.launchpad.net/ubuntu/+question/97279)

---

### Post by Magnesium on 2010-01-17
Okay, run this for me please:

```
cat /proc/asound/card0/codec#* | grep Codec
```

(If that doesn't work, do aplay -l). Also, is this in a retail HTPC, or did you build your own?

Mg

---

### Post by SR_ELPIRATA on 2010-01-18
Hello again:

```
Codec: Realtek ALC1200
```

and the aplay...

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Its a HTPC that I built myself. Its quite simple actually, nothing too complicated (system wise).

---

### Post by Magnesium on 2010-01-20
> **SR_ELPIRATA said:**
> Hello again:

```
Codec: Realtek ALC1200
```

and the aplay...

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Its a HTPC that I built myself. Its quite simple actually, nothing too complicated (system wise).

Okay, try these things: paste
```
options snd-hda-intel model=auto probe_mask=1
```
at the end of
```
/etc/modprobe.d/alsa-base.conf
```
(and make sure that the other line with power_save is commented out). Then add
```
snd-hda-codec-realtek
```
to the end of /etc/modules. Then reboot...

There is no dedicated "hda-ati" driver/module, but the above things should help with the ALC1200.

I hope that this helps fix it....:)

Mg

---

### Post by Bash/inactive on 2010-01-21
Hello everyone I am trying to switch over from windoze.  I am very new to this stuff .  honestly i am clueless but i been at this os for for past 2 days still cant get my nvdia drivers installed.  I still have windoze in dual boot but eventually give up windoze all toghter. 

Here is my problem

currently i have envy in the system tools nothing happens when i put my password.  So i am trying this installation.  I went into dos mode by pressing ctrl+alt+f1 but when i type in my password and enter it says wrong password so i am stuck at this stage. Can anyone help me install my nvdia drivers for my 8800 GT?  

Thank You

Bash

---

### Post by bobbyo23 on 2010-01-21
> **ttguy said:**
> I upgraded to 9.10 and then found web browsing stopped. ( I am not sure if audio was working on this upgraded version. )

I restored a cloned image of my  /dev/sda1 partition. (My /home is on /dev/sda3).

After restoring back to  9.04 my browsing works but my audio is gone. I used to have the master volume control in the menu bar at the top. But this has disappeared. 

So this is major suckyness. :(

I guess the upgrade changed some audio configuration in  /home. 

I bet a windows 7 upgrade would work !!! ;)

Any suggestions.

edit: Fixed the missing Volume Control after restoring 9.04 - Right click on menu bar and choose add to panel. Choose Volume Applet.
After restoring the volume control I was able to unmute the audio. 

Still want to know what the fix for my browsing problems in 9.10 though!


i had the same problem with the web browsing, it turned out all i had to do is reboot then f10 for boot menu and my lan wasnt turned on...might give that a try...and when i dwnloaded flash plugins for flashplayer, thats when my sound went to crap....so any takers on this problem?

---

### Post by Mwbrouwer on 2010-01-22
I was having sound trouble after upgrading from Ubuntu 9.04 32bit to Kubuntu 64 bit.

I heard the login sounds, but no media would play through the speakers. I installed the GUI for ALSA Mixer and unmuted the speaker channel. This Worked! KMix showed all channels up, but ALSA Mixer fixed my sounds problem. 

Hope this helps someone else.:popcorn:

---

### Post by SR_ELPIRATA on 2010-01-22
Hey Mag!

hehehehehe....

I was writing about how the results were still bad and I was going to add the 7.1 problem that my sig refers to and I dont know why but I went again to the hardware preferences and then I noticed that FINALLY i had a 7.1 output option!!!!

So, select, raise and decresae volume, HORRID SOUND IS GONE!!!! woot! Thanks!

Now I need to see why the sub isnt getting any data.... in alsamixer I can see that all volume sliders are increasing/decreasing as they should, but I get nothing on the sub. I'm going to try something I read on another thread and will let you know how it works out.

Thanks!

ELP

PS: I just did the speaker-test thingie.. didnt know we had that.

```
speaker-test -c8 -twav

speaker-test 1.0.21

Playback device is default
Stream parameters are 48000Hz, S16_LE, 8 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 24 to 262144
Period size range from 8 to 87382
Using max buffer size 262144
Periods = 4
was set period_size = 65536
was set buffer_size = 262144
 0 - Front Left
 4 - Center
 1 - Front Right
 7 - Side Right
 3 - Rear Right
 2 - Rear Left
 6 - Side Left
 5 - LFE
```

I dont have the sides connected so no sound is obviously expected. The LFE actually got data as it said "rear center". That surprised me. Ok, got the sub to work uncommenting this line and changing it to yes (in /etc/pulse/daemon.conf)

```
enable-lfe-remixing = yes
```

Now its everything working as it should :) Thanks!

PS2: LOL I forgot. After changing that line and restarting the system made my mouse cursor to disappear (cant say that is the real reason but is the only thing I remembering modifying). I enabled the press control to see where the mouse is and thats how Im managing to post this hehe, can anyone PM me a suggestion on how to fix it? (so as to not hijack the thread)

---

### Post by Magnesium on 2010-01-22
> **Bash/inactive said:**
> Hello everyone I am trying to switch over from windoze.  I am very new to this stuff .  honestly i am clueless but i been at this os for for past 2 days still cant get my nvdia drivers installed.  I still have windoze in dual boot but eventually give up windoze all toghter. 

Here is my problem

currently i have envy in the system tools nothing happens when i put my password.  So i am trying this installation.  I went into dos mode by pressing ctrl+alt+f1 but when i type in my password and enter it says wrong password so i am stuck at this stage. Can anyone help me install my nvdia drivers for my 8800 GT?  

Thank You

Bash

Welcome to the Ubuntu Community, Bash! Linux can seem frustrating at times, but, as a user of Windows, Mac, and Linux, I can assure you that the Linux community is the most helpful and kind of any of them. (I might suggest that you read the "not Windows" link in my sig...it's an interesting perspective on Linux that may help ease your transition :) )

For sake of consistency, it might be best if you repost your question in a new thread (perhaps in the [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") forum), so as not to distract from this thread (which is about audio specifically). Reply here when you've done that, though...I might be able to help you figure this out.

Welcome again to Linux!! :D

Mg

---

### Post by Magnesium on 2010-01-22
> **bobbyo23 said:**
> i had the same problem with the web browsing, it turned out all i had to do is reboot then f10 for boot menu and my lan wasnt turned on...might give that a try...and when i dwnloaded flash plugins for flashplayer, thats when my sound went to crap....so any takers on this problem?

I don't understand exactly what happened with your sound...did you lose it completely, or did it just get all crackly? When I first installed flash, I had no sound in Flash stuff...I just had to launch alsamixer in the terminal, and increase the PCM slider.

Mg

---

### Post by Magnesium on 2010-01-22
> **SR_ELPIRATA said:**
> Hey Mag!

hehehehehe....

I was writing about how the results were still bad and I was going to add the 7.1 problem that my sig refers to and I dont know why but I went again to the hardware preferences and then I noticed that FINALLY i had a 7.1 output option!!!!

So, select, raise and decresae volume, HORRID SOUND IS GONE!!!! woot! Thanks!

Now I need to see why the sub isnt getting any data.... in alsamixer I can see that all volume sliders are increasing/decreasing as they should, but I get nothing on the sub. I'm going to try something I read on another thread and will let you know how it works out.

Thanks!

ELP

PS: I just did the speaker-test thingie.. didnt know we had that.

```
speaker-test -c8 -twav

speaker-test 1.0.21

Playback device is default
Stream parameters are 48000Hz, S16_LE, 8 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 24 to 262144
Period size range from 8 to 87382
Using max buffer size 262144
Periods = 4
was set period_size = 65536
was set buffer_size = 262144
 0 - Front Left
 4 - Center
 1 - Front Right
 7 - Side Right
 3 - Rear Right
 2 - Rear Left
 6 - Side Left
 5 - LFE
```

I dont have the sides connected so no sound is obviously expected. The LFE actually got data as it said "rear center". That surprised me. Ok, got the sub to work uncommenting this line and changing it to yes (in /etc/pulse/daemon.conf)

```
enable-lfe-remixing = yes
```

Now its everything working as it should :) Thanks!

PS2: LOL I forgot. After changing that line and restarting the system made my mouse cursor to disappear (cant say that is the real reason but is the only thing I remembering modifying). I enabled the press control to see where the mouse is and thats how Im managing to post this hehe, can anyone PM me a suggestion on how to fix it? (so as to not hijack the thread)

Hooray! I'm glad all the sound stuff is working for you...hope my posting helped some too.

About the mouse cursor (I know you suggested PM, but it's okay for a couple of posts OT)...that sounds extremely weird that uncommenting that line out would have that effect. Can you comment it back out again and reboot? See if the mouse cursor came back....:confused:

Mg

---

### Post by spiritofelric on 2010-01-23
> **crimsun said:**
> 
    * Attach an ALSA codec dump to your linux bug report if jack sense (e.g., connecting headphones mutes internal laptop speakers) does not seem to function properly.

My laptop speakers do not turn off when i plug in my headphones.  Any ideas on how i could fix this?

I've attached the ALSA codec dump as per instructions listed at:
[https://wiki.ubuntu.com/ALSA/JackSense](https://wiki.ubuntu.com/ALSA/JackSense)

Though it may be a manufacturer fault as per:
[https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionTX2000](https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionTX2000)

---

### Post by grouchyolddude on 2010-02-19
okay folks.. I've been fiddling with this for a couple of weeks. No audio in firefox..
I've tried uninstalling and reinstalling the  esound client, alsa oss, and flash plugin non-free with no improvement.

also tried the fix here [http://mindaict.blogspot.com/2010/02/solved-fixing-flash-problems-in-firefox.html](http://mindaict.blogspot.com/2010/02/solved-fixing-flash-problems-in-firefox.html)
with no luck

---

### Post by Magnesium on 2010-02-19
> **grouchyolddude said:**
> okay folks.. I've been fiddling with this for a couple of weeks. No audio in firefox..
I've tried uninstalling and reinstalling the  esound client, alsa oss, and flash plugin non-free with no improvement.

also tried the fix here [http://mindaict.blogspot.com/2010/02/solved-fixing-flash-problems-in-firefox.html](http://mindaict.blogspot.com/2010/02/solved-fixing-flash-problems-in-firefox.html)
with no luck

But you get audio elsewhere? ie, Totem, system sounds, Rhythmbox, etc.?

Try running ```
alsamixer
``` in terminal and making sure all volume controls (especially PCM) are up.

Mg

---

### Post by mihamtalamac on 2010-02-20
no sound with flash on my Ubuntu 9.10 either. i get sound using Mplayer and Amarok but thats it. in the Hardware tab in the Sound Preferences i don't see anything. I enabled all chanels with Alsamixer, have the latest kernel (2.6.31-20-generic) installed Linux-backpots-modules-alsa-Karmic-generic and nothing. i get no sound using "speaker-test". here is some other output that might be usefull for someone to help

sudo lshw -class multimedia 
*-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:25 memory:ffe38000-ffe3bfff

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

only thing which helped so far is "sudo alsa force-reload" but that isn't real solution to this problem. after rebooting you must do it again.

Help please :(

---

### Post by ratcheer on 2010-02-20
mihamtalamac, do you have more than one sound card on your system, e.g., an onboard and a plugged in card? If so, ALSA is probably detecting the "wrong" one as the first card. That is to say, the one you do not intend to use.

If that is the case, you need to add code to an ALSA configuration file to force the unwanted card to be second. After you do that, sound will work in Flash and, probably, in Firefox, too.

If you verify that this is your situation, I will help you find the ALSA changes you need to make.

Tim

---

### Post by mihamtalamac on 2010-02-20
> **ratcheer said:**
> mihamtalamac, do you have more than one sound card on your system, e.g., an onboard and a plugged in card? If so, ALSA is probably detecting the "wrong" one as the first card. That is to say, the one you do not intend to use.

If that is the case, you need to add code to an ALSA configuration file to force the unwanted card to be second. After you do that, sound will work in Flash and, probably, in Firefox, too.

If you verify that this is your situation, I will help you find the ALSA changes you need to make.

Tim
Hi Tim. i have only one sound card (Amilo m1450g laptop). just to add that after clean install everything worked well. problems apeared after upgrade

---

### Post by grouchyolddude on 2010-02-21
> **Magnesium said:**
> But you get audio elsewhere? ie, Totem, system sounds, Rhythmbox, etc.?

Try running ```
alsamixer
``` in terminal and making sure all volume controls (especially PCM) are up.

Mg
okay mag'.. the alsamixer shows up, the master shows 91, PCM 81, surround 0, center 100, LEF 0, line 0, cd 81.
 and I can't seem to make 'any' adjustments on any of them. 
yes, totem and other sound works fine. Only issue seems to be in firefox.

> o@o-desktop:~$ sudo lshw -class multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: MCP2S AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0


---

### Post by SR_ELPIRATA on 2010-02-22
Hey Mag!

Well, after a restart.. the mouse behaved as normal, so I think it was an abnormality I guess :P

BTW, I was forced to change hard drives again and since I hadnt noticed before when the 7.1 option had appeared, decided to start all over and just add the options you last suggested and not the other most recent pulseaudio stuff and voila, the 7.1 option appeared and its still working today.

The biggest difference I guess is not soundwise, the alsamixer shows different, in the prior installation I could see all 6 channels sliders and could see some of the audio card details from there, and since the change, I see the normal alsamixer with also the mics and other stuff. But its not really a big issue.

The other thing I need to test now, is something that happened yesterday as I was playing an AC3 file-movie and the center channel was sounding on the left speaker whereas all the others were working normally (besides the center which I guess was working like the left front). I dont remember seeing this before with other 5.1 files that I have but after testing I will confirm if its happening or just another abnormality in a single file.

ELP

PS: Did another 5.1 test and sounded great, so I guess the problem I was experiencing earlier was just an abnormality.

---

### Post by Eyore15 on 2010-02-22
Regrettably I haven't had time to follow the entire thread.  This may duplicate somethings that have all ready been proposed.  I had audio problems when I upgraded my Starling to 9.10.  After fighting with the wireless, I gave up and went back to 9.04 -- still had the audio problem.

Lots of helpful suggestions; the one that showed the most promise was to install the pluse-audio" components.  I did that following the directions in  one of the replies.  No audio,  It was then I found a reference stuck in some programmers old blog that said 9.04 and 9.10 didn't function well with Pulse.  He strongly recommended ALSA == and not the latest and greatest, but rather the software available though Synamtc

Sure enough, I did the install via Synaptic and dug around the the new interface.  There, for all the word to see, was a checked "mute" box for the primary playback channel.  Nothing; not the pulse-audio stuff or anything in Sound Preferences showed this level of "mutedness" 

Clicked the box, and I got audio I can spare.  I had a 9.10 box that I did the same thing to; works like a champ.  I have a tower with a surround sound system that I'm working with -- will run this procedure on it before I do anything else..  Although I'm kind of Holding off for Lucid to see if they learned their lesson about releasing software that's not quite ready for the consumers.

---

### Post by Magnesium on 2010-02-22
> **SR_ELPIRATA said:**
> Hey Mag!

Well, after a restart.. the mouse behaved as normal, so I think it was an abnormality I guess :P

BTW, I was forced to change hard drives again and since I hadnt noticed before when the 7.1 option had appeared, decided to start all over and just add the options you last suggested and not the other most recent pulseaudio stuff and voila, the 7.1 option appeared and its still working today.

The biggest difference I guess is not soundwise, the alsamixer shows different, in the prior installation I could see all 6 channels sliders and could see some of the audio card details from there, and since the change, I see the normal alsamixer with also the mics and other stuff. But its not really a big issue.

The other thing I need to test now, is something that happened yesterday as I was playing an AC3 file-movie and the center channel was sounding on the left speaker whereas all the others were working normally (besides the center which I guess was working like the left front). I dont remember seeing this before with other 5.1 files that I have but after testing I will confirm if its happening or just another abnormality in a single file.

ELP

Hey Elp! Either you have incredible uptime, or just never posted earlier...but I'm glad your mouse was just a little weirdity. Also glad that the options got you 7.1 again.

As for the center/front left anomaly...to see if it's just that file or if it is a system-wide problem, run:

```
 speaker-test -c8 -t wav
```

This will play "Front Right", "Front Center", etc. out of the corresponding speaker, one at a time, for you to test that everything is working right and assigned to the right channel.

Mg

---

### Post by mihamtalamac on 2010-02-23
> **mihamtalamac said:**
> no sound with flash on my Ubuntu 9.10 either. i get sound using Mplayer and Amarok but thats it. in the Hardware tab in the Sound Preferences i don't see anything. I enabled all chanels with Alsamixer, have the latest kernel (2.6.31-20-generic) installed Linux-backpots-modules-alsa-Karmic-generic and nothing. i get no sound using "speaker-test". here is some other output that might be usefull for someone to help

sudo lshw -class multimedia 
*-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:25 memory:ffe38000-ffe3bfff

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

only thing which helped so far is "sudo alsa force-reload" but that isn't real solution to this problem. after rebooting you must do it again.

Help please :(
HI guys. just to report that I finaly managed to get my sound working :)))
Thing is that it looks like my **[COLOR=Red]software modem[/COLOR]** caused the trouble. i've just disabled it (System/Administration/Hardware Drivers) and it works now :)))))))))

---

### Post by SR_ELPIRATA on 2010-02-26
Yes, I did the speaker test and it worked ok, then ran one of the planet earth episodes and again worked flawlessly. (I just changed hard drives again and I'm again doing the adjustments lol) This time, finally the system will be only for HTPC purpouses.

ELP

---

### Post by tcmagicfan on 2010-03-02
having trouble upgrading the new firefox, goes into the download file but do anything after that, can somebody help me. wont let me get into myspace until i upgrade, thats wierd,,,,,.

---

### Post by DJRWolf on 2010-03-05
When I boot into Ubuntu 9.10 I get nothing but static coming out but in Win7 it works fine. [Link to sound card I have.]("http://www.bestbuy.com/site/Rocketfish%26%23153%3B+-+5.1-Channel+PCI+Sound+Card/9180405.p?id=1218047304449&skuId=9180405")

Update: It seams the updates I did since I last tried it before I posted fixed the problem.

---

### Post by Stone age on 2010-03-14
I too have been wrestling with flash sound in a freshly installed kubuntu 9.10, using the Realtek ALC883 audio chip on a Gigabyte GA-31M-ES2L motherboard. KDE seemed fine: login greeting sounds, Test button in the Multimedia section of System Settings works; but flash in either firefor or konquerer is silent. I tried a lot of wizardry posted here in vain and I think I reverted all of it.

What did work was:
 - open something soundful in your browser (just to be able to hear when it works)
 - open sound mixer (for instance, click the volume applet and the mixer button that appears)
 - go Settings > Configure Channels
 - checkmark the "Side" entry (and maybe some others) and press OK
 - in the new "Side" column, uncheckmark Mute

There are many more "optional" channels with exotic names. Somehow they all have to be "on" to hear plain old stereo, but their volume doesn't seem to matter.

---

### Post by kforum on 2010-03-14
i have an intel card that uses snd-hda-intel driver, i had sound if and only if i reloaded alsa driver, at every session.

the fix was to uninstall the software modem driver, somehow it blocks the regular sound card from being properly detected.

PLEASE include this as a fix, in the list of fixes, i did not need to have searched for 3 hours to find this, thank you.

---

### Post by teeliina on 2010-03-21
Hi! I'm fairly new to this forum, but have played with ubuntu for some time. I first got this audio problem when I updated from 9.04 to 9.10 in January. That time I fixed it with installing alsa, not removing pulseaudio. that led to having the mute-box always ticked at sound-preferences after boot. very annoying. I also had the might-be-a-bug of disk-failure notification, so I thought to reinstall to see what happens(I have only updated since 8.04). nothing really- sounds gone, disk-failure still there, even flashplayer didn't work. This time I got all sounds back by reinstalling all pulseaudio files with synaptic, and installing pulseaudio extras and gstreamer extras at software center. no problems yet. easy to do, since I'm not that technical really.

---

### Post by JosephGarrison on 2010-03-28
The only audio problem I have have is something I know is Ubuntu related, not just a single software on my comp. Often the audio does not start with a vid or when a song begins. I need to turn the volume up or down and then the sound will start, then I just restart the song or vid. This isn't too often that it's a problem but it does kind of get annoying once in awhile.

---

### Post by sderrick on 2010-04-08
> **Mwbrouwer said:**
> I was having sound trouble after upgrading from Ubuntu 9.04 32bit to Kubuntu 64 bit.

I heard the login sounds, but no media would play through the speakers. I installed the GUI for ALSA Mixer and unmuted the speaker channel. This Worked! KMix showed all channels up, but ALSA Mixer fixed my sounds problem. 

Hope this helps someone else.:popcorn:

Worked like a charm!  :popcorn:

---

### Post by ScarySquirrel on 2010-04-22
I have installed Kubuntu 9.10, and I get sound only in the left speaker. I have tried splitting "front" mixer slider, and all manner of fiddling with the mixer. I have tried both gstreamer and xine backends. Nothing has worked so far.

---

### Post by ScarySquirrel on 2010-04-22
I guess I should have expected this. There's always something. 
I even tried installing that alsa backport kernel, for which I guess I didn't have the headers. I then installed the kernel headers, and now I can't update with synaptic due to "broken packages" whatever those are. 
Also, no sound for me now. sudo modprobe says "no sound for you."

---

### Post by jabrilm on 2010-05-13
I know this thread is for audio problems in 9.10, but I've got audio issues after an upgrade from 8.04 to 10.04 (hardy to lucid). Basically I have no sound at all. No system sounds (e.g. on startup and login), no sound in banshee, no sound in firefox, nothing. If I type 'alsamixer' all the levels look fine. I've tried tips that other people have posted that worked for them, but with no luck. If anyone can offer detailed suggestions they'd be much appreciated. Otherwise I may have to revert to an older Ubuntu LTS.

---

### Post by Eyore15 on 2010-05-13
> **jabrilm said:**
> I know this thread is for audio problems in 9.10, but I've got audio issues after an upgrade from 8.04 to 10.04 (hardy to lucid). Basically I have no sound at all. No system sounds (e.g. on startup and login), no sound in banshee, no sound in firefox, nothing. If I type 'alsamixer' all the levels look fine. I've tried tips that other people have posted that worked for them, but with no luck. If anyone can offer detailed suggestions they'd be much appreciated. Otherwise I may have to revert to an older Ubuntu LTS.

Another kind soul pointed me towards GNOME ALSA mixer. Note that this is different from ALSA mixer -- the latter showed that settings were apparently OK, it took the GNOME version to find the wayward settings. It showed that my sound was muted and volume level set to "zero".  Once I made the necessary changes there, I had my sound back.  It works in 9.10 and 10.04. At least for me.

hth

mcm

---

