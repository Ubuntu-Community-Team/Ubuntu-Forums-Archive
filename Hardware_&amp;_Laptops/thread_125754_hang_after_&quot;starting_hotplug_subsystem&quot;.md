---
title: "hang after &quot;starting hotplug subsystem&quot;"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by jrjbertram on 2006-02-04
Hi,

I'm an off-again-on-again linux user with some basic understanding of linux (though I'm a long way from really understanding it), and I thought I'd try out 5.10.  I've got a box with an intel 865g that I can't get ubuntu to boot on, though.  It appears to hang right after the "starting hotplug subsystem" message.  I've tried both the live CD and the install disc, and both have the same affect.  I also tried a 5.04 disc that I had laying around, and have the same result.

I figured that maybe the hotplug hang was due to the internal graphics, sound, or usb, so in my bios, I selected all the options that disable as much as I can.  Sound, video, and usb should now be shut off.  I've got an old nVidia TNT2 card plugged into PCI at the moment that I'm running my video off of.

I know this isn't much to go on, but I can't really get it to the point where I can do anything useful.  I've been googling and have found a number of other people who've run into similar issues, but no resolutions were posted.

If anyone has any ideas, I'd appreciate some pointers.

Thanks,
- J.

---

### Post by jrjbertram on 2006-02-04
Actually, as a last ditch effort, I reverted back to my internal graphics card (as suggested in a web site I found)... and this turned out to be the problem.  So.. give that a shot if you run into the same issue someday.  Weird.

---

### Post by vrode on 2006-02-04
I have a similar situation on my brand new laptop (Alienware area51-m5700). Machine locks up during bootup on hotplug subsystem message. How do you revert to an internal graphics card on a laptop?

Pointers will be appreciated.


regards,
/virendra

---

### Post by jrjbertram on 2006-02-05
I don't think you can.  You're already on 'internal' graphics because you're using the graphics chip on your motherboard.  'external' graphics means a video card that you plug in to a spare PCI or AGP slot.  Laptops don't usually have spares of either because they're built to be so small and compact.

You might try to find out what kind of hardware is on it.  If it's an intel-based motherboard, it seems like linux has lots of issues with recent intel hardware.  (intel doesn't play nice with open source developers).  One thing that you might try is to go into setup in your BIOS and disable some of your devices.  Start with the sound, if it'll let you shut it off.

Also, I think there's a separate area on this forum for laptop issues; re-posting your message there might get you some *real* help.  (I don't have a laptop!)

Good luck.
- J.

---

### Post by vrode on 2006-02-05
[QUOTE=jrjbertram]I don't think you can.  You're already on 'internal' graphics because you're using the graphics chip on your motherboard.  'external' graphics means a video card that you plug in to a spare PCI or AGP slot.  Laptops don't usually have spares of either because they're built to be so small and compact.

You might try to find out what kind of hardware is on it.  If it's an intel-based motherboard, it seems like linux has lots of issues with recent intel hardware.  (intel doesn't play nice with open source developers).  One thing that you might try is to go into setup in your BIOS and disable some of your devices.  Start with the sound, if it'll let you shut it off.

Also, I think there's a separate area on this forum for laptop issues; re-posting your message there might get you some *real* help.  (I don't have a laptop!)

Good luck.
- J.[/QUOTE]

-------
I tried disbling everything possible option that I can think of within my BIOS w/ no avail. BTW, I don't have sound option in my BIOS.

I have posted help in laptop forum as well. Searching for "hotplug subsystem hang" brought me to this thread. Currently I'm trying to reach as many folks I can for help for my new alienware area51 m5700 laptop which is days old :(

regards,
/virendra

---

### Post by jrjbertram on 2006-02-05
Yeah, I had the same problem finding information.  I suspect that this is a common problem with booting up linux, but I'm no guru and can't really help beyond this... hopefully someone else will be able to pick up the thread.

Sorry,
- J.

---

### Post by jrjbertram on 2006-02-05
And if you do figure it out, be sure to post your solution here so others can benefit from it later without having to retrace our steps. :)

---

### Post by vrode on 2006-02-05
Thanks for trying.

What's interesting, when I boot into the system via recovery mode, hitting esc on the grub menu,

I see the cursor sitting on the following message,

snd-hda-intel: can't be laoded
missing kernel or user driver snd-hda-intel
shpchp: already loaded
uhci-hcd: already loaded
uhci-hcd: already loaded
uhci-hcd: already loaded
uhci-hcd: already loaded
<3>hw_random: RNG not detected
hw_random: can't be loaded
missing kernel or user mode driver hw_random

How can I fix this issue :(

I'm hoping someone from the development group is reading this message.


regards,
/virendra

---

### Post by 111787 on 2006-02-05
[http://www.ubuntuforums.org/showthread.php?t=103948&highlight=RNG]("http://www.ubuntuforums.org/showthread.php?t=103948&highlight=RNG")

A search of "RNG not loaded" yielded this.

---

### Post by vrode on 2006-02-07
Actually for me, when I chmod -x /etc/init.d/hotplug and rebooted, I was able to bypass the hotplug subsystem lockup.

I beileve intel-hda module is solved in alsa-1.0.9.


regards,
/virendra

---

