---
title: "Help....new USB stick not working!"
date: 2012-11-06
forum: Hardware
---

### Post by mohanp06 on 2012-11-06
well, I bought a new HP v220w stick of 16 GB, 
but my ubuntu 10.04 LTS is not detecting it.

when i plug the USB nothing happens.
on typing dmesg | tail, i get the following output:

------------------------------------------------------------------------------------------------
[SIZE=1][455318.120541] usb 2-5: device descriptor read/64, error -62
[455318.404534] usb 2-5: device descriptor read/64, error -62
[455318.684555] usb 2-5: new low speed USB device using ohci_hcd and address 22
[455318.868535] usb 2-5: device descriptor read/64, error -62
[455319.152532] usb 2-5: device descriptor read/64, error -62
[455319.432535] usb 2-5: new low speed USB device using ohci_hcd and address 23
[455319.840520] usb 2-5: device not accepting address 23, error -62
[455320.016553] usb 2-5: new low speed USB device using ohci_hcd and address 24
[455320.424528] usb 2-5: device not accepting address 24, error -62
[455320.424553] hub 2-0:1.0: unable to enumerate USB device on port 5[/SIZE]
------------------------------------------------------------------------------------------------


I tried searching solutions but could not understand those,
and found that most of them them require system reboot.
But I do not want to reboot my pc.

is there any way to make this work without rebooting my pc?

Thanks a lot....

Regards

---

### Post by Bashing-om on 2012-11-06
mohanp06; Hi !

What pops into my mind is no format on the usb drive ???
As you do not want to re-boot your box, can you check the format of the usb drive on another machine ?
[INDENT]just my thought ==> BDQ

[/INDENT]

---

### Post by mohanp06 on 2012-11-06
"<deleted>"

---

### Post by mohanp06 on 2012-11-06
hi _Bashing-Om_,

thanks for replying...

well, i had already tried that some days back.
it works perfectly fine on win7 on my friend's pc.

but on my ubuntu does not seem to even detect it.
no clue..

regards

---

### Post by edm1 on 2012-11-06
Is your 10.04 install fully updated? What version of the linux kernel are you using? This will tell you.

```
uname -r
```

---

### Post by mohanp06 on 2012-11-06
> **edm1 said:**
> Is your 10.04 install fully updated? What version of the linux kernel are you using? This will tell you.

```
uname -r
```

thanks for the reply, it's
2.6.32-44-generic

---

### Post by uclugLee on 2012-11-06
Does it happen if you connect it to a different USB port on your Ubuntu machine?

---

### Post by CaptainLinux on 2012-11-06
It sounds like it might be an issue with the kernel and USB 2.0 support.

Can you disconnect the USB drive and try it again after removing the high speed USB device module with the following command:

```
sudo modprobe -r ehci_hcd
```

---

### Post by mohanp06 on 2012-11-06
> **uclugLee said:**
> Does it happen if you connect it to a different USB port on your Ubuntu machine?


wow! i was trying both the front ports it was not working...
but as soon as i plugged it in one of those backside ports, its working!
also i am able to see files i have saved on it...

oh thanks so much..

never could have imagined this!

but again what could be the problems with front ports? i mean other usb sticks are working with these ports, and each time connecting on backside ports is troublesome...

either way thanks a lot for the suggestion...

regards..

---

### Post by mohanp06 on 2012-11-06
> **CaptainLinux said:**
> It sounds like it might be an issue with the kernel and USB 2.0 support.

Can you disconnect the USB drive and try it again after removing the high speed USB device module with the following command:

```
sudo modprobe -r ehci_hcd
```

when I run the command, i get:

FATAL: Module ehci_hcd is builtin

---

### Post by CaptainLinux on 2012-11-06
> **mohanp06 said:**
> when I run the command, i get:

FATAL: Module ehci_hcd is builtin

That means that the module for high speed USB device support is built into the kernel, therefore that command will not work as intended.

If other USB flash drives are working with your front ports, it might be a bug afflicting that particular drive.

---

### Post by mohanp06 on 2012-11-07
> **CaptainLinux said:**
> 
    it might be a bug afflicting that particular drive.

but the drive is working fine on back side ports!

in either case, the _combination of the drive and front ports is definitely not working_ which i want to get resolved.

regards

---

### Post by deadmantfa on 2012-11-11
My Usb ports are working but I have the same error and my syslog file is getting filled with it. Please help

error 
hub 2-1:1.0: unable to enumerate USB device on port 5

I have reached line 8410 in syslog as i was writing the reply

---

