---
title: "Intel HD Graphics 4400 not recognized"
date: 2015-04-13
forum: Hardware
---

### Post by Namnamseo on 2015-04-13
Hello.
My laptop has i5-4200U + Intel HD Graphics 4400, with no external VGAs.

I recently had to install Ubuntu 14.04 on it, and I encountered some problems.
I made a UEFI Live USB. When I boot with it, four menus with black background comes out :
(Try Ubuntu without installing), (Install Ubuntu), something related with OEM, and (Check disk for defects).
When I selected either the first two, The screen went black and responded to nothing.
However, I found out **the system was actually booted**, with nothing on the screen.
For example, When I alter between Ctrl+Alt+F2 and Ctrl+Alt+F7, the screen brightness changes for a little.
And when I use Alt+SysRq+B, the system immediately reboots.
So I searched through some threads and set '**nomodeset**' at the booting menu, and the installer installed properly.

After installation, the computer still needed 'nomodeset' for the screen to come up properly, and it was VERY slow.
I don't have much knowledge about it, but with a little search, I assumed it was not using the hardware accelerator.
With a lot of reboots, edits, searching through logs for two days(in my exam period!), I think it's right.
When I remove **xserver-xorg-video-vesa**, the screen doesn't show up, no matter whether I use **nomodeset** or not.
I thought it didn't have appropriate drivers and tried to install **Intel Graphics for Linux**(01.org/linuxgraphics).
I needed to upgrade the distribution to 14.10 to use the installer(what is LTS for after all by the way, if some people ignores it?),
and the installer installed something which I don't know.

But, after all, nothing worked. The display shows nothing until I use **nomodeset**, which uses default(maybe fallback?) graphics driver.
Here are some informations I acquired.
If any more information is needed, I'll be happy to update them.


lspci | grep VGA shows ```
Intel Corporation Haswell-ULT Integrated Graphics Controller
```

There's nothing on the **Proprietary drivers**.

I installed **xserver-xorg-video-intel**, it still didn't work.

Under **System Settings** > **Details** : Gallium 0.4 on llvmpipe

---

### Post by dino99 on 2015-04-13
there is a lot of graphic issues with 14.04 & 14.10, so better to move to 15.04 (ubuntu works better than the other flavours)

this could be due to some non genuine ubuntu packages, like ppa or third party (if any)

---

### Post by Vladlenin5000 on 2015-04-13
This is a quite peculiar issue. If I hadn't experienced it myself when installing an ACER laptop for a friend, I wouldn't believe it. Intel drivers are open source, included by default and they should just work.
Here are two suggestions:
1. As mentioned in the previous post, 15.04 is around the corner. Why don't you try it?
2. If you want to keep the LTS - 14.04 - then you can do what I did, after booting with *nomodeset*, force install the Intel drivers with the Intel installer -> [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

---

### Post by Namnamseo on 2015-04-13
> **Vladlenin5000 said:**
> This is a quite peculiar issue. If I hadn't experienced it myself when installing an ACER laptop for a friend, I wouldn't believe it. Intel drivers are open source, included by default and they should just work.
Here are two suggestions:
1. As mentioned in the previous post, 15.04 is around the corner. Why don't you try it?
2. If you want to keep the LTS - 14.04 - then you can do what I did, after booting with *nomodeset*, force install the Intel drivers with the Intel installer -> [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

Oh, I forgot to mention that, I actually upgraded to 14.10, and the Intel graphic driver installer worked alright. It did install something. Even after the reboot, the problem persists.

---

### Post by Namnamseo on 2015-04-14
Okay, I found something more.

When I boot **without **nomodeset, the graphic driver was being properly loaded.

from Xorg.0.log -- "**[    23.373] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4400**"
So after all, the problem was something else than drivers or hardwares.

I attached some logs from **/var/log/gdm**.
**log_0.log.txt** corresponds to **:0.log** (I stripped some messages about mouse, keyboard, camera, etc. for the sake of file size),
**log_0-greeter.log.txt** corresponds to **:0-greeter.log**,
**log_0-slave.log.txt** corresponds to **:0-slave.log**.
I also read a few messages from /var/log/Xorg.0.log, but it was similar to /var/log/gdm/:0.log, so I decided not to upload it.
I've also dumped **/var/log/dmesg**, so if you need something from the file, please tell me.

I'll try Ubuntu 15.04 when it's up, as mentioned in the previous posts.
But I hope to solve the problem here, as the internet at my school is not so good.

---

### Post by variona on 2015-04-18
@Namnamseo 
Just for clarification, you solved the problem by upgrading to 14.10?
Can you you use two monitors?

---

### Post by Namnamseo on 2015-04-23
@variona :
No, I upgraded to 14.10 and the graphics driver installer worked just fine.
If I boot without nomodeset, the main monitor does not work, but HDMI monitor works.
I tried swapping between display modes(same screen on both display, extended screen, etc.), but only HDMI monitor works.

---

