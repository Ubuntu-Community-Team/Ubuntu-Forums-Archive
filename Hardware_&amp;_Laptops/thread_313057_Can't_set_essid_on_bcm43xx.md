---
title: "Can't set essid on bcm43xx"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by viniosity on 2006-12-05
I've got Edgy Eft on a tablet pc and everything is working fine except the wireless.  lspci shows the bcm43xx module loaded and iwconfig confirms it is there under eth1.

But when I type (as root)
iwconfig eth1 essid "mynetwork"

It doesn't do anything.  Instead from iwconfig showing the essid as OFF it then shows the essid as ""  Has anyone see this before?  

The behavior I am used to is setting the essid, sending the wep password and then doing ifup eth1.

iwlist eth1 scanning is apparently not supported and iwconfig eth1 essid any isn't attaching to anything either.

Thanks.

---

### Post by endersshadow on 2006-12-05
I had this problem, too.  So I installed ndiswrapper.  Do note that you *must* use ndiswrapper-1.8 and not plain old ndiswrapper with Edgy. Here's how:

```
sudo apt-get install ndiswrapper-utils-1.8
sudo rmmod bcm43xx
sudo gedit /etc/modprobe.d/blacklist
```

Add this line to the end:

```
blacklist bcm43xx
```

Save and close. Next:

```
sudo ndiswrapper-1.8 -i /path/to/bcmwl5.inf
ndiswrapper-1.8 -l
sudo ndiswrapper-1.8 -m
modprobe ndiswrapper
```

Restart. Upon restart:

```
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo iwconfig eth1 essed "mynetwork"
```

Good luck!

---

### Post by viniosity on 2006-12-06
Thanks for the help.. it's mostly worked.  I think I'm getting stuck because I can't find a valid .inf file anywhere.  Through google I found a bunch of drivers but they're all .sys files and are showing up as invalid drivers when I install them.  Any idea where I can track down the correct driver?

TIA

---

### Post by justin credible on 2006-12-06
Have you tried ripping the inf files from the Window drivers? I know Prism2 chipsets that use the Prism54 firmware allows you to do that. Here's a link if your interested: [http://prism54.org/misc.html](http://prism54.org/misc.html)

---

### Post by endersshadow on 2006-12-06
You should also be able to go to your OEM's (such as Dell) web site and grab the drivers from there.  You need the .sys and the .inf file in the same directory, since ndiswrapper uses the inf to find the sys, if that makes any sense.

---

### Post by viniosity on 2006-12-06
> **endersshadow said:**
> You should also be able to go to your OEM's (such as Dell) web site and grab the drivers from there.  You need the .sys and the .inf file in the same directory, since ndiswrapper uses the inf to find the sys, if that makes any sense.

Ah, didn't realize both files were needed.  That solved it. Thanks much!

---

### Post by endersshadow on 2006-12-06
Great! Glad to hear you got it working!

---

