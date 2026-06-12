---
title: "Cdrom drive won't read audio cd"
date: 2009-07-03
forum: Hardware
---

### Post by glennric on 2009-07-03
I can't get the cdrom drive to read audio cd's, however data discs work fine.
sudo lshw -C disk
shows
```
 *-cdrom
       description: SCSI CD-ROM
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio
       configuration: status=nodisc

```
when no disk is in.  If I insert an audio cd nothing happens.  The drive spins and the lights on the drive show for a little bit and then go off.  Then it takes a long time before the drive will eject.  Sometimes it won't eject.  In this case I have found that if I switch to console and stop gdm that I can eject the drive.  I also tried running mplayer from the console to play audio discs, but I get io errors.  I have tried the drive in windows and it works fine.

Any ideas as to how to fix this?  Other cd drives work fine.

---

### Post by glennric on 2009-07-03
I should also add that this drive used to work for audio cd's in Intrepid.  It might have worked earlier with Jaunty, but I haven't tried to play an audio cd in this drive for a few months.

---

### Post by glennric on 2009-07-06
Does anyone out there know anything about how to fix this?

---

### Post by glennric on 2009-07-07
Bump?

---

