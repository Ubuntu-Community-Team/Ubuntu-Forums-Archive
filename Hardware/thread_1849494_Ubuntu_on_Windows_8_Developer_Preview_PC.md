---
title: "Ubuntu on Windows 8 Developer Preview PC"
date: 2011-09-24
forum: Hardware
---

### Post by Aide9aic on 2011-09-24
(NOTE: yes, this is somewhat of a lengthy post. However, I want to ensure you have enough info about what I'm attempting.)

I attended Microsoft's //build/ conference a couple weeks ago and picked up one of those new "developer preview" tablet/slate PCs. This is a tricked-out Samsung slate of some kind; either [it is]("http://www.istartedsomething.com/20110914/build-attendees-take-home-samsung-windows-developer-preview-pcslate/") or [it isn't]("http://www.withinwindows.com/2011/09/16/the-windows-developer-preview-pc-is-not-a-samsung-series-7/") a variant of the forthcoming [Series 7 slates]("http://thisismynext.com/2011/08/31/samsung-series-7-slate-specs-release-date-hands-on/"). Last night I thought I'd see whether I could get Ubuntu to at least boot on my shiny new toy.

I downloaded the x64 ISO of Oneiric beta 2 and (on my Kubuntu 11.04 laptop) used Startup Disk Creator to copy the ISO to a 2 GB flash drive. Fortunately, there's already a Microsoft forum for these slates, and someone posted [instructions for entering the BIOS]("http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/42859fb8-7a89-44ed-a8e3-09a51e2fb2ab"). So I did that, booted the USB, and saw an error telling me that my image was unsigned. Uh oh, I thought, locked out? Nope, there's a setting to disable secure boot. So I did that. Now the USB boots, but instead of seeing the purple splash screen with the keyboard and the human, a very brief error message flickers in the upper left corner (white text, black background) and then GRUB's menu appears. It gives me three options: try without installing, install, check media. Since I don't actually want to install Ubuntu (yet), I chose the first option.

The screen went blank, although the backlight remained on. The LED on the USB drive flickered for a while, say 20 seconds. Then it remained solidly lit, with no further progress. I waited for a couple minutes before rebooting back into the BIOS.

There aren't a whole lot of configuration options in this BIOS. For one thing, it's actually a UEFI machine, and it comes with CSM (compatibility systems module) support disabled. Hmm, I thought, maybe I should enable that. So I did, and when I rebooted, the Samsung logo looked wider, as if the display were a lower resolution -- hmm, are there two video chips in this box, one for UEFI mode and one for BIOS mode? Regardless, when Ubuntu started, I saw the exact same behavior as before: GRUB menu, choose "try," 20 seconds of USB light flicker, then nothing.

Alright, so now it's time to try some manual troubleshooting steps. With the slate still in BIOS compatibility mode, I booted the USB and this time, when the menu appeared, I dropped to a command prompt. In /boot/grub/grub.cfg we see the following:

```
if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
```

Issuing the **lsmod** and **terminal_output** commands showed that, in fact, they executed fine: the modules were loaded and the output mode was correct. Next I tried manually issuing each of three commands under the menu entry. No errors appeared so I issued a **boot** command, which resulted in the same behavior as before.

Next step: return the BIOS to UEFI mode (CSM disabled). Follow the steps as before. Same result again. Argh!

Next steps: try, in sequence, first in BIOS mode then in UEFI mode, manually setting the **gfxmode** and **gfxpayload** variables to each of the six values returned by GRUB's **videoinfo** command -- in fact, there are different video modes, three for BIOS and three for UEFI. I would do this, follow with the **linux** and **initrd** commands, and this time, set **debug=all** before issuing the **boot** command.

Adding that **debug** variable showed at least one bit of consistency: in UEFI mode, I could watch as the kernel was displaying its status parsing the UEFI. It would appear to get all the way to the end, the screen would clear, and then the system would hang. This happened for all three **videoinfo** resolution choices. When I switched the machine to BIOS mode, with **debug=all** set, the kernel appeared to crash before it reached the end of parsing EFI: eventually it would just stop during the scrolling debug messages.

So after two hours of testing and futzing, I'm stuck. I don't know where to go from here. I finally found a [Samsung web page]("http://www.samsung.com/global/buildpc/index.html") with more info on the machine; alas, it lacks good technical data. What I do know about this machine is that it's got a Core i5 processor, so I'm wondering if I'm running into issues with Sandy Bridge stuff? I'd appreciate any pointers to how I can get Unbuntu to run on this gadget. Thanks for reading this far, and thanks for any ideas you might have.

---

### Post by wolfen69 on 2011-09-24
My guess is that since it is a new tablet, it will be highly proprietary and very difficult to install any form of linux on it. It normally takes 6 months to a year for the linux devs to catch up and add the proper firmware and drivers to the kernel for new hardware, if ever. I wouldn't count on it working anytime soon.

---

### Post by OrphanShadow on 2011-09-24
> **wolfen69 said:**
> My guess is that since it is a new tablet, it will be highly proprietary and very difficult to install any form of linux on it. It normally takes 6 months to a year for the linux devs to catch up and add the proper firmware and drivers to the kernel for new hardware, if ever. I wouldn't count on it working anytime soon.

