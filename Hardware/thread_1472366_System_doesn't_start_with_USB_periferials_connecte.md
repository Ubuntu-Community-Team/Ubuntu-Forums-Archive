---
title: "System doesn't start with USB periferials connected"
date: 2010-05-04
forum: Hardware
---

### Post by leoh on 2010-05-04
I have an HP (dv2600) laptop which has a strange hardware problem.
It has a few USB periferials connected to it: an USB hub (not powered) with 3 other periferials (USB mouse, USB to PS/2 - with a keyboard, and a USB Bluetooth adaptor), and an HP scanner.
What happens about 1/3 of the times is that when I turn it on, nothing happens (the system "turns on", LEDs and fan, etc) but it doesn't show BIOS screen (nor does it boot or the HD LED blink).
I have the latest BIOS installed.

I called HP support and the guy told me this is normal **on laptops** (!!!:confused:) and the normal procedure is to disconnect everything before turning it back on. He insists it is not a hardware or BIOS issue.

I confirmed it doesn't happen when the laptop has no periferials connected to it. Only when it has those USB periferials.

Is this correct?! What can I do about it?

---

### Post by Manyette on 2010-05-04
No help here, except to say that it is true for me also.  I thought that if the USB thumbdrive had no boot sector, it shouldn't be noticed, but apparently it is, and I do believe it is a BIOS issue.

---

### Post by leoh on 2010-05-04
> **Manyette said:**
> No help here, except to say that it is true for me also.  I thought that if the USB thumbdrive had no boot sector, it shouldn't be noticed, but apparently it is, and I do believe it is a BIOS issue.
The problem I am describing is way before booting. I don't even get the POST (HP logo, memory test, etc). If it was something related to the boot sector of any device, it should at least do the POST and give an error of "no boot found" or something.

---

### Post by Manyette on 2010-05-04
I agree absolutely, and that is why I believe it to be a BIOS problem.  I spent many years writing BIOS code, and that thumb drive should be ignored, and the boot process should continue, but it does not.  In my case, I have an HP machine with an "unknown", or little known company who wrote the BIOS for HP, and even their own techs admit it is "not much of a BIOS".  But if it was BIOS written by Phoenix or one of the other "mainstream" companies, I don't believe this would happen,  Perhaps someone can confirm my suspicion.

---

### Post by garvinrick4 on 2010-05-04
> **leoh said:**
> I have an HP (dv2600) laptop which has a strange hardware problem.
It has a few USB periferials connected to it: an USB hub (not powered) with 3 other periferials (USB mouse, USB to PS/2 - with a keyboard, and a USB Bluetooth adaptor), and an HP scanner.
What happens about 1/3 of the times is that when I turn it on, nothing happens (the system "turns on", LEDs and fan, etc) but it doesn't show BIOS screen (nor does it boot or the HD LED blink).
I have the latest BIOS installed.

I called HP support and the guy told me this is normal **on laptops** (!!!:confused:) and the normal procedure is to disconnect everything before turning it back on. He insists it is not a hardware or BIOS issue.

I confirmed it doesn't happen when the laptop has no periferials connected to it. Only when it has those USB periferials.

Is this correct?! What can I do about it?Do you have USB to boot before HD in BIOS settings and it looks for something to boot off of in a USB port?
 I do and I have a couple of items that seem to screw around with my booting when attached at boot. I suggest find which one and deal with it. I like to boot Live usb's verses CD's so I go CD, USB and Hd in by boot order. Of course if you change order and go CD, HD, USB then it will not happen.

---

### Post by Manyette on 2010-05-04
In reference to my previous post, I just tried the same test on another laptop with a Phoenix BIOS, and it boots just fine with the USB drive in place.  I think that confirms my suspicion.

---

### Post by garvinrick4 on 2010-05-04
> **Manyette said:**
> In reference to my previous post, I just tried the same test on another laptop with a Phoenix BIOS, and it boots just fine with the USB drive in place.  I think that confirms my suspicion.Are they both set-up in boot order the same in BIOS?

---

### Post by Manyette on 2010-05-04
Hi All,
Well, color me frustrated.  I had a long chat (unproductive) with HP's tech support, since they "don't support Linux", but here is what I have learned so far.  There does exist a much later BIOS that the one on my G71-340US machine (F.14), but how to load it becomes a problem since their utility only runs under Windoze, which I haven't had loaded for a long time now.  And, there is no guarantee that it will fix the problem, since the tech support type I talked to seemed totally unaware of the problem.  But if someone does have a Windoze partition, you might dowload the latest BIOS from the HP support website, and see if it fixes the problem.  To be honest, I have my doubts, but I have no way of finding out at this time, and I'm sure not going to load Windoze for what to me is a minor problem anyway.  I just learned not to boot with a flash drive installed.  Some of you may have a more irritation setup.  Anyway, at this point, there's not much more I can do, but I hope this info might help someone else.

---

### Post by Manyette on 2010-05-04
Hi garvinrick4,
I guess you don't have an HP machine with an early BIOS.  But this old one has only two options for boot order:  Hard Drive or DVD Drive.  The USB's are always enabled, since if a bootable USB stick is present, it will boot DOS.  (Probably at least a part of the BIOS problem)  The other machine, as I mentioned, has a Phoenix BIOS, and has that option.  No question this is a BIOS problem.

---

### Post by garvinrick4 on 2010-05-04
> **Manyette said:**
> Hi garvinrick4,
I guess you don't have an HP machine with an early BIOS.  But this old one has only two options for boot order:  Hard Drive or DVD Drive.  The USB's are always enabled, since if a bootable USB stick is present, it will boot DOS.  (Probably at least a part of the BIOS problem)  The other machine, as I mentioned, has a Phoenix BIOS, and has that option.  No question this is a BIOS problem.
I am on a laptop now G71-34OUS 17.3 inch and I can boot with my internal HD with USB external HD installed but never a
Flash drive after I screw around with them making Live USB's and then reformat them for something else. Right out of the box the flash drives can be in a port and works fine. As long as my CD and USB boots before my HD I am fine with HP. It is annoying when I forget to pull one out and have to reboot to get to the grub screen. It is a flaw though you are right, by me or them I do not know but now leaning towards them after your tech support call. Always like to lean towards someone other than me anyway.

---

### Post by Manyette on 2010-05-04
Hi garvinrick4, well that confirms what I suspected.  But I also think that you might have a somewhat later BIOS than I do.  As I said, mine is F.14, which just from the numbering must be very early, since they are now up to 2.xx something.  Sure, I'd like to have an update, but it has caused me no other problems, so I suppose I can (and have to) live with it.  But if you have a Windoze partition, you probably could update yours, assuming you need it.  Anyway, thanks for the info.

---

