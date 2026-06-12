---
title: "Hp Pavilion DV6 Wifi Issues"
date: 2011-03-03
forum: Hardware
---

### Post by rabbitdaone on 2011-03-03
Good day to all reading, having some wifi issues with my newly installed Ubuntu 10.10 32 bit version. 

The blu led stays on as it should, and it connects to the router as it should, but I cant get any access to the internet; whether by browser or other application. 

And there is a blinking thing it does...Seems to happen when its "loading" something that requires the internet, but it never loads...For whatever reason. Right now I dont mind the blinking, as long as the Wifi will actual work. 

Im using an ethernet cable to use the internet now, but seeing as though I am not the only user of the internet, this is not a permanent fix. 

I have a Intel Centrino Wireless-N 1000 card, all help is appreciated. Take care, thanks for reading.

---

### Post by DanneStrat on 2011-03-03
> **rabbitdaone said:**
> Good day to all reading, having some wifi issues with my newly installed Ubuntu 10.10 32 bit version. 

The blu led stays on as it should, and it connects to the router as it should, but I cant get any access to the internet; whether by browser or other application. 

And there is a blinking thing it does...Seems to happen when its "loading" something via that requires the internet, but it never loads...For whatever reason. Right now I dont mind the blinking, as long as the Wifi will actual work. 

Im using an ethernet cable to use the internet now, but seeing as though I am not the only user of the internet, this is not a permanent fix. 

I have a Intel Centrino Wireless-N 1000 card, all help is appreciated. Take care, thanks for reading.

Hi.

Let's start by getting some info about your card.

Do this in a terminal and then post the output:

```
lspci
```

and

```
lsusb
```


Also, let's have a look at:

```
lsmod
```

---

### Post by rabbitdaone on 2011-03-04
@DannStrat:

lspci output:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

lsusb output:
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0408:03f1 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1e3d:6025  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod output:
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40236  1 
usbhid                 36978  0 
hid                    67742  1 usbhid
binfmt_misc             6599  1 
parport_pc             26378  0 
ppdev                   5556  0 
joydev                  8767  0 
arc4                    1165  2 
snd_hda_codec_atihdmi     2411  1 
iwlagn                179815  0 
snd_hda_codec_idt      54919  1 
iwlcore               127479  1 iwlagn
mac80211              231959  2 iwlagn,iwlcore
hp_accel               13204  0 
lis3lv02d               8556  1 hp_accel
lirc_ene0100            6899  0 
snd_hda_intel          22299  4 
lirc_dev                9393  1 lirc_ene0100
video                  18712  0 
uvcvideo               55847  0 
input_polldev           3491  1 lis3lv02d
output                  1883  1 video
fglrx                2252898  320 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms               7483  0 
cfg80211              144694  3 iwlagn,iwlcore,mac80211
hp_wmi                  5223  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
memstick                8249  1 jmb38x_ms
psmouse                59033  0 
serio_raw               4022  0 
intel_agp              26926  0 
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
agpgart                32075  2 fglrx,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
libahci                21792  1 ahci
sdhci_pci               6339  0 
r8169                  36777  0 
firewire_ohci          21554  0 
sdhci                  15954  1 sdhci_pci
led_class               2633  2 hp_accel,sdhci
mii                     4425  1 r8169
firewire_core          46675  1 firewire_ohci
crc_itu_t               1383  1 firewire_core

Thanks for your reply

---

### Post by zeroseven0183 on 2011-03-04
Hi rabbitdaone, check if you have Additional Drivers to install in System > Administration menu. From there you can install the Wireless Driver.

You have "02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000".

---

### Post by rabbitdaone on 2011-03-04
> **zeroseven0183 said:**
> Hi rabbitdaone, check if you have Additional Drivers to install in System > Administration menu. From there you can install the Wireless Driver.

You have "02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000".

I have dont that before, and the only thing that was there was a graphics card updated. The same applies now, what do you mean by > You have "02:00.0 Network controller

---

### Post by DanneStrat on 2011-03-04
As I can see you have the "iwlagn" module loaded

for your intel card and all seems good at that end.

