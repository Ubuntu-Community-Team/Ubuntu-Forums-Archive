---
title: "D-Link DNS-321"
date: 2009-02-14
forum: Hardware
---

### Post by ogger on 2009-02-14
I bought a NAS device (DNS-321) but cannot install it. I tried to run the install CD with Wine, but the software doesn't work. Is there another way to install this device? 

PS: I just installed Ubuntu 2 weeks ago, ie I am very new to this.

---

### Post by ogger on 2009-02-18
So I set it up in my windows partition and I can work with the NAS from my windows computers. In my Ubuntu 8.10 I can see it under network places, but I cannot see the actual folders in it. I was reading a couple of threads wrt the DNS-323, but with all the code they are way over my head. 

any help would be much appreciated.

---

### Post by ogger on 2009-02-19
Please anybody

---

### Post by ogger on 2009-02-19
OK, never mind. Suddenly it works after switching it and off again.

---

### Post by ogger on 2009-02-20
Ha, it's again not working. I figure I might need to rewrite my fstab. Is this right? Again, I see the drive from my windows machines just fine. 


I appreciate any response.

---

### Post by Keith_Beef on 2009-02-21
I'm thinking of buying a NAS, and in researching what's available I found several threads referring to mdadm... maybe that's what you need?


K.

---

### Post by ogger on 2009-02-23
I found this (a workaround, I guess): [http://ubuntuforums.org/showpost.php?p=4920136&postcount=11](http://ubuntuforums.org/showpost.php?p=4920136&postcount=11)

---

### Post by DownTown22 on 2009-03-04
I have a D-Link DNS-323 at home, and used this How-To to get it all setup on both 8.04 and 8.10 - works like a charm!

[http://www.marcus-furius.com/?p=59]("http://www.marcus-furius.com/?p=59")

---

### Post by runes on 2009-03-24
> **DownTown22 said:**
> I have a D-Link DNS-323 at home, and used this How-To to get it all setup on both 8.04 and 8.10 - works like a charm!

[http://www.marcus-furius.com/?p=59](http://www.marcus-furius.com/?p=59)


Here's my process to get the Dlink DNS-323 working on Ubuntu 8.10.  I tested with both 32bit and 64bit..tell me what you think and feel free to add your suggestions to the document.

---

### Post by FiReSTaRT on 2009-12-03
> **runes said:**
> Here's my process to get the Dlink DNS-323 working on Ubuntu 8.10.  I tested with both 32bit and 64bit..tell me what you think and feel free to add your suggestions to the document.
Thanks for the article. It worked like a charm for me. After a while, I wanted to avoid automounting the network drive and to be able to unmount it without sudo, so I dug up this article: [http://kmandla.wordpress.com/2007/03/08/howto-mounting-without-sudo/](http://kmandla.wordpress.com/2007/03/08/howto-mounting-without-sudo/)

For those of you too lazy to read it, just add "users,noauto" between "dir_mode=0777" and the 3 0's in the fstab entry.

---

