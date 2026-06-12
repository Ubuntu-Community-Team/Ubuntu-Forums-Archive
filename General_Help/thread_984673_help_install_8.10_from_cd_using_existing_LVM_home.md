---
title: "help? install 8.10 from cd using existing LVM /home"
date: 2008-11-16
forum: General Help
---

### Post by gschoppe on 2008-11-16
my root dir is on an ext3 partition, but my /home directory is on a Logical Volume... (using LVM)

I royally trashed my installation, and I want to re-install from disk...

how do I perform a new install, keeping my existing home directory?

---

### Post by gschoppe on 2008-11-17
this is messy, but it kinda worked...

i made a clean install, with everything, including /home, on one partition... then I started, installed LVM2, and copied the contents of /home to the LVM partition, overwriting older files... I then added the LVM partition to my fstab as /tempHome, booted to a live cd, deleted the contents of /home, and edited fstab to make the LVM mount to /home, rather than /tempHome...


THIS CREATED A NEW ISSUE...

I think I now have ownership issues...

my desktop effects settings wont persist over sessions, and I can't get firefox to work properly (it won't accept certificates, or even let my use the google bar, unless I run it as "sudo firefox")

I ran "sudo nautilus", and did a recursive ownership change of /home/username/ to my user, but it didn't help...

how do I do a recursive CHMOD, and what parameters should I be using to properly own my home folder (including all hidden folders and files)?

---

