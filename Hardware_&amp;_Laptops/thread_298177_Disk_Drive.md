---
title: "Disk Drive"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by Sammm_ on 2006-11-12
Well, I recently got given an old PC and decided I would like to install linux on it. So I found my old ubuntu disks and installed 5.10 which all went fine, great I thought, I'll try and upgrade this installation to 6.06. I inserted my disk and tried to run the update command (which I had gotten from a website) something along the lines of...

gks sh /cdrom/cdupgrade/

Which failed.

I tried to open the disk drive, via the button on the drive, to no avail, so I used Ubuntu's eject feature and the disk drive started mentally opening and closing.

So I rebooted the computer hoping all would be ok, it wasn't, I can't open the CD drive without using the eject feature which then starts the CD drive opening and closing until I shut the computer down. 

Now sometimes it boots normaly, with the disk being closed, but not opening via the button, others the disk drive ejects on startup, and wont go back in until the "enterprise volume managment" (I think) section of the start up in which it starts opening and closing until it fishes booting up, I log in and shut down. This is also preventing me from booting from cd, because I cant get the disk in for long enough for it to be recognized.

Help please?

Thanks in advance.

---

### Post by Sammm_ on 2006-11-12
Update: A slow push has started making the disk go back in on boot up, still not booting from cd though.
Also If I manage to get a cd in on boot up it'll be recognized under Ubuntu, but there's no getting it out without going through the eject option.

---

### Post by ncc74656m on 2006-11-12
Stupid question...

Tried replacing the drive? I know it's an old crap box, but any geek worth his salt should have a spare drive laying around, or you can try swapping it for one in whatever 'main' computer you have. Or borrow one. Or anything.

If any of these options are available to you, try 'em, and report your results on that front first.

---

### Post by Sammm_ on 2006-11-12
I'm not your typical geek, I'm pretty sure I don't have a drive laying about... I'll have a look like.

Also, if I change the BIOS so booting from hard drive is disabled yet leave a disk in at boot up it will boot from the HD. If that's of any significance.

---

### Post by ncc74656m on 2006-11-12
Actually, that does make a difference. Is there any way you can try to determine the manufacture of that computer or motherboard and see if there's a BIOS update for it. It seems like your BIOS might be having fits. If it had also been sitting for a bit, it's possible that your CMOS battery is dead. Those are $2 almost anywhere, and easy to find.

In that order, I would probably update the BIOS, and then if that doesn't help, try replacing the battery...

One more option. Depending on how advanced the BIOS is in that system of yours, you could try changing the detection of your HDD (IDE Channel 1, Primary) to None so that it doesn't even try to see the HDD. That'll give you at least a bit more of a clue. Try these suggestions, and report back.

---

### Post by Sammm_ on 2006-11-12
How would I go about updating the bios if it wont boot from CD?

---

### Post by ncc74656m on 2006-11-12
You don't need to worry about booting at all when you boot to the BIOS, or for that matter, update the BIOS. In fact, most times, you need to update the BIOS from a floppy.

When you go to the BIOS, you usually press F2, F10, or Del, or something. You can use the tricks I mentioned above to disable detection of all drives other than your floppy, and try to boot from it. Like I said, not change the boot order, simply disable the detection of the extranneous drives. Then use the floppy to update the BIOS. If you need to, unplug the damned drives from the cables.

---

