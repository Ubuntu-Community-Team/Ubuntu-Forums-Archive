---
title: "Ubuntu Reccomended for computer illiterate people?"
date: 2008-09-12
forum: General Help
---

### Post by Vunutus on 2008-09-12
Hello all,

I'm trying to set up a computer for someone with very limited computer knowledge. The computer is, frankly, junk. Combined with Windows, said junky computer absolutely will not run. Service Pack two completely breaks it and generates tons of fatal ACPI errors.

In lieu of Windows, I was considering putting Ubuntu (8.04 is the CD I have) on it. This brings about several questions:

1. How smoothly will Ubuntu likely support it's hardware out of the box? I know that's a vague question without supplying said hardware, I can only give a few general guesses at it's hardware (I don't have access to it right now). It's a Sony Viao (however it's spelled) desktop made around 2002-2003, using a Dynex NIC. I don't really have any information on it beyond that. 
2. Is Ubuntu really easy enough for someone with almost no computer experience to use (for basic tasks, obviously) without extensive learning?
3. Again with a hardware related question, the person in question needs a specific model of digital voice recorder to work. It's an Olympus VN-4100PC. To transfer files, it uses a program made specifically for Windows. I'm not sure whether or not it works as a USB mass storage device (I'm leaning towards no). How would I go about getting this to work under Ubuntu?

---

### Post by EmanresuusernamE on 2008-09-12
> **Vunutus said:**
> 1. How smoothly will Ubuntu likely support it's hardware out of the box? I know that's a vague question without supplying said hardware, I can only give a few general guesses at it's hardware (I don't have access to it right now). It's a Sony Viao (however it's spelled) desktop made around 2002-2003, using a Dynex NIC. I don't really have any information on it beyond that. 
The CD you burned should be a live CD, meaning you can try Ubuntu out without touching your hard drive at all.

> **Vunutus said:**
> 2. Is Ubuntu really easy enough for someone with almost no computer experience to use (for basic tasks, obviously) without extensive learning?
Yes, I've had people who've never used Linux before say they like it, and that it's easy.

> **Vunutus said:**
> 3. Again with a hardware related question, the person in question needs a specific model of digital voice recorder to work. It's an Olympus VN-4100PC. To transfer files, it uses a program made specifically for Windows. I'm not sure whether or not it works as a USB mass storage device (I'm leaning towards no). How would I go about getting this to work under Ubuntu?
If it's just acting like a normal USB drive, you won't have to do anything at all, except plug it into your computer.  If it requires drivers to use, then perhaps the manufacturer has some Linux drivers you can install.

---

### Post by pcjunkie on 2008-09-12
> **Vunutus said:**
> Hello all,

I'm trying to set up a computer for someone with very limited computer knowledge. The computer is, frankly, junk. Combined with Windows, said junky computer absolutely will not run. Service Pack two completely breaks it and generates tons of fatal ACPI errors.

In lieu of Windows, I was considering putting Ubuntu (8.04 is the CD I have) on it. This brings about several questions:

1. How smoothly will Ubuntu likely support it's hardware out of the box? I know that's a vague question without supplying said hardware, I can only give a few general guesses at it's hardware (I don't have access to it right now). It's a Sony Viao (however it's spelled) desktop made around 2002-2003, using a Dynex NIC. I don't really have any information on it beyond that. 

I have a friends laptop from 2002 running 8.04. I had to put in new RAM and that was it. It runs faster with Ubuntu and I can even run Compiz. The only way to find out is use the CD. If it runs and everything works then it will work once installed. If some things don't check back here to find out why and if there are workarounds. If you have something like "Kernel Panic!" appear then use the live cd to run memtest. usually you will find the memory is damaged and this can cause windows to either crash periodically or not run at all. Especially if a system IRQ is assigned to a chip on the board that is damaged. 
 
If it won't load (the live CD) try using the no APIC method. Some older bios systems are more like a dog chasing its tail than something useful. 


> **Vunutus said:**
> 
2. Is Ubuntu really easy enough for someone with almost no computer experience to use (for basic tasks, obviously) without extensive learning?Yes. Windows makes life harder IMHO, so many rules, so many things can break with no real solution. The whole point of Linux is that it is open and in that, fixable, simply. Solutions for almost all problems you might encounter are everywhere and nothing is left to chance on security and performance. Most fixes are distro transportable so a fix for one Linux will still work on others. With BAsic tasks, eg web surfing, mail, msn its all there. The only thing people will say is "wow, nice computer. (but that's me)

> **Vunutus said:**
> 
3. Again with a hardware related question, the person in question needs a specific model of digital voice recorder to work. It's an Olympus VN-4100PC. To transfer files, it uses a program made specifically for Windows. I'm not sure whether or not it works as a USB mass storage device (I'm leaning towards no). How would I go about getting this to work under Ubuntu?Run the live cd and plug it in, if you are connected to the net it will get what it needs if it the cd does not already have it. Most of these things work within the computers hardware specs and not through "driver magic". If it uses USB then it will work. Look at the packages for audio and see what can be found in general software (unsupported and supported), You will find a whole field of recording, editing, manipulation tools are available. Installing is a tick in a box and ok. can it be any easier?

---

### Post by mb_webguy on 2008-09-12
You might find the "Ubuntu for Grandma" article from [Full Circle Magazine #2]("http://fullcirclemagazine.org/issue-2/") interesting...

---

