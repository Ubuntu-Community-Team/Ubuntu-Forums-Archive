---
title: "Sound Card Disappeared"
date: 2010-09-23
forum: Hardware
---

### Post by something_clever on 2010-09-23
Before I get started, here's the specs, HP Pavilion dv7 laptop running ubuntu 10.04, sound card is radeon.

So I installed the latest batch of updates from the update manager. nothing looked like it should get the ok so i installed them all. Then I went to restart my computer and the volume control icon is showing my speakers as muted. I can move the slider up and down and hit the volume up and down buttons but nothing changes. If I hit the mute button it shows the muted icon in the little notification box but when I hit it again the notification box shows it's unmuted but the icon doesn't change and there is no sound. I also tried plugging in my headphones and there was still no sound.  When i go into my sound preferences under hardware it isn't reading my sound card, or HDMI sound card (usually it would display both, but HDMI didn't work properly). ad under output it only has the option of dummy output. I opened Pulse Audio Volume Control and it has the same option for output.

I ran aplay -l and what i got back was

aplay: device_list:223: no soundcards found...

I have also already added "options snd-hda-intel enable_msi=1" to /etc/modprobe.d/alsa-base.conf so that's not the issue.

Anyone know what I should do?

---

### Post by lkjoel on 2010-09-23
> **something_clever said:**
> Before I get started, here's the specs, HP Pavilion dv7 laptop running ubuntu 10.04, sound card is radeon.

So I installed the latest batch of updates from the update manager. nothing looked like it should get the ok so i installed them all. Then I went to restart my computer and the volume control icon is showing my speakers as muted. I can move the slider up and down and hit the volume up and down buttons but nothing changes. If I hit the mute button it shows the muted icon in the little notification box but when I hit it again the notification box shows it's unmuted but the icon doesn't change and there is no sound. I also tried plugging in my headphones and there was still no sound.  When i go into my sound preferences under hardware it isn't reading my sound card, or HDMI sound card (usually it would display both, but HDMI didn't work properly). ad under output it only has the option of dummy output. I opened Pulse Audio Volume Control and it has the same option for output.

I ran aplay -l and what i got back was

aplay: device_list:223: no soundcards found...

I have also already added "options snd-hda-intel enable_msi=1" to /etc/modprobe.d/alsa-base.conf so that's not the issue.

Anyone know what I should do?
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by something_clever on 2010-09-23
so apparently the 8th time getting shut off is the charm because suddenly everything works again. so i guess this one is solved. weird

---

### Post by Mamoth on 2010-11-20
Hi.

I have a similar problem.
During an update of my Ubuntu Lucid, a few weeks ago, I ended up with no sound at all after the update.

It turned out that it is the soundcard which is not installed any more. It seems the drivers are gone.

The PC is a [Toshiba Satellite a660-13q]("http://es.computers.toshiba-europe.com/innovation/product/Satellite-A660-13Q/1087035/toshibaShop/false/"). (sorry, it is in Spanish).

So, the symptoms :

[LIST]
[*]There is no soundcard in *Preferences > Sound > Hardware*
[*]When I start the laptop, I can choose between 2 kernel versions : 2.6.32-25 (current) and 2.6.32-24.
And [COLOR=DarkRed]**when I use the 2.6.32-24 version, the sound works **[/COLOR]! And the soundcard appears in *Preferences > Sound > Hardware.*
[*]lspci and aplay gives the following :
[/LIST]
```
~$ **lspci** | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
~$ sudo apt-get install Pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Pulseaudio
~$ **aplay** -l
aplay: device_list:223: no soundcards found...
```
[LIST]
[*]I have reinstalled all already installed *pulseaudio** packets in Synaptics. No result.
[*]The command cat* /proc/asound/modules *gives no output (empty file).
[*]I also tried ```
Mamouth@myPC:~$ sudo /sbin/alsa-utils reset & sudo /sbin/alsa-utils restart
[1] 2866
 * Resetting ALSA...                                                             * Shutting down ALSA...                                                 [ OK ] 
 * warning: 'alsactl store' failed with error message 'alsactl: save_state:1502: No soundcards found...'...                                              [fail] 
 * Setting up ALSA...                                                            * warning: 'alsactl restore' failed with error message 'alsactl: load_state:1608: No soundcards found...'...                                                      ...done.
[1]+  Done
```and ```
Mamouth@myPC:~$ sudo apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``` and ```
Mamouth@myPC:~$ alsa force-reload
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-oss snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).
``` With no results again.
[*]I also tried a purge : ```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-'uname -r' linux-ubuntu-modules-'uname -r' libasound2

``` and ```
sudo aptitude --purge reinstall pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils

``` again with no results.
[/LIST]
So what should I do to repair this ?
I guess some config files changed between the 2 versions, but which ones ?

