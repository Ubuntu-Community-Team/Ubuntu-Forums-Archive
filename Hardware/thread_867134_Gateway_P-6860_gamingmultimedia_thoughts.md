---
title: "Gateway P-6860 gaming/multimedia thoughts?"
date: 2008-07-22
forum: Hardware
---

### Post by Der_Idiot on 2008-07-22
I'm going to get a Gateway P-6860 laptop for my portable desktop replacement, and I'll be getting a second drive to dual-boot with windows and run either gnome or kubuntu. Any thoughts on the hardware specs? I want to make sure the wireless and other things (bluetooth?) wont be a nightmare.

Here's a [link to the specs]("http://www.anandtech.com/mobile/showdoc.aspx?i=3273&p=2") on an older model. I'm really only concerned about getting bluetooth, wireless, and HD audio. Nvidia has been playing nice with their drivers, so I should be able to run wine and emulate my games, I plan on double-drive dual-booting until I can dump windows entirely.


Thoughts? This would be happening reasonably soon too :)

---

### Post by Scharpe on 2008-07-22
> **Der_Idiot said:**
> I'm going to get a Gateway P-6860 laptop for my portable desktop replacement, and I'll be getting a second drive to dual-boot with windows and run either gnome or kubuntu.

Exactly what I tried - a Toshiba 320GB that I got for $139.  Ubuntu 8.04 installs beautifully to sdb1 (200GB for Ubuntu, an 8GB swap and the rest for NTFS), and GRUB says it's installing to sdb.

Problem?  GRUB can't mount sdb1 and sda1 (Vista) is invalid.

Don't get me wrong - I love this box, even though I paid $1,300 for it about a week before the price came down to $1,050, but I wish I could get it to boot Ubuntu.

> Any thoughts on the hardware specs? I want to make sure the wireless and other things (bluetooth?) wont be a nightmare.

Ubuntu, from the Live CD, recognizes the wirelsss NIC (I haven't tried it on the Ethernet card yet) - you don't have to do anything.  But you'll probably want to get the nVidia driver - it runs at 800X600 without it.

I haven't tried bluetooth or sound yet either, so I can't help you there, but maybe someone can help both of us with GRUB.

Oh, and putting the laptop to a torture test (Second Life and OpenSim both caused overheating in my other, fairly new, HP laptop) gives me a frame rate banging the pin on an unoccupied region - for anyone who doesn't know what that means, it means that the 8800M GTS is one heck of a GPU.

As I said, GRUB is my only complaint, and I'm sure it's just my lack of experience with GRUB that's not letting me see the solution.

---

### Post by Der_Idiot on 2008-07-23
I see, that's good news. Grub is probably just some setting that needs to be re-worked. But the fact that the rest of it works that well is a heck of a motivator! :)

I might end up just wiping the vista install or pushing the partition down to say... 100g.

And, where did you get it for 1g? I still see it on best buy website for 1350 :(

---

### Post by Scharpe on 2008-07-23
> **Der_Idiot said:**
> I see, that's good news. Grub is probably just some setting that needs to be re-worked.
Now I can get it to the "Starting ..." line, but it hangs there.  Oh, well.  I'm in the middle of upgrading Vista to Ultimate (we're a Windows house, so I have to keep that junk on my computers), but I installed /boot to an SD card, so we'll see if it's the drive or something else.

> I might end up just wiping the vista install or pushing the partition down to say... 100g.
Good idea.

> And, where did you get it for 1g? I still see it on best buy website for 1350 :(
I'm not in my office right now, but I'll ask the gal who told me about the price reduction and post back.  (I paid 1350, but I still think it's worth it.  Compare it to the Alien51 and see if it's worth the extra 2530.  Not to me.)

Edit:  It was $1099 and it was a July 4th one-day special.

And I still can't get GRUB to work, but there are a few more tricks I'll be trying over the weekend.

---

### Post by Der_Idiot on 2008-07-23
Sounds like good times. I'll have to re-work my network and get everything setup for an addition. I'll have to add a wireless card to my router pc.. :-k

---

