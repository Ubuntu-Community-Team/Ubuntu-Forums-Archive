---
title: "Laptop running too hot under 12.04"
date: 2012-09-22
forum: Hardware
---

### Post by rem18 on 2012-09-22
I have a Samsung 305v this uses duel graphics on a AMD A8.
Under 11.10 I had to re-install the Radeon driver everytime I updated a drag but it worked.

Now with 12.04 the Ubuntu driver seems to work ok.
But the laptop is burning. It was hotish with 11.10 but with 12.04 its burning and the battery lasts only about 1 hour.
I guess the graphics are running very high.
Has anyone else experienced this or can offer a solution if not to keep Ubuntu I will end up burning the computer.
Thanks

---

### Post by BigSilly on 2012-09-22
You might wish to [give this a shot]("https://launchpad.net/~voria/+archive/ppa"). It didn't solve my particular problem, but it may fix yours. :)

---

### Post by rem18 on 2012-09-22
Thanks
So many there I dont know where to start.
I am monitoring temperature and just tried this.
But I dont actually know what a good temperature would be for my laptop.

maybe below is good for you_

sudo nano /etc/rc.local
chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

---

