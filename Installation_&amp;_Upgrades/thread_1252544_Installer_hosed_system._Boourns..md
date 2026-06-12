---
title: "Installer hosed system. Boourns."
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by jeamer on 2009-08-29
Hi, totally baffled here.

I booted into the Kubuntu installer, formatted my linux HD to install Kubuntu, all prompts completed and install started. Left for a bit, came back, screen was blank, couldn't revive. Left it for an hour to finish "installing" if it was still installing and not communicating with the display, then powered down and powered back up. 

The install didn't work. Grub ends with error 2, a bad file or directory type. Pop the install CD back in, now my keyboard or mouse (tried several different ones BTW) aren't recognized by the computer (can't even access BIOS). They blink on boot up, suggesting that the hardware is communicating with them, but I can't get them to respond.

Further, because the keyboard/mouse aren't recognized initially anymore, my only two boot options are the error-grub or boot into the live CD. But, the live CD wont work anymore. Actually, NO live CD will work, I've tried the aforementioned Kubuntu 9.04, Ubuntu 9.04, Ubuntu 8.10. Some of the error messages I get now when trying to load the liveCD:

Buffer I/O error on device sr1, logical block 315579
end_request: I/O error, dev sr1, sector 1262300
SQUASHFS error: sb_bread failed reading block 0x98525
SQUASHFS error: Unable to read page, logical block 313198

Alternate installers won't work without the keyboard. The funny, frustrating, and ironic thing is that in the screwed loading of the LiveCD, the keyboard/mouse are recognized. It would appear the only thing not recognizing the keyboard/mouse is the language selection at the very start. This language selection counts down from 30, booting into the liveCD (if on a live CD cd) at 0, or just sits there in the alternate installer. 

I am completely unable to do anything, not being able to access my BIOS. What the heck am I supposed to do in this situation? Thanks for any input. I've used Ubuntu for ~5 years now, and as such want to work this out big time. No going back to any other OS (I hope!). This'll teach me for trying KDE ;)

PS This was *finally* my first clean install after upgrading since 6.10. Everything was running smoothly (but bloated :) ) before the attempted install

---

### Post by jeamer on 2009-08-31
UPDATE: No one seemed to have an answer, that's fine, the thread got pushed down in priority pretty quickly.

I did some looking and found that the SQUASHFS errors related to:

"After searching the WEB again for problems with squashfs I came across a reference to DMA. By supplying the boot time option:

ide=nodma

I got both the Ubuntu and Fedora live CDs to boot."

so I followed this. I also replaced some of the wiring (which was pretty old) between the HD and the mobo (due to the I/O errors) and that seemed to fix the LiveCD bootup. I found this strange as a fix, however, as in booting off the LiveCD I didn't think you needed the HD until you started GParted. Oh well! 

The KDE cd never worked, likely due to incompatibility with the hardware, which is really old, but the gnome ubuntu install went well.

EDIT:
[https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors) shows that it may not have been both, but one or the other. It lists the memory problems (my first fix) and the bad data cables (my second) as possible errors. So, it may have been either or both!

---

