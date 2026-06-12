---
title: "troubles to mount my cdrom (no medium found)"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by enneisirap on 2007-06-12
hi there.......

i've trouble to mount my cdrom it says: no medium found when i try to mount it manually.......
(sudo mount -t iso9660 /dev/sr0 /media/cdrom)
(the cdrom should work as i booted the ubuntu (server 7.04) for installation from it)

the cd-rom is a goldstar cdrom CRD-8482B 1.01 PQ: 0 ANSI: 5

my /etc/fstab entry looks like that:
/dev/sr0     /media/cdrom0   udf,iso9660  user,noauto 0 0

the /var/log/syslog cdrom part looks like that:
sr0:scsi-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
uniform CD-ROM driver revision: 3.20
sr 1:0:0:0: attached scsi CD-ROM sr0

i have on / a symbolic link "cdrom" which points to "/media/cdrom"
and "/media/cdrom" points to "/media/cdrom0/"

does anyone has an idea what i could do to make it work?

thanks

ivan

---

### Post by robbster on 2007-06-12
Where does your /dev/sr0 point to?

---

### Post by enneisirap on 2007-06-12
hi robbster

the /dev/sr0 points to scd0
scd0 looks like this with an ls -l:
brw-rw---- 1 root cdrom 11,..........

---

### Post by robbster on 2007-06-12
ok, so everything seems to be setup fine... presumed that this is your only optical drive in your computer (?)
(otherwise you should check your symlinks and correct your fstab if needed)

I'd also try: 
```
sudo mount /dev/sr0
```
That usually works due to your entry in the fstab. 

If that doesn't work, try 
```
sudo cat /dev/scd0
```
If your drive can be accessed, you will get a lot of weird signs to your console. Abort with Ctrl+C. 
If you do not get anything, there is something going wrong...

---

### Post by enneisirap on 2007-06-12
ok i tried to boot again from the cdrom and it didn't work out......
so i replaced the cdrom from an other pc...... and it worked.....

so my cdrom crashed between setting up the ubuntu and trying
to apt-get something from the cdrom after installation.....

thanks anyway for your help.....

ivan

---

