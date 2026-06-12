---
title: "Removing GRUB"
date: 2009-06-21
forum: Hardware
---

### Post by M3TAL1QU1D on 2009-06-21
I would like to know if it is possible to remove GRUB off of my exteral HD. I want to create a recovery partition on it and be able to boot from it if needed, but i cannot achieve that with GRUB in the way. I used to have a version of Ubuntu on my external but i have removed it since then. I now have another verson running on my HD.

I do not mind if i need to reformat my external HD cause everything is backed up. I just want to be able to remove GRUB and then load on my recovery partiton and then make it bootable.

Thanks for any help:)

---

### Post by ajgreeny on 2009-06-21
Have a look at [http://mbrwizard.com/](http://mbrwizard.com/) which should help you out.  Don't forget grub is just another MBR, like the windows MBR, so this should do it just as well for you as if you still had a winMBR on the disk.

It is also possible to do it with the command dd, but be careful as that is very powerful with no safety-net if something goes wrong.  I can not remember the exact command, but I'm sure others will know and probably answer your query.

Finally you can certainly do it with a format of the whole disk, but it sounded as if you preferred not to do that.

---

### Post by M3TAL1QU1D on 2009-06-21
alrite, ill give it a shot. Thanks!

---

### Post by M3TAL1QU1D on 2009-06-21
i actually wouldnt mind formatting it to do that. I have everything backed up from it. However, i have formatted it once before and it did not get rid of the GRUB... unless there is a method of sorts to do so.

I tried the program above in XP and it would close out after it says, "press any key for more options".

---

### Post by M3TAL1QU1D on 2009-06-21
Well, im gonna give this a shot. It is called "HDD low level formatting tool." Its freeware too. I read it suposedly erases the MBR as well.

Here's the link for anyone else who is interested

[http://hddguru.com/content/en/software/](http://hddguru.com/content/en/software/)

---

### Post by M3TAL1QU1D on 2009-06-21
Well, that program worked very well. It got rid of GRUB, all i need to do is make it bootable and I'm set!

---

