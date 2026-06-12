---
title: "Monitor problem in 9.10"
date: 2010-01-25
forum: Hardware
---

### Post by begambegam on 2010-01-25
Hi,

I have installed Ubuntu 9.10 and everything with monitor and resolution was fine until...
I installed nvidia drivers, reboot laptop and it started. Now laptop screen is **divided into six little screens** with terrible resolution (640x480 and less). When I try to change something in display section, it shows me, that monitor is not recognized. But it detects my video card (Nvidia GeForce GT 130M). When I unload Nvidia drivers it works fine again.

Any ideas about that? Please, help.

---

### Post by Grenage on 2010-01-25
Install the drivers, then install and run nvidia-settings:

```
sudo apt-get install nvidia-settings
gksu nvidia-settings
```

It will give you decent control of the proprietary drivers.

---

### Post by begambegam on 2010-01-25
That's the problem. When nvidia drivers are active, they give me that problem and in nvidia-settings I can't do anything about resolution or display. When drivers are not active, nvidia-settings just give me nothing.

---

### Post by Grenage on 2010-01-25
So within nvidia-settings, you cannot change anything under "X Server Display configuration"?  You are definitely running them as root (gksu)?

Which version of drivers are you using?

---

### Post by begambegam on 2010-01-25
Yes, I can't change anything, and I'm trying it under the root. 
It's 185 version.

And there is no resolution set in my xorg.conf.

---

### Post by Grenage on 2010-01-25
Ok, I've net seen the issue with separate screens before.  xorg.conf won't have anything in it unless you've manually created an entry, display detection is performed by EDID in 9.10.

I could point you in the direction of a guide I wrote for manually specifying resolutions, but I've never used it when dealing with a split-screen display.

You won't do any harm by specifying it in there, so have a look [here]("http://www.grenage.com/xorg.html").

---

### Post by begambegam on 2010-01-25
Okay, I was able to get a resolution I need, but my display is still split. I'm thinking, maybe this is the problem?
[IMG]http://img709.imageshack.us/img709/2040/screenshotuc.png[/IMG]

---

### Post by Grenage on 2010-01-25
Was that using xorg.conf, or the nvidia control panel?  I'll see if I can find anything about the splitting.

---

### Post by Grenage on 2010-01-25
Put the following in xorg.conf under the *Device* section:

```
Option "ModeValidation" "NoTotalSizeCheck"
```

---

### Post by begambegam on 2010-01-25
Thank You very much! That line helped, yey! : )

Firstly i edit xorg.conf, after that I was able to see all nvidia-settings panel, and I was able to write resolution by hand.

Now display is okay : )

---

### Post by Grenage on 2010-01-25
Glad to hear that it's all sorted :)

---

### Post by hoho32 on 2010-02-13
sorry guys .please help 
where i can type those order 


 	Code:
 	Option "ModeValidation" "NoTotalSizeCheck" 
where i can put xorg.conf window and where i can find device section

---

