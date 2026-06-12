---
title: "hal/policykit not allowing user access to USB HD"
date: 2008-10-16
forum: General Help
---

### Post by wayover13 on 2008-10-16
Have xubuntu 8.04 installed. Recently hooked up an internal HD using an IDE-to-USB adapter. Hal would detect and mount it, and put an icon representing it on the user's desktop. But the user couldn't do much with the mounted drive, i.e., no write access, not allowed to unmount, etc. Root and sudo'ing gets full access to the mounted drive. 

I fiddled around with making some udev rules to allow the user full access but that was unsuccessful (undid all changes there). Then I understood the PolicyKit might be causing problems, so I fiddled a bit with that. First, I tried modifying the /etc/PolicyKit/PolicyKit.conf file. I did not succeed in getting the drive writeable like that. I made one crucial mistkae while doing that: I edited the /etc/PolicyKit/PolicyKit.conf file without first making a backup. So I'm not sure I restored the file to its original condition. On that note, could someone please post here a virgin copy of the /etc/PolicyKit/PolicyKit.conf file so I can see if I've restored mine to its original condition?

In addition, I need tips on how to get this drive writeable by my user. The problem seems to be that the auto-mounting system is seeing it as a fixed drive and does not want to give unpriviledged users full access to fixed drives. It shows up as /dev/sddX, btw. Input will be appreciated.

James

---

### Post by wayover13 on 2008-10-17
I've discovered after having edited the PolicyKit.conf file (not being certain that I returned it to its previous state after having edited) that my system will no longer suspend or hibernate. I suspect the problem may be related to some error I introduced into /etc/PolicyKit/PolicyKit.conf . Once again I'd like to request that someone please post here the content of their stock PolicyKit.conf file so I can check whether I introduced some error. Your help in that regard will be much appreciated.

Thanks,
James

PS Once I get that straightened out I'll try to work out the disk mounting problem I addressed above.

---

