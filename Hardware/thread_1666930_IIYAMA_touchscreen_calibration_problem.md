---
title: "IIYAMA touchscreen calibration problem"
date: 2011-01-14
forum: Hardware
---

### Post by victor-be on 2011-01-14
Hi

I have a touchscreen IIYAMA ProLite T2250mts. I'm using Ubuntu Maverick 10.10 amd64 and it can be used right away, but i have a configuration/calibration problem : the mice of the touchscreen places itself at the left of the finger on the screen; furthermore this changes according to to position on the screen; at the very right of the screen the mice places itself under the finger; at the very left of the screen, the mice places itself more than 10 cm away from the finger...

I've generated a xorg.conf, because i've seen it a lot in the forums; i've searched a lot, and tryed many things but i'm still unable to find something that works for me; even that post doesn't help :

[http://ubuntuforums.org/showthread.php?t=1469326&highlight=touchscreen+iiyama]("http://ubuntuforums.org/showthread.php?t=1469326&highlight=touchscreen+iiyama")

(i cannot patch)

There is something, however, that works : when i set the screen in "mirrors" (the same image in both screen), the mice places itself under the finger, but a low resolution of 1024 x 768 (i have normally 1366 x 768 on my asus laptop, and 1920x 1080 on the touchscreen)...

Idea? Tip?

Thank you!

Victor

---

### Post by IcarusR on 2011-01-14
> (i cannot patch)

What do you mean by this ? Did the instructions on your linked thread fail on the patch stage ?
If so what error did you get ?

---

### Post by victor-be on 2011-01-14
> **IcarusR said:**
> What do you mean by this ? Did the instructions on your linked thread fail on the patch stage ?
If so what error did you get ?


Well actually nothing happened. AFter the 

**patch -p 1 < <path to your hidtouch.patch>**
 
instruction, nothing happened, even for 10 minutes... 

On the other hand, i've noticed that there is 

*Option          "Device"                "/dev/usb/quanta_touch"*

in the proposed Xorg.conf; and i don't have a /dev/usb directory...

Finally, this link propose a soution because this monitor was not working out of the bow at that time; but it does now....... should i search fot the solution somewhere else?

I precise that i've installed the evtouch driver (from Synaptics)

Thank you for your reply

victor

---

### Post by IcarusR on 2011-01-14
> patch -p 1 < <path to your hidtouch.patch>

You did change '<path to your hidtouch.patch>' to the path to the patch file ?
So if you downloaded it to your home directory the the command would be 

```
patch -p 1 < /home/victor-be/hidtouch.patch
```

I assume you followed all the other instructions to the letter ?

---

### Post by IcarusR on 2011-01-14
Double post sorry.

---

### Post by victor-be on 2011-01-14
That's it!
I had forgotten the "<" character between **patch -p 1** and the path of the patch file (which was correct)

so i've been able able to patch, and to install... without succes; however , in the xorg.conf i've been trying to replace 

**Option          "Device"                "/dev/usb/quanta_touch"**

with **"/dev/input/event1"** (i don't have /dev/usb directory)

I didn't change the /etc/udev/rules.d/99-touch.rules but maybe i should (but i don't know how)

I must say that i have try this also 

[http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html]("http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html")

[]("http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html")
i've applied the patch to a 2.6.36.3 downloaded on kernel.org and compiled a new kernel; everything step went fine, but it doesn't change anything...

also i've applied their other tutorial [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html]("http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html")
also without succes

my monitor is among the list of supported hardware... (vendor : product = 0408:3000)
...

thank you for your help

v

---

### Post by victor-be on 2011-01-14
sorry this is the missing link in my previous post

[http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html]("http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html")

the linux multitouch how to :-)

---

### Post by IcarusR on 2011-01-14
> with "/dev/input/event1" 

Trouble with this is that if you plug a usb item in one day & then boot your laptop the event numbers are likely to change, or if you plug moniter into a different usb port the same will happen.

> (i don't have /dev/usb directory)


You can create it, without it usb items will not work. You do not use usb stuff ?

```
sudo mkdir/dev/usb
```

Then the code in the original thread you linked should work. 

> The touch screen is an infrared multipoint touch screen from Quanta. No kernel driver is needed, only an input driver for X is required. 

From the Debian wiki install instructions where your original linked thread instructions came from.

You are best off trying to get this to work as originally tried.

---

### Post by IcarusR on 2011-01-14
> with "/dev/input/event1" 

Trouble with this is that if you plug a usb item in one day & then boot your laptop the event numbers are likely to change, or if you plug moniter into a different usb port the same will happen.

> (i don't have /dev/usb directory)


You can create it, without it usb items will not work. You do not use usb stuff ?

```
sudo mkdir/dev/usb
```

Then the code in the original thread you linked should work. 

> The touch screen is an infrared multipoint touch screen from Quanta. No kernel driver is needed, only an input driver for X is required. 

From the Debian wiki install instructions where your original linked thread instructions came from.

You are best off trying to get this to work as originally tried.

---

### Post by IcarusR on 2011-01-14
Another double post. Having problems connecting to ubuntuforums.org

---

### Post by victor-be on 2011-01-15
hello

strange; i've posted a reply yesterday, and i cannot see it here... 

anyway, it is SOLVED; i may look stupid, but i must confess that all this was unecessary; as i've read somewhere, the Iiyama ProLite T2250mts works natively in Ubuntu.

My mistakes were : 

- first i had to go to Preferences > Monitors and choose to turn off my laptop screen, thus redirecting everything to the touchscreen; 

- i also had to remove the evtouch driver; it works perfectly without it

- finally, no xorg.conf is necessary; i could delete; and it is the same for the udev rules...

Nothing to do...

Thank you very much for your help!!!

PS for the record , regarding the debian how-to, I couldn't patch; i had a lot of messages during compilation; among others messages regarding something deprecated...

thanks again

Vic

---

### Post by HornedBeast on 2011-02-01
Hello,

I am curious as to how you solved this issue?

Did you have to install anything new, or compile kernels to get it to work?

I have a fresh Ubuntu 10.10 64bit and was wondering how you got past the issue of the cursor being in the top left corner all the time?

Thanks in advance.

Andy

---

### Post by victor-be on 2011-02-04
Hello

i didn't do anything to have it working, it works natively; but with my previous manipulation (creating Xorg and so on) i prevented to work... 

regarding the position of the mous : indeed it doesn't work in twin view : the best is to use the monitor screen only (so deactivating the laptop screen) and the mouse is perfectly placed;

finally, and i didn't mention this because i fixed it later : this touchscreen is DUAL TOUCH but only single touch works natively; so i've been searching in ENAC website [http://lii-enac.fr/en/architecture/linux-input/]("http://lii-enac.fr/en/architecture/linux-input/"); they provide many drivers for multitouch including this one (so this allows dual touch to work); they have a linux procedure and a ubuntu-specific procedure detailed to have it... in my case, they was probably a bug in the driver; i contacted them and i got an immediate fix... and dual touch works now...

Vic

---

