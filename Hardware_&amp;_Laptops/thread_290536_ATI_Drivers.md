---
title: "ATI Drivers"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by DevNull11 on 2006-11-01
I have downloaded xorg-driver-fglrx and fglrx-control. I also setup Xorg to use fglrx. 
```
Section "Device"
        Identifier      "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

```

Whenever I run fireglcontrol I get this error.
```
fireglcontrol: cannot connect to X server
```

I think I don't have my drivers setup right. Please tell me I'm wrong.

---

### Post by IcemanV9 on 2006-11-01
I have exact same ATI video card as yours (Radeon Mobility X600).

Check out this offical **[COLOR="Orange"][wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")[/COLOR]** OR unoffical **[COLOR="Orange"][guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")[/COLOR]**.

Those info will help you to make sure it is installed correctly.

---

### Post by strabes on 2006-11-01
Yeah those should work for you. It looks like you just haven't followed one of them.

---

### Post by DevNull11 on 2006-11-02
I used both guides and I get the same result with both. 
```
sam@sam-laptop:~# sudo fglrxinfo
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

```

---

### Post by IcemanV9 on 2006-11-02
If you are [COLOR="Orange"]**root**[/COLOR], then do NOT use [COLOR="Orange"]**sudo**[/COLOR]. Just type [COLOR="Orange"]**fglrxinfo**[/COLOR].

Anyhow, you can get info via fglrxinfo as normal user. Here's info as normal user ...

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

---

### Post by DevNull11 on 2006-11-04
Ok now I'm starting to get it root dose not have an X server so thats why I was getting the errors.

---

