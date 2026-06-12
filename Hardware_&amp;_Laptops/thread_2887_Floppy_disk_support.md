---
title: "Floppy disk support"
date: 2004-11-01
forum: Hardware &amp; Laptops
---

### Post by DCuser on 2004-11-01
While I don't know how common this problem is, or if it has something to do with my specific computer (a Dell Dimension), the floppy disk support is not completely automatic.

I mentioned this in the FAQ forum, but I wondered if anyone has a solution to this situation.

I can get Ubuntu to read msdos floppies properly, but initially, when clicking on "Computer" "Disks" and "Floppy 1", I get a message that the disk cannot be read because the format was not specified.

I go into a terminal and type 

sudo mount -t msdos /dev/fd0 /media/floppy0

and it mounts. This has issues when I try to use it with programs in my normal user-id though.  This probably has something to do with the root user/regular user crossover happening in Gnome.

I can type 

sudo umount -l /dev/fd0

to unmount. The -l is for a "lazy" unmount, which works everytime.

At this point, once I have unmounted in the root level, I can use the top-bar "Computer", "Disks" and select "Floppy 1". The floppy is properly recognized under my normal user-id, and the unmount option works correctly also.  Everything is fine for floppies after this as long as I don't reboot.

This seems to have something to do with not being the root user, or not having the ability to specify the -t msdos option when initially clicking on "Floppy 1".  Does anyone have a solution that will eliminate the need to do the extra steps (or at least automate them)?  It is a problem for me to train other users of the computer to simply learn how to mount the floppy, let alone to go through the special commands that get the mount to properly work.

---

### Post by jeremy on 2004-11-02
I modified my fstab line to read:
/.dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0
(added the . ) works perfectly now.

---

### Post by Caudata on 2004-11-02
When I looked in my fstab  the entry for the floppy drive had the filesystem set as auto,I just changed the filesystem to msdos. Now I can put a floppy into the drive go to drives click on the floppy and it will read. When I want to unmount I use the desktop icon and right click unmount. Hopefully DCuser that is what you wanted, good luck!

                                                                                                          -caudata

---

### Post by DCuser on 2004-11-03
Thanks for the replies.  I used Caudata's advice and got the floppy disks working properly.  I had no idea what fstab was, but now I know.  This sort of thing makes me think that free distributions of Linux still have too many techie issues to be blanket replacements for a typical MS Windows user, but they are definitely getting closer and closer (and I think Ubuntu has super forum support).

---

