---
title: "I can suspend one way but not another."
date: 2009-11-29
forum: Hardware
---

### Post by Windows Nerd on 2009-11-29
Hey guys,

I recently convinced my dad to install Ubuntu on his ageing laptop which was running as slow as a snail on XP. He wants me to configure it so everything is working fine. All he needs to to with the laptop is use OpenOffice and Firefox. His wireless worked out of the box (I cheered aloud when it did because that can be a bitch to configure), and I have installed all the extra programs he needs. The only thing remaining was to fix suspend (he has no use for hibernate really with the fast boot times) which of course did not work out of the box. I tried suspending from the menu on the task-bar, the screen went blank with the blinking underscore in the upper left corner, with the laptop still running full power. I could not do anything except give it a cold reboot (which I HATE having to do). So I did some googling and tried installing uswsusp, and then doing a suspend from the menu, with no avail. Then (after a reboot) I tried running:

```
sudo s2ram -f
```And bingo! It suspends. So problem fixed right?

Not. It can suspend, though my dad wants the ease of use to just use the taskbar method, not type 3 words into the terminal. Which is funny, because he is fine with using command line in Windows (he loves Powershell, and grew up using computers in the days of DOS). 

Is there anyway to change the Suspend option on the taskbar to run the command that works rather than the sleep script it runs by default, which doesn't?

Thanks, Scott.

PS: I would post the Sleep logs here but I can't seem to find my USB key to transfer them over from my dad's laptop. If you wish to see them, wait a couple days, because I think my Mom borrowed it to bring some files for her business trip.

---

### Post by Windows Nerd on 2009-12-03
Bump

---

### Post by jako on 2009-12-04
I suggest you follow this carefully:

[http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)

especially the beginning which shows you ways of determining if you need to bother with S2ram at all. I've managed with my Compaq NC8430 by putting 'acpi_sleep=s3_bios,s3_mode' on the grub command line.

---

### Post by Windows Nerd on 2009-12-05
> **jako said:**
> I suggest you follow this carefully:

[http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)

especially the beginning which shows you ways of determining if you need to bother with S2ram at all. I've managed with my Compaq NC8430 by putting 'acpi_sleep=s3_bios,s3_mode' on the grub command line.
For some odd reason the link you supplied me ends up displaying in Spanish, even if I google it, it *still* comes out in Spanish. Some help?

Also, where do I add acpi_sleep=s3_,s3_mode in the "grub command line". Do you mean grub/menu.lst? 

Scott

---

