---
title: "USB DVD writer doesn't write"
date: 2008-11-11
forum: Hardware
---

### Post by Rayaz on 2008-11-11
Hello all,

Just purchased a DVD writer Sony DRU-840A and connected it to my laptop with a USB 2.0 IDE cable. It can mount CD's perfectly but just simply won't write. I've tried K3B and Brasero and Gnomebaker. None work.:mad: On a whim searched for a Nero version for Linux and downloaded the Nero Linux 3. It's a trial version. And guess what it writes CD's perfectly!!:mad: Why???

Any pointers?

---

### Post by Rayaz on 2008-11-16
Update: Did some more research, tried Intrepid, still no luck. At Launchpad there was this discussion about a kernel problem, however the latest kernel in Intrepid didn't work.. I also tried modifying initramfs modules by adding piix, ide, ide-cd modules, still no luck. Can I expect to get some help on this issue in this forum?

---

### Post by Rayaz on 2008-11-17
Bump;

---

### Post by Yezinki on 2008-11-17
Hi I am using Sony DRX-S70U.........usb drive....reads/writes CDs/DVDs....perfectly using any application.

---

### Post by Milkium on 2008-11-17
Does it give an error message?

---

### Post by Rayaz on 2008-11-17
Thank you for your replies. When using K3B or Gnomebaker I get the error "OPC failed, maybe the drive doesn't like the medium".
@ Yezinki, did you have to do anything special to get it working?

---

### Post by Yezinki on 2008-11-18
```
@ Yezinki, did you have to do anything special to get it working? 
```

Nah.....just plug into usb & start the job lol......try using quality medium....like Verbatim.

Good luck.

---

### Post by Yezinki on 2008-11-18
Such errors usually come with substandrad media, low quality brands, dirty lens.......might be a refurbished/repacked Sony.......

---

### Post by Yezinki on 2008-11-18
Hey its gotta a IDE interface & you must have got it converted to usb......no wonder it wont work.

Return & get a proper usb burner......not one thats been converted from IDE to USB.

Good luck!!

---

### Post by Rayaz on 2008-11-18
@Yezinki

Thanks for your suggestions, but it really doesn't answer my question i.e: Why does Nero Linux manage to burn a CD using the exact hardware setup when K3B and Gnomebaker et al fail?:confused:

---

### Post by Yezinki on 2008-11-18
It's not the difference BTW Nero Linux or K3b...its just coincidental.

The electrician who made the converter did not do a good job.

As regards to conversion from IDE to USB...it functions ok at times & at others gives a OPC error.

Can I ask you a personal question.....why did you save 20 bucks & buy a IDE burner & convert it to a usb......you should have bought a usb in the first place.

Just my thoughts,

Regards,

Yezinki.

---

### Post by SqRt7744 on 2008-12-02
I doubt it has much to do with it being an IDE-to-USB, it might be a usb issue itself, I'm having trouble in intrepid with a Sony DRXS70U. It works fine in hardy. There were some changes to the kernel, and when I plug it in dmesg says something about the sr0 driver needing updating, and then when I put a blank cd in, it comes up with more errors "Buffer I/O error on device sr0, logical block 0" again and again. All burning programs fail, but it can read from disks fine.

I've tried a few kernel parameters to no avail, but I haven't given up on that route yet, also I tried toggling USB legacy support in the bios, but that didn't help in my case either.

If I find a solution I will let you know.

I made a bug report, maybe somebody on the kernel team will have a better idea
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/304434/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/304434/)

---

### Post by Rayaz on 2008-12-02
Hi

Remember Nero for Linux works fine. Wonder why?

---

### Post by MichaelBKK on 2008-12-29
I've been having a different problem for quite some time.  I have an LG USB CD/DVD writer.  It was working perfectly, but since v7 (on 8.04 now) all my CD's turn out blank.  The CD Writer app doesn't produce any errors.  It acts as if everything went fine, but when I put the CD into ANY other CD drive, it's basically still blank.

---

### Post by crjackson on 2008-12-30
> **Rayaz said:**
> Hi

Remember Nero for Linux works fine. Wonder why?

I have issues with Gnome Baker, K3b, and Brasero depending on what I'm working on (this is for internal burners, I have 8 of them on different PC's) and it's not predictible.

NERO works perfectly on ALL of them for me...

---

