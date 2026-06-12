---
title: "Memory issues + Linux motherboard updates"
date: 2014-09-10
forum: Hardware
---

### Post by bluesoviet on 2014-09-10
Long story short... my Ubuntu OS freezes up and crashes at times and claims that it can't access my systems memory at a specific address(but recovers and works fine there after). I am certain that this is because i don't have the Linux motherboard update that my computers manufacturer has provided. However before updating. i need to know if updating my BIOS with such an update would in anyway prevent me from booting into Windows 7 as from what i can tell... the update is meant for Linux specific OS's only.

My computer is an Acer Aspire M3970G

Picture of the motherboard updates that i'm talking about:
[IMG]http://i.gyazo.com/c44ce2092e2b16153088e13265a83888.png[/IMG]

Any help would be appreciated!

---

### Post by weatherman2 on 2014-09-11
Most computers don't have a separate BIOS for Linux.  I have never seen one myself.  In fact, had I not seen your example, I would not have believed it.

Why does Acer provide a separate BIOS for Linux for your model?  I'm not sure.  It may be for a marketing reason, not a technical reason.  It's possible they sell this computer with Linux at a lower price than the Windows version and that you can't install Windows on the Linux version.  I do know that for my Acer netbook, Acer has separate BIOS version chains for Windows 7 and Windows 8, perhaps for a similar reason.

But I highly doubt the problems you are having have anything to do with having the "wrong BIOS."  Linux should run just fine on a Windows PC with either BIOS.

I'd check the RAM (run Memtest from any Linux/Ubuntu boot disk) and the hard drive for starters.

---

### Post by weatherman2 on 2014-09-11
But to answer your question: it's quite possible that updating the BIOS to the Linux version would prevent Windows 7 from booting.  It's also possible you wouldn't be able to install the Linux version even you tried, because it detected you have the Windows BIOS.  Even so, the kind of errors you describe would make me reluctant to try updating the BIOS at all, because if there is some hardware problem, your BIOS flash could get corrupted or interrupted in the middle, and that could be very dangerous.  You could very well "brick" the computer and make it unbootable with any operating system.

---

### Post by grahammechanical on 2014-09-11
What is the underlying difference between Windows 7 and Windows 8? The secure boot requirement. Windows 8 machines require a boot loader to be signed with a digital key. This could be the reason why there are different versions of the BIOS/UEFI file.

Windows 8 will install on a machine that has a UEFI or BIOS that does not have the secure boot requirement or it would be impossible to upgrade windows 7 to Windows 8 . Ubuntu will install on machines that do not have secure boot or that do have secure boot.

But I agree with the advice from weatherman2, Look for another reason for this problem. Look for another solution.

Regards.

---

### Post by bluesoviet on 2014-09-11
> **weatherman2 said:**
> Most computers don't have a separate BIOS for Linux.  I have never seen one myself.  In fact, had I not seen your example, I would not have believed it.

Why does Acer provide a separate BIOS for Linux for your model?  I'm not sure.  It may be for a marketing reason, not a technical reason.  It's possible they sell this computer with Linux at a lower price than the Windows version and that you can't install Windows on the Linux version.  I do know that for my Acer netbook, Acer has separate BIOS version chains for Windows 7 and Windows 8, perhaps for a similar reason.

But I highly doubt the problems you are having have anything to do with having the "wrong BIOS."  Linux should run just fine on a Windows PC with either BIOS.

I'd check the RAM (run Memtest from any Linux/Ubuntu boot disk) and the hard drive for starters.

Doesn't Windows Memory Tester do the same thing? I ran a scan not long ago and it never found any issues...

Don't know if its useful info or not but I installed Ubuntu through a virtual box before installing onto my new HDD and sometimes when i shut down the virtual machine it'd give a similar "cannot access memory at address blah blah blah" error and also got some error relating to the OS not being able to access something on the motherboard and that my BIOS needed to be upgraded. Again, not sure it it relates or not since it was a VM.

 Again, Windows by itself doesn't have this problem, just whenever i run Ubuntu.

---

### Post by d-cosner on 2014-09-11
Is this the computer you have?

[http://desktop-computers.tech-specs.com/acer-aspire-m3970-n73664187](http://desktop-computers.tech-specs.com/acer-aspire-m3970-n73664187)

Do you have the proprietary drivers installed in Ubuntu for your graphics? The reason I ask is because I believe you need the proprietary drivers installed, otherwise you will have problems with the system locking up.

---

### Post by bluesoviet on 2014-09-11
> **d-cosner said:**
> Is this the computer you have?

[http://desktop-computers.tech-specs.com/acer-aspire-m3970-n73664187](http://desktop-computers.tech-specs.com/acer-aspire-m3970-n73664187)

Do you have the proprietary drivers installed in Ubuntu for your graphics? The reason I ask is because I believe you need the proprietary drivers installed, otherwise you will have problems with the system locking up.

Well it looks the same but no - my GPU is an ATI and not nVidia and my clock speed is 3GHZ not 3.3GHZ(unboosted). Otherwise, yes they are the same.

Are these the drivers your talking about?

[IMG]http://i.gyazo.com/66c92d05f98403a3b4a755b9ffc7753d.png[/IMG]

I was using the xserver driver when the freezing happened. It hasn't happened since but i don't know if that means anything.

Slightly off-topic... is there a way to get more graphics drivers or update existing ones? In one of my games, Left 4 Dead 2, the game freezes to the point of being unplayable and I think its because of the drivers. Also, how do i install the AMD Cataylst center? i tried running the .run file but it'd get 2/16ths of the way finishes and then force quit for no reason.

---

### Post by d-cosner on 2014-09-12
There is information about updated drivers here.

[http://ubuntu-tweak.com/source/xorg-edgers-ppa/](http://ubuntu-tweak.com/source/xorg-edgers-ppa/)

Be careful though because these are more bleeding edge.

---

