---
title: "Upgrade to Jaunty X display is messed up"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by baileyone82 on 2009-04-27
Hello,

Just upgraded to Jaunty. Same thing happened when I upgraded to Ibex.

After the install and reboot, it goes to a page that looks like it should be the login page, but you can't read or see what is going on.

After the Ibex upgrade I found a utility in the forums that I ran from the command line that took me through a wizard that fixed everything. The wizard was some sort of graphics tool (and other stuff too, like keyboard setup, etc.). It was a bunch of blue screens with text.

Anyone know what I am talking about? Since this fixed my problem last time, I would like to run it again.

Another frustration with upgrading this time is the USB errors:
"usb 1-1:device descriptor read/64, error -110"

I have not even started to tackle that until I get my screen back.

AMD64
ATI video card
22" widescreen samsung

---

### Post by aikiwolfie on 2009-04-27
Have you tried this?
```
dpkg-reconfigure xserver-xorg
```

---

### Post by baileyone82 on 2009-04-28
I am pretty sure that is what I was looking for, although it asked me about the keyboard only. I seem to remember last time it asked more about the monitor and resolutions, etc.

I also got rid of the fglrx driver due to my ATI card:
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16814121538"]http://www.newegg.com/Product/Product.aspx?Item=N82E16814121538
[/URL]

I used this to do that:
```
apt-get remove xorg-driver-fglrx
```

This action was based on reading other posts about the FireGL drivers.

One of the two worked. I still get the messed up screen, but just for a split second before the login screen appears.

I would say fixed! Thank you! :)

Now on to the USB error :(

---

