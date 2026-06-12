---
title: "NTFS-3G FSTAB mounting"
date: 2008-10-04
forum: General Help
---

### Post by GuDoN on 2008-10-04
Hello!

I have done this before, and when I tried now again, I couldn't get it to work.

How can I mount an ntfs-3g driver - with my NTFS drive in the fstab?

I want it to mount on boot, and it has to be accessable to all users. :)

Please could you help me out :popcorn:

---

### Post by /////// on 2008-10-04
So you want to mount a NTFS drive at startup? Just add this to your fstab then:
/dev/(disk) (mount position) auto auto 0 0

---

### Post by GuDoN on 2008-10-04
Yeah, I had:

```
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0
```

I'll try yours when I get home, thanks! :KS

---

### Post by Nepherte on 2008-10-04
To start with you will need to use UUIDs instead of /dev/disk. So replace /dev/<your partition> with UUID=uuidnumber. You can figure out the uuidnumber with:
```
sudo blkid
```

The rest of your fstab entry line looks good. Make sure the mount point exists.

---

### Post by shuttleworthwannabe on 2008-10-04
WHat works for me is this: install from repo's ntfs-config and then once installed go to Applications>Systems Tools>NTFS Configuration Tool [make sure you have unmounted all ntfs drives first.

HTH,
S

---

### Post by GuDoN on 2008-10-04
> **Nepherte said:**
> To start with you will need to use UUIDs instead of /dev/disk. So replace /dev/<your partition> with UUID=uuidnumber. You can figure out the uuidnumber with:
```
sudo blkid
```

The rest of your fstab entry line looks good. Make sure the mount point exists.

That's my problem, UUID shouldn't be required, but the folder should be! :D

---

### Post by GuDoN on 2008-10-04
I confirm: Just create the folder, you don't need any UUID - device path is fine.

Thanks for the insight! :D

---

### Post by Nepherte on 2008-10-05
Actually it *is* advised to use UUIDs instead of /dev/sdxx. The reason for this is that one harddisk may switch /dev/sdxx and UUIDs don't.

---

### Post by GuDoN on 2008-10-05
> **Nepherte said:**
> Actually it *is* advised to use UUIDs instead of /dev/sdxx. The reason for this is that one harddisk may switch /dev/sdxx and UUIDs don't.

Oh yeah, also true... I'll then have to change it later. Thanks again :)

---

