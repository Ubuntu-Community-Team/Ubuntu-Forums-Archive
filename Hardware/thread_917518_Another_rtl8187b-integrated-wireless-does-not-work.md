---
title: "Another rtl8187b-integrated-wireless-does-not-work thread!"
date: 2008-09-12
forum: Hardware
---

### Post by HighFrictionZone on 2008-09-12
NOTE: I solved my problem, see third post.
Also: This is only me having a problem with the Intrepid (8.10) testing. If you are using Hardy (8.04), this does not help you at all. 

I have a Gateway ML6732 laptop. It has the mentioned-in-the-title integrated RTL 8187B wireless. Based on the number of help-me threads with this card, I know I'm not alone.

At any rate, at one point in time, I actually had it set up, it WAS working.

Then I screwed around and forgot to take regular backups. One system restore later, I realize that while my firefox profile and files were saved, my wireless settings weren't.

The only results I EVER got was with ndiswrapper. I could see the wireless network. I could enter my connection info and WEP password. It starts connecting, gets as far as requesting a network address, and then fails. Sorry that I don't have a more detailed explanation, but I'm on my Vista partition right now. I'll reboot shortly to get exactly where it stops working. 

I will note that:
After mucking about for a while, I heard somewhere that the 2.6.27 kernel would have better native support for it. So off I go to try out the latest intrepid build. Didn't help, but I suppose that I deserve it for not compiling my own kernel. Whatever. Nothing mission-critical is on the drive, so I can wipe it and start over. But any way I can avoid the effort to reinstall would be very much obliged.

Additional information:
Results of lsusb:
```
Bus 007 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

When using ndiswrapper and either the windows 98 or the windows xp drivers, it nm-applet only gets as far as "Requesting a network address from the wireless network 'WarpZone'" (in the tool tip). I'll try and connect to it manually via the command line and get the exact output shortly.

I am using the latest ndiswrapper.
If I have any additional information, I'll edit back with that later.

---

### Post by HighFrictionZone on 2008-09-22
Right, so. Update. I removed network manager because I wanted to try Wicd. That didn't help (but I love the interface!)

I've removed ndiswrapper because even though that let me view my wireless networks, no selection/combination of windows wireless drivers would ever let me connect. I see via modprobe -l that:
```
philbert@lappy2-ubuntu:~$ modprobe -l rtl8187
/lib/modules/2.6.27-3-generic/kernel/drivers/net/wireless/rtl8187.ko

```

Is this the included rtl8187b support that is supposed to be working? Because it isn't doing a very good job of, you know, working.

I'm going to try a reboot because I forgot to remove ndiswrapper from my /etc/modules - I'll see if that clears anything up. Failing this, I'm kinda at a loss. Go back to Network Manager? Install the hacked and patched drivers? Reinstall ndiswrapper again? Some fourth option that I don't know about but is dead simple. (I'm hoping for that last one!)

Also, bump.

---

### Post by HighFrictionZone on 2008-09-22
HA HA HA! SUCCESS!

As it turns out, I forgot to actually add the module, so while the module was installed and ready to go, I had to activate it or whatever the fancy terminology is
```

sudo modprobe rtl8187

```

So now I just add this to /etc/modules and I'm set, right? Funny how the simplest of things trip you up. I just hope that when 8.10 is finalized and released as a finished product, so to speak, this detection and activation is completely automated. Or something. I honestly don't know why it wasn't auto-detected and loaded, probably still experimental or something.

But it functions and I can now browse the web. Intrepid rocks, even if it is still in testing. (Second monitor support was fixed, so now I can use my second monitor correctly, and now WiFi is fixed so I can do wireless, two down, now they just need to get the backlight control working properly and my laptop will be completely functional!)

Edit: I will note that it ALMOST functions. I can see networks, and I can connect, and occasionally I can load up webpages, however if they load at all, they load slowly. More often than not things just don't load. Makes downloading things... difficult. Sure, I can technically go online, but it is currently just easier to plug a cable in. Which defeats the whole purpose =(

Any suggestions for fixing it?

---

