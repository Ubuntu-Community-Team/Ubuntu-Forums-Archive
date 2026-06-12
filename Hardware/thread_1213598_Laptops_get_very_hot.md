---
title: "Laptops get very hot"
date: 2009-07-15
forum: Hardware
---

### Post by Sir_Sid on 2009-07-15
Hi, I own two dell laptops. One Ive had ubuntu running on for over a year and just recently installed windows 7. I had always assumed my laptop ran very warm, but I noticed in windows 7 it was noticeably cooler. Same with a new laptop I just received. In Vista, the computer was a lot cooler. I cant cite specific numbers, but its to the point where in ubuntu the keyboard is very warm and the bottom is burning hot for both laptops. When I run windows, the fan runs more often I believe and its noticeably cooler to the touch.

I was wondering if there was a way to have the fan run more aggressively in ubuntu.
My laptops are a 3 year old inspiron and a year old XPS which I just received.

---

### Post by Sir_Sid on 2009-07-15
Ive been doing some searching and I think the problem may be the CPU does not scale properly. I have speedstep enabled in bios but how do i check that its working properly in ubuntu.

---

### Post by theluddite on 2009-07-15
To see if there actually is a problem install conky.  It will show you your CPU load and temperature.

---

### Post by ubudog on 2009-07-15
Or use smartctl.

smartctl -a /dev/"whatever" | grep Temp

---

### Post by Sir_Sid on 2009-07-16
I ended up using computertemp. The CPU temps between linux and windows are very small. In Windows 7 im getting a temp of 42C and in linux a temp of 44-45C. This is not enough of a difference to create such a hot surface on the keyboard. The only other unit I think that can create such heat would be the videocard. 
How would I monitor to the temperature of my video card in linux?

---

### Post by ubudog on 2009-07-16
What kind of video card do you have?

---

### Post by Sir_Sid on 2009-07-16
Its an nvida card. 

Oh and the cpu temps are actually more like 7C apart. In Windows 7 they idle at 40C vs 47 in ubuntu

---

### Post by ubudog on 2009-07-16
Then go to System>Admin>NVIDIA X Server Settings.  One of the things on there should show you the temp.

---

### Post by AoSteve on 2009-07-16
In a terminal the following code should show you the temperature as long as you have a nVidia driver installed:

```

nvidia-settings -t -q=GPUCoreTemp

```

This is an easy way to check your temperature of the core quickly.   I personally don't like the GUI because it's "heat ratings" aren't feasable to me.  My 8800GTS G92 runs at about 50 - 70 celcius depending on how much I'm using it.  :)

---

