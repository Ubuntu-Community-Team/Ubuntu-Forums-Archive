---
title: "Backlight never goes off!"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by roobarb! on 2007-02-22
Hi all!

Need a bit of help on this one. I've installed Ubuntu Server 6.06.1 on a beat-up old Dell C510 laptop I got off eBay, so I can use it as a little home server. It works really well, except that the backlight on the display never goes off when the lid is up.

Fine, you might say, just put the lid down. The problem there is that although the backlight goes off and I can restore the screen when I reopen the lid, if I reboot the server with the lid down it doesn't restart - it simply turns itself off. Normally I would run the laptop with the lid closed, but if I know I'm going to be doing some work on it and it might need restarting, I would prefer to know that the backlight would power down after a few minutes. And yes, I have these things configured in the BIOS, but it makes no difference.

I've heard 'vbetools' bandied about a bit in the forums, but I can't find them anywhere. I've also heard about using aspects of the Gnome desktop, but I don't really want to go so far as to install the whole of Gnome just to get the display to turn off (although if I have to, I probably will).

Any advice?

TIA,

    Andy.

---

### Post by Richard Kut on 2007-02-23
Hello roobarb! Have you tried changing the settings in the power management console? I am not in front of my Ubuntu laptop right now, but if I recall properly you can access the settings by right clicking on the battery icon in the panel. Please update this post with your results.

---

### Post by roobarb! on 2007-02-23
Thanks for the reply, Richard - but I'm running the server version here. Just a console, so there's nothing for me to right-click on. :(

Although I'd prefer not to, I would install the desktop environment if it were the only way to get this working, although I wouldn't be leaving it to boot into Gnome all the time.

Any other clues? Do you know if I'm on the right track with this 'vbetools' thing, or am I barking up the wrong tree?

Thanks,

    Andy.

---

### Post by Richard Kut on 2007-02-23
I have never used it myself, but this site describes it's uses:

[http://www.columbia.edu/~ariel/acpi/acpi_howto.0.2a.html]("http://www.columbia.edu/~ariel/acpi/acpi_howto.0.2a.html")

I think that you will want to use the command:

vbetools dpms off

---

### Post by roobarb! on 2007-02-23
Blimey, charlie! It works!

After all that, my major problem was that it's 'vbetool' and not 'vbetools'. To get it working I followed this complicated procedure:

```
apt-get install vbetool
vbetool dpms off
```

Thank you very much for pointing me the right way! I guess there's nothing I can do about the 'shutting-down-not-rebooting-when-the-lid's-closed' problem - seems like that's just the way this thing was made - but being able to kill off the backlight when I'm away is a real bonus.

Thanks again!

Andy.

---

### Post by roobarb! on 2007-02-23
Drat. Double posted due to squiffy internet.

---

