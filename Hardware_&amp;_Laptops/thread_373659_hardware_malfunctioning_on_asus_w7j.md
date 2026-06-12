---
title: "hardware malfunctioning on asus w7j"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by amaan on 2007-03-01
hello, i just recently installed ubuntu and it works fine, i'm even running virtualbox using windows xp also

alas, there are a few minor details that need to be fixed...firstly i'm running all of this on an asus w7j notebook pc. the problems i've been having involve my mouse, my usb, my built in webcam, and virtual box

1. so the problem with my mouse is that i can't disable it using the function key on my keyboard and i can't find any other way to do it

2. my webcam doesn't work at all

3. virtualbox doesn't allow me to transfer files between ubuntu and xp, and virtualbox doesn't allow me to access usb devices (i already changed the option saying to allow them) this is the error i get:

Not permitted to open the USB device, check usbfs options.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 4. when i change the sound volume to whatever, the settings revert and go back up to full when u reboot the pc

5. i can't hibernate the pc, when i do it freezes and i have to do a complete reboot of the system


and yea that's basically it, it would be wonderful if i can even solve at least 1 of these problems

thanks,
kind regards,
amaan

---

### Post by Lfrb on 2007-03-08
Hi,

I have the same laptop, so I can help you about a few points

Firstly, #2 : There is no driver for this webcam yet...so we have to wait :-( But it seems to have someone working on it (search "linux sn9c20x" on Google)

#1 : You're talking about the touchpad ?? Because it works for me. I can disable it with Fn+F?. Maybe it's because I install GSynaptic (you can enable scrolling with GSynaptic as well). Not sure

#3 I don't know what is VirtualBox..sorry

#4 It works for me...maybe try to install the latest Alsa-driver. Which Ubuntu version are you using ?

#5 Are you using the proprietary NVidia driver ?? Can you paste the log when it fails. Usually it's a probleme about the nvidia card.

Sorry, I can't help so much :-p

Bye

--
Louis-Francis

---

### Post by amaan on 2007-03-08
thank you, i got it all working except #5...when i try hibernating it fails and even when i suspend it my wireless fails (i have to disable/enable it)

also for the wireless, what wireless utility are you using? because for me it won't find the wireless networks around the area, i have to manually type in the SSID and then it connects

thanks for your help,
kind regards,
amaan

---

### Post by amaan on 2007-03-08
one more thing...my bluetooth doesn't work well. do you have any suggestions for a good bluetooth utility?

---

### Post by Lfrb on 2007-03-10
I'm using Network-Manager and it scan the wifi networks really well.

But I got the same probleme than you about Suspend (Wifi is down after the computer woke up). But I don't use really often so I didn't try to correct it. What is the problem you get when you try to hivernate ? Because I can hibernate in Edgy but it doesn't work anymore in Feisty (a weird message : "code=32 quark='g-exec-error-quark'"

--
Louis-Francis

---

### Post by amaan on 2007-03-10
when i hibernate it hangs and nothing happens i have to then manually reboot my computer :(

---

### Post by amaan on 2007-03-10
what are you using for bluetooth?

---

### Post by Eric DANE on 2007-03-14
Hello

I also have a Asus W7J
I update the wiki documentation [https://wiki.ubuntu.com/LaptopTestingTeam/AsusW7J]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusW7J")

You are welcome to use it to memorize you solutions.

best wishes

---

### Post by Eric DANE on 2007-03-14
Hi Louis-Francis, 

> **Lfrb said:**
> 
Firstly, #2 : There is no driver for this webcam yet...so we have to wait :-( But it seems to have someone working on it (search "linux sn9c20x" on Google)
Louis-Francis

How come did you find out sn9c20x is the chipset of the webcam ?

--
Eric DAné

---

### Post by savesys on 2007-04-19
OK amaan, i'm curious how you got both working.. 

1) transfering files from the one virtual box to another without using a stick
2) having it recognize a usb wireless device

:)
Thanks

---

### Post by HumanAnarchist on 2007-04-21
I'm considering bying this laptop. Do you guys know if the webcam works in Feisty Fawn? 

-ha-

---

### Post by towersoft on 2007-04-23
> **amaan said:**
> thank you, i got it all working except #5...when i try hibernating it fails and even when i suspend it my wireless fails (i have to disable/enable it)

also for the wireless, what wireless utility are you using? because for me it won't find the wireless networks around the area, i have to manually type in the SSID and then it connects

thanks for your help,
kind regards,
amaan

Hi,
    Could you please tell me how you got the USB to work as I have been struggling with this for a week or so now. Thanks.

Best Regards
Philip Thomson

---

### Post by Lfrb on 2007-04-23
The built-in webcam on the W7J use the sn9c201 chipset according to this post :

[http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg00542.html](http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg00542.html)

Th webcam isn't working for now because it's a relatively recent chipset and Sonix doesn't any clue how to build a driver on their website. Michel Xhaard is currently developing a driver, so hopefully we can see some progress in the next month

--
Louis-Francis

---

### Post by Lfrb on 2007-04-23
What is your problem about USB towersoft ??

--
Louis-Francis

---

### Post by towersoft on 2007-04-24
Just the USB in Virtual Box. Cant get access to some devices, just tells me:


Not permitted to open the USB device, check usbfs options.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Any help most apprecited.

Best Regards
Philip Thomson

---

