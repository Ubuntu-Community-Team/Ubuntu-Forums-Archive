---
title: "Cannot boot linux at all."
date: 2008-11-09
forum: General Help
---

### Post by allforcarrie on 2008-11-09
I have an odd problem. I am trying to install Linux on my system under WUBI but, nothing seems to work. When i try to boot using WUBI i get a busy box error, when i try using a live CD i only get a black screen. This happens with ubuntu 8.04 and 8.10 as well as Linux mint 5. I kn its not the disks because I have used them on other computers.

AMD 3200 X2
gigbyte mobo
3 gigs of ram
Nvidia 9600 video card
3 sata Hard drives

---

### Post by TeXtonyx on 2008-11-09
Have you set your bios to boot from a cd?
Have you put aside a partition to install Ubunt into?
Ubuntu, when installed to the drive, doesn't install into the
Windows partition. It is safer to make a partition ahead of time
for Ubuntu to reside. Then during live cd install, choose to drive,
and choose 'largest free space (guided)' which will prevent your
Windows partition from being overwritten. Wubi can be removed from
Windows using the Add/Remove programs utility. I think it is a file,
not a partition on the drive withs its own filesystem. You can also
install Ubuntu to its own drive. free space doesn't mean how much
space you have within a used partition, but how much is unallocated,
it exists outside a formatted partition.

---

### Post by allforcarrie on 2008-11-09
I cant even boot from a live CD. it starts then goes to a black screen. WUBI gives me a busy box screen every time.

---

### Post by TeXtonyx on 2008-11-10
When you say Wubi gives you a busy box screen, that means that you
can boot from Windows? You said you had tested the install cds on other
computers. Have you tested different working install cds on this cd drive,
to find out if the cdrom drive is ok?

---

### Post by night_fox on 2008-11-10
Is the live CD the correct CD for the AMD architecture?

---

### Post by allforcarrie on 2008-11-10
i have tried x86 and x64 disks. The disk also wont work on the second drive on this machine. The disks work fine on my laptop so i'm assuming its something wrong with this machine.

---

### Post by night_fox on 2008-11-10
[http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.iso](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.iso)

Try this one. Your processor has different instructions to the intel x86 and the binaries are not compatible.

---

### Post by allforcarrie on 2008-11-10
I already have.

---

### Post by slyde on 2008-11-11
How long have you left it at the black screen, my system stays at a black screen until x is almost fully loaded, I have an athlon 64x2 4200+ 2gbram, 1sata hd 1 ide hd, on an msi mobo and a geforce 8600gt, the problem seems to be fixed in 8.10 for me, I'd say give it a good 10min at the black screen, I know it sounds dumb but I discovered this on my system when I got disgusted and walked away for a bit, when I came back it was up. I'm not sure what caused it for me but someone once told me it was probably the video card, which at the time was relatively new, maybe your problem is similar.

---

### Post by allforcarrie on 2008-11-11
I have let it sit for 15 min or so, i'll try it again i guess.

---

### Post by allforcarrie on 2008-11-11
i have WUBI running now. For whatever reason, I had to restart windows twice for it to work.  :confused:

---

