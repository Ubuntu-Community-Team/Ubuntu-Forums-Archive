---
title: "Alien Symbols or Busted Graphics Unit? - Stress test with log option"
date: 2011-12-16
forum: Hardware
---

### Post by somethis on 2011-12-16
Hello all, I'm new here and been using Ubuntu for about a year. Thank you in advance for suggestions and help.


My question:

1) From the description and the images below would you agree that the graphics unit is probably defect?  Or are they symbols from aliens projected onto my screen?

2) Is there a straightforward linux/ubuntu program to detect and log defects in the graphics unit?  Maybe a stresstest?


Background:
Bought a used laptop type IBM ThinkPad T60 from a refurbishing company.  As with my desktop computer, I kicked Windows off and installed Ubuntu 10.04.03 LTS Lucid on it.  I was a happy man.

Now, two days later it seems the graphics unit is busted.  When I boot the machine it often goes straight into a blue/black screen with red pixels at the top - the scary alien symbols (see images).

This happens every fifth attempt to boot the system.  Beforehand, nothing is displayed on the screen (no memtest, no blinking cursor etc.).  On the other hand, once the laptop makes it past booting I haven't experienced any problems with the graphics unit so far - it runs sweet as cake.


So, I've sent the laptop to the refurbishing company for fixing/replacement but they've simply returned it.  They've insisted that after rigorous testing (yeah right) no problems could be detected with it ...

I guess it's left to me to proove the potential defect to the company.  Your help is appreciated :)


Here are two screenshots of the "alien symbols"

[IMG]http://i180.photobucket.com/albums/x12/antill_photos/ubuntu/DSC03946.jpg[/IMG] 

[IMG]http://i180.photobucket.com/albums/x12/antill_photos/ubuntu/DSC03945.jpg[/IMG]

---

### Post by somethis on 2011-12-19
Dear forum,

was my question or the way it was articulated confusing?  Please let me know if anyone has a suggestion to solve the issue.

Thank you, some

---

### Post by tgalati4 on 2011-12-19
Thinkpads were (and perhaps still are) known for graphics chip problems.  The T40 series were especially troublesome.

A comprehensive test suite:

sudo apt-get install phoronix-test-suite

sudo apt-get install cpuburn

man cpuburn

Shortly after booting to the desktop, hit control-alt-F2.  That will get you to a text console.  Run burnP6 for a few minutes and see if the machine is still responsive.  Then hit control-alt-F7 to get back to the graphical desktop.

Keep the laptop in a cool area.  As the GPU heats up, it can delaminate from the motherboard causing the problems that you are experiencing.  Of course it could be aliens.  In that case, you better fabricate a tin foil hat.

---

### Post by somethis on 2011-12-25
> **tgalati4 said:**
> Shortly after booting to the desktop, hit control-alt-F2.  That will get you to a text console.  Run burnP6 for a few minutes and see if the machine is still responsive.  Then hit control-alt-F7 to get back to the graphical desktop.

Thank's tgalati4.  I ran the burnP6 test for a full hour and the laptop did remain responsive.  The ACPI thermal sensor went from 42°c to 68°c (= 107.6°f to 154°f) so the processors were loaded.  Nevertheless, no breakdown.

What a bummer since all I want to do is return the laptop to the refurbisher.

What do you think?  Either burnP6 doesn't put load on the gpu but only the cpu?  Or, maybe, the gpu is not even the cause for the red symbols as I originally thought or ...


... should the alien theory actually hold TRUE ?!?

---

### Post by somethis on 2011-12-26
I just came up with another idea:  is there a logfile that tracks when the gpu fails in the manner described?

Then I could just return the laptop with a printout of the logfile.

---

