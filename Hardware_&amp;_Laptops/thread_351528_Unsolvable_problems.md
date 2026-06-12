---
title: "Unsolvable problems ?"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by Yoeri on 2007-02-02
I am using Ubuntu now as primary OS for a while (month). I like it and I am planning to remove windows completely. 

There is just one "big" problem, I can't get 3D acceleration to work.
I have an Asus A4K laptop with an AMD64 3200+ and an ATI mobility 9700. The AGP controller is NVidia NForce3. I read over at the ATI site that there are problems when there are missing/wrong kernel modules loaded for agp. I tried adding the nvidia_agp.ko but this totally screwed up my system with a complete reinstallation as result.

I did some searching and found solutions like downgrading your bios (which is not an option for me). I also found a bug entry in the kernel bugzilla database describing a similar agp-problem.

Does anybody know if this problem is going to be solved? I found one user in this forum describing the exact same problem as I have.

See thread: [http://ubuntuforums.org/showthread.php?t=158442&page=2]("http://ubuntuforums.org/showthread.php?t=158442&page=2")

---

### Post by notasquirrel on 2007-02-03
I'm running Ubuntu also on my laptop.  I hate to say it but Ubuntu might not be ready yet as a primary laptop os.  I've read of lots of laptop hardware related problems, and they're kind of plaguing me too.

You'll want to double check the problem areas before erasing windows:

- Can you close the laptop screen and open it ok?  Mine blanks the screen and does not know how to un-blank it, so unless I disable screen-shut events I end up with a permanently blank screen if I close it and have to hard reboot.

- Synaptics touchpad?  If so search around...  Mine freezes up every minute or two, waits for me to stop touching the pad, has a nice 5-second fart while the kernel does something with the module, then starts working again.  Sometimes the system forgets it's a synaptics touchpad and loads a different driver for some reason (??) and I lose the side-scroll sections and double-finger tapping.  I'm sure there's a way to fix it, but I have enough research projects as is.

- My built-in card reader doesn't seem to have any support, which I found out after I noticed my new digital camera won't connect to Ubuntu either.  So I have to switch to Windows to transfer pictures.

- Do your laptop special function keys work ok?  (Mine do for most part but seems I read of problems)

- Can you hybernate and successfully restore?  I cannot, and have run into other people with the same problem.

- Laptop displays seem to be "loose" in their actually following some of the communication standards...  Mine consistently reports the wrong vertical refresh, which seems to be an AlienWare thing.  Seems different people have to disable different parts of the EDID checks in unpredictable ways to get their laptop screen to turn on.  (Mine was invalidating all resolutions due to the screen offering 1KHz higher than whatever I requested it to do, every time.)

- I could be wrong about this, but it seems to me like my battery life in linux is drastically lower than what it is in windows on the same laptop.  It sucks to begin with which is why I noticed, but I get usually about 30 minutes in windows, and 15-18 in linux.  I have no clue how or why that could happen, I just notice it going on.


Just giving you a head's up, because my experience has been one surprise after another.  If only it wasn't so pretty and fun to use when it works!

---

### Post by Yoeri on 2007-02-03
I know, there are still a lot of problems ...

I cannot
- Install 3D-things like beryl, xgl,... because of the issues with my ati card an agp-bus
- Hibernate function not working properly as you mentioned
- Sleep function not working properly 

There is still a long, long way to go but as long as I see progress after each new release, I am a happy user ... (if they could only solve my 3D problems, I want to show of beryl,... to every Windows-adept I know)

I am eagerred to see the Feisty Fawn release and hope my problems are solved in the upcoming kernel versions

---