---

### Post by lkjoel on 2010-11-20
Did you try Fix your sound!
and Post-Fix your sound!?

---

### Post by hedge.hog on 2011-03-12
I've experienced the same issue - no snd cards after an update...

does anyone have a suggestion that dos not involve oss?

PS Some (irrational?) reasons for the non-oss solution request:
I'd like to stay with std ubuntu snd as far as possible.
the suggested solution has not been updated to 10.04 (it mentions 9.04/intrepid)
I don't want my sound to be on the bleeding edge
Ubuntu should 'just work'

---

### Post by lkjoel on 2011-03-13
> **hedge.hog said:**
> I've experienced the same issue - no snd cards after an update...

does anyone have a suggestion that dos not involve oss?

PS Some (irrational?) reasons for the non-oss solution request:
I'd like to stay with std ubuntu snd as far as possible.
the suggested solution has not been updated to 10.04 (it mentions 9.04/intrepid)
I don't want my sound to be on the bleeding edge
Ubuntu should 'just work'
OSS 4.x works with 10.04, and it should work with 10.10.

Maybe [this thread]("http://ubuntuforums.org/showpost.php?p=4790346&postcount=1") could help? [http://ubuntuforums.org/showpost.php?p=4790346&postcount=1]("http://ubuntuforums.org/showpost.php?p=4790346&postcount=1")

---

### Post by rkdvs on 2011-09-05
Hi All,
I have the same issue with the sound card. I recently, installed Ubuntu 11.04 using WUBI. When I first installed the OS I was able to hear the sound from the ear phone jack. I tried to update the OS using Update manager and I lost the sound card configuration and sound does not even work from the ear phone jack. 

Please read the output from the following commands:
$ aplay -l
*aplay: device_list:240: no soundcards found...*

$ aplay -L
[I]default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server[/I]

$ cat /proc/asound/version
*cat: /proc/asound/version: No such file or directory*

$ cat /proc/asound/cards
*cat: /proc/asound/cards: No such file or directory*

$ cat /proc/asound/timers
*cat: /proc/asound/timers: No such file or directory*

$ cat /proc/asound/pcm
*cat: /proc/asound/pcm: No such file or directory*

$ cat /proc/asound/modules
*cat: /proc/asound/modules: No such file or directory*


$ lspci -v
[I]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5110 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, fast devsel, latency 0
    Memory at d2500000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 50e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 50c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 50a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at d4705c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d4700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: d3700000-d46fffff
    Prefetchable memory behind bridge: 00000000d0400000-00000000d14fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d2600000-d36fffff
    Prefetchable memory behind bridge: 00000000d1500000-00000000d24fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 5080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 5060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 5040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at d4705800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at 5108 [size=8]
    I/O ports at 511c [size=4]
    I/O ports at 5100 [size=8]
    I/O ports at 5118 [size=4]
    I/O ports at 5020 [size=32]
    Memory at d4705000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: medium devsel, IRQ 11
    Memory at d4706000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: fast devsel, IRQ 11
    Memory at d4704000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 360b
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at 3000 [size=256]
    Memory at d0410000 (64-bit, prefetchable) [size=4K]
    Memory at d0400000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d0420000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Hewlett-Packard Company Device 1381
    Physical Slot: 1
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d2600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k[/I]

When I check the "Sound Preferences" from the Menu (top) I find that Hardware tab do not contain any sound cards listed. 
I am sure that when I executed the following commands to re-install the sound card drivers in the terminal, I lost the sound from the head-phone jack.
[I]sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-'uname -r' linux-ubuntu-modules-'uname -r' libasound2

sudo aptitude --purge reinstall pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils[/I]


Please help me how to install the drivers for the hardware listed above. I appreciate if you could post the reply to my sound card issue at the earliest possible.

---

### Post by lkjoel on 2011-09-05
Could you give me the output of this Terminal command?
```
sudo aplay -l

```
This might just simply be a permissions issue.

---

### Post by moonsoup on 2011-09-17
> **lkjoel said:**
> Did you try Fix your sound!
and Post-Fix your sound!?

Wow! I'm ready to try this right now!.....
What the "bleep" is it?... What does this mean?
I think nobody knows what this is referring to. 
Could you be more specific?:confused:

---

### Post by lkjoel on 2011-09-17
It's outdated, and no longer recommended. It was in my signature one time, but I deleted it.
Instead, look at Sound Troubleshooting in my signature. It uses the safest methods possible.

---

