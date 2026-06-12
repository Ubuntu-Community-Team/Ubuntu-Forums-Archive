---
title: "Question about Jaunty Hibernate Feature"
date: 2009-05-04
forum: Hardware
---

### Post by Dorzu on 2009-05-04
I installed 9.04 on my Asus 1000HE(netbook) and have had _zero_ problems with Hibernate. However, I noticed something peculiar that I've never seen previously. If I Hibernate it, and later reactivate the machine, Grub appears. I can load XP, use that, and later return to my (still open!) Ubuntu session.

Is that an intended feature? Something serendipitous? Has it been available in the past or is it simply something I've never noticed? I don't ever use Hibernate for my desktop machine, but I found this while carrying my first portable computer in years. I had no idea this could be done. It's awesome! (I hope it's not a bizarre "bug". This is extremely useful to me.)

I just want someone to tell me when/where/how this originated, if possible. I attempted to search for it in the Ubuntu Wiki and these forums, but only found information about errors. As a result, I didn't try Google yet. It will probably be my luck to see a Google link in the first few posts. :-/

---

### Post by keithpeter on 2009-05-05
> **Dorzu said:**
> I just want someone to tell me when/where/how this originated, if possible. I attempted to search for it in the Ubuntu Wiki and these forums, but only found information about errors. As a result, I didn't try Google yet. It will probably be my luck to see a Google link in the first few posts. :-/

My Dell L400 P3 which dual boots XP and a linux distro has always worked like that as well, since 6.06, and with Debian Etch, so I can reassure you there.

I rationalised it as follows: Bios picks up me closing the lid, Windows hibernates the Windows ram and state to the virtual memory file on the Windows hard drive. On waking up, Grub intercepts the event, I pick Windows, Windows knows it has to wake up rather than boot.

Same with Linux, I close lid in Linux, Bios triggers hibernate to swap partition. On wake up, Grub intercepts the event, I pick Linux from the Grub menu, Linux knows it has to wake up rather than boot.

I have two separate hibernates, and when I wake the laptop up, I have to choose which one to wake up from Grub.

I use OpenOffice and Firefox on both OSes, and, yes, I have hibernated one and awoke another and wondered were my documents went!

---

### Post by darthmob on 2009-05-05
it's actually quite simple when you don't go to far into details. hibernate saves all information about the running programs on your hard drive. when you boot the os again it restores that information.

as the information is stored on different locations for windows and linux you can have both in hibernate at the same time.

---

