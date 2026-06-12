---
title: "booting problem ubuntu 8.10"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by poolet2000 on 2009-04-09
ok. i try to boot normal my cd but i have the this error message:


[64.152004] ata4: SRST failed (errno=-16)
            ata6: SRST failed (errno=-16)
            
Buffer I/O error on device sda1, logical block 293233536


all this error is the same with differned numbers at the beginning and at the end..... 

i have raid 0 on hard drives.... i think is that my problem but i don't  know how  to fixed it....please help me.....

also i compare the ubuntu hashes of my iso before i burn my iso.. and its ok....  

thank you very much for your help....

---

### Post by ronparent on 2009-04-09
I doubt that failure to boot a live cd is related to rhe raid. Though unless it is an 'alternative cd', you can't use it to partition or mount the raid0 drive. It does sound like a cd read problem however. I wouldn't dare ask why, but I have had to burn five disks to finally install to one of my computers (on second thought, I finally had to clone the install from a working usb memory stick).

---

### Post by poolet2000 on 2009-04-09
> **ronparent said:**
> I doubt that failure to boot a live cd is related to rhe raid. Though unless it is an 'alternative cd', you can't use it to partition or mount the raid0 drive. It does sound like a cd read problem however. I wouldn't dare ask why, but I have had to burn five disks to finally install to one of my computers (on second thought, I finally had to clone the install from a working usb memory stick).


so, their is now way to install ubuntu with raid 0???
and if there is can anyone help me... 

i don't think so that the problem is on disk, because the hash of iso is good and i write it at the minimal speed.... 
 
also, ubuntu booting has many options.. you can boot live or you can install, i try from live and i try also to install but it's stuck... 
with the same error, every time... i try another think that i found on web.... i start my windows normal and i run the ubuntu cd... then ubuntu gives me 2 options 
1. to try live, the cd 
2. install via windos  

i choose 1 and then another 3 options
1. if i want to restart 
2. restart manual 
3. (this is the most importan) help me with boot

i choose 3 and cd install something on my hard drive then i try again to boot but my problem didn't fix...

---

### Post by poolet2000 on 2009-04-10
so their is nothing to do????

just to pick my 2 raid 0 drivers at normal???

---

