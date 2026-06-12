---
title: "need help with onboard video chipset"
date: 2011-08-01
forum: Hardware
---

### Post by NERDMAN! on 2011-08-01
a friend of mine asked me to see what i could do about lack of video memory on his pc.
he and i have both been informed by various sources that it apparently can be configured in bios, however i have no clue what i'm doing in this case as ive never tried to do anything this advanced. his pc is running american megatrends bios version 2.61.
it has a pitiful 8megabytes of shared video memory, and a full 4gig of ram. all he wants is a bit more memory to run a 16bit game called wonderland online.
just wonderin if anyone here has ever managed to up the shared memory on their pc.
and if they can share their experience so i may be able to pull this off without blowing the pc to bits. thanks in advance!!

---

### Post by sisco311 on 2011-08-01
You can download the user's guide from:L [http://freetechebooks.com/download/ami-bios-settings-2.html](http://freetechebooks.com/download/ami-bios-settings-2.html)  (Chapter 3 AMI® BIOS USER'S GUIDE)

You have to reboot the computer. During the boot-up hold down the Del key until the BIOS screen appears. Use the arrow keys to highlight the "Chipset Features Setup" entry then press Enter to select it. Highlight "AGP Aperture Size" and use the "PageUp" and "PageDown" keys to select the size (64MB should be enough, but with 4GB of ram you can choose 128 or 256). Press ESC to exit to the main menu, then select "Save and Exit Setup". That's all.

---

### Post by NERDMAN! on 2011-08-01
i shall try this. thank you good sir. i'll throw a post up here if it works :D

---

### Post by NERDMAN! on 2011-08-01
i checked it out, there is no agp aperture size option.
i see internal graphics mode selection, options being auto, 1mb, 8mb,
i see DVMT mode select, options being DVMT and fixed.
and a DVMT/fixed memory selector options being 128mb, 256mb, or maximum DVMT.
i'm not feeling confidant enough to go experimenting with a pc not my own so can someone explain to me what this DVMT thing is?

---

### Post by .... on 2011-08-01
DVMT means that the system will dynamically allocate system memory to be used as video memory based upon need. So, when you load a game or other graphically demanding program that needs more video RAM, DVMT reserves system memory for video use. Once you're no longer running graphically demanding program, the memory is freed and can be used as regular system memory again.
Feel free to play with the setting. The worst that can happen is that DVMT is buggy (I've seen some reports) and you change it back.

---

### Post by NERDMAN! on 2011-08-01
well its set on maximum DVMT. but how much is maximum i wonder. well in any case thanks for all the help. methinks i understand a bit more about it now.

---

