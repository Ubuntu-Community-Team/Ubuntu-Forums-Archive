---
title: "Computer Keeps Shutting Down/Restarting"
date: 2015-08-25
forum: Hardware
---

### Post by john441 on 2015-08-25
I am using the newest ubuntu and a pretty new laptop I bought a couple weeks ago with ubuntu pre installed. Today the device was running fine until it randomly restarted twice when I wasnt even using it and no programs were running. I thought it was just a weird error so I dismissed it and now the device wont be on for more then 10-15 seconds at most before it restarts or usually just shut downs again. I don't have enough time to even login. 

I don't think it's overheating as the laptop isn't hot at all and I do not game or anything else too intensive on it. 

I bought the device from linux certified it's the [B]LC2430E notebook model. 


[/B]

---

### Post by weatherman2 on 2015-08-25
Can you boot a live USB version of Ubuntu?

If you power it on and enter what used to be called "BIOS Setup" (now "EFI Setup" or "Firmware Setup" or something) without booting into an OS, does the computer restart still or will it stay there indefinitely?

Can you run Memtest?  Try holding down the Shift key as the computer restarts; if you aren't using Secure Boot you should get a menu that includes Memtest as an option.  You can also run it as an option from a USB boot of Ubuntu.  I'd run Memtest to make sure the RAM is good.

Even a brand new computer can have a hardware problem.

---

### Post by john441 on 2015-08-27
I am running a memtest now, has been going for about an hour. Today I was using the device for about 3 hours with no issues then it restarted and kept restarting. It hasn't restarted during memtest so that is a good sign. 

Also I ran the temperature checks and the temps were fine. 

I don't have a USB stick to test that but this is a fairly fresh reinstall of ubuntu only thing I've done is added a bunch of packages to run my usual applications (python pip etc).

I was debating taking the device to geek squad but I wasn't exactly sure what they would do.

---

### Post by weatherman2 on 2015-08-27
Yeah, don't take it to Geek Squad.  I doubt the support Ubuntu - they can barely support Windows.

If it doesn't shut down in Memtest, then yes, that's a good sign.  That probably means it's not the motherboard or something.

Is there any way you can make/obtain a Ubuntu USB stick?  If you can also boot live from USB and have it not shut down - then we can guess something you added - an additional driver(?) or even a package is causing your issue.

Also - what version of Ubuntu is this computer certified for?  If it isn't certified for the version you use (15.04?) maybe you need to go back to the version that is certified.

---

### Post by john441 on 2015-08-27
> **weatherman2 said:**
> Yeah, don't take it to Geek Squad.  I doubt the support Ubuntu - they can barely support Windows.

If it doesn't shut down in Memtest, then yes, that's a good sign.  That probably means it's not the motherboard or something.

Is there any way you can make/obtain a Ubuntu USB stick?  If you can also boot live from USB and have it not shut down - then we can guess something you added - an additional driver(?) or even a package is causing your issue.

Also - what version of Ubuntu is this computer certified for?  If it isn't certified for the version you use (15.04?) maybe you need to go back to the version that is certified.

Yes I will try the USB tomorrow. Do you know how I enter BIOS on this specific device?

It came with 15.04 installed and with a 15.04 CD. I reinstalled the CD it from the CD because I wanted to set it up with my preferences like name. It took probably 2-3 hours of just downloading packages and what not to get my 3-4 applications set up. 

There is a local computer repair place that deals with Ubuntu I am considering. I just feel like he wouldn't be able to pinpoint the issue and instead reinstall the OS, charge me $200, and in reality fix nothing I go home and it happens again the next day. 

I wish all these packages came preinstalled on the OS.

---

