---
title: "Another displaylink driver issue in kernel 4.10.0-38-generic"
date: 2017-11-20
forum: Hardware
---

### Post by di-mk1 on 2017-11-20
I just did a fresh install of 16.04.3, Unity environment and kernel 4.10.0-38-generic. My laptop is a Dell XPS 1350 and I have attached the DA100 adaptor to connect to my VGA monitor at work.
  Problem: the desktop behavior in the external monitor is very sluggish, mouse flickers, a general sense of things done slowly :)
  
Some info: 
1. DLM service is up and running

  ```
&#9679; dlm.service - DisplayLink Manager Service
   Loaded: loaded (/lib/systemd/system/dlm.service; enabled; vendor preset: enabled)
   Active: active (running) since Mo 2017-11-20 14:07:50 CET; 23min ago
  Process: 1372 ExecStartPre=/bin/sh -c modprobe evdi || (dkms install evdi/1.4.210 && modprobe evdi) (code=exited, status=0/SUCCESS)
 Main PID: 1375 (DisplayLinkMana)
   CGroup: /system.slice/dlm.service
           &#9492;&#9472;1375 /opt/displaylink/DisplayLinkManager

Nov 20 14:07:50 xps systemd[1]: Starting DisplayLink Manager Service...
Nov 20 14:07:50 xps systemd[1]: Started DisplayLink Manager Service.
Nov 20 14:07:50 xps systemd[1]: Started DisplayLink Manager Service.

```  

2. Output of **xrandr --listproviders**
```
Providers: number : 2 
Provider 0: id: 0x49 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 6 associated providers: 1 name:Intel 
Provider 1: id: 0x12b cap: 0x2, Sink Output crtcs: 1 outputs: 1 associated providers: 1 name:modesetting

``` 
 
What I've done so far to troubleshoot the problem is to add the file **20-displaylink.conf** into my **/usr/share/X11/xorg.conf.d/** folder containing:
  ```
Section "Device"
    Identifier  "Intel"
    Driver      "intel"
    Option      "VSync" "false"
EndSection
```
  
This in fact allowed me to get at least a display in the external monitor since previously I was getting just a frozen screen.
  **THE WEIRD PART:** the exact same setup was working like a charm on a previous kernel. I think it was 4.9.xxx. Any ideas?

---

