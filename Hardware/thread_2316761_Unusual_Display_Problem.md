---
title: "Unusual Display Problem"
date: 2016-03-10
forum: Hardware
---

### Post by ross4 on 2016-03-10
I am trying to get a handle on a display problem that I have.  I know that the whole thing is failing but I want to understand what is going on, not necessarily fix it. (So please don't tell me to chuck out the machine :P )

 

 Essentially, the question is “Why is the screen readable or unreadable depending on what stage I am at from bios to a full Linux desktop?”

 Here are the symptoms:
 At start-up, when I get into the BIOS, the print on the screen is readable, though there are vertical blue or red lines at various places across the screen.  
 When I boot (from a USB or CD, I have no OS on the machine at present), the screen fills with rows/columns of characters that come from some non-English character set. When a menu comes up (for example the first menu on the Xubuntu install disk), it is unreadable, but because of the change in the pattern of the characters, it is obviously being displayed.
 Since I know from previous experience what the menu says, I can choose the option of running it as a live CD. When I do this, eventually Xubuntu comes up and the screen is readable (though the vertical blue lines are there again).  
 I got more or less the same behaviour with  Core plus and Puppy.
 

 I wanted to try installing Arch but, oddly, the install menu screen on that comes up is readable but  when I choose the option to install, the screen becomes unreadable as it waits for input from the keyboard. (When in a live CD, the terminal works fine, by the way).
 

 The system I am having this trouble on is a Toshiba Satellite P100, Intel core two CPU, T5500 @  1.66  GHz, 1.67 GHz, 2.00 GB of RAM with a VGA compatible controller: NVIDIA Corporation G73M [GeForce Go 7600].

Any ideas?
Ross

---

### Post by weatherman2 on 2016-03-10
If by chance you have another computer available that doesn't have this issue, you can install Linux on the hard drive first on the other system, then move the drive back to your Toshiba.  If you don't have that option, I'm sure someone else can suggest an alternate solution - but that's what I would do (have done) in cases like that.

---

### Post by ross4 on 2016-03-10
All four of my computers are laptops and I am just not that savvy enough to try exchanging disk. Way too scary for me! But also, I'm really trying to understand what is going on here and I don't have any idea of how to begin. Even describing the problem was difficult. I wonder if I haven done it in a way that people can't follow.

---

### Post by Edison_James on 2016-03-17
> **ross4 said:**
> All four of my computers are laptops and I am just not that savvy enough to try exchanging disk. Way too scary for me! But also, I'm really trying to understand what is going on here and I don't have any idea of how to begin. Even describing the problem was difficult. I wonder if I haven done it in a way that people can't follow.

Changing the disk drive in a laptop is very staightforward and relatively easy. Don't be afraid to try. Most drives are interchangeable even between different makes and models, although you may have to leave out the caddy that holds the drive.

Since you have no operating system on the machine at present, I suspect the problem is in your install media, perhaps download and burn another disk and try that.

---

### Post by ross4 on 2016-03-25
The problem has become "academic" since I have wiped the disk and given the machine over to be recycled. However, I think it was more likely something to do with a failed video chip or other piece of circuitry or something like that. I re-installed Xubuntu on it from a USB that I use to install on another machine (which worked fine). In that install, the streaks always persisted but the bios screen was readable, the initial install menu screen unreadable, the subsequent screens readable and the final install readable. I still wonder what different electronic 'paths' the signals took as they went from bios or USB or the hard-drive through a video card/chip to the screen, where the text was either a garbled mishmash of strange characters or a readable presentation. How should I mark this thread? I can't say "solved" since that would be misleading to other readers.

---

