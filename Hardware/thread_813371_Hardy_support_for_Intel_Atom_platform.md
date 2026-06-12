---
title: "Hardy support for Intel Atom platform"
date: 2008-05-30
forum: Hardware
---

### Post by El Puño on 2008-05-30
Hello

I'm considering to install the Ubuntu server on an Intel Atom ITX board.

Dispite a lot of STFG I'm not sure if Hardy support this ?

---

### Post by anontrol on 2008-08-10
I've been working with an Intel D945GCLF board trying to get a general feeling for how well Ubuntu works with it.  I'm running 2GB of RAM and 32GB transcend SSD with an Aterhos based PCI wireless card (not using the wireless for general network access).

My initial assesment was that Ubuntu + firefox = unusable.  I would get grey "I'm busy go away" screens that seemed to be associated with disk writes.  I went through the standard disk activity minimization tweeks with no improvment.  In addition the wireless card was not recognized.  I moved to Opera to continue my assesment, but still ran in to frequent grey screens because of disk activity.

On a whim, I decided to upgrade the BIOS (looks like Intel has gotten smart and is distributing their BIOS upgrade as bootable .iso images... nice).  Anyway, that help a little (boot up was faster and certain types of disk access no longer produce grey screens) and my wireless hardware was finally recognized; however, I still get occassional grey screens every couple of minutes when there seems to be a huge block of disk activity (file system journaling?).  Firefox is still pretty much unusable.

My recomendation would be to first upgrade the BIOS, then try some disk access tweeks:  [http://www.kaobear.com/2008/07/30/reduce-disk-activity-in-ubuntu/](http://www.kaobear.com/2008/07/30/reduce-disk-activity-in-ubuntu/) .  If that doesn't get the system usable, then I'd recomend looking at moving away from a journaling filesystem (but I haven't tried that yet as my system is now relatively usable under Opera).

You'd think Intel/Ubuntu would get more involved, but it's obvious that they're not particularly serious about making sure their lower end stuff is super usable.  In 12 to 18 months, these Atom based systems are going to be everywhere...

---

### Post by Xeon3D on 2008-08-31
anontrol (nice nick) - I'm almost 100% sure that the BIOS update has nothing to do with your wireless card being updated. Maybe some ubuntu updates had.

Also, I'm running the same board with a normal SATA HD and 1GB of ram. Didn't see any Gray Screens yet and I'm running Apache \ SQL \ SABNZBD for a small network (max 6 machines).

---

### Post by Euthenics on 2008-09-11
I'd like to install Ubuntu Server (Hardy) on an Intel Atom processor and possibly using Intel or Gigabyte motherboard. Looking forward to upcoming of the Atom dual core processor too very soon.

Is it really possible to run the server edition on it without any problem? I'd like to build a mini server like those Qnap, Thecus and Synology NAS.

---

