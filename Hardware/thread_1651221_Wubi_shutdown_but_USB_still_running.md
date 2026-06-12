---
title: "Wubi shutdown but USB still running"
date: 2010-12-22
forum: Hardware
---

### Post by allencch on 2010-12-22
I installed Wubi on my HP laptop with Windows 7 for dual boot. It is fine for the booting, running Ubuntu, etc. Until that, after I shutdown from Ubuntu, the USB power still running on my cooler. I tried all the 3 USB ports and also different cooler, all the USB port still power on. And I confirmed that my laptop is shutdown completely, without any light on it. 

I think it is Ubuntu shutdown problem. So, I tried to boot into Windows 7 and shutdown, but the problem remains.

So, my final solution was took off the battery, then plug the battery back, and only that, the USB is not running.

Please help me diagnose the problem and the solution of shutting down with Ubuntu. I quite afraid that shutdown with Ubuntu will cause any other problem.

---

### Post by bcbc on 2010-12-23
I find it's useful to search on the computer brand/model number - someone else might have posted some info: there are some boot options that are required for some computers to function correctly. Also make sure the bios is up to date.

---

### Post by allencch on 2010-12-23
Hi, my laptop is HP Pavillion dv3-2238tx. I didn't update the BIOS.


> **bcbc said:**
> I find it's useful to search on the computer brand/model number - someone else might have posted some info: there are some boot options that are required for some computers to function correctly. Also make sure the bios is up to date.

---

### Post by cascade9 on 2010-12-23
Ubuntu didnt cause the 'problem', or else it wouldnt happen when you shut down from Win7. Its also soemthign that many computers do- 

> most USB ports are powered from standby power, which means that they stay powered up even when the PC is switched off

[http://www.gifford.co.uk/~coredump/usbpwr.htm](http://www.gifford.co.uk/~coredump/usbpwr.htm)

You might be able to turn of standby USB power in the BIOS. Sometime its by turning off 'wake on USB', sometimes it by disabling 'standby USB power' and sometimes there is no control at all......

---

### Post by allencch on 2010-12-23
I found a similar thread ([link]("http://ubuntuforums.org/showthread.php?t=1399730")).

And besides the problem I got as mentioned above, I had another problem, that is I cannot move file to trash, where the files are within /host.
So, I used the solution based on [this]("http://ubuntuissues.wordpress.com/2008/06/19/cannot-move-files-to-trash/") article.

The article and the thread both mentioned GRUB_CMDLINE_LINUX_DEFAULT.

But after modifying the grub file, I don't have the USB issue after shutting down.

I am not sure this is the correct solution to solve my problem. But this is what I have done, and the problem is solved.

Thanks.

---

### Post by allencch on 2011-01-03
I thought the problem is solved. But it does not. When I shutdown the laptop, with the AC still connected, then the cooler will not running. But after I switch of the AC, then the USB cooler suddenly start working again. Quite frightening.

---

### Post by allencch on 2011-01-03
The following is the experiments the USB problem, USB here means the any USB ports that connect with the USB cooler:

[LIST]
[*]In the normal state (meaning that USB will not running anymore after shutting down), shutdown from Windows 7 will be normal.
[*]In the normal state, shutdown from Ubuntu (Wubi), will cause USB still running only when AC power is off. If AC is on, the USB will stop. As a result, the battery will not cool down.
[*]In the abnormal state (meaning that USB is still running when the laptop is shutdown), shutdown from Windows 7 will not recover to normal state.
[*]To recover it to normal state, need to unplug the battery from the laptop, then plug in again.
[/LIST]
So, the annoying solution is, do not shutdown from Wubi, but restart, then shutdown from Windows.

Is there any better solution?

---

### Post by bcbc on 2011-01-03
I found this other thread [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1399730](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1399730)

I guess you're not the only one with a USB issue. No solution I found :(

---

### Post by allencch on 2011-01-04
Thanks bcbc, but at least I do not need to unplug the battery every time.

---

