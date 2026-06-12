---
title: "RaLink RT3090 Wireless Woes on 11.10 b2"
date: 2011-09-24
forum: Hardware
---

### Post by OrphanShadow on 2011-09-24
Hello

I have a Lenovo S205 currently running 11.10 beta 2.

I have installed the system fine, and everything works swell except for the Wireless card.

lspci reports the card is a Ralink RT3090 pci.

When I look at the network indicator, its shows the wireless as being disabled. However, whenever I try to enable it, it just defaults straight back to disabled.

So far I have tried the following:

Blacklisting different combinations of old rt drivers (rt2800pci, rt2x00lib etc) - no effect (other than sometimes completely removing wireless from the networking menu)

Installing the rt3090-dkms package from Markus Tisofts ppa - no effect

Compiling source from the ralink website - results in errors (and I have build-essential installed)


Can somebody help out with this issue?

(And no, I will not use ndiswrapper)

---

### Post by OrphanShadow on 2011-09-24
Just an update again: I'm going to try activating oneiric-proposed and see if any 'in-the-pipeline' updates fix this small issue I'm having too.

---

### Post by OrphanShadow on 2011-09-24
One last update:

I managed to compile the latest rt3090 drivers from Ralink with a few tweaks, but even after this Wireless will not enable in Network Manager.

Gonna try one more idea before bed: Manually copying the rt3090.ko into the kernel drivers staging folder, and see if anything happens then.

In the meantime, any help would be wonderful xD

---

### Post by OrphanShadow on 2011-09-24
GOTCHA!!

Apparently the acer_wmi module is loading at startup which is interfering with the wireless, making it think the switch is constantly off.

Removing and blacklisting this package has resulted in me being able to connect to wireless networks :KS

Im gonna do some speed testing before marking this as solved, but its halfway there xD

---

### Post by OrphanShadow on 2011-09-24
Just as a final note, compiling RT3090 from source and installing apparently doesnt work no matter what I try.

The built in rt2800pci module actually works the best here. Link is limited to Wireless-G speeds however (54Mbps)

At least now, though, I can say it works, and is stable.

---

### Post by nrosvall on 2011-09-26
Hi,
 
Recently I had some trouble getting my lenovo s205 to work with a Oneiric daily build(before beta 2). I could not get the wireless to work. Could you tell what modules you had to blacklist to get rt2800pci to work? Only acer_wmi? 
 
Also, does your machine shutdown ok? Mine was hanging on shutdown, reboot worked ok. Maybe I should give beta 2 a try.
 
Cheers!

---

### Post by amirfoad on 2011-09-29
Hi.
I have a HP Mini 110 and the wireless card is also rt3090.
As you know it didn't work well in Ubuntu 11.04 and Ubuntu couldn't recognize the right card, but by installing the right driver from [here]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/") and blacklisting other cards, it was working pretty well.
But after upgrading to Ubuntu 11.10 beta2, the wireless is completely disconnected and couldn't find access points and it seems to be switched off although it's on! :D
What can i do?
I searched a lot but didn't get right answer! I really need it!
Get me a help if you know! :D
Thanks a lot!

---

### Post by rstefan on 2011-09-30
Hello,

Try to remove the blacklists you made and it should work after reboot. At least this worked for me.
My problem now is that i cannot connect to WPA2-PSK wireless networks.

Regards!

---

### Post by Steviepower on 2011-10-14
Are there any updates on this? I'm having the same problem after the upgrade...

---

### Post by Pro$pect on 2011-10-14
same here

---

### Post by amirfoad on 2011-10-15
> **rstefan said:**
> Hello,

Try to remove the blacklists you made and it should work after reboot. At least this worked for me.
My problem now is that i cannot connect to WPA2-PSK wireless networks.

Regards!

Yes! Thank you! It works perfectly after removing from blacklist!

---

### Post by rstefan on 2011-10-17
Did you tried to connect to WPA2-PSK? I still can't connect to any of these networks.

---

### Post by amirfoad on 2011-10-17
Not yet! I'll try and tell the result!

---

### Post by dan_a on 2011-10-19
I've been having similar problems with 11.10:
[LIST]
[*]Default driver chosen by Ubuntu: Drops connection every few seconds
[*]Markus Herbergling's PPA: Won't install on 11.10
[/LIST]

I've not had chance to test this yet (I will in about 4 hours) but what I've done is:
[LIST=1]
[*]Installed Markus Hebergling's patched driver by doing "wget [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb) ; dpkg -i rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb" (this step won't work completely)
[*]Created a file called "linux-3.diff" in the folder /usr/src/rt3090-2.4.0.4/patches with the following contents:
```
Index: rt3090-2.4.0.4/os/linux/cfg80211.c
--- rt3090-2.4.0.4/os/linux/cfg80211.c  2011-05-05 14:41:31.000000000 +0100
+++ rt3090-2.4.0.4/os/linux/cfg80211.c  2011-10-19 13:38:26.498902459 +0100
@@ -2059,7 +2059,7 @@
               pChan->band = IEEE80211_BAND_2GHZ;
       /* End of if */

-       pChan->center_freq = ieee80211_channel_to_frequency(ChanId);
+       pChan->center_freq = ieee80211_channel_to_frequency(ChanId, pChan->band);

 #if (LINUX_VERSION_CODE < KERNEL_VERSION(2,6,32))
       if (pAd->CommonCfg.PhyMode >= PHY_11ABGN_MIXED)
@@ -2620,7 +2620,7 @@
       for(IdLoop=0; IdLoop<NumOfChan; IdLoop++)
       {
               pChannels[IdLoop].center_freq = \
-                                       ieee80211_channel_to_frequency(Cfg80211_Chan[IdLoop]);
+                                       ieee80211_channel_to_frequency(Cfg80211_Chan[IdLoop], Cfg80211_Chan[IdLoop]>14?IEEE80211_BAND_5GHZ:IEEE80211_BAND_2GHZ);
               pChannels[IdLoop].hw_value = IdLoop;

               if (IdLoop < CFG80211_NUM_OF_CHAN_2GHZ)


```
[*]Edit /usr/src/rt3090-2.4.0.4/dkms.conf and add the following to the end of the file:
```

PATCH[0]="linux-3.diff"
PATCH_MATCH[0]="(2\.6\.39.*|3\..*)"

```
[*]Run "dkms install rt3090/2.4.0.4"
[/LIST]

I've done this in a VM and it has compiled cleanly but I won't know if it actually worked until tonight.

This might not be the best way to do things but as a quick and dirty change it might work.

---

