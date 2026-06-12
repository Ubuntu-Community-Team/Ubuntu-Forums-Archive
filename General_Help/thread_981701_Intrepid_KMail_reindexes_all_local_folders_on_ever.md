---
title: "Intrepid: KMail reindexes all local folders on every mail check"
date: 2008-11-14
forum: General Help
---

### Post by Xianath on 2008-11-14
I use a combination of dIMAP and local folders. As of the last KMail crash, it would go on and reindex(*) ALL of my local folders as soon as any mail hits them by means of a filter. This is rather ridiculous behavior of course, but is also exemplified by the fact that I have 22G of local mail. This makes KMail, and actually mu computer, quite unusable. I am down to basic OWA with zero filtering (on a 500+ mails/day mailbox) until this is resolved. Please help!

/home is an xfs partition mounted rw,noatime, if that makes a difference.

Thanks,
Peter

(*) I *assume* it reindexes mail based on lsof output and the fact that /proc/<pid>/io clocks just over 23G each time I check mail

---

### Post by Xianath on 2008-11-14
Help? Please? Someone? Look at these stats, this is unbelievable:

ppopov@ppopov-laptop:~$ cat /proc/20295/io
rchar: 98674809850
wchar: 1403447374
syscr: 5215007
syscw: 2173019
read_bytes: 90301657088
write_bytes: 993431552
cancelled_write_bytes: 28233728

I have been unable to use my laptop for the last 10 hours! And KMail crashed again... I am being pressed to explain why my OS of choice can't cope with the simple task of reading and writing email. If I can't fix this today I'll have some very serious problems at work and will be forced to abandon KMail or even Linux. :(

Any ideas welcome.

Thanks,
Peter

---

