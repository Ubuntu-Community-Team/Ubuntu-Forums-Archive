---
title: "SSD + Encrypted LVM + TRIM"
date: 2012-02-18
forum: Hardware
---

### Post by kurci2 on 2012-02-18
Hi everybody.
I am wondering if anyone here own SSD.
I am just about to buy one, but when i googled a little, i found out that it is very imoprtant that you have TRIM support of SSD.
Well, my chosen SSD does support TRIM, but i use encrypted LVM. As far as i get the think i can not permanently enable TRIM.
According to this sice: [http://code.google.com/p/cryptsetup/wiki/Cryptsetup140](http://code.google.com/p/cryptsetup/wiki/Cryptsetup140)

I will of course wait till Ubuntu 12.04 (with kernel 3.2 and newer cryptsetup) is finished.

My question is (if anyone knows anythink about that) if there is a possibility to enable TRIM on encrypted LVM on SSD?
If it is not...Is a SSD good choice?

---

### Post by kurci2 on 2012-02-19
bump.

---

### Post by kurci2 on 2012-02-19
one last try...

---

### Post by nariub on 2012-03-10
quick look about says encrypted LVM and SSD are not currently compatible.
so went basic and just encrypted my home dir...

so it goes..

---

### Post by Ceiber Boy on 2012-05-11
Found this: [http://superuser.com/questions/124310/does-luks-encryption-affect-trim-ssd-and-linux](http://superuser.com/questions/124310/does-luks-encryption-affect-trim-ssd-and-linux)

The short story seams to be that TRIM is ineffective for encrypted volumes, as encryption fills the drive with random data so an attacker dose not know where to look, consequentily meaning that there is nothing to trim!

Amyone else?

---

### Post by nariub on 2012-05-11
[http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html]("http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html")

URL explains how to turn it on in 12.04
usefull or not, I would like to amend my previous remarks to say that is is now available in 12.04

---

### Post by kurci2 on 2012-05-11
well, i have just ordered Verbatim SSD 128 GB, so if this works, i'll mark thread as solved =)

---

### Post by Ceiber Boy on 2012-05-11
> **kurci2 said:**
> well, i have just ordered Verbatim SSD 128 GB, so if this works, i'll mark thread as solved =)

I've also purchased one on online and awaiting it's arrival, my plan is to install 12.04 with encrypted LVM. I'll enable TRIM as described in the URL of the previous post to yours.

Please let us know how you get on, as I'd be interested to read how it goes.

Thanks.

---

### Post by kurci2 on 2012-05-11
yeah sure.
i'll get SSD in next two weeks and than i'll start working on it

But i think taht i'll install Kubuntu 12.04 (i hope it is good).

---

### Post by kurci2 on 2012-05-19
OK!
I installed Kubuntu 12.04 encrypted lvm.
Than i followed instructions on page [http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html](http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html) and everything works great.
around 4 sec boot time =)

i have also fixed "no video mode activated" error: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802/comments/24](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802/comments/24)
but now i have really ugly and not properly shown splah screen... After i press escape twice, it is as it should be...

But in general, everything works cool.
Does anyone know fix for ugly splash screen??

---

### Post by Ceiber Boy on 2012-06-16
> **kurci2 said:**
> OK!
I installed Kubuntu 12.04 encrypted lvm.
Than i followed instructions on page [http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html](http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html) and everything works great.
around 4 sec boot time =)

i have also fixed "no video mode activated" error: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802/comments/24](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802/comments/24)
but now i have really ugly and not properly shown splah screen... After i press escape twice, it is as it should be...

But in general, everything works cool.
Does anyone know fix for ugly splash screen??

What a result my TRIM works perfectly

Thank you

---

### Post by nariub on 2012-06-18
For those of you who want a hint at the secret sauce

Everybody knows to add discard to /etc/fstab
noatime, nodiratime, are optional  discard is the TRIM bit..
example
> /dev/mapper/volumegroup-root    /    ext4    discard,noatime,nodiratime,errors=remount-ro    0    1

The exception for encrypted harddrives is an edit of /etc/crypttab
you have to add discard to the crypttab too
example

> sda5_crypt UUID=e364d03f-[...]6cd7e none luks,discard
Lastly, rebuild initramfs
> sudo update-initramfs -c -k allPlease note this is the short version and the referenced URL does give a more complete answer

---

