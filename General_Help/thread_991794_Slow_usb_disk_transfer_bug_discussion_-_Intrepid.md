---
title: "Slow usb disk transfer bug discussion - Intrepid"
date: 2008-11-23
forum: General Help
---

### Post by fugative on 2008-11-23
Q: is the slow usb transfer bug still in intrepid? i'm on mint5 (based on hardy and transfers are down to 1.3 mbps at times and rarely above 5. this bug is all over the forum and other places but no mention in intrepid but no mention anywhere of a fix that actually works. 
like to know as i'm thinking of going up to mint6 but i don't want to bother if it's still there.


cheers
Dave

---

### Post by Gary.M on 2008-11-23
> **fugative said:**
> Q: is the slow usb transfer bug still in intrepid? i'm on mint5 (based on hardy and transfers are down to 1.3 mbps at times and rarely above 5. this bug is all over the forum and other places but no mention in intrepid but no mention anywhere of a fix that actually works. 
like to know as i'm thinking of going up to mint6 but i don't want to bother if it's still there.
cheers Dave

Just in from Launchpad on this bug:

"Iomega HDDs with USB-ID 059b:0177 is also affected. There seems to be a patch by Alan Stern for 2.6.28:
[http://bugzilla.kernel.org/show_bug.cgi?id=11843](http://bugzilla.kernel.org/show_bug.cgi?id=11843)
It is a kernel-problem and therefore Fedora and others are also affected."

---

### Post by fugative on 2008-11-24
Has this always existed? Now i think of it when i gave up doze i was more or less on usb 1.1 or didn't use usb flash drives and hdds much but i've seen doze boxes shift 500mb files to a flash drive in the blinking of an eye. 
this is becoming an issue and it doesn't seem to be being addressed properly. 
i'm not about to go running back to mamma Gates but some will.

---

### Post by detroit/zero on 2008-11-24
I've been talking about this problem for months ([thread]("http://ubuntuforums.org/showthread.php?t=793688") [thread]("http://ubuntuforums.org/showthread.php?t=911052") [thread]("http://http://ubuntuforums.org/showthread.php?t=952479") [thread]("http://ubuntuforums.org/showthread.php?t=909158") [thread]("http://ubuntuforums.org/showthread.php?t=895386") [thread]("http://ubuntuforums.org/showthread.php?t=933705")) But it never seems to go anywhere. Either people don't have the problem, don't care about those who do, or just think everything works as it should.

I have [a post over at linuxquestions.org]("http://http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/") that also seems to have dried up.

As I've outlined in other places, the problem is apparent on not only CF memory, USB external HDDs, but also when moving files from one partition to another (i.e., removing deleted files from trash and sending them back to somewhere in my home folder, which resides on its' own partition).

I've not had the problem until Hardy, and I've been using Ubuntu since Edgy. I've narrowed it down to a kernel update that happened back in July or August. Hardy's default kernel (the one that comes on the CD; before any updates) doesn't have this problem. (2.6.24-18?) But I've found posts on this problem across every major distro you can think of going as far back as 2005, which is pretty much when USB2.0 was introduced.

---

### Post by fugative on 2008-11-24
Yeah, don't want to get all zeitgeist but it seems to keep disappearing as a topic.
i checked today cut and paste from usb to laptop gives me 10-13 mbps but the same file back again gives me no more than 3.
BUT Detroit i've got  2.6.24-16 generic . how can i be sure i've got usb ports at all? starting to doubt myself.


don't drop it Detroit but watch out for brown cars parked outside all hours of the night.

 module=ohci_hcd
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: 7.2
                bus info: pci@0000:02:07.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ehci bus_master cap_list
                configuration: driver=ehci_hcd latency=64 maxlatency=34 mingnt=16 module=ehci_hcd



anything here that helps?

---

### Post by detroit/zero on 2008-11-24
> **fugative said:**
> Yeah, don't want to get all zeitgeist but it seems to keep disappearing as a topic.
i checked today cut and paste from usb to laptop gives me 10-13 mbps but the same file back again gives me no more than 3.
BUT Detroit i've got  2.6.24-16 generic . how can i be sure i've got usb ports at all? starting to doubt myself.


don't drop it Detroit but watch out for brown cars parked outside all hours of the night.

 module=ohci_hcd
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: 7.2
                bus info: pci@0000:02:07.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ehci bus_master cap_list
                configuration: driver=ehci_hcd latency=64 maxlatency=34 mingnt=16 module=ehci_hcd



anything here that helps?
It's weird that you get that problem with 2.6.24-16.. That's the default kernel for 8.04, isn't it?

At my last re-install, I locked the kernel version in synaptic to 2.6.24-16. I forgot to find and lock one of the files (headers or modules.. I forget which) and when my update process finished, I was back to square one with slow speeds.

I still have 2.6.24-16 installed (updated right from that version to 2.6.24-21) and if I boot into the old kernel version, all my problems disappear.

---

