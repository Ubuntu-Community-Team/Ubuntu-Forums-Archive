---
title: "External Monitor not Recognized by Display Settings"
date: 2011-12-13
forum: Hardware
---

### Post by TheSixDollarSoda on 2011-12-13
Hey Y'all I have a slight problem..my Ubuntu 11.10 32-Bit won't recognize my External Monitor. I just reinstalled Ubuntu 11.10 today because my 11.10 that I used Wubi was glitchy for unknown reasons. 

So..I habe a nVIDIA GeForce 8660M GT 512MB in a Dell XPS M1530 (Product)RED Edition Laptop.

here are some possibly useful screenshots
[img]http://img256.imageshack.us/img256/3222/screenshotat20111213172.png[/img]
[img]http://img843.imageshack.us/img843/712/screenshotat20111213175.png[/img]
[img]http://img189.imageshack.us/img189/712/screenshotat20111213175.png[/img]
[img]http://img806.imageshack.us/img806/712/screenshotat20111213175.png[/img]

See it detects it but it is not shown on the Display Settings..what do I need to do?

---

### Post by papibe on 2011-12-13
Use the 'Nvidia X Server Settings' to recognize the monitor. Select 'X Server Display Configuration' on the right, then on the left you'll see the detected displays. Press 'Detect Displays' if not initially on the layout (remember to turn it on).

Hope it helps,
Regards.

---

### Post by TheSixDollarSoda on 2011-12-13
> **papibe said:**
> Use the 'Nvidia X Server Settings' to recognize the monitor. Select 'X Server Display Configuration' on the right, then on the left you'll see the detected displays. Press 'Detect Displays' if not initially on the layout (remember to turn it on).

Hope it helps,
Regards.

I get an error ;_;
[img]http://img802.imageshack.us/img802/2236/screenshotat20111213185.png[/img]

If this is what your talking about

---

### Post by papibe on 2011-12-13
Yes, but it seems that the proprietary driver is not being used.

Could you post your /etc/X11/xorg.conf ?

Regards.

---

### Post by TheSixDollarSoda on 2011-12-13
> **papibe said:**
> Yes, but it seems that the proprietary driver is not being used.

Could you post your /etc/X11/xorg.conf ?

Regards.

hmmm
Here you go ^_^
[img]http://img196.imageshack.us/img196/6201/screenshotat20111213191.png[/img]

---

### Post by papibe on 2011-12-13
The driver is not being used.

Run this to create a new conf file:
```
sudo nvidia-xconfig
```
Then check that you have a new xorg.conf with a line that says 'Driver "nvidia"' inside a section called "Device".

After that reboot your machine, so the driver take effect.

Tell us how it goes.
Regards.

---

### Post by TheSixDollarSoda on 2011-12-13
> **papibe said:**
> The driver is not being used.

Run this to create a new conf file:
```
sudo nvidia-xconfig
```
Then check that you have a new xorg.conf with a line that says 'Driver "nvidia"' inside a section called "Device".

After that reboot your machine, so the driver take effect.

Tell us how it goes.
Regards.

it does say nvidia
[img]http://img208.imageshack.us/img208/2164/screenshotat20111213193.png[/img]

But it says unknown on the display settings and the Xserver-Display-Configuration still has the error...

---

### Post by papibe on 2011-12-13
Did you reboot?

If so, could post this file:
```
/var/log/Xorg.0.log
```
Paste it [here]("http://paste.ubuntu.com/"), and then post the link.

Regards.

---

### Post by TheSixDollarSoda on 2011-12-13
> **papibe said:**
> Did you reboot?

If so, could post this file:
```
/var/log/Xorg.0.log
```
Paste it [here]("http://paste.ubuntu.com/"), and then post the link.

Regards.

Yes I did reboot :)
and [Here is the paste](http://paste.ubuntu.com/769659/)

---

### Post by papibe on 2011-12-13
It looks like you have a laptop. And you are trying to connect an external CRT monitor (DELL E176FP). Is that right?

I had a old laptop that needed to explicitly tell the Nvidia driver that an external monitor was connected.

Try adding this 2 lines in the screen section:
```

    Option         "ConnectedMonitor" "DFP-0, CRT-0"
    Option         "UseDisplayDevice" "DFP-0, CRT-0"

```
Then restart and try again.

Regards.

---

### Post by TheSixDollarSoda on 2011-12-13
> **papibe said:**
> It looks like you have a laptop. And you are trying to connect an external CRT monitor (DELL E176FP). Is that right?

I had a old laptop that needed to explicitly tell the Nvidia driver that an external monitor was connected.

Try adding this 2 lines in the screen section:
```

    Option         "ConnectedMonitor" "DFP-0, CRT-0"
    Option         "UseDisplayDevice" "DFP-0, CRT-0"

```
Then restart and try again.

Regards.

I don't know where the screen section is...
Cheers :)

---

### Post by papibe on 2011-12-13
Edit your /etc/X11/xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
There should be a section called screen. Add the previous line so it looks something like:
```
Section "Screen"
...
    Option         "ConnectedMonitor" "DFP-0, CRT-0"
    Option         "UseDisplayDevice" "DFP-0, CRT-0"
...
EndSection
```
Regards.

---

### Post by TheSixDollarSoda on 2011-12-13
> **papibe said:**
> Edit your /etc/X11/xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
There should be a section called screen. Add the previous line so it looks something like:
```
Section "Screen"
...
    Option         "ConnectedMonitor" "DFP-0, CRT-0"
    Option         "UseDisplayDevice" "DFP-0, CRT-0"
...
EndSection
```
Regards.
I got a massive error rebooting lol and now it doesn't detect my laptop screen o__o

here is the error
[img]http://img841.imageshack.us/img841/3394/screenshotat20111213203.png[/img]
here is the file
[img]http://img11.imageshack.us/img11/2306/screenshotat20111213204.png[/img]

---

### Post by papibe on 2011-12-13
Not good.

Could you post your /var/log/Xorg.0.log right after you boot with the error?

Regards.

---

### Post by TheSixDollarSoda on 2011-12-13
> **papibe said:**
> Not good.

Could you post your /var/log/Xorg.0.log right after you boot with the error?

Regards.
[Here you go](http://paste.ubuntu.com/769690/)
Cheers :)

---

### Post by papibe on 2011-12-14
Add this line, right below the ones you added before:
```
    Option         "TwinView" "TRUE"
```
Regards.

BTW, this remind me how difficult was to work with my old Geforce 440, around the time Hardy just came out :(

---

### Post by TheSixDollarSoda on 2011-12-14
Thanks for you help :)
UI fured it out o__o
[There is a Nvidia thingy on Ubuntu Site](https://help.ubuntu.com/community/NvidiaMultiMonitors)
Appearently I had the wrong driver, so I went with the recommended driver and it allowed me to use the Server Display Configuration Menu :)

I really appreciate you help :)


Cheers :D

---

