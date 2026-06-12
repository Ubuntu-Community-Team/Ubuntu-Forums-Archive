---
title: "Error while trying to install and boot |   acpi=force"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by -oXo- on 2009-03-10
Hi, I have been looking around all evening looking for a possible fix for this and i'm stumped. So i'll try to explain whats happening and hopefully someone can help.

I just wiped XP from a machine with the intention of a full install of ubuntu 8.10 while at the point of inserting my CD I have a couple of problems.

One is if I try to run the distro as a live cd it sits on the splash screen for ages then screen turns black and a underscore just sits there flashing constantly doing nothing.

Then if I try to run the installer I get this flash up on the screen and it just hangs on the splash screen.

```
[ 0.000000] ACPI: BIOS age (1999) fails cutoff(2000), acpi=force is required to enable ACPI
```

Please post anything you might think will help and i'll answer every question as best as possible.

Thanks
oXo

---

### Post by Partyboi2 on 2009-03-12
Try doing what it suggests. When you are at the main menu of the live cd press F6 and at the end of the line add[FONT=monospace] [/FONT]```
acpi=force
``` then press enter.

---

### Post by BiggoCharley on 2009-03-12
I am having the same problem --except I am trying to run the live 8.04.2 Hardy cd.  The machine is an IBM Thinkpad 600x.  (I have had ubuntu dapper running very well on this machine in the past.)  I tried the "acpi=force" command with the same results you describe above. Oddly, one thing different happened with the acpi=frce command -- I was unable to turn the machine off --In order to get out I had to disconnect he power and remove the battery.  This didn't happen without the acpi=force command. 

I have been searching the forum for days and this is the first time I have seen this problem -- I hope someone has the answer.

---

### Post by Partyboi2 on 2009-03-12
Have you tried to update your bios?

---

### Post by BiggoCharley on 2009-03-12
Just now finished updating bios to the latest version from IBM's site. No change --thanks for the suggestion.

Incidentally also tried dabbling with the bios boot options --quick boot vs normal boot.  
Also tried "smart boot manager" and selected cdrom as the boot disk --again no change.

I'll continue to dabble --maybe I'll get lucky. :P

---

### Post by Partyboi2 on 2009-03-12
Have you tried turning acpi off, you can try this by adding
```
 acpi=off
``` as a boot option.

Edit: Looking at the default specs for the ibm thinkpad 600x and how low they are I would suggest trying [[COLOR=Blue]darn small linux[/COLOR]]("http://damnsmalllinux.org/") (dsl)

---

### Post by BiggoCharley on 2009-03-13
> **Partyboi2 said:**
> Have you tried turning acpi off, you can try this by adding
```
 acpi=off
``` as a boot option.

Edit: Looking at the default specs for the ibm thinkpad 600x and how low they are I would suggest trying [[COLOR=Blue]darn small linux[/COLOR]]("http://damnsmalllinux.org/") (dsl)

I tried turning acpi off with the same results as before.

I'll consider dsl --thanks for the suggestion.

---

### Post by BiggoCharley on 2009-03-16
Got it solved.  Here is what i did --I'm sure that this is specific to my machine-- IBM Thinkpad 600X.  I installed using the alternate cd "ubuntu-8.04.2-alternate-i386.iso" burned at 4x to a Philips 700 mb cd-r.

First I cleaned the hard drive thoroughly with dban which erased everything.  Then I booted the install cd with this parameter "generic.all_generic_ide=1".  (I arrived at this through trial and error --its not like I knew what I was doing.)  
Went through the install without a hitch.

It seems that i hijacked this thread form the original poster "oXo" --I apologize for that. and thanks to Partyboi2 for all the help.

---

