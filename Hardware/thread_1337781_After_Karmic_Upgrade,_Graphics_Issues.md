---
title: "After Karmic Upgrade, Graphics Issues"
date: 2009-11-25
forum: Hardware
---

### Post by TrevT93 on 2009-11-25
Okay...so there's a laptop I upgraded to Ubuntu Karmic (from Jaunty).  It runs Intel Integrated graphics (a 945GMS, I believe).  The graphics worked fine under Jaunty, though a little slow, but after upgrading it to Karmic, the graphics are awful.  The resolution and refresh rate both work fine, but windows take forever to load minimize, and close.  And this is not a very weak PC I'm talking about; it has 2 gigs of memory and a Core 2 Duo processor.

Something I've noticed: if I open up the system monitor and try to move it around the screen, the CPU usage skyrockets, occasionally to 90% and above (while running other applications; without, usually 50-60%).  Also, the system monitor window will stutter very badly with another window in the background.  I'm no professional, but I don't think that's supposed to be happening.

Now, my laptop runs the same graphical chipset (or somewhat close; let's put it this way, both chipsets are in the Intel integrated 945 series).  It's running Kubuntu Karmic, and the graphics performance is fine, much better than this other laptop's.  The difference is that my laptop was not upgraded to Karmic; it was installed that way.

Does anyone know of anything that I can do to get the graphical performance back to a norm?  I know that the graphics are pretty weak, but they definitely shouldn't be running as badly as they do on this laptop.

Thanks in advance for any help.

---

### Post by TrevT93 on 2009-11-27
I know I probably shouldn't doublepost like this, but I do have some helpful information.

I installed Sysinfo onto the laptop in question.  It reported that the Linux kernel installed is kernel 2.6.28-16.  Isn't that a bit old?  Wouldn't that have an effect on the rest of the system and therefore the graphics?

More importantly, if what Sysinfo is reporting is true, then why doesn't the laptop's update manager pull a more recent kernel for installation?

I'm fairly sure that Sysinfo *is* reporting the truth; I installed it on Kubuntu on my laptop and it reported the 2.6.31-14 kernel.

(Also, I just found out the other day that the laptop I had upgraded Ubuntu had a processor that supported 64-bit instruction sets, but it's using the 32-bit version of Ubuntu.  Is that something that I need to fix or just something that would be helpful to fix?)

---

### Post by TrevT93 on 2009-11-27
Sorry to do this a THIRD time in a row, but the problem is solved now.  I fixed it myself (one in a row, I'm on FIRE!!).

Here's what happened (and I didn't realize it until I broke something): when Jaunty was in the upgrade process, I chose to allow GRUB to keep the old version of menu.lst.  I had made changes to the GRUB menu using KGrubEditor which would make the menu easier to understand for the person whose laptop I was upgrading, before I underwent the upgrade process.

Of course, as I realized just a short time ago, that means keeping the old initrd and vmlinuz, which were both the 2.6.28-16 kernel's files.  Oops >.< .

But I didn't realize it until I went into synaptic and tried to uninstall the old kernel image.  I (again) told GRUB to keep the old menu.lst.  When I went to reboot the computer, GRUB reported that files weren't found.  And that's when it clicked.

So, to fix it, I ran Karmic from a flash drive and used "gksudo gedit" to edit the menu.lst to read the right files for both the regular and recovery menu entry.  Reboot and BAM!, Ubuntu boots.  And the graphical slowdown doesn't exist anymore.

I know I haven't gotten any responses yet, but if anyone was looking, please do tell me this: is this issue, as far as any of you see it, completely resolved or is there more I need to do before I return this laptop to its rightful owner, to prevent further issues?  Personally, i think it's done, but I just want to make sure.

---

### Post by c_07 on 2009-12-02
Thank you for posting on this issue -- I have a laptop with integrated Intel (945GM) graphics and experienced the same problem after upgrading. Booting with the latest kernel fixed the problem for me as well.

Thanks again!

---

