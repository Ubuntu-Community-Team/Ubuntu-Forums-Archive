---
title: "Upgraded to 9.10, now cannot write to floppy"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by davehkent on 2009-11-09
root now apparently owns my floppy drive, so that when I try to copy a file from my Documents folder to a floppy disk, various error messages appear on screen, culminating with "permission denied".

I can see the contents of the floppy disk by typing "sudo mount /dev/fd0" in Terminal, but If I try to copy a file to the disk, the errors occur.

Entering "ls -l /dev /fd0" in Terminal gives the following output:

brw-rw---- 1 root floppy 2, 0 2009-11-09 22:01 / dev/fdo

I tried to change owner to me, but it's reverted back to root. Any help will be appreciated.

Cheers
Davehkent

---

### Post by erilidon on 2009-12-08
Did you ever get this fixed? I am having the same problem.

---

### Post by davehkent on 2009-12-22
No, still working on it, but getting nowhere at the moment

---

### Post by davehkent on 2009-12-29
Problem now solved!

By following the instructions at [www.psychocats.net/ubuntucat/rootlauncher](www.psychocats.net/ubuntucat/rootlauncher) I have created a 'browse as root' launcher button on the top panel. Clicking this opens the nautilus file system as root user. If I then insert a floppy disk, enter 'sudo mount /dev/fd0'in the terminal to mount the floppy drive, then go back to nautilus and click on 'floppy 0' in the left-hand pane, this accesses the contents of the floppy disk, and I can now copy files to the floppy disk!

hope this helps
davehkent

---

### Post by mhampson on 2010-03-24
Simpler solution (not ideal but quick and it works): sudo nautilus

---

### Post by bullet311 on 2010-03-24
So you are basicly using a program that allows you to acess as a root user? Is it only for floppies or any hardware owned by the root?

---

### Post by mhampson on 2010-03-24
> **bullet311 said:**
> So you are basicly using a program that allows you to acess as a root user? Is it only for floppies or any hardware owned by the root?

Nautilus is the name of the usual file and device browser in Ubuntu.

Sudo opens it with extra privileges.

---

