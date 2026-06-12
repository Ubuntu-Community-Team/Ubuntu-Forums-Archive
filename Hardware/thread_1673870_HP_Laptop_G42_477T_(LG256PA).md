---
title: "HP Laptop G42 477T (LG256PA)"
date: 2011-01-23
forum: Hardware
---

### Post by Ananth on 2011-01-23
Wondering how well Ubuntu can run on [HP Laptop G42 477T (LG256PA)]("http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/321957-321957-3329744-3848802-3848802-4346229-5045325.html").

Specs: Intel i5 480M, 14", 4GB DDR3 1066,  500GB SATA, Intel HD, Broadcom (I guess) wireless with blue tooth

---

### Post by Skrapp_Jaw on 2011-01-24
I'm currently working on an HP g42-410us. Not a bad laptop but you may have problems with drivers at first.

[http://ubuntuforums.org/showthread.php?t=1666611](http://ubuntuforums.org/showthread.php?t=1666611) <--- Take a look here first before you attempt. You may have better luck than I did.

---

### Post by valluvar on 2011-06-18
Bought a HP g42 488TU a week ago. The notebook came with Win7 home so i had to pay the windoze tax for crap i am not going to use. HP has created 4 primary partitions in the 500 gb disk, probably to stop people from installing other OS's. At least i suspect so. So the best procedure is

1. Boot to Windoze and use the disk tool to shrink the c: partition.
2. create the backup media set (important to roll back if you need win7 or a reluctant to pay for it and format it, as in my case)
3. Delete the small HP_tools partition ( this is the way out so you have to make a call on this. this probably invalidates your warranty)
4. Create an extended partition and create 2 logical partitions within that for linux and swap inside the free space created by shrinking c:
5. The rest of the install should be flawless. Natty runs very well on the g42. 
6. the 100 odd mb freed up when you knock off the hp_tools partition will become unusable. 
7. Grub should pick up the windoze bootable partition without intervention

Good luck.

---

