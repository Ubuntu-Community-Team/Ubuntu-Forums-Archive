---
title: "USB hard drive disappears from desktop after suspend"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by motoperpetuo on 2008-02-08
i have an external USB hard drive connected to my laptop. actually, it's connected to a PCMCIA card that's connected to my laptop (it's an old computer and i need the card for USB 2.0).

whenever i bring the laptop out of suspend mode, the external drive disappears from my desktop and from my file browser. i'm not able to access it from the command line either. the only way to get access back that i know of is to unplug it and plug it back in.

for what it's worth, when this happens i can run fdisk -l from the command line and the external drive is listed there as /dev/sdb1, even if i can't see it on my desktop or access it from the file browser or the command line. anyone know how i can prevent it from disappearing like this?

---

### Post by chrisdeckard on 2008-02-08
I'd say this would be expected behavior.  I don't believe PCMCIA saves it's state during suspend.  The modules are unloaded, and then reloaded at resume.  It just seems that it isn't rescanning what's connected.

I guess the big question is, why are you suspending a laptop while having an external drive attached?  If you're not going to move it around, why not just keep it on?  :-)

If reattaching the drive makes it show up again, you're just going to have to get used to that.  PCMCIA is old technology.

-Chris

---

### Post by motoperpetuo on 2008-02-09
> **chrisdeckard said:**
> I'd say this would be expected behavior.  I don't believe PCMCIA saves it's state during suspend.  The modules are unloaded, and then reloaded at resume.  It just seems that it isn't rescanning what's connected.

I guess the big question is, why are you suspending a laptop while having an external drive attached?  If you're not going to move it around, why not just keep it on?  :-)

If reattaching the drive makes it show up again, you're just going to have to get used to that.  PCMCIA is old technology.

-Chris

actually, that brings up another thing i've always wondered about. right now, i have my laptop set to go into suspend mode when i close the lid (i like to close it when i'm not using it to keep dust out). would it be a bad idea to change that to "do nothing"? i've always been under the impression that not going into suspend or hibernate when the laptop is closed is somehow harmful and, hence, always gone with suspend. should i maybe go with "do nothing" and see if that works?

another point is that i don't recall ever losing access to the external drive when coming back from suspend in windows on this computer. like i say, even in linux, the computer still sees the drive after coming back from suspend, i just can't access it. maybe PCMCIA saves its state during suspend in windows, but not in linux, or at least not entirely? that wouldn't surprise me; suspend is one of the small handful of things that seem to generally work better in windows than in linux.

---

### Post by Yellow Pasque on 2008-02-09
Yeah, as long as your laptop's on AC, there's no need to suspend (provided your hard disk head parking behaves properly under Linux). I would set it to turn the screen off when the lid closes, though.

---

### Post by tirade on 2008-02-27
I have a USB Western Digital Passport hard drive plugged into my T61p and I have the same issue.

Is there something I can do to the suspend script (if such a thing exists) to make it unmount the USB when going into suspend/hibernate so that it rediscovers the USB drive when it wakes up?

---

### Post by s0lar on 2008-05-23
Funny that last thing. I have the problem that my cd drive shows up again when I resume. There's an option at the tab media for file management preferences that you can select with the option "browse media when inserted".
I like the option but it makes my cd drive reappear when I resume after suspend, very annoying :).

---

