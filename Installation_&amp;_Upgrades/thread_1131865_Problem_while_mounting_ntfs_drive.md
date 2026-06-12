---
title: "Problem while mounting ntfs drive"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by tiago.gmarques on 2009-04-21
Hi there,

I am having some trouble mounting a ntfs drive where I have an old windows xp installation. I am no longer able to boot to windows and I was hoping to recover some documents by mounting the drive while booting from a Ubuntu CD.

When I do:
sudo mount /dev/sda /media/drive

I get:
mount: you must specify the filesystem type

How do I do this?

Thanks,
Tiago

---

### Post by _Purple_ on 2009-04-21
```
sudo mount -t ntfs-3g /dev/sda /media/drive
```

---

### Post by tiago.gmarques on 2009-04-21
Thank you.

However, I do have another problem. I get an error stating:

Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper directory, (e.g. /dev/mapper/nvidia_eahaabcc1).

The problem is, when I try to boot it on windows it crashes after the windows xp logo and then it restarts. It prompts me whether I want to start in safe mode or check the disk, but whatever the option I get the same problem.

---

### Post by StuartN on 2009-04-21
Try adding -r (readonly) and -s (sloppy - ignore errors) to the mount command:

sudo mount -t ntfs-3g -r -s /dev/sda /media/drive

---

### Post by tiago.gmarques on 2009-04-22
Doesn't work. I am going to try to run chkdsk /f with the windows xp boot cd and see if then I can mount it correctly.

---

