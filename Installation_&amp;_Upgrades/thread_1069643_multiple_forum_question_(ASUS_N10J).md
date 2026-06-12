---
title: "multiple forum question (ASUS N10J)"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by Fragrant Seahorse on 2009-02-14
Hey again friends.

I'm using this link[http://forum.notebookreview.com/showthread.php?t=315810]("http://forum.notebookreview.com/showthread.php?t=315810")  that I discovered on another old thread here to configure my beautiful new laptop and have encountered a slight problem that I figured somebody here could probably solve instantly.

On STEP 2 (installing the NVIDIA drivers) I have to drop down to text only, but my wireless connection disappears as soon as I do this and I can't wget the driver files.

Is there a way to reconnect to a wireless lan from text? There's a bunch of networks around here so I guess I need to be able to pick.

Thanks in advance 

p.s. sorry I couldn't tell if this was the correct forum~

---

### Post by ALLurGroceries on 2009-02-15
I guess using the wired ethernet isn't an option?

Depending on your wireless AP, if it's unencrypted, you can do a
```
iwconfig ap any essid any
dhclient wlan0
```

To associate and get an IP. You can replace 'any' with your AP's SSID/ESSID if you have lots of APs around. If you have encryption you specify that with the 'key' option to iwconfig. For more info on the iwconfig command see the man page.

If you have further problems please hit us up on NBR forums, the thread there is active. I only found your post from searching the net for 'N10J linux' while I was bored ;)

Edit: Alternatively, you could just download the NVIDIA installer files before you stop gdm/kdm, since there is no need for internet access during the installation process.

Good luck :)

---

