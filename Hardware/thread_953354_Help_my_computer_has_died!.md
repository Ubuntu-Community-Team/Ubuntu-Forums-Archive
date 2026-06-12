---
title: "Help my computer has died!"
date: 2008-10-20
forum: Hardware
---

### Post by karamu on 2008-10-20
I don't think this is strictly an Ubuntu issue- it seems to be hardware but I am running Ubuntu and I've been impressed by the expertise in these forums before.

My desktop has PCI sound and video cards situated next to each other- from time to over the past couple of months my screen has gone black when the computer has been running- this often happened when I was changing the speaker/ headphone output output so I thought I must have been knocking the cards or something. A long press of the power button and a restart always fixed the problem. However last week it happened from boot- the machine powered on but there was no signal to the monitor. I tried several times and always the same thing.

So, I opened the case and took the cards out, cleaned them and the slots with air, popped them back in and tried to boot- this time the monitor had a signal but the splashscreen (where you can enter the BIOS) came up..... and stayed up- it sat on this screen and did not boot at all.

I went into the BIOS and checked the settings- all normal. I then tried to boot from a live CD- same thing, the computer just stays on the initial screen and does not boot (the CD spins up).

I am at a loss what to try to resolve this issue- the machine just refuses to boot. The only thing I have done is remove and replace the PCI cards- I haven't made any other hardware changes.

Any suggestions what to try would be most gratefully received!

---

### Post by Kevbert on 2008-10-20
Have you tried cleaning around the memory chips and tried refitting them ?
What's the bios chipset ?  Do you get an audio beep when you switch on ? Are there a row of LEDs on the motherboard and what is lit up when you turn on and the PC freezes ?  What system hardware do you have (including power supply rating) ?

---

### Post by felker2 on 2008-10-20
First check: memory.

Thus run memtest86 from the Ubuntu cd or from your harddisk: memtest86 is in the boot option menu.

Let it run for a few hours and see what memtest86 reports.

I've had system lockups, and after running memtest86 it was clear one of the two memory DIMMs was defect. After removing that DIMM my system was stable again.

---

### Post by Kevbert on 2008-10-20
> **felker2 said:**
> First check: memory.

Thus run memtest86 from the Ubuntu cd or from your harddisk: memtest86 is in the boot option menu.

Let it run for a few hours and see what memtest86 reports.

I've had system lockups, and after running memtest86 it was clear one of the two memory DIMMs was defect. After removing that DIMM my system was stable again.

Agreed, but I don't think the PC is booting that far.

---

### Post by felker2 on 2008-10-20
> **Kevbert said:**
> Agreed, but I don't think the PC is booting that far.

Ah ... on re-reading the OP's message, I see it's the *BIOS* splash screen that halts (not the Ubuntu splash) ...

Then I would remove as much hardware as possible (PCI cards, all drives, etc), set the BIOS to default / save settings, and start from there.

And, OP: check that the fan of your CPU is working; if not the CPU can become too hot and halt in seconds.

The power supply can be problem too... which is a nasty problem to locate ... :-(

---

### Post by karamu on 2008-10-20
No, the computer doesn't even get past the initial splashscreen- it doesn't boot so I can't run anything like memtest.

I trIed taking the mem sticks out and cleaning around the sockets.

No- I didn't get any beeps before and no I can't see any LEDs on the motherboard.

But now it beeps four times when I switch it on- I currently don't have any PCI cards in the slots.

Not too sure about the BIOS chipset but the specs are:

Celeron 1.8 ghz, 1 gig RAM, Geforce FX 5200 128mb video card (PCI type) 150W power supply.

---

### Post by karamu on 2008-10-20
Yes, the fan is working fine.

Update- if I switch on with the video card in the slot it was previously inhabiting, no beeps. Switch on with no cards in place, four beeps.

The machine had been working fine (apart from the occasional monitor signal problem I mentioned at the start of the thread) for about a year and a half in it's current setup with the video card if that means anything.

---

### Post by Kevbert on 2008-10-20
Sounds promising. PSU is quite a low rating. If you have a floppy drive and a boot floppy (DOS is fine), try disconnecting any hard disks and CD drives and try to boot the machine from floppy. The only things you want to have connected externally are the monitor, keyboard and mouse.

---

### Post by Kevbert on 2008-10-20
It may be worth checking the CMOS battery has not come loose and the jumper for it is OK. This is a small button cell close to the bios chip and is normally marked CR2032 or something similar. If you've been loosing time, the time and date has been wrong when you've booted the PC, The battery may need replacing. The jumper setting info should be in your PC manual.

---

### Post by karamu on 2008-10-20
OK, I'll check the battery and let you know- the machine is quite old so I guess that could have died.

It's getting kinda late here so I'm gonna call it a night- I have the day off tomorrow so I'll play around with the machine and see if I can get anywhere.

Thanks for the support, appreciated.

---

### Post by karamu on 2008-10-20
Sorry, forgot to say that there is no floppy drive- my boot options are only CD or HDD- or I guess I could connect the USB CD drive. Will experiment in the morning.

---

### Post by Sef on 2008-10-20
>  But now it beeps four times when I switch it on- I currently don't have any PCI cards in the slots.

Who makes your BIOS?  The sound could indicate what the problem is.

---

