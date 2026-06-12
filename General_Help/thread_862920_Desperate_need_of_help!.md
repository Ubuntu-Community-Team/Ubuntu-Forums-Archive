---
title: "Desperate need of help!"
date: 2008-07-18
forum: General Help
---

### Post by Killaspike on 2008-07-18
Ok, I have tried installing Ubuntu before, it did fine and worked. The problem was I wanted to remove windows, I have some kind of weird OCD thing where I just want one operating system on my computer.

I removed the Linux eventually because I couldn't get windows off and just leave Linux ( I don't have a CD-ROM drive so I cant install it that way)

After that I boot and now I see Windows and Ubuntu, the thing is I uninstalled Ubuntu but it still says its there. When I try to go into it it gives me an error. I guess its just still partitioned or something?

Anyways I wanted to have Ubuntu on this computer and im tired of Windows so I go to install Ubuntu again this time using my IPOD. For some reason I cant get my computer to boot from my IPOD.

Once I realise I cant get my IPOD to boot Linux I try to install it via Windows again. I get it installed and now I see Windows, and 2 Ubuntu's for my OS choices.

The really crazy thing is this second Ubuntu didnt even install right, it gives me an error when I try to load it up.

What I want to know is there some kind of way to install Linux and then delete all those partitions and use that space for one Linux install without using any CD's, floppys or my IPOD (Unless someone can explain why I cannot boot from it).

Thanks.

---

### Post by falcon61102 on 2008-07-18
When you say you are seeing them, do you mean they are listed in your GRUB or are you using the Windows boot loader?  In either case, pick which OS you want to stick with and remove the others from the boot loader.  If you need help with that, let us know what system you finally want to keep and what boot loader you are using(whether it is GRUB or Windows).

And yes, it's theoretically possible to install it using none of the components you listed, however, you would need a flash drive or external hard disk.  And yes, you could delete all the other partitions as well.

---

### Post by Killaspike on 2008-07-18
> **falcon61102 said:**
> When you say you are seeing them, do you mean they are listed in your GRUB or are you using the Windows boot loader?  In either case, pick which OS you want to stick with and remove the others from the boot loader.  If you need help with that, let us know what system you finally want to keep and what boot loader you are using(whether it is GRUB or Windows).

I mean when I load my computer and the BIOS is asking me wich OS I want to load into, I have three choices

Windows Vista Home

Ubuntu

Ubuntu


The second Ubuntu is the one I just installed and it didnt install correctly, the first one is the one I removed a while ago.

---

### Post by lisati on 2008-07-18
> **Killaspike said:**
> I mean when I load my computer and the BIOS is asking me wich OS I want to load into, I have three choices

Windows Vista Home

Ubuntu

Ubuntu


The second Ubuntu is the one I just installed and it didnt install correctly, the first one is the one I removed a while ago.
It seems a little strange that the BIOS is asking you that - sure you didn't see any message bout "Grub" or anything like that?

---

### Post by falcon61102 on 2008-07-18
Ok, that's fine.  When you go to install Ubuntu again make sure you install the boot loader and it will detect any other OS's on the computer but being that there are none, you won't have any other ones listed.  

As far as all the other partitions, when you are going through the install, use the partitioner to delete and resize to your wishes.  

Have you been able to boot from your iPod in the past?

---

### Post by falcon61102 on 2008-07-18
> **lisati said:**
> It seems a little strange that the BIOS is asking you that - sure you didn't see any message bout "Grub" or anything like that?

I don't know if he realizes the difference... If he can get a fresh install on there like he wants to, it should start him out new anyway so it's probably easier to help him do that than to edit his GRUB/boot loader.

---

### Post by Killaspike on 2008-07-18
> **falcon61102 said:**
> Ok, that's fine.  When you go to install Ubuntu again make sure you install the boot loader and it will detect any other OS's on the computer but being that there are none, you won't have any other ones listed.  

As far as all the other partitions, when you are going through the install, use the partitioner to delete and resize to your wishes.  

Have you been able to boot from your iPod in the past?

No, I cannot figure out why.

If I install Ubuntu via Windows can I get rid of all the other partitions while Ubuntu is running?

---

### Post by Killaspike on 2008-07-18
> **falcon61102 said:**
> I don't know if he realizes the difference... If he can get a fresh install on there like he wants to, it should start him out new anyway so it's probably easier to help him do that than to edit his GRUB/boot loader.

Im trying to get a fresh install but I dont have a CD drive so my only option left it to boot from my IPOD but I cant seem to get that working.

---

### Post by Killaspike on 2008-07-18
Sorry its not my BIOS asking, its my windows boot loader. But I don't know how to change anything with that. 

I also don't know how to use GRUB

---

### Post by falcon61102 on 2008-07-18
I realize this.  Have you been able to boot from you iPod in the past?  Or do you have an external hard drive or flash driver you could use?

---

### Post by Killaspike on 2008-07-18
> **falcon61102 said:**
> I realize this.  Have you been able to boot from you IPod in the past?  Or do you have an external hard drive or flash driver you could use?

This is the first time Ive tried booting from my IPOD.

And its the only external USB or Hard drive I have.

I go into my boot menu for devices and it doesn't show up under Hard Drives like it should. I don't know if my BIOS supports external Hard Drive booting from USB or if I need to partition the IPOD (Which I don't know how to do)

---

### Post by Cl0ud9 on 2008-07-18
I have never used wubi, but in your situation I would take a look at installing wubi in windows and then using this post: [http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591") to get a full install.

---

### Post by sloggerkhan on 2008-07-18
my guess is that you were using wubi, possibly wubi somehow uses the windows bootloader (no bootloaders come from bios, so far as I know). Possibly uninstall did not remove linux entry from windows bootloader or from grub?

So far as switching to only ubuntu, I believe there is a way to install from flash drive and install ubuntu across the whole hard drive erasing what's there.

---

### Post by falcon61102 on 2008-07-18
It may be that you have to setup your BIOS to check for USB drives on boot.  Normally it is an option in your BIOS.  If you go into your BIOS and search around you should see something along the lines of USB on Boot?  with options.  Once you do that, you should be able to see your iPod when you boot

---

### Post by jimv on 2008-07-18
> **Killaspike said:**
> I go to install Ubuntu again this time using my IPOD.

That is the awesomest thing I have EVER read on these forums.

---

### Post by falcon61102 on 2008-07-18
Lol... why's that?  If you really look at it, an iPod is just an external hard drive or flash drive with a pretty screen and controls; as is any mp3 player out there.  With a little work they can pretty much work just like an external hard drive and with a little more work, it's theoretically possible to partition an iPod so that it remains an iPod but has a seperate partition for data storage.

---

### Post by jimv on 2008-07-18
> **falcon61102 said:**
> Lol... why's that?  If you really look at it, an iPod is just an external hard drive or flash drive with a pretty screen and controls; as is any mp3 player out there.  With a little work they can pretty much work just like an external hard drive and with a little more work, it's theoretically possible to partition an iPod so that it remains an iPod but has a seperate partition for data storage.

I wonder if partitioning and putting a bootloader on an ipod would mess it up?

Probably would be good for this guy to run to Walsmart and get a 2 or 4 gig thumbdrive.  They're like 15 bucks now.

---

### Post by falcon61102 on 2008-07-18
You could always restore it through iTunes... have to have iTunes, but it shouldn't be a problem otherwise.  But I definitely agree, 4gigs is almost nothing now... I'm surprised 7-11's aren't selling them yet... :).

---

