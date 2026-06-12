---
title: "Lethal power-saving mode?"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by Cheizzz on 2007-02-05
As a happy ubuntu user since the hoary release, I haven't encounterd any problems that i could not solve. reading some error messages and reading these great forums would mostly give me the key to solving those problems. 

But this time, i do not know where to begin.
The situation: Since i first saw the "Power-saving" and "hibernation" buttons in the "log off / lock screen / reboot / shut down" menu, I've been curious about what they would do. hibernation seemed logical, just saving the session to the harddisk so it would be loaded the moment I would log on again. But "power-saving" button intrigued me. what would it do? could this be a low-power, low-noise kind of mode with i could turn on so i can actually sleep while my pc is downloading torrents at night, like a laptop? (this is about a desktop PC, not a notebook/laptop)

Yesterday evening i could not hold my curiousity any longer: I decided to bluntly click it. what  could go wrong? this is ubuntu, if it goes wrong i can easily get it right again by modifying some config files, no? 

After the now infamous click, ubuntu seemed to shut down really fast, without the nice shut down graphic. But i didn't see that as a problem, because i wasn't  shutting down, but going to "power-saving" mode, whatever it is.

and then: silence. a little too silent for me: i could not see any difference with the computer just being off / shut down. no lights, no vents, nothing. I slightly paniced. what did i do? 
I remembered the tooltip: i could go back to the normal session by pressing a button on my keyboard (which one then?) or pressing the power-button. 
As none of the pressed keys seemed to sort any effect i pressed the power button.

for a moment all was well: I could hear the vents again, the leds went on and the cdrom drive started purring. But that was it. No picture on my monitor, no hard-drive activity and,  what frightened me most of all: no sound of the ever reliable system speaker, which has already told my innumerable times what was wrong with my computer.

And here i am now: my computer doesnt even want to run the selfcheck and boot the bios, and i cant turn it off except for the dirty way (holding the power-button for 5 seconds)

Im truly puzzled and haven't got the any clue how to fix it. heck, i dont even know what the problem is! I've posted this under hardware because i think its a problem in my hardware, but then again, this occured by doing something in Ubuntu...

Please help me out of this mess. this system is very important to me as it is my computer which i use to get my work done: it's absolutly mission critical for my schoolwork!

and since the first reply will be about the specs of my PC:
Mainboard: Asrock 939dual-sata2
Proc:    AMD athlon 64 3000+
Graphic card: Gigabyte 7600 GS 
memory: 2x twinmos 256mb
harddrive: maxtor diamondback 10 160GB

software:
Ubuntu edy eft, using the generic kernel


Please, help me out!

---

### Post by ianpeters on 2007-02-05
Have you physically unplugged the PC? Sometimes the ACPI/APM can get screwed up but will reset if you disconnect it from power. If that didn't work, check your mobo manual how to clear the CMOS and try again.
As a last resort, unplug all devices, PCI-cards and such and then insert stuff back to see if anything happens.

Good luck!

---

### Post by Cheizzz on 2007-02-05
I've disconected the power and have also reset the bios. no luck though. 
What does this "power-saving" mode do exactly? maybe if i understand it better, i will be able to find the solution

---

### Post by Xenogis on 2007-02-05
Power-saving mode = Standby in windows
It keeps the ram powered and shuts everything else down so that when you hit the power button your computer is instantly back on.

---

