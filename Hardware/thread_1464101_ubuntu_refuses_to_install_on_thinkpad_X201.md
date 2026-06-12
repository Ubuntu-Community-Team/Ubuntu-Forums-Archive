---
title: "ubuntu refuses to install on thinkpad X201"
date: 2010-04-27
forum: Hardware
---

### Post by gregnorc on 2010-04-27
I had at least gotten a mostly working setup via the 9.04 alternative install... I had a working system, except for one tiny problem: The system froze shortly 30 seconds after login, without fail.

I looked around, and the issue apparently was with my graphics card on the X201.

Here is the thinkwiki page for the laptop and the graphics card:
[http://www.thinkwiki.org/wiki/Category:X201](http://www.thinkwiki.org/wiki/Category:X201)
[http://www.thinkwiki.org/wiki/Intel_HD_Graphics](http://www.thinkwiki.org/wiki/Intel_HD_Graphics)

I had been attempting to manually update the kernel to 2.6.33 using .debs I found online - no luck.

I downloaded the Ubuntu 10.04 RC alt install CD... it installed fine, but when it starts up, it now just goes to a black screen.

:confused:

I am very desperate, I am very close to sending this laptop back to Lenovo, if anyone has any suggestions on how to get a working Ubuntu (or any other distro) install going on an X201, please share any details you can remember!

---

### Post by Agnaramasi on 2010-04-27
I just figured out how to install 10.04 RC on my X201 yesterday. The key is inserting the options "xforcevesa i915.modeset=0" in the boot line for the installer and then the installed system itself. Worked for me.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569)

---

### Post by amy_cgi on 2010-04-27
Just got a new x201 today and after some effort, I was able to get Ubuntu 9.10 running.  (Though the release candidate version of 10.04 failed; [another post]("http://ubuntuforums.org/showthread.php?t=1457382") makes it sound like it may be possible with the alternative install...)

To get 9.10 installed, I ran the install in "safe graphics" mode.  The install then goes through without a hitch.  Upon boot, my resolution was off and my wireless didn't work.  Some googling indicated that kernel version 2.6.32 fixes the graphics issues; they also fixed my wireless issues.  You can get .deb files for version 2.6.32 [here]("http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/").  Just install them in the order listed on that page "dpkg -i <filename>", then run "sudo update-grub".  For some reason, even after this I had some graphics issues upon boot, but they have magically disapeared and everything seems fine now.  The graphics issues may have come from booting into the older Linux version.  Be sure to install the new kernel on the first run of Ubuntu after install; otherwise, you may never get in.

Hope that helps!

---

### Post by gregnorc on 2010-04-28
> **Agnaramasi said:**
> I just figured out how to install 10.04 RC on my X201 yesterday. The key is inserting the options "xforcevesa i915.modeset=0" in the boot line for the installer and then the installed system itself. Worked for me.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569)

Which image did you use? Alt or main? 32 or 64 bit? Server or home? Any details would be helpful!

Also, how/when in the process do I add that boot parameter? (Where do I get the boot command line?)

---

### Post by Agnaramasi on 2010-04-28
I am using linux-image-2.6.32-21-generic 64bit.
When the grub menu loads (you need to hold shift after the bios screen), I select my kernel image and press 'e' to edit the boot parameters. At the end of the line beginning with "Linux" I append the option "i915.modeset=0". Turns out I can omit the "xforcevesa" option. On my system the modified line looks like this:
```
linux   /boot/vmlinuz-2.6.32-21-generic root=UUID=3c809b01-30e9-434d-8dc8-96adf09007b1 ro   quiet splash i915.modeset=0
```
Then you press ctrl+x to boot with the modified parameter.
To make the change semi-permanent (it will last until a kernel update), I added the "i915.modeset=0" to the appropriate line of the the kernel's main menuentry section in /boot/grub/grub.cfg. Apparently this is not how to alter the boot menu properly, but it works for me.
To install 10.04 from the regular livecd you will have to similarly modify the boot parameters of the installation media. I believe I did this by pressing F6 and then Esc from the live cd main menu.

