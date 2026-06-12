---
title: "New Kernel update now ipw2200 is broke"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by unique on 2005-09-27
Yesterday my update manager installed a new kernel update... everything went as expected. After a reboot i noticed that I had no more wireless. No prob I just remove the ieee80211 and the ipw2200 driver and then did a reinstall. 

I have wireless agian but my problem is that when I issue:
```
sudo iwconfig eth0 mode monitor
```

I get:
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Invalid argument.
```

Anyone know what I did wrong or what I need to do to be able to set my card into monitor mode agian?

---

### Post by mlomker on 2005-09-27
> moniter mode agian?

It's spelled **monitor**.

---

### Post by unique on 2005-09-27
[QUOTE=mlomker]It's spelled **monitor**.[/QUOTE]

ya sorry typo...

---

### Post by mlomker on 2005-09-27
[QUOTE=unique]ya sorry typo...[/QUOTE]

Is that why it didn't work?  I made the comment because I thought you might have made a typo when entering the actual command.

---

### Post by unique on 2005-09-27
[QUOTE=mlomker]Is that why it didn't work?  I made the comment because I thought you might have made a typo when entering the actual command.[/QUOTE]

No I just made the typo when posting to this thread.

I did just however notice that I have to linux-headers in my /usr/src dir....
I have linux-header-2.6.10-5 & linux-header-2.6.10-5-386
I'm running the 2.6.10-5-386 kernel. could that be a prob?  if my active kernel is 2.6.10-5-386 should the ipw2200 driver use the 2.6.10-5-386 linux-headers? Or does it matter?  Not even sure if this makes a diff.

---

### Post by unique on 2005-09-28
Ok I got it to work!

By commenting out a couple lines in the Makefile and reinstalling i got monitor mode to work agian.

First
```
cd ipw2200-1.0.6
```

Next
```
gedit Makefile
```

Find ```
ifndef CONFIG_IPW2200
```

And replace with ```
#ifndef CONFIG_IPW2200
```

Find ```
endif
```

And replace with ```
#endif
```
Save and close gedit

Then run
```
make
sudo make install
```

And your all set!

here is a sample of my make file:

```
# If CONFIG_IPW* isn't set, we'll assume the user has never configured
# their kernel to include this module and set up some defaults.
#
# NOTE: If you have previously added the IPW project to your kernel 
# 	and configured it for inclusion, these settings will be 
#	overridden by your kernel configuration.
**#ifndef CONFIG_IPW2200**
EXTERNAL_BUILD=y
CONFIG_IPW2200=m
CONFIG_IPW_DEBUG=y
CONFIG_IPW_QOS=y

# If you are not interested in using monitor mode, simply comment out:
#
# NOTE:  If you have problems compiling due to IW_MODE_MONITOR not being
#        defined then you need to update the wireless extension version
#	 installed in your kernel, or comment this line out.
CONFIG_IPW2200_MONITOR=y

**#endif**
```

The 2 line that are in bold are the lines I commented out.
**ifndef CONFIG_IPW220** and the line...
**endif**

Now when I type **sudo iwconfig eth0 mode monitor** it works!
You may need to reboot first for this to work.

---

