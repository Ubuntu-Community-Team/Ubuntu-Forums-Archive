---
title: "How well does laptop with minimum requirements run Ubuntu 20.04?"
date: 2021-12-16
forum: Hardware
---

### Post by zitsky on 2021-12-16
I have an old Dell XPS M1210 with 4GB memory and 500GB? hard drive, Nvidia Geforce Go 7400.  I have not installed an SSD because I think it's not worth the trouble.

I see it meets the minimum requirements but I wonder how well it will perform?  I only plan to use a web browser for light browsing and check email.  Maybe watch DVD's.

I have Windows 10 on this now but recent updates have made it almost unusable.  Before I turned it back on and did a few Windows updates, it was usable.

Before you ask me to upgrade, I do have a Lenovo Flex 5 in the house.  I share it with my partner who took it upstairs.  So I have something much faster than this.  Plus I have my phone!  I'm just looking for an internet terminal.

---

### Post by Autodave on 2021-12-16
It should work fine.  I would go with a lighter desktop like Xubuntu.

Here's what I would do: download Xubuntu 20.4 and make a bootable USB or DVD with it.  Boot that machine up to it and make sure that the graphics card is recognized.  If it is recognized, then you should be golden.  I would, at that point, put an SSD into it though......will make it much faster.

---

### Post by TheFu on 2021-12-16
The Geforce GS 7400 doesn't have any proprietary GPU drivers for any current supported Ubuntu version, so you'll be using the F/LOSS GPU driver. I know my 7200GS lost support in 2016.

An SSD is the single, most cost efficient, way to drastically improve system performance. It will make more difference than adding more RAM. Of course, it isn't mandatory.

If all you want is an internet terminal, then Ubuntu is much too heavy for that. Look for a **ChromiumOS** version to install instead. This is like ChromeOS, but uses the F/LOSS Chromium instead. I doubt you'll notice any difference.  It will be a very fast chromebook. I think you'll like it.
 [https://www.alphr.com/download-install-chrome-os/](https://www.alphr.com/download-install-chrome-os/)  They used to make virtual machine versions available, but they stopped that for some reason. They only want this installed onto real hardware now. That should be fine for your your needs.  Give it a try.
> 6. Boot into Chrome OS Without an Installation

The great thing about Chrome OS is that you don&#8217;t need to install it, and it doesn&#8217;t take any space on your hard drive. You can boot it right from the USB without installation, so your primary OS won&#8217;t be affected at all. You can set up your Chrome OS with a Google account and use it only for surfing the internet.

No risk. Try it.  I used the "guest account" for 3 months and never connected any gmail account to a chromebook. It was very usable and fast.

---

### Post by T6&amp;sfpER35% on 2021-12-16
like post #2 said it'll be fine , on xubuntu. My specs are lower and xubuntu is flying , with no SSD
i found [this](http://www.opendrivers.com/modeldriver/nvidia_geforce%20go%207400-driver-download.html) for drivers for your Nvidia
or you could just use the Nouveau drivers.

---

