---
title: "Touchpad ceased working"
date: 2010-05-14
forum: Hardware
---

### Post by npattillo on 2010-05-14
I have an Acer Laptop w/ Ubuntu 10 that the touchpad stopped working on. It works on the login screen but does not when I login. I have to use a USB mouse there after. Any help from anyone on this as to what I should do to fix the problem?

---

### Post by nmyrick on 2010-05-14
Have you tried hitting Fn-F7 to enable or disable the touchpad?

---

### Post by npattillo on 2010-05-14
Yeah, doesn't do a thing. What is frustrating is that it used to work and now it doesn't. I wish I knew what else to do.

---

### Post by nmyrick on 2010-05-14
Yeah, I'm having the same issue then. Mine worked for a while with Ubuntu 10.04, but then it just stopped today. Rebooting doesn't help, and reinstalling the Synaptics touchpad driver doesn't help either.

I happened to have installed Podslueth for Banshee right before this started happening, but I don't think that would have had anything to do with it.  Banshee was not detecting my second gen IPod nano, but it does now.

---

### Post by nmyrick on 2010-05-14
I have an active post for the same issue at 
[http://ubuntuforums.org/showthread.php?t=1483458](http://ubuntuforums.org/showthread.php?t=1483458)

---

### Post by npattillo on 2010-05-14
Thanks for your help. Hopefully, someone will have clue about how to resolve it.

---

### Post by nmyrick on 2010-05-14
I hope so too. It is really weird that it just started happening.

---

### Post by nmyrick on 2010-05-14
I found the following post, however, what I have found out is that I have no xorg.conf file.  Maybe that's the issue.

When you click on this, scroll down to the Synaptics Touchpad section.

[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#touchpad](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#touchpad)

---

### Post by nmyrick on 2010-05-14
I think I may have found the root of the problem, but I still don't know the fix.

I installed tpconfig, which is touchpad configuration software that is supposed to work with synaptics touchpads. When I tried to run it, I got the following error.

nmyrick@laptop1:~$ tpconfig
Could not open PS/2 Port [/dev/psaux].

So, apparently the touchpad is on a PS/2 port, but it is not being recognized.

---

### Post by npattillo on 2010-05-15
Thanks for the tips. I don't have the xorg file either. I have no clue what to do. Thanks again - hope we can find a solution. It would be nice to have that back.

---

### Post by nmyrick on 2010-05-15
I think I found the fix.  It is the weirdest thing, but this worked for me.

Step 1: Login to your laptop

Step 2: Put your laptop in Stand by Mode after you logged in

Step 3: Wake your laptop from Stand by Mode

Step 4: While at the Login Screen, Press the key combination Fn+F7 (or whatever Function key combination enables and disables your touchpad)

That's it.  It worked for me.

---

### Post by npattillo on 2010-05-15
Ok - Looks like I might have figured out the issue and fixed it. I went into the users and groups GUI under Administration and noticed that I was not logged in as an administrator. I changed it to that and went in under advanced settings and noticed that as an administrator, there were several features that I was not allowed to access under this section. After changing that and restarting, I am not sure why, but my touch pad works great. Hope it helps.

---

### Post by Elmer Fudd on 2010-05-18
Pad used to work until I disable with keyboard switch then wont togle back on (9.10 and 10.4) External mouse continues to work in all cases.
Now Pad works for login then continues to work until just before the first task bar loads.  Works fine under Win7. none of the above solutions worked for me. :(

Ubuntu 10.04
Acer 7736Z

---

### Post by liutszho on 2010-05-19
Hi all,

I type in "gconftool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled -t boolean true" in my terminal to get it working,

Ive added it to startup applications, not sure if that will work automatically, but doing it through terminal does the trick!

---

### Post by RainEverAfter on 2010-05-22
> **liutszho said:**
> Hi all,

I type in "gconftool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled -t boolean true" in my terminal to get it working,

Ive added it to startup applications, not sure if that will work automatically, but doing it through terminal does the trick!

Yehey! This worked code worked for me even without adding it on the startup applications. I've been searching for an answer for two days now.
Note: It stopped working after I've inserted my usb wireless mouse and ran automatic updates. So I'm not exactly sure which one caused the problem. Anyway, I'm off to search for an answer to my other problem - sound. thanks again!

---

### Post by liutszho on 2010-05-23
> **RainEverAfter said:**
> Yehey! This worked code worked for me even without adding it on the startup applications. I've been searching for an answer for two days now.
Note: It stopped working after I've inserted my usb wireless mouse and ran automatic updates. So I'm not exactly sure which one caused the problem. Anyway, I'm off to search for an answer to my other problem - sound. thanks again!

So the gconftool line doesn't work for you anymore?

---

### Post by RainEverAfter on 2010-05-23
oh sorry for the confusion... what i meant is that the problem started after i've used my usb wireless mouse, ran automatic updates, played with disable button for the touchpad to see if it works... then after I restarted the machine thats when the problem happened.

but all is good now after the gconf, good thing I found this thread! :)

---

