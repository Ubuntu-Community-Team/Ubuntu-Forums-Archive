---
title: "T410s - will it work fine?"
date: 2010-06-12
forum: Hardware
---

### Post by warnec on 2010-06-12
Hi. I'm planning to buy a Lenovo ThinkPad T410s and install Ubuntu on it.

I've already read ThinkWiki many times, and I think I could quite easily get webcam, bluetooth and fingerprint reader to work. Ultrabay battery shouldn't be a problem as well.

What I don't know, though, are two things:

1)   I don't know yet if I should buy a laptop with only Intel GMA 4500MHD or with switchable graphics and NVIDIA Quadro NVS 3100M. 

     I prefer the Intel-only solution, because it saves more battery and should be cooler (and cheaper, of course) but I am not sure about Compiz. I love desktop effects, and would like the laptop to run them effortlessly. My nvidia hardware in my current desktop system does this job outstandigly, and I am a little concerned if the laptop will stand up to the task. Besides Compiz, I don't expect any breathtaking 3D performance - it's Intel, after all. I just want Compiz to work nicely.

2)    I want to make sure the touchpad will work fine - that includes two-finger scrolling and circle scrolling. I found a nice ArchWiki article here:

[http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Edge_scrolling](http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Edge_scrolling)

and am just wondering if it will work fine (all this HAL and X.org magic)

Besides, it looks like I'd have to disable gnome's mouse config utility:

[http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Touchpad_not_working_properly_in_Gnome_.28No_tap_zones.2C_scrolling_etc..29](http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Touchpad_not_working_properly_in_Gnome_.28No_tap_zones.2C_scrolling_etc..29)

Do you think it would work fine on Ubuntu as well?



and the last question. It's not decisive, but I'd like to know that as well.
[B]
Is it possible to log in and authenticate (sudo in console and gksudo in GUI) using only the fingerprint reader?[/B]

PS.: As you can see, there's lot of text magic required to make some gestures work on Linux, and these are not still all of the ones available for Synaptics touchpad.
I hope there might be an easier solution. See here:

[http://www.engadget.com/2010/04/20/synaptics-extends-multitouch-gesture-suite-to-linux-chrome-os-i/](http://www.engadget.com/2010/04/20/synaptics-extends-multitouch-gesture-suite-to-linux-chrome-os-i/)

This "SGS-L" suite is said to have been released in April to OEMs, which could result in better support for Synaptics touchpads in future editions of these systems. **But why is it not possible to download this suite for an end user? Has it been released at all?**

---

### Post by warnec on 2010-06-12
bump. Nobody can help me?

---

### Post by dino99 on 2010-06-12
[http://www.google.com/search?q=T410s%2Bubuntu&btnG=Rechercher&hl=fr&sa=2](http://www.google.com/search?q=T410s%2Bubuntu&btnG=Rechercher&hl=fr&sa=2)

---

### Post by warnec on 2010-06-12
Great, but you still didn't answer my questions - all reports I can find are basically of users who installed Ubuntu and din't care to explore the matter deeply, which can be seen from reports claiming the fingerprint reader doesn't work - and it **should**, in fact. One should just need newest libfprint libraries (at least that's what ThinkWiki claims)

That's why they are barely helpful. I haven't seen any reports about Compiz performance, where it'd be clear one uses only Intel GMA hardware. I"m seeing some error reports of hanging, but by the time I install Ubuntu on T410s (read:Meerkat) an updated kernel should fix it. The same goes to sound issues.

I still don't know how it is with the fingerprint reader authentication - is it possible to use it with sudo and gksudo in terminal&GUI? 

And this Synaptics magic - it's a totally unadressed issue throughout the Internet.

---

### Post by warnec on 2010-06-13
bump

---

### Post by aztektum on 2010-07-01
I just got one at work. I don't have the finger swiper on mine, have Intel graphics which work fine, Intel wifi which works out of the box. Have not tried to get the fancy touchpad stuff to work. I prefer ****-mouse/hands on keyboard.

Hope to get around to figuring out the webcam and touchpad soon, but getting married this weekend so soon is ambiguous :)

Bought the cd-slot battery too. Nice extra couple hours with the standard battery.

EDIT: BT works out of the box.

---

### Post by venturax on 2010-07-13
I have a Lenovo t410s with a SSD drive and Karmic wont boot at all. Just a blank screen after the message: "GRUB loading."

10.04 installs ok and works, but currently is not supported in our cooperate IT.

Just FYI

---

### Post by cpbl on 2010-11-07
Lenovo t410s:

Ubuntu 10.10 installed, works flawlessly (See [cpbl.wordpress.com]("http://cpbl.wordpress.com"))
for basics, with exceptions of multitouch touchpad and the fingerprint scanner.

Tried instructions for installing thinkfinger, but I get 
"Initializing...USB device not found" when I try 

```
sudo tf-tool --acquire
```

So I'm stuck.

---

