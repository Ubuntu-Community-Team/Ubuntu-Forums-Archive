---
title: "Crazy question"
date: 2012-02-21
forum: Hardware
---

### Post by SteMMo on 2012-02-21
Hi all,
i'm wondering if it is possible the following:
- Ubuntu installed on a AMD machine
- for any reason i have to change PC and i must move on a Intel machine
Is it possibile to move the OS HD to the new machine and hope to see, at least, the textual command line?
What happen in this case?
How should recover this situation?

thanks!

---

### Post by bouncingwilf on 2012-02-21
I have certainly moved a hard drive loaded with Lucid between AMD and Intel based machines and rebooted with no significant problems - It may just take a little longer on initial boot ( 32 bit systems only - you can't move a 64 bit version to a 32 bit Intel and expect it to work)

Bouncingwilf

---

### Post by roelforg on 2012-02-21
The first one is a definate yes;
 
If you want to do the second thing,
i asvise installing the i386 (32bit) version of ubuntu (unless you know that the intel one is 64 bit).
 
In Winslow it _does_ matter which one you choose because in winslow the 32-bit only handles 3 gb mem, in linux the 32-bit handles well in the hundreds of gb of mem by default.
I really advise 32-bit for this.
 
When you're gonna move the disk from 1 pc to the other;
make sure you prefix every line in /etc/udev/rules.d/70-persistent-net.rules with #
Otherwise ubuntu might not recognise your new NIC; (it would assign eth1 to it and the netmgr might not see it; so it's a good idea to prefix those lines, done it countless times myself).
Ubuntu shouldn't worry about other things (linux has so many build in drivers and so many modules build by default that udev should fix it all up).
 
If any issues arrise; feel free to PM me.
Have 6 machines myself, 3 of them had the hd's switched countless times, i'm pretty confident it should work as long as you install the 32-bit version.
 
And no question is too crazy here; we're all here to help.
Once you've made experience; you can help others too.
 
FYI; My speciality is with HW/Net(wired)/Programming problems but i can always try to help you with other stuff as i have had a host of other stuff too, the experience comes with solving them (those graphical issues are a pain in the a** but should be solvable; example: one of my Ubuntu's wouldn't recorgnise it's graphics card, i managed to install openssh-server and ssh in from my other pc and solve the issue (problem: color wasn't detected right and it offset the bits in the graphical mem by one (e.g. assigning text values to color-regs and color values to text-regs *; unreadable, but my experience in os-dev helped a lot in determining the cause) and set so high my card wouldn't take it; dailing it down fixed it).
 
 
Graphic mem 101: in text mode (i was using server version) this is how graphic card work: their base addr was (IIRC) 0x8b000; you'd assign letters like this: 0x8b000=<hex value of the ascii value of the char> 0x8b001=<hex value of the color> 0x8b002=<hex of char> 0x8b003=<hex of color> etc. now, offset this by one (i tried this in an emulator and i reproduced it with a simple selfwritten kernel) and any value to high would cause the color to default to black-on-white (instead off grey-on-black) , so assigning ascii values (0x69 is IIRC a) would be to high, the low ascii values are special chars or empty ones so assigned the (relativly) low color values to the text regs would cause unreadable text)

---

### Post by roelforg on 2012-02-21
bouncingwilf got it before i did (that's what i get for long posts);
he's right though.

---

### Post by Grenage on 2012-02-21
> **SteMMo said:**
> Hi all,
i'm wondering if it is possible the following:
- Ubuntu installed on a AMD machine
- for any reason i have to change PC and i must move on a Intel machine
Is it possibile to move the OS HD to the new machine and hope to see, at least, the textual command line?
What happen in this case?
How should recover this situation?

thanks!

I've also done it, and had no problems.  Linux is exceptionally forgiving, which I assume is down to the drivers packed into the kernel.

---

### Post by roelforg on 2012-02-21
> **Grenage said:**
> I've also done it, and had no problems. Linux is exceptionally forgiving, which I assume is down to the drivers packed into the kernel.
 
FTR: Linux doesn't have "drivers" it has modules, a whole lot of them. + They aren't all packed in the kernel (than you'd need a lot of mem to house the kernel), it only packs generic ones; udev loads all the others once they're needed.

---

### Post by Grenage on 2012-02-21
> **roelforg said:**
> FTR: Linux doesn't have "drivers" it has modules, a whole lot of them. + They aren't all packed in the kernel (than you'd need a lot of mem to house the kernel), it only packs generic ones; udev loads all the others once they're needed.

Indeed, but given the nature of both the forums (and more pertinently, the opening post), simple generalisations suffice.

---

### Post by roelforg on 2012-02-21
> **Grenage said:**
> Indeed, but given the nature of both the forums (and more pertinently, the opening post), simple generalisations suffice.
I agree, i do that all the time.
But, from experience with teaching linux (ubuntu, to be exact) to others, i know that you need to tell newbies the right terms because they might get confused over them when reading stuff in which they do use the right terms if they've never heard of them (e.g. there are enough topic's here where everyone talks about modules, if you've never heard of them, it might seem very complex and not related when searching for driver issues, so now they know that (for the average user*) the terms mean the same thing); better do it right the first time!

So I wasn't correcting you, i was adding info (hence the "For The Record") (motto: it's generally better to give to much info than not enough).

* More advanced users will know that modules can do much more than that; i just don't wanna confuse people as the whole point of my earlier post was about not confusing people.

---

