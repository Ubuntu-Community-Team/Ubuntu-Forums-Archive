---
title: "Overheating problem for Windows 10 &amp; Ubuntu 18.04 dual boot"
date: 2018-09-02
forum: Hardware
---

### Post by gokberkalagoz on 2018-09-02
[FONT=arial][SIZE=3]Hi all,

I recently bought a new HP laptop with Windows 10 and installed Ubuntu 18.04 as well. However, at the end of Ubuntu installation, when I clicked on "Restart Now", everything froze and I got a black screen (image is attached). Then I forced my laptop to restart, booted Ubuntu, entered my password but got a plain black screen this time. So, I forced my laptop to restart again and at the grub screen, pressed "e". Then at the line starting with "linux", I deleted "quiet splash" and added "nomodeset". Finally, I could reach the Ubuntu desktop and changed driver settings following "Software & Updates">"Additional drivers">"using NVIDIA driver metapackage...">"Apply Changes". However, now I'm having this overheating problem in Ubuntu, but everything is fine in Windows 10. I'm not sure if it's related with this "nomodeset" thing though.

My graphics card is NVIDIA® GeForce® GTX 1050 and I have read a lot of stuff about NVIDIA graphics cards and Ubuntu problems.

I was wondering if anyone has any idea about what might be the problem is.

Thanks in advance![/SIZE]
[/FONT]

---

### Post by dsstorefile1 on 2018-09-06
How do you know it is an overheating problem?

---

