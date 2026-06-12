---
title: "Newbie"
date: 2008-10-29
forum: General Help
---

### Post by fossil112 on 2008-10-29
Hi.  I"m an electrical engineer (hardware) by trade and just started using Ubuntu 8.04.  I've recently downloaded Amarok for my music.  Question is: I have a slave drive installed that holds all my music.  I can't seem to find the drive when importing music into Amarok.  Any help?  Thanks in advance and I look forward to contributing!

---

### Post by Wayne_V on 2008-10-29
Slave drive?   Is it mounted (see 'df' output)?  Is it seen by the kernel (see 'dmesg | grep sd[abcd]')?

---

### Post by sdennie on 2008-10-30
If it's been automounted but you aren't sure where it lives, you could also try:

```

ls /media/*/*

```

You should know pretty quickly if/where it's mounted after that command.

---

### Post by ad_267 on 2008-10-30
Or just have a look under /media in the file browser.

---

### Post by fossil112 on 2008-10-30
Thanks for your help guys.  I'm a total rookie, so it might take me a minute to figure out what you mean.  
Amarok did end up finding the media on the second drive on it's own...I wasn't being patient enough to realize it had to "do it's thing".  
I will go ahead and follow the commands that which you posted, in order to help me keep learning. 
Thanks again!

---

