---
title: "Problem on getting latest Nvidia driver from Nvidia website"
date: 2010-10-04
forum: Hardware
---

### Post by js0823 on 2010-10-04
Hi all.
I am quite a noob with Linux platform and I have a question regarding getting latest Nvidia on the latest version of Ubuntu(10.04).

I downloaded the latest driver by using this command line

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```

However, this doesn't enable the Nividia driver from "Hardware Drivers". To use the normal visual effect, I still have to enable the graphic driver from Hardware Drivers to use it. It seems Nvidia website has version 235(or 225 I forgot) while Hardware Drivers only has version 173.

My laptop has Geforce 8700M GT.

Can someone guide me how to install the latest version of Nvidia driver I got from Nvidia website? Or is it better to use the recommended driver from Hardware drivers?

And just one more question. Is Nouveau driver better than Nvidia driver? Can Nouveau driver enable all the graphic settings needed to run demanding games and desktop effects?

Thank you very much.

---

### Post by mikewhatever on 2010-10-04
I'd recommend using the driver from the repositories. The latest driver would likely not benefit you much, since you don't have the newest graphics card.

---

### Post by js0823 on 2010-10-04
I see.
If I don't have any nvidia driver enabled on Hardware Drivers, does that mean it's using nouveau driver? How can I check what driver it's using?

I'm asking this because when I first installed Ubuntu, the startup screen before login screen was a very nice 1650x1050 resolution(biggest for my laptop), but when I enabled nvidia driver, it changed the startup screen to a small one. It's not a big issue as it changes back to biggest resolution on login screen, I just wanted to know.

Thanks tor the reply.

---

### Post by mikewhatever on 2010-10-04
> **js0823 said:**
> I see.
If I don't have any nvidia driver enabled on Hardware Drivers, does that mean it's using nouveau driver? How can I check what driver it's using?

I think nouveau is used by default when nvidia hardware is detected. You can see what driver is in use from the output of the following:
```
sudo lshw -C display | grep driver
```

> I'm asking this because when I first installed Ubuntu, the startup screen before login screen was a very nice 1650x1050 resolution(biggest for my laptop), but when I enabled nvidia driver, it changed the startup screen to a small one. It's not a big issue as it changes back to biggest resolution on login screen, I just wanted to know.

Thanks tor the reply.
That's one of the known issues with Lucid. I think you can change the splash screen resolution by editing /etc/defaul/grub
and applying suggested workarounds. [Here is one]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/"), with nvidia related info towards the end.

---

