---
title: "Intermittant hard lockup problems"
date: 2006-01-18
forum: Hardware &amp; Laptops
---

### Post by Bil-E-daKid on 2006-01-18
Hey there guys,

I'm having an odd intermittent problem on my Breezy Desktop here at work.  

Occasionally, the system will hard lock - the mouse will stop moving and everything freezes - I can't even SSH into it.

I then have to reset the machine and start everything up again.

I've had a look through some log files and can't see anything that stands out as being a problem - hence the reason this is posted on the hardware forum as that's what it seems to be to me (and my small amount of linux knowledge).

The machine is a Dual PIII-1Ghz with 2Gb RAM and two 80Gb IDE hard disks. I typically run a couple of VM's in VMWare 5.5.1 Workstation (latest version). It has an Nvidia GeForce 2MX200 with 32Mb RAM and I'm using the nvidia drivers. (I've tried 'nv' but the same problem occurs - and I used to have an older ATI card before this one and experienced the same problems then). 

Unfortunately, my boss is starting to frown about the problem as he thinks it's a 'linux bug'. :???: Can someone please help me track down the real source of the problem and - if possible - fix/workaround it?

Thanks!

---

### Post by mlmurray on 2006-01-19
I was having the same problems.  There seemed to be no rhyme or reason to it especially since the exact same hardware had not exhibited this problem when I was running Mepis on it.  Therefore I think it may be kernel related (or Ubuntu specific at least).

Anyway, after some research, I finally found something that fixed the problem for me.

Basically, I changed the "kernel:" line in grub (/boot/grub/menu.lst) to read as follows:
```
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro noapic nolapic pci=noacpi quiet splash
```

The relevant options here are "noapic nolapic pci=noacpi"

I would put this on all kernel lines in grub.  Also, to make sure these options are preserved between updates, find the line in menu.list that starts: "# kopt=root=/dev/hda1" (yours may be slightly different, don't change the /dev/hd??) and add "noapic nolapic pci=noacpi" to the options that are already there.  It should end up looking something like this:
```
# kopt=root=/dev/hda1 ro noapic nolapic pci=noacpi
```

Note: don't "uncomment" that line - the "#" needs to be there.

---

### Post by Bil-E-daKid on 2006-01-19
Thanks mlmurray,

I've modified my GRUB menu.lst and will see how we go. (I was just in the process of downloading openSUSE in an attempt to prove whether it was hardware or software.....)

Thanks for your suggestion!

---

### Post by Bil-E-daKid on 2006-01-19
Blast - just locked up again. Going to temporarily switch to openSUSE to prove whether it's hardware or software.

I think it may actually be related to VMWare but not entirely sure. It's a pity I'm running that as, if I wasn't, I might be able to go with a non-SMP kernel which may also help as well.

:-(

---

### Post by Bil-E-daKid on 2006-01-21
Nope - not VMWare as I removed it and still had a hard lock occur.

Now running on a non-SMP kernel and it seems *way* slower (yeah!) but hasn't crashed just yet.

Could it be time to roll my own kernel for the very first time?

---

### Post by Bil-E-daKid on 2006-01-25
Wow - that was a crazy experience.

After downloading five CDs for SUSE OSS 10, I ran the install and booted into my shiny new OS. Kewl - some nice touches since last I this distro. Much more welcoming than it used to be.

Well, then I tried to use the Archive Manager and it wouldn't work - complained about too big a command line, so I couldn't unpack my vmware installer from within gnome. Oh well, I'll use the command line I guess.....

Then I wanted to install mtr to run some test traces across our work network. Downloaded the RPM and rpm -Uvh'd it. Sorry - you need libblahblahblah for this to work.

I'm really not trying to diss Suse here, but by this point I was tearing out what little hair I have left.

Anyway, back to now (Breezy again thank goodness), I think my problem may have been faulty ram slots on my motherboard.

I have now got 2 x 1Gb PC133 modules installed instead of 4 x 512Gb ones. I had problems initially (while still in SUSE) and moved the second module into the third space and away it went.

Methinks the second slot is 'dirty' perhaps.

So, my work world is at peace again and everyone can go about their business.

Thanks for watching.

:-D

---

