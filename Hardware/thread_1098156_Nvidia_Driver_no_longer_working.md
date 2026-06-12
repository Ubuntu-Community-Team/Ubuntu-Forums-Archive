---
title: "Nvidia Driver no longer working"
date: 2009-03-16
forum: Hardware
---

### Post by Sub101 on 2009-03-16
Ive been running Ubuntu on my laptop (HP DV2699ea) for 2 years now, I felt like trying the new Alpha 9.04 but it failed on my laptop so I decided to completely reinstall 8.10 and reformat my disk.

Having installed, I then enabled the restricted Nvidia driver and restarted my laptop. It now boots through splashy fine but turns to a black screen before the login screen is shown. What is odd is that 2 days ago the driver worked fine on the same laptop. For the time being I have removed the driver but it makes watching DVD's very unpleasant. 

The graphics card is an Nvidia Geforce 8400m. I would appreciate any help. Thanks.

---

### Post by andeol on 2009-03-17
I also get a blank screen after the splashy, got it for the first time after powering up this morning. If I use the open source nv driver instead of the nvidia driver, everything works. This makes me also suspect something has broke during a recent upgrade, I'm investigating it right now.

---

### Post by Sub101 on 2009-03-17
Yes. I believe it to have been caused by a bad update but I am unsure of how to fix it.

---

### Post by andeol on 2009-03-17
This might be related:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/339489](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/339489)

I still don't know how to fix it though.

---

### Post by Sub101 on 2009-03-17
Yep looks exactly the same. Cheers for the find. 

Will hopefully be fixed in the next updates then.

---

### Post by Sub101 on 2009-03-17
Brilliant. 

After my last post did a sudo apt-get update which downloaded some new nvidia drivers. Reboot and works perfectly. 

And people complain bugs take ages to fix!
Thanks developers.

---

### Post by andeol on 2009-03-18
Yes, works for me too, probably as a result of the upgrade of the kernel packages from 2.6.27-13 to 2.6.27-14. A fast fix is good but I wish there was some way of reverting package upgrades, that way my whole work day would not have been lost.

---

