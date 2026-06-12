---
title: "Can i install intreped and keep hardy too?"
date: 2008-08-29
forum: General Help
---

### Post by dragos240 on 2008-08-29
I wanted to test 8.10 but i wanted to keep 8.04 hardy for my main os. Is there any way i can do this?

---

### Post by Oldsoldier2003 on 2008-08-29
Yes. Install Intrepid in its own partition.

---

### Post by dragos240 on 2008-08-29
> **Oldsoldier2003 said:**
> Yes. Install Intrepid in its own partition.
Have any links to tut's that can explain that?

---

### Post by Seisen on 2008-08-29
You could also use Virtualbox and run intrepid in that.

---

### Post by Oldsoldier2003 on 2008-08-29
you dont really need a tutorial, just download and burn the hardy live cd iso boot to it and run Gparted. Shrink your Hardy Installation to make room for Intrepid, then install Intrepid in the unpartitioned space.

If you want to get fancy with your setup you can create partitions manually to fit your needs.

---

### Post by Oldsoldier2003 on 2008-08-29
> **Seisen said:**
> You could also use Virtualbox and run intrepid in that.

+1 

That is the easy option and one that I use a lot. VMs are easy to wipe out if you decide you'd rather use the disk space for other purposes. No grub magic needed :)

---

