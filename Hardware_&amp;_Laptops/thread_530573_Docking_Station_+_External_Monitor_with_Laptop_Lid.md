---
title: "Docking Station + External Monitor with Laptop Lid Closed"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by oddball on 2007-08-20
Evening all...

I thought I would firstly share a bit of knowledge and then ask how to improve it.

After installing the Nvidia drivers on my Dell XPS M1710 running Feisty, my laptop would boot up with the External monitor working, but then as soon as GDM starts it turns off. Opening the lid of my laptop revealed that it had infact reverted to the laptop panel.

It took me bloomin' ages to find out how to fix this but eventually got there, so here's what I did:

1. Started up the Laptop off the dock and logged in
2. Placed laptop on the dock and ran:
```
sudo nvidia-settings
```
3. Clicked on 'X Server Display Configuration'
4. Clicked on 'Detect Displays'
5. Clicked on the disabled display and made a mental note of the device name for the external monitor which is in brackets (in my case DFP-2)
6. Clicked on Save to X Configuration File
7. Clicked on Quit
8. Edited the device section of my /etc/X11/xorg.conf file as per the following:
```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7900 GTX"
**    Option         "UseDisplayDevice" "DFP-2"**
EndSection
```
9. Saved it and quit

Now when GDM / X starts on the dock it uses the external monitor, and when it starts off the dock it uses the laptop display panel giving a warm(ish) dock / undock setup so long as you are prepared to restart X using CTRL + ALT + BACKSPACE

So now, what I would love to do is somehow write a dock / undock script to set this but without having to restart GDM / X, but have no idea if that's possible?

Regards,
Gaz.

---

