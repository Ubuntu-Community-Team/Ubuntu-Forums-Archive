---
title: "Sony Vaio E-Series (SVE15113EN) Brightness Issue"
date: 2013-07-16
forum: Hardware
---

### Post by deepupn on 2013-07-16
Hi everyone,

This is my first post. I went through the entire thread Toz and Karl was discussing. I have the same issue and same laptop, where the only difference is my laptop is Sony vaio SVE15113EN. I tried some your tips but no end result. I am a novice in Linux, literally. 

One of the most interesting part is that when I checked inside etc/acpi and etc/acpi/events, instead of having sony brightness files, I have Asus brightness files. I am confused with this.

Can you help me guys. The bright screen is hurting my eyes. 

Than you in advance for your replies.

---

### Post by Toz on 2013-07-16
*Moving post to its own thread. Originally posted in [http://ubuntuforums.org/showthread.php?t=2033273]("http://ubuntuforums.org/showthread.php?t=2033273").*

Hello and welcome to the forums. Can we please confirm some information:

1. What version and flavour of ubuntu are you using?

2. Your current kernel command line:
```
cat /proc/cmdline
```

3. Your video card and driver:
```
sudo lspci -vnn | grep -A12 VGA
```

4. You backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

### Post by deepupn on 2013-07-16
Hi Toz,

Thank you for the reply.

1. Ubuntu 12.04LTS

2. My current kernel command line:
```
BOOT_IMAGE=/boot/vmlinuz-3.5.0-36-generic root=UUID=c9f390f4-3d8d-473f-adae-955af075f7a6 ro quiet splash acpi_backlight=video vt.handoff=7
```

3. My Video card and Driver:

```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:90ac]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 94000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915
```

4. My You backlight interfaces:

```
/sys/class/backlight/acpi_video0
5
15
/sys/class/backlight/intel_backlight
2500
4882

```

The 2500 appears there because I applied this command "echo XXXX | sudo tee - /sys/class/backlight/intel_backlight/brightness", where xxxx is 2500.

These are the files inside /etc/acpi

```
/etc/acpi$ ls
asus-brn-down.sh            brightdown.sh~   lid.sh       powerbtn.sh      sleep.sh                       webbtn.sh
asus-brn-up.sh              brightup.sh~     lockbtn.sh   power.sh         stopbtn.sh
asus-keyboard-backlight.sh  ejectbtn.sh      mailbtn.sh   prevbtn.sh       thinkpad-stretchortouchpad.sh
asus-touchpad.sh            events           mediabtn.sh  rotatescreen.sh  tosh-wireless.sh
asus-wireless.sh            hibernate.sh     nextbtn.sh   screenblank.sh   undock.sh
batterybtn.sh               ibm-wireless.sh  playbtn.sh   sleepbtn.sh      videobtn.sh

```


Why do I have Asus and Toshiba files? 

Eagerly waiting for your reply. Thank you

---

### Post by Toz on 2013-07-16
Can you try with the kernel parameter **acpi_backlight=vendor** instead (to see if we can get just one backlight interface)? After reboot, post back:
```
cat /proc/cmdline
```
...and
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

Also try brightness function keys and echoing directly into backlight interface again so see if it works?

> Why do I have Asus and Toshiba files? 
Those are just the default files for other laptop manufacturers.

---

### Post by deepupn on 2013-07-16
Hi Toz,

Thank you for the reply. 

1. cat /proc/cmdline:

```
BOOT_IMAGE=/boot/vmlinuz-3.5.0-36-generic root=UUID=c9f390f4-3d8d-473f-adae-955af075f7a6 ro quiet splash acpi_backlight=vendor vt.handoff=7
```

2. for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done:
```

/sys/class/backlight/intel_backlight
2500
4882
/sys/class/backlight/sony
6
7

```

I forgot to tell you that before contacting you, I had applied this command also.```
 "sudo modprobe -r sony_laptop".
```

Now when i try to adjust the brightness using the Fn keys what happens is, slider doesn't move all the way back. It just slides back just a little back. I thought you wanted to know this.

Toz, I am a very very novice in terms of linux. 

I didn't understand what you meant by this **"and echoing directly into backlight interface again so see if it works?"**

Thanking you in advance for the reply and patience.

---

### Post by Toz on 2013-07-16
> I didn't understand what you meant by this "and echoing directly into backlight interface again so see if it works?"
You did this earlier with the command:
```
echo XXXX | sudo tee /sys/class/backlight/<INTERFACE>/brightness
```
...but hold on to this for a second. We'll test these shortly.

-----

Try removing the acpi_backlight parameter so there is nothing there. Run "sudo update-grub" and reboot. Once rebooted, _don't_ "sudo modprobe -r sony_laptop" and post back again:
```
cat /proc/cmdline
```
...and
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

Lets see what interfaces you have.

---

### Post by deepupn on 2013-07-16
Hi Toz,

Here are the new results:-

1. cat /proc/cmdline:

```
BOOT_IMAGE=/boot/vmlinuz-3.5.0-36-generic root=UUID=c9f390f4-3d8d-473f-adae-955af075f7a6 ro quiet splash vt.handoff=7
```

2. for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done

```
/sys/class/backlight/acpi_video0
6
15
/sys/class/backlight/intel_backlight
4882
4882
```

Thank you for the reply.

---

### Post by Toz on 2013-07-16
Which of the following sets of commands change the brightness?
```
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 6 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

```
echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

---

### Post by deepupn on 2013-07-17
Hi Toz,

Sorry for the late reply. I was very sleepy last night. It was almost 3 AM.

Now the results are that no chages occur when these two commands are given:

```
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness 
echo 6 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

But when I apply the command having intel reference, the brightness does change.

Thank you for the reply and patience.

---

### Post by Toz on 2013-07-17
Okay, lets try one more thing before we look at creating a workaround script for you.

First, can you:
```
echo 0 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...then can you try the brightness function keys and slider again to see if they work.

---

### Post by deepupn on 2013-07-18
Hi Toz,

I tried the command and the whole screen went blank. I then used the Fn keys, but no positive results. The slider still doesn't work.

Thank you for the reply and patience. Eagerly awaiting for the reply.

---

### Post by Toz on 2013-07-18
Thank you for trying. You have 2 backlight interfaces (intel_backlight and acpi_video0). When we tell the OS to use the vendor mechanism, you end up with 2 interfaces again (intel_backlight and sony). This is problemmatic since the OS can't reliably determine which is the active one. If you are looking for a proper solution, you need to create a bug report and follow tthrough that process.

As a workaround, we might be able to create a script to give you control of the brightness using the function keys (there is no guarantee the slider will work, but we can see).

To see if the script will work, your brightness function keys needs to emit a keycode. Can you run the following command in a terminal window:
```
acpi_listen
```
...then press the function the brightness up key combination once then the brightness down key combination once. Post back the codes that show up in the terminal window.

---

### Post by deepupn on 2013-07-18
Hi Toz,

These are the results:-
```

acpi_listen 
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b
```

I hope I did it correctly. Thank you for the reply.

---

### Post by Toz on 2013-07-18
Good. Follow the [instructions here]("http://ubuntuforums.org/showthread.php?t=2088190&p=12373220&viewfull=1#post12373220") to create the necessary scripts and hooks. All of the values should work for you as shown in that post.

---

### Post by deepupn on 2013-07-19
Hi Toz,

Very sorry for the late reply. I think what I need to do is to create myself the Sony brightness up and down files and also the other bright up and down files. Is is correct?. Let me try this out and will let you know as soon as possible. Thank you very much for the help, support and patience. I appreciate it very much. Thank you.

---

### Post by Toz on 2013-07-19
> **deepupn said:**
> Hi Toz,

Very sorry for the late reply. I think what I need to do is to create myself the Sony brightness up and down files and also the other bright up and down files. Is is correct?. Let me try this out and will let you know as soon as possible. Thank you very much for the help, support and patience. I appreciate it very much. Thank you.

Yes. Follow those same instructions.

---

### Post by deepupn on 2013-08-03
Hi Toz,

It's been a long time. I didn't even log in to Ubuntu when I heard that the website was hacked, so I couldn't try any scripts. This morning I tried and created all the scripts that you showed and WOW it works like a charm. A million thanks to you. I am really sorry for the late reply. You can mark this thread as solved. I will be bugging you in future for other Ubuntu related issues. Thank you.
 		 			 				:KS 		 			 				:KS 		 			 				:KS 		 			 				:KS 		 			 				:KS 		 			 				
=D>" title="Applause">

5 stars and applause to you

---

### Post by Toz on 2013-08-04
Glad to hear it worked for you. Marking this thread solved.
In the future, you can mark threads solved by selecting "Mark this thread as solved" from the "Thread Tools" link above.

---

