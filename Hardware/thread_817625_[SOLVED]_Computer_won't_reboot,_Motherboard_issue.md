---
title: "[SOLVED] Computer won't reboot, Motherboard issue?"
date: 2008-06-03
forum: Hardware
---

### Post by Cappy on 2008-06-03
My computer won't [POST]("http://en.wikipedia.org/wiki/Power-on_self-test").

The computer was running fine but I turned it off and a few minutes later I turned it back on but it wouldn't POST. No screen output, no beeps, etc.

The LEDs indicated "Memory Error".

I reset the CMOS using the CMOS jumper (I did it correctly).

Now, the computer has long beeps which means "No DRAM Detected or Installed" and the LEDs still indicate "Memory Error".

I've tried some spair (new) DDR2 memory I had and some DD2 memory from another computer with no results.

I've tried all available slots with single sticks.

This seems like a Motherboard issue. Unfortunately, my Motherboard is out of warranty so I will have to buy a new one just to test that theory.

Has anyone seen any problems like this where the computer runs fine but once shut off it displays errors on POST?

---

### Post by Sam Lars on 2008-06-03
Have you tried cleaning the memory slots and the memory *really well*, with compressed air or a good vacuum cleaner?  That's a definite number one culprit for problems like this.

---

### Post by new2linux2008 on 2008-06-03
bummer, sounds like that mobo is gone man...

---

### Post by Sef on 2008-06-04
Have you tried to boot with a Live CD?

---

### Post by Cappy on 2008-06-04
> **Sam Lars said:**
> Have you tried cleaning the memory slots and the memory *really well*, with compressed air or a good vacuum cleaner?  That's a definite number one culprit for problems like this.

Thanks for the suggestion but still no go. 

I cleaned the memory with alcohol and I blew the memory slots with compressed air.

I also note that the "teeth" of the memory slots and memory are fully intact.
> **new2linux2008 said:**
> bummer, sounds like that mobo is gone man...

Maybe =(

> **Sef said:**
> Have you tried to boot with a Live CD?

The system is not POSTing ^_^ I changed my original post to say this instead of "not booting".

---

### Post by Cappy on 2008-06-06
I replaced the motherboard and now everything is working =)

This ASUS M3A-H is really sweet too. Its ACPI works with Linux and it also has linux embedded in the motherboard! 
**Edit: The M3A-H has a clock drift of 4 minutes a day. There is a fix here: [http://ubuntuforums.org/showthread.php?t=835288](http://ubuntuforums.org/showthread.php?t=835288)**

[http://www.asus.com/products.aspx?l1=3&l2=149&l3=639&l4=0&model=2129&modelmenu=1](http://www.asus.com/products.aspx?l1=3&l2=149&l3=639&l4=0&model=2129&modelmenu=1)

I wish this board was out a year ago.

---

