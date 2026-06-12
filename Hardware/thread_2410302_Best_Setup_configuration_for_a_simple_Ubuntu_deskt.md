---
title: "Best Setup configuration for a simple Ubuntu desktop with 120GB SSD + 500GB or 1TB HD"
date: 2019-01-14
forum: Hardware
---

### Post by sunbear-c22 on 2019-01-14
A common practice for setting up a simple desktop is to use a SSD+HHD configuration, e.g. setup 120GB SSD + 500GB or 1TB HDD. In setting up Ubuntu, how should I optimize storage arrangement? I am thinking of the following options:

Option 1: Mount / and SWAP on SSD, and /Home on HDD.
The issue for such an arrangement is / typically occupies less than 20GB; this means 100GB of the SSD will not be utilized. Also, when a user is login in, the read and write speed of the HHD will severely slow down user experience and would not benefit from the fast speed of the SSD.

Option 2: Mount /, SWAP  and /Home on the SSD.
The user experience will be fast as every read write process will only be limited by the SSD speed. However, this will mean that the user storage capacity is capped at 92GB (less 20GB for / and 8GB for SWAP). The HDD can be use to back up the 92GB of the /Home drive. For a 500GB or 1TB HDD, this will mean that over 480GB to 908GB of the HD is not utilized, i.e. the HDD is under utilized. Also, such an arrangement caps the max user storage to 92GB.

Is there a way to setup a Ubuntu system such that during operation the SSD will be the main work horse and before logout or shutdown the user's data will be transfer back to the HDD? What is the best arrangement for a system with 120GB SSD + 500GB or 1TB HDD storage?

---

### Post by CatKiller on 2019-01-14
You won't need a swap partition. A swap file is fine.

You can mount your HDD somewhere and then use symlinks to access folders on that drive through your Home folder. ~/Music and ~/Downloads, say.

---

### Post by sunbear-c22 on 2019-01-14
> **CatKiller said:**
> You won't need a swap partition. A swap file is fine.

You can mount your HDD somewhere and then use symlinks to access folders on that drive through your Home folder. ~/Music and ~/Downloads, say.

Can you elaborate on the steps to do what you wrote? What is the implication on security?

---

### Post by CatKiller on 2019-01-14
> **sunbear-c22 said:**
> Can you elaborate on the steps to do what you wrote? 

So you'd install Ubuntu normally, with everything on the SSD, but use the installer to mount your HDD at /mnt/bigfatpileofstorage. The name doesn't matter in the slightest, you just need to call it something. 

Then create directories there called Music, Downloads, and whatever other bulk stuff you want stored there rather than on the SSD, or user1/Music, user2/Music, and so on, if you're doing it multi-user. 

Then make links from /mnt/bigfatpileofstorage/user1/Music to /home/user1/Music, and so on, for convenience, so that stuff that would be written to ~/Music ultimately goes on the HDD. 

> What is the implication on security?
I don't think there is any difference.

---

