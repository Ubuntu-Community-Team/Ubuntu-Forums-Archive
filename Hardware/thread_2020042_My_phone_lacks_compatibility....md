---
title: "My phone lacks compatibility..."
date: 2012-07-07
forum: Hardware
---

### Post by Animeniac on 2012-07-07
I just got a Samsung Galaxy S III. I plugged it into my Ubuntu computer, but it doesn't work properly as an MTP or a PTP device. I can't switch the phone's USB mode into USB Mass Storage mode. Only the root of the phone's internal flash memory is opened but it cannot access all the other files in it. If I transfer some files into it, the transfer is WAAAAAAYYYYYY too slow. Furthermore, if I click on the phone's properties, it only shows over 500MB used and a storage capacity of over 5GB. The phone's real storage capacity is 16GB and I have photos, music and apps on it. The phone will not work at all in my Windows XP SP3 virtual machine in VirtualBox.

Because of this lack of compatibility, I have to settle with a wifi transfer app to move music into the phone. 

Is there a way to fix this compatibility issue so that my phone will work as a mass storage device or as if I plugged it into a host Windows PC? Thank you.

---

### Post by Redblade20XX on 2012-07-07
Another galaxy problem..... have you tried gmtp?

I believe that the hardware (device controller) that dictates whether you can use mtp mode or ums (mass stoarage device). But maybe I'm wrong. Check out the galaxy forums to see.

On the virtualbox note, see here: 
[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

Also (not a windows expert) isn't XP a little to old to handle MTP devices? Does the galaxy work on a XP windows host? If not, you'll probably need a driver for it.

- Red

---

### Post by Animeniac on 2012-07-07
I installed gmtp; it didn't work. Also, I have the drivers installed in my Windows guest, but the phone will not connect to it. It stops at "Found New Hardware: SAMSUNG MTP Device"; it doesn't go any further.

Maybe you're right about the lack of compatibility between Windows XP and MTP devices?

---

### Post by Animeniac on 2012-07-12
Finally, I've been able to get my phone connected to my Windows XP virtual machine!!! 

All I had to do is to follow these steps in this order:

1. install the [device drivers]("http://www.samsung.com/ca/support/usefulsoftware/KIES/JSP"),
2. install the [MTP drivers for Windows XP]("http://www.sendspace.com/file/r59n5s"), 
3. install [Windows Media Player 10]("http://www.microsoft.com/en-us/download/details.aspx?id=20426"), 
4. create a USB filter for the phone in MTP mode,
5. run Windows Media Player 10, and
6. connect my phone to the computer via USB.

I did steps 1-4 already.

I can now access all the file in the phone's flash drive and transfer files to and from the phone just like I would in a Windows 7/Vista host machine!

---

### Post by Animeniac on 2012-07-12
I tried it again and I run back into this problem. Apparently, Ubuntu did not get its hands on the phone before the Windows virtual machine did. Now, the opposite is true again, even with the filter activated.

I have to stop Ubuntu from recognizing the phone before the virtual machine does. How do I do that?

---

### Post by Animeniac on 2012-07-13
Never mind about the previous post. I restarted the VM and it connects to the phone every time I plug it in now. The VM needs to be booted completely.

---

### Post by Redblade20XX on 2012-07-13
> **Animeniac said:**
> Never mind about the previous post. I restarted the VM and it connects to the phone every time I plug it in now. The VM needs to be booted completely.
 
Glad it works!!! ):P

- Red

---

