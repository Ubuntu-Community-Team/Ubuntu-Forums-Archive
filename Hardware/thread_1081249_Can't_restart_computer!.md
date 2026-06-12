---
title: "Can't restart computer!"
date: 2009-02-26
forum: Hardware
---

### Post by Dawei87 on 2009-02-26
I am using ubuntu 8.10 on an hp dv5 and i cannot restart my computer at all. After spending a long time on the forums i fixed the problem with suspend/resume/hibernate, but i cant restart. when i press the restart button it seems to shut down fine, but then when it restarts it shows the hp splash screen, but then just a blank screen with a flashing cursor and grub wont load. please help! this is one of the last things i need before i can wipe vista off my hard drive for good!!

---

### Post by Dawei87 on 2009-02-27
bump

---

### Post by brokenLockpick on 2009-02-27
Is this only happening on reboots, or does it happen on cold boots as well?

---

### Post by Dawei87 on 2009-02-27
it only happens on restarts, i can shutdown fine and suspend fine, and up until i upgraded my graphics card driver last night i could suspend as well. i have not been able to restart my computer though since i first installed ubuntu

---

### Post by brokenLockpick on 2009-02-27
> **Dawei87 said:**
> it only happens on restarts

So if the computer is turned off completely and you power it back on you can boot?

If that is indeed the case, I had a similar problem with my Asus 900A, where a reboot would fail but a complete power off followed by turning it back on allowed it to boot. This turned out to be a hardware quirk that was resolved by a bios update.

But if you are saying that you shut it down once and that it hasn't been able to boot scince then there is an entirely different problem.

---

### Post by Dawei87 on 2009-02-27
yea, i can shutdown fine. im actually about to upgrade my bios, so im glad you said that helped you. it'll take me a minute but i'll put a post on here and let you know if it worked. thanks for the quick responses!

---

### Post by Dawei87 on 2009-02-27
OK. i just upgraded my bios and now i can restart my computer!! but i still am having trouble with hibernate. when the computer tries to wake up from hibernate all i get is a black screen with a few random splotches of color. i can suspend fine, and i was able to hibernate until i upgraded my graphics card driver. andbody have any ideas on this?

EDIT: turns out i still cant restart consistently. after the bios upgrade i restarted twice, but now im back to the same problem as before. so i guess the bios didnt change much

---

### Post by brokenLockpick on 2009-02-27
> **Dawei87 said:**
> turns out i still cant restart consistently

That's unfortunate. I'm really inclined to believe it is a harware related problem. I'm out of ideas that are more than speculation at this point. It almost seems like something hangs around that prevents grub from being loaded into memory. 

Maybe try a memory test, my logic is that when initialized from powered down state it would either load all 1s or all 0s but perhaps during reboot there is a bit that can't clear properly and throws off the bootloader.

---

### Post by Dawei87 on 2009-02-27
i am willing to try anything. im still pretty new though, what is a memory test?

---

### Post by brokenLockpick on 2009-02-27
You can still get to grub if you totally power off the computer correct?

There should be an option for memtest86 or something similarly named.

Alternately I believe the Ubuntu live cds include an option to test the memory.

---

### Post by Dawei87 on 2009-02-27
ok. ill give that a try. and yes, i do get grub when i shutdown completely. so what exactly will this memory test do? and how can i make it help me?

---

### Post by brokenLockpick on 2009-02-27
What it does is tests the RAM to make sure that it is not malfunctioning. It will do things like write all ones write all zeros, write a specific pattern and swap pieces of it around. I don't know the exact steps but it seems similar to alot of the OE supplied tools that I encounter at work for detecting defective sticks of RAM.

What it will do for you is isolate whether or not you have a memory module(RAM stick) that is somehow defective. From my experience hardware isn't necessarily broken or working but sometimes it's in the process of failing where it works sporadically. Sometimes small errors don't cause problems except with specific tasks.

---

### Post by Dawei87 on 2009-02-28
ok. did the memtest and everything seems ok. (it took quite awhile). also, my computer is barely six months old, so i dont really think my hardware would be failing on me yet. i havent even used the computer too much.

---

### Post by brokenLockpick on 2009-02-28
I'm pretty stumped then, unfortunately I don't have really deep knowledge of hardware.

But as far as only being six months old, that means very little when you deal with the number of systems I've had to on the job, it can be truly shocking how often systems from mainstream companies with good reputations ship with faulty components. I've unpacked brand new machines with bad memory, motherboards, PSUs etc. We got one run where the motherboards all failed within the first 6 months. 

You said that your machine was from HP correct? Do they have a diagnostic suite like Dell's diagnostics or Lenovo's PC Doctor. Not that those things always catch errors, I've actually had to do old school "swap this swap that" process of elimination troubleshooting on some systems.

Have you tried turning off the ubuntu boot splash screens so you can check for error messages during boot shutdown etc? Some times that can be illuminating.

---

