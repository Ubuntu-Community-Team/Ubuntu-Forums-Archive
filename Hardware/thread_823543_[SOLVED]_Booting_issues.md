---
title: "[SOLVED] Booting issues"
date: 2008-06-09
forum: Hardware
---

### Post by WhyAreWeRunning on 2008-06-09
I just tried installing Hardy on my computer, I just formated the whole drive so I can Finally wave good bye to windows, and after the installation I got "Reboot ans select proper Boot Device or Insert Boot media in selected boot device and press a key". It never having any problems booting XP, so I'm at a loss to what could have happened in those few minutes. Any Ideas?

The computer specs are
Athlon 64 3400+
Asus K8V deluxe Mother Board
2 gigs of G.Skill ram
a 20 gig ide hard drive (for the OS)
and a 250 gig sata drive for documents, music, and movies

Thanks  for any help in advance.

---

### Post by thideras on 2008-06-09
You will need to check your boot order in your BIOS.

---

### Post by WhyAreWeRunning on 2008-06-09
Boot order is fine

1. is the DVD drive
2. is the floppy drive
3. is the IDE hard drive

---

### Post by thideras on 2008-06-09
If you put the HDD first, does it do the same thing? 

Do you have multiple HDD's?  If so, change the boot order of those around :)

---

### Post by WhyAreWeRunning on 2008-06-09
Ya if I switch the IDE drive to 1 same thing, and the only other drive in the box is the SATA and that doesnt even show on the boot list.

---

### Post by Tomatz on 2008-06-09
> **WhyAreWeRunning said:**
> I just tried installing Hardy on my computer, I just formated the whole drive so I can Finally wave good bye to windows, and after the installation I got "Reboot ans select proper Boot Device or Insert Boot media in selected boot device and press a key". It never having any problems booting XP, so I'm at a loss to what could have happened in those few minutes. Any Ideas?

The computer specs are
Athlon 64 3400+
Asus K8V deluxe Mother Board
2 gigs of G.Skill ram
a 20 gig ide hard drive (for the OS)
and a 250 gig sata drive for documents, music, and movies

Thanks  for any help in advance.


Press **e** on the entry you want to boot in grub (bootloader) then **e** again on the first entry. Thin you will have to change the drive numbers E.g.

**hd,0,1** (first drive second partition)

to

**hd,0,0 ** (first drive first partition)

Change the numbering press **enter** then press **b** to boot. 

You will have to experement to find the correct drive numbering. If it is the primary drive you installed ubuntu on it should be hd,0,0 ;)


If it works post back and i will tell you how to make the changes persistant.

---

### Post by Vivaldi Gloria on 2008-06-09
Tomatz, this is a bios problem, not grub.

WhyAreWeRunning, There is a further option in your bios to choose the boot priority among your disk drives. Find that bios setting.

---

### Post by WhyAreWeRunning on 2008-06-09
> **Tomatz said:**
> Press **e** on the entry you want to boot in grub (bootloader) then **e** again on the first entry. Thin you will have to change the drive numbers E.g.

**hd,0,1** (first drive second partition)

to

**hd,0,0 ** (first drive first partition)

Change the numbering press **enter** then press **b** to boot. 

You will have to experement to find the correct drive numbering. If it is the primary drive you installed ubuntu on it should be hd,0,0 ;)


If it works post back and i will tell you how to make the changes persistant.

It doesn't even get to GRUB.

---

### Post by Tomatz on 2008-06-09
Ahhh at a second glance it just looks like your drive you have installed ubuntu on is not set up as primary drive in the bios.

Just move the 20gb drive to the second position in the boot device priority section in the bios with cd/dvd rom at the top (first).

;)

---

### Post by WhyAreWeRunning on 2008-06-09
Vivaldi, The only other boot options I can see of ones for enabling/disabling the SATA boot rom (which is enabled but I don't see my SATA drive on the boot list, which is a problem for another time I guess) and LAN Boot ROM which is disabled. I guess I could changed some settings and see what happens, thanks for the help so far guys I'll keep you posted

---

### Post by Vivaldi Gloria on 2008-06-09
WhyAreWeRunning,

I have taken a couple of shots of my bios to give you a better idea. In the first pix you can see that there is a menu called "Hard Disk Boot Priority". When I choose it sends me to a list where I can arrange my disks in order of boot priority, see the second pix. 

In your bios it must be possible to change the order of your drives one way or another. May be take a couple of photos of your bios and post here so that we can have a look.

---

### Post by WhyAreWeRunning on 2008-06-09
Vivaldi, at lunch I got home for a little and I followed you advice and found a list of hard drives to boot from, my sata drive was listed there and just for the sake of trying I switched to boot off the sata drive. GRUB booted! And it saw my ubuntu install on the IDE drive. So somehow the ubuntu auto partioner thought it was a good idea to put the bootloader on a different hard drive then the OS, weird right? So when I get out of work I'm going to go home pull the sata cable and do a fresh install on the IDE drive to see if I can get Ubuntu and GRUB on the same drive. If it works I'll comeback and post this problem as solved. Thanks for the help.

---

### Post by WhyAreWeRunning on 2008-06-09
Disconnecting the Sata drive and doing a fresh reinstall worked.

---

