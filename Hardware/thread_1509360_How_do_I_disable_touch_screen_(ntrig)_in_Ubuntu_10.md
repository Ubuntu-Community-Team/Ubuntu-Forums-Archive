---
title: "How do I disable touch screen (ntrig) in Ubuntu 10.04 (HP TX2) ?"
date: 2010-06-14
forum: Hardware
---

### Post by 2bittech on 2010-06-14
I have a HP tx2 touchsmart laptop and I have installed 32 bit version of  Ubuntu 10.04 on it. (Kernel 2.6.32-22)

The touchscreen and the digitizer pen work out of the box, however, the  problem is that it disables the touchpad and forces me to use the  Digitizer Pen (stylus) which is very annoying.

I have already searched for ways to disable touchscreen without much  success, most of the posts discuss enabling it rather than disabling  it.The file /etc/X11/xorg.conf does not exist and I have removed the  wacom drivers:

sudo apt-get purge wacom-tools xserver-xorg-input-wacom

I believe that ntrig is using some other drivers/packages which may need  to be removed. 

Ideally, I'd like to enable both Touch Screen (nTrig) and the Touch pad. But I  am willing to give up touch screen functionality in favor of the  touchpad. Please help or point me in the right direction.

---

### Post by Favux on 2010-06-14
Hi 2bittech,

Welcome to Ubuntu forums!

Normally I'd tell you to go to "6) Turning touch on and off" in the N-trig HOW TO.  But you aren't using the wacom drivers.  My guess is it is the evdev driver that has your digitizer.  Check in Xorg.0.log in /var/log to find out which driver.

By the way there is no wacom-tools in Lucid.  And purging xserver-xorg-input-wacom will remove xserver-xorg-input-all also, which I doubt you want to do.

Hope this helps.

---

### Post by 2bittech on 2010-06-14
> **Favux said:**
> Hi 2bittech,

Welcome to Ubuntu forums!

Normally I'd tell you to go to "6) Turning touch on and off" in the N-trig HOW TO.  But you aren't using the wacom drivers.  My guess is it is the evdev driver that has your digitizer.  Check in Xorg.0.log in /var/log to find out which driver.

By the way there is no wacom-tools in Lucid.  And purging xserver-xorg-input-wacom will remove xserver-xorg-input-all also, which I doubt you want to do.

Hope this helps.

Hi Favux,

Thanks for your response, I was just about to give up on this.

As per Xorg.0.log I am using "evdev" driver. So where does that leave me, and what are my options? Install wacom and somehow force Ubuntu to use it instead of evdev?

Meanwhile I will look up more info on evdev.

Cheers!

---

### Post by 2bittech on 2010-06-14
One more weird thing that I noticed is that both the touchpad and the touchscreen work on the login screen. But the touchpad stops working as soon as I login.

---

### Post by 2bittech on 2010-06-14
Found the solution. The post below seems to have done the trick for me. Both, the touchpad and the touchscreen work.


[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727)

> 
[Chris  Highfield]("https://launchpad.net/%7Ecmhighfield")             wrote             on 2010-04-12:                                                             [  #9]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727/comments/9")                                                        I have managed to resolve the problem on  my HP DV2054ea laptop by installing the following two packages:
 gpointing-device-settings
touchfreeze
 I hope this helps others.
 Regards,
 Chris.

        



---

