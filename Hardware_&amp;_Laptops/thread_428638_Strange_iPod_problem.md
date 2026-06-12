---
title: "Strange iPod problem"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by fca_neo on 2007-04-30
I use Kubuntu Feisty. On Edgy my ipod worked fine but now, after doing a clean feisty install (since the update failed), my iPod refuses to automount.

As a matter of fact, the iPod mounted nicely just after installing but it stopped working pretty quickly.

The problem:
When I plug the iPod in it doesn't automount, when i go to the disk & Filesystem configuration utility it says the utility is missing. If the iPod is not plugged in, the utility works just fine.

I tried reinstalling kde guidance package, kubuntu package and I got the same behaviour. Since i did not find anything on the forums or google I'm asking it here: how can I solve this problem. I hope it is the right place.

BTW I find the the iPod support in kubuntu is a bit sketchy compared to the one in Ubuntu. Still Kubuntu is better. And please, do not answer "use Ubuntu" or something like that (I already got that answer from the staff in the past for a similar problem). I would to have like a solution for KDE/Kubuntu.

Thanks

PS: my iPod is a 1st gen 2Gb nano

---

### Post by Käferthias on 2007-05-06
I have a similar problem.
I have a fresh install of Feisty Fawn (Ubuntu) and my iPods don`t automount any more. I had Edgy on the same System. Ipods worked fine, there. I tried a simple 512MB USBstick - works. I tried to connect my 1G Nano, a 4G Ipod and a 4G Ipod Photo, but they are not recogised. 
What could I do?

---

### Post by fca_neo on 2007-05-06
I have notices almost the same problem when running the kubuntu live cd. Unfortunately, I have no clue on how to solve it and there is not much info about this anywhere.

I can mount it manually but it is rather anoying and I dont now hpow to get the permissions right for it to work with amarok
```
sudo mount /dev/sda2 /media/iPod
```

I'll try to post this question in another forum to see if I get some feedback. I'm also considering in changing the distro.

---

### Post by Käferthias on 2007-05-07
On my machine at work, where I updated to Feisty, I also had the problem. Ipod did automount, but the mountpoint changed from /media/ipod to /media/IPOD. I changed the settings in Amarok, now it works.
To do that, I had to go to settings -> configure Amarok -> Media Devices then remove the "old" Ipod, add it again and type in the correct mountpoint.
 
At home, my ipods are not mountable, even manualy.

---

