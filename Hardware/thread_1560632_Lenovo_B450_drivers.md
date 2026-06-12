---
title: "Lenovo B450 drivers"
date: 2010-08-25
forum: Hardware
---

### Post by Kanshu on 2010-08-25
I'm currently configuring my new **Lenovo B450** laptop computer and I can't seem to find a site where I can download the drivers for Linux.

Right now, default wireless networking in Ubuntu 10.04 cannot detect all available WIFI networks in my area and will sometimes return a garbled network name. But it can connect to some wireless network. It just so happen that I can access one open WIFI network in my area from my other Compaq notebook computer, but I can't do so using my Lenovo computer.

I'm also currently testing my Windows XP partition with drivers I have just downloaded, but my priority is my Ubuntu and Kubuntu partitions because those are the two I use to connect to the internet.

Anyway, is there a site where I can find drivers for my Lenovo B450 computer? Or, are there compatible generic drivers I can try?

---

### Post by clrg on 2010-08-25
I don't know if there are any sites where you can get all the drivers for your specific model. However, if you search for drivers for a certain piece of hardware, I'm sure you'll find something. If you are unsure what your laptop has got inside of it, try

```
sudo lshw
```

and

```
sudo hwinfo
```

---

### Post by Kanshu on 2010-08-25
I've been searching for hours, but I only found drivers for Windows. Anyway, I will trying to downgrade to Ubuntu 9.04 to see if it can solve my problems with equivalent drivers. This is what I have on my Compaq computer.

Incidentally, I haven't been able to have WIFI access in my Windows partition. I may have to test some more drivers today.

Thanks for the "sudo lshw" suggestion.

---