I dont think this is as proprietary as it seems. These new Samsung slates use general off-the-shelf x86 processors (Core i5's I think).

As to the OP, you could try utilizing one of the alternative boot images found at [http://cdimage.ubuntu.com/releases/11.10/beta-2/]("http://cdimage.ubuntu.com/releases/11.10/beta-2/"). Generally they allow for more boot options, as well as non-graphical installation.

If you manage to get it installed with one of those, you may need to edit the UEFI partition that Windows 8 has undoubtedly put on the machine, so as Grub can be loaded as the main bootloader (see here: [https://help.ubuntu.com/community/UEFIBooting]("https://help.ubuntu.com/community/UEFIBooting"))

---

### Post by Aide9aic on 2011-09-24
> **OrphanShadow said:**
> As to the OP, you could try utilizing one of the alternative boot images found at [http://cdimage.ubuntu.com/releases/11.10/beta-2/]("http://cdimage.ubuntu.com/releases/11.10/beta-2/"). Generally they allow for more boot options, as well as non-graphical installation.

While I'd prefer to try before installing, I got frustrated enough that I even gave the alternate image a go. Same essential problem: the GRUB menu appears, but ultimately none of the choices makes progress. Curiously, I can't seem to get the thing to boot into what looks like a true non-graphical mode -- the text in the menu has kind of a graphical shape to it. I haven't seen that good old 80x25 pure text.

> **OrphanShadow said:**
> If you manage to get it installed with one of those, you may need to edit the UEFI partition that Windows 8 has undoubtedly put on the machine, so as Grub can be loaded as the main bootloader (see here: [https://help.ubuntu.com/community/UEFIBooting]("https://help.ubuntu.com/community/UEFIBooting"))

Yup, read through that page a couple times. I'll admit I'm fairly clueless about UEFI, so I do have some learning ahead of me. But since I'm struggling even to get this thing to boot, I suspect there's still another issue yet to be resolved.

---

### Post by bsm117532 on 2011-10-29
Could you give us a status update?  I'm thinking of buying one of the Samsung Slates when they come out in a couple weeks, and I intend to install Linux on it.

Were you ultimately successful or have you made any more progress?

After it's officially released, there will certainly be more people trying...

---

### Post by Aide9aic on 2011-10-30
Unfortunately, I haven't been able to devote a lot of time to this. I was unable to get any of the various Ubuntu release types to get past GRUB. My suspicion is that it's a video driver problem, because the output of GRUB's **videoinfo** command seems strange, as if it were unable to identify any modes it knew and instead just guessed.

Another potential problem could be the unit's BIOS compatibility support module. When that's enabled, I can't even get to a GRUB prompt.

It's highly likely that the UFEI on this machine is extensively customized. I don't know whether the forthcoming similar retail units will be similarly affected. If you can get your hands on one before you plunk down money, press both the Volume-up and Volume-down buttons on the left side while pressing the power button on the right. This launches the UEFI setup. If you see this screen...

[IMG]http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-01-29-43-metablogapi/0624.Figure_2D00_5_2D002D002D00_Samsung_2D00_PC_2D00_secured_2D00_boot_2D00_setting_5F00_thumb_5F00_02016A69.jpg[/IMG]

...then avoid the purchase.

One thing that might help is if any UEFI experts happen to be lurking about here on the forum. If so, I'd like some assistance building a good UEFI-capable boot installer on USB. I've seen various pages with steps, some of which are contradictory, some of which are too Mac-oriented, and some of which seem to require using a computer with UEFI to build -- but none of my other computers do.

---

### Post by bsm117532 on 2011-11-10
There's some good info over at the Arch linux wiki: [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

Have you tried installing a UFEI shell (toward bottom of that page)?  If you did, is the keyboard usable to navigate it?

Also that page indicates the importance of compiling a kernel with UFEI support.  Do the ubuntu installers you used have it?

---

### Post by Aide9aic on 2011-11-11
> **bsm117532 said:**
> Have you tried installing a UFEI shell (toward bottom of that page)?
Not yet. I found that page a while ago, and didn't quite understand what I was reading. I've learned more now, and that seems like a reasonable approach. Thanks for the reminder.
> **bsm117532 said:**
> Also that page indicates the importance of compiling a kernel with UFEI support. Do the ubuntu installers you used have it?
The [UEFI Booting]("https://help.ubuntu.com/community/UEFIBooting") page has a blurb that leads me to believe they do: "From Ubuntu 11.04 onwards (x86_64 only), the ISO CD supports UEFI booting and the Ubuntu installer will try to set up the bootloader for (U)EFI boot." It goes on to warn that the installer formats the EFI partition as FAT16, which seems kind of strange.

I also just noticed this thread about [Natty and Windows 7 co-existence with UEFI]("http://ubuntuforums.org/showthread.php?t=1753717"); I suspect some of the discoveries reported there would apply to Oneiric and Windows 8. More research...

---

### Post by Aide9aic on 2012-02-11
**Update**

Recently I obtained a couple new UEFI-capable ThinkPads, and I decided it was time to get off my butt and learn this stuff. Through trial and error, I managed to build some decent UEFI skillz, which I reported at Kubuntu Forums:

[How I (sort of) conquered UEFI]("http://www.kubuntuforums.net/showthread.php?57257-How-I-(sort-of)-conquered-UEFI")

I'm now working on getting Ubuntu to boot on the Samsung tablet. I'm live-reporting my progress in a different thread there:

[Getting Ubuntu onto my Samsung //build/ tablet]("http://www.kubuntuforums.net/showthread.php?57362-Getting-Ubuntu-onto-my-Samsung-build-tablet")

---

### Post by Aide9aic on 2012-05-03
**Another update**

Finally, success! I've recorded a brief 15-minute tour of Plasma Active Two, running the [Kubuntu Active]("http://cdimage.ubuntu.com/kubuntu-active/daily-live/current/") build linked from the Plasma Active [installation page]("http://community.kde.org/Plasma/Active/Installation").

Two pages of interest for you:

* [An earlier post]("http://www.kubuntuforums.net/showthread.php?58504"), typed using the tablet and on-screen keyboard
* [My video tour]("http://www.kubuntuforums.net/showthread.php?58630")

---

