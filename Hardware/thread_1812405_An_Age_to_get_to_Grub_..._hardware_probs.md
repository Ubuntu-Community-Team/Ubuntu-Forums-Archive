---
title: "An Age to get to Grub ... hardware probs?"
date: 2011-07-26
forum: Hardware
---

### Post by Bucky Ball on 2011-07-26
Hi all,

What do people make of this? I was rearranging my room and in the process knocked over my desktop box (landed pretty hard). I have finally got everything connected a month later and have booted it and everything almost works fine, amazingly, apart from the fact that it takes forever to get to the grub menu ...

Once I choose a kernel, all seems fine with software. Just the pre-grub. When I boot the machine:

* First I get a flashing cursor in the left top of the screen;
* After some time it gives me the first 'GRUB loading stage 1.5';
* Some time after that I get 'GRUB loading, please wait' underneath the first;
* Some time after that I get the grub menu;
* Once I choose a kernel everything seems back to normal with software and hardware.

I'm leaning towards hardware. I have 'sudo update grub'-ed and reinstalled grub to the MBR (I dual-boot with Windows XP) but nothing doing. Still enough time after boot to make a sandwich (in some situations handy, I guess).

Anyone like to have a punt at what the possible problem(s) is/are? I will proceed to dig. ;)

---

### Post by 2F4U on 2011-07-26
Did you already look into the log file? Each entry has a timestamp and this may reveal where the system spends the time. Maybe there is a device set to be automatically mounted and which is not there?

---

### Post by Bucky Ball on 2011-07-26
I'll have a look ...

UPDATE: Booted it up to have a look and ran the recovery kernel and it got stuck. There seems to be a problem with /sda5 not having a valid NTFS filesystem by the looks. It halted not long after that error. The fall may have killed that section of the disk as won't boot Windows either.

I'll keep trying.

---

### Post by Bucky Ball on 2011-07-27
Looks like the machine could be screwed. I booted off a Xubuntu LiveCD and it did boot, just took ... an age. So I'm thinking this is definitely a hardware thing. Perhaps I have screwed the boot drive (I have a 80Gb drive where XP, Ubuntu, /home, and /swap live). Although when I can get there everything seems to be there and accessible. 

Tempted to reinstall but realise that is probably not going to make any diff. 

and ... bump ... any ideas how I might check that drive?

Maybe the MBR is just somehow screwed up. I did use some commands to fix that from Windows sometime ago but have no idea which ...

---

### Post by Blasphemist on 2011-07-27
It seems to me that booting from you cd tells us something. If that takes a long time, and that is the issue when booting from the hard drive, then it's unlikely it is the hard drive. When booting from the cd, the bios loads the data it needs from the cd, not the hard drive. 

First thing I'd do given the cause and symptoms, is make sure that every chip on the motherboard at least that is in a socket is well seated. Also check all cables and their connections. Remember, KISS, keep it simple. Be sure you don't see something shifted that is causing a binding or pressure. 

I'm in the process of trying to digest the specifics of stage 1, 1.5 and 2 of the boot process but haven't absorbed everything yet. Stage 1 is only loading 500 bytes from the mbr and using different devices to boot from you've read that from 2 different devices into RAM. The RAM is consistent in that and not the mbr. Look first at the RAM.

---

### Post by oldfred on 2011-07-27
Are you booting with grub legacy?

The grub2 includes the search line and has to parse all the system to find that the UUID in the set root is correct. If it has trouble parsing any partitions then it has to time out or sometimes even gets lost. I had a full install in my USB flash that was mounting as sdg and it just stopped looking for it. I edited out search and edited set root to correct drive that grub saw it (had to experiment a bit) and then it worked.

I have had gparted not mount my XP drive but XP would boot. After chkdsk on NTFS partition then everything worked faster.

---

### Post by Bucky Ball on 2011-07-28
> **Blasphemist said:**
> ... make sure that every chip on the motherboard at least that is in a socket is well seated. Also check all cables and their connections. Remember, KISS, keep it simple. Be sure you don't see something shifted that is causing a binding or pressure. 

Done already. Nothing unusual. Will quadruple check though (already triple checked). I built this machine (and it has worked faultlessly for years until the unfortunate knock over) so know where everything should be. 

> **oldfred said:**
> Are you booting with grub legacy?

Grub 2. 10.04 LTS. 

> **Blasphemist said:**
> ... chkdsk on NTFS partition then everything worked faster.

I'll have a search for how to run chkdsk on the drive. 

To all; yes, the 'super-lag' slowness is happening right from boot. Once it actually gets to the menu and I chose something (Ubuntu kernel) things seemed to be okay. Now, though, Ubuntu won't boot and neither will Windows (Win didn't from the start).

Will have another look tonight when I have some time. Thanks for the replies. ;)

---

### Post by oldfred on 2011-07-28
If you are booting with grub2, you should not be getting a message about 'GRUB loading stage 1.5' as that is grub legacy.

Post boot script.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Bucky Ball on 2011-07-30
Wondering if we might be barking up the wrong tree by looking at the grub and software as the software side was fine before the fall. So not sure how a knock could alter the software configuration (unlike a knock to a human brain!).

Anyhow, I have bunged in the XP disk and am currently in the Recovery Console running:

> Chkdsk /r... so I'll see what that turns up, if anything. 

Definitely leaning toward hardware here, but what? My next plan is to unplug the four SATA drives in there and boot from the IDE which is where XP and Ubuntu live. If the problem persists with just the IDE boot drive plugged in I'm imagining that disk might be stuffed. If it doesn't it is perhaps one of the others.

If the latter is the case I'll plug the SATA drives in one by one and see if one creates the lag problem. Then I can identify which drive it is. If I can't identify a drive then not sure where to go next, but I'd be thinking hardware.

Incidentally, RAM shows correctly and temperature of machine same as always so can rule those two things out I'd say. Chkdsk just finished on the IDE Windows drive and reports:

> CHKDSK found and fixed one or more errors on the volumeI'll reboot and see what happens.

*** MAJOR UPDATE! After Chkdsk /r I rebooted and no lag, straight to the menu, choose Windows and straight in, no problems. So now XP boots at least. I'll check to see if Ubuntu does but think I'm close to 'solved'. But unsure how the knock scrambled the drive brain. I need to replace that IDE soon anyhow so maybe coincidental and it is on the way out and this would have happened regardless. Working for now at least ... 

Thanks for the suggestions and thanks for the Chkdsk idea oldfred (although I do know how to create code tags - you left out the fact that you can type 'm in, too!). ;)

*** Further Update: Ubuntu booting fine now, too, so solved! Cheers. ;)

---

### Post by oldfred on 2011-07-30
Glad you got it working. 

For whatever reason Linux's NTFS driver is more sensitive to issues on NTFS than windows is. I think NTFS should be like Linux and run a check every 40 odd reboots.

I have stopped using PATA/IDE drives. I always had issues of bumping cable and half disconnecting connector, so It might power up but not boot. I just had too many cables with multiple drives. But even with SATA I find I have to change to a locking connector. I must be ham-handed with hardware.

---