---

### Post by amy_cgi on 2010-04-30
For any who might want full details: I was able to install Ubuntu 10.04 Desktop (released version) yesterday using the main install disks (not alt).  I did this by including the options "xforcevesa i915.modeset=0" on the boot line for the default install -- I needed both these options in order to get it to work.  After install, I edited the grub boot command (hold down shift until after the BIOS screen to be able to edit boot options) to include these options in the kernel call.  I then edited /etc/default/grub, setting GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa i915.modeset=0", and then called "sudo update-grub".  Worked like a charm!  I'm loving 10.04!

---

### Post by gregnorc on 2010-04-30
> **Agnaramasi said:**
> I am using linux-image-2.6.32-21-generic 64bit.
When the grub menu loads (you need to hold shift after the bios screen), I select my kernel image and press 'e' to edit the boot parameters. At the end of the line beginning with "Linux" I append the option "i915.modeset=0". Turns out I can omit the "xforcevesa" option. On my system the modified line looks like this:
```
linux   /boot/vmlinuz-2.6.32-21-generic root=UUID=3c809b01-30e9-434d-8dc8-96adf09007b1 ro   quiet splash i915.modeset=0
```
Then you press ctrl+x to boot with the modified parameter.
To make the change semi-permanent (it will last until a kernel update), I added the "i915.modeset=0" to the appropriate line of the the kernel's main menuentry section in /boot/grub/grub.cfg. Apparently this is not how to alter the boot menu properly, but it works for me.
To install 10.04 from the regular livecd you will have to similarly modify the boot parameters of the installation media. I believe I did this by pressing F6 and then Esc from the live cd main menu.

Can you be a little more specific?

Right now what I do is upon boot, I hit F12, and select my USB CD rom drive as the boot drive, then hold shift

I am asked the following questions (Y/N), and answer yes to each...

Load Boot graphics (Y/N)?
Detect display size (Y/N)?

Then it says "initalizing gfx code" and spits out a bunch of hex, and tells me to press a key to continue. I do so. Then more hex is displayed, then I press any key again, then it goes to a black screen...

If I hit "n" for load boot graphics I get a different screen, but do not see any kernel images. It says it will start installing automatically in 4 seconds and does NOT list any kernel images that I could "hit e to edit"

I am using the Desktop install CD for Ubuntu 10.04 RC, if you could give me some visual clues/hints so I can get to the right spot to enter those changes it would be very helpful... I am not very familiar with how to get to this boot parameters area and any information you have would help greatly

---

### Post by Agnaramasi on 2010-04-30
You don't have to hold shift when booting from the live cd. The boot options are specified within the live cd menu, not grub. Let the live cd main menu load (the list of options like 'repair existing installation' and 'try ubuntu') and then press F6 and then ESC to edit the boot options for ubuntu on the live cd. Sorry I can't be more specific...

---

### Post by gregnorc on 2010-05-01
> **amy_cgi said:**
> For any who might want full details: I was able to install Ubuntu 10.04 Desktop (released version) yesterday using the main install disks (not alt).  I did this by including the options "xforcevesa i915.modeset=0" on the boot line for the default install -- I needed both these options in order to get it to work.  After install, I edited the grub boot command (hold down shift until after the BIOS screen to be able to edit boot options) to include these options in the kernel call.  I then edited /etc/default/grub, setting GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa i915.modeset=0", and then called "sudo update-grub".  Worked like a charm!  I'm loving 10.04!

Did you have to do anything special to get the boot screen?

