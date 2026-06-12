---
title: "Toshiba NB 205 and Lucid Lynx UNR"
date: 2010-05-23
forum: Hardware
---

### Post by neoanderthal on 2010-05-23
I wanted to start a thread to try to capture all of the information regarding what works and what doesn't on the Toshiba NB 205 netbook series and Lucid Lynx.

What works out of the box (so to speak):
[list]
[*]WiFi (presuming it's enabled) - no more backports!
[*]Trackpad scrolling (right side of trackpad)
[*]MMC/SD card slot at front
[*]Wired ethernet
[*]Webcam
[*]Function keys:
[list]
[*]Fn+Esc - Mute / Unmute (see note re: audio in Not Working)
[*]Fn+F3 - Suspend to RAM
[*]Fn+F4 - Suspend to disk
[*]Fn+F6 - Screen Brightness down
[*]Fn+F7 - Screen Brightness up
[*]Fn+3 - Volume up
[*]Fn+4 - Volume down
[/list]
[*]Suspend
[*]Hibernate
[/list]
Workarounds:
Slow Boot Times - Set your SATA Controller mode to 'Compatibility' instead of 'AHCI'.
[LIST]
[*]Press F2 on machine boot to enter the BIOS
[*]Select the 'Advanced' tab
[*]Change SATA controller mode from AHCI to Compatibility
[/LIST]

Not working:
It's incorrect to say that audio does not work on the NB 205. Audio through the headphone jack works fine. Audio through the external speaker doesn't work out of the box. Changing the Audio output under Sound Preferences makes no difference. Perhaps the methods used to enable sound through the speaker from previous versions will work; I haven't tried anything yet.

I'm still in the process of testing what works and what doesn't, so I'll update this post with more information on battery life, vga output via connector, audio output, and anything else I run across.

If you've got something to contribute to this information regarding Lucid and the NB 205, please post it here.

Resources:
Various and sundry links that contain helpful information on the Toshiba NB 205
[list]
[*][https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)
[*][http://ubuntuforums.org/showthread.php?t=1215665](http://ubuntuforums.org/showthread.php?t=1215665)
[/list]
cheers,
neo

---

### Post by djmoore85 on 2010-05-23
Hey there. Same options worked for me out of the box, except the Fn+F4 hibernate key. Sound, bluetooth, fixed using methods in [http://ubuntuforums.org/showthread.php?t=1215665&highlight=toshiba+nb205]("http://ubuntuforums.org/showthread.php?t=1215665&highlight=toshiba+nb205") as well as the slow boot workaround in that thread. Would like to get all of the Fn+ keys to work. Unlike the aforementioned thread hibernate works flawlessly without the camera draining power. Adding the als-intel..... line in the alsa config file lets skype and internal speaker work perfect. Using UNR I would like to tweak a couple things, like having the shortcut left-side menu be able to hide so desktop backgrounds can be seen in whole vs partially covered. Overall the hardware has not been painful to set up on the NB205 using Lucid.

---

### Post by mtalexan on 2010-07-06
djmoore cited the thread that seems to have all the fixes in it, but it starts way back with UNR 9.04 and only works up to 10.04 in the last handful of posts.  I thought I'd consolidate the info relevant to 10.04 (Lucid Lynx) here.

**[SIZE="2"]General[/SIZE]**

If you're upgrading to Lucid from a previous version, don't.  It will upgrade successfully, but you won't get any of the necessary upgrades to things like audio.  I did the replacing PulseAudio with OSS audio fix in 9.10 and when I upgraded it refused to recognize that I even had audio hardware.  Back up your stuff, or hopefully you were smart enough to create a seperate partition for your personal files, and do a clean install.

**[SIZE="2"]Audio[/SIZE]**
Audio, both playback and the internal mic, has been a real issue with UNR on the Toshiba NB 200 series so far.  Luckily, it's mostly fixed in Lucid right out of the box.  With a clean install and no tweaks, you'll get no mic or external audio, but headphones will work.  Fixing both is simple and is pulled from the launchpad bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318").  The directions are:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
paste at end of file:
```
options snd-hda-intel index=0 model=auto
```
save, exit, reboot.

Alternatively, if you REALLY want to, you can update your kernel to the next version, 2.6.34, from what Lucid comes with and that will fix the audio issue in the same way.  The directions, if you're interested, are as follows:
```
mkdir 2.6.34 
cd 2.6.34 
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-source-2.6.34_2.6.34-020634_all.deb
sudo dpkg -i *.deb
```
Finish it by rebooting.  I haven't tried this, and there are some possible hang ups with dependencies, but according to numerous people, it works.

**[SIZE="2"]Long Boot[/SIZE]**
Apparently there's an issue with how the BIOS identifies the SATA adapter for the hard drive.  The full discussion can be found at [http://ubuntuforums.org/showthread.php?t=1476638&highlight=toshiba+NB205+slow+boot]("http://ubuntuforums.org/showthread.php?t=1476638&highlight=toshiba+NB205+slow+boot") but the solution is to reboot your computer, press [F2] when the Toshiba splash screen comes up to enter BIOS, then look for and change the SATA controller mode from "AHCI" to "Compatibility" under the "Advanced" tab.  The result is a boot time of 30 seconds or less.

**[SIZE="2"]Battery Life[/SIZE]**
Battery life always seems to suck right after you clean install or upgrade, but the common fix is the correct one.  Use powertop, which is a command-line utility to tweak your power settings.  The directions are as follows:
```
sudo apt-get install powertop
sudo powertop
```
While it's running, it will give a series of suggestions at the bottom of the screen for how you can save power.  You'll be presented with a command you can run in the terminal to enable the power saving, or you can just press a single character button it mentions and it will automatically do it for you.  After each selection wait a moment and a new one will come up until there's nothing left for it to suggest.  [One experience]("http://ubuntuforums.org/showpost.php?p=9544700&postcount=216") had the battery life going from 4.5 hours back up to 7.5 hours after running powertop.
One thing to note, pay attention to what you're agreeing to while running powertop.  After running powertop, and setting it to auto-sleep non-Human Interface USB devices, my USB wireless mouse stopped working.  All it took to fix it was to disconnect and reconnect the USB hookup so it could re-identify itself as a Human Interface device, but it's just one example of things that can unexpectedly go wrong.

**[SIZE="2"]How Dare You Be Helpful![/SIZE]**
Hate that I re-posted the relevant information?  Want to slog through the posts yourself?  The [thread mentioned before]("http://ubuntuforums.org/showthread.php?t=1215665&highlight=toshiba+nb+audio&page=3") starts talking about 10.04 (Lucid) final release installs in post #197, and now you don't have to look through 200+ posts to find it!

---

### Post by bobglaub on 2010-07-23
I love you.  I looked for 2 days how to fix my headphone jack.  tried all sorts of different things, nothing worked.  you're easy to understand instructions on how to update my kernel fixed it.  you rule.  thank you so much!

---

### Post by beaneater on 2010-07-30
Hey thanks mtalexan for the instructions.

Who should we notify to update the wiki?
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)

---

### Post by balente84 on 2010-08-10
> **mtalexan said:**
> djmoore cited the thread that seems to have all the fixes in it, but it starts way back with UNR 9.04 and only works up to 10.04 in the last handful of posts.  I thought I'd consolidate the info relevant to 10.04 (Lucid Lynx) here.

**[SIZE="2"]General[/SIZE]**

If you're upgrading to Lucid from a previous version, don't.  It will upgrade successfully, but you won't get any of the necessary upgrades to things like audio.  I did the replacing PulseAudio with OSS audio fix in 9.10 and when I upgraded it refused to recognize that I even had audio hardware.  Back up your stuff, or hopefully you were smart enough to create a seperate partition for your personal files, and do a clean install.

**[SIZE="2"]Audio[/SIZE]**
Audio, both playback and the internal mic, has been a real issue with UNR on the Toshiba NB 200 series so far.  Luckily, it's mostly fixed in Lucid right out of the box.  With a clean install and no tweaks, you'll get no mic or external audio, but headphones will work.  Fixing both is simple and is pulled from the launchpad bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318").  The directions are:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
paste at end of file:
```
options snd-hda-intel index=0 model=auto
```
save, exit, reboot.

Alternatively, if you REALLY want to, you can update your kernel to the next version, 2.6.34, from what Lucid comes with and that will fix the audio issue in the same way.  The directions, if you're interested, are as follows:
```
mkdir 2.6.34 
cd 2.6.34 
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-source-2.6.34_2.6.34-020634_all.deb
sudo dpkg -i *.deb
```
Finish it by rebooting.  I haven't tried this, and there are some possible hang ups with dependencies, but according to numerous people, it works.

**[SIZE="2"]Long Boot[/SIZE]**
Apparently there's an issue with how the BIOS identifies the SATA adapter for the hard drive.  The full discussion can be found at [http://ubuntuforums.org/showthread.php?t=1476638&highlight=toshiba+NB205+slow+boot]("http://ubuntuforums.org/showthread.php?t=1476638&highlight=toshiba+NB205+slow+boot") but the solution is to reboot your computer, press [F2] when the Toshiba splash screen comes up to enter BIOS, then look for and change the SATA controller mode from "AHCI" to "Compatibility" under the "Advanced" tab.  The result is a boot time of 30 seconds or less.

**[SIZE="2"]Battery Life[/SIZE]**
Battery life always seems to suck right after you clean install or upgrade, but the common fix is the correct one.  Use powertop, which is a command-line utility to tweak your power settings.  The directions are as follows:
```
sudo apt-get install powertop
sudo powertop
```
While it's running, it will give a series of suggestions at the bottom of the screen for how you can save power.  You'll be presented with a command you can run in the terminal to enable the power saving, or you can just press a single character button it mentions and it will automatically do it for you.  After each selection wait a moment and a new one will come up until there's nothing left for it to suggest.  [One experience]("http://ubuntuforums.org/showpost.php?p=9544700&postcount=216") had the battery life going from 4.5 hours back up to 7.5 hours after running powertop.
One thing to note, pay attention to what you're agreeing to while running powertop.  After running powertop, and setting it to auto-sleep non-Human Interface USB devices, my USB wireless mouse stopped working.  All it took to fix it was to disconnect and reconnect the USB hookup so it could re-identify itself as a Human Interface device, but it's just one example of things that can unexpectedly go wrong.

**[SIZE="2"]How Dare You Be Helpful![/SIZE]**
Hate that I re-posted the relevant information?  Want to slog through the posts yourself?  The [thread mentioned before]("http://ubuntuforums.org/showthread.php?t=1215665&highlight=toshiba+nb+audio&page=3") starts talking about 10.04 (Lucid) final release installs in post #197, and now you don't have to look through 200+ posts to find it!

This is great. Thank you for your clear summary!

---

### Post by cadcam on 2010-11-30
just wanted to say thanks for this article.  i love my nb205, and now finally i'm getting linux to function on it....

thanks,
A

---

### Post by mengong on 2010-12-27
my nb205 cant detect my sd card .. i use ubuntu remix .. this is the information when i type dmesg on it ..
[46460.326486] usb 1-4: new high speed USB device using ehci_hcd and address 15
[46460.704437] usb 1-4: configuration #1 chosen from 1 choice
[46460.710621] scsi9 : SCSI emulation for USB Mass Storage devices
[46460.711112] usb-storage: device found at 15
[46460.711120] usb-storage: waiting for device to settle before scanning
[46465.112558] usb 1-4: USB disconnect, address 15

---

