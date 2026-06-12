---
title: "Well, Im all out of options here gang."
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by phyerboss on 2007-06-15
For over 24+hrs I have been wrestling with trying to just get ANY linux distro to install onto my server after I upgraded it to a dualcore setup...

Specs: 
AMD 3800+ Athlon 64x2
Biostar NF61s Mobo
1gb DDR2 533mhz ram

Sound, LAN and vid are all onboard. Vid works fine but between Kubuntu, Ubuntu & PCLOS. Its 1 thing or several other issues. 1st off I know PCLOS is NOT a favorite here or supported. But I only bring it in as comparison to the issues I am having. I only wanted to make that all understood so there is'nt people chargin' at me with pitch forks.

Ok, with PCLOS2007(FINAL), the os fails to detect the LAN or sound. With U/Kubuntu, both will detect the LAN but apparently not the sound. But when I try to do a full install, the installation process crashes. Normally when selecting language or making it all the way to the Partition Manager and conking out there.

I brought this up to the PCLOS guys in their IRC chat and the most lousiest excuse I ever heard popped up. "Maybe your hardware is too new". C'mon guys, dont tell me its the same thing with Ubuntu as well?! This is ridiculous and I cannot RMA this stuff nor get win2000 to install on it! My intentions were to get away from windows and give linux a chance. But its blowing up in my face!  I have tried the 32 & 64bit versions of 7.10 & niether will install! All the bragging on "linux will work on anything" is falling to pieces here and I am tired and just want a decent answer! No more "read this" or "look this up". If you know the answer or someone who might, then please share that info.

Im just really tired and want my server back up. 

Thank you.

---

### Post by colo on 2007-06-16
I got a similar board to yours, I may be able to help in a few hours.

---

### Post by phyerboss on 2007-06-16
Thanks! Sent you a PM.

I just cannot understand what is going on here! Its like everything Linux I am trying to install is extremely unstable and keeps crashing on itself at the slightest move of the mouse. Win2000 was the only exception so that tells me the hardware should be fine. However, I do not have SP4 and so all the drivers(especially LAN) will not install in order for me to update to SP4...Quite a delima eh?^^

Heh, but seriously, I prefer using Linux and any help or ideas will be awesome as to why this wont work. Because the "its too new" excuse is not a viable answer to me.

---

### Post by phyerboss on 2007-06-16
My apologies...

I neglected to mention that the setup is also AM2(mobo, cpu, ram). Not sure how much help that could be but I forgot to mention it in the 1st post and I like to supply as much info as possible when I need help.

---

### Post by phyerboss on 2007-06-16
Hey, I hav'nt recieved any further corespondence from "colo" or anyone else on this matter. 

Therefore I am bumping this as there has been 70+ views but no answers as to what I might can do to get U/Kubuntu to install on my setup.

---

### Post by kerry_s on 2007-06-16
Have you tried the alternate install or the mini.iso net installer?

---

### Post by phyerboss on 2007-06-17
Alternate install? Aw man, no I hav'nt.

And what specificly is the mini net install?

---

### Post by kerry_s on 2007-06-17
alternate-> [http://mirrors.kernel.org/ubuntu-releases/feisty/ubuntu-7.04-alternate-i386.iso](http://mirrors.kernel.org/ubuntu-releases/feisty/ubuntu-7.04-alternate-i386.iso)

mini.iso net installer, you will need to be connected-> [http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

the mini.iso is like a boot disk, it boots your system then grabs and installs everything straight from the web. it can install any of the supported *ubuntu's. i would try that one first, it's a short download and you will have a fully up to date system when it's done installing.

Sound just usually needs to be turned up/unmuted after the install as some are muted in the mixer.

---

### Post by phyerboss on 2007-06-17
Alright, I'll try these. Not sure how i'll be able to use the mini net installer unless it can setup the lan on its own. Ubuntu seems to be the only distro detecting the lan. So, if I can just get it to install, It should be easy going from there. 

Thanks, I'll keep this thread updated with my results.

---

### Post by Wattos on 2007-06-17
alernate worked for my laptop when live failed. Make sre to make a memtest too

---

### Post by phyerboss on 2007-06-17
I got another question...

The mini ISO is but 8mb! Is'nt there a way I can get that to boot off of a pendrive as opposed to wasting up a CD?

---

### Post by phyerboss on 2007-06-18
Alright heres the update regarding using the alternate text-based installer.  It deffinately gets me farther that the GUI based installer but for some reason upon setting up my partitions it keeps rebooting the system as the others have! Most of my initial startups and reboots have been throwing out a a few error messages that pop up but dont stay long enough for me to jot down(half a second*). However this paticular 1 did come up and stayed in place:

1.720000]crc error
1.720000]Kernel panic-not syncing: VFS: Unable to mout root on unknown-block(104,1)

I did ran the mem test as advised. Not certain what to look for but it seems to check out alright but just keep looping back and starting over again. There was a another error I was getting about not detecting the ACPI. But that was due to me being advised to turn it off by the PCLOS guys. I enabled it again and that message went away. 

These reboots during setup are random(and frustrating*) but they commonly happen while setting up the partition. I am planning to try the mini install but before I waste another CD I want to know is there a way to set the files for it on my pendrive to boot it off there? Plus, if anyone has a clue regarding this text based installer conking out on the partitioning portion of the installation, PLEASE say something. I am 2 days past my time to get this machine back up.

---

### Post by IntuitiveNipple on 2007-06-18
Everything you've said makes me think you've got a hardware issue going on. 

You say this is a new motherboard and CPU? Did you mount the CPU and heat-sink yourself? Have you gone into the BIOS setup at boot-time and used the hardware monitor page to watch the temperature of the CPU to ensure it isn't running hot.

It would be typical that during periods of intense activity (such as whilst installing) the CPU will heat up. If the thermal coupling is bad it could be tripping over - I've seen this symptom countless times. It's quick and easy to clean off the thermal compound and re-apply.

If the CPU temperature seems fine then investigate the cables and disk-drive connections. The block errors make me strongly suspect the disk drive. If you've got a spare lying around try removing the current drive and installing on the spare as a test.

Also, if you have other PCI adapters that aren't essential to boot the system remove them and see if it helps to get past the installer - this would point to a faulty hardware issue.

---

### Post by phyerboss on 2007-06-21
Alrighty, 
after a bit more tinkering around I ran the mem test again but this time for just about the entire day.

TONS of memory address errors. So, after talking to a PC savy buddy of mine's it was determined that the ram I recieved was a dud. Unfortunately its too late to RMA it since its over 30 days I had it. sitting in its box. So, to my grief, I went on and dropped the old mobo & cpu back in and viola! everything loads fine.

But I just wanted to update this thread regarding this issue and state that its resolved. Thanks again to all of you that helped me and provided excellent advice.

---

