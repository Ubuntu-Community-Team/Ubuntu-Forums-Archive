---
title: "Laptop boots up to blank screen. Seems fine but no display. Think it may be hard disk"
date: 2008-07-20
forum: General Help
---

### Post by garethsimpsonuk on 2008-07-20
*by the way this laptop runs xp ( a modified 1 called 'vision' by M.O.D ) but I believe this is a hardware issue and I couldn't think of a better forum for tech support, even if it is windows*

Well my laptop booted up into a blank screen a couple of weeks ago, it's been getting worse every day. Sometimes it boots sometimes it doesn't. I hoped it was a software issue and reinstalled xp ( which i do monthly anyway ). It didn't work and neither did other versions of xp.

The laptop is not old but heavily used. I remember doing a disk health check with a 3rd party app around 3 months ago and it said the disk was under 30% health and approaching critical. I save everything on my ubuntu server anyway and planned on replacing the disk when he dies. 
I assumed when it does die, files will corrupt and reinstallation would fail but I can't find anything else wrong and it's fine running a bootable DVD i.e. a different medium to the hard disk. 
So I would say it's the hard disk on it's way out but wanted to be sure before i bought a new 1.

What do you guys think?

Sorry if i posted in the wrong board

---

### Post by srwilde on 2008-07-20
I would say that if things are running OK from disk but not HD then you have a reasonably solid assumption.  Try loading another O/S on the system for grins.  If you have the same problem then you have more support for your theory.

---

### Post by Execute_Method on 2008-07-20
> **garethsimpsonuk said:**
> *by the way this laptop runs xp ( a modified 1 called 'vision' by M.O.D ) but I believe this is a hardware issue and I couldn't think of a better forum for tech support, even if it is windows*

Well my laptop booted up into a blank screen a couple of weeks ago, it's been getting worse every day. Sometimes it boots sometimes it doesn't. I hoped it was a software issue and reinstalled xp ( which i do monthly anyway ). It didn't work and neither did other versions of xp.

The laptop is not old but heavily used. I remember doing a disk health check with a 3rd party app around 3 months ago and it said the disk was under 30% health and approaching critical. I save everything on my ubuntu server anyway and planned on replacing the disk when he dies. 
I assumed when it does die, files will corrupt and reinstallation would fail but I can't find anything else wrong and it's fine running a bootable DVD i.e. a different medium to the hard disk. 
So I would say it's the hard disk on it's way out but wanted to be sure before i bought a new 1.

What do you guys think?

Sorry if i posted in the wrong board

Yeah probably should have had this one in the hardware forum, but that's OK. Anyway, it seems you did pretty good troubleshooting your lappy. Trying to boot from a DVD is a great way to check if the problem is video related or another component. You didn't say which app you used to check your disk, but if it wasn't healthy before(combined with the fact you can boot from DVD), I'd say that you are on the right track.

Just to make sure:

when you boot, you get display + can access bios, but BEFORE the boot loader the display goes blank. I am assuming you don't get boot loader, because you probably would have mentioned trying to boot into recovery(linux)/safe mode(windows) if you did.

what are the specs of the pc, might it have to do with your bios configuration (ie. boot order)? Do you normally keep a jump drive in one of the usb slots (I've seen this before:confused:, where boot priority has usb before primary HD)?

The other possibility is a corrupt MBR, but if you are fairly confident that the HD is/was damaged. You probably should look into a new one.

---

### Post by garethsimpsonuk on 2008-07-21
> I am assuming you don't get boot loader, because you probably would have mentioned trying to boot into recovery(linux)/safe mode(windows) if you did.

this is a very good point and i think you may have turned my theory on it's head. i totally forgot about safe mode last night and it boots up into safe mode no problem now. Also it's always got to the 16 colour xp logo screen after the post. this tells me that the bios is finding the mbr and the os no problem and the xp logo screen must be stored on the disk aswell so it's reading fine + i have installed numerous os'es on to the drive as a test, wouldn't i get write errors? Becsuse i haven't had any at all. 

i've tried ubuntu on this laptop but it's never worked, with this new found knowledge i'm gonna try a fedora disk but i've got a feeling that it's a hardware issue unrelated to the disk. 

oh yea, no peripirals are affecting it and i haven't gone into the bios for months as i have no need to so nothing has changed in there and am i right in thinking that an mbr issue would be fixed during installation?

the specs are a HP pavilion zd8000, p4 3.0 ghz laptop if relevant. 

when i go into control panel - system - device manager ( in safe mode ) none of the components are flagged as faulty, what other tests can i try? i'm not really a hardware guy. 

i appreciate the replies guys so thanks. and yea i suppose the hardware section probably would've been more appropiate! maybe a mod can move it if they've stumbled down this way?

it was good to know the ubuntu forums are where i turn 4 all things tech related, it's not just about the OS

cheers

p.s. is there a way of locating a thread when you forget to subscribe to it? took me ages to find this and the search feature doesn't always index the posts imo.

---

### Post by Execute_Method on 2008-07-21
> p.s. is there a way of locating a thread when you forget to subscribe to it? took me ages to find this and the search feature doesn't always index the posts imo.

Login & hit search dropdown-> find all my posts/threads 

gotta run, I'll post again l8r

---

### Post by Execute_Method on 2008-07-21
> by the way this laptop runs xp ( a modified 1 called 'vision' by M.O.D ) but I believe this is a hardware issue and I couldn't think of a better forum for tech support, even if it is windows

I couldn't find any info on what type of modifications this has, although that may be what's causing the problem.

QUOTE]am i right in thinking that an mbr issue would be fixed during installation[/QUOTE]

Usually this is a good assumption, however, I have seen issues w/ corrupt MBRs that don't get completely overwritten upon new installation. The fact that you have been using a "modified version of XP, may lend to this occurring. I have seen this mostly with old Win 95/98/millenium and NT 4.0 installations.

The way to get around this is using the mbr switch with fdisk in dos. 
```
fdisk /mbr
```
this will completely erased the mbr before you create your partition table, so you can almost guarantee a clean MBR.

I'm not sure of the equivelant in linux though, as I haven't had to do this with anything but M$ written MBRs.

> I remember doing a disk health check with a 3rd party app around 3 months ago and it said the disk was under 30% health and approaching critica

This is still sticking out as being a point of interest in troubleshooting this issue. What app did you use to check this.
I think you should boot into safe mode and run checkdisk. As well, you can try:

Drive Fitness Test from Hitachi:
[http://www.hitachigst.com/hdd/support/downloads/dft32_v413_b00.iso](http://www.hitachigst.com/hdd/support/downloads/dft32_v413_b00.iso)

that is a direct link to the CD image, just burn it and boot from it. It works with most hard drives.

Let me know how it goes

---

