---
title: "Laptop won't tun on"
date: 2009-11-02
forum: Hardware
---

### Post by Praxicoide on 2009-11-02
Hello,

I have a very old Vaio laptop running with Xubuntu, the battery has been dead for a while, but I use(d) it plugged in.

Anyways, the computer went dead. When I plug it in, only the caps lock lights up, and pushing the on button does nothing. I am aware that this is a hardware issue, but can anyone tell me if the light is indicating something specific or if it's maybe the power source (or the button even?). Thank you in advance

---

### Post by Praxicoide on 2009-11-03
I removed everything and it finally turns on, giving eight beeps. Nothing loads, but it's a start.

Do eight beeps mean anything?

EDIT: they're not eight regular beeps, but three, then two then more beeps

---

### Post by Dark_Stang on 2009-11-03
Different beep codes mean different things for different motherboards. 
Pop your hard drive and memory out, see if it still beeps.
If it doesn't beep, you've probably got a bad motherboard... tough luck.
If it does beep, put the memory in 1 stick at a time and test it each time. If it passes POST (the splash screen) then you may just have some bad memory. If it still beeps during this you may want to buy another stick just to test with.
If it still beeps with known good memory, then you most likely have a bad motherboard.

---

### Post by Praxicoide on 2009-11-03
Whoa! it loads the BIOS! I took out the internal battery (the one that's like a watch), and it turns on again.

---

### Post by batterybaby on 2009-11-03
i an glad to see that ypurlaptop works again.i want to ask how much did you buy that?>

---

### Post by bubbles99 on 2009-11-03
maybe the system was confused by a bad CMOS battery (the one ur talkin about). replace it, they are usually model 2032. if it still doesnt boot fully, then yo mainboard is bad.

---

### Post by Praxicoide on 2009-11-03
> **batterybaby said:**
> i an glad to see that ypurlaptop works again.i want to ask how much did you buy that?>

I got it for free, actually. They tried unsuccessfully to install Windows XP on it, and the person the original owner took it to said that it needed more ram and other stuff, so they never installed it. She ended buying a new computer. I couldn't get the live CD to boot, but the alternative installed fine.

---

### Post by Praxicoide on 2009-11-03
> **bubbles99 said:**
> maybe the system was confused by a bad CMOS battery (the one ur talkin about). replace it, they are usually model 2032. if it still doesnt boot fully, then yo mainboard is bad.

I can get to the login screen (SLiM), which means that it loads fine, but I can't get past it, it returns me to the same. I logged in from a tty and I logged in just fine. It was kind of late, so I'll have to check that when I get back from work.

---

### Post by Dark_Stang on 2009-11-03
Try putting a new CMOS battery in it. If it won't load with a new CMOS battery the mobo is failing, but you can use it without the battery for now. Your laptop just won't remember what time it is.

---

### Post by Praxicoide on 2009-11-03
Will do. Thank you.

---

### Post by Praxicoide on 2009-11-07
Just an update. This laptop is still giving me grief. The original install had issues with its encryption that rendered it pretty much useless. I downloaded the 9.10 minimal iso, and have tried to reinstall it, only to have it freeze.

In my previous install, I remember this computer froze because of apic or because it ran out of memory. This is a cli install, so I don't think it's the second, unfortunately, I don't know if I can do anything about the first (I typed in cli noapic nolapic and so forth, but I don't know if it makes any difference; I typed cli mickeymouse as a test, and it proceeded just the same).

Memtest gives no errors, so that rules out RAM, but once the boot process gave me a Machine Check Exception error, so rather there may be a problem with thee CPU or mainboard. Maybe I touched something I shouldn't when I opened it, maybe it's something with the fan, who knows? With all this I'm reluctant to crack it open again, but I guess that is what I will have to do.

But maybe it really is a kernel panic because of apic or similar. It's not a consistent freezing, sometimes it will freeze after a few options, but other times it freezes when it is about to finish installing.

---

### Post by Praxicoide on 2009-11-07
To test if the problem is with apic (or acpi, or whatever), I tried an Ubuntu 9.10 disc I used on another machine, and giving it the noapic, nolapic and acpi=off). This is a 256MB RAM machine so I was cutting it really close. It booted the Live CD environment without problems, but froze on the partitioning stage. 

I'm going to download the Xubuntu alternative CD, and see if that works.

---

### Post by Praxicoide on 2009-11-07
I scavenged around and found an Ubuntu 6.10 (yeah) Live CD, so I tried that in safe graphics mode and it worked OK. I didn't want to install it, obviously, but I surfed the web with the session for a while and generally enjoyed the retro-look, without it ever crashing; so I'm thinking this is a 9.10 problem.

Looks like now I have to download 9.04

---

### Post by Praxicoide on 2009-11-08
It indeed was a 9.10 issue, since I could install 9.04 without much hassle. It warns me about 10 unalocated acpi instances, but boots and works normally. Good thing. Since this started as a hardware issue, I was about to toss this machine into the garbage.

So, I guess the solution is not to use 9.10! (kidding, it installed just fine on another machine, but on this one I'll have to wait for the LTS).

I messed up the strip connecting to the trackpad, so I can't move the cursor at the moment, but I (hope) I can buy another one to replace it.

---

