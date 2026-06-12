---
title: "&quot;failed to determine the codename of the release&quot; issue 8.04.2 Hardy Heron"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by dblagbro on 2009-06-18
OK after spending the last 24 hours trying to figure this error message out I found the cause and can't believe someone else didn't run into this so I'm posting it for others that may have this problem.

Installing AMD64 version of Ubuntu Server 8.04.2 (Hardy Heron) I kept getting "failed to determine the codename of the release" messages from Debootstrap while in the "installing the base system" of the setup.

The issue was that right after entering setup, at the network selection part I was changing the hostname of the machine to continue with the install.  DON'T DO THIS... leave it as "ubuntu" and you will be prompted to later select the permanent hostname of the machine.

I had searched and searched and found nothing for "ubuntu 8.04.2 failed to determine the codename of the release" from Google or this forum (at least nothing that worked, my memory tested ok and the CD-ROM passed integrity check) so I hope this helps someone....
-d

---

### Post by brunobueno on 2009-07-06
Hi,

I also had this problem today, and your workaround has saved me.
I got the same error message (Failed to determine the codename of the release) when I was installing a Ubuntu 8.04 Server. I am going to use this as firewall test server.

One thing that I think is relevant, is the size of the hostname. I was trying to use the name " TESTE-FIREWALL ". So, when I saw your post I restarted the installation and just put the name " FIREWALL " on hostname field and the system was installed without errors.

So, thanks for your post, it was a very good help !

Bruno Bueno

---

### Post by Ian-on-the-Trent on 2009-07-08
I tried the suggestion, keeping the hostname as Ubuntu. Unfortunately, this did not prevent the Debootstrap Error. Note that I am trying to install Ubuntu 9.04.  I'm going to give Xubuntu 9.04 alternate a try now.

System: Acer 213TE laptop
CPU: Celeron 850mhz
HDD: IBM Travelstar 20GB
RAM: 256MB (another 128mb stick to be added)

*(And yes, why hasn't this install issue been discovered by others?)*

---

### Post by Ian-on-the-Trent on 2009-07-09
I referred to [http://www.debianhelp.org/node/2031](http://www.debianhelp.org/node/2031).

I wondered if my DVD/CD-ROM was acting odd after I tried various Linux installs over the past couple of years.  (Never a problem installing XP). So I noticed a mention in the above link about the DVD/CD drive being too old. Well, I replaced the drive with a newer one and lo and behold the install completed...no debootstrap errors.

Now, I had replaced the hard drive and RAM previously so I'm not entirely sure if the previous unsuccessful installation attempts can be completely blamed on the CD-ROM. But I suspect that the debootstrap error was.

---

