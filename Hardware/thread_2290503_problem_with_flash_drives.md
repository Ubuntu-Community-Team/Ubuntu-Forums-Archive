---
title: "problem with flash drives"
date: 2015-08-12
forum: Hardware
---

### Post by jgw on 2015-08-12
I am using ubuntu 15.04

I was going to use a flash drive.  I plugged it in and it appeared in my files list.  I then tried to copy to it and that was refused.  I checked the permissions and it was owned by root.  I tried several other flash drives and they were all owned by root.  I then tried a chmod, first with a sudo, and then logged in as super user (su)  Same thing.  I seem to have fixed my machine so that I cannot deal with flash drives.  I have used gparted to change partitions, etc.   

I have no idea how to fix this one.

---

### Post by ajgreeny on 2015-08-12
What filesystem do the flash drives have on them, fat32, ntfs, ext4?

---

### Post by jgw on 2015-08-12
fat 32.  They are, however, blank and I can reformat.  The strange thing is that I can take the same drives and plug them into another ubuntu system and they work just fine.  The problem machine is using 15.04 and the one that works is 14.04.2

Thank you for the reply.

---

### Post by jgw on 2015-08-13
I have continued to work on this one.  I have four flash drives that now work, for absolutely no reason I can tell.  I still have one that is root owned.  I have tried to change the owner with su, and sudo (chown, group add, nautilus, etc) and get this same response - not allowed.  This seems to be true even when I am the root!  I have now read at least 20 topics concerning this one but I still am failing.  I do not want to deal with the fstab thing as I believe the ownership is built into this flash drive.  I have also used gparted to remove and then partition and format.  There must be an answer to this one?

---

### Post by efflandt on 2015-08-13
What specific flash drive is it? Some may have some sort of protection or encryption.

Something I ran across a while back was a Sandisk Cruzer with U3. Although, I had never encrypted it and had no trouble using it, the Windows encryption software was on a read-only pseudo cdrom that would mount as a separate device when plugged into USB in Linux, so maybe you are attempting to write to such a read-only alternate device instead of the writable flash memory. There are ways to remove the pseudo cdrom if you web search "sandisk cruzer u3 linux"

---

### Post by jgw on 2015-08-14
Nope the one that is owned by root has "COLOR TURN Usb 3.0" written on the side.  Its a 16gb drive, there is nothing special about it.  I have no problem using gparted to remove and put new partitions on it.  the strange thing is that I own 2 of these and only one has a root owner.  Nothing I have tried has changed the ownership.  Just keeps on telling me that its forbidden, even when I am logged in as root.  Its very odd, I think.

thanks for the reply.

---

### Post by jgw on 2015-08-27
I now have all my thumb drives working.  There is absolutely no reason for this happening.  Over several days I just kept testing them, on the same machine they had been failing on and, suddenly, one would no longer be owned by root and would be accessable.  I did this with no fewer than 5 thumb drives.  I have also noticed that one may work one day and, the next, got owned by root again and inaccessable.  This has repeated several times.  I have no idea what is going on and, obviously nobody else does either.  This is, I think, a product of bad fairy interference.  I have lots of these things so I can get by.  

thanks for any replies I might have had.  I am, more than ever, convinced its all done with smoke and mirrors <G>

---

