---
title: "no sound on Toshiba Satellite A135-S7404"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by crazyforpurple on 2007-10-10
After installing Ubuntu on this laptop i find that it cant see my sound card. 

Does anyone have any advice on where to start to fix this?  i guess im going to have to install the drivers for it?

thanks in advance xxx

lucy x

---

### Post by stchman on 2007-10-10
> **crazyforpurple said:**
> After installing Ubuntu on this laptop i find that it cant see my sound card. 

Does anyone have any advice on where to start to fix this?  i guess im going to have to install the drivers for it?

thanks in advance xxx

lucy x

What sound card does your laptop have.  Ii have a Toshiba A135 laptop and it has the SB450 ATI sound card.  I got it to work by doing this:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

If that does not work then you will probably need to update your ALSA drivers.  I have a script to do this in my ALSA update section:

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

I hope these help.

Also please post an lspci -v here for us to see.

---

### Post by crazyforpurple on 2007-10-10
can anyone explain to me what g streamer is? do i need it? how do i install it if i do need it thanks xx

love lucy x

---

### Post by crazyforpurple on 2007-10-10
thank you xx i will check out both of those links. 

heres the result from that command that you asked:

mommy@mommy-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: dc000000-dc0fffff
        Prefetchable memory behind bridge: 0000000068000000-000000006bffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7128
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at da000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at d4000000 [disabled] [size=128K]
        Capabilities: <access denied>

06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 68000000-6bfff000 (prefetchable)
        Memory window 1: 6c000000-6ffff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 18
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 20
        Memory at dc005800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

mommy@mommy-laptop:~$ 

does this help at all?

thanks, 

love lucy xx

---

### Post by crazyforpurple on 2007-10-19
> **stchman said:**
> What sound card does your laptop have.  Ii have a Toshiba A135 laptop and it has the SB450 ATI sound card.  I got it to work by doing this:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

If that does not work then you will probably need to update your ALSA drivers.  I have a script to do this in my ALSA update section:

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

I hope these help.

Also please post an lspci -v here for us to see.

hey stchman, i am trying various things here but it seems that from that command i have 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

as my sound device? not the ATI 450 thingy? do you know of any workarounds for this device? 

i am now off to check my ALSA  drivers that i thought i had installed but now im thinking i made a mistake somewhere as its not loading so im gong to check your link about that too. 

love lucy xx

---

### Post by crazyforpurple on 2007-10-19
> **crazyforpurple said:**
> hey stchman, i am trying various things here but it seems that from that command i have 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

as my sound device? not the ATI 450 thingy? do you know of any workarounds for this device? 

i am now off to check my ALSA  drivers that i thought i had installed but now im thinking i made a mistake somewhere as its not loading so im gong to check your link about that too. 

love lucy xx


hello, 

from your page 

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

i cant seem to run the script :( so i went to

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and followed the instructions step by step.... and i can do it smoothly until i get to "Manually Specify Module Parameters" zand when i type in the command i get:

mommy@mommy-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
mommy@mommy-laptop:~$ 

if i try to do it as root like this i get:

mommy@mommy-laptop:~$ sudo su cat /proc/asound/card0/codec#* | grep Codec
Unknown id: cat
mommy@mommy-laptop:~$ 

so i went to this page:

[http://ubuntuforums.org/showthread.php?t=568463](http://ubuntuforums.org/showthread.php?t=568463)

and typed in the other 2 commands it gives there and these are the responses i get...

mommy@mommy-laptop:~$ cat /proc/asound/card0/codec\#*
cat: /proc/asound/card0/codec#*: No such file or directory
mommy@mommy-laptop:~$ cat /proc/asound/*
--- no soundcards ---
  1:        : sequencer
 33:        : timer
cat: /proc/asound/oss: Is a directory
cat: /proc/asound/seq: Is a directory
G0: system timer : 4000.000us (10000000 ticks)
Advanced Linux Sound Architecture Driver Version 1.0.15rc3.
Compiled on Oct 19 2007 for kernel 2.6.22-14-generic (SMP).
mommy@mommy-laptop:~$ 

do you ahve any idea why it comes up as saying "no soundcards" ??? please help me as to what i ahve done wrong and what i should do now xxx

very frustrates xxx

love lucy xx

---

### Post by crazyforpurple on 2007-10-24
I GOT IT WORKING!!!! WOO HOOO!!!

 below is a list of what i did, I actually got the info from this link:

[http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374)

but below is specificatlly what I did:

hope this helps someone else!! xxx

love lucy xxx


1. after installing ubuntu gutsy i had no sound and no sound cards were detected.
2. when i tried the command "cat /proc/asound/cards" it would just say no soundcards installed
3. i couldnt even find these files....
"Remove ~/.asoundrc and ~/.asoundrc.asoundconf."

let alone remove them! so i went on to the next step:

4. i then went onto your next step:
"Install Ubuntu kernel back ports (linux-backports-modules-* ). You may need to run the above command (Possible conflicting driver issue). Then reboot."

to do this i did the following:

go to system, administration, synaptic package manager,
type in your password
in synaptic package manager, go to settings, repositories

under the "ubuntu software" tab I checked on each entry under "downloadable from the internet" and unchecked the cd/dvd option.

then under the "updates" tab I checked everything including the gutsy backports.
close the repositories box and then click reload in the synaptic package manager.

5. I don't think its necessary at this time but I restarted my laptop for good measure at this point.

6. I then went back into the synaptic package manager and ran a search for backports

7. I also went to applications, accessories, terminal and ran the following command
uname -r to find the details of my kernal.

it came back with 2.6.22-14-generic

8. In the synaptic package manager I had many options from my search and I wasnt sure which one I should use... I narrowed it down to

linux-backports-modules (which in the info said "Generic Linux backported drivers.")
and
linux-backports-modules-gene-2.6.22.14.21 (which in the info said "Backported drivers for generic kernel image")

I'm not quite sure why, but I clicked on the latter on and marked it for install. I then clicked "apply" and once it was all done I restarted the laptop and on restart I had sound!!!!!!


This may not be worth noting but when I use the term "restart" I actually shut down and then start up the laptop as using the "restart" option on mine means that it hangs before the log in screen.

---

### Post by rtfirefly1000 on 2007-11-16
I hate to rain on the parade, but I recently bought an A135-S7404 (wee it felt good to wipe vista off it), and if you install the linux-backports-modules-* packages your sound will start working.  Tried it out on a hunch, and everything seems to work nicely, except for the fact the volume knob on the front controls the headphone volume...

---

### Post by whitemice on 2007-11-26
I have a P205-S6207, same model but roughly the same vintage.  I didn't have sound until I booted with "acpi_osi=!Linux".  The sound card was recognized before but didn't work due to some ACPI issue.

My kernel is "2.6.22.12-0.1-default" (openSUSE 10.3).  From what I've read acpi_osi=!Linux will be the default ACPI mode in 2.6.23

Sound card is the Intel Corporation 82801G (ICH7 Family) HDA.

---

### Post by jsharkey on 2007-12-21
I have the exact same laptop and I've been working to get Gentoo linux installed on it.

To get sound working I had to play with latest unstable ALSA (kernel module, not compiled in), and I had to use "model=lenovo" to get the sound to auto-detect when I plugged in my headphones. With the default configuration it would otherwise ignore when I plugged in headphones.

Also I've detailed everything I've done over at the Gentoo wiki, including getting the internal wireless working with madwifi:

[http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_A135](http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_A135)

---

