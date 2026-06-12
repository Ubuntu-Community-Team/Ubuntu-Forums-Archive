---
title: "ACPI New Motherboard"
date: 2011-11-26
forum: Hardware
---

### Post by Toxcity on 2011-11-26
Good evening all! 

I am running Ubuntu 11.10 64 and have just moved it to a new PC. Everything within the PC has changed apart from the GPU and the Memory.

I am under the impression that ACPI is what controls shutdown and sleep. After the upgrade my OS can't shutdown on its own, it prints "Will Now Halt" and you hear the HDDs turn off but the PC and fans remains on. Same kind of issue with sleep mode. If I tell it to sleep the screen goes blank but everything stays on.

Now ACPI 2.0 is enable in the bios and worked perfectly find on my previous hardware. 

I have not reinstalled the OS because I like it just the way it is and it would take ages to get a distro back to this state. I was also under the impression the Linux is plug and play.

Everything else is fine.. just no automatic shutdown or sleep mode.

Any ideas? 

Thank you. :) 

Nic

---

### Post by Redblade20XX on 2011-11-26
If my believe isn't correct than some please enlighten me! :) 

I believe that when you first installed ubuntu it sets the os up based on the hardware that was there at the moment. Replacing the motherboard caused a fundamental change in the system thus invalidating the setup scheme. It's like giving  specific instructions, based on a specific map,  to someone and the specified map to get to a location. Upon replacing the mobo, you essentially gave them a new, different map with the old instructions therefore they will have problems find the location.

If you can make a spare partition on your current hard drive or an use a spare hdd, try a fresh install of the os and see if this changes anything before you have to reinstall anything on your primary partition/hdd.

Hopefully my assumptions are correct and this helps! :-P

- Red

---

### Post by Toxcity on 2011-11-27
That was the impression I was under. But is there a way around it? To get the system to reconfigure? :)
Thanks for the reply!

---

### Post by Toxcity on 2011-11-27
Things get interesting...

Gave up trying to get it to work so I reinstalled. STILL DOESN'T WORK! :O

STUCK! :(

---

### Post by dandnsmith on 2011-11-27
I suggest a google search using the motherboard model (or the manufacturer/model of the PC) and acpi problem.
It has worked for me in the past - but the advice is often a bit OS/BIOS oriented.

---

### Post by trundlenut on 2011-11-27
What happens if you add "acpi=off" or "noacpi" to the grub entry?

---

### Post by Toxcity on 2011-11-28
I've search and searched. Can't imagine why it isn't supported it has a common chipset (X39). I'll have a go messing with the kernel acpi boot parameters. 

Already tried acpi=force. :(

Edit: Updated from Kernel 3.2.0-1 to 3.2.0-2 and everything seems to be working. Thanks for all the suggestions guys. :)

---

