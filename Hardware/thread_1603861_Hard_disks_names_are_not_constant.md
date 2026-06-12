---
title: "Hard disks names are not constant"
date: 2010-10-23
forum: Hardware
---

### Post by snnicky on 2010-10-23
I'm not sure this is correct place to ask the question. And I do not know how to find an answer without complete description of the situation. Please forward me to a proper place.
So, the situation:

I had Ubuntu 10.04 installed. That worked fine. And I had soft raid1. In /etc/mdadm/mdadm.conf there **were** the following records:
DEVICE /dev/**sdb**1
DEVICE /dev/**sdc**1

Week ago I upgraded to Ubuntu 10.10 and the raid stopped working. During boot I saw the following screen (attached).
The text on the screen is: 
++++++++++++++
Ubuntu 10.10

&#9632;&#9632;&#9632;&#9632; &#9632;&#9632;&#9632; /media/important_data &#9632;&#9632;&#9632; &#9632;&#9632; &#9632;&#9632;&#9632;&#9632;&#9632; &#9632;&#9632;&#9632; &#9632;&#9632; &#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;

&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632; &#9632;&#9632;&#9632;&#9632;&#9632;&#9632;: &#9632;&#9632;&#9632; &#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632; <S>, &#9632;&#9632;&#9632;&#9632;&#9632; &#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632; &#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632; &#9632;&#9632;&#9632; <M> &#9632;&#9632;&#9632; &#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632; &#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;&#9632;
------------------------

As you can se almost whole text was just some squares. Perhaps that was something in Russian written with wrong front.

My guess was something wrong with the raid and <S> meant "skip mount", <M> "mount anyway". I chose <S> and was able to boot. After that I ran gparted and checked hard disks names. And found that one component of raid was sdb1 as expected while the second was **sdd**1 instead of expected **sdc**1. Ok. I modified my mdadm.conf because I decided that is something new in Ubuntu 10.10 and my raid1 worked fine after that. However in couple of days the issue appeared again. That time the component became sdc1 instead of sdd1 recorded in config file. **But** I just rebooted couple of times and didn't modify mdadm.conf. After several reboots all returned back and I was able to boot normally. I didn't append or remove any hard disks (and even any devices). There was nothing similar in Ubuntu 10.04.

To fix the problem I removed DEVICE records from mdadm.conf file. That solved the problem because by default mdadm scans all available partitions. Right now when I run sudo blkid I see
++++++++++++
/dev/sda2: LABEL="home" UUID="2113e90c-8ca6-44af-8c48-9bc5e1a24213" TYPE="ext4" 
/dev/sda3: UUID="285d01bd-0239-47a8-9e6f-5c8d2aa23771" TYPE="swap" 
/dev/sda4: LABEL="linux_root" UUID="d549b98f-c0b3-434d-9965-eaf2ec78b6c4" TYPE="ext4" 
/dev/**sdb1**: UUID="dff6e1c2-3aaa-32d2-322f-7065c9908917" TYPE="linux_raid_member" 
/dev/sdb2: LABEL="dist_and_video" UUID="470f53db-2ac9-4908-bcb0-aaebc706ab1c" TYPE="ext4" 
/dev/**sdc1**: UUID="dff6e1c2-3aaa-32d2-322f-7065c9908917" TYPE="linux_raid_member" 
/dev/sdc5: LABEL="nothing special" UUID="D2A03447A03433F7" TYPE="ntfs" 
/dev/md0: LABEL="important_data" UUID="1ad85ff1-d6a5-4d31-9e2b-633f3f46a11e" TYPE="ext4" 
----------------------

Here is my fstab file just for a case
++++++++++++
# /
UUID=d549b98f-c0b3-434d-9965-eaf2ec78b6c4 /               ext4    relatime,errors=remount-ro 0       1
# /home
UUID=2113e90c-8ca6-44af-8c48-9bc5e1a24213 /home           ext4  exec,rw

# swap
UUID=285d01bd-0239-47a8-9e6f-5c8d2aa23771 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/md0        /media/important_data           ext4    noexec,rw
UUID=470f53db-2ac9-4908-bcb0-aaebc706ab1c       /media/distribs_and_video       ext4    exec,rw
#
---------------------

Could anybody help me understand why disk names are not constant ?
Thank you.

---

