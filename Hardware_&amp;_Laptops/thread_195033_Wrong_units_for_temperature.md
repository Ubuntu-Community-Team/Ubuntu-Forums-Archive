---
title: "Wrong units for temperature"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by lil_rich on 2006-06-12
Hi All,

I know everyone is probably sick of the temperature problems, but I had an idea today and haven't seen it anywhere in the forums. If it's around, feel free to point me in the right direction :-)

I'm using ubuntu 6.06 on a compaq r3360us. It's one of the presarios with a P4 processor, which I'm starting to wish I'd never bothered with. The reason is the fecking acpi temperature readings causing it to shut down randomly. Usually I just turn off the acpi support, but after upgrading I was determined to fix whatever the problem is.

Here's the deal. When I booted this morning, I did an "acpi -V", and the temperature said it was 60 degrees C (140 F)!!! How is this possible? I only just booted the damn thing! But that got me to thinking, the temperature in the room is about 60 F, so is the kernel mis-interpreting the units of the temperature sensors? One thing that I thought could be going on is that I'm British, using an American laptop (in America). When I installed Ubuntu, I specified that I had a US keyboard, but the language is British English. Is it possible that when I said I was British, it tacked a "degrees C" onto whatever number the temperature sensor reads?

Is there anywhere in /etc that I can change this kind of thing?

Cheers,
Richard

---

### Post by nolongerlivecd on 2006-06-12
Hey, my hard disk runs at 60 sometimes...

---

### Post by lil_rich on 2006-06-12
Sorry, I should have made it clearer. When I booted it was at 60 Degrees C, which then increases to about 75 in about 15 mins. When I actually start to use the cpu, the temperature approaches 85 and shuts down.

Oh, and these are the cpu temps. Forgot to say that.

---

### Post by mrmitch on 2006-06-12
I have this same exaclt problem with my HP pavilion ze5185.  The OS also runs extremely slowly.  and i have a 2.4 p4 and 512 ram, there should be no reason for this.

---

### Post by Boelcke on 2006-06-13
Remember, the CPU has warmed up a bit by the time you get through the boot process and have your ubuntu desktop up.  Try rebooting, and then going into the BIOS and see what *that* says the temperature is.

I don't know squat about your particular laptop, but it is possible it's getting that hot.

---

