---
title: "Mounting problem with  WBFS partitioned  USB disk"
date: 2011-03-13
forum: Hardware
---

### Post by banff2010 on 2011-03-13
I am still in 10.04.

I can see all the partitions in  WD Passport (320GB, USB) through disk utility, but it just auto mount the smartware partition  when I connect. When tried to mount it using another GUI package (disk mount, I think ), it keeps saying that disk is not connected. I was ready to wipe out dual mounting with  XP and install 10.10, but this is troubling me.

Thank you in advance.

---

### Post by banff2010 on 2011-03-15
I upgraded it to 10.10, but I still can't mount the partition. I am talking about the 157GB partition in the attached screenshot. I must be missing something really obvious. The funny thing is I have dual booting on the same machine and XP recognise it.

---

### Post by banff2010 on 2011-03-18
I am marking it as solved as there is no solution. The software that recognizes wbfs partitions will recognize them if you change the permission appropriately. For example  wiibafu would work if you use > sudo chmod 666 /dev/sdc1  where /dev/sdc1 is the wbfs partition. This is not a clever solution nor its mine, but it works.

---

### Post by Neobuntu on 2011-05-12
chmod on my wbfs drive did not work. 

None of the other WBFS (Linux) managers work, without large investments of time.

I'm going to punt; and download and run live Ubuntu 10.04 ISO (on USB with MULTISYSTEM), and reload the old Wiithon that way. 

This is a downhill sign, for Ubuntu. Just stating a fact. You can not tear down and rebuild everything, every Six months. That doesn't work. you just wind up with perpetually buggy, non-built-out systems. We don't, just need email, and a web browser. We need it all. The definition of insanity, they say, is doing the same thing over, and over, and expecting a different result. How many Six month cycles does it take, to catch a clue? Does (Dollar)Bill gates, secretly own Ubuntu, or what???
[B]
**ADD:** I just installed "WBFS filemanger"; on an old windows notebook, and got the real work done, that way. WINE, may be another option for Ubuntu 10.10, as I read it should work with WBFS Filemanager (3.0). If any of you don't know me by now, I'm the world biggest open software (OS) fan. This is no troll, it's current reality. The Wiithon program on 10.04 was faster than Windows managers (as this transfer is about 1/4 done, I can see it's slower). 

Therefore, with Ubuntu 10.04 this had Windows beaten. Then, we lost it. Too many issues. Seems 10.10 is back at square one, and meanwhile my 10.10 is begging me to update to 11.04. I ALREADY tested that, and I know it doesn't work for me! Compiz and Unity (3D) do not work, and right there where they ARE, with 10.10.

Lets keep begging the world, to run our broken experiments, and see how that works out. Yeah; not![/B]

---

### Post by mansion12 on 2011-12-25
I found a working solution [here]("http://www.wiihacks.com/wiihacks-newbie-discussions-forum/77687-confused-about-wbfs-partition.html"):

"Actually there is a very good WBFS manager for linux which can be found here:
[wbfs-manager_0.1.11-1_i386.deb]("http://www.mediafire.com/?tckzdnonz44")

Its a .deb file. I used it before and it works great but you cant pull the .wbfs off the WBFS partition, that is actually the reason I started this thread. To use it you need root access.

sudo /opt/linux-wbfs-manager/wbfs_gtk

niidmiiwii"

I am using Ubuntu 11.10.

---

