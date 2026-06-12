---
title: "Backup Laptop HDD with Multi OS?"
date: 2009-01-02
forum: Hardware
---

### Post by Mursalin on 2009-01-02
Hi ..
I have an HP Pavilion dv2680ee laptop with two OSes inside (Ubuntu 8.10 and Vista Home Premium). But there is a problem that I still can't figure out: I want to back up all my laptop hard disk drive, and copy all of that image to a Desktop PC. I mean ALL, includes those Ubuntu and Vista partitions and the data partition too. I hear about Acronis software, but am not sure how to use it. 

Anyone here can help/guide me?  At least a link or URL to a web page for me to read. 

Here's my laptop details:

HP Pavilion dv2680ee 
160 GB HDD, splited into 6 partitions:
1. a C: NTFS drive for Vista OS,
2. a D: NTFS drive for Windows data (accesible from Ubuntu),
3. a E: NTFS drive for HP Recovery,
4. a /dev/hda5 for swap,
5. a /dev/hda6 ext3 for Ubuntu (codename Intrepid Ibex),
6. a /dev/hda7 ext3 for Linux data drive.

Thanks.

---

### Post by logos34 on 2009-01-02
**dd** is the simplest way--one command: basically just do

> dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror


[http://wiki.linuxquestions.org/wiki/Dd#Clone_a_harddisk](http://wiki.linuxquestions.org/wiki/Dd#Clone_a_harddisk)
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by handydan918 on 2009-01-02
> **logos34 said:**
> **dd** is the simplest way--one command: basically just do



[http://wiki.linuxquestions.org/wiki/Dd#Clone_a_harddisk](http://wiki.linuxquestions.org/wiki/Dd#Clone_a_harddisk)
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Really? It looks to me like that will just write the contents of the first drive over the contents of the second drive. From my reading of the OP, I doubt that's what they want...

---

### Post by logos34 on 2009-01-02
> **handydan918 said:**
> Really? It looks to me like that will just write the contents of the first drive over the contents of the second drive. From my reading of the OP, I doubt that's what they want...

Well, what do you suggest?

---

### Post by handydan918 on 2009-01-02
> **logos34 said:**
> Well, what do you suggest?

I'd suggest giving the OP a dd command that will write across the network to his desktop box, like he said. 

Or the op could try rsync/grsync.

dd scares hell out of me. Far too easy to hose everything.

---

### Post by logos34 on 2009-01-02
> **handydan918 said:**
> I'd suggest giving the OP a dd command that will write across the network to his desktop box, like he said. 



ok.  Netcat + dd command will do the job (the ENTIRE drive vs. partition-by-partition) very simply.  Basically:

> # netcat -p 2222 -l |bzip2 -d | dd of=/dev/sdb

[http://www.cyberciti.biz/tips/howto-copy-compressed-drive-image-over-network.html](http://www.cyberciti.biz/tips/howto-copy-compressed-drive-image-over-network.html)
[http://www.novell.com/coolsolutions/feature/19486.html](http://www.novell.com/coolsolutions/feature/19486.html)

rsync would work fine too, like you say

---

### Post by Mursalin on 2009-01-02
> **handydan918 said:**
> I'd suggest giving the OP a dd command that will write across the network to his desktop box, like he said.. dd scares hell out of me. Far too easy to hose everything
Yes handydan918, You got my point there :) 

> Or the op could try rsync/grsync.
I will do a reading of this two commands too, many thanks to You.

> **logos34 said:**
> ok.  Netcat + dd command will do the job (the ENTIRE drive vs. partition-by-partition) very simply.  Basically:
> # netcat -p 2222 -l |bzip2 -d | dd of=/dev/sdb
[http://www.cyberciti.biz/tips/howto-copy-compressed-drive-image-over-network.html](http://www.cyberciti.biz/tips/howto-copy-compressed-drive-image-over-network.html)
[http://www.novell.com/coolsolutions/feature/19486.html](http://www.novell.com/coolsolutions/feature/19486.html)

Hi logos34.. sorry for my late reply. And many thanks for your help and your refering me those links. I'm going to give it a try. 

I appreciate your support guys :)

[Moderator, You may consider this as a solved thread]

---

