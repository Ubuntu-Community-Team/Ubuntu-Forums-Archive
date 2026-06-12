---
title: "Extremely long boot time, hangs at a few different points"
date: 2008-11-29
forum: General Help
---

### Post by Rubicon421 on 2008-11-29
Wubi install on 3.2GHz P4/2GB RAM/ XP home machine. On reboot, the first screen where you can choose Ubuntu or Windows comes up fairly quickly. If you choose Ubuntu, it use to get an error that said something about 'gave up waiting for root device. I found a post that said how to edit rootdelay and did that and now it at least reboots into Ubuntu without error, but it is really slow. 
Now when I choose Ubuntu, it gets to the Ubuntu logo screen with the progress bar and takes about a full minute for it to go to the next screen which is all the checks that say [OK] on the right side of the screen after them. All of the checks are done pretty much instantly until the end, then it takes just over a minute while the last line says 'Activating swapfile swap.......
 
After that it goes to the log in screen.
 
I think the longest single screen it sits at is not much more than 1 minute but all together it takes about 5 minutes to restart.
 
I edited the bios to remove the floppy drive as a boot device and made sure the HD with the OSs (only HD in machine) is the 2nd boot device right after CD drive.
 
What else can be done to speed things up? I prefer GUIs to edit these types of settings if that is an option because I am very new to Linux and a little nervous about editing in the GRUB loader before the OS boots, or using the terminal. If that's the only way, then please be thurough in your explanation. 
 
Thanks for the help

---

### Post by Orlsend on 2008-11-29
This due to high disk fragmentation in windows,try running a defrag in windows.

(you don't need to do the whole disk,just your Ubuntu folders in your c drive)

---

### Post by Rubicon421 on 2008-11-29
tried it. Uninstalled Ubuntu and tried it again on the partition Ubuntu was on and reinstalled Ubuntu and still have same problem. Don't know if it is related or not but I had a problem earler where I got an error in the boot process that said 'gave up waiting for root device' or something like that. I fixed that by changing the rootdelay in menu.lst. It may have nothing to do with it but you probably know way more about this stuff than me.

---

### Post by Orlsend on 2008-11-29
Have you tried it after installing it in windows, remember the wubi install deals with several gigs (It can take up to 30 gigs depends on the install you choose) that could easily fragment your Hard drive.

---

### Post by Rubicon421 on 2008-11-29
I did a defrag on the partition with the install. That didn't work so I uninstalled Ubuntu and defragged the partition again. Then I reinstalled Ubuntu and defragged it again. I'm pretty sure I've beat this dead horse long enough. The problem probably has nothing to do with defragging anyway. Especially considering it only hangs at the swapfile point then finishes booting fast and runs fast once the OS is up.

---

### Post by Orlsend on 2008-11-29
*Bump* I am curious if anyone has another thing to try.

---

### Post by Rubicon421 on 2008-11-30
There are a lot of theads out there about speeding up boot time and even a few that address other swapfile issues. I'm not willing to try fixing everything around the real issue here to speed up everything else and hide the real issue. Could anyone perhaps just provide more info on the problem even if you don't have a solution?
I gathered from some other posts that you can turn off the swapfile which probably would speed up the boot time but slow down everything else once I'm in Ubuntu. I really don't want to do that. I would be willing to try cutting the size of the swapfile in half and see how things go, but I don't know how to do this.
I also came across some setting in GRUB loader or kernel about clockspeed=jiffies or something like that. It sounded like it worked well for some other people but when I edited my menu.lst as they described it would no longer boot and I had to restore my back up of it.

---

### Post by Swagman on 2008-11-30
This happens on my mates laptop too.

I haven't found a solution either.

Bloody annoying isn't it.

---

### Post by Rubicon421 on 2008-11-30
Yeah, but at least it reboots without error and runs well once the OS is up. I'm worried that I will mess up the boot sequence or end up having to reinstall Ubuntu altogether if I mess with it too much. Right now the only problem is that it takes forever to restart. Maybe I should just leave it be.

---

### Post by ago on 2008-12-01
What exactly is the operation being performed that causes the slowdown. Boot in rescue mode and please post the exact text of any command/error you see.

---

### Post by Swagman on 2008-12-01
Thats the thing ago

There are **NO** errors.
The orange bar goes over about 40% then hangs... Then drops to the text screen and rattles off a whole ream of [OK]'s
When it gets to "activating Swap file" it hangs for quite a considerable time.... Probably two to three minutes.

It then boots up perfectly and runs like a dream.

---

### Post by ago on 2008-12-01
when you boot if you remove the options that turn on the graphic bootloader (quiet splash) you can have more insights into the issue. If you press esc at boot and then "e" to edit the menu entries, then enter and "b" to boot.

---

### Post by Swagman on 2008-12-01
I'm going to have to let Kill Vista answer this as my issue is on my mates laptop (I installed Ubuntu on it for him a while ago) and I wont see him until Saturday (Workout day).

---

### Post by Orlsend on 2008-12-07
Ok what kill vista said, just happened to my that with his fresh 8.10 install any solutions out there?

I am going to try to defrag, but I don't have much hope on that.

---

### Post by Rubicon421 on 2008-12-07
Well, for the sake of anyone else having this problem, I hope someone can solve it. I don't have the computer that was having this issue anymore, and the one I have now with Ubuntu on it is working fine. 

Good luck to the rest of you.

---

### Post by Orlsend on 2008-12-07
Just as a note, when I run Ubuntu in recovevry mode and resume to normal boot it works like a charm! but this require your supervision every time to choose and hit enter.

And still for shuting down it takes ages.

---

### Post by lukthree on 2008-12-09
Im having the same issue. brand new hardware, dualbooted with a fresh install of xp, so defrag or hardware shouldnt be the problem. boot goes fine until i get to the splash screen then the progress bar hangs at like 25% for about two minutes, then after that it finishes booting quickly.  When i initially installed 8.10 i didnt have this problem, only upon installing the lastest updates did it arise.  Ill try booting in recovery mode so i can see the text output and what process its hanging on as soon as i get home. Has there been a solution for this yet?

---

### Post by lukthree on 2008-12-09
well, i solved the problem, and what a stupid one it was >_<

it was showing buffer I/O error on device sr0 or something along those lines, it was just a dirty cd in the optical drive, boots fine now

---

### Post by Orlsend on 2008-12-10
Well we never had a single error, yet my dad gave up and we just installed 8.04.

But I think its a must to see the answer fort this issue.

---

