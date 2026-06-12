---
title: "Dell D620 - keyboard and mouse freeze sometimes on wake from suspend."
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by sgarman on 2007-05-08
I have a brand new Dell Latitude D620 laptop. It works pretty well with Ubuntu Fiesty, but I'm getting an intermittent problem about once per week when waking from suspend/sleep. Xorg  comes back up fine, and the computer is still running, as I can see NetworkManager is connecting to my wifi network. But my keyboard and mouse/trackpad do not work at all. I have to hold down the power button for four seconds to totally kill power to the machine. 

My hardware specs are:

* Intel Core2Duo @ 2.0 GHz
* Intel 950 integrated graphics card (using i810 xorg driver)
* WXGA+ 1440x900 resolution
* 2 GB RAM
* Intel 3945 wifi card

I've searched these forums with various keywords and can't seem to find anyone else with this problem. 

I haven't tried ssh'ing into this machine during a lockup, I will try that the next time it happens if I can. My syslogs don't indicate a kernel panic or anything unusual. 

Any ideas?

Scott

---

### Post by Martin on 2007-05-08
I had a similar problem when I had my laptop setup to hibernate as opposed to suspend. Suspend seems to work a lot better. 
I've also had problems with mouse freeze when I've got a USB drive or memory stick plugged in and I try and wake the system up - but less now that I'm using suspend. Still irritating though

---

### Post by sgarman on 2007-05-09
I've hibernated a few times and never noticed the problem, but it does only happen intermittently. 

So you're saying you suspend and wake up regularly, and have never had the problem on your laptop? Which graphics chipset do you have, the Intel 950 or the NVIDIA?

Thanks,

Scott

---

### Post by Martin on 2007-05-09
My laptop has an ATI Mobility Radeon 6700 and suspend works fine - unless I've got an external USB drive of some sort plugged in - and then only sometimes (but I'll check the 'sometimes' today) Otherwise the laptop is a2 year old NEC M540

---

### Post by sgarman on 2007-05-10
Ok - I had the problem happen this morning. Here's what I did.

Laptop wakes from suspend, keyboard and trackpad do not respond. NetworkManager successfully connects to my network.

I managed to figure out the IP address with a portscan and could ssh in. 

I hooked up a USB mouse, and it worked. Keyboard and trackpad still locked up.

I tried running the /etc/acpi/sleep.sh script via my ssh login, and nothing happened. 

I tried restarting the gdm service via my ssh login, but once again, only the USB mouse worked - not the keyboard or trackpad. 

I saved the output from lsmod, guessing maybe that a kernel module needed for my keyboard was not properly reloaded. 

I rebooted the machine, and then compared the output of lsmod with what was saved.

Modules that were loaded during the crash, but not after a fresh reboot:

