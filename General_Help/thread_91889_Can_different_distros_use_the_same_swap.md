---
title: "Can different distros use the same swap?"
date: 2005-11-18
forum: General Help
---

### Post by commodore on 2005-11-18
Can different distros use the same swap?

---

### Post by Pablo_Escobar on 2005-11-18
AFAIK there should be no problem in sharing swap between distros.

---

### Post by slux on 2005-11-18
Of course they can. The only situation I can think of where this might not be possible is if the other one is using a really old kernel (2.2 I think) while another's got the latest.

---

### Post by yaraju on 2005-11-18
Just wanted to bring to your notice...
If you have a common swap space, and hibernate on one distro, you had better not access the other distro before you get the first out of hibernate. Or, u'll end up messing up the hibernate, which, the last time I tried it, made hibernate malfunction even on subsequent trials. Someone do test this to confirm it.

---

### Post by commodore on 2005-11-18
If I put my /home directory on a separate partition, can OS-s share it? I don't actually need this but it's interesting to know.

---

### Post by matthew on 2005-11-18
Sharing a swap is fine if you aren't planning to use hibernate. I'm doing it on my testbox right now (Debian Sid and Ubuntu Dapper).

Sharing a /home can be done but isn't a good idea. Each OS will put hidden folders into the /home that contain various configurations and so on and it can make one OS work great and the other have problems or other variations on that theme. A better idea would be to make smaller /home partitions for each OS and then a large shared partition for files, etc. that you would want to use in both.

---

