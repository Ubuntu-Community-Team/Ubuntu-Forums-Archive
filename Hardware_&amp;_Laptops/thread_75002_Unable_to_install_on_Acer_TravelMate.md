---
title: "Unable to install on Acer TravelMate"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by shufla on 2005-10-13
Hello,

I'm using laptop: Acer TravelMate 522TX

I've downloaded, md5sumed, burned, then checked CD. I'd like to install default version. I type Enter on boot prompt and installation stops while loading `ide-cd' module (86% of first hardware detection).

What could I do more, to analyze this problem?

Best Regards,
Luke

---

### Post by stevenaei on 2005-10-13
same thing for my Acer Travelmate 529TXV...

---

### Post by civilwarlord on 2005-10-13
Try something like this:  linux acpi=off noacpi (then press enter, instead of just pressing enter)

---

### Post by shufla on 2005-10-13
Hello,

Thanks! With "linux acpi=off noacpi" all runs fine.

But why sarge with linux26 has installed properly w/o such trick?

Best Regards,
Luke

---

### Post by stevenaei on 2005-10-13
worked!  thanks civilwarlord!  the only thing i had to change
is  'linux' to 'live' since i am trying out the live CD first... so,
live acpi=off noacpi

---

### Post by civilwarlord on 2005-10-13
[QUOTE=shufla]Hello,

Thanks! With "linux acpi=off noacpi" all runs fine.

But why sarge with linux26 has installed properly w/o such trick?

Best Regards,
Luke[/QUOTE]

Not sure, just be thankful your problem was easily fixed (knock wood).

---

### Post by shufla on 2005-10-13
Hello,

Well, I'll do bugreport on [http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/)
Huh. I'll do more test right now - just needed to start working with Breezy :)

Best Regards,
Luke

---

### Post by grinias on 2005-10-13
The installation & boot problems on single processor Acer machines are avoided by simply typing 

linux noapic 

since "apic" is useless for a single processor.

---

### Post by civilwarlord on 2005-10-13
[QUOTE=grinias]The installation & boot problems on single processor Acer machines are avoided by simply typing 

linux noapic 

since "apic" is useless for a single processor.[/QUOTE]


Maybe I meant to type apic, not sure, what's the difference acpi & apic?
Also, will what I told them to type in cause trouble for shufla & stevenaei later?

---

### Post by grinias on 2005-10-13
acpi provides essential laptop management; on the other hand apic is needed only for multi-processor machines, although i don't really know what it does to them :p

---

### Post by shufla on 2005-10-14
Hello,

[QUOTE=grinias]The installation & boot problems on single processor Acer machines are avoided by simply typing 

linux noapic 

since "apic" is useless for a single processor.[/QUOTE]

Well, that's funny, cos when I installed it, and now try to boot it only with "noapic", system hangs with such lines:

Uncompressing Linux... Ok, booting the kernel.
Loading, please wait...

Uhh. I waited for about 3 minutes, and 4 more lines are here:

irq15: nobody cared (try booting with "irqpoll" option.
handlers:
[<d48994a0>] (ide_intr+0x0/0xed [ide_core])
Disabling IRQ #15

And these lines are repeated after about 3 minutes...

I'll try "irqpoll" option...
And, YES! irqpoll is what is needed! :) Just irqpoll.

Best regards,
Luke

---

### Post by grinias on 2005-10-14
Hello again,

i 'd like to apologize since i tested the "noapic" option for installation and booting only on Acer TM 410? laptops. It works fine there, without any problems. But at least you found the solution.

See you

Elias

---

### Post by beercz on 2005-10-14
Hello

This thread may be of interest:

[http://ubuntuforums.org/showthread.php?t=75820]("http://ubuntuforums.org/showthread.php?t=75820")

It's more about the acpi issue on Acer laptops

Ian

---

### Post by zootm on 2005-10-14
For the record, I have a TravelMate (521TEV or something, it's not handy at present to check, sorry), and when I upgraded (through APT) to Breezy the kernel installed does not work without adding the "irqpoll" boot option. After this option is added, however, it works fine. Althought this was mentioned earlier in the thread, it might be preferable to turning off ACPI (to be honest, I don't even know what irqpoll *does*...) if it saves the same problem.

The Breezy install CD also freezed at the point mentioned, I never got the chance to try that with irqpoll though.

---

### Post by 5-HT on 2005-10-15
Also running an Acer TravelMate...

[QUOTE=civilwarlord]Try something like this: linux acpi=off noacpi (then press enter, instead of just pressing enter)[/QUOTE]

Thanks! I've been struggling with this all day.

[QUOTE=zootm]
when I upgraded (through APT) to Breezy the kernel installed does not work without adding the "irqpoll" boot option. After this option is added, however, it works fine. [/QUOTE]
Thanks, the irqpoll option lets me boot with the new kernel.

It works for me if I go into grub and append a "irqpoll" in the kernel boot pat...but don't know if that'll pose problems down the road).

---

### Post by bikeboy on 2005-10-19
The apci=off noacpi works for me too on a Travelmate 529ATX using the live cd.

Well done again to the ubuntuforums community, I always find solutions here :)

---

### Post by blondilox on 2005-12-10
ARGH!! Hello everyone, trying to install on the TravelMate, get most of the way thru after commanding linux acpi=off noapic nolapic now I have Killed Killed Killed Killed infinitely marching down the left hand side of my screen? Any thoughts?

thank you

B

---

### Post by kevinlw on 2006-02-15
Good day all,

I'm definitely a nooB here.  I have an old Acer 521DX, standard config with a 6GB HDD.  
1) I used a failed EDUBUNTU 5.10 ISO burn unknowingly and I think my bios loaded Dr DOS.  So I partitioned my HDD into 2GB for Windows and 4GB for linux and saved the settings into Dr. DOS.  

2) I rebooted and tried to install a good EDUBUNTU ISO burn.  However, the laptop failed to run, all I get is a blank screen; both HDD and CD-ROM runs simultaneously several times thens the whole thing hangs.

3) I will try flashing the BIOS againto see if this gets things running at least at the BIOS level.

Can anyone help?

Thanks a lot,
Kevinlw, Malaysia

---

### Post by beauty on 2006-02-21
[QUOTE=kevinlw]Good day all,

I'm definitely a nooB here.  I have an old Acer 521DX, standard config with a 6GB HDD.  
1) I used a failed EDUBUNTU 5.10 ISO burn unknowingly and I think my bios loaded Dr DOS.  So I partitioned my HDD into 2GB for Windows and 4GB for linux and saved the settings into Dr. DOS.  

2) I rebooted and tried to install a good EDUBUNTU ISO burn.  However, the laptop failed to run, all I get is a blank screen; both HDD and CD-ROM runs simultaneously several times thens the whole thing hangs.

3) I will try flashing the BIOS againto see if this gets things running at least at the BIOS level.

Can anyone help?

Thanks a lot,
Kevinlw, Malaysia[/QUOTE]
----------------------------
Travelmates have a notorious problem with both ACPI and APIC (they look similar, but are completely different).  I have a Travelmate 602TER and they only way I could get it to load UBUNTU was with this command:

   linux noapic nolapic acpi=off pci=noacpi

One thing I found on a German website but haven't tried is:  pnpbios=off

Good Luck!

---

### Post by TeoLinuX on 2007-07-24
Thanx a lot everybody. it worked with the "linux apci=off noacpi" boot command

My old (but still great) 522TX now is born to new life with xubuntu 7.10 tribe3

:popcorn:

---

