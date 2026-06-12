---
title: "Radeon 9200 and FireWire problems"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by The Keeper on 2005-07-28
Hello,

I'm new to Ubuntu and my linux expertise is limited to quite basic level, but that's why I installed Ubuntu, to learn more. :)

Now to the point. I installed Ubuntu AMD64 on my second AMD64 system which uses Radeon 9200SE. With default ATI drivers the login screen is completely corrupted and unusable, even though I followed some of the instructions I found in these forums, I couldn't solve the problem. I replaced ati driver with vesa driver and that solved the login screen corruption problem, even though there is still slight corruption noticeable for a few seconds. However, I would still like to get the most out of the card. And I am quite sure the card's fine, it does not seem like I'm the only one with this problem.

The second problem is that I have two computers networked together via 400Mbit FireWire, however Ubuntu does not recognize FireWire as a network connection and I am unable to set any ip's and subnet's on it. There was next to nothing about firewire network discussion on these forums, so I didn't even get any good hints.

Sorry for being a newbie, but a man's gotta start somewhere. :)

---

### Post by yyagol on 2005-07-28
hi
did you install the "fglrx" driver ?
i have the same ATI RADEON 9200 se and it work perfect
with the "fglrx" driver ,i got  the TV out and it work for me
heare is waht i did :
```
 $ sudo apt-get install linux-restricted-modules-<uname -r> xorg-driver-fglrx
``` 
then i did copy the original xorg.conf to another location
in case somthing go wrong
```
 $ sudo cp /etc/X11/xorg.conf /<path to location>/xorg.conf-old
``` 
next step is to edit the xorg.conf by adding this lines
under  Section "Device"
```
 Driver        "fglrx"

# === Video Overlay for the Xv extension ===
      Option         "VideoOverlay"         "on"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
      Option         "OpenGLOverlay"     "off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
      Option         "UseInternalAGPGART"     "no"
``` 
save xorg.conf and restart the X with Ctrl+Alt+Backspace
log in and run $startx
 \\:D/

---

### Post by The Keeper on 2005-07-29
Yes, I tried that as well. The result was black screen where login screen was supposed to appear. :(

---

### Post by The Keeper on 2005-07-29
I tried it again and this time it worked. Dunno what went wrong last time.
Thanks. :)

Anyone got any ideas how to get firewire networking to work?

---

