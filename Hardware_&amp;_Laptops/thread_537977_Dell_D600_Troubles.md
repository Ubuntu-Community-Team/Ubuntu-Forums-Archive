---
title: "Dell D600 Troubles"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by detox187 on 2007-08-29
Let me start off by saying that I am completely new to linux, so please bare with me.  A friend of mine gave me an Ubuntu CD and the journey starts from there.

I installed Ubuntu and noticed that my wireless wasn't working.  The laptop has an integrated Intel Pro/Wireless 2200 b/g wireless nic.  I used my windows pc to find the drivers from intel themselves which wasn't a big deal, but now what?  The instructions for installing were far from detailed, and I started playing around with different things while reading on the internet and found nothing that seemed to help me get it going.  I was kinda bummed, but decided to look around the net some more.

While searching the net I found kubuntu, which I didn't even know existed.  I downloaded the .iso, ripped it to a cd and installed with out a single problem.  To my astonishment, it recognized my wireless card and with the click of a mouse I was connected to my access point, downloading updates.

Here is my question, if Kubuntu saw my wireless and configured it, why wouldn't ubuntu?  Is there a way that I can take the driver from kubuntu, store it to a flash drive, and then use it with ubuntu or is that just asking for trouble?  Also, does it have to do with the desktop environment and having the drivers?  I guess I don't know enough yet, and will continue to research.

Thanks in advance,

---

### Post by chriscl on 2007-08-29
You shouldn't need to do this - I have the same model of laptop (Latitude D600) with the same model of Wireless Card, and the Wireless Card is recognised straight away upon installation (the "driver" is actually built into the linux kernel, which is identical between the two versions of Ubuntu you have tried).

To be honest, there is no reason why it *shouldn't* work; mine "just worked" out of the box?

When you installed Ubuntu, you go (from the main menu) "System", "Preferences" and "Hardware Information",  do you see "PRO Wireless 2200BG" in the list of devices?

That said, Kubuntu is (basically!) Ubuntu with the KDE Desktop, you could, if you wanted, install the Gnome Desktop onto your Kubuntu installation (there are posts on this forum regarding this issue!)

---

### Post by Damanther on 2007-08-29
I have Kubuntu on a D610, same wireless card though. When I did the install it had the wireless device disabled at boot. Maybe the same thing happened in your Ubuntu install somehow. I think if you bring up the network manager and make sure that guy is enabled you will be OK.

---

### Post by detox187 on 2007-08-29
Thanks you for your quick responses. 

 I don't know what is going on with the laptop, but I am determined to figure it out.  I did try last night to install the gnome environment on the computer.  I got to the login screen, loaded up gnome and it still wouldn't work.  So I am assuming that maybe it is disabled and I truly overlooked possibly the easiest fix.  I will try to enable it when I get home.

I was under the impression that Ubuntu and Kubuntu were the same kernel wise, so I was right in assuming that.  The desktop environment shouldn't affect the hardware though correct, it would only affect which programs can be used (guessing there) and the desktop environment.

I will tinker around with it after work, and hopefully get it to work.  I really like the gnome interface, kde is ok, but not my first choice.

---

### Post by StevoG7 on 2007-12-08
You may have to download NDISwrapper with the synaptic package manager, which will allow you to install the wireless card.  To do this you will have to download the driver from dell.com and run the file using wine (also available through synaptic).  This will extract the driver, and you will need to go to system-admin-windows wireless drivers, and add a new one.  Browse for the file where you extracted to, and it will be the only ".inf" file of the bunch, in the driver folder that was extracted.  Hope this fixes your problem, worked for me.

---

### Post by StevoG7 on 2007-12-09
Hey I've found a fix for this on my machine.  When turning on the computer enter the bios setup screen (f2).  Find the quick boot bios option and disable it, or if it is set to minimal boot set it to thorough.  It takes a few more seconds to load the bios and boot but nothing thats a problem.  Try it out, it worked for me, good luck.

---