### Post by rodhull on 2011-10-19
On my system (a Lenovo S205 running 64-bit 11.10) these patches fail with:
```
applying patch linux-3.diff...patching file os/linux/cfg80211.c
Hunk #1 FAILED at 2059.
Hunk #2 FAILED at 2620.
```Instead, I just manually edited cfg80211.c, and reverted dkms.conf removing the 
patch lines you suggest, and it builds/installs perfectly.

However, the module does not seem to work correctly once installed.

I blacklisted rt2800pci, rt2800lib, rt2x00pci and rt2x00lib and upon a  reboot the rt3090sta module was automatically loaded, but I had no  networking. 

/var/log/syslog is flooded with messages of the form:
```
Tx Power, BBP R49=10, TssiRef=10, TxAgcStep=1, step = +0
```I've gone back to the built-in rt2800pci module for the time being which  at least connects etc. - as long as you have the following somewhere in your /etc/rc.local:

```

rfkill unblock wifi
rfkill unblock all
modprobe -r acer-wmi

```...but it's severely throttled in speed - max. d/l  speeds seem to be no more than ~100kb/sec where my WLAN is running at  approx 15Mbps... Unfortunately it isn't consistent - sometimes it *does* operate at full-speed, but after a time may revert back to the throttled speeds...

Anyone else with any ideas on how to get this adapter running at full-speed permanently? 

It seems to be quite a popular chipset which is found in a number of large manufacturers hardware (Lenovo, HP, Acer etc.). Very surprising that it appears to be crippled under Ubuntu...

---

### Post by dan_a on 2011-10-19
> **rodhull said:**
> 
/var/log/syslog is flooded with messages of the form:
```
Tx Power, BBP R49=10, TssiRef=10, TxAgcStep=1, step = +0
```I've gone back to the built-in rt2800pci module for the time being which  at least connects etc. - as long as you have the following somewhere in your /etc/rc.local:

[CODE]


I'm getting the same.  I'll keep working on it and see if I can figure out what's happening.

---

### Post by dan_a on 2011-10-20
I disabled the wireless interface in /etc/network/interfaces and then rebooted.
After doing this I was able to do some magic with iwpriv and get wpa_supplicant working properly - and no packet loss!

I'll try to figure out what the exact steps to make this work are and post them up soon.

---

