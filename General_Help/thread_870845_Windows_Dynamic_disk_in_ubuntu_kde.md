---
title: "Windows Dynamic disk in ubuntu kde"
date: 2008-07-26
forum: General Help
---

### Post by tordaasen on 2008-07-26
Hi folks and a great warm weekend from sweden :)

I have ubuntu installed on mu computer thas was from the begining a windows file server 
with 4 st hard drives with ntfs and dynamic disks
i can acsses the other ntfs disk i have from ubuntu but not the dynamic disks. then i got a error thats bad raid and so on
so my question can Ubuntu access windows dynamic disk and if so how can i do that 
and its not a ntfs error because i can reach the other nfts disk thats not dynamic


Have a nice weekend

/tka

---

### Post by Taxman415a on 2008-07-26
I did some googling, and "dynamic disks linux" got some results.
This link: [http://www.debianhelp.org/node/2966](http://www.debianhelp.org/node/2966)
hinted that it should be possible and has some links that should be helpful to you including this one:
[http://www.linux-ntfs.org/cvs/vc/dynamic-disk/README?hideattic=0&revision=1.13&view=markup](http://www.linux-ntfs.org/cvs/vc/dynamic-disk/README?hideattic=0&revision=1.13&view=markup)
Apparently ldm (Logical Disk Manager) is the term for the partitioning scheme that dynamic disks use. I didn't see any straight answers for how to use it and I have no experience with the stuff. If no one here knows, try asking at: [http://forum.linux-ntfs.org/](http://forum.linux-ntfs.org/)
They used to have ldm documentation, but it's offline right now, I don't know why. If you have to go that route, please come back and post what you did to get it working.

Your other option is to convert back to basic discs:
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

---