Like, when I boot my 10.04 RC cd, it works fine... I can edit the boot param and start the process, but not with the main cd. (I'm using a usb dvd drive obviously since its an X201)

---

### Post by gregnorc on 2010-05-01
> **amy_cgi said:**
> For any who might want full details: I was able to install Ubuntu 10.04 Desktop (released version) yesterday using the main install disks (not alt).  I did this by including the options "xforcevesa i915.modeset=0" on the boot line for the default install -- I needed both these options in order to get it to work.  After install, I edited the grub boot command (hold down shift until after the BIOS screen to be able to edit boot options) to include these options in the kernel call.  I then edited /etc/default/grub, setting GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa i915.modeset=0", and then called "sudo update-grub".  Worked like a charm!  I'm loving 10.04!

Question: How did you run sudo update grub? In the live session, or afterwards, cause I did this... I edited the boot parem, then after install, I wrote GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa i915.modeset=0"... I did this from within the live image, by writing to the hard drive. But when I try and run update-grub it gives me the error:

> /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)

And booting to the hard drive still gives a black screen :(

---

### Post by Agnaramasi on 2010-05-01
If you've successfully installed Ubuntu, then you will need to manually edit the boot command in the grub screen in order to boot into the OS before you can update grub. Alternatively, you could boot into recovery mode and edit the grub config / update grub from there.

---

### Post by gregnorc on 2010-05-02
OK it is mostly working now, all that's left is wifi.

The rtl8191SEVA2 driver seems to be extremely buggy - right now I can see networks but connecting to them fails. (all the other devices in the house connect to the WLAN fine, so I know it's not an issue with the network)

Did any of you with an X201 have to do anything special to get the wireless working?

I now cannot connect to any networks at all... I can see them, I can attempt to join, but the connection fails.

I'm trying to find drivers to update but with no luck, I found this page but the links for my chipset (rtl8191SE-VA2) don't work:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2262](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2262)

---

### Post by Agnaramasi on 2010-05-02
Sorry, my X201 uses an Intel wireless card and I had no problems.

---

### Post by gregnorc on 2010-05-02
> **Agnaramasi said:**
> Sorry, my X201 uses an Intel wireless card and I had no problems.

Out of curiosity, are you using any encryption on your network? (WEP, WPA/WPA2, etc?)

---

### Post by Agnaramasi on 2010-05-02
Yes, WPA AES encryption, which is required to achieve true 802.11n speeds on intel adapters.

---

### Post by gregnorc on 2010-05-03
Did you have access to compiz's visual effects? My install can't do transparency (probably due to the kms tweak) which is annoying since avant window manager needs it, the compiz equiv of expose also doesn't work

---

### Post by Agnaramasi on 2010-05-04
No, visual effects don't work for me, which is a minor inconvenience. I guess we'll have to wait for a bug fix.

---

### Post by gregnorc on 2010-05-05
> **Agnaramasi said:**
> No, visual effects don't work for me, which is a minor inconvenience. I guess we'll have to wait for a bug fix.

If you do hear about a fix, could you do me a favor and post it in here?

---

### Post by amy_cgi on 2010-05-10
Everything seems to be working well except that I can't dim the monitor at all and visual effects don't work.  The screen is at maximum brightness which is painful to look at late at night.  Any thoughts?

---

### Post by pIII on 2010-05-21
> **amy_cgi said:**
> Everything seems to be working well except that I can't dim the monitor at all and visual effects don't work.  The screen is at maximum brightness which is painful to look at late at night.  Any thoughts?

for the screen brightness see here:
[http://old.nabble.com/X201-brightness-key-to28496959.html](http://old.nabble.com/X201-brightness-key-to28496959.html)

im wondering if the kernels from here will help:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D)

---

### Post by amy_cgi on 2010-05-21
> **pIII said:**
> for the screen brightness see here:
[http://old.nabble.com/X201-brightness-key-to28496959.html](http://old.nabble.com/X201-brightness-key-to28496959.html)

im wondering if the kernels from here will help:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/?C=M;O=D")

Thanks for the links.  I just tried several kernel version from kernel.ubuntu.com; no luck so far, but I'm hoping to get a reply on the nabble.com thread.

---

### Post by pIII on 2010-05-22
heia amy, here is something extra to keep and eye on:
[http://bugs.freedesktop.org/show_bug.cgi?id=28180](http://bugs.freedesktop.org/show_bug.cgi?id=28180)

---

### Post by jskulski on 2010-06-02
I have been having the same issues. I have a new X201 and trying to get 10.04 up and running. 

So far I was able to boot the ubuntu installer via USB stick using the 

xforcevesa i915.modeset=0 

but I can not get the actual installed instance to boot even with the same parameters. This is both regular and recovery mode.

Anyone know why? 

I want to try to install the debs in the launchpad thread but can't do so unless i can boot the system.

---

### Post by amy_cgi on 2010-06-03
> **jskulski said:**
> I have been having the same issues. I have a new X201 and trying to get 10.04 up and running. 

So far I was able to boot the ubuntu installer via USB stick using the 

xforcevesa i915.modeset=0 

but I can not get the actual installed instance to boot even with the same parameters. This is both regular and recovery mode.

Anyone know why? 

I want to try to install the debs in the launchpad thread but can't do so unless i can boot the system.

You have to supply those same parameters to the installed kernel to get it to boot:

> **amy_cgi said:**
> 
For any who might want full details: I was able to install Ubuntu 10.04  Desktop (released version) yesterday using the main install disks (not  alt).  I did this by including the options "xforcevesa i915.modeset=0"  on the boot line for the default install -- I needed both these options  in order to get it to work.  After install, I edited the grub boot  command (hold down shift until after the BIOS screen to be able to edit  boot options) to include these options in the kernel call.  I then  edited /etc/default/grub, setting GRUB_CMDLINE_LINUX_DEFAULT="quiet  splash xforcevesa i915.modeset=0", and then called "sudo update-grub".   Worked like a charm!  I'm loving 10.04!


---

### Post by jskulski on 2010-06-07
> **amy_cgi said:**
> You have to supply those same parameters to the installed kernel to get it to boot:

Right, what I am saying is that when I supply those parameters to the installed instance it doesn't work. I am not sure why that it is, I would assume it was the same kernel.

Anyway, I sucessfully mounted my installed instanced, chrooted and patched the kernel, compiled and installed it. However updated blew away my grub config (points back to the original install)

---

### Post by eph214 on 2010-07-06
I followed the instructions posted here, and was able to get a livecd install from an SD card (using the modeset option ), also edited the /etc/default/grub file and works fine on reboot, also installed later kernels (2.6.34 rc7 etc from mainline) in an attempt to resolve the brightness issue, didn't work.
I see the thinkpad_acpi driver loaded:

lsmod | grep thinkpad
thinkpad_acpi          81537  0 
led_class               3455  1 thinkpad_acpi
snd                    71802  21 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_usb_lib,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
nvram                   7835  1 thinkpad_acpi


a cat of the thinkpad driver setting:

cat /sys/devices/platform/thinkpad_acpi/leds/tpacpi\:\:standby/brightness 
0
matt@matt-laptop:~/ibm_driver$ cat /sys/devices/platform/thinkpad_acpi/leds/tpacpi\:\:standby/max_brightness 
255

from [http://www.thinkwiki.org/wiki/Thinkpad-acpi](http://www.thinkwiki.org/wiki/Thinkpad-acpi)

not sure where to go from here, I did a recompile but since the driver is already enabled (i think) not sure what to do..






/sys/devices/platform/

---

### Post by xxphilippxx on 2010-07-11
I am having similar issues on my lenovo x201 tablet. About one half of the times I boot the machine I get a black screen. The other half of the times everything works out perfectly, even with visual effects like transparency. What could be the reason for this strange behaviour?

I tried the "i915.modeset = 0"-suggestion but this only made things worse: The graphics starts with the wrong resolution and crashes after one second.

Please note that I am completely new to Linux and not so aquainted with the finer details of the booting process and graphics. My system is up to date.

Anyway, I can still work with this problem, I just need to reboot a couple of times in order to get everything running. Still, I would very much like to resolve it.

Any help would be appreciated,

Philipp

---

### Post by flamacue on 2010-07-24
> **amy_cgi said:**
> For any who might want full details: I was able to install Ubuntu 10.04 Desktop (released version) yesterday using the main install disks (not alt).  I did this by including the options "xforcevesa i915.modeset=0" on the boot line for the default install -- I needed both these options in order to get it to work.  After install, I edited the grub boot command (hold down shift until after the BIOS screen to be able to edit boot options) to include these options in the kernel call.  I then edited /etc/default/grub, setting GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa i915.modeset=0", and then called "sudo update-grub".  Worked like a charm!  I'm loving 10.04!

Thanks for this!

BTW, I'm not sure about the holding in Shift bit...  At the grub (bootloader) options screen, I selected Ubuntu, and hit "c" to edit it...then proceeded as you describe.

Although, it seems I had to hold Shift to get the options screen after booting the Ubuntu install CD (10.04, x86-64).

---

### Post by LeighB2282 on 2010-07-30
> **amy_cgi said:**
> For any who might want full details: I was able to install Ubuntu 10.04 Desktop (released version) yesterday using the main install disks (not alt).  I did this by including the options "xforcevesa i915.modeset=0" on the boot line for the default install -- I needed both these options in order to get it to work.  After install, I edited the grub boot command (hold down shift until after the BIOS screen to be able to edit boot options) to include these options in the kernel call.  I then edited /etc/default/grub, setting GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa i915.modeset=0", and then called "sudo update-grub".  Worked like a charm!  I'm loving 10.04!

Hi All, just installed 10.04 onto my X201, without the grub setting change it worked good when plugged into an external monitor (this was also how I managed to install it) but now I have the setting 'xforcevesa i915.modeset=0' in the grub setting it doesn't boot beyond briefly throwing up the ubuntu logo with purple background the 5 dots then goes to a black screen with the Caps lock LED blinking. anything else I can try?

---

### Post by timesti on 2010-08-17
Hi all,

I am having the same problem as [LeighB2282]("http://ubuntuforums.org/member.php?u=844163"). I have ubuntu 10.04  working on my x201 laptop but the external monitor is not detected. If I boot ubuntu without the i915.modeset=0 option then the monitor is detected but not the laptop's screen --its blank. (This is not true however if I connect the external monitor through the docking station, in which case the external monitor is not detected.)  In the case that I remove the modeset=0 option, the external monitor is detected but the resolution is off and the gui interface in the system options does not recognize the resolution of the monitor, rather it sticks with the original laptop resolution.

Any help on this would be very much appreciated, as I use this laptop many hours a day and having an external monitor working would help me a lot.

thank you!

---

### Post by xxphilippxx on 2010-08-19
Hi!

To whom it may concern: My problem has been resolved by installing a new BIOS version from the Lenovo HP.

Cheers, Philipp

---

### Post by allaboutsam on 2010-08-22
I got mine working and posted the detailed process I followed here:

[http://ubuntuforums.org/showthread.php?p=9752385]("http://ubuntuforums.org/showthread.php?p=9752385")

---

### Post by droople on 2010-08-28
> **LeighB2282 said:**
> Hi All, just installed 10.04 onto my X201, without the grub setting change it worked good when plugged into an external monitor (this was also how I managed to install it) but now I have the setting 'xforcevesa i915.modeset=0' in the grub setting it doesn't boot beyond briefly throwing up the ubuntu logo with purple background the 5 dots then goes to a black screen with the Caps lock LED blinking. anything else I can try?

I got the same issue, add the code, and Caps LED blinking :(


Anyone can help?

---

