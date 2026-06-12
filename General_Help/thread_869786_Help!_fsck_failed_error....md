---
title: "Help! fsck failed error..."
date: 2008-07-25
forum: General Help
---

### Post by c_martini on 2008-07-25
My partner rebooted my pc this morning after an unspecified problem. I wasn't awake yet so did not see what was happening before the reboot. Anyhow upon rebooting, it did not make it to starting x or the desktop and this is what was on screen when I saw it:

```
* Setting kernel variables... [ok]
* Activating swap [ok]
* Checking root file system...
1232
fsck 1.40.8 (13-Mar-2008)
/dev/sbd2 contains a file system with errors, check forced.
Checking drive /dev/sbd2: 0% (stage 1/5, 2/195)
Checking drive /dev/sbd2: 1% (stage 1/5, 3/195)
Checking drive /dev/sbd2: 1% (stage 1/5, 4/195)
Checking drive /dev/sbd2: 1% (stage 1/5, 5/195)
Checking drive /dev/sbd2: 5% (stage 1/5, 14/195)
Checking drive /dev/sbd2: 8% (stage 1/5, 23/195)
Checking drive /dev/sbd2: 11% (stage 1/5, 32/195)
/dev/sbd2: Inodes that were part of a corrupted orphan linked list found.

/dev/sbd2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
             (i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sbd2: 12% (stage 1/5, 35/195)
                                                                                                                 [fail]
* An automatic file system check (fsck) of the root file system failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the
root file system mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@POOT~#_
```The fsck check thing has run before as I have dual boot (Windows XP)system with a shared NTFS drive. Sometimes when Xp locks up or needs a hard reset, upon booting Kubuntu, the fsck thing complains and will not mount the drive. That is usually easily fixed by rebooting windows, restarting again into Linux. But this time the reboot was as a result of some problem with a hanging application. My partner is not computer literate and did not realise you can simply kill the app itself rather than restarting the pc.

I am not sure what to do about this error and unable to get into x or the desktop...

Any ideas?

---

