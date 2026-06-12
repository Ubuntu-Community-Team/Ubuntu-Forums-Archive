---
title: "can't configure mic on new Asus"
date: 2014-02-05
forum: Hardware
---

### Post by eli_fabrikant on 2014-02-05
Hi Guys,

I installed Ubuntu 13.10 on a new Asus R510L and had loads of problems installing the sound card ( Intel HDA PCH, the chip is Realtek ALC233) properly.
 After updating ALSAmixer (by installing the packages from the alsa project daily feed), FINALLY the internal speakers starting working. BUT, the internal mic AND any external mic I try to conne ct bring no input. I went a thousand times through the Alsamixer in the terminal and PulseAusio to make sure that the mic is not muted. It's not. I really don't know what else to do.

p.s, trying to install the latest daily feed didn't work out for some reason, there is no INSTALL folder in the TAR.GZ package and I have no idea how to install it otherwise. but that's a size issue.

I really wasted hours on hours reading the forums to try and solve it for myself but I just hit this dead-end and I have no idea how to continue...
would really appreciate your help !!!
thanks in advance
Eli

---

### Post by LinuXXuniL on 2014-02-06
Hi, try to open "Sound Settings" go to "Input" menu and select your mic from the list, turn it on. It works here!

---

### Post by eli_fabrikant on 2014-02-06
> **LinuXXuniL said:**
> Hi, try to open "Sound Settings" go to "Input" menu and select your mic from the list, turn it on. It works here!


Well, the only mic that is showing in the list is 'internal microphone - built-in Audio'. It's on, but it shows no signs of life. By the way, when i plug my headset in the headphone jack, it recognises it only as an output, and nos as an input. Should i buy a special mic that has a usb rather than jack connection ??

---

### Post by LinuXXuniL on 2014-02-06
I used an USB set (mic + headphones) and it worked, but I'm using a cheap mic now and it is working. Try to enter skype and see if you internal mic is working. Maybe it will work from the application! In alsamixer check the Mic and unmute it with "M" key.

---

### Post by eli_fabrikant on 2014-02-06
> **LinuXXuniL said:**
> I used an USB set (mic + headphones) and it worked, but I'm using a cheap mic now and it is working. Try to enter skype and see if you internal mic is working. Maybe it will work from the application! In alsamixer check the Mic and unmute it with "M" key.

First, thanks linuxxunil for trying to help !
Hmm.. when you write 'a cheap mic' you mean a mic with a jack connection ? 

Anyway, I already checked alsamixer many times, the mic is not muted. and the internal mic does not work with skype. Even in 'Sound Settings' I see that the bar that shows the input of the mic is on zero, although the mic is unmuted...

Any other ideas ??

---

### Post by LinuXXuniL on 2014-02-08
Yes, I am using a mic with jack connection. Anyway, this is very strange and might be a problem of the driver integration, don't know what to think. I will try to find more about your problem and I'll let you know if I find anything.

---

### Post by eli_fabrikant on 2014-02-09
> **LinuXXuniL said:**
> Yes, I am using a mic with jack connection. Anyway, this is very strange and might be a problem of the driver integration, don't know what to think. I will try to find more about your problem and I'll let you know if I find anything.

Thanks ! I'm crossing my fingers (and at the same time considering just to buy a usb mic)

---

### Post by ivans76 on 2014-03-24
I am new to Ubuntu Forums, but I have the same problem on my new Asus. The only solution I found was to install pavucontrol and change the port to Microphone from internal Microphone on the Input Devices tab. I am not happy with it and I was hoping the alsamixer would automatically switch to external mic when I pull my headphones/mic out of the plug.

---

### Post by MarseHole on 2014-07-28
I had a similar problem with my Asus Vivobook (Intel HDA PCH, Realtek ALC233).
As suggested elsewhere, what eventually worked for me was separating the L/R channel levels for recording in the alsa mixer. My current setup is:
- Mic Boost1: L=100, R=0
- Mic Boost2: L=100, R=0
- Capture: L=100, R=100

I didn't need to install the nightly alsa builds; the release bundled with the Ubuntu 14.04 kernel (ALSA Version k3.13.0-32-generic) seemed to work fine.

---

### Post by cake-seller on 2014-12-22
> **MarseHole said:**
> I had a similar problem with my Asus Vivobook (Intel HDA PCH, Realtek ALC233).
As suggested elsewhere, what eventually worked for me was separating the L/R channel levels for recording in the alsa mixer. My current setup is:
- Mic Boost1: L=100, R=0
- Mic Boost2: L=100, R=0
- Capture: L=100, R=100

I didn't need to install the nightly alsa builds; the release bundled with the Ubuntu 14.04 kernel (ALSA Version k3.13.0-32-generic) seemed to work fine.

Thanks a lot! That helped me with Ubuntu 14.04 LTE on Asus Vivobook X202E.

---