### Post by rodhull on 2011-10-21
[This thread]("http://ubuntuforums.org/showthread.php?t=1794360") has a few pointers to a similar issue. Have you tried disabling hardware encryption (as per post #25).

I haven't had time to test, but I assume that it should still be able to connect to encrypted networks using software?

**EDIT:**

Disabling hardware encryption with "options rt2800pci nohwcrypt=1" in /etc/modprobe.d/rt2800pci.conf has no effect :(

The behaviour still stands - for the first few minutes of the module being loaded, the WLAN performs at maximum speed, but after a few minutes, the speed becomes seriously throttled...if you unload, then reload the module you will get faster speeds again for a few minutes before it reverts to the sluggish "norm".

---

### Post by robu on 2011-10-24
Same problem with my netbook also having the rt3090.

For Ubuntu 11.04 I solved the problem by blacklisting rt2800lib, rt2800pci, rt2x00lib and rt2x00pci. Then it uses the rt2860 with no problems.

For Ubuntu 11.10 using no blacklisting results in an unstable WLAN connection. After very slow attempts, requesting the user to provide passwords, which are already configured, the connection comes up after several retries and minutes. 

Using the blacklisting results in no WLAN network at all.

Did not found good instructions on how to install a proper driver. Attemps to download/use rt3090sta or rt2860sta failed.

I noted that /lib/firmware/rt3090.bin is a link to rt2860.bin.

I noted also that the lshw command is very slow.

---

### Post by moteprime on 2011-10-25
I used three weeks working on this problem on my Lenovo s205.
This thread helped me to finally make it work:
[http://ubuntuforums.org/showthread.php?p=11377614]("http://ubuntuforums.org/showthread.php?p=11377614")

I installed this driver: [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)
It did not work with newer driver.

Blacklisted "acer_wmi" in /etc/modprobe.d/blacklist.conf

Added "rt3090sta" til /etc/modules

I reported a bug on it this problem:
[https://bugs.launchpad.net/ubuntu/+bug/875659](https://bugs.launchpad.net/ubuntu/+bug/875659)

---

### Post by rodhull on 2011-10-25
Thanks for the advice **moteprime**.

I'll try this when I get home. How did you settle on which specific version of markus' driver worked? Did you just use trial/error (I take it 2.3.1.7 didn't work either)?

Using the default rt2800pci module I have had better results recently since I totally disabled IPv6 by adding the following 3 lines to */etc/sysctl.conf*

```

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

``` I had noticed a good few messages in */var/log/syslog* regarding the WLAN and the associated unavailability of IPv6 (which I don't use at all) so thought that trying to disable it wouldn't hurt...I also changed the "Method" under the IPv6 tab for all connections in Network Manager to "Ignore" for good measure too...

I can't say for sure whether it's more stable speed-wise since I haven't used it for extended periods of time transferring large files via SCP (which is my usual benchmark), but since disabling IPv6 it definitely seemed to be running at full-speed for longer than usual the last time I used the S205.

I'll certainly try the RT3090 staging driver too, however...I always think it best to have a dedicated driver rather than a module that incorporates many different chipsets.

---

### Post by moteprime on 2011-10-25
Unfortunately I have to admit to not being very clever, all this is very complicated to me.

There are more than five ways i have tried that work, including ndiswrapper. But they all suffer from very slow network speed.
By instinct i tried the newest driver, but it did not work, so I tried the next going back, (which "cirelosborn" described, leaving me with the impression that he tried several versions) . And combined with the blacklist and the loading of the module ít just worked. Earlier i have tried every combination, of all that i could find on the net. 

To me the problem seems be that the ralink driver has been updated in 11.10, and it doesn't work with rt3090, possibly combined with the conflict with acer_wmi.

It seems to be a simple problem that could be fixed, and I have reported a bug on it (se above link), but i think that maybe i did not do it right.
If anybody can report this bug right, maybe we could get it fixed. (please post the link here).

---

### Post by rodhull on 2011-10-26
Well, my earlier posts about disabling IPv6 helping things are totally unfounded - the performance is no better after all...after using it for a solid few hours last night I found my speed dropping to ~100kb/sec after a time for local SCP transfers between the laptop and the main PC over the WLAN.

Your tip also didn't work unfortunately.

I installed the .deb you pointed to which *was* successful and indeed appeared to build correctly.

Upon rebooting (even after backlisting/rmmoding acer-wmi and adding rt3090sta to /etc/modules) I had no WLAN connectivity via Network Manager. lspci showed that the driver *was* associated with the adapter, and the module was loaded OK - I appeared to have an interface - it had changed its name from "wlan0" to "ra0" but whatever I did, Network Manager did not see it and I essentially had no WLAN. Is there anything I can do at this point to allow NM to "see" the interface? Not an expert in this area unfortunately...I'd prefer to use NM to facilitate the connection.

I tried all sorts of things like blacklisting and/or rmmoding the rt2800/rt2x00 modules but it still left the same results: a loaded rt3090sta module and an interface but no connectivity with Network Manager. I didn't try any manual console "iwconfig" commands, however...

I'm not up on the inter-workings between NM and wireless interfaces, so don't know where to go from here...I've gone back to the regular rt2800pci for now.

Anyone have any more success or tips to get Markus' dkms package working under Oneiric?

---

### Post by moteprime on 2011-10-26
I'm really sorry it did not work for you. Just to be sure what I did.

Hardware: Lenovo S205 E-450
Ubuntu 11.10 Desktop 64bit (AMD)
uname -a
Linux Ideapad-mot 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


The file I installed: rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb

In my: /etc/modprobe.d/blacklist.conf
blacklist acer_wmi

(There are other blacklists but they are all default. My installation are "Clean", not upgradeed).

In my: /etc/modules
rt3090sta


I have tried all kinds of ways to get it to work, and they did. But always with the sub 100Kb/s speed.
If you (or anybody) need more info on my installation or system don't hesitate to ask, I will do what I can to help solve this.

---

### Post by rodhull on 2011-10-26
Are you certain of the spelling of the acer module? On my system it is listed as "acer-wmi" NOT with an underscore as you mention.
Did you not also have to blacklist the built-in rt2x00 modules?

Would you mind posting back the results of the following commands so I can try to compare with my own?

```

lspci -v

modinfo -v rt3090sta 

lsmod |grep rt

iwconfig


```

---

### Post by moteprime on 2011-10-26
No problem, I'm happy to help if I can.

```

lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9806 (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 397b
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 2000 [size=256]
	Memory at f0200000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
	Subsystem: Lenovo Device 397b
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f0244000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at 2118 [size=8]
	I/O ports at 2124 [size=4]
	I/O ports at 2110 [size=8]
	I/O ports at 2120 [size=4]
	I/O ports at 2100 [size=16]
	Memory at f024a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0249000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f024a500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0248000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f024a400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
	Subsystem: Lenovo Device 397b
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Lenovo Device 397b
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f0240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.2 PCI bridge: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f0100000-f01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
	Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
	Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
	Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
	Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
	Flags: fast devsel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
	Subsystem: Lenovo Device 397b
	Flags: bus master, fast devsel, latency 0, IRQ 42
	I/O ports at 1000 [size=256]
	Memory at f0004000 (64-bit, prefetchable) [size=4K]
	Memory at f0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
	Subsystem: Lenovo Device f101
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0100000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2860
	Kernel modules: rt3090sta, rt2800pci

```

```

modinfo -v rt3090sta 
modinfo: invalid option -- 'v'
Usage: modinfo [-0][-F field][-k kernelversion][-b basedir]  module...
 Prints out the information about one or more module(s).
 If a fieldname is given, just print out that field (or nothing if not found).
 Otherwise, print all information out in a readable form
 If -0 is given, separate with nul, not newline.
 If -b is given, use an image of the module tree.

modinfo  rt3090sta 
filename:       /lib/modules/3.0.0-12-generic/updates/dkms/rt3090sta.ko
version:        2.3.1.3
srcversion:     FFE8374362ED5B734E14328
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

```

```

lsmod |grep rt
parport_pc             36962  0 
rts5139               351143  0 
rt3090sta             885958  1 
parport                46562  3 parport_pc,ppdev,lp

```

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"moteprime"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 00:19:70:3B:DE:04   
          Bit Rate=65 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-47 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

As you can see modinfo did not accept the "-v", but ran it without it.
I am 100% sure acer_wmi is with an underscore, it is copy/pasted from my "/etc/modprobe.d/blacklist.conf". Just blacklisting this single module is enough the make wireless work, (if we do not consider the network speed). There most be more than one bug in this S205 wireless issue.

Here are my /etc/modprobe.d/blacklist.conf

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# Lenovo S205 fix - indsat af mig selv.
# blacklist rt2800pci
# blacklist rt2800lib
# blacklist rt2x00pci
# blacklist rt2x00lib
# blacklist rt2860sta
blacklist acer_wmi

```

---

### Post by rodhull on 2011-10-26
Great thanks!

Sorry about the extra "-v" . I wasn't near a computer and  going from (my admittedly poor) memory!

Do you have anything in your /etc/rc.local ?

---

### Post by moteprime on 2011-10-27
Hi.
No, my /etc/rc.local is completely empty. -it's not true, but everything has "#" except "exit 0".

---

### Post by rodhull on 2011-10-27
Well, I'm giving up with this I think - I spent literally hours with it last night and whilst I got the driver/module to load and service the WLAN card, Network Manager simply could not connect to my WPA2-PSK-protected network when it can fine with rt2800pci.

I see these 3 lines repeated many times flooding the syslog like this:

```

Trying to associate with SSID 'THEODEN'
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.
```This looks to me looks like the auth is failing (or more likely WPA2-PSK support is broken for WPA_Supplicant in the rt3090sta module) - what kind of security does the WLAN you can successfully connect to have?

Also worth pointing out that NM cannot even scan for nearby WLANs either - "sudo iwlist scan" produces no results either.

I'm going to try following up with some of the guys on the rt2x00 project or perhaps raise a bug myself - I noticed someone on the rt2x00 website's forum has a very similar issue whereby his card will drop its speed to ~1Mbps after a time - sounds exactly what's happening here...

---

### Post by moteprime on 2011-10-27
I'm really sorry to hear that it did not work, i know how frustrating it can be.
Please post the bug number if you report a bug on it, which i really think you should.
Would it be any help if i try following my own steps on a live usb pen to see if it works on a clean Ubuntu, i have been doing a lot of experimenting on my installation?

And also, a lot of other people has the Lenovo s205, have any of you got it working on 11.10, and how?

---

### Post by rstefan on 2011-10-27
I tried moteprime's method and worked for me. It looks like I can connect to WPA2-PSK networks now. I have to try at home when i get back from work to be 100% sure :).

---

### Post by jcneto on 2011-10-27
Hi all for it's worked!!! Thanks

I used the solutions of rodhull in the post #21 and the solution of moteprime at #24 together... 

For the file used to install be sure that is this version... any other that I've tested don't work 

Thanks very much!!!

---

### Post by rodhull on 2011-10-28
Feeling a bit left out now! Can't understand why it won't work for me!

Tried it a number of times now, sure the module/driver installs and works but I simply cannot get the interface to scan for networks - if I manually enter the details, it simply never connects :(

I actually got the latest source code for the RT3090 driver direct from Ralink's site to compile last night (I had to manually patch one of the source code files using a couple of separate diffs I've collected from all my troubleshooting I've been doing recently - one from dan_a earlier in this thread, and the other from Markus' PPA) but even though the module/driver loaded and appeared to be servicing the card, it essentially locked out Network Manager (I had no icon in the notification area) and many console commands essentially hung too. The following was logged repeatedly to syslog:

```

Tx Power, BBP R49=10, TssiRef=10, TxAgcStep=1, step = +0
```

The only way I could get my machine back in a usable state was boot to recovery, re-mount the root partition as r/w and remove the listing from /etc/modules for the rt3090sta driver.

Back to square one now...:(

---

### Post by moteprime on 2011-10-29
Maybe a reinstallation of Ubuntu, and starting from scratch would be a solution?

---

### Post by rodhull on 2011-10-29
Ah - the Microsoft approach ;-)

Think I'll persevere with rt2800pci in its current state and submit a proper bug report when I have time to collect all the stats etc.

---

### Post by moteprime on 2011-11-01
Has any of you other Lenovo s205 owners reported a bug on this driver problem?

---

### Post by nitroguy on 2011-11-01
I've got another thread going with moteprime dealing with this issue (here: [http://ubuntuforums.org/showthread.php?p=11409680#post11409680](http://ubuntuforums.org/showthread.php?p=11409680#post11409680)) but thought I'd update here as well in case anyone has any suggestions.

Doing a bit more digging here.

Perhaps I have the wrong driver? Although a "modinfo 3090sta" states I have 2.3.1.3, which is correct, as mote says.

However, on the archive site ([https://launchpad.net/~markus-tisoft...+build/1491488](https://launchpad.net/~markus-tisoft...+build/1491488)) it states it's for i386. Forgive my ignorance, but isn't that 32bit? Are you running 11.10 32 bit, or 64 bit? I've got 64 bit installed, as I thought that was the appropriate version. Is this incorrect perhaps?

---

### Post by moteprime on 2011-11-02
Hi nitroguy
About the 32/64 bit, I am also using Ubuntu 64 bit version.
I found the solution here: [http://ubuntuforums.org/showthread.p...ghlight=rt3090](http://ubuntuforums.org/showthread.p...ghlight=rt3090)
At first I, out off habit installed the newest version, but had no luck, then I checked up on the version used by cirelosborn, and the 2.3.1.3 worked.
I did notice that the build are for i386, but it must be working anyway. (i'm new to 64-bit)
And as there are only the one build version i can't be wrong about the version i downloaded, it would have been so easy to get things mixed up. it is 2.3.1.3
rodhull seems to have the same problem as you have now, his network manager does not scan for network. Could it be the same?

---

### Post by rodhull on 2011-11-02
The module/driver is a DKMS one so is architecture-independent - therefore, it will build against whatever kernel headers you have (32 or 64-bit)...it should in theory work on both.

However, it appears that **nitroguy** does indeed have the exact same issue as me.

The module loads, services the WLAN card but Network Manager doesn't "see" it - I bet if you did a "sudo iwconfig scan" you'd get no results either.

I really think that module is broken and can't see how it works on some systems and not others (when essentially they're the same hardware)...it is specfically built for previous builds of Ubuntu, remember...

---

### Post by nitroguy on 2011-11-02
Indeed. Weird that it's sporadic. Definitely good to know that it's architecture independent. Wouldn't have thought that's possible. I'll do a "sudo iwconfig scan" at lunch and see what I get.

I think I'll try the Windows method, and reinstall 11.10 64bit on my 205 (when I get the chance, that is). That way I can be absolutely certain that it works / doesn't on a fresh install. I'll be sure to report back my findings. While I hope that it's not what it takes to get this working, I also hope to find a solution!

---

### Post by moteprime on 2011-11-02
On all of my three laptops the return from sudo iwconfig scan are: "scan      No such device"
Two of them work 100% out of the box?

---

### Post by rodhull on 2011-11-02
Really sorry - my brain is not working very well...

It should be "sudo iwlist scan" - you can substitute your interface name between "iwlist" and "scan" to just scan on that interface...

---

### Post by moteprime on 2011-11-02
> Really sorry - my brain is not working very well...

Don't we all feel like that most of the time... ;-)


iwlist scan does seem to work here...

---

### Post by rodhull on 2011-11-02
It should work for you, since your Network Manager is working fine too with the DKMS module from Markus' site, isn't it?

I wonder if it does on **nitroguy's** install? Since he looks to have the same issue as me, I'd it expect it not to at all like me...

---

### Post by nitroguy on 2011-11-02
"sudo iwlist scan" returns

lo    Interface doesn't support scanning
eth0  Interface doesn't support scanning
ra0   No scan results


Does this tell you anything?

---

### Post by nitroguy on 2011-11-03
In the process of re installing 11.10. Apparently it's not easy, I just got lucky the first time around...

---

### Post by moteprime on 2011-11-07
Hi nitroguy
Are you up and running again?

---

### Post by chipist on 2011-11-07
Moteprime,
 
I too had the same problem.  I tried to install the .deb package from your link, and did the blacklist stuff etc.  Now the wireless networking is enabled, but can not find any networks.  I have not tried command line scanning yet, but I assume it will be the same.
 
I have not swapped network managers yet though, so will try this later
 
This is on 11.10 64bit.

---

### Post by moteprime on 2011-11-07
@chipist. It sounds like you got the same problem as rodhull and nitroguy. We have found no solution, and are waiting for nitroguy's result after reinstalling.

---

### Post by nitroguy on 2011-11-09
Terribly sorry for the delayed response. I've been knee deep in partition woes.

Apparently I got incredibly lucky the first time I installed 11.10 on my S205 (or incredibly unlucky this time around). For the life of me, I cannot get Ubuntu to install to my computer. I've been back and forth with a bunch of threads and people (this being the latest: [http://ubuntuforums.org/showthread.php?p=11436221](http://ubuntuforums.org/showthread.php?p=11436221)), but cannot get the darn thing to load.

I'll be sure to update back as I know more, but unfortunately, wireless is the least of my worries at this point.:(

---

### Post by chipist on 2011-11-10
Hi Nitro,
 
See my thread here...
 
[http://ubuntuforums.org/showthread.php?t=1872913](http://ubuntuforums.org/showthread.php?t=1872913)
 
I never got it to work with startup disk creator, use unetbootin.
 
I never had to do the grub2 to grub stuff, it just worked anyway!  This may be a false trail that is only needed when DUAL booting.
 
You MUST use gparted.  Delete all partitions (right click delete, for swap you need to disable swap partition before you can delete).  When done apply changes.  Then create new partition table and make sure it is MSDOS (which is default).
 
Follow my instructions and keep trying!
 
When you start the install (make sure you have an ethernet connection to you router) and get to the partition page and select something else (I think) you need to click the format partition box when installing at the partiton page.
 
My method DOES work............eventually!

---

### Post by nitroguy on 2011-11-10
Good news, and bad. 

Bad: I still don't have a working Ubuntu installation. Working on it, and I just installed unetbootin, so I'll try chip's recommendation.

Good: I got wireless working! (well, on a live session, anyways). I did: ```
sudo modprobe acer_wmi
sudo modprobe -r acer_wmi
```

Not sure if that carries over to a real install, I'll be sure to update as I know more, but I can confirm that I indeed can connect to a wireless network using the above method.

Now to try installing. Again...

---

### Post by nitroguy on 2011-11-12
And I'm out.

Sorry guys, I just can't waste any more time on this. I absolutely LOVE Ubuntu, but after using it solely for 4 years, I'm going back to windows. I have no idea why this dumb thing won't install, but like I said, I gotta get some work done.

Best of luck, hope to see you around these parts soon. Hope you get your wireless problems sorted asap. Sorry I couldn't be of more help!

Peace.

nitroguy

---

### Post by Enverex on 2011-11-15
I'm having the same issue on Arch Linux. It looks like this card simply isn't supported well in Linux yet.

Disabling acer_wmi is needed to get it to really work at all. When it does work, it's limited to Wireless G speeds and is still a bit scetchy in general (I appear to be using rt2x00 and rt2800 drivers at the same time).

Lets just hope the driver improves soon.

---

### Post by rodhull on 2011-11-18
I haven't looked at this speed issue for a couple of days, but I checked the git commits on wireless and it looks like someone MAY have picked this speed issue up!

Look here - there were a couple of commits in the last few hours - there are interrupt issues with the rt2800pci driver that might be causing the degraded performance:
[http://git.kernel.org/?p=linux/kernel/git/linville/wireless.git;a=commit;h=23085d5796561625db4143a671f1de081f66ef08](http://git.kernel.org/?p=linux/kernel/git/linville/wireless.git;a=commit;h=23085d5796561625db4143a671f1de081f66ef08)
[http://git.kernel.org/?p=linux/kernel/git/linville/wireless.git;a=commit;h=4ba7d9997869d25bd223dea7536fc1ce9fab3b3b](http://git.kernel.org/?p=linux/kernel/git/linville/wireless.git;a=commit;h=4ba7d9997869d25bd223dea7536fc1ce9fab3b3b)

Can anyone with their affected rt3090-chipset machine to hand (I can't since I'm at work and the S205 laptop is at home) try this out? Looks like the latest daily actually is from 16/11 so might not contain it yet...might have to wait until tomorrow, but this is definitely tantalising!

**EDIT:**

Well, looks like you can get a snapshot of the tree here (I'm def. a newbie when it comes to git):
[http://git.kernel.org/?p=linux/kernel/git/linville/wireless.git;a=tree;f=drivers/net/wireless](http://git.kernel.org/?p=linux/kernel/git/linville/wireless.git;a=tree;f=drivers/net/wireless)

I presume you can replace this folder with the one in the daily compat-wireless one so you can use the friendly driver-select script etc...

I suppose you might only actually need the very latest [rt2800pci.c]("http://git.kernel.org/?p=linux/kernel/git/linville/wireless.git;a=blob;f=drivers/net/wireless/rt2x00/rt2800pci.c;h=4dc2d0f840d45d8559a5af36edeb0bef50d6e265;hb=4ba7d9997869d25bd223dea7536fc1ce9fab3b3b") that contains the patch...

I'll be trying this as soon as I get home - if anyone else has any thoughts, please update this thread!

---

### Post by moteprime on 2011-11-19
@rodhull
It looks like they got something, but it's to complicated for me.
Have you tried the patch at the bug at launchpad. -it did not work for me. -I'm a bit unsure if I did it right.


if others are interested: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659")

---

### Post by rodhull on 2011-11-20
It's actually very simple:

1) Get the newest daily of compat-wireless from:
[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

2) Unpack

3) Go into the dir you unpacked, and do:

```
./scripts/driver-select rt2x00
```4) Then, run "make" and "sudo make install"

5) Reboot

The process will install new wireless drivers using the following as the base /lib/modules/3.0.0-12-generic/updates/ rather than the built-in path of: /lib/modules/3.0.0-12-generic/kernel/

The system will use the "updates" folder to look for kernel modules over the default.

To reverse the process, simply go back into the compat-wireless folder you unpacked and run "sudo make uninstall".

I've tried it, and I've confirmed the patch is definitely in there, but it hasn't made any difference to the speed for me - I've posted on the rt2x00 forums about it - hopefully someone will look into it further - I'll try raising a separate bug with Ubuntu later on (I think the speed issue is sufficiently different to the acer_wmi conflict you have already reported).

People using Fedora and RedHat have reported the issue too (it was how the IRQ handling patch was created - from following up on a reported RedHat bug). I'm pretty positive the issue is not confined to Ubuntu in general, and it's the rt2x00 drivers that are at fault for this particular chipset (RT3090).


**EDIT**

Well, I rebooted again (having installed the daily compat-wireless package from 18/11) and used the laptop for a good few hours last night and couldn't see any discernible speed reduction this time! Looks like this may have been fixed but I may have just got lucky - usually the speed will be fine for a while and then it drops - it rarely starts out slow straight after bootup - I must say I've never used it for so long with decent WLAN speeds however. I was copying large files in the background and surfing at the same time and it seemed fine.

I didn't try the new kernel patch from your bug, **moteprime** since you'd reported it hadn't worked. I think you did it correctly. You should only need to install the 3 .deb files and reboot (the .patch files were only included by Ike I think just so anyone can see the changes made to the underlying code included in the patched kernels) - the system will automatically use the patched kernel from then on since it replaces the generic version. For me, the workaround for that bug (blacklisting/removing the acer-wmi module) is trivial and I've been focussing more on getting the speed improved since I still think they're mutually exclusive bugs - esp. seeing as the latest compat-wireless certainly seems to improve things...

---

### Post by payload on 2011-11-21
thanks for all this testing and giving information!

i did
```

echo blacklist acer-wmi > /etc/modprobe.d/blacklist-wlan.conf
modprobe -r acer-wmi
# reading and downloading http://linuxwireless.org/en/users/Download
# choosed driver-select rt2x00
modprobe -r rt2800usb && modprobe -a rt2800usb # maybe i did more here, see modprobe --show-depend

```

testing connection speed on different networks tomorrow

slow on:
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on

---

### Post by moteprime on 2011-11-22
rodhull
Through the testing of the kernels that Ike Panhc on Launchpad suggests, I have discovered a strange behaviour regarding my solution in post #20. If I at any time connect my s205 through the wired LAN port the speed of the wifi drops to the below 70kb/s and cannot, no matter what I do work at full speed again.
But if I reinstall the "rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb" driver again. (with wired network NOT plugged in) and restart, the wifi is again at full speed!
I have tried to plugin the wired network cable again, and the behaviour are the same. the wifi speed breaks until I reinstall the driver.

> I'll try raising a separate bug with Ubuntu later on (I think the speed issue is sufficiently different to the acer_wmi conflict you have already reported).

The bug that I reported on launchpad was to get both the acer-wmi issue and mostly the speed issue fixed, but I am inexperienced at reporting bugs and should have chosen another summary or title for the bug.

I think that reporting a new bug for the network speed issue would be a good idea, and if you could find the time to do it i think that you will do a better job than I did. ;-)
Please post a link.

Thank you for confirming that I installed the test kernels right, I haven't figures out how to get them uninstalled and still being able to boot up again. so I have to reinstall my test system every time. I will try the new compat-wireless driver as soon as i have tested the last test kernel that Ike Panhc suggests.

---

### Post by rodhull on 2011-11-22
There's basically something weird about the networking hardware in this laptop - wish I'd have known before I bought it since it's causing me no end of grief!

I have realised that the fix applied to the latest compat-wireless DOES NOT work after all - I had just got lucky that time I managed to surf for a few hours with no speed drops - tried again last night, and within about 5 minutes of booting up it was crawling along at sub 100kb/sec speeds :(

I'll definitely try to submit a bug report ASAP...

---

### Post by moteprime on 2011-11-22
I wont test the compat-wireless driver unless you want me to then?

The last three laptops i have bought had these kinds of problems for at least half a year after they where introduced, its always a matter of time before there drivers get up to date. -i hope. ;-)

It is not only when i plug in the cable that i have the speed dropping, but also when i have booted in the test system i have installed, and boot back up i my working everyday system. The other drivers must be setting something in the chip that the rt3090-dkms_2.3.1.3 driver cannot handle before i have booted a couple of times.

I just received a mail from the bug on launchpad, he thinks the patch worked.

---

### Post by chipist on 2011-11-22
Just a quick note to give a very temporary solution to this, I use my android phone tethered to the S205 and use the tethering on my android phone (wia WIFI) to get a connection.  Obviously this is not the answer but as a quick fix........

---

### Post by moteprime on 2011-11-22
BTW. complete of topic, but a new BIOS version has been release for Lenovo S205. date: 20 Oct 2011

---

### Post by rodhull on 2011-11-25
Well, if you know how to apply BIOS updates to Ideapads without having to use Windows - I do not have a dual-boot mechanism - my sole OS is Oneiric. I have tried using Wine to run the BIOS flasher - at the error, I delved into the temporary directory where the contents of the .exe are extracted to and ran the updater manually there which worked (having modified one of the conf files to ignore that I had a valid battery  since Wine couldn't detect the battery installed) but wasn't brave enough to finally click on the final confirmation to update! If anyone knows how to SAFELY update via Linux I'd love to know...

In relation to the speed issues, I'm happy to report that I'm having very good WLAN results in Oneiric (finally) by using the stock  Ubuntu 3.0.0.13 kernel combined with compat-wireless from 22/11/11 PLUS  turning power-saving off on the WLAN interface. No speed drops anymore, no kernel panics, no problems resuming - basically everything "just working".

---

### Post by moteprime on 2011-11-26
Rodhull
For updating the bios, this guy has a solution that looks ok.
[http://ubuntuforums.org/showthread.php?t=1867367]("http://ubuntuforums.org/showthread.php?t=1867367")
I always keep windows on some small partition fort things like this.

I'm glad to hear that your wifi problems are getting to a point where its working.

I still think that we should report a bug on it. Will you do it or should I? -i do believe you will do a better job at it that me.
For the testing i have a partition with a clean installation, thats installed just for testing, so can do testing.

---

### Post by rodhull on 2011-11-26
It looks like the S205 has a different BIOS flasher/ROM than the laptop that guy used as an example. You cannot extract it using an archive manager.

This how far I got:

Basically, if you run the flasher with Wine (it will error out, but make sure you keep it open), open another terminal window and go to in your Wine temp folder (usually something like ~/.wine/drive_c/users/username/Temp) you will see a new folder called "WinFlash". In here you'll find the flasher itself (WinFlash.exe) and a bunch of other files.

You can then try and run "WinFlash.exe" by itself. This will error out too since it cannot sense that the power adapter is plugged in (even when it is).

You can edit WINFLASH.INI and change the values of "AC=" and "Battery=" to "0" so that it won't check for the presence either.

Then run WinFlash.exe again with Wine and it looks like it will let you start the procedure - I was never brave enough to actually do it though! If anyone has a test system it would be good to give it a go!

As for the speed issue - I agree it probably ought to have a bug raised for it - don't quite have time at the moment and you sound like you have a good test environment set up for this! Go for it - I'm happy to chip in and test - the acer_wmi issue is looking well on the way to being solved so that's great!

---

### Post by moteprime on 2011-11-26
I would not dare to do it either ;-)
For what I read about the update it solves some windows related issues, and I have not experienced any differences after the update myself.

[B]I reported the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/896582]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/896582")
[/B]
Please add any information you find necessary.

Everyone that's reading this please follow the link and click that this bug affects you under the heading, and subscribe if possible, so that we can get this fixed.

---

### Post by CFBauer on 2012-01-20
> **rstefan said:**
> Hello,

Try to remove the blacklists you made and it should work after reboot. At least this worked for me.
My problem now is that i cannot connect to WPA2-PSK wireless networks.

Regards!
Booyah! It worked, thanks a ton!

---

### Post by nitroguy on 2012-02-07
Hey all!

I'm back up and running on ubuntu (LOVING it, as always!).

Has there been any progress made in the area of wireless? I'm using my method posted on the previous page, but as has been said, it's spotty, unstable, and subject to slow speeds. Has anyone come up with a more permanent fix?

Thanks! Glad to be back in the game!

nitroguy

---

### Post by moteprime on 2012-02-08
Hi nitroguy
We reported two bugs, one on the acer-wmi conflict (solved now) and one on the slow network. (see post #67)
I'm still running successfully with full network speed using method in post #20

---

### Post by rodhull on 2012-02-08
Well, I completely gave up and simply didn't have time to continually test everything - I never got that pre-built DKMS package to work either but I did manage to find out how to successfully compile the Ralink driver direct from their website and am using that with zero problems (along with having to blacklist acer_wmi as previously suggested).

Here's what to do if anyone's interested. Once downloaded, unpack and edit as follows:

in the file ../common/cmm_wpa.c :

```


UCHAR PrimaryRsnie;
  BOOLEAN bMixCipher = FALSE; // indicate the pairwise and group cipher are different
  UCHAR p_offset;
- WPA_MIX_PAIR_CIPHER FlexibleCipher = MIX_CIPHER_NOTUSE; // it provide the more flexible cipher combination in WPA-WPA2 and TKIPAES mode
+ WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES; // it provide the more flexible cipher combination in WPA-WPA2 and TKIPAES mode

```

then lastly in the file ../os/linux/config.mk :
```

HAS_GREENAP_SUPPORT=n
 #Support MAC80211 LINUX-only function
-HAS_CFG80211_SUPPORT=y
+HAS_CFG80211_SUPPORT=n

 #Support RFKILL hardware block/unblock LINUX-only function
 HAS_RFKILL_HW_SUPPORT=y

```

Run "sudo make ; sudo make install" and you should have a working built module/driver.

It's helpful to blacklist rt2800pci so the system doesn't use this - it will use the new rt3090sta/rt2860 instead after a reboot...

Incidentally, the memory footprint of Unity/Compiz and/or Gnome 3 all started to annoy me too, so I'm using Mint 12/Mate now with excellent results - much less memory usage and a far more responsive system with less swapping to disk due to low physical memory (my S205 only has 2Gb of RAM where 512Mb is reserved as video RAM).

---

### Post by moteprime on 2012-02-08
Hi rodhull. -long time no see. :-)

If you successfully used the driver from ralink, wasn't this something the guy trying to solve the bug on launchpad could use to get it fixed?

---

### Post by rodhull on 2012-02-08
Hey - not really I don't think - the issue is with the kernel and the built-in open-source rt2x00 driver, not the proprietary Ralink one...

---

### Post by nitroguy on 2012-02-09
Hey rodhull! Sorry to see you leave the land of 'buntu, but glad you're happy (and staying away from the dreaded land of Microsoft) :-)

Mote- I'll give your #20 post a shot again, although I do recall that it didn't work for me the first time around. Perhaps between post 20 and rodhull's latest, I'll get something working. I'll be sure to post back results of what I get working.

---

### Post by rodhull on 2012-02-10
Installing the driver from source is working absolutely fine for me - no idea why the pre-built package never worked for me, but the install is so simple (having learned which bits of the source to change to get it to build) I'm totally happy with this solution. I actually found the instructions on another launchpad bug report for another wireless problem that was related to this one...if I can find the link I'll paste it in later on...

Well - I'm not strictly leaving Ubuntu - Mint is essentially Ubuntu with a fork of Gnome 2 (MATE) plus a more friendly variant of Gnome 3 (MGSE) - same repos/packages for everything else for the most part.

I just find Unity/Compiz so memory-hungry (and the performance is really not snappy enough for me on the whole unless you have ~4Gb+ RAM if you are used to having lots of programs and/or browser tabs open). 

On my Lenovo S205 (2Gb RAM - 512Mb reserved for video, 1.5Gb left for everything else) it's difficult to have user switching enabled for 2 users since the footprint of Compiz/Unity whilst two users are simultaneously logged in only leaves a few hundred Mb left free - open more than a couple of tabs for each user in their browsers and the system starts having to swap like crazy (even with vm.swappiness dialled right back).

I still use Ubuntu LTS on all my Linux headless servers (no X you see!) and if I have any servers doing XDMCP in the future I'll use releases pre-11.10 since there's still the ability to use Gnome 2 without any real hacking about...

Also I've still got Ubuntu on my two other desktops I use regularly - one is still on 11.04 for the same reasons above and I'm trialling Cinnamon and MATE desktop on the other Oneiric machine - simple to install ontop of "standard" Ubuntu.

Since Mint shares so much in common with Ubuntu wireless probs like this are still very much there however!

---

### Post by moteprime on 2012-02-15
@Rodhull.

You are right the memory usage are to large, and several processes memory usage just keeps growing to what seems to be more that reasonable. 

How do you get to switch between users that are logged in without getting that good'old, it ends in black screen after a couple of switches?

I have been checking up on your driver, I find it more sensible than the pre-built DKMS package that only works in one specific version and not the others.
The drivers(*) that I download from the Ralink support page has different code than you described in you post. What driver are you using?
Thanks


(*)
RT3090PCIe
RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)

---

### Post by rodhull on 2012-02-15
Well, as for the user switching - I I really don't know what causes that behaviour - I used to see it too when using Oneiric but I don't get it under Mint - again, it could well be Unity to blame?

The driver I used was from this page:
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

...the one listed as "RT3090PCIe" - it gives you a file called:

"2010_1217_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.zip"

My markup to change those files doesn't follow the correct "patch" diff format - it was just from notes I made for myself.

I just checked again, and those locations are definitely there - you're basically just changing one line of code in each of the two files (the lines that need removing are marked with a "-" and the line that you need to replace with has a "+" - the other lines are just so you can navigate to the correct block of code - there may be parts where there are very similar-looking sections...

It works fine but you do have to keep the source code handy and "sudo make clean; sudo make; sudo make install" each time having installed a new kernel - that's when having a DKMS package is more useful!

---

### Post by moteprime on 2012-02-15
@rodhull
You are right, and if i had payed more attention to what I was doing i would have found out myself. I got it installed and it works fine.
Thanks!!

---

### Post by moteprime on 2012-02-19
@rodhull

What would it take to make a dkms packeage out of this driver code?
My english aren't good enough to make proper jokes about this, but i am not suggesting that you go and make one, I'm just wondering about it. I have seen that some times people are relatively easy making packages out off the proprietary driver code.

---

### Post by kpuz on 2012-02-20
> **rodhull said:**
> Well, I completely gave up and simply didn't have time to continually test everything - I never got that pre-built DKMS package to work either but I did manage to find out how to successfully compile the Ralink driver direct from their website and am using that with zero problems (along with having to blacklist acer_wmi as previously suggested).

Here's what to do if anyone's interested. Once downloaded, unpack and edit as follows:

in the file ../common/cmm_wpa.c :

```


UCHAR PrimaryRsnie;
  BOOLEAN bMixCipher = FALSE; // indicate the pairwise and group cipher are different
  UCHAR p_offset;
- WPA_MIX_PAIR_CIPHER FlexibleCipher = MIX_CIPHER_NOTUSE; // it provide the more flexible cipher combination in WPA-WPA2 and TKIPAES mode
+ WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES; // it provide the more flexible cipher combination in WPA-WPA2 and TKIPAES mode

```

then lastly in the file ../os/linux/config.mk :
```

HAS_GREENAP_SUPPORT=n
 #Support MAC80211 LINUX-only function
-HAS_CFG80211_SUPPORT=y
+HAS_CFG80211_SUPPORT=n

 #Support RFKILL hardware block/unblock LINUX-only function
 HAS_RFKILL_HW_SUPPORT=y

```

Run "sudo make ; sudo make install" and you should have a working built module/driver.

It's helpful to blacklist rt2800pci so the system doesn't use this - it will use the new rt3090sta/rt2860 instead after a reboot...

Incidentally, the memory footprint of Unity/Compiz and/or Gnome 3 all started to annoy me too, so I'm using Mint 12/Mate now with excellent results - much less memory usage and a far more responsive system with less swapping to disk due to low physical memory (my S205 only has 2Gb of RAM where 512Mb is reserved as video RAM).

Hi rodhull, 

Thank you for this post.  I just want to clarify something before I proceed.  In the changes you made, anything that starts with a netagive sign (-) should be removed and anything starting with a positive sign (+) should be added.  Is this correct?  Please forgive me as I don't know the conventions of compiling modules.  

Secondly, in the readme file for the Ralink driver, they also ask to make certain changes to the makefile and the config.mk files.  Did you make those changes as well.  Thanks for your work so far.  

I am having some problems with the rt2800pci module which is allowing me to connect to the internet with sub-optimal speeds.  When I run iwconfig wlan0, it shows a very large amount of 'Tx excessive retries' and 'Invlaid Misc' counts.  It also ends up slowing down the internet connection for everyone else on the network as soon as I connect.  I'm hoping the Ralink driver is able to solve these issues and hopefully even give me 802.11n speeds finally on linux.

Edit: It worked great. No more Tx excessive retries or Invalid Misc with this driver (2010_1217_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.zip from [http://www.ralinktech.com/en/04_support/license.php?sn=5015](http://www.ralinktech.com/en/04_support/license.php?sn=5015)).  Currently I am unable to check if I can get n-speeds because I'm on a g-speed router.

---

### Post by frncz on 2012-02-25
Rodhull's instructions to compile rt3090 worked fine, and somehow my network speed on my Lenovo S205 running precise pangolin increased from 0.4 Mb/s to 6 Mb/s. Fantastic, as this is a good as for any of my other laptops.
However, I think I can't blacklist the acer_wmi. If I do, I can't connect.
Anyway, many thanks Rodhull

---

### Post by Klopapier on 2012-03-16
Hi, I just got the S205 (E-450, RT3090) and managed to install ubuntu 11.10 with the help of this forum (thanks!). I'm quite unexperienced with Ubuntu (only installed on older PCs with everything working out of the box). Unfortunately I can't manage to get wireless working...

I tested all steps from the beginning of this thread also in different combinations (modules, blacklisting, driver, even compiling) with setting up the system new 5 times.

Could you please tell me which combinations gets the RT3090 to work in the S205?

Thanks!

---

### Post by moteprime on 2012-03-16
klopapier.
What works for me, and most others are this:

Clean up what you tried until now.

Download and install this driver, and it has to be the exact verion:
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb]("https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb")

In the file  /etc/modprobe.d/blacklist.conf
Put in "blacklist acer_wmi" in the end, with no quotes.

And in the file /etc/modules
Put in "rt3090sta" in the end, no qoutes.

If it does not work, then try the solution rodhull described.

And off topic, about graphics driver send me a mail, im or pm me an i will guide you.

---

### Post by i_am_lost on 2012-05-05
>In the file  /etc/modprobe.d/blacklist.conf
>Put in "blacklist acer_wmi" in the end, with no quotes.


Download kernel source, make, and sudo make install this:

compat-wireless-3.4-rc3-1.tar.bz2

This works 100% with 12.04 LTS kernel 3xx on amd64....

There is only one driver package for the rt5890 that works in client mode for the rt3090:

[B][U][https://launchpad.net/~marko-techytalk.info/+archive/ralink-wireless]("https://launchpad.net/%7Emarko-techytalk.info/+archive/ralink-wireless")
[/U][/B]
This will enable you to connect to wireless.  Note, you will have to **_re-enable 2800 mods_**, and  >_**purge**_< any driver deb package you installed before installing the new .ko 

Do not use the manufacturers website at all... 
 
the card cost me $10... and I still feel ripped off.

---

### Post by moteprime on 2012-08-13
Hi Again.

I got a Bug reported (As Hansen):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/896582](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/896582)
-on the RT3090 Wifi driver on Ideapad s205 , trying to establish if the bug is a regression or not. Can any of you help?

---

### Post by moteprime on 2012-09-28
Hi again.
[B]Have any of you guys tried out 12.10 with the build in driver.
[/B]For me it kinda works. It connect's data comes through, but the speed if going up and down, and different stuff doesn't work well, for example IM takes a long time to connect.

---

### Post by dtzortzis on 2013-02-07
> **rodhull said:**
> 
Run "sudo make ; sudo make install" and you should have a working built module/driver.


I'm getting these errors and I really don't know why :(

```

~/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO (2) $ sudo make
make -C tools
make[1]: Entering directory `/home/dimitris/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO (2)/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dimitris/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO (2)/tools'
/home/dimitris/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO (2)/tools/bin2h
[B] /bin/bash: -c: line 0: syntax error near unexpected token `2'
[/B]/bin/bash: -c: line 0: `/home/dimitris/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO (2)/tools/bin2h'
make: *** [build_tools] Error 1

```

UPDATE: The folder the files are in (20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO (2)) has got spaces in its name. It turns out spaces are bad, bad, bad... Moved it somewhere else and it worked.

---

### Post by moteprime on 2013-02-07
@dtzortzis - I'm on kernel 3.5 and it seems to support RT3090 just fine.

---

### Post by mma8x on 2013-03-02
> **moteprime said:**
> @dtzortzis - I'm on kernel 3.5 and it seems to support RT3090 just fine.

I'm still getting erratic behavior with the 2800pci driver, using both stock 3.5 kernels and the latest 3.8.x ubuntu mainline kernel.  Having an impossible time compiling the 3090 ralink driver.

---

