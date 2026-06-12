---
title: "Limit Laptop CPU Frequency on AC"
date: 2008-06-22
forum: Hardware
---

### Post by pmaconi on 2008-06-22
My laptop has a terrible overheating problem. Whenever it runs at 100% while on AC, it goes up to about 90 Celsius. If I unplug it, the maximum frequency it can reach is 800 MHz, with a temperature of about 55 C. I need a way to change the maximum AC frequency from 2,300 MHz to something around 1,500 MHz (or lower, depending on how hot that gets). 

Can someone tell me how to do this? I've searched around on the forums for a while, but haven't found a solution.

---

### Post by damphoud on 2008-06-22
what is the output of:

sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

---

### Post by pmaconi on 2008-06-22
```
2300000 2200000 2000000 1800000 1600000 800000 

```

---

### Post by damphoud on 2008-06-22
hrm, now i dont know how to do this but... if temp is over lets say 75 then run:

cpufreq-selector -f 1600000

or what ever speed you want of the output... i just don't know where to add this

---

### Post by nightwolf2k5 on 2008-06-22
u could use emifreq-applet.
Goto system -> administration -> synaptic package manager
there click on find and type cpu
scroll down and u will find emifreq-applet..
install it..
restart.
once u are in ubuntu, right click on one of ur panels and click on add to panel. There should be a new cpu related applet. There you can manually set the clock speed or choose automatic. You can also view ur cpu temp with this applet.

p.s. the speed needs to be set everytime u start ubuntu. It would be at automatic otherwise.

---

### Post by pmaconi on 2008-06-22
Thanks, that will work as a temporary solution. But is there a way to globally restrict the maximum frequency?

---

### Post by damphoud on 2008-06-22
> **nightwolf2k5 said:**
> u could use emifreq-applet.
Goto system -> administration -> synaptic package manager
there click on find and type cpu
scroll down and u will find emifreq-applet..
install it..
restart.
once u are in ubuntu, right click on one of ur panels and click on add to panel. There should be a new cpu related applet. There you can manually set the clock speed or choose automatic. You can also view ur cpu temp with this applet.

p.s. the speed needs to be set everytime u start ubuntu. It would be at automatic otherwise.

An applet is nice, but I think he wants it to run in the background and not care.

---

### Post by damphoud on 2008-06-22
Depends on the laptop bios. but there is usually a setting where you can sellect the FBS (front side bus). eg. from 133mgz to 100mgz.

---

### Post by pmaconi on 2008-06-22
My bios doesn't have any settings like that to configure. Also, messing with a bios setting isn't what I am looking for. I dual boot with Vista - which doesn't have an overheating problem. I use Vista to play games - crippling my processor for Vista isn't an ideal solution.

---

### Post by pmaconi on 2008-06-22
I found two somewhat acceptable solutions: I used sudo dpkg-reconfigure gnome-applets to give the frequency applet root permissions (letting me change it on demand, like emifreq-applet, but without the graphical glitches). I also used gconf-editor to show the frequency settings in the applet. Choosing maximum power saver forces my processor to stay at 800 MHz. Ideally I want to limit it to 1600 MHz, but the 800 MHz solution is fine for what I use the computer for.

---

