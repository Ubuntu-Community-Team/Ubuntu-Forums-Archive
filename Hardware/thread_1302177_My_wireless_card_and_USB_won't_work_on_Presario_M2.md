---
title: "My wireless card and USB won't work on Presario M2000?"
date: 2009-10-26
forum: Hardware
---

### Post by MrMusic25 on 2009-10-26
Hi. I like Ubuntu 9.04 and decided to replace Windows with it on my Compaq Presario M2000 laptop computer. so far it has been great, but now I've run into the problem of the integrated wireless card won't work. It just says "Device Not Ready". How do I make it work? also, how can I make the USB's work, too? I plugged in a flash drive to see if it would work, and nothing even happened. If you have an answer to either of these questions, or have another post that might help, please post it. thanks you for your help! =)

---

### Post by poltr1 on 2009-12-02
You'll probably need to plug in to a wired network before attempting this, as you'll need to download the drivers.

For my Compaq Presario M2000 running Karmic, I tried 
sudo apt-get install ndisgtk 
as suggested in a similar topic for Kubuntu.  Then I went into Administration/Hardware Drivers and activated the "Broadcom B43 Wireless Driver".  Then I rebooted.  I was then able to view the local wireless networks.

---