### Post by ZhuaSD on 2008-12-03
Hi, I had this problem too, with an external ide hd, and have been reading a lot of posts about it since then.

I fixed the problem by clearing out and re-formatting my external hd.  The hd data was transfered at normal speed on my old box. I was concerned that the hd was going bad, and on widoze it also was slow as heck and messed up, even timing out without transfering a few times. But I used some tools and everything came back fine, it's only six months old, and the data was always intact and accessible.  Just not easily movable, taking a long long time.

And I had trouble to properly re format, but ended up getting it done properly in my old system with the live disk.  I have a sata drive and thought this was related to a conflict between sata and ide, and posted about it.  Anyways, since then, so far so good.  Knock on wood.

The reason I am posting here is because I think I might have some useful info or thoughts to figuring out what is going on.  I am on Hardy 8.04, but that doesn't seem to matter.

One thing I noticed about all the different threads was that everyone seems to have a slightly different problem.  For me, it was my ide 250 g WD hd, but NOT my three ~100 g 2.5 portable drives OR the three or so thumb drives I have used on the machine.  

But for Detroit, IIRC, it is/was his thumb drive.

Also, for me the transfer dialog would just stop for minutes at a time.  Then start running again like it should have, then...stop again.  And a gig was taking 5-6 minutes or so, it really wasn't worth timing.

NO system freeze, (like some people have), no slowing down to a crawl and running at xxx kb/sec, often no info in the dialog about what speed it was going at all.

Based on this, I suggest that we should not rule out other causes.  Could this be hardware related?  It might be for me.

Could this be a problem in fstab? I am still really new, but I asked my buddy, a grizzled vet of 2+ years, and he asked about mounting issues.

BOTH of these solutions could explain the problem better based on the fact that everyone has got slightly different symptoms.

Anyway this is meant only as a suggestion to pull back and re-examine the situation. I was pulling my freaking hair out on this one for awhile and even though its fixed for me I just thought I would chime in with my experience.):P

I suggest this is not a kernel issue at all.

---

### Post by detroit/zero on 2008-12-03
> **ZhuaSD said:**
> Could this be a problem in fstab? I am still really new, but I asked my buddy, a grizzled vet of 2+ years, and he asked about mounting issues.

BOTH of these solutions could explain the problem better based on the fact that everyone has got slightly different symptoms.

Anyway this is meant only as a suggestion to pull back and re-examine the situation. I was pulling my freaking hair out on this one for awhile and even though its fixed for me I just thought I would chime in with my experience.):P

I suggest this is not a kernel issue at all.
That's an interesting solution, and one I haven't tried - reason being I have a 320GB USB HDD with >200GB of stuff on it and am running off 
a laptop with a 75GB home partition on a 120GB drive.

I do say kernel issue, though. because I remember exactly when this problem started. This past summer, running 8.04, a kernel update came through for 2.6.24-19. After that is when this problem first appeared. There was nothing else in the update.. I mean, there was the kernel and the headers and the common files, but nothing to do with Nautilus or GVFS or drivers or anything.

To this day, if I do a completely fresh install of 8.04 (with kernel 2.6.24-16) all the transfer-speed issues disappear until the kernel (or modules or headers or common files) gets updated. I still have .24-16 in my grub menu, and if I boot into that kernel, I have no problems.

The last time I did a re-install (middle/end of September) I locked the kernel at the default install version number and updated the rest of the system. I ran for a little over one full week, updated as updates were issued, and rebooted often just to make sure... Until I unlocked the kernel and updated it, I had zero issues with USB file transfer speed, and could both read and write to all USB devices at speeds approaching 30MB/s.

---

### Post by mavk84 on 2008-12-03
hi I'm new to the forum and I had the same problem.
I solved it removing the "noacpi" option in /boot/grub/menu.lst
I had to put that option because of sound problem with intel device but removing it and just leaving "irqpoll" seems to solve both problems... I just tried to play a song and it worked, I transfered one big file (1GB) and nautilus goes up to 23MB/s.
i don't know if this could be helpful.
PS. I'm not really an expert and I don't even know what that option means so if anyone could tell how that could be related to this problem it would be great.
):P

---

### Post by ZhuaSD on 2008-12-03
You could well be right, I was just trying to throw out some different ideas.

For me, this install is just over three weeks old now, and I have kept it well updated the entire time.  The problem happened about one week ago.

---

### Post by ZhuaSD on 2008-12-03
hey mavk, that's interesting because I am having some sound issues on a intel audio controller, its just the vlc player will lose sound if I watch videos in firefox.

That fix works for some people, not everyone.  I didn't get that far...

---

### Post by BrownieMan on 2008-12-14
Is there ANY workaround for this? Can I install a kernel from when it worked properly? And how would I do that without reformatting?

---

### Post by ZhuaSD on 2008-12-16
You got to start from square one, BrownieMan.  Start a new thread and explain your symptoms, seek out some advice.  You had connectivity between drives and then???

I am more convinced than ever that it is related to mounting and fstab.  For what that is worth.

---