* arc4, blkcipher, ecb, ieee80211_crypt_tkip, ieee80211_crypt_wep, libusual, michael_mic, usb_storage. (None of these matter, they're wifi crypto modules or things I was using for usb storage before I had suspended).

Also, the number listed after the kernel module for evdev changed from 4 to 3 (I think that's a reference count of some sort, isn't it?). This interests me because evdev is what handles Xorg events from the keyboard and mouse. 

Any advice on what I could do next time to troubleshoot further would be greatly appreciated. 

Thanks,

Scott

---

### Post by budhe888 on 2007-05-13
I am having the exact same problem, except it is on an HP nc8430 laptop, and it happens EVERY time I wake from suspend.  Now I think a solution might lie somewhere in the MODULES_WHITELIST environment variable, which is set in '/etc/default/acpi-support'

I feel like if we can set that to leave the keyboard and touchpad modules loaded, then they might work upon wake from suspend.  The problem is, I have no idea which modules from the 'lsmod' list correspond to these two:

```

~$ lsmod
Module                  Size  Used by
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
ieee80211_crypt_wep     6144  1 
af_packet              23816  4 
ipv6                  268704  10 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
fglrx                 540004  11 
ppdev                  10116  0 
acpi_cpufreq           10056  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
sbp2                   23812  0 
lp                     12452  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
joydev                 10816  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipw3945               118816  1 
pcmcia                 39212  0 
hci_usb                18204  2 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
soundcore               8672  1 snd
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
parport_pc             36388  1 
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
bluetooth              55908  7 rfcomm,l2cap,hci_usb
psmouse                38920  0 
serio_raw               7940  0 
sdhci                  18700  0 
tpm_infineon            9112  0 
tpm                    16672  1 tpm_infineon
tpm_bios                8448  1 tpm
parport                36936  3 ppdev,lp,parport_pc
intel_agp              25116  1 
mmc_core               26756  1 sdhci
tifm_7xx1              10240  0 
tifm_core               9856  1 tifm_7xx1
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  2 fglrx,intel_agp
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
evdev                  11008  5 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
ata_piix               15492  0 
sd_mod                 23428  3 
usbhid                 26592  0 
hid                    27392  1 usbhid
ata_generic             9092  0 
ehci_hcd               34188  0 
tg3                   109700  0 
generic                 5124  0 [permanent]
ahci                   22020  2 
libata                125720  3 ata_piix,ata_generic,ahci
scsi_mod              142348  5 sbp2,sr_mod,sg,sd_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
uhci_hcd               25360  0 
usbcore               134280  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

From my xorg.conf file, I tried using the driver keywords that were used there, 'kbd', and 'synaptics', but that didn't work.  I'm pretty sure those are not correct.  Anyone know which modules from the above list are the keyboard and touchpad modules?  Otherwise, I will just go through and try each one that might be a candidate.

---

### Post by sgarman on 2007-05-13
Thanks for the reply...hopefully we're close to figuring this one out. 

The modinfo command can be run with the name of any kernel module to get information about what it does. For example:

*modinfo processor*

Scott

---

### Post by chele on 2007-05-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/acpi/+bug/37672](https://bugs.launchpad.net/acpi/+bug/37672) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				On this HP nw8000 laptop, sudo rmmod vesafb allows it to resume from suspend. That is with Ubuntu 7.04 (Feisty). On Dapper, putting nosplash in the grub menu.lst file bypassed the framebuffer and fixed the problem.

How does one permanently block vesafb from loading on Feisty? It still loads even with the nosplash option.

---

### Post by archiesteel on 2007-05-13
I believe the kernel modules responsible for such things as keyboards and mice are "hid" and "usbhid".

I've tried whitelisting these modules as I've also encountered this intermittent problem...I'll let you guys know if the problem happens again or not.

---

### Post by archiesteel on 2007-05-15
> **archiesteel said:**
> I believe the kernel modules responsible for such things as keyboards and mice are "hid" and "usbhid".

I've tried whitelisting these modules as I've also encountered this intermittent problem...I'll let you guys know if the problem happens again or not.

No love, the problem just happened again even though the modules were whitelisted. I have also tried unloading them then reloading them during resume, to no avail.

I'm a bit lost as to what to try next...

---

### Post by archiesteel on 2007-05-15
I connected to my laptop via SSH after it happened again, and looking at the dmesg output I was able to spot these two suspicious candidates:

```
[20840.484000] i8042 kbd 00:06: resuming
[20840.484000] pnp: Device 00:06 does not support activation.
[20840.484000] i8042 aux 00:07: resuming
[20840.484000] pnp: Device 00:07 does not support activation.
```

It seems that the i8042 controller is part of the serio_raw kernel module on Feisty, though trying to stop and restart this module have not help...I'm going to try whitelisting it and see how it goes.

Incidentally, I found this thread (dated from April) on the Linux Kernel Mailing List about resume problems that mentions the i8042 driver:

[http://lkml.org/lkml/2007/4/15/81](http://lkml.org/lkml/2007/4/15/81)

If this is a kernel issue, let's hope that a Ubuntu backport of the latest kernel will be available soon, because it's not going to be easy to fix without recompiling (and for some here that may not be an option).

---

### Post by archiesteel on 2007-05-15
Never mind...I get those messages in dmesg even when the keyboard and touchpad work on resume, so I doubt this is related.

Sorry for the false hopes...I'll post again if I actually find something.

---

### Post by chele on 2007-05-16
> **archiesteel said:**
> No love, ...I'm a bit lost as to what to try next...[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

---

### Post by hpklett on 2007-05-20
Same computer, same problem.  Fix here:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497)

I wasn't able to install the package listed, but I looked at the patch and made the changes.  The result was bizarre, but then I noticed his note about priority right below the patch.  Changing 80 to 40 in the filename as he suggested did the trick.

Summary:
As root, create the following files: 

/etc/acpi/resume.d/40-i8042-input.sh
```
#!/bin/sh

# Rebind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
fi
```

/etc/acpi/suspend.d/20-i8042-input.sh
```
#!/bin/sh

# Unbind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
fi
```

Set them as executable and you're good to go.

---

### Post by budhe888 on 2007-05-20
Wow that worked, thank you!

One small thing however... now whenever I resume, the computer is not locked anymore, it comes up right into my session without having to enter a password (whereas before, it came up on a password entry screen, but with the inputs locked).

It's not a huge deal.  Again, thanks.

---

### Post by budhe888 on 2007-05-20
disregard that last post.  It works fine.

---

### Post by sgarman on 2007-05-21
hpklett, thank you SO much for posting this info! I have tried it and it's working so far. Kind of hard to tell for sure given that it's an intermittent problem, but from the Launchpad notes, I think this should do it. 

Many thanks!

Scott

---

### Post by sgarman on 2008-06-17
I'm running Hardy on my D620 and would like to note that the fixes mentioned above will not work. I've been perplexed for a while that I've ran into this problem again even though I thought I had a workaround for it. The /etc/acpi/suspend.d and resume.d scripts are no longer run, as Hardy uses the pm-utils package. See the following bugs for more info:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/83243](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/83243)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99755](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99755)

Scott

---

### Post by sgarman on 2008-06-19
> **sgarman said:**
> I'm running Hardy on my D620 and would like to note that the fixes mentioned above will not work. I've been perplexed for a while that I've ran into this problem again even though I thought I had a workaround for it. The /etc/acpi/suspend.d and resume.d scripts are no longer run, as Hardy uses the pm-utils package.

Okay, I finally read up on how pm-utils works, and here is a solution that should work with Hardy. 

Create the following file: /etc/pm/sleep.d/25i8042

```
#!/bin/bash

case "$1" in
	hibernate|suspend)
		# Unbind the AT keyboard interface.
		if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
			echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
		fi
		;;
	thaw|resume) 
		# Rebind the AT keyboard interface.
		if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
			echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
		fi
		;;
	*)
		;;
esac

exit $?
```

Make sure this file is executable. There is no need to reboot your computer - your next suspend should work. Please let me know if this works for anyone else.

Scott

---

### Post by ryuko2002 on 2008-06-22
Last character is a "?". Is it right? I just created the file, let's see if it works.

---

### Post by sgarman on 2008-06-22
> **ryuko2002 said:**
> Last character is a "?". Is it right? I just created the file, let's see if it works.

Yes.

It's been working so far for me for a few days.

Scott

---

