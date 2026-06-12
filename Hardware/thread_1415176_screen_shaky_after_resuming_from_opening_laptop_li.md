---
title: "screen shaky after resuming from opening laptop lid"
date: 2010-02-24
forum: Hardware
---

### Post by Veratyr9 on 2010-02-24
running 9.10 64 bit on an hp dv7-3085dx laptop.  geforce 230m, with an intel i7 quad cpu. i have some of the ubuntustudio packages installed (but did not install from an ubuntu studio cd, rather started with plain ol ubuntu and installed the packages.  also i am NOT running the RT kernal, im still using the normal one that ships with ubuntu)

i notice that when i shut down and usplash starts the shutdown screen the screen begins to wiggle, bad.  like a glass of water on a decent subwoofer holding a solid tone.

it also does this when i close and open the lid to my laptop.  there is no way to get it to stop (even when hitting ctrl alt f12 and it gets sent to a command prompt, the cursor even shakes)

any ideas?

---

### Post by Lone_wolf92c on 2010-03-03
I'm having the same problem as you, as well as getting an "overheated" computer message anytime I reboot. Supposedly there is a fix for the overheating by patching the BIOS...Googled it and got the .exe file. Only way to run that is with WINE and i did that...still no fix.

I would assume that the fuzzy screen has something to do with the Nvidia drivers because they give a larger resolution than normally given under Ubuntu.

---

### Post by crlang13 on 2010-03-03
I had a similar problem on my MSI netbook.  The screen would flicker when I booted up, adjusted brightness, closed and opened the lid, etc.  It was a bios problem.  

You can't update it in Wine because it's only an emulator, it behaves like windows but is not windows.  Similarly, you can't update it in dosbox because it's not actually Dos.

Your options are:

if you have windows, update the bios in windows and you should be fine.

download freedos ([www.freedos.org](www.freedos.org)), use unetbootin to make a bootable flash drive and install the bios in dos.

---

### Post by Lone_wolf92c on 2010-03-04
So, how exactly do i go about using freedos to install?

make the flashdrive boot into dos? how do i then grab the bios?

---

### Post by crlang13 on 2010-03-04
Throw the bios into your "C" drive in freedos :p.

I use unetbootin to make the flash drive.  So, although it's a bootable flash drive, you can still inspect its contents in Ubuntu.  Open it open, there should be a folder called freedos in there along with some other stuff.  That's your C drive.

---

### Post by Lone_wolf92c on 2010-03-04
Wait...i thought i had to make the bootable drive FOR freedos...sorry i'm kind of new at this. mind a bit more of a step-by-step breakdown?

---

### Post by crlang13 on 2010-03-04
> **Lone_wolf92c said:**
> Wait...i thought i had to make the bootable drive FOR freedos...sorry i'm kind of new at this. mind a bit more of a step-by-step breakdown?

Hey, I sent you a private message with a step by step, but I was going to cut and paste it back into the thread so everyone could check it out and now I can't find it!  I hope it went through to you.  If it did, can you send it back to me?

Thanks

---

### Post by Lone_wolf92c on 2010-03-04
I have it and can repost it if you'd like...but you're assuming we have a BIOS to replace it with...we dont.

HP only posts the BIOS patches as far as i can tell...which leaves us high and dry as far as your solution (which was great if we had a BIOS). As it is, I had to boot up a windows 7 disc and then patch that way (fully installed 7, used a flashdrive to transfer the .exe)

Either way...it does not fix the shaky screen problem. The overheat warning is gone however, so thats nice. I'm going to try and use a screensaver like the free fire in order to avoid the shaky screen. Will post updates

---

### Post by crlang13 on 2010-03-04
@Lone_wold92c

grrr... That's annoying that you can't get a BIOs flash from HP. I can help you no further then:p. As you know, I only have experience fixing the problem on my hardward (MSI netbook).  Hopefully, at the very least, it's gotten you 1 step closer to a full fix, and, maybe if you do figure out the full fix for your hardware, feel free to modify my directions and pass them on :p

Goodluck.

Edit:
and yes, I had the bios flash already which I was able to download from MSI

---

### Post by Lone_wolf92c on 2010-03-05
thanks for all your help crlang, i think it's just these HP's having issue with Linux. I've now patched the BIOS to F.13 from F.04 and while the overheat message is no longer displayed i still get the fuzzy/shaking screen after comming out of sleep mode and random lock-ups.

for the lockups, is there anyway to pull a "crash report" on it in ubuntu?

---

