---
title: "help clamav found trojan in virtualbox"
date: 2008-09-22
forum: General Help
---

### Post by tjwoosta on 2008-09-22
i decided to run a clamscan today because i often share files with a windows machine (and its been about 6 months since the last time)

to my surprise ClamAV found a Trojan in my virtualbox thats running XP

```

tj@tj-laptop:~$ sudo clamscan -i -r /
LibClamAV Warning: Bad compression in flate stream
LibClamAV Warning: Bad compression in flate stream
//home/tj/.VirtualBox/VDI/XP.vdi: Trojan.KillCMOS FOUND

```

i dont know if its actually safe to have clamav remove the file or will i lose my whole virtualbox install?

notice the infected file is XP.vdi

(that is the XP virtualmachine itself)

so how can i find the actual trojan without deleting the whole .vdi?

i have scanned the virtual machine from within with Avast Pro but it found nothing


also does anybody know what "LibClamAV Warning: Bad compression in flate stream" means?

---

