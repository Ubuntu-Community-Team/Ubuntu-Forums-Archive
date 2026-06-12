---
title: "USB device not showing"
date: 2011-11-01
forum: Hardware
---

### Post by Jethro_uk on 2011-11-01
hi all

I have 4 USB devices ... 3 disks, and a UPS. When I "lsusb" I can only see the disk drives (which are working perfectly).

Is there something I have missed ?

---

### Post by WasMeHere on 2011-11-01
Hi Jethro_uk,

I guess your USB UPS is not recognized by linux. Probably it has some proprietary driver to be installed in Windows for monitoring or communication about the power situation.

Have you been able to 'see' it in Ubuntu earlier? Or in Windows? I guess it works without that communication until the battery is running low. Then you must shutdown manually unless there is automatic communication.

Have fun finding out :-)
Olle

---

### Post by Jethro_uk on 2011-11-01
> **Olle Wiklund said:**
> Hi Jethro_uk,

I guess your USB UPS is not recognized by linux. Probably it has some proprietary driver to be installed in Windows for monitoring or communication about the power situation.

Have you been able to 'see' it in Ubuntu earlier? Or in Windows? I guess it works without that communication until the battery is running low. Then you must shutdown manually unless there is automatic communication.

Have fun finding out :-)
Olle

Thanks Olle,

my brother got it working using some sort of Web-based interface a while ago. Unfortunately that was under 9.10 on a different machine, and I have no idea what he did. I could bother him again (it's just a phone call), but want to stand on my own two feet.

So I know the UPS *will* work - certainly under 9.10. But exactly what I need to do is a mystery.

Oh well, GIYF ....

---

### Post by WasMeHere on 2011-11-01
I think your brother will be happy to help you :-)

Let us know your result, and to make the information useful, please describe the hardware (the UPS) too!

---

### Post by Jethro_uk on 2011-11-02
UPDATE:

It always pays to check your hardware *100%* before posting ! The silly old cable was very slightly loose on the UPS (my server is high on a back shelf so not easy to access - I am connecting over X2Go).

After plugging cable in, I got  

```
Bus 004 Device 008: ID 0665:5161 Cypress Semiconductor USB to Serial
```

Still couldn't get apcupsd to work though, so I installed and configure NUT. As far as I can tell that works now, after I followed [this]("http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/") excellent guide.

The only problem I face now, is trying to get the nut cgi-bin working, so I can actually see what the UPS is up to ....


FURTHER UPDATE:

After installing nut cgi-bin, and following the README file, I now have the UPS status available on my localhost ...

---

