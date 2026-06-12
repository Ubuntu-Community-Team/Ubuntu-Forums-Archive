---
title: "8800 series card and Fiesty Flake"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by Visceral Monkey on 2007-04-19
Wow, I've had nothing but problems with the Fiesty final since trying to install it today. I'll skip over the horrible partitioner that suddenly doesn't want to work for me and crashes at just about every step and get right to my main problem.

8800 video card series support.

I've followed several guides in the forums for the Fiesty herd releases and always eventually got my 8800 series card up and running. For some reason, it just wont work anymore. I've tried it the manual way outside an x server with the newest nvidia drivers and I've tried it via synaptic. All I get for my troubles is the xserver wont start message. Does anyone have the "definitive" guide for getting nvidia working in Feisty and 8800 cards? At this point I'm about to switch to Sabayon because it installs everything with almost zero prompting and it works 100% of the time.

Anyone?

---

### Post by bbzbryce on 2007-04-20
Here's what I had to do to sucessfully boot into Feisty without using the recovery mode on my GTS8000. Also note I'm on x64 but I don't think that matters for this.

I used the regular desktop install cd and at the first menu I hit F4 and selected the highest resolution and color setting which allowed me to run the installer.

[INDENT]On a side note: I'm guessing this is because the repositories are very slow to respond but I got about 82% of the way being done when it tried to check for updates (or something along those lines) to which I had to disable my network card to continue the install. That can be done simply by system->administration->network.[/INDENT]

On the first restart once I discovered it didn't work I booted into the recovery console and then after a bit of trouble did the following:

edit the grub menu:
nano /boot/grub/menu.lst

Look for the line ## ## End Default Options ##
and below it there is the regular generic kernel listing.
Delete *quiet* and *splash* from the line and add *vga=0x31B* to the end of the line so it looks something similar to:

kernel       /boot/vmlinz-2.6.20-15-generic root=UUID=.... ro vga=0x31B

Then restart and hopefully you can boot without using the recovery console. At the very least you should be able to see any errors you might get.

---

### Post by Visceral Monkey on 2007-04-20
Still no fix with this. I've tried every idea on the boards and the new Envy script, but that fails to. If *anyone* has an 8800 series card and has the nvidia drivers working without problems, I'd like to hear about it. It appears Ubuntu no longer supports 8800 cards in 3d.

---

### Post by RawMustard on 2007-04-20
Are you using the 32 bit version or the 64bit version.  Because I have the 8800GTX running fine in the 32bit version of feisty.  I can't get the 64bit version to show me a screen to install it though :(

---

### Post by eyelessfade on 2007-04-20
the 8800 series is only supported by the nvidia-glx-new package. I know cause I have it ;)

---

### Post by Visceral Monkey on 2007-04-21
32 bit. Whats the process for getting it to work? Do I just install the glx-new package and that's it? I could swear  I've tried it...

---

### Post by RawMustard on 2007-04-21
See my post here:
[http://ubuntuforums.org/...]("http://ubuntuforums.org/showthread.php?t=413961&page=3&highlight=64bit")

---

### Post by Visceral Monkey on 2007-04-21
Yea, I saw your post there and did the exact same thing according to it..and had no luck. X still crashes when I rebooted.

---

### Post by bbzbryce on 2007-04-21
I have a GTS8800 working using the NVIDIA 64 bit drivers fine. As I wrote before I needed to modify the flags to boot into ubuntu then once I did that I could install the NVIDIA drivers fine following this:

[http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2](http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2)

Even though the above is technically for edgy it still works fine.

---

