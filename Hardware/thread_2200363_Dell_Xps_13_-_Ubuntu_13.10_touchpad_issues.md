---
title: "Dell Xps 13 - Ubuntu 13.10 touchpad issues"
date: 2014-01-18
forum: Hardware
---

### Post by Aman_Khosa on 2014-01-18
I am having issues with my touchpad, it works however scrolling does not work. I have tried installing synaptiks, gpointing-devices, dconf-editor, and tried modifying certain settings however nothing seems to work. Every time i open synaptiks i am greeted with the message "no synaptics driver loaded". The problem, from what i can see is that ubuntu is recognizing the touchpad as a generic mouse, as in system settings under the mouse & touchpad settings there are only options you would get for a mouse. Any help would be appreciated.

---

### Post by gunksta on 2014-02-12
I am having almost the exact same problem you appear to be having. I haven't had any luck either and I don't see much written here about it.

Brand new Dell XPS 13 Developer edition. I did a clean install using Kubuntu 13.10. Over-all, I am really happy with it, but the touch pad is largely a brick and I can't get the touch screen to work. Of the two, I'm the touchpad bothers me more. I'm not sure I really think touching my screen is necessary on a laptop.

---

### Post by gunksta on 2014-02-13
I upgraded my kernel last night and now the touch screen seems to work. But, Synaptiks still complains about not being able to find a touch pad (clearly it is mistaken) and I can't find any way to adjust the settings of the touch screen.

I haven't tested multi-touch on the screen. In fact, I kinda think the touch screen is silly on this device. I tried using it some last night and noticed it was real easy to tip the laptop over because the aluminum backing of the lid is so much heavier than the carbon fiber in the base. Perhaps they should have gone 100% CF. It would have been even lighter AND it might have balanced better when I put my paws all over the screen.

---

### Post by gunksta on 2014-02-15
It took me a few days, but I have more or less beaten this bug. I hope the OP logs in and sees this AND I hope it is useful for anyone else fighting this bug.
Disclaimer - I am running Kubuntu 13.10. This should work for all 13.10 Ubuntu variants but I can't easily verify that this works on 12.10 or 13.04.

First, I found this:
[https://wiki.ubuntu.com/DebuggingTouchpadDetection#In_case_Touchpad_features_like_scrolling.2C_tapping.2C_etc._do_not_work_at_all.](https://wiki.ubuntu.com/DebuggingTouchpadDetection#In_case_Touchpad_features_like_scrolling.2C_tapping.2C_etc._do_not_work_at_all.)

I ran:

```
[COLOR=#333333]cat /proc/bus/input/devices > ~/devices [/COLOR]
```

And looked into my new ~/devices file. I had seen something on the Internet that the dysfunctional touchpad was probably being incorrectly registered as a regular mouse. So, I looked for a regular mouse, other than my Microsoft ArcTouch, which ironically worked perfectly out of the box.

I found the following:

```

I: Bus=0018 Vendor=06cb Product=2734 Version=0100
    N: Name="DLL060A:00 06CB:2734"
    P: Phys=
    S: Sysfs=/devices/pci0000:00/INT33C3:00/i2c-8/8-002c/input/input8
    U: Uniq=
    H: Handlers=mouse1 event8 
    B: PROP=0
    B: EV=17
    B: KEY=30000 0 0 0 0
    B: REL=3
    B: MSC=10

```

After seeing my touch pad registered as a mouse, I did some googling and found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1263319](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1263319)

In the end, I was able to fix this by creating a file (as root) called:
```
/etc/modprobe.d/blacklist_i2c_hid.conf
```

Open the file and add one line that looks like
```
blacklist i2c_hid
```

Restart your computer. Your problems should be mostly solved. There are some comments that if you use standby to memory frequently, there are some problems where the touch pad does not always reinitialize properly, but I have not yet experienced this. But, I have only used suspend to memory twice since using this fix.

As always, YMMV and Good Luck!

---

### Post by David_Peter on 2014-02-26
Thanks gunksta, great response, very educational, it worked flawlessly

---

### Post by gunksta on 2014-03-02
Glad it worked for you.

---

### Post by kornelixgmx.de on 2014-04-05
Thanks gunksta. Worked fine for my Dell XPS 13.

---

### Post by Untarnished_Truth on 2014-04-28
> **gunksta said:**
> 
```
blacklist i2c_hid
```


Same problem here, on a Dell XPS Duo 12.  I might add that I also ran Kubuntu 14.04 Live on this ultrabook, and still no touchpad. 

Anyway this thread's solution worked well for me (confirmed only for Kubuntu 13.10), thanks gunksta!

---

### Post by psmedley on 2014-06-09
FWIW with the 3.15 kernel, this hack prevents the touchpad working at all. Removing the hack allows the touchpad to work, however two-finger scrolling doesn't work :(

---

