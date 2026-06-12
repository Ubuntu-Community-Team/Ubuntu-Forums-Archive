---
title: "MSI 580 GTX lighting with Ubuntu"
date: 2012-12-17
forum: Hardware
---

### Post by rasmus91 on 2012-12-17
Hi Everyone.

I've run Ubuntu as my only OS on my laptop for more than a year now, and im thrilled to do so. With steam coming for Linux, and generally a lot of things seeming to head in the right direction. such as the amount of time for gaming not being much Im considering putting Ubuntu on my Desktop Simply because I'm sick of windows and when what i do most is browse the web and watch movies i and do programming I'd really prefer using ubuntu.

the graphics card is an:
MSI nvidia geforce 580 GTX lighting

quite a powerful, power consuming devil. and something im quite happy to use, but so far it seems like it has some sort of problem when i boot from USB, as when i press "try Ubuntu" it locks up, and the console complains about stuff with the nouveau driver. Can't help but think that this may be fixed by installing the proprietary driver.

does anyone have any experience with this card?

Thank you for your time.

---

### Post by haqking on 2012-12-17
> **rasmus91 said:**
> Hi Everyone.

I've run Ubuntu as my only OS on my laptop for more than a year now, and im thrilled to do so. With steam coming for Linux, and generally a lot of things seeming to head in the right direction. such as the amount of time for gaming not being much Im considering putting Ubuntu on my Desktop Simply because I'm sick of windows and when what i do most is browse the web and watch movies i and do programming I'd really prefer using ubuntu.

the graphics card is an:
MSI nvidia geforce 580 GTX lighting

quite a powerful, power consuming devil. and something im quite happy to use, but so far it seems like it has some sort of problem when i boot from USB, as when i press "try Ubuntu" it locks up, and the console complains about stuff with the nouveau driver. Can't help but think that this may be fixed by installing the proprietary driver.

does anyone have any experience with this card?

Thank you for your time.

I have a GTX 580 though not the MSI but it shouldnt matter, blacklist nouveau and install the proprietary driver, if you do it properly it will blacklist the nouveau for you.

here is the readme for installing [http://uk.download.nvidia.com/XFree86/Linux-x86_64/310.19/README/installdriver.html](http://uk.download.nvidia.com/XFree86/Linux-x86_64/310.19/README/installdriver.html)

and get your driver from here [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by rasmus91 on 2012-12-17
> **haqking said:**
> I have a GTX 580 though not the MSI but it shouldnt matter, blacklist nouveau and install the proprietary driver, if you do it properly it will blacklist the nouveau for you.

here is the readme for installing [http://uk.download.nvidia.com/XFree86/Linux-x86_64/310.19/README/installdriver.html](http://uk.download.nvidia.com/XFree86/Linux-x86_64/310.19/README/installdriver.html)

and get your driver from here [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

the MSI we're talking about here is a special version, as i recall, with 3GB RAM, optimized for overclocking. But yeah, in windows at least it runs the standard nVidia driver.

I'll give it a go.

---

### Post by haqking on 2012-12-17
> **rasmus91 said:**
> the MSI we're talking about here is a special version, as i recall, with 3GB RAM, optimized for overclocking. But yeah, in windows at least it runs the standard nVidia driver.

I'll give it a go.

it is still the same driver, same GPU.

And mine is 3GB too, but the RAM is irrelevant

---

### Post by rasmus91 on 2012-12-17
Update: Ubuntu 12.10 (booted from live USB) freezes as i reach the Desktop. I've tried to ctrl+alt+f1 to go into a terminal, but it forces itself back to the desktop where it then freezes. What can i do?

---

### Post by haqking on 2012-12-17
> **rasmus91 said:**
> Update: Ubuntu 12.10 (booted from live USB) freezes as i reach the Desktop. I've tried to ctrl+alt+f1 to go into a terminal, but it forces itself back to the desktop where it then freezes. What can i do?

edit grub for nomodset flag.

as described here [http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation](http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation)

---

### Post by rasmus91 on 2012-12-17
> **haqking said:**
> edit grub for nomodset flag.

as described here [http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation](http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation)

Thank you very much, that seems to work.

why, however, does this make the ubuntu splashscreen so damn ugly?

---

### Post by rasmus91 on 2012-12-18
It gets to the Desktop (after installing nVidia driver) but its all messed up, theres no UI to speak of, other than a desktop without any of its elements other than the cursor. I don't really have any idea on what to do... but it sure boots fast.

any idea what could be wrong?

---

### Post by rasmus91 on 2012-12-19
Ah, there we have the problem!

i did this:

```

sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current-updates
sudo dpkg-reconfigure nvidia-current-updates
```
(thanks to Lisiano in [this thread]("http://ubuntuforums.org/showthread.php?t=2072862"))

then i rebooted and it still didn't work.

but thanks to mdshann on page 5 of the same thread saying:
> Installed 12.10 today. had this issue. I went to install the headers, which worked fine. I then ran dpkg-reconfigure nvidia-current and it said that the headers for the currently running kernel did not exist. OK, so we'll do an apt-get update && apt-get upgrade to make sure I am on the latest kernel. It held back the latest kernel and I had to manually ask it to install the new kernel with apt-get install linux-image-generic. After that install finished I rebooted and everything worked perfectly.

i tried:
```
sudo apt-get install linux-image-generic
```

and now it works, so thank you very much mdshann!

---

