---
title: "screen brightness on HP dv7"
date: 2012-01-10
forum: Hardware
---

### Post by biodiesel-bri on 2012-01-10
I have a dv7-6b78us and the screen brightness keys weren't working.  I'll be posting my success getting those going here.  I have a temporary workaround.

None of the threads I read were quite accurate with respect to the hybrid graphic card setup on this laptop, so here's the workaround that worked for me.

Set the brightness at about 50%
```
echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

Set the brightness to max
```
cat /sys/class/backlight/intel_backlight/max_brightness | sudo tee /sys/class/backlight/intel_backlight/brightness
```

Even though I installed the Radeon drivers, the Intel graphics card is on by default as well, hence we have to use that.

Once I figure out how to bind the actual fn-F2 and fn-F3 keys to increase and decrease brightness I'll post that here.  I'll be working on getting the graphics cards to behave as well.

---

### Post by biodiesel-bri on 2012-01-29
I found a much better solution.

Run this in a terminal:
```
sudo nano /etc/default/grub
```
and change this line:
```
GRUB_CMDLINE_LINUX=""
```
to:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

Save the file and run:
```
sudo update-grub
```

Now reboot.  Your function keys for brightness should now work.

---

### Post by Mr Mutis on 2012-01-30
Thanks!! I fixed my dv7-6153ea! Next, need to fix the hybrid graphics crap... Cause battery only lasts an hour after fully charged.

---

### Post by biodiesel-bri on 2012-01-30
Ah, I did that too.  Here's how:
[http://ubuntuforums.org/showthread.php?p=11652878](http://ubuntuforums.org/showthread.php?p=11652878)

---

### Post by lawrencesilva on 2012-02-14
hi guys ive the same problem with the brightness control not working on my hp dv7-6135dx.

i tried the grub update didnt work

i used to have that folder: /sys/class/backlight/intel_backlight/ folder and now its missing

any ideas on how i can get it back and have my brightness control again? its pretty hard to the eyes looking

at my laptop at its highest backlight level. 

thanks

---

### Post by mastablasta on 2012-02-14
you might want to have a look at this thread and get those new testing  AMD drivers on to get hybrid GPU support: [http://ubuntuforums.org/showthread.php?t=1924347](http://ubuntuforums.org/showthread.php?t=1924347)

---

### Post by biodiesel-bri on 2012-02-14
You also have to remove the proprietary drivers from your system, at least I did.

add to /etc/modprobe.d/blacklist-local.conf:
```
blacklist fglrx

```

I also added this to my /etc/local.rc (above the exit 0 line):
```
modprobe radeon
```

---

### Post by THPubs on 2012-07-11
Thanks bro this solved my problem! But 1 little bit... When restarted, the brightness resets. We have to adjust it again every time we restart the machine! Know how to fix that?

---

### Post by prosiedem on 2012-11-26
> **biodiesel-bri said:**
> I found a much better solution.

Run this in a terminal:
```
sudo nano /etc/default/grub
```and change this line:
```
GRUB_CMDLINE_LINUX=""
```to:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```Save the file and run:
```
sudo update-grub
```Now reboot.  Your function keys for brightness should now work.

I can confirm it works like a charm with HP Pavilion DV7

---

### Post by Dans564 on 2012-11-26
Check out my guide on getting everything on a dv6 working [here]("http://ubuntuforums.org/showthread.php?p=12371440#post12371440"). Should help you get your dv7 up and running 100%

Happy ubuntuing!
Dan

---

### Post by Tarun_Chand on 2013-10-17
I have a HP Probook 4440s and the instructions to tie the Fn+F2/F3 dont work. Pls advise

PS- am a new user so detailed instruction would be appreciated

---

### Post by cmacia06 on 2014-02-28
Hello. This is a common problem whenever I install ubuntu on hp laptops so i made a small program which precisely does what this forum says. This way people who dont understand can just run it. This is such a simple operation that maybe it is not nessisary to create a program but... im trying to practice what I learn at the university... Thought it would be a good idea to contribute. ANYWAYS. Here is the download link to the archive. [https://dl.dropboxusercontent.com/u/93765018/hp_dv7_brightnessfix.tar.gz](https://dl.dropboxusercontent.com/u/93765018/hp_dv7_brightnessfix.tar.gz)   ... I'm going to make one program to fix all of these issues in one shot. Feel free to reivew and edit the code (Included in the archive written in C) in any way you wish.

EDIT: Forgot the instructions... ha ha
First: Download and Extract
Second: Navigate to the directory in a console (terminal) window. Short cut is press "ctrl + alt + t" . If you extracted it to your Desktop you would type.. " cd ~/Desktop/hp_bri_fix/ "
Third: Give run permission. Type " chmod 775 ./brightness_fix "
Fourth:  Run as elevated user. " sudo ./brightness_fix"
Follow the instruction and that's it!

---

