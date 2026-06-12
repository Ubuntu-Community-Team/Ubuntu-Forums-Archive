---
title: "Success story: Lubuntu with ACPI on old laptop"
date: 2012-07-22
forum: Hardware
---

### Post by Henry E on 2012-07-22
Hi, I haven't posted yet, but I've read a lot of threads here that helped me to solve my problem. To "give back", I want to write about the problem and the solution.

I wanted to put Ubuntu LTS on my old laptop, an Acer TravelMate 292LMi.
But there was a problem, the processor lacks a feature ("pae"), so the current Ubuntu wouldn't work.

Then I found that Xubuntu and Lubuntu should be working. I chose Lubuntu 12.04. 
But again a problem: It did not boot, I got the message "Fixing recursive fault but reboot is needed.." With the help of this forum, I found that the culprit was ACPI. So I edited the linux line in grub and put "acpi=off" there. Finally, I was able to boot Lubuntu!

But turning ACPI completely off is quite harsh. Lots of threads have tips on which kernel parameter to try instead. With a lot of trial and error, I still could not find an option that worked apart from acpi=off. 

Then, I found this post [http://ubuntuforums.org/showpost.php?p=11476988&postcount=7](http://ubuntuforums.org/showpost.php?p=11476988&postcount=7) in which matt_symes pointed to this page: [http://www.lesswatts.org/projects/acpi/debug.php](http://www.lesswatts.org/projects/acpi/debug.php)

Also, Daniel Richter from Grub Customizer told me how to make my own grub menu entries that differ only in the kernel parameters. I made a number of copies of the default menu, and tried the arguments from LessWatts in that order:

acpi=off 
(was my working default)

acpi=ht 
pci=noacpi 
acpi=noirq 
pnpacpi=off
noapic 
nolapic

then I had some arguments that worked for others in the forums, and combinations of arguments:
acpi_os=Windows
acpi_os=Linux
acpi_os=Windows noapic
noapic nolapic
acpi=force lapic

So now I could try one after the other, and did not have to edit the default line every time.
And I got lucky -- the 4th argument worked for me! pnpacpi=off does the trick: Lubuntu boots, and I can see the battery status, and the laptop doesn't run at full power all the time.

I hope that this summary might help someone with a similar problem. Trying the possible arguments in that order seems to be a very sensible thing.

---

### Post by amjjawad on 2012-07-25
Thank you for choosing and using Lubuntu :)

---

