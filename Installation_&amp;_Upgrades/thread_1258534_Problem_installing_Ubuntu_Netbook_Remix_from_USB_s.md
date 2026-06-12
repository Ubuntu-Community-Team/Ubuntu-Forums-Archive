---
title: "Problem installing Ubuntu Netbook Remix from USB stick on HP2140"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by TomTom_London on 2009-09-05
I hope someone can help.

I'm trying to install UNR on an HP Mininote 2140 using a USB stick.

I've followed the instructions using Win32 disk imager to get the img file on the USB stick.  I've checked the MD5 hashes and they are correct.

The 2140 boots from the USB stick, and I first get the language choice, then the "try ubuntu, install, check deic, test memory and boot from first hard disk" options.  But I've tried both the install and also "try ubuntu" options, and both times, it seems to freeze at the same point.  The last two lines being:
[   3.647366] [<c0737099>] __init_begin+0x99/0xa1
[   3.647366] ---[  end trace 3af2f8412540f2c7  ]---

It sits here for 20-30 mins and then eventually I just manually rebooted the netbook.

Any ideas what's going wrong?  Does it need more than 30mins at this stage or is soimething else up?

It's a brand new internal hard drive in the Netbook, which I assume was pre-formatted.

Any suggestions would be really appreciated.

Thanks

Tom

---

### Post by senectus on 2009-09-05
I've just made a USB boot thumb drive using USB-Imagewriter [(Easy install)]("https://wiki.ubuntu.com/UNR/Installation/Easy") and on Tuesday I'll be getting a free 2140 from Tech Ed Australia that I intend to boot from.
I'll see if I can duplicate your problem.

---

### Post by TomTom_London on 2009-09-05
Thanks -I just tried it on an HP2133 and it worked fine - so i think there must be something wrong with my 2140????  Very strange but at least I now know it's not the USB stick or image on it that's the problem.

---

### Post by senectus on 2009-09-05
Try this, I've been finding others having issues with having "Dual CPU" enabled in the BIOS.
Disable "Dual CPU" and try again...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376728](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376728)
Also you'll probably notice:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795)
and
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/376793](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/376793)

Other than those, it should work A-ok!

---

### Post by TomTom_London on 2009-09-06
Thanks for the tip. I disabled dual core in the BIOS and it's loaded!! :D

For some reason I'm getting some error messages - including one that must relate to the tool bar across the top of my screen as it's missing???  But at least it's working and I'm not connected to my WiFi network.

I'll get those other bits sorted today I hope!

Thanks again.

Tom

---

### Post by TomTom_London on 2009-09-06
All problems now solved - simply did a check for updates.  When all the updates were installed, everything works just fine now.

Yeeehaa!!! :D

---

### Post by 1205919 on 2009-10-28
Senectus

You are brilliant!!!!!!
I hve been strugling for more than 2 weeks to get my 2140 to boot the new UNR with no luck.
This morning i did a last search  bfore going backto winxp :(
And I found your advice on disabling the dualcore....workd lik a charm

Brilliant!!!!!!
Thank you very much!!!!!!!!!!!!!

---

### Post by 1205919 on 2009-10-28
Hi TomTom

Did you ge the top toolbar issue fixed????
I am experincing the same problem
Any advice on how to fix it?
thx

---

