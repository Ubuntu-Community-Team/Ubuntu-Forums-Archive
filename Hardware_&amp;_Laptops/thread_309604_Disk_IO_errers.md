---
title: "Disk I/O errers"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by dlehman on 2006-11-29
I am not sure if this is the right place to post this but...

I am having trouble with my hard drive and want to know is there any way to get ubuntu to ignore bad blocks and just keep working, OR does ubuntu harm hard drives in any way?

my parents have an emarchies with an 80 GB that I setup to dual boot for ubuntu and one day it started acting up and not wanting to boot talking about a system disk error and I could not get the hard drive to work in any other computer. 
So I took the 80GB from their last computer that has quit working and put it in set it up with ubuntu to dual boot. and now I am getting I/o errors the computer will work fine for a little while then when Mom goes to switch a game she gets an error like
Failed to execute child process /usr/games/kpat (disk input / output error)

she clicks ok and the panels disappear when I switch to console I can't login the only option is a hard shutdown.  at first she blamed these errors on edgy because it was right after the edgy upgrade that this happened. 

I did a disk surface test with Hiren's BootCD and it showed bad blocks.

So I have two questions 

1. is there a way to make ubuntu ignore bad blocks?
2. is edgy to blame for these errors?

Thanks for any help

---

### Post by po0f on 2006-11-30
dlehman,

There is a way to make Linux ignore bad blocks, but it would involve a reinstall.  At filesystem creation time, all bad blocks would be marked bad (clever!), and they won't be written to.  This will not stop more bad blocks from appearing though.

My suggestion would be to backup what you can, cut your losses, and get a new hard drive.

Edgy is not to blame for this one, it's just bad/old hardware.  You're lucky it told you, actually.  Better for Edgy to complain than to start losing important data silently.  :)

---

### Post by dlehman on 2006-11-30
I didn't think it was edgy I was just throwing that out there because it has been two in a row.  I figured a new harddrive was the solution I was just hoping there was something else I could do.


Thanks

---

