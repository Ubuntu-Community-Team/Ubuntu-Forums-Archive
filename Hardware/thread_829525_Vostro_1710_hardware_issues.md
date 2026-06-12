---
title: "Vostro 1710 hardware issues"
date: 2008-06-14
forum: Hardware
---

### Post by dhasenan on 2008-06-14
Hi --

I'm posting this from elinks right now.

1. The builtin keyboard for my Vostro 1710 is only recognized about once every six times I boot the laptop.
2. GNOME mucks about with my keyboard settings so the external one doesn't work once GNOME starts. Fortunately, GDM doesn't, so I can actually get to a terminal to post this.
3. My ethernet card doesn't work two thirds of the time.

I thought at first it was a module load order issue, but I compiled a kernel with all the essential stuff built in, so that's not it.

Has anyone else successfully installed Ubuntu on a Vostro 1710? Any suggestions what to look at first? I've been using Linux for some years, but I haven't had to deal with any significant hardware issues.

---

### Post by dhasenan on 2008-06-18
- The keyboard issues were from using the dvd installer rather than the cd installer.

- The ethernet issues were solved by setting Wake On Lan to Enabled in the BIOS. Kudos to the Gentoo wiki on this: [http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)

Now Ubuntu's running pretty well on the Vostro.

---

### Post by konzeew on 2008-06-20
> **dhasenan said:**
> - The keyboard issues were from using the dvd installer rather than the cd installer.

- The ethernet issues were solved by setting Wake On Lan to Enabled in the BIOS. Kudos to the Gentoo wiki on this: [http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)

Now Ubuntu's running pretty well on the Vostro.

I am interested in Vostro 1710 with ubuntu and I have some questions for you, please.

- The ethernet issue were solved simply by setting "enabled" in Bios or it needs the long procedure about recompiling kernel explained in gentoo-wiki that  you linked?

- When you close the notebook, SUSPEND mode works out of the box?

- Issues with cpufreq, fan speed, and Hardrive Load Cycle Count?

- Have you the video card Nvidia 8600 GS or GT? It works simply with restricted drivers enabled or it requires some fixing?

Thank you very much! Bye.

---

### Post by amlgglma on 2008-06-20
Hi dhasenan,

