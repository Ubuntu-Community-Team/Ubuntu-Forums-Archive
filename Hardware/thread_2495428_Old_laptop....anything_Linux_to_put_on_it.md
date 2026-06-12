---
title: "Old laptop....anything Linux to put on it?"
date: 2024-02-18
forum: Hardware
---

### Post by Autodave on 2024-02-18
I was presented with an old laptop today.  It is a Toshiba Satellite 3000-S353.  Pentium 3 with a whopping one meg of memory.  It is about 37 years old.  Battery is toast.  Originally bought with Win98, upgraded to Win98SE, and lastly to Win ME (yuck).  I plugged it in and hit the power button.  Unbelievably, it powered right up to the desktop!  Everything that I have checked so far......works!

Just curious: was there ever a Linux distribution that would work on this?  I obviously would not use it online.  Or, is there ANY use for this machine other than a conversation starter?

---

### Post by guiverc on 2024-02-18
> **Autodave said:**
> I was presented with an old laptop today.  It is a Toshiba Satellite 3000-S353. ** Pentium 3 with a whopping one meg of memory**.  It is about 37 years old.  Battery is toast.  Originally bought with Win98, upgraded to Win98SE, and lastly to Win ME (yuck).  I plugged it in and hit the power button.  Unbelievably, it powered right up to the desktop!  Everything that I have checked so far......works!

Just curious: was there ever a Linux distribution that would work on this?  I obviously would not use it online.  Or, is there ANY use for this machine other than a conversation starter?

Check your specs; windows 98 required 8MB of RAM (*with the minimum recommended being 16MB*),  and wouldn't start with 1MB as that was provided with the earlier DOS 5  (640KB being the prior limit of earlier DOSes) in the pre-windows  world.

Pentium 3 hardware usually came with 384-1024MB of RAM.

I do have a win 98/me device under the house that has a *floppy* inserted that causes a GNU/Linux system to be booted (*the  GNU/Linux is stored on the FAT file-system of the original windows, as  the device wasn't mine but loaned to me as I wanted a device with a real  serial port; so I just installed what I needed in the free space of the  provided system, take out the floppy & it boots into the windows  that came with the box, and I have only a single file to remove should I  ever need to return the device*).  The box I have has 64MB of RAM (*so it would run windows 98*).  FYI:  The box I'm using as example here is an early Pentium (ie. 1) and not a much newer II or III.

FYI:  I used to have a pentium II box under my current desk; it ran Ubuntu 10.04 LTS (*from memory*), though of course had more RAM than you specify (*384MB originally though that too was upgraded though I forget how far*).  I still have a Nokia IP440 on this desk that is an AMD equivalent to a pentium III (*hasn't been used in awhile beyond holding screens at the right height, or if I want some ambient white noise; its a rack mount box & its fan has multiple speeds so is great as a white-noise generator) - but it still operates too (still booting to the [easter.egg grub of opensuse]("https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Fm56o6r18id441.png") from long ago; with timeout of 8 hours so you've plenty of time to watch the grub penguins).*

---

### Post by Rubi1200 on 2024-02-18
Scratch what I wrote, was not paying enough attention to the specs.

I cannot think of anything that might work.

But, you could have fun trying?

If **guiverc **is correct and the Pentium III comes in at the upper end, you could in theory run Bodhi Linux.

---

### Post by ajgreeny on 2024-02-19
Maybe freedos. It is a sort of open-source version of msdos without any GUI.

It's not actually Linux but could be interesting to try!

[https://freedos.sourceforge.io/wiki/index.php/Main_Page](https://freedos.sourceforge.io/wiki/index.php/Main_Page)

---

### Post by Autodave on 2024-02-19
[QUOTE=guiverc;14179909]Check your specs; windows 98 required 8MB of RAM (*with the minimum recommended being 16MB*),  and wouldn't start with 1MB as that was provided with the earlier DOS 5  (640KB being the prior limit of earlier DOSes) in the pre-windows  world.

Pentium 3 hardware usually came with 384-1024MB of RAM.

OK.  System properties is showing 127.0MB Ram.  That sounds better, but still nothing to get excited about.  It is a 900MHZ Pentium III.  I pulled the covers off of the back and found that it does only have 128MB.  One chip, but there is a spot for another.

---

### Post by tea for one on 2024-02-19
> An absolute minimum of RAM is 46mb. TC won't boot with anything less, no matter how many terabytes of swap you have.
Microcore runs with 28mb of ram.
The minimum cpu is i486DX (486 with a math processor).

A recommended configuration:
Pentium 2 or better, 128mb of ram + some swap
Minimum requirements from [http://tinycorelinux.net/faq.html](http://tinycorelinux.net/faq.html)

---

### Post by Autodave on 2024-02-20
Not sure what I am going to do with this machine at the moment.  I was given a small box of "extra parts" for it.  Looking closer, these extra parts are actually drives that plug into the case itself.  After removing the plastic cover, I have a DVD drive and a 3.5" floppy drive!  Since I have a box of 3.5" disks that I saved from YEARS ago, and there are some games that I really liked to play then, I am going to hope that the floppy drive works and go live in the past!

---

### Post by guiverc on 2024-02-20
Out of interest; I went downstairs & booted the *prehistoric pentium MMX* device under the house with the *floppy *inserted and from what I can read on the screenit appears to have FreeDOS on the floppy, which then boots Puppy Linux from hdd...  Alas it looked like the HDD was dead, as it failed to boot.. but I found the screen hard to read so didn't hang around & explore specifics.

I do recall many Linux systems would work on that 64MB thing, and Puppy Linux (Wary 5.3) was I felt the best, DSL (*damn small linux*), TinyCore & others would boot & run fine too, but my device wouldn't boot USB thumb-drives (*too old*) and wouldn't boot any DVDRW/DVDR I attempted to write for it; so I limited myself to old GNU/Linux systems I could find stored away that came with magazines; Puppy Linux 5.3 was my favorite on the 64MB box.

The pentium II server I had (*that ran 10.04 LTS from memory last** I believe*) I only used as a file-server (7 SCSI + 4 pATA disks)... but I do recall it not booting or using anything like 11.10 or later as its CPU didn't have required instructions.

I can't recall what I could run on a pentium III desktop I had; sure it ran newer stuff than I could with the pentium II system, but I didn't keep  pentium III long anyway, as the CPU lacked the instructions required by updated versions of web browsers & thus the box had less value to me than pentium 4 boxes I had. I didn't recycle the last p4 box until after it was no value in QA testing for Ubuntu (*last release for i386/p4 was August 2020*).

---

### Post by him610 on 2024-02-21
Is there a facility near you that accepts donated obsolete electronic devices?

---

### Post by Autodave on 2024-02-21
> **him610 said:**
> Is there a facility near you that accepts donated obsolete electronic devices?

There is, but I am not getting rid of this machine.  I used to have a full-height HD at one time and I am still sorry that I didn't hang on to that.  I am just not sure what I am going to do with it.  I do have the install disks....they were in the box with drives.  I don't have the ME disk, but I do have the Win98SE install disk.  But, I have to make sure the 3.5" floppy works before I know that I could reinstall that if needed.

I ended up with this machine because I had repaired 2 other laptops that this fellow owned.  Being retired, I have lots of time to fix others' PCs.  When I get one donated to me for whatever reason, I either fix them and pass them on to someone that needs one  or I scavenge whatever good parts out of that I can scavenge.  Right now, I have 2 laptops and 3 desktops that are ready for someone who needs one.  This old Toshiba is a different story: it is too old to really be used by the average person, so I will keep it as a museum piece. :-)

---

