---
title: "New question related to &quot;PCI: cannot allocate resource region ...&quot;"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by pmilin@ptt.yu on 2006-10-23
Hi all,
There are many threads related to the problem of allocation of the resource region. For example:
[HTML]http://www.ubuntuforums.org/showthread.php?t=265132[/HTML]
[HTML]http://www.ubuntuforums.org/showthread.php?t=2544[/HTML]
There was even mine with no answer at all:
[HTML]http://www.ubuntuforums.org/showthread.php?t=243453[/HTML]
Since I have HP nx8220, I saw on the HP site a patch for PCI bus Scanning:
[HTML]http://h18007.www1.hp.com/support/files/server/us/download/8904.html?jumpid=reg_R1002_USEN[/HTML]
However, this patch is for Linux systems running on the 2.2 Kernel, and I have latest Ubuntu 2.6.15-27-686. So, my question is, since I am far from an expert, can I use this patch? And, how to rebuild the kernel, as manual requires for the last step?
Sincerely,
Petar Milin

---

### Post by xyz on 2006-10-23
Hi,
I've got that "cannot allocate...", too and have never found an answer to solve it. However, as far as I can tell, it doesn't seem to interfere/cause major problems. As you posted, most threads about it remained unanswered.

Are you experiencing major pbms because of it?

---

### Post by pmilin@ptt.yu on 2006-10-23
Yes, you are so right! But, what about the possibility to use the patch I asked about? Do you have HP laptop?

Best,
Petar Milin

---

### Post by xyz on 2006-10-23
I did check out your link:
>  	
HP ProLiant DL580 Server
HP ProLiant DL380 Server
HP ProLiant DL360 Server
HP ProLiant DL320 Server
HP ProLiant ML570 Server
HP ProLiant ML530 Server
HP ProLiant ML370 Server
HP ProLiant ML350 G2 Server
HP ProLiant ML350 Server
HP ProLiant ML330 Serve

These HP's seem to be supported. You didn't mention your exact model. Is yours in that list?

---

### Post by sedd on 2006-10-23
I don't think you can use a 2.2 patch on a non-2.2 kernel. 2,2 is pretty old. I think you're outta luck.  Does this PCI resource region cause problems for you? I get this error too on my HP laptop, but I'm not sure what effect is has. Maybe none. I can't get suspend or hibernate to work, but who knows if that's related.

---

### Post by pmilin@ptt.yu on 2006-10-24
You are right, again. Sorry!
I have HP nx8220. Hence, it is not on the list. Nevertheless, can I use the patch? The answer is, probably, not.

Best,
Petar Milin

---

### Post by xyz on 2006-10-24
> **pmilin@ptt.yu said:**
> You are right, again. Sorry!
I have HP nx8220. Hence, it is not on the list. Nevertheless, can I use the patch? The answer is, probably, not.

Best,
Petar Milin
sedd's probably right; it's a bit old but would it hurt to try? Can always remove it afterwards! I'm one  to think we should just try!

Make a system backup and restore it the way it was prior to applying the patch in case of problems.

to sedd...I don't know if the laptop issue in my sig can be of any help to you (Sudpend/Hibernate Laptops); all I can say is that it worked wonders for me. (Toshiba Satellite A 40). According to the link, it should work on most laptop. To resume from Suspend, I just press on the power button.

---

