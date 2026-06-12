---
title: "Resume from Hibernate/Suspend properly (Lucid, NVIDIA, Lid...)"
date: 2010-12-07
forum: Hardware
---

### Post by CodeRage on 2010-12-07
Like many, I have struggled like hell with Hibernate/Suspend/Resume in Ubuntu Lucid Lynx. Many attempts to fix it included using uswsusp, editing power management scripts to point to s2ram/s2disk, dinking around with graphics drivers, drowning in swap, hitting a brick wall with Xorg, and even traveling to Level 7 hell to get a drop of demons blood and a locket of Succubi hair and mixing it up with some divine acid (ok ok.. I made that part up, but you get the idea of how frustrating  and ridiculous troubleshooting this problem can get). 

Thanks to [_Roco's post at launchpad.net_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488720"), I have fixed hibernate/suspend, and most importantly RESUMING from them without hanging at a black screen, with or without motion from a mouse pointer or having to hard-boot (holding power button until machine shuts off - this is like zipping your pants up with skin in the zipper ya know?) to get back to a desktop. The following is my system specs, and then the fix. 

**My Kernel:** 2.6.35-22-generic (64-bit mode - this fix might work on previous kernel builds, but others will have to confirm/deny this)
**Hibernate/Suspend program:** pm-utils (default in Lucid, uswsusp not tested with this fix yet)
**Graphics Card:** nVidia GeForce 360M (mobile card for laptop) 
**Graphics Driver:** nVidia 260.19.21 (downloaded from nVidia, installed in shell after stopping gdm, then restarting gdm after install)
**Machine:** Toshiba Qosmio X505 Q870 (desktop replacement laptop)

The fix was simply adding a **nomodeset** option to the GRUB_CMDLINE_LINUX line in /etc/default/grub. To get this fixin started, go into a terminal and use your favorite editor on /etc/default/grub (in my case I prefer using Scite), so do:

```
sudo scite /etc/default/grub

**OR**

sudo gedit /etc/default/grub
```

modify the line : 

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to look like: 

> GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"

Then save and exit the file, then in the terminal run: 

```
sudo update-grub
```

Reboot your machine, then try suspend first through the shutdown menu, then try it again using the lid (if you have the lid action set to suspend in [sudo gconf-editor > apps/gnome-power-manager/buttons &#8211; lid_ac and/or lid_battery keys] or [Power Management Preferences > &#8220;When lid is closed: &#8220; dropdown list of &#8220;On Ac Power&#8221; and &#8220;On Battery Power&#8221; tabs]). 

Once you have confirmed/denied suspend/resume functionality, test hibernate via the menu (and/or hotkeys if yours happen to work, which mine don't). [COLOR="Red"]A word of forewarning, you may need to reboot a few times after failed hibernate/suspend on ac power and battery power each to run out the kinks[/COLOR]. If all works well, then that's a sweet nut cracked. If not, what's new right? The fix is out there somewhere for ya, just don't give up. 

I would like to credit Roco over at launchpad.net for his [_fix posted on launchpad.net_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488720"), as quoted below: 

> An update on my last comment: adding the kernel boot option nomodeset to kernel 2.6.33 fixes the suspend/resume X crash for me. I now get the screensaver password prompt instead of a new login when I resume. I added it to /etc/default/grub in the GRUB_CMDLINE_LINUX_DEFAULT entry and ran sudo update-grub to update /boot/grub/grub.cfg.

I hope this rather simple fix works charms for others as well.

---

### Post by CodeRage on 2010-12-07
I'd like to add a note regarding the hibernate part of this business. It does take longer than previous ubuntu distros to go into hibernate, and resume from it. On resuming, you will see a black screen with your mouse pointer over it for upwards of 10 to 30 seconds before your desktop is restored as it was prior to going into hibernation. 

All we need is the hibernate part to be optimized and then I think we're back in business. So my guess is the next step in flushing out the bug rather than using workarounds is to have devs analyze the processes that **nomodset** affects, and deduce which one(s) are the actual issue(s) to suspend/hibernate/resume. 

FYI: I was never able to get suspend/hibernate to work when my swap file was located in the active partition that I run linux from. I literally had to make a swap partition only. When the day comes that I figure out how to make it work, i'll certainly post it. :D

Thank you to all ubuntuforums users and launchpad folks, and the linux community in general for the rockin work done to improve unbuntu all the time, even if some decisions break it at release/update time.

---

### Post by zenon222 on 2011-09-04
AWESOME!  Works for me in 10.04.3 LTS on my desktop machine.
Thanks!

---

### Post by mauricebis on 2012-09-15
On my machine, Toshiba satelllite A110, I had to add the option acpi_os_name="Microsoft Windows NT" in the booting option to fool the BIOS/ACPI as discussed in [https://wiki.archlinux.org/index.php/Suspend_to_RAM]("https://wiki.archlinux.org/index.php/Suspend_to_RAM"). Before then, it would sometimes work and sometimes not.

---

### Post by overdrank on 2012-09-15
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

