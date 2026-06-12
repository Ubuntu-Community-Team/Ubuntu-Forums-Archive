---
title: "URGENT: Laptop won't boot!"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by dbbolton on 2007-11-20
Note: I'm still running Feisty. 

I shut my laptop down normally today. When I tried to turn in back on later, Ubuntu would not boot. I turned it off with the power button, then tried to boot an older kernel, but the same thing happened. So I turned it off with the power button again, and then tried to boot Windows, which also failed. Next, I attempted to boot into recovery mode, and that failed. Finally I tried to boot from a Feisty live CD, but that didn't work either.

I ran the Ubuntu Memtest and a hard disk self-check from BIOS- both passed.

Does anyone have any idea of what's going on? I have some important files on my laptop that I would like to retrieve before pitching the damned thing.

---

### Post by irw on 2007-11-20
Can you give any more details about what is happening?

Is sounds like you manages to get to GRUB; what happens next?

What do you see / how far do you get with the live CD?

---

### Post by salamba on 2007-11-20
If you're trying to get those important files off, and an Ubuntu disk won't boot.  Try a more lightweight rescue CD - I'd recommend the INSERT rescue disk from [http://www.inside-security.de/insert_en.html]("http://www.inside-security.de/insert_en.html")
It's only 60MB and has never failed to boot for me,  even on quite dodgy hardware.

---

### Post by dbbolton on 2007-11-20
> **irw said:**
> Can you give any more details about what is happening?

Is sounds like you manages to get to GRUB; what happens next?

What do you see / how far do you get with the live CD?
After booting Ubuntu, it goes to the screen that says "Starting up..." and hangs.

After booting Recovery Mode, some text flies by and then it just stops. It doesn't show any errors.

After booting Windows, the screen comes up asking something like "Use last known good configuration or Start Windows normally." I tried "Use last known good configuration" then it went to a blank screen.

After booting the live CD the menu shows up. I chose "Start or Install Ubuntu." Some green text flies by at the top of the screen, then it goes to a blank screen.

---

### Post by dbbolton on 2007-11-20
> **salamba said:**
> If you're trying to get those important files off, and an Ubuntu disk won't boot.  Try a more lightweight rescue CD - I'd recommend the INSERT rescue disk from [http://www.inside-security.de/insert_en.html]("http://www.inside-security.de/insert_en.html")
It's only 60MB and has never failed to boot for me,  even on quite dodgy hardware.
Thanks for the suggestion. I'll look into this.

---

### Post by oneadvent on 2007-11-20
did you check ram

---

### Post by dbbolton on 2007-11-20
> **oneadvent said:**
> did you check ram
Yeah, I ran Ubuntu Memtest and it passed with 0 errors.

---

### Post by oneadvent on 2007-11-20
how many passes?

I'm thinking....

---

### Post by dbbolton on 2007-11-20
> **oneadvent said:**
> how many passes?

I'm thinking....
I ran the test completely through ("Passed" to 100%) once.

I really suspect that if there is a harware problem, it's with the hard drive, not the ram. I had to have the hard drive replaced in that computer twice .

---

### Post by scrooge_74 on 2007-11-20
You should open it take the RAM out and just wipe it, it does wonders.

A friend of mine was having weird issues with a PC the other day and it all came down to a faulty ram. It would boot normal, work for a few minutes and then crash and reboot. (Your results may vary)

---

### Post by dbbolton on 2007-11-20
> **scrooge_74 said:**
> You should open it take the RAM out and just wipe it, it does wonders.

A friend of mine was having weird issues with a PC the other day and it all came down to a faulty ram. It would boot normal, work for a few minutes and then crash and reboot. (Your results may vary)
I tried this, to no avail.

---

### Post by Nem1976 on 2007-11-20
How far do you get with the Windows boot?  It's almost sounding like data corruption on the HDD I  don't think the smart test does a full Hdd scan.

---

### Post by oneadvent on 2007-11-20
> **dbbolton said:**
> I ran the test completely through ("Passed" to 100%) once.

I really suspect that if there is a harware problem, it's with the hard drive, not the ram. I had to have the hard drive replaced in that computer twice .

bad hd would not make a livecd act poorly.

Just in case I am wrong, try it without the hd in at all.

(I am wrong 10 percent of the time...I think this is number 8, lol)

---

### Post by dbbolton on 2007-11-20
> **oneadvent said:**
> bad hd would not make a livecd act poorly.

Just in case I am wrong, try it without the hd in at all.

(I am wrong 10 percent of the time...I think this is number 8, lol)
you mean remove the HD and try to boot the live cd?

---

### Post by oneadvent on 2007-11-20
yes.

---

### Post by dbbolton on 2007-11-20
It did the same thing as when the hard drive was in it. So i put it back in, and I'm running a second hard drive test from the bios.

---

### Post by oneadvent on 2007-11-20
> **dbbolton said:**
> It did the same thing as when the hard drive was in it. So i put it back in, and I'm running a second hard drive test from the bios.

If it did the same thing, you have ruled out your hd.

The ram came back ok....

so, what does it do? Does it still show video on the screen when it goes down, or does it reboot or does it freeze?

We gotta be getting closer.

---

### Post by dbbolton on 2007-11-21
> **oneadvent said:**
> If it did the same thing, you have ruled out your hd.

The ram came back ok....

so, what does it do? Does it still show video on the screen when it goes down, or does it reboot or does it freeze?

We gotta be getting closer.
It just shows the menu, then it goes to a blank screen with a blinking underscore.

---

### Post by oneadvent on 2007-11-21
I see. 

How long have you let it go before you gave up? 

It wont go into recovery mode? 
What does it say during the boot up in recovery mode? It should tell you something.

It should be erroring out somewhere.

---

### Post by dbbolton on 2007-11-22
> **oneadvent said:**
> I see. 

How long have you let it go before you gave up? 

It wont go into recovery mode? 
What does it say during the boot up in recovery mode? It should tell you something.

It should be erroring out somewhere.
In recovery mode, it should be erroring out somewhere, but it doesn't. It prints several lines, and stops at this one:

```
[   19.585885] io scheduler cfq registered (default)
```

---

### Post by dbbolton on 2007-11-25
> **salamba said:**
> If you're trying to get those important files off, and an Ubuntu disk won't boot.  Try a more lightweight rescue CD - I'd recommend the INSERT rescue disk from [http://www.inside-security.de/insert_en.html]("http://www.inside-security.de/insert_en.html")
It's only 60MB and has never failed to boot for me,  even on quite dodgy hardware.
I tried this last night. It wouldn't boot either.

---

### Post by dbbolton on 2008-01-22
Is it possible that the motherboard is just shot?

---

### Post by dbbolton on 2008-04-26
I ran a hard disk scan from bios, and it was clean.

I ran a memtest from GRUB, also clean.

I took it to some repair shop and the guy couldn't figure out what was wrong with it. He asked for a "recovery" disc but I haven't got one and I really don't want to erase the hard drive if I don't have to.

Does anyone have any thoughts on this?

---

