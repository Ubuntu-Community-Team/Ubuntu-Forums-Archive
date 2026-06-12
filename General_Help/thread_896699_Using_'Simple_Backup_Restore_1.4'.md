---
title: "Using 'Simple Backup Restore 1.4'"
date: 2008-08-21
forum: General Help
---

### Post by RagtimeTom on 2008-08-21
I'm an aging newbie using a 10 year old pc to learn Linux.

When my PC died the first time, I rebuilt it from scratch, but had no backup system.

I installed 'Simple Backup 1.4', and began backing up to USB hard drive.

When it died again, I did the following...

Reloaded Gutsy Gibbon from CD-ROM
Upgraded to Hardy Heron
Installed 'Simple Backup Restore 1.4'
Restored /usr /var /home

Cannot restore /etc because it is locked.  1.4 seems to have no help screens.

Restored /etc to /etc2.

I cannot find a way to rename these folders to replace /etc.  How do I do it?

Thanks, RagtimeTom :guitar:

---

### Post by adrien214 on 2008-08-21
what about doing it from the safe mode (boot in command line mode):

sudo mv -R /etc2 /etc

and then

rm -f /etc2

anybody stop me if I am wrong... plus I prefer [flyback]("http://flyback-project.org/")

...but you know, the content of /etc is probably largely upgrade-dependent, so I wouldn't, your call on this one.

---

### Post by RagtimeTom on 2008-08-21
There is no -R in the mv command, so I copied /etc to /etc3 with no problem. 

but doing anything with /etc gave me the following:

sudo: uid 0 does not exist in the passwd file!!!

My thinking leads me down the path of adding a password to the root account, coming back and trying again.

Any ideas?
Regards, RagtimeTom

---

### Post by RagtimeTom on 2008-08-21
Well, I got it to work in safe mode without having to set a root password, but how I did it I'm just not sure.

And thanks for the reference to FLYBACK.  While I restored everything simple restore 1.4 would allow me to do, I was still missing some applications, codec, etc.  It seems to me that if I do a 'full backup', I should get a full restore. So after I get everything finally reconfigured, I'm in the market for new backup software.

Thanks for all your help.  Regards, RagtimeTom :)

---

