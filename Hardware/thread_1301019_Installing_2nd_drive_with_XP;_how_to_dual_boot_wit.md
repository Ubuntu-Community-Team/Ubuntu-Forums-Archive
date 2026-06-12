---
title: "Installing 2nd drive with XP; how to dual boot with 2 drives?"
date: 2009-10-25
forum: Hardware
---

### Post by 213374U on 2009-10-25
Hey guys, it's been a while since I sat down and actually messed with the inner workings of my Feisty desktop. Yes, I'm still running feisty, got compiz up and working well with my ATI card and decided that it was a good point to stop until I pick up a new box.

My question, I just picked up another Dell Dimension desktop off my dad who upgraded there system a few months ago. I'm wanting to take the hard drive from his (loaded with Win XP) and add it to my Ubuntu box for a total of 2 drives. I played around with a dual boot of Ubuntu and XP on the same drive a while back but found that I didn't need XP taking up the additional space on my measly 60GB drive, just didn't use it enough.

In that setup, I used a grub loader to boot into the Ubuntu or XP partitions on the drive. Would I be doing the same thing here? 

I haven't even tried cracking into it on my own yet, want to make sure I'm not getting in over my head. 

Anyway, thanks in advance for any help. And I'm sorry if this is the incorrect place for this post. Assumed it would be here as I'm adding a second drive to my box.

---

### Post by mustafa-khattab on 2009-10-25
Well, first you have to make sure that the drive that has Linux installed is your master drive, so that you may be able to boot into Linux and edit your grub.conf file.

I suggest checking this link out, an almost exact solution to your problem:
[http://www.linuxquestions.org/questions/linux-general-1/grub-dual-boot-dual-drives...-311832/](http://www.linuxquestions.org/questions/linux-general-1/grub-dual-boot-dual-drives...-311832/)

---

### Post by 213374U on 2009-10-25
Thanks for the quick response mustafa. I checked out that link but didn't understand a word of it :P

I went ahead and pulled the drive from the XP machine and installed it in my box. Hooked everything back up and turned it on. It attempted to boot into Windows but was unsuccessful, stopping to "dump physical memory", something about the ACPI.

Going to disconnect the drive and boot back into Ubuntu. Where do I need to start looking to configure on that end? Not sure if I even have GRUB installed anymore.

Man, haven't been active in the tinkering for almost 2 years. Think I forgot more than I knew :P

---

### Post by louieb on 2009-10-25
XP is not going to like being moved to new hardware. It will require at least new activation. 

Might look at getting a KVM switch to share your keyboard, video, mouse.

---

