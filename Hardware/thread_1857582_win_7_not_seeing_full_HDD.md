---
title: "win 7 not seeing full HDD"
date: 2011-10-10
forum: Hardware
---

### Post by Spite91 on 2011-10-10
Ok before anyone starts on my about posting this on a ubuntu forum I have also post this within a microsoft forum. I am trying to get a desktop setup for my girlfriend However I've been having some issues. I have 2 320gb sata drives (not connected at the same time) and 1 80gb ATA drive. 1 of the sata drives has personal info on it that I'm trying to transfer to the newly restored system once its done so I cant format it. The problem is that when I was trying to format the hard drives that were in it (because they werent my own) I tried using my windows 7 disk to just format over them and I assumed they would be fine. However windows 7 couldnt see either drive at all and when I tried plugging in my personal sata it wasnt read either. All 3 of them showed up in the bios however so I tried using a ubuntu 11.04 disk. Well it saw the drives but it wouldnt let me do away with the old partitions and reformat the drive. It's hard to remember the error but I think it said something to the effect that it couldnt find a root partition or...well root SOMETHING. I did some looking online and found dban. The tool allowed me to wipe the 80gb drive which I then used the windows 7 disk on. That worked so I was gonna hook up my sata drive to get the data off of it then reformat both of the sata drives with windows 7 putting all the data on them afterwards. However when I booted up the 80gb drive with my sata connected it only was able to read 31gb on the 80gig and 147gb on the 320gig. As for the other sata it isn't seen at all, in disk management or otherwise. I've looked online and the only thing I could find was something called the LBA. Pretty sure i understand it but I figure if that is the problem the desktop wouldnt have come with a 320gb HDD. So I was wondering if anyone could give me any ideas on what to do next or if anyone has had the same problem. THanks a ton.

P.S.- I also used dban on the older sata drive and windows still couldnt see it at all. =/

---

### Post by Spite91 on 2011-10-10
Also this is off topic but I plan on making linux my primary os on my laptop and I've looked around but Its rather difficult to see the differences between the different versions so any links or overviews of them would be greatly appreciated

---

### Post by Spite91 on 2011-10-10
anybody?

---

### Post by mastablasta on 2011-10-11
hard to say since we don't know what happened to you SATA drive. also your report on error message is vague.
 
perhaps bootinfoscript can help. boot form Ubuntu LiveCd (or USB) and then download the scrip and follow insctructions here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Rubi1200 on 2011-10-11
+1 to the boot info script.

If there are problems with the drives or their partitions the script should help us troubleshoot this.

---

