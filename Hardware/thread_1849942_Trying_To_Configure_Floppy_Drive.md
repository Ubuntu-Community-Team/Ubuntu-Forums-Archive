---
title: "Trying To Configure Floppy Drive"
date: 2011-09-25
forum: Hardware
---

### Post by haon8 on 2011-09-25
Hey all,

Over the summer I built a new computer for my dad and put Ubuntu on it. We installed a floppy drive because my dad is a psychologist and has a large number of old files that he keeps on floppies that he still needs to be able to access. He didn't have any need to use it at the time so we didn't test it to see if it worked, but now I'm at school and he recently tried using it but it doesn't work. What he told me is that he puts a floppy in and it doesn't appear on the desktop. He tried going into the Ubuntu equivalent of "My Computer" (can't remember what it's called) and double clicked on the floppy drive button, but it gives him an error message saying that there's no media in it and/or it couldn't mount the drive (something along those lines). I'm sorry the description is a bit vague, though my dad isn't the most proficient with computers and I can't help him directly. Any help would be appreciated so that I can give him a hand. Thanks!

---

### Post by coffeecat on 2011-09-25
Have a look at this post:

[http://ubuntuforums.org/showpost.php?p=11244050&postcount=2](http://ubuntuforums.org/showpost.php?p=11244050&postcount=2)

It's not so elegant as using the GUI, but the udisks command works for most people. Just substitute "dad" for "friend" in the last paragraph of that post. :wink:

---

### Post by haon8 on 2011-09-25
Thanks, I'll give him a call to try it out.

---

### Post by haon8 on 2011-09-25
Just tried it, it gave the following error message:

jonathan@jonathanscomp:~$ udisks --mount /dev/fd0
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: /dev/fd0 is not a valid block device

Any ideas?

---

### Post by coffeecat on 2011-09-25
Open a terminal and see what this command outputs:

```
ls /dev/fd*
```

---

### Post by haon8 on 2011-09-25
This was the output:

jonathan@jonathanscomp:~$ ls /dev/fd*
/dev/fd0       /dev/fd0u1600  /dev/fd0u1760  /dev/fd0u720
/dev/fd0u1040  /dev/fd0u1680  /dev/fd0u1840  /dev/fd0u800
/dev/fd0u1120  /dev/fd0u1722  /dev/fd0u1920  /dev/fd0u820
/dev/fd0u1440  /dev/fd0u1743  /dev/fd0u360   /dev/fd0u830

---

### Post by coffeecat on 2011-09-25
That was a bit unexpected. I've not seen that long list of /dev/fd0u???? before. The fact that you do have a /dev/fd0 makes the earlier error message puzzling.

I'm a bit hamstrung at the moment by not having access (temporarily) to a system with a floppy drive and by posting from a small laptop. I'll get back to you.

Which version of Ubuntu are you running: 10.04, 10.10 or 11.04?

---

### Post by haon8 on 2011-09-25
I believe it's 11.04. We installed it around June, if that time period helps.

Also, the ls /dev/fd* output was in a yellow font, if that's what it's supposed to be.

---

### Post by coffeecat on 2011-09-25
I've been looking at some different systems and getting more puzzled with the /dev/fd* business, so I'll put that on hold. Here's something else to check. Open /etc/fstab and see if you have this line:

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by haon8 on 2011-09-29
Sorry it's taken me so long to get back to you. I just got home and I've been trying to figure out the issue on my own, to no avail. Regarding etc/fstab, how do I pull that up?

EDIT: Nevermind, just got it. And yes, I do have that line. It's the last one in the file. Just for kicks, I also checked the Disk Utility. Under "peripheral devices" the floppy drive is listed, though it tells me that the connection is unknown, SMART status is not supported and no media is detected even when a floppy is inserted.

---

### Post by coffeecat on 2011-09-29
SMART status is a hard drive thing only, so if Disk Utility mentions it in respect of floppy drives, that's a bit misleading of Disk Utility.

I'm sorry - I'm out of ideas at the moment. I will do a bit of digging around and post back if I find anything.

---

### Post by haon8 on 2011-09-29
Is it possible that this is due to a shoddy floppy drive or cable? It seems like the valid block device error is due to there not being any media present in the drive, or the drive thinking that there's no media present.

---

### Post by coffeecat on 2011-09-29
> **haon8 said:**
> Is it possible that this is due to a shoddy floppy drive or cable? It seems like the valid block device error is due to there not being any media present in the drive, or the drive thinking that there's no media present.

Tbh, I didn't think of hardware problems. That's a good thought. Yes certainly check the cable and whether it is seated properly both at the drive end and in the motherboard. Might be worth looking at the power connector too. If the power supply has two floppy power connectors (unlikely, I guess) it might be worth trying the other one.

---

### Post by haon8 on 2011-09-29
It's not an issue of power, because the indicator light on the front of the drive is illuminated. My dad and I are going to stop by the local computer shop in a bit to pick up a new drive and ribbon. If they work then the problem will have been the hardware.

---

### Post by haon8 on 2011-09-29
It turns out that the floppy drive cable was defective. After swapping it out with a new one, the drive works perfectly using the udisks command. However, I was wondering if there was some way to make it so that I didn't need to re-mount the drive every time I put a new disk in. As it is, if I switch out floppies without turning the computer off, I have to use the same command (with substituting 'unmount' for 'mount') to unmount the drive, and then re-mount it with the same command. IF I turn the computer off, I still have to mount it again. This isn't a huge problem, but it is inconvenient, and like I said, my dad isn't the most literate with computers. I can write down instructions for him, but I know it'll be easier for him if it worked like it does in any other computer (put in the disk, take it out, and it works)

---

### Post by coffeecat on 2011-09-29
Even if the GUI were working as it should - that is, by double-clicking on the floppy icon which tbh I don't know where it appears in 11.04 - you would still be mounting the drive. And you would still have to remember to unmount it each time you wanted to remove the disc by right-clicking on the desktop icon. The way you handle floppies in the Linux/gnome GUI is somewhat different from what you are used to in Windows. Have a look at what I say in the single post I linked. There's no way round that that I know of.

What you could do is to create a desktop launcher. Right-click on the desktop > create launcher. Put the udisks code in the command box, and you need something in the name box. You can give it a custom icon if you click on the default icon in the create launcher window. Once you have the launcher on the desktop, your father could either double-click on that, or you could drag it into the launcher bar at the left and you would have a launcher there which would work with one click. But you still must unmount one disc before you remove it and then mount another if you put another in.

By the way - I'm glad that you discovered the hardware problem. That explains a lot.

---

### Post by diasf on 2011-09-29
Just a random bit of information. If the drive's LED was always on, that means the cable was hooked up in a wrong way (upside down). It's easier to do that than you might think of :)

