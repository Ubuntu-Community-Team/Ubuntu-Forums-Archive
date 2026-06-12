---
title: "Kubuntu 13.10 Sound issues"
date: 2014-03-29
forum: Hardware
---

### Post by sunnydays42 on 2014-03-29
Kubuntu forum wouldn't let me post, so im posting here.

I have a maibal x7200 laptop, and everything works fine, but i get no sound, If i could get the sound to work i would use kubuntu all the time, according to windows my integrated sound card is
Realtek High Definition Audio

I'm on my windows boot, but i'll list my lspci here in a bit.

Also, if i can't get the sound to work, is there a cheapo USB sound device that linux will recognize that i could use to hook my speakers up to?

thanks
C

my lspci

00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 22)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 22)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 22)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 22)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 22)
00:13.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 22)
00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 22)
00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 22)
00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 22)
00:16.0 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.1 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.2 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.3 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.4 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.5 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.6 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.7 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.3 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode]
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 VGA compatible controller: NVIDIA Corporation GF100M [GeForce GTX 480M] (rev a3)
03:00.1 Audio device: NVIDIA Corporation GF100 High Definition Audio Controller (rev a1)
04:00.0 VGA compatible controller: NVIDIA Corporation GF100M [GeForce GTX 480M] (rev a3)
04:00.1 Audio device: NVIDIA Corporation GF100 High Definition Audio Controller (rev a1)
07:00.0 PCI bridge: Texas Instruments XIO2213A/B/XIO2221 PCI Express to PCI Bridge [Cheetah Express] (rev 01)
08:00.0 FireWire (IEEE 1394): Texas Instruments XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller [Cheetah Express] (rev 01)
09:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
0a:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
0a:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
0a:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
0a:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)

---

### Post by SeijiSensei on 2014-03-29
First you can try examining the audio settings in System Settings > Multimedia > Audio and Video Settings.  Check to make sure the right audio device is selected and the correct output destination chosen as well.

If that doesn't work for you, try installing **pavucontrol** from the repositories.  It will show up in the Kubuntu menu under Multimedia as "Volume Control."  I have both HDMI and analog outputs in use and find pavucontrol an easier method for switching between the devices.

I've used [this USB device](http://www.newegg.com/Product/Product.aspx?Item=N82E16812186035) with Kubuntu on a laptop where the physical connector to the onboard audio broke.

---

### Post by houstonbofh on 2014-03-29
OK, you have the onboard audio at;
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
You also have the HDMI audio via your Nvidia graphics at;
03:00.1 Audio device: NVIDIA Corporation GF100 High Definition Audio Controller (rev a1)
04:00.1 Audio device: NVIDIA Corporation GF100 High Definition Audio Controller (rev a1)

Check that you are using the Intel audio, not the nvidia...

---

### Post by sunnydays42 on 2014-03-30
well, under the windoze side, it said realtek.. lspci give you the truth

---

### Post by sunnydays42 on 2014-03-30
Thanks for the help folks, I use the win7 side for gaming and stuff, them the linux side for torrenting, netflix, and audio and video viewing

---

### Post by SeijiSensei on 2014-03-30
So did you fix your problem?  How?  If it is fixed, then please mark this thread as [[SOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads).

---

### Post by sunnydays42 on 2014-03-30
None of those worked, I guess I'll have to get the usb dongle. It's worth it, but i drives me nuts it won't wrk, but it's all intergrated and its a malibal motherboard with 2 nvidia cards and 2 six core cpus.. its not surprising it wont work.. oh well, thank god the dongle is cheap

Thanks again
guess it's solved. is that dongle just plug and play?

---

### Post by SeijiSensei on 2014-03-31
> **sunnydays42 said:**
> guess it's solved. is that dongle just plug and play?

Yes.  My machine was running Kubuntu 12.04 at the time I bought one, and it was recognized immediately when I plugged it in.  

Those comments at Newegg about how loud the device is are spot on.  Turn your master volume control down low before installing so you can protect your speakers and your ears.

---

### Post by sunnydays42 on 2014-03-31
Thanks a lot, I've ordered it and it should arrive in a few days, I got mine from amazon, i hope it's not a cheap knock off

---

