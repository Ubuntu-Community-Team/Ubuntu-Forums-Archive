---
title: "SWAP - is it necessary?"
date: 2008-08-11
forum: General Help
---

### Post by Krupski on 2008-08-11
Hi all,

I've got a network file server (no video or keyboard, just network cable and power) running Ubuntu Server 64 bit and 8 gigabytes of DDR-2 memory installed.

The OS is installed on a 4GB Compact Flash card which is setup 2GB for Ubuntu and 2GB for swap space.

Here's a listing of current memory usage I just did:

```

root@storage:/# free -kolt
             total       used       free     shared    buffers     cached
Mem:       8113368    8069188      44180          0      40596    7930324
Low:       8113368    8069188      44180
High:            0          0          0
Swap:      2000084        196    1999888
Total:    10113452    8069384    2044068

```

Note that RAM is almost completely spoken for (normal) and there is barely any swap space used.

The only reason I setup a swap partition on the CF card in the first place was that during install, the partitioner wanted me to make it!  :)

I've run the server box without any swap and it seems to work just fine.

So, my question is... do I NEED a swap space given that the box has 8 gigs of ram in it?

I want to replace the 4GB compact flash card with a 2GB card and use the 4GB card for my camera (i.e. I don't want to have to buy another CF card)!!!

Any info about swap space and it's importance will be greatly appreciated!

Thanks!

-- Roger

---

### Post by mc4man on 2008-08-11
> do I NEED a swap space given that the box has 8 gigs of ram in it?

Personally i don't think your going to need it. 
While i don't have any exp. with the type of setup your running you could also keep in mind the linux swap partition doesn't have to be on the 'drive' the Os is installed to.

for ex. here hardy is installed to /dev/sdb3, and the swap is installed to other drive /dev/sda5
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=622a0b49-e4a4-41bb-b871-1d1291b46905 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a6b48647-b3cd-4e76-9a83-f912dbd503c8 none            swap    sw            

---

### Post by jerome1232 on 2008-08-11
Looks like you are using almost no ram
```

   total: 8113368
- cached: 7930324
---------------
           183044
```

that's only ~183 MB used of ram right. So I'd say its safe to assume you will never need to dive into swap. Correct me if I'm wrong though.

---

### Post by Ryadt on 2008-08-11
If you are using over 1GB RAM, I don't think that swap is really needed.

---

### Post by sayakb on 2008-08-11
Swap contains the RAM overflows. Try disabling the swap partition and see if it affects your performance. Assuming /dev/sda2 is swap:
```
sudo swapoff /dev/sda2
```
Personally, you would never actually need RAM unless you want to suspend to RAM/disk.

---

### Post by Taxman415a on 2008-08-11
You don't need it, there's just some good reasons to have it.
Swap can increase your performance even if you have plenty of memory "by allowing unused memory to be replaced with often-used memory." from this link: [http://kerneltrap.org/node/3202](http://kerneltrap.org/node/3202) which is a little old, but I don't think that part has changed, that's standard virtual memory algorithms.

Another good link to read: [http://www.linux.com/feature/121916](http://www.linux.com/feature/121916) though it didn't seem highly authoritative. He jsut mentions the system will crash if it runs out of memory without swap. I'm not sure how that's different than if you run out with swap since swap is just virtual memory, but maybe it has to do with the Out of Memory killer acting differently. I dunno. You'd have to do more research if you wanted a definitive answer.

Finally a way to combine both perhaps is to run your swap in memory. This lets the vm run the way it is designed and is fast. Here's a link discussing that a bit, though I'm not sure they are doing it the "right way". [http://blogs.smugmug.com/don/2008/05/01/mysql-and-the-linux-swap-problem/](http://blogs.smugmug.com/don/2008/05/01/mysql-and-the-linux-swap-problem/)

Finally, anytime you don't have as much swap as used ram you can't suspend as I understand it. But if that ever became an issue you could create a swap file and use it for swap. There is no need for a swap partition compared to a swap file.

The links I gave I got from googling for 'linux swap required'. Other combinations of similar terms and more extensive searching may get you more up to date and or definitive answers.

---

### Post by Krupski on 2008-08-11
> **mc4man said:**
> Personally i don't think your going to need it. 
While i don't have any exp. with the type of setup your running you could also keep in mind the linux swap partition doesn't have to be on the 'drive' the Os is installed to.

for ex. here hardy is installed to /dev/sdb3, and the swap is installed to other drive /dev/sda5

Oh yes.. I know that the swap space doesn't have to be on the same drive as the OS. The reason I did it was to keep ALL of the OS on the compact flash card and use the two hard drives SOLELY as data storage space.

Another reason is that I can use 'dd' to make a binary image of the entire CF card and, if I make a mistake, I can just pop out the CF card, stick it into my PC and copy a "last known good" image back to it.

Whenever I plan to make a change to the system (or try something that I'm not 100% sure about), I first make a backup of the CF card and save the image on my Windoze machine.

If I screw up, the fix is 5 minutes away!  :)

---

### Post by Krupski on 2008-08-11
> **Taxman415a said:**
> You don't need it, there's just some good reasons to have it.
.....various links......


Thanks! I'll read those!

-- Roger

---

