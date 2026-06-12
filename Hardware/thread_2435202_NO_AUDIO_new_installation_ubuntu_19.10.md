---
title: "NO AUDIO: new installation ubuntu 19.10"
date: 2020-01-17
forum: Hardware
---

### Post by querelledb on 2020-01-17
I've just installed Ubuntu 19.10 on my new PC and i notice an issue: there's no audio. 
I read a lot of guides and solutions on Google but no one fits for me. 
I have a "MSI x570 gaming plus carbon pro wifi" . 
Any help? :)


  Ask me for more details if needed

---

### Post by CelticWarrior on 2020-01-17
First thing to check is whether the audio device is enabled in UEFI. Many MSI motherboards have it disabled by default for reasons unknown to me.

---

### Post by querelledb on 2020-01-17
> **CelticWarrior said:**
> First thing to check is whether the audio device is enabled in UEFI. Many MSI motherboards have it disabled by default for reasons unknown to me.
How could i check it?? I googled it and I found a lot of solution related to windows.
I didn't mention it yet but audio works fine with windows
Sorry, I'm a complete newbie!

Thanks for your answer :)

---

### Post by CelticWarrior on 2020-01-17
No need to check if it's working on Windows. But if you're installing OSes you should familiarize yourself with your hardware, namely how to access your firmware (UEFI) settings and what to look for. Your user's manual is a good starting point.

---

### Post by CelticWarrior on 2020-01-17
Now, what audio device are we talking about?

The integrated audio card or HDMI or other?

---

### Post by querelledb on 2020-01-17
It's an integrated audio card on my MSI mobo that I need to use with my HDMI monitor.

---

### Post by CelticWarrior on 2020-01-17
> **querelledb said:**
> It's an integrated audio card on my MSI mobo that I need to use with my HDMI monitor.

This makes no sense, at all. HDMI audio is managed by the graphics card and its drivers and has nothing to do with the integrated audio card. And monitors typically don't have audio, TVs do. Please describe exactly what you need.

---

### Post by querelledb on 2020-01-17
ok, but my headphone doesn't work too.
By the way, I have a Acer SA270Abmi
This is my lshw output!

[https://paste.ubuntu.com/p/dq3xqvWhkh/](https://paste.ubuntu.com/p/dq3xqvWhkh/)

---

### Post by CelticWarrior on 2020-01-17
OK, the Acer SA270Abmi does have speakers.

The problem with HDMI audio is that you have a Nvidia graphics card but you didn't install the Nvidia proprietary drivers. Please open Additional Drivers, select and apply the recommended driver version. Reboot. Now you should be able to select HDMI output at System Setting > Sound.

Regarding the headphones, if they aren't using an USB connection, then they must be using an analog audio jack. Where are you connecting them exactly? If on the front panel make sure you got the connections right in the motherboard. If you're connecting them in the back then it's another issue, what happens exactly when you select the integrated audio in System Settings > Sound? Or there's no such option?

---

### Post by querelledb on 2020-01-17
> **CelticWarrior said:**
> OK, the Acer SA270Abmi does have speakers.

The problem with HDMI audio is that you have a Nvidia graphics card but you didn't install the Nvidia proprietary drivers. Please open Additional Drivers, select and apply the recommended driver version. Reboot. Now you should be able to select HDMI output at System Setting > Sound.
This is the first step iI checked after I installed the OS but there are no drivers to install in there.
> **CelticWarrior said:**
> Regarding the headphones, if they aren't using an USB connection, then they must be using an analog audio jack. Where are you connecting them exactly? If on the front panel make sure you got the connections right in the motherboard. If you're connecting them in the back then it's another issue, what happens exactly when you select the integrated audio in System Settings > Sound? Or there's no such option?
I connected the jack in front and in the back and it doesn't work. It works in Windows.

---

### Post by CelticWarrior on 2020-01-17
> **querelledb said:**
> This is the first step iI checked after I installed the OS but there are no drivers to install in there

You need to do it with an active internet connection. Please post the results from lspci in terminal to check the specific Nvidia graphics model.

> I connected the jack in front and in the back and it doesn't work. It works in Windows.

In the previous post I asked what's the situation in System Settings > Sound?? Namely what happens when you select the internal audio and/or if you see that option

---

### Post by querelledb on 2020-01-17
This is the "ubuntu-drivers devices" output:

```

== /sys/devices/pci0000:00/0000:00:01.2/0000:20:00.0/0000:21:06.0/0000:28:00.0 ==
modalias : pci:v00008086d00002723sv00008086sd00000084bc02sc80i00
vendor   : Intel Corporation
manual_install: True
driver   : backport-iwlwifi-dkms - distro free


```

---

