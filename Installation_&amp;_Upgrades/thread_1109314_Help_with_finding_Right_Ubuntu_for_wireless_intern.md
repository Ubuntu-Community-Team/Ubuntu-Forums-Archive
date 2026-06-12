---
title: "Help with finding Right Ubuntu for wireless internet"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by Capital E on 2009-03-28
**I have KDE 8.10 right now, and using WINE or ndiswrapper is not helping it. Plus I kinda like the UBUNTU design better than KDE. Oh, and Open Suse sucks for me.** I use to have Windows xp sp3, but I just installed KDE 2 days ago.....***I'm very new to linux.***



Sooooooooo

I was reading the forums for ubuntu, and they said if any of the files did have a "exe" file, then it should work with WINE. All wine did was open it, and install it. I don't know if it installed the programs to be SAVED .......but it all didn't work.

[B][SIZE="4"]
Anyway, here are my Specs for my Laptop:[/SIZE][/B]
[LIST]
[*]amd athlon processor
[*]512 MB RAM
[*]ATI RAGE mobility
[/LIST]


[U]
I really want my Belkin G wireless card to work, and Linksy Router to work on it too (it's encrypted, so I gota use a exe. file to transfer the password through USB and all that stuff).[/U]

[http://www.walmart.com/catalog/product.do?product_id=2470289](http://www.walmart.com/catalog/product.do?product_id=2470289)


[http://www.walmart.com/catalog/product.do?product_id=3163627](http://www.walmart.com/catalog/product.do?product_id=3163627)


[SIZE="6"]HELP!!!!![/SIZE]
:confused::confused::confused::confused::confused:

---

### Post by cariboo on 2009-03-29
It may be that the driver for your wireless device is already loaded. You have to open a terminal, I'm not sure where it is located, so you'll have to look through the menus for something called kterm, then type:

```
sudo lshw -C network
```

and paste the output in your next post.

Jim

---

### Post by Mark Phelps on 2009-03-29
Not a Wine expert, but I really doubt using Wine is going to fix your networking problem ...

Two other Linux distros that claim to be better with autoconfiguration of wireless networking are PC Linuux OS and Mint.

You can find both on distrowatch.com.

Personally, I was unable to get wireless working on an older laptop, even after NDISwrapper and a lot of hacking, so I installed PC Linux OS 2007 -- and it loaded NDISwrapper for me, and wireless worked from the getgo.

---

### Post by SuperSonic4 on 2009-03-29
Mandriva has good hardware support too - PCLinuxOS is a fork of mandriva.

Although the new Mandriva will be released in 1-2 weeks from now

---

