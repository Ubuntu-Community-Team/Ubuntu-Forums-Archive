---
title: "hda: lost interrupt"
date: 2008-05-06
forum: Hardware
---

### Post by devinWhalen on 2008-05-06
Problems booting up.  I turned off my computer a couple of days ago and when I tried to restart the machine it made a bit of a clunking noise and would just get stuck with the grub loading message and would never boot up.

I tried using the Ubuntu install cd but when I try booting from the harddrive I get messages like this:

hda: timeout error
ide: failed opcode was: unknown
hda: lost interrupt

The thing is I didn't make any software changes.  I checked to make sure all the cables were in all the way in case something came loose but everything looks fine.  The bios seems to be able to recognize the harddrives.  Could this be a power issue?

Is there a way I can try to boot up just to make sure my harddrives still have all my data on them?  Has anyone seen this before.

Thanks for any help.

---

### Post by jocko on 2008-05-06
It sounds to me your hard drive is dead or dying.
Have you tried booting from a live cd to see if you can mount the drive?

---

### Post by devinWhalen on 2008-05-06
Thanks for your response.

I tried the system repair option from the cd but it was having problems with my DVD player, it was asking for me to load in a module from a disk.  Is there somewhere do download modules for DVD players?  Or maybe something I can run off a floppy?

Thanks.

---

### Post by jocko on 2008-05-06
> **devinWhalen said:**
> Thanks for your response.

I tried the system repair option from the cd but it was having problems with my DVD player, it was asking for me to load in a module from a disk.  Is there somewhere do download modules for DVD players?  Or maybe something I can run off a floppy?

Thanks.

System repair option? Are you talking about a windows cd? I can't help you with windows...
Have you tried booting from an ubuntu live cd? Or any other live cd?

---

### Post by devinWhalen on 2008-05-06
No windows, I am talking about using the live CD and using the Repair system option or whatever it is called.  I don't want to try to install because I don't want to loose any data.  I suppose I could try getting to the point just before you install on the harddrive to see if it sees them.

---

### Post by jocko on 2008-05-06
> **devinWhalen said:**
> No windows, I am talking about using the live CD and using the Repair system option or whatever it is called.  I don't want to try to install because I don't want to loose any data.  I suppose I could try getting to the point just before you install on the harddrive to see if it sees them.

There is no "system repair option" on a ubuntu live cd.

The options are:
1. [COLOR=Blue]Try ubuntu without any change to your computer[/COLOR]
2. Install ubuntu
3. Check cd for defects
4. Test memory
5. Boot from first hard disk

The first option does exactly what it says: it starts ubuntu from the cd without reading or writing anything to/from your hard drive.
Once it's started, you should be able to access your hard drive to see if there is anything you can do to recover.

---

### Post by devinWhalen on 2008-05-07
So, now it won't even make it past the POST for me to get into the BIOS.  Hopefully, this means that it is not harddrive problem but rather a motherboard or power supply issue.  Not sure what to do from here.

---

### Post by jocko on 2008-05-07
> **devinWhalen said:**
> So, now it won't even make it past the POST for me to get into the BIOS.  Hopefully, this means that it is not harddrive problem but rather a motherboard or power supply issue.  Not sure what to do from here.

That sounds to me like your motherboard or bios is damaged (but I'm no expert).
If you still have a warranty, it shouldn't be a problem to get it fixed but otherwise it will probably cost you some money...

---

### Post by devinWhalen on 2008-05-08
So I was able to get past the POST (don't know why it didn't work the other night) and the options on my Live CD are:

1. Install to the harddisk
2. Install in OEM mode
3. Install a server
4. Check CD for defects
5. Rescue a broken system
5. Memory Test
6. Boot from the first harddrive

So, it seems that my options are different then yours.  I think I better get a newer version of the Live CD and try the "Try ubuntu without any change to your computer" that way I can see if my data is still on the harddrives.

I tried option 6 and got the following error:
isolinux Disk error 05, AX = 000 drive 80, boot failed

I have been looking around on other forums and seen other people with this problem but they all seem to have it happen when trying to install.

Thanks.

---

### Post by jocko on 2008-05-08
Then you don't have a live cd, you have an alternate cd. Download a new one and make sure you pick the "desktop" cd, not the alternate.

---

