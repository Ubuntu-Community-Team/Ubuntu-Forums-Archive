---
title: "Modprobe(ing) after every boot."
date: 2012-03-09
forum: Hardware
---

### Post by babakott on 2012-03-09
I followed some posts and got my Netgear WMDA3100v2 USB wireless working flawlessly. The only problem I am running into is that I have to run the command ***sudo modprobe ndiswrapper*** after every boot to get it working. While its not a huge deal, I am wondering if there is a way that I can have it remain modprobed.

To be honest, I quit using Linux for sometime, and I am not even sure exactly what modprobe does (I think it adds drivers to the kernel?). I checked the man page and nothing looked like it would do what I need. 

This is probably a simple fix, but your help will be greatly appreciated.

Thanks.

---

### Post by haqking on 2012-03-09
> **babakott said:**
> I followed some posts and got my Netgear WMDA3100v2 USB wireless working flawlessly. The only problem I am running into is that I have to run the command ***sudo modprobe ndiswrapper*** after every boot to get it working. While its not a huge deal, I am wondering if there is a way that I can have it remain modprobed.

To be honest, I quit using Linux for sometime, and I am not even sure exactly what modprobe does (I think it adds drivers to the kernel?). I checked the man page and nothing looked like it would do what I need. 

This is probably a simple fix, but your help will be greatly appreciated.

Thanks.

```
sudo su
echo ndiswrapper >> /etc/modules
exit
```

Should do the trick i think, by the way i am crediting [Chilli55]("http://ubuntuforums.org/showpost.php?p=11733120&postcount=4") for this, personally i have never used ndiswrapper so this may not work.

Cheers

---

### Post by babakott on 2012-03-09
That did the trick. Much appreciated!

---

### Post by haqking on 2012-03-09
> **babakott said:**
> That did the trick. Much appreciated!

no worries you are welcome.

Peace

---