---

### Post by haon8 on 2011-09-29
Hm, that's funny. Aside from the hour or so of time wasted, it's ok. The computer shop gave us the cable for free (clearly they don't move any of them).

However, I am now having another (worrisome) issue. We put in one floppy to retrieve the file on it, however after removing it and putting it in again (the first was as a test, the second was to get the file), the file either got deleted or corrupted. The only thing that was on the disk was what Ubuntu labeled as an executable text file. It's name was just two letters, though I can't remember what they were. We assumed that it was just an isolated incident, but the same thing happened with another floppy. The second one was a disaster, because it was an old program that my dad still uses and as far as I know he doesn't have a backup of it. If anyone can tell me what caused this, how to stop it, and if there's any way I can retrieve the files from the disk, I'd appreciate it.

And before you ask, yes, I did unmount it before I ejected it.

---

### Post by diasf on 2011-09-30
Are you sure the disk itself isn't damaged?

Two things you might consider:
- Write lock the disks. That way you can't damage them.
- Do an image of the disks (dd if=/dev/fd0 of=img.iso, then mount using mount --loop img.iso dir/ )

That way you minimize the physical reads to the disk, and the drive itself.

But i have to say, this whole thing is weird. Never had a problem with floppy drives (only with disks)

---

### Post by haon8 on 2011-09-30
Unless the drive itself is damaging the disks, no, they aren't damaged. I'll try what you suggested, but is where any way to retrieve the lost files from them?

---

### Post by diasf on 2011-09-30
From the top of my head I don't know any way. It can be done, that's for sure (assuming the disk isn't damaged beyond repair, that is), i just never needed it. 

First step, do not trust the drive, try reading the disk (-write protected-) on some drive you know works, then you can isolate the problem. If the disk is indeed damaged, make an image and work on the image, not on the disk. 

And remember, does not matter the media, if there is only one copy, all is lost :)

---

### Post by haon8 on 2011-09-30
> **diasf said:**
> From the top of my head I don't know any way. It can be done, that's for sure (assuming the disk isn't damaged beyond repair, that is), i just never needed it. 

First step, do not trust the drive, try reading the disk (-write protected-) on some drive you know works, then you can isolate the problem. If the disk is indeed damaged, make an image and work on the image, not on the disk. 

And remember, does not matter the media, if there is only one copy, all is lost :)

We don't have floppy drives anywhere else in the house. I built my computer a couple of years back and I have no need for them...my mom uses a laptop and has no need for them, and as far as I know, the other computers laying around have been cannibalized beyond repair.

---

### Post by haon8 on 2011-10-01
Is there anyone who knows how to recover lost files from a floppy? I'm going back to school tomorrow and would like to try to get this resolved before then. I'm hoping that my dad made a copy of the program way back in the day (I know he did with some of his other scoring programs), but in case he didn't I'd like to try to resolve it.

---

