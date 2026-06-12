---
title: "Kodak Printer Inoperative After Ink Change"
date: 2012-06-27
forum: Hardware
---

### Post by E.T.Smith on 2012-06-27
The hardware is: Kodak ESP 9250
The version is: Ubuntu 10.04, Lucid Lynx

I dealt with an annoying low-ink beep on my kodak printer by simply turning it off, for about a month. After finally getting around to replacing the ink and turning it back on, the thing can't print. Note that it was able to do so before (barring some hiccups with pdf's).

The Document Print Status indicates a "Printer configuration error." When following the prompts in the Printing Troubleshooting frame the following error message is repeated several times:

> Printer 'KODAK-ESP-9200-Series-Aio' requires the '/usr/lib/cups/filter/command2esp' program but it is not currently installed.

Clicking prompts doesn't seem to change anything, the test-page won't print and I get a very long error log before the Troubleshooter gives up. I've looked for "command2esp" in synaptic, to no avail.

First, how do I fix this? I have a big project coming up soon I need plenty of hardcopy for.
Second, any ideas what caused this? Did leaving the printer off let it be "forgotten" somehow?

---

### Post by E.T.Smith on 2012-06-28
So ... Is the solution that obvious, or is the problem that bad?

---

### Post by coffeecat on 2012-06-28
The reason why your post hasn't been answered yet is probably more to do with the fact that few members will have experience of a Kodak printer, mainly because of Kodak's seeming indifferent reputation for Linux support.

This bug report concerns a different Kodak printer and different version of Ubuntu from which you are using, but the problem appears to be the same and the comment in the second post might be worth looking into.

[https://bugs.launchpad.net/c2esp/+bug/816160](https://bugs.launchpad.net/c2esp/+bug/816160)

---

### Post by E.T.Smith on 2012-06-28
For the moment, looks like I was able to solve the matter myself with some more searching. After downloading installing [cups driver]("http://cupsdriverkodak.sourceforge.net/") it looks like I at least have b&w printing capability. I'll see how color goes shortly.

Still leaves open the question of how the driver got uninstalled in the first place.

---

### Post by |{urse on 2012-06-28
You could try gently cleaning the contacts for the color ink cartridge, sometimes a buildup of dry ink occurs when the unit has sat for a long period. I usually use a q-tip with a [SIZE="3"]SMALL[/SIZE] amount of isopropyl (rubbing) alcohol.

---

### Post by paulnewall on 2012-06-28
command2esp is a cups command filter that allows you to check the ink level, start the printer's internal test page etc from your pc.

command2esp should get installed with the c2esp package

I've got no ideas why it should have seemed to disappear.

Once I delayed replacing an ink cartridge and then found that the print head seemed to be blocked, after a lot of trying to unblock it, I eventually gave up and replaced the print head which was a bit expensive. 
So, just in case the print head failure was caused by the ink drying out, I will be replacing cartridges promptly in future. I am also trying to do some colour printing at least once a week to avoid leaving ink in the head for a long time.
Maybe this is all unnecessary, but a little more ink and paper is a lot cheaper than a new head.

---

### Post by E.T.Smith on 2012-06-29
Some eerily prescient posts above. After printing a few pages, the black ink stopped working. Color was operable, but no grey-scale. I assumed, like **|{urse** suggested, the cartridge had dried or otherwise jammed over the interim and replaced it with a new one. But after a few successful jobs, the black ran dry again. Ridiculously, I can get it to print again by taking the cartridge out and shaking it a bit (until the contact sponge is moist) then reinserting it, but as that has to be done every couple pages, its not exactly practical.

Of course, this is now clearly a hardware problem, not software.

---

### Post by kurt18947 on 2012-06-29
> **E.T.Smith said:**
> Some eerily prescient posts above. After printing a few pages, the black ink stopped working. Color was operable, but no grey-scale. I assumed, like **|{urse** suggested, the cartridge had dried or otherwise jammed over the interim and replaced it with a new one. But after a few successful jobs, the black ran dry again. Ridiculously, I can get it to print again by taking the cartridge out and shaking it a bit (until the contact sponge is moist) then reinserting it, but as that has to be done every couple pages, its not exactly practical.

Of course, this is now clearly a hardware problem, not software.

It's problems like this that make it worthwhile to have a small Windows install. You probably have a hardware issue, not an O.S. issue but if you're doing trouble shooting with Kodak, they are NOT gonna want to hear what the printer is doing under Linux.  Linux will most likely be presumed to be the problem, even if it's not.  Nobody said life was fair and it's human nature to blame the "I've never heard of it/used it/we don't support it so it's the source of all your problems" device.

---

### Post by paulnewall on 2012-06-30
Hmmm, Now you have the question: Is the current problem due to the printer or the new cartridge. I think that ink cartridges usually have an air inlet, so that air can get in to replace the ink that is used. To stop the cartridge drying up, the air inlet might be a long narrow channel. If the air inlet was blocked, I'd imagine you would get the symptoms you described: ie you can print a few pages, then the reduced pressure in the cartridge stops any more ink from coming out.
 
If the shaking is required to get the printing to work, and just removing and replacing the cartridge does not help, I would blame the cartridge. It's possible that another new cartridge will fix the problem (I'd buy it from a different shop, so you get a cartridge from a different manufacturing batch)

---