Intel temporarily disabled wireless N in the drivers because

some code needs to be reworked.


Try to turn off wireless N in the

drivers by doing the following

in a terminal:

First we unload the module from the

kernel:

```
sudo modprobe -r iwlagn
```

Then we load the module with

wireless N disabled:

```
sudo modprobe iwlagn 11n_disable=1
```

Reboot your computer and check your

connection.

Hopefully it will work better now.

---

### Post by DanneStrat on 2011-03-04
I will post a little more info about

it here. It has been reported at launchpad.

You can have a look at it:

"802.11n support for the iwlagn driver has been temporarily disabled. Intel is actively 

working to get this properly fixed up in the firmware. This workaround should be reverted 

once updated firmware is available. (630748)"

[https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Known%20issues](https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Known%20issues)

Launchpad:

[https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748)

---

### Post by rabbitdaone on 2011-03-04
@DanneStrat
 
Thanks for the tips, I will do so now and report back with results. 

Thanks for the links and for posting the bug as well. Much appreciated

---

### Post by DanneStrat on 2011-03-04
> **rabbitdaone said:**
> @DanneStrat
 
Thanks for the tips, I will do so now and report back with results. 

Thanks for the links and for posting the bug as well. Much appreciated

You're welcome.

good luck!

---

### Post by rabbitdaone on 2011-03-04
> **DanneStrat said:**
> You're welcome.

good luck!

Thank YOU! It now works! Thanks again! How do I mark this as solved?

---

### Post by DanneStrat on 2011-03-04
> **rabbitdaone said:**
> Thank YOU! It now works! Thanks again! How do I mark this as solved?

I'm glad you got it fixed!

You can mark the thread solved on the top of the

thread in "thread tools".

---

### Post by rabbitdaone on 2011-03-05
So the fix was not permanent...Nor does it want to work more than once. 

I am now thinking it would be better to downgrade to an earlier version of Ubuntu that is without this issue. Does anyone have any recommendations? Should I have posed this question in a different thread?

---

### Post by DanneStrat on 2011-03-06
> **rabbitdaone said:**
> So the fix was not permanent...Nor does it want to work more than once. 

I am now thinking it would be better to downgrade to an earlier version of Ubuntu that is without this issue. Does anyone have any recommendations? Should I have posed this question in a different thread?

No you don't have to downgrade

to an earlier ubuntu version.


The info I gave you earlier with unloading

the module and then loading it with a parameter

was not a permanent fix, it was just so we could

see if that fixed the problem.

I forgot to tell you what you need to do to make the

module use that parameter by default.

Do the following in a terminal and post the

output you get. I will tell you what to do next:

```
grep iwlagn /etc/modprobe.d/*
```

---

### Post by rabbitdaone on 2011-03-06
@DanneStrat

Thanks for the reply friend, your assistance is much appreciated.

As for the output...Nothing happens. It just gives me a fresh line to input code. 

Could you also tell me what  "11n_disable=1" means?

---

### Post by DanneStrat on 2011-03-06
> **rabbitdaone said:**
> @DanneStrat

Thanks for the reply friend, your assistance is much appreciated.

As for the output...Nothing happens. It just gives me a fresh line to input code. 

Could you also tell me what  "11n_disable=1" means?

Hi again!

"11n_disable=1" is a parameter for the "iwlagn" module

used by your wireless card. That option disables

wireless N which doesn't seem to work properly at the moment

for intel cards. "1" means that the option is enabled and

"0" means the option is disabled.

Since you didn't get any output from the above command, let's

try this instead(we need to find the right file to edit)

```
cd /etc/modprobe.d/
```

then do:

```
ls
```

Post the output.

---

### Post by rabbitdaone on 2011-03-06
@DanneStrat

Oh ok lovely, thanks for the info. 

Is there any way to make a fix permanent? Or will I have to downgrade?

---

### Post by DanneStrat on 2011-03-06
> **rabbitdaone said:**
> @DanneStrat

Oh ok lovely, thanks for the info. 

Is there any way to make a fix permanent? Or will I have to downgrade?

I edited my post above.

Have a look there.

---

