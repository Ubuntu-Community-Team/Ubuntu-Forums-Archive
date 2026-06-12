---
title: "Ubuntu LiveCD Installer Not Working"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by Klopenator on 2009-08-30
I have been attempting to load Ubuntu 9.04 onto my old Toshiba Satellite [COLOR=Red]2805-S302[/COLOR] but when I insert the LiveCD and click install, the computer hangs and never starts the installer.

I have tested the disk on another computer and it works perfectly fine and the computer has a 750MHZ PIII with 256 MB of ram, so those can't be the problem.  I have also tried to boot openSUSE;  Its LiveCD shows a progress bar as the kernel is loaded from the disk and the computer always hangs around 18% loaded.

Any solutions?

---

### Post by snowpine on 2009-08-30
Not enough ram. I would recommend using the Ubuntu Alternate Install CD instead, or better yet, use a different Linux distribution with lower system requirements. (I personally love SliTaz, but there are a lot of options... Puppy is really popular for older hardware.)

---

### Post by Klopenator on 2009-08-30
Thanks for the info Snowpine, i'll try out SilTaz.  I already tried Puppy but it had some wirless card issues.

---

### Post by tal007 on 2009-08-30
Here is what I would do:

1. Go to Ubuntu site.

2. Read the installation requirements.

3. Type of CPUs supported.

4. Type of CPU you have on board 32 bit, 64 bit.

5. Type of Ubuntu you are trying to install on it(32 bit, 64 bit )
6. Examine the Hard Drive using the Live CD to see if you have
   enough space on it.

7. If so, the space must be unused,unallocated and unoccupied by
   other OS such XP, Vista...

8. What version of Ubuntu you have Desktop or Laptop.

9. Mindful of BIOS. System BIOS has limitation.when it comes to 
   handling of hard drive space. Allocated too large space may 
   cause freeze. Too small will cause also cause problem.
   Test it with small unused space such as 10 GB, 20 GB etc.

If all these are met, probably a hardware issue such RAM etc..

Be patient, go step by step. You will get there.

---

### Post by mustafa-linux on 2009-08-30
you can still install ubuntu on that machine, but the trick is to make a swap file before you run the installer. if you are interested I can give you the instructions.

---

### Post by Klopenator on 2009-08-30
mustafa-linux
Ok, would I just allocate space for a Linux swap file onto the hard drive?  I can do that =)

tal007:
The hard drive is completely empty. 0_0

---

### Post by tal007 on 2009-08-30
It would be better if the other fellow posted how he did it. If you don't have enough RAM on board, you can sometimes make up for that by setting aside large enough space for SWAP to do the job. Now, how large ? That's bit a difficult to answer. Normally we allocate twice the maximum amount RAM for SWAP space. In you case, it may require more than that. Do some experiments. If you have a big Hard Drive, it would not hurt giving 2, 3, 4 gb for swap. Usually if you have enough RAM on board, you don't need that much for swap space.
Also be mindful when you allocate space for Ubuntu. It has to be within limit of BIOS.

---

### Post by snowpine on 2009-08-30
384mb ram is requred to install from the Live CD. (You are 128mb short.) A 4gb swap partition is overkill. Swap is very, very slow... if your operating system needs swap to perform its everyday tasks, it will not perform well.

256mb of ram should be sufficient to install with the Alternate CD.

---

### Post by mustafa-linux on 2009-08-30
if the cause of the fault is RAM issue then swap [file or partition] should solve the problem. after the installation the system should run normal if your ram is 256MB.

the swap file I used in similar situation was 1GB.

---

