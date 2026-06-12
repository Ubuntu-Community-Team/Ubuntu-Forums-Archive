---
title: "Physically Moved Hard Drive Stops Booting"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by jimmywet on 2007-01-29
I think I understand what happened and what to do to correct, but is there another, better way?

Some background:  I have an IBM T41 laptop that I use for work and pleasure.  I have a second hard drive bay that I use for work with different OS's on different HDs.  I can slide the appropriate HD in the bay, change the bios and I am booting a different OS.  After using the Live CD Edgy, I wanted to try a HD install for performance and permanence.  So I grabbed another HD for the Ubuntu Edgy OS.  This way I was not worried about dual booting and messing up another OS as I learn Linux.  I installed the HD in the Main HD bay, put the CD in the bay and booted.  I partitioned with Gpart and all went much better than I expected!!!  I was impressed!!!  I spent the weekend getting under the hood and adding, personalizing (hopefully all in my /Home partition and really loving the experience.

Today, I put my main HD (XP Pro) back in the main HD slot, put the Ubuntu HD in the second Drive bay caddie and went to work.  XP Pro worked as expected when needed for work, but for my use, I wanted to use Ubuntu.  When I did the bios switch to boot from the Second HD it fails and I am sure you all are knowing why.  I got the message /bin/sh: can't access tty; job control turned off etc. etc.  Generally, I like to figure things out on my own.   I figured out the naming with Linux is different hda1 is now hdb1, since I moved it.  I changed the Grub menu.lst to reflect that and it got further, but still failed.  More research and I found out about the fstab file and see the references to the old locations, but read in the forums that I should not edit it in graphical mode.  I have only tried one terminal process with a detailed instruction on apget or "Something" similar.  That was two days ago and I basically just typed the instructions I read.  Obviously, I have switched the HD around at the moment to access the OS and I can not have the Ubuntu HD in the machine at the same time as the CD, since they go in the same bay, or I would have just re-installed that way.

Is there an easy way to solve this?  If not, am I on the right path and what am I missing and how would I edit in non-graphical mode?  If I do that while it is in the Main HD Slot, will I become unstable or cause other issues?

Sorry for the long post, but wanted to get as much info out there to the community for your help.  I searched and could not find one post about moving hard drives, so maybe I am the only chicken out there that would not use Grub for a true dual-boot system...

Thanks in advance!

---