### Post by rabbitdaone on 2011-03-06
> **DanneStrat said:**
> Hi again!

"11n_disable=1" is a parameter for the "iwlagn" module

used by your wireless card. That option disables

wireless N which doesn't seem to work properly at the moment

for intel cards. "1" means that the option is enabled and

"0" means the option is disabled.

Since you didn't get any output from the above command, let's

try this instead(we need to find the right file to edit)

```
cd /etc/modprobe.d/
```then do:

```
ls
```Post the output.


These are the files/directories in that folder:

alsa-base.conf          blacklist-firewire.conf     blacklist-watchdog.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  fglrx.conf
blacklist-bcm43.conf    blacklist-modem.conf
blacklist.conf          blacklist-oss.conf

---

### Post by DanneStrat on 2011-03-06
Alright.

We will make a new file in that folder.

Do this in a terminal:

```
gksudo gedit /etc/modprobe.d/intel_11n_disable.conf
```

Gedit will open up with our new file.

Now put this line in the file:

```
options iwlagn 11n_disable=1
```

Now save the file(file > save)

and exit.

At this point we want to unload the kernel

module and reload it and after that it

should run with wireless N disabled by default.

In terminal do:

```
sudo modprobe -r iwlagn
```

Then reload it with:

```
sudo modprobe iwlagn
```

Now check if everything works

and try to reboot the computer to make sure

the settings remain.

Good luck.

---

### Post by rabbitdaone on 2011-03-06
@DanneStrat

So far so good, is gksudo the same as sudo? If not, whats the difference?

---

### Post by DanneStrat on 2011-03-06
> **rabbitdaone said:**
> @DanneStrat

So far so good, is gksudo the same as sudo? If not, whats the difference?

They work in a similar way, but

you should always use "gksudo"

for graphical applications (like gedit)

and "sudo" for "non-graphical" terminal applications

when you want elevated permissions.

The reason for this is because you don't 

want to make "root" the owner of files in your home directory.

More info here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by rabbitdaone on 2011-03-06
@DanneStrat

Thanks again sir.  Much appreciated.

---

### Post by DanneStrat on 2011-03-06
> **rabbitdaone said:**
> @DanneStrat

Thanks again sir.  Much appreciated.

Everything works fine now?

---

### Post by rabbitdaone on 2011-03-06
> **DanneStrat said:**
> Everything works fine now?

It worked before the restart, but after. its back to square uno.

---

### Post by DanneStrat on 2011-03-06
> **rabbitdaone said:**
> It worked before the restart, but after. its back to square uno.

I had a look around and it

seems like many people have problems

getting their options specified

in "modprobe.d" to be used as default and

at startup(which is what we want).

I think I found a solution.


Try to update "initramfs"

by doing this in a terminal:

```
sudo update-initramfs -u
```Now reboot and check if everything

works again.

If it does then we successfully set

the module parameter to be

used as default.

Test your adapter thoroughly to make

sure everything is ok.

If you run into more problems then feel

free to ask.

---

### Post by rabbitdaone on 2011-03-06
@DanneStrat

You are too good to me bro. Thanks for the assistance, I restarted and connected successfully.

---

### Post by DanneStrat on 2011-03-06
> **rabbitdaone said:**
> @DanneStrat

You are too good to me bro. Thanks for the assistance, I restarted and connected successfully.

Alright!

You're welcome!

---

### Post by rabbitdaone on 2011-03-06
Is it possible to make this thread a "sticky"? Is that what they are called? 

I have seen other threads that are unsolved, and since this solution actually works it might be a good thing to make it easier to find.
Can a mod do this?

---

### Post by DanneStrat on 2011-03-06
> **rabbitdaone said:**
> Is it possible to make this thread a "sticky"? Is that what they are called? 

I have seen other threads that are unsolved, and since this solution actually works it might be a good thing to make it easier to find.
Can a mod do this?

Yes, exactly. It's called a "sticky".

The info from this thread is also relevant for all who want to

specify custom "module parameters",

who are not aware that they may have to

refresh "initramfs" to apply the changes.


I would also say, make it a sticky

since many would benefit from it.

---

