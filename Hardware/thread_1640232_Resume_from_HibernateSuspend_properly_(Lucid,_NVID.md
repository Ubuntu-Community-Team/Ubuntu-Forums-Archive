---
title: "Resume from Hibernate/Suspend properly (Lucid, NVIDIA, Lid...)"
date: 2010-12-07
forum: Hardware
---

### Post by CodeRage on 2010-12-07
Like many, I have struggled like hell with Hibernate/Suspend/Resume in Ubuntu Lucid Lynx. Many attempts to fix it included using uswsusp, editing power management scripts to point to s2ram/s2disk, dinking around with graphics drivers, drowning in swap, hitting a brick wall with Xorg, and even traveling to Level 7 hell to get a drop of demons blood and a locket of Succubi hair and mixing it up with some divine acid (ok ok.. I made that part up, but you get the idea of how frustrating  and ridiculous troubleshooting this problem can get). 

Thanks to [Roco's post at launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488720"), I have fixed hibernate/suspend, and most importantly RESUMING from them without hanging at a black screen, with or without motion from a mouse pointer or having to hard-boot (holding power button until machine shuts off - this is like zipping your pants up with skin in the zipper ya know?) to get back to a desktop. The following is my system specs, and then the fix. 

My Kernel: 2.6.35-22-generic (64-bit mode - this fix might work on previous kernel builds, but others will have to confirm/deny this)
Hibernate/Suspend program: pm-utils (default in Lucid, uswsusp not tested with this fix yet)
Graphics Card: nVidia GeForce 360M (mobile card for laptop) 
Graphics Driver: nVidia 260.19.21 (downloaded from nVidia, installed in shell after stopping gdm, then restarting gdm after install)
Machine: Toshiba Qosmio X505 Q870 (desktop replacement laptop)

The fix was simply adding a 'nomodeset' option to the GRUB_CMDLINE_LINUX line in /etc/default/grub. To get this fixin started, go into a terminal and use your favorite editor on /etc/default/grub (in my cause I prefer using Scite), so do:

```
sudo scite /etc/default/grub
```

modify the line : 

> GRUB_CMDLINE_LINUX=""

to look like: 

> GRUB_CMDLINE_LINUX="nomodeset"

Then save and exit the file, then in the terminal run: 

```
sudo update-grub
```

Reboot your machine, then try suspend first through the shutdown menu, then try it again using the lid (if you have the lid action set to suspend in [sudo gconf-editor > apps/gnome-power-manager/buttons – lid_ac and/or lid_battery keys] or [Power Management Preferences > “When lid is closed: “ dropdown list of “On Ac Power” and “On Battery Power” tabs]). 

Once you have confirmed/denied suspend/resume functionality, test hibernate via the menu (and/or hotkeys if yours happen to work, which mine don't). [COLOR="Red"]A word of forewarning, you may need to reboot a few times after failed hibernate/suspend on ac power and battery power each to run out the kinks[/COLOR]. If all works well, then that's a sweet nut cracked. If not, what's new right? The fix is out there somewhere for ya, just don't give up. 

I would like to credit Roco over at launchpad.net for his fix posted on [launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488720"), as quoted below: 

> An update on my last comment: adding the kernel boot option nomodeset to kernel 2.6.33 fixes the suspend/resume X crash for me. I now get the screensaver password prompt instead of a new login when I resume. I added it to /etc/default/grub in the GRUB_CMDLINE_LINUX_DEFAULT entry and ran sudo update-grub to update /boot/grub/grub.cfg.

I hope this rather simple fix works charms for others as well.

---

