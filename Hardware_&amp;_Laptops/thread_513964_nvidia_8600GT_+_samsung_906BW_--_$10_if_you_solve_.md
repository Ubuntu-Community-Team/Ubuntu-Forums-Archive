---
title: "nvidia 8600GT + samsung 906BW -- $10 if you solve it!"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by John Nowak on 2007-07-31
I am PISSED. If anyone can solve this, I'll paypal $10 immediately.

I have a nvidia 8600GT and a samsung 906BW monitor. The nv driver works fine. The binary nvidia driver, **** that it is, only will run at 1024x768 or 1280x1024. Why the hell is widescreen so difficult in 2007!?

I've tried ingoring edid, setting modelines, manually setting sync/refresh rates, and every combination thereof. I'd return the monitor and get a non-widescreen model, but newegg won't let me return it, bastards that they are.

So seriously. $10 immediately if you solve this. Thanks.

---

### Post by Furesta on 2007-08-01
Hi, I have a 8600GT running in widescreen on a HannsG display, I used Envy to install the nvidia drivers, I ran nvidia-settings, set up 1440x900 and it works like a charm. What did you use to install the drivers?
Cheers

---

### Post by ricecakeburner on 2007-08-01
Hello,

I am also running an 8600 GT. I initially had a similar problem you had with the widescreen, but I used Envy as well to install the newest nVidia drivers (see [here]("http://www.albertomilone.com/nvidia_scripts1.html")).

After that, go to terminal and type:

```
sudo nvidia-settings
```

There should be an option to set resolution, so set your resolution to whatever you want it to (I chose "auto" because for some reason when I use 1680x1050 it craps out on me), then there should be a button near the bottom that allows you to save the option to xorg.conf.

Hope this may solve your problem!

---

### Post by John Nowak on 2007-08-03
> **Furesta said:**
> Hi, I have a 8600GT running in widescreen on a HannsG display, I used Envy to install the nvidia drivers, I ran nvidia-settings, set up 1440x900 and it works like a charm. What did you use to install the drivers?
Cheers

I tried envy and installing manually. And yes, they work -- But only at non-widescreen resolutions.

As for the HannsG, yes, I'm sure it works well. Unfortunately, this samsung sends nonsensical edid information.

---

### Post by John Nowak on 2007-08-03
> **ricecakeburner said:**
> Hello,

I am also running an 8600 GT. I initially had a similar problem you had with the widescreen, but I used Envy as well to install the newest nVidia drivers (see [here]("http://www.albertomilone.com/nvidia_scripts1.html")).

After that, go to terminal and type:

```
sudo nvidia-settings
```

There should be an option to set resolution, so set your resolution to whatever you want it to (I chose "auto" because for some reason when I use 1680x1050 it craps out on me), then there should be a button near the bottom that allows you to save the option to xorg.conf.

Hope this may solve your problem!

Nope, won't work. Again, the monitor outputs bogus edid data. It's out to get me. No "auto" anything is going to work. I need a way to hit it with a hammer. Oh, and 1440x900 won't show as an option either.

---

### Post by stchman on 2007-08-03
> **John Nowak said:**
> Nope, won't work. Again, the monitor outputs bogus edid data. It's out to get me. No "auto" anything is going to work. I need a way to hit it with a hammer. Oh, and 1440x900 won't show as an option either.

Using the nvidia driver add the following to your xorg.conf file

"1440x900"

Add this as the first in the list of resolutions.

---

### Post by John Nowak on 2007-08-03
> **stchman said:**
> Using the nvidia driver add the following to your xorg.conf file

"1440x900"

Add this as the first in the list of resolutions.

Again, doesn't work. 

BUT, I figured out the solution. The Samsung monitor, piece of crap that it is, outputs the WRONG edid information. I used some windows edid editor (Phoenix EDID Designer) to rewrite it, and loaded it by adding 'Option "CustomEDID" "DFP-0:<path>' to my Device section.

Thanks for the attempts guys! And don't buy a Samsung 906BW!

---

