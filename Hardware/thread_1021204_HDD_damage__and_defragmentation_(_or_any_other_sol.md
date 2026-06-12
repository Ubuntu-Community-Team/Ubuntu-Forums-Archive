---
title: "HDD damage  and defragmentation ( or any other solution?)"
date: 2008-12-25
forum: Hardware
---

### Post by eniss on 2008-12-25
I've seen a lot of threads on defragmentation, telling "ubuntu does not need defrag.". but it is a special situation:

My notebook fall over 1 meter and some parts of HDD was damaged (still it works). Then 3 months ago, I formatted HDD, installed ubuntu and started using it. Day by day it slows down, and could not mount HDD sometimes, could not write it on (depending on the damage surely). 

So I formatted it again and installed ubuntu now. I need to deactivate these bad sectors on HDD, and never use them in anyway. And I know defragmentation as a solution. If any defrag tool (with manual ) could help me? or any other solution exist for it?

Thanks.

---

### Post by anagor on 2008-12-25
Apart from the obvious statement, that your HD is probably dying and will give up soon, you can try the fsck tool.
Of course it will properly work only on unmounted drive, so the best action would be:
start from live cd.
open a terminal there and write:

sudo fsck -cf /dev/<partition>

where <partition> is the name of the partition on the disk you want to be checked.

the "c" option will check for bad blocks and mark them as that, the "f" option will force the check no matter if the system thinks the disk is ok or not.

hope this helps.

---

### Post by eniss on 2008-12-25
Thanks.

---

### Post by jovani on 2008-12-25
I had the same problem while running under windows xp 1.5 years ago.
I tried to format my disk but widows went up to 10 g and then stuck. I then made a 10g partition where i put my system. With windows disk manager i made 2 more partitions. After the 10g there was an area nearly 2g that windows could not read. I left then unformated and then i formated a new partision of 8g and went on. After a very long time i fixed my disk like this, 10g - filesystem, 2g-unformated, 8g-second disk, 5g-unformated,
25g-third disk, 10g-unformated.
The unformated areas cannot be seen by my computer.
My laptop is still running with no problems. I have put ubuntu now but i am new and i dont mess with such things yet. It still works with 3 disks.
I say this because i think the last 10g are not all damaged but i could not have more than 3 active partitions under windows xp.

---

