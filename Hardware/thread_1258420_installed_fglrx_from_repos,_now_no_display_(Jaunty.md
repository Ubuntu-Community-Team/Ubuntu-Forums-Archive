---
title: "installed fglrx from repos, now no display (Jaunty)"
date: 2009-09-05
forum: Hardware
---

### Post by anonymousT on 2009-09-05
I just installed xorg-driver-fglrx from synaptic. The next time I turned it on I get no display (all black except some garbage on the top of the screen), it won't even go to the login screen. 

Is there a way to remove the driver and revert to default xorg driver for ati cards using the live cd?

I have ati x1400 on a dell inspiron 6400 / e1505

---

### Post by sinfony on 2009-09-05
At the Grub menu, pick the recovery mode kernel; when presented with options, pick Root prompt without networking.  At the command line, type:
```

sudo apt-get --purge remove xorg-driver-fglrx fglrx-control
```

You may need to reconfigure the x-server; either do so manually or enter:
```
sudo dpkg-reconfigure xserver-xorg
```
and follow the prompts.

I had exactly this problem not an hour ago.

---

### Post by anonymousT on 2009-09-05
Hey, that worked great, thanks!

So, what do you use for your ati card then?

---

### Post by Yellow Pasque on 2009-09-05
The radeon open-source driver is pre-installed and selected by default.

---

### Post by lseguin on 2009-09-07
Brilliant! Thanks so much. Just changed my video card and then I couldn't boot into Ubuntu at all. After reconfiguring my bios to always recognise my wireless usb keyboard I was able to boot into terminal from grub then used the first command from a recovery terminal window and voila it's booted up and recognised and updated my video driver. Now even have a better resolution than the old card. Wahey!

Thanks again!:popcorn:

---

### Post by anonymousT on 2009-09-09
does the open source driver support automatic power savings? Also, flash runs slowly, I have Adobe-flashplugin 10. I'm not sure if that the plugin's problem or the graphics card's

---

