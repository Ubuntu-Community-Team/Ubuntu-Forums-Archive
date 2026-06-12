---
title: "Wanting to set display defaults in terminal"
date: 2010-11-29
forum: Hardware
---

### Post by DJJoeJoe on 2010-11-29
Freshly installed from wubi, upgraded to 10.10, first thing I do is bork myself into booting straight into the terminal with no display.

I have 2 monitors, which I should state right off the bat. So when trying to make those actually work I ran into this issue, and I know this is my fault to assume I could get things working.

After setting the display settings for the two monitors, to the option in between twin view and the default and learning that I need to sudo nvidia-settings to even get it to save to the file (should it just not allow if not running sudo? sigh) I restart and it boots into terminal. sudo startx doesn't work, says no display found etc. So I assume this borked the display stuff.

I'm wondering how I can restore my display stuff to default from the terminal, and I guess just make due with the default open source drivers for my video card :(

As a side request, it would be nice to know if it's possible to get 2 monitors working with ubuntu and an nvidia card. Seeing as I have them etc, I'd rather they work :) Or do I have this whole ubuntu thing wrong and I should expect to run it only on a secondary machine?

---

### Post by Yarui on 2010-11-29
I have done this to myself more times than I care to remember and every single time I have to do some reading to figure out how to fix it.  I have never done dual displays so I can't really help you there, but getting one display back should be a good start.

I generally start by trying to use an auto configuration tool, like nvidia-xconfig.  I think there are actually 2-3 different tools like this that you can try out if I remember correctly, nvidia-xconfig is just the only one I can remember at the moment.  Basically you just run the utility and it does all the configuration stuff for you.  You then restart your computer and if you are lucky, your display will be working again.

If that doesn't work, you can try to simply uninstall all video drivers and then reinstall the nvidia display drivers then restart.

```
sudo apt-get install nvidia-current
```

I think this is the method that has worked for me more often than anything else, actually, so it may be the better place to start.  I don't think there should be any need for you to revert to generic drivers.  In my experience nvidia-current is the best display driver to run, so I would do my best to get that working before moving to something else.

If neither of those methods works for you, you might end up having to manually set up an xorg.conf file.  The file is located at /etc/X11/xorg.conf.  If there is no avoiding this method, you are going to need to read up on setting up an xorg.conf file.  This is the last thing you should try because it is the least desirable method that will take a lot more work than the others.

---

