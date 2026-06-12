---
title: "Force version doesn't work?"
date: 2008-09-16
forum: General Help
---

### Post by Holonet on 2008-09-16
I have a Nvidia 9800GT card and have installed the driver from the website.  Works fine until I updated the linux headers and kernel from 2.6.24-19.36 to 2.6.24-19.41, at which point, gnome tries to load a few times and fails, and goes into low graphics mode.  Another weird thing is that if I shut down gdm and reinstall the driver, and start gdm back up, it works again...but restarting the computer screws it up again.

If I go to these problem packages in synaptic, force version is grayed out, despite the fact that I just updated them.  I should add this is not a configuration problem as I just did this process on a fresh ubuntu install.  Anyone know how I can fix the problem...or at least know why I can't revert the version?  It really is crap considering part of Ubuntu's philosophy is being able to change your software and do what you want with the computers...except when it's a security update and we don't want you to...X-(

---

### Post by ryanhaigh on 2008-09-16
When you boot your system press Esc to see the grub menu and just boot into the older kernel. 

Kernel updates are brought in by meta-packages which always depend on the latest available kernel package. I believe the highest level meta-package is called linux-generic which depends on linux-image-generic and linux-modules-generic which in turn depend on the latest kernel image and modules. As far as I can tell the kernel versions get their own packages so you can simply uninstall the latest kernel (the one that is causing you problems) and also uninstall linux-generic,linux-image-generic and linux-modules-generic so that you won't get any further updates. This should also make your previous working kernel the default.

---

### Post by Holonet on 2008-09-16
Thanks for the info.  I tried uninstalling and reinstalling 2.6.24-18, but the problem remains.  The only way to get rid of it seems to be to replace the xorg.conf file with the default, then reinstall the driver.

Also, synaptic does not differentiate between 2.6.24-19.36 and 2.6.24-19.41 except before it's updated.  Now, it only shows 2.6.24-19...I had no problem with that, except there is no way to choose .36 over .41...just -19, which probably automatically selects the latter...this makes no sense...

In addition, even though I did not bother to uninstall the previous kernel, there was no previous kernel to select in grub, I'm assuming because there is more than one version of 2.6.24-19, and they're both the same to grub...

So I put in -18 instead, but seriously...wtf....  (Thanks for the help amidst my frustration :D).

---

### Post by ryanhaigh on 2008-09-16
Unfortunately installing -18 isn't going to address the issue. I must have missread your original post because I thought you had a working install with -18 then updated to -19.

I wouldn't have thought hat doing a minor version update would have caused problems with your nvidia driver install. I haven't installed the driver from the nvidia site for some time but I do remember having to deal with conflicts associated with the nvidia modules provided by the restricted modules package, was there a step in your original installation related to this?

This page should provide you with more information:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by Holonet on 2008-09-17
Yeah I wouldn't have thought so either, but I've done it multiple times, and it's true.  For some reason, with this card, nothing shows up in the restricted drivers, as in I do not even have the option of enabling them conventionally.  I went to nvidia's site, and selected my card (9800 GT), and it led me to their generic driver, of course...but I noticed even on their site, the list of supported cards did not explicitly mention the 9800 GT...  However, it did mention the 9800 GTX...so I wasn't sure if it was implicit or not.

Still, that makes no sense...it's their own product.

I'm not sure whether to blame ubuntu or nvidia...but something tells me to lean toward the latter, given this ambiguous support.

---

### Post by wwusnobrdr on 2008-09-17
Just a suggestion you may want to try to use Envy NG, a script that can remove and download/build the latest drivers for your source.  Helped me with my drivers and xorg before.

---

### Post by Holonet on 2008-09-17
Appreciate the input, but I have tried envy...didn't even detect the card, nvidia-glx, it all does the same thing.  For some odd reason, if I don't update 2.6.24-19.34 then it turns out ok with the website driver.  Makes me nervous about the next core change...

---

### Post by xanghel13 on 2008-09-27
I am having a very similar problem. I installed the nvidia drivers for the 9800gt from their website and it worked fine. But after i updated it won't hold the settings when i reset and it bumps me into low-graphics mode. When i reconfigure X and reinstall the driver it works fine.
Heres the disturbing news. I read your previous posts and so i chose not to update the Linux-headers or nvidia-glx. I got the same problem, so I don't know if it is the headers or something more general than that. Perhaps if any update messes with the X config it might be doing this.
However I don't have much time lately to continue messing with it so for now I do not shut down my computer. I merely put it in Hibernate or Standby as this doesn't give me problems. Only restarting the computer completely will.

---