I received my Dell Vostro 1710 a few hours ago. I installed Ubuntu 8.04 from the Live CD and all went well. However, at the fourth boot-up or so, the built-in keyboard would not respond (it's still fine in GRUB). It would not even work using the Live CD for a few more boot-up attempts after that. Eventually, for this boot-up, it works again.

After using the CD for installation instead of the DVD, has your keyboard been working full time? Or have you managed to find a different solution?

Thanks

---

### Post by dhasenan on 2008-07-03
> **konzeew said:**
> I am interested in Vostro 1710 with ubuntu and I have some questions for you, please.

- The ethernet issue were solved simply by setting "enabled" in Bios or it needs the long procedure about recompiling kernel explained in gentoo-wiki that  you linked?

The Linux driver for the NIC is flaky, and the NIC might shut down whenever you turn the computer off. Turning the NIC back on, for me, usually involves turning off Wake-On-Lan, turning it back on, and turning the computer off for a couple minutes with the ethernet cable unplugged. This is just a rain dance and might involve some unnecessary steps.

> - When you close the notebook, SUSPEND mode works out of the box?

I don't use hibernate/suspend. This machine is a desktop replacement for me.

> - Issues with cpufreq, fan speed, and Hardrive Load Cycle Count?

None whatsoever.

> - Have you the video card Nvidia 8600 GS or GT? It works simply with restricted drivers enabled or it requires some fixing?

I have an Intel video card that works out of the box.

[QUOTE=amlgglma]I received my Dell Vostro 1710 a few hours ago. I installed Ubuntu 8.04 from the Live CD and all went well. However, at the fourth boot-up or so, the built-in keyboard would not respond (it's still fine in GRUB). It would not even work using the Live CD for a few more boot-up attempts after that. Eventually, for this boot-up, it works again.

After using the CD for installation instead of the DVD, has your keyboard been working full time? Or have you managed to find a different solution?[/QUOTE]

Sorry to hear that -- I haven't had any keyboard issues since using the livecd, and I haven't had keyboard issues while using any of the installation media.

---

### Post by dhasenan on 2008-07-04
Update on suspend: I used it earlier today. The only ill effect is that sound doesn't work after resuming from suspend, as far as I can tell. alsamixer claims that all channels are unmuted and maxed out, but I don't get any sound.

---

### Post by dhasenan on 2008-07-26
I just installed the Realtek 8168 driver (they released one on Thursday [24 July] that works with kernels version 2.6.24 and above). This seems to have solved the ethernet issues.

I had to modify their makefile slightly; apparently the $(PWD) macro isn't working on my machine. In r8168-8.008.00/src/Makefile, replace $(PWD)/src with the path of the src directory, and it should work.

Now, the only thing not working is the microphone.

---

### Post by malcontent on 2008-08-03
> **dhasenan said:**
> I just installed the Realtek 8168 driver (they released one on Thursday [24 July] that works with kernels version 2.6.24 and above). This seems to have solved the ethernet issues.

I had to modify their makefile slightly; apparently the $(PWD) macro isn't working on my machine. In r8168-8.008.00/src/Makefile, replace $(PWD)/src with the path of the src directory, and it should work.

Now, the only thing not working is the microphone.


Where did you get this driver? Also did it help your sound problems?

---

### Post by nigel.charman on 2008-09-01
I have Ubuntu 8.04 amd64 running satisfactorily on my Vostro 1710.  

The ethernet issues are due to bug 212497 [(here)]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212497") and were resolved by applying Cedric Schieli's backport [(here)]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212497/comments/48")  (to get the PPA to work, I had to reboot about 6 times until the network worked).

The only time I have seen any keyboard issues if is I boot with a 65W adapter, rather than the supplied 90W adapter.  I get a boot-time message warning that a 65W adapter is being used, and about half the time the built-in keyboard does not work.  If I boot using battery power, then plug in the 65W adapter I don't have any problems.

Suspend works fine.

Using EnvyNG, the nvidia drivers installed fine and twin view screens are working.

I haven't got the microphone working yet, and would like to hear if anyone has got it working.

---

### Post by amias on 2008-09-28
> **dhasenan said:**
> Update on suspend: I used it earlier today. The only ill effect is that sound doesn't work after resuming from suspend, as far as I can tell. alsamixer claims that all channels are unmuted and maxed out, but I don't get any sound.

me too , everything else works amazingly well , even the finger print reader (thinkfinger) . 

heres my lspci - 

amias@rome:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

there are no error messages and all the apps will happily output to
the soundcard but no audio appears regardless of what is done with
the mixer. If any more info is needed i will gladly help and
run tests.

Toodle-pip
Amias

---

### Post by amias on 2008-09-28
further testing shows that the audio is going through pulseaudio fine 
(i can see the meters move with pavumeter)

something somewhere is muted , there must be a hidden volume control
that i cant see on any of the many mixer devices present.

I am using ubuntu hardy which uses alsa version 1.0.15 (from alsactl -v)
, there appears to be an newer alsa version that is not yet in ubuntu
hardy which mentions fixes for alc268 codec  version of snd-hda-intel.
Anyone tried building the new version yet ?

---

### Post by amias on 2008-10-03
sound now works after hibernate - the fix is 

create /etc/modprobe.d/snd_hda_intel

which should contain - 

options snd_hda_intel model=dell

audio now works on resume , the muting seemed 
to be done by the phone out control in aumix.

Still no joy with the microphone tho.

Toodle-pip
Amias

---

### Post by kaiten7 on 2008-11-26
Hey there, I have ubuntu on a Vostro 1710, and I never got problems such as yours. Once my keyboard stopped working for no apparent reason, but I suspect it's related to the "Fn + brightness" bug.

The webcam I didn't test yet, but the microphone worked out of the box for me. Are you sure you didn't screw up any volume configuration? (mine was mute by default)

---

### Post by burtus on 2008-12-12
Hi! i have a big problem with my dell vostro 1710....keyboard not working in games...Any suggestions? Thanks

---

### Post by durand on 2009-03-19
Just got a vostro 1710. Everything works apart from when my keyboard and touchpad randomly don't... I have no idea why it happens but it's not very often.

---

### Post by durand on 2009-03-22
I managed to get the mic working in Jaunty. The volume on Capture was actually too high so everything was boosted beyond usable. If you reduce the Capture slider volume to 60%, it works.

PS: See the attached screenshot.

The touchpad/keyboard bug is still annoying me. It really seems to be a completely random effect....Does anyone know anything about it?

---

### Post by durand on 2009-04-21
BTW, fixed the touchpad/keyboard bug. You need to add i8042.reset to the end of the kernel boot line in /boot/grub/menu.lst

Just posting this for reference.

---

### Post by Idefix82 on 2009-05-05
> **durand said:**
> BTW, fixed the touchpad/keyboard bug. You need to add i8042.reset to the end of the kernel boot line in /boot/grub/menu.lst

Just posting this for reference.

Thanks for the solution. What exactly does this command do?

---

### Post by durand on 2009-05-05
> **Idefix82 said:**
> Thanks for the solution. What exactly does this command do?

I have absolutely no idea. I tried to find out but didn't get very far. It does work though!

---

### Post by durand on 2009-05-07
Solved the final problem! To get my card reader working, I found this article:
[http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu](http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu)

---

### Post by Idefix82 on 2009-05-08
> **durand said:**
> Solved the final problem! To get my card reader working, I found this article:
[http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu](http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu)

Did you card reader work on previous Ubuntu versions? I am still running Hardy and my card reader works out of the box.

Should have said that I also have a Vostro 1710.

---

### Post by durand on 2009-05-08
> **Idefix82 said:**
> Did you card reader work on previous Ubuntu versions? I am still running Hardy and my card reader works out of the box.

Should have said that I also have a Vostro 1710.

I've only ever used jaunty on this laptop.

---

### Post by rmhartman on 2009-06-27
> **amlgglma said:**
> Hi dhasenan,

I received my Dell Vostro 1710 a few hours ago. I installed Ubuntu 8.04 from the Live CD and all went well. However, at the fourth boot-up or so, the built-in keyboard would not respond (it's still fine in GRUB). It would not even work using the Live CD for a few more boot-up attempts after that. Eventually, for this boot-up, it works again.

After using the CD for installation instead of the DVD, has your keyboard been working full time? Or have you managed to find a different solution?

Thanks


Trying to run 9.04 desktop cd on Vostro 1310, neither keyboard nor touchpad work.  Haven't even had a chance to attempt to install, still running from CD ... except that it doesn't respond to anything after it boots up.  Any special options I need to set?

---

### Post by durand on 2009-06-27
> **durand said:**
> BTW, fixed the touchpad/keyboard bug. You need to add i8042.reset to the end of the kernel boot line in /boot/grub/menu.lst

Just posting this for reference.

That. Press e and add it to the end of the boot line.

---

### Post by rmhartman on 2009-06-30
> **durand said:**
> That. Press e and add it to the end of the boot line.

'e' didn't work, but f6 (other options) did.  Thanks.  The i8042.reset thing works (added it to /boot/grub/menu.lst afterwards so I don't have to keep doing this.)

Any suggestions on the wireless?

---

### Post by durand on 2009-06-30
Sorry, I forgot that you were using the live cd. For wireless, you need to enable Wake On Lan (WOL) in the bios and make sure that vista didn't hibernate itself rather than shutdown properly. That was my problem. After that, you should be able to enable wifi with System > Administration > Hardware Drivers

---

