---
title: "Asus EEE 1000 - no network connections"
date: 2008-10-01
forum: Hardware
---

### Post by ExNomenDei on 2008-10-01
I just got an Asus EEE 1000 from the shop and used UNetBootin (Windows version) to make a USB stick and install a default Ubuntu 8.04 on it. It's the Wireless-N networking version.

Neither the wired nor the wireless connection seems available, and my networking knowledge on Linux is very limited. How can I fix this? Without a working network, of course, so downloading files is complicated to say the least.

Perhaps I could get something on there via USB stick, if that helps.

---

### Post by DShad on 2008-12-18
I've got the same here with my MSI WInd.  THe ethernet port is seen but unable to configure it because it doesn't appear on the Network tab or the network icon near date & time.

Any ideas?

> **ExNomenDei said:**
> I just got an Asus EEE 1000 from the shop and used UNetBootin (Windows version) to make a USB stick and install a default Ubuntu 8.04 on it. It's the Wireless-N networking version.

Neither the wired nor the wireless connection seems available, and my networking knowledge on Linux is very limited. How can I fix this? Without a working network, of course, so downloading files is complicated to say the least.

Perhaps I could get something on there via USB stick, if that helps.

---

### Post by snowpine on 2008-12-19
Hi there,

No version of Ubuntu supports wireless on the eee pc "out of the box." There are a couple of different methods to get it working. One (which I've never personally tried) involves downloading the appropriate madwifi drivers. The "hack" I personally use is to install the custom kernel from array.org, which adds support for all of the eee's hardware (wireless, wired, webcam, etc.) and works with Ubuntu/Xubuntu/Kubuntu hardy or intrepid: [http://array.org/ubuntu/](http://array.org/ubuntu/)

If you don't have wired OR wireless, you'll need to copy the files over with a USB stick: [http://array.org/ubuntu/setup-hardy-alt.html](http://array.org/ubuntu/setup-hardy-alt.html)

Sorry DShad, but I don't know whether or not this will work on the MSI Wind.

---

