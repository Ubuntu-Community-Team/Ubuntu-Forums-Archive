---
title: "Various installation issues and advice needed!"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by weirdbeardmt on 2009-05-10
Hi,

Have inherited three old Compaq Evo slimline machines that were surplus to requirements. They look good, few issues tho:

1) No CD drives (only multibay things)

I've got one of the machines up by just swapping in the hard drive from a different Ubuntu 9.10 machine, but I ran in to some issues when trying to install to the drive in the machine

- I attached a variety of USB CD drives and changed the bios to allow boot from USB media - but it just wouldn't do it. I know the install CDs I have (both 8.04 and 9.10) are fine because they worked on a standard install route - but on the external drive, it didn't.. any ideas? 

I tried using Smart Boot Manager from a USB key - I copied it from the install CD but when I boot with it, I just get "SBMK bad!" - how do I fix that? 
(FYI - I don't have any Windows computers - only OSX (and now this Ubuntu machine) - I coped the files using dd in a terminal window.

2) I've got three of these identical machines - I was thinking about doing some sort of totally pointless but fun "cluster" type thing... any thoughts on doing this with Ubuntu?

3) Can I create an image of the machine that is up and running and just copy that to the hard drives of the other machines (I have one of those IDE to USB adaptor things) - so that I don't actually have to install it 3 times?

Thanks!

---

### Post by logos34 on 2009-05-10
Since these machines apparently don't even have old windows on them (so network install is out), and can't boot from usb cdrom, looks like installation from usb stick is the only way, but the error you got with sbm is not encouraging.

Try he suggestions [here]("https://help.ubuntu.com/community/Installation/FromUSBStick") (including UNetbootin)

Normally you would be able to copy / partition with Clonezilla, Partimage or whatnot (to usb drive), to duplicate on the other machines.  But you need to work from a live rescue cd since / cannot be mounted during the process.  So I'm not sure how to manage cloning given the circumstances.

---

### Post by weirdbeardmt on 2009-05-10
Yeh sorry, should have mentioned that the drives had been flattened.

They're basically old servers and will do network / PXE boot so I guess if I could be bothered to set up a PXE server/ftp site or something it might do it. 

The cloning - I'm referring to the working machine - it's easy enough just to take the hard drive out and plug it into another machine (in this case the working Ubuntu box) - if I can just clone it to the attached hard drive, that'd work...?

---

### Post by cariboo on 2009-05-10
If all the hard drives are the same size, you can use your usb to ide device to connect another hard drive and use dd to clone the drive in the working computer:

```
dd if=/dev/sda of=/dev/sdb
```

If the drives are of different sizes, use partimage instead as dd copies everything, even empty space.

DD is installed by default, and partimge is in the repositories.

---

### Post by weirdbeardmt on 2009-05-10
> **cariboo907 said:**
> If all the hard drives are the same size, you can use your usb to ide device to connect another hard drive and use dd to clone the drive in the working computer:

```
dd if=/dev/sda of=/dev/sdb
```

If the drives are of different sizes, use partimage instead as dd copies everything, even empty space.

DD is installed by default, and partimge is in the repositories.

Perfect, thanks. I'll give it a shot.

---

### Post by logos34 on 2009-05-10
> **weirdbeardmt said:**
> 
The cloning - I'm referring to the working machine - it's easy enough just to take the hard drive out and plug it into another machine (in this case the working Ubuntu box) - if I can just clone it to the attached hard drive, that'd work...?

my brain wasn't working...yeah that would work...

You could do it cariboo's way I guess but 

>  Originally Posted by cariboo907  View Post
If all the hard drives are the same size, you can use your usb to ide device to connect another hard drive and use dd to clone the drive in the working computer:

Code:

dd if=/dev/sda of=/dev/sdb

If the drives are of different sizes, use partimage instead as dd copies everything, even empty space.

DD is installed by default, and partimge is in the repositories.

but wouldn't you have to unmount / to run the dd command?  Wouldn't you need to run it from a live cd? Do you have a cdrom on the working machine?

---

### Post by weirdbeardmt on 2009-05-10
> **logos34 said:**
> 
  Wouldn't you need to run it from a live cd? Do you have a cdrom on the working machine?

No - this is an old hard drive in the "new" CDROM-less machine. But it does have working network if that makes any difference... so I could copy the install CD to that machine... ?

---

