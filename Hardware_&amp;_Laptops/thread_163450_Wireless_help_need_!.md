---
title: "Wireless help need !"
date: 2006-04-20
forum: Hardware &amp; Laptops
---

### Post by Blacktalon on 2006-04-20
Hello,
  Well here is my problem I have a Broadcom wireless card intergated into my laptop.  And I been trying for about 5 hours but no success, I looked in my devices and see alot of unknown stuff and one of them is my Wireless, I was able to figure this out by it saying for the vendor title thing Broadcom.  But the thing is how do I get my Laptop to see my wireless card, and not as a unknown?


Any idea's guys.

Thanks,
  ~Blacktalon

---

### Post by verbalshadow on 2006-04-21
Ok you mostly likely are going to have to use Ndiswrapper following the link:
[Breezy ndiswrapper driver]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28WifiDocs%2FDriver%29")

but if you are on dapper you can try the new bcm43xx driver

[Dapper bcm43xx drivers]("https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?highlight=%28WifiDocs%2FDriver%29")

You will need a uncompressed copy of the windows driver files for both drivers, for different reasons.

---

### Post by Blacktalon on 2006-04-21
Yeah, I have used the ndiswrapper, and it says I have a driver present but it doesn't seem to see the hardware.  Any Idea on how to get it to see the hardware, I didn't see anything on how to get it to detect the hardware on the sight for Breezy.


Thanks,
  ~Blacktalon

---

### Post by verbalshadow on 2006-04-22
this probably a stupid question but have you added the module to the system
```
sudo modprobe ndiswrapper
```

to make it premanent do this

```
sudo gedit /etc/modules
```
the add ndiswrapper below the last line.

---

### Post by Blacktalon on 2006-04-22
I kinda gave up and just went ahead and upgraded to Dapper Drake Beta, and so far I am highly satified with it.....it seem my wireless card....YAY!

Thanks for the suggestion anyways
~Blacktalon

---

