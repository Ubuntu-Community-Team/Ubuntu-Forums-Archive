---
title: "How do I change the fan speed in ubuntu 9.10?"
date: 2009-11-21
forum: Hardware
---

### Post by kunnie on 2009-11-21
Hi guys, I have a problem: I just installed a hardware temperature monitor applet, using "sudo apt-get install sensors-applet lm-sensors", and I discovered my GPU is hot. I mean, 68° C hot. I need someone to be a hero and tell me how to change the fan speed so I can lower it down

FYI, my gpu, a Nvidia GeForce 8800 GT, comes with a design flaw, that makes the fan speed go at 29%. I need to make it go faster: in Windows XP, I used something called RivaTuner, and it worked great.

---

### Post by mr clark25 on 2009-11-22
you might be able to unhook the fan plug from the card and hook it up to 12V from that floppy power conector thats never used anymore. try that, and if its to loud, then hook one wire (+) into the 12V and another into the 3.3V to give it 9V. that should keep the noise down if it is to loud.

hope the card will work when it thinks it doesnt have a fan... it should because some people water cool their cards...

---

### Post by w0mbatharcos on 2010-01-01
Hi there! I have had the same problem earlier with my EVGA 8800 GTS, but I think I found a way to fix it:

In terminal:

```
sudo apt-get install nvclock 
```This downloads You a prgram, that let's You modify some things with Your nVidia VGA.

After it has ended, type

```
sudo nvclock -f -F auto
```This brings the fan to 'Auto' speed, depending on the actual temperature of the GPU. If it were not enough, You can change the "auto" part to a number 25-99, as "fan speed in %"

After it seems to be OK, You have to manage to run this every time the computer starts. So You have to put in the auto-starting sessions.

System->Options->Sessions     (Or something like that, I use a hungarian version)

[IMG]http://reformedmusings.files.wordpress.com/2009/01/nvidia-session-gtk.jpeg[/IMG]
  
I hope this helps! Bye!

---

### Post by SergeantOreo on 2010-01-17
> **w0mbatharcos said:**
> Hi there! I have had the same problem earlier with my EVGA 8800 GTS, but I think I found a way to fix it:

In terminal:

```
sudo apt-get install nvclock 
```This downloads You a prgram, that let's You modify some things with Your nVidia VGA.

After it has ended, type

```
sudo nvclock -f -F auto
```This brings the fan to 'Auto' speed, depending on the actual temperature of the GPU. If it were not enough, You can change the "auto" part to a number 25-99, as "fan speed in %"

After it seems to be OK, You have to manage to run this every time the computer starts. So You have to put in the auto-starting sessions.

System->Options->Sessions     (Or something like that, I use a hungarian version)

[IMG]http://reformedmusings.files.wordpress.com/2009/01/nvidia-session-gtk.jpeg[/IMG]
  
I hope this helps! Bye!


Thanks a lot for this; I was just doing some research as my 8800gt had an idle temperature of 70C, and now is down to 60C. ;)

---

