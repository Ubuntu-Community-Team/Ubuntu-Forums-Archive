---
title: "Toshiba Qosmio g20-120"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by hamil on 2006-02-12
Hello!

I recently bought a new laptop, a Qosmio G20.
I am planning to install Ubuntu on it, but first I wanted to hear if anyone have succeded with it yet?
I have heard that it is some troubles with it, due to the QosmioPlayer that is installed on an unpartitoned location of the HD, and that some of its functions is not avaliable in Linux, such as the TV-tuner etc.

Looking forward to hear something about a Linux install on these kinds of machines!

---

### Post by paxel on 2006-02-12
Hi, I know you posted it long ago - I've got Qosmio G20 and still could not install ubuntu

Have you (or anybody) found the solution?

---

### Post by hamil on 2006-02-12
Well, it is not long ago since my post... I posted this thread, almost 10 hours before your reply.. :)

I have managed to find some interesting articles about Qosmio and Linux, amongst others:
[This one]("http://www.drechsler-soft.de/de/linux/qosmio_en.php")

And [this one..]("http://linux-on-laptops.com/hosted/toshibaQosmioG20-gentoo.html")

They both states that it is some trouble with the tv-tuner...
And I really want the Qosmio Player to work, without booting up the machine...

---

### Post by CookieOrc on 2006-02-12
Well from what it looks like to me and i sure as hell not a prefession, but i get this a lot :) . Well This new technology. Everyone is comin out with the Media center editions and all that stuff. It will just take time for linux to start develop the software.

---

### Post by david_sedman on 2007-08-07
Hello
I have a qosmio f20 and i cant figure how to get the tv tuner working. I no i can be done because the makers of knopp myth use a qosmio f20 to demo there distro at trade shows. the g20 has the same tuner as the f20. I wondered if you have got your tuner working. 

I've asked at knoppmyth forum for the driver details but no one has responded. if any one can help would be greatful.

---

### Post by Akre on 2007-09-16
My girlfriend has g20.

From live cd you modprobe ahci module, then install normally.

If there are problems during boot-up (root FS not found) you need to blacklist ata_piix in initramfs. If it gets loaded before ahci , ahci will not see harddrives. If another way around, all works fine. So blacklisting module in initramfs will couse it to load latter.
Anyway, thas only if and when ubuntu does not boot after instaling it.

It seems it is alread in bugzilla:
[https://bugs.launchpad.net/ubuntu/+bug/133892](https://bugs.launchpad.net/ubuntu/+bug/133892)

---

