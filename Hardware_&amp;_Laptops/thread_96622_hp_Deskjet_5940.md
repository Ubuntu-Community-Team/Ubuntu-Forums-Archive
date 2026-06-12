---
title: "hp Deskjet 5940"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by zappa on 2005-11-29
Hello, 

I'm using Ubuntu, but I can't get my printer working. 

It's on port 3: lsusb:

Bus 003 Device 002: ID 03f0:8704 Hewlett-Packard

I have both drivers (hpijs and hpoj) this is the output of sudo
/etc/init.d/hpoj setup

Probing "%003%002"...
    Found "Deskjet 5900 series"
    with serial number "CN56E1Z12H047H".

    This device will be set up as "mlc:usb:Deskjet_5900_series".

But, it is not found via the gnome set-up. So installed printconf to let it
being set-up. It was found. gs -h gives me ijs in the listing, so that's OK
too. 

I was able to ask a test page. It only started printing after I asked to print
an open office doc too, but incredibly slow. The doc never came out. 

After a reboot my printer is not found again. I haven't tried it with CUPS yet,
but please, I'm really puzzeled. Can someone help? 

Thanks a lot in advance.

---

### Post by bugi on 2005-11-29
If you have hplip already installed, write
```
sudo /etc/init.d/hplip restart
sudo /etc/init.d/cupsys restart
```

And now try to set it up in System -> Administration -> Printing , use URI .

---

### Post by zappa on 2005-11-29
Thanks, it's responding somehow without uri. At least it is detected. Now, I don't know cups. I followed the instructions of HP, but the web interface is not accessible as non-root, but I don't get pas it since as I believe root is blocked. 
So any idea what the uri should look like, or how I can make one alternatively?

---

