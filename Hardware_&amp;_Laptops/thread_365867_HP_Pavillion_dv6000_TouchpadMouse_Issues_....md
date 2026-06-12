---
title: "HP Pavillion dv6000 Touchpad/Mouse Issues ..."
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by dbee on 2007-02-20
So my hp Pavillion touchpad has a mind of it's own when I installed linux on it. It works fine for windows.

The touchpad right clicks, and left-clicks of it's own volition. It's extremely annoying when I'm trying to type and the caret keeps resetting to the cursor mark. If I happen to leave the cursor on the system tray or by an open window. It will open, close or switch windows on me. Things work fine when I disable the touchpad.

I've installed gsynaptics and that really didn't help at all.

Does anyone know what I can do ? If this goes on, I'll have to dump ubuntu and go back to windows I'm afraid :-( ... So please, please help ...

---

### Post by teaker1s on 2007-02-21
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")
also on desktop under system tab you can alter mouse preferences and alter sensitivity.

---

### Post by dbee on 2007-02-22
Thanks teaker :-)

I might be able to get my microphone working now.

However, unfortunately it doens't say anything about the gittery touchpad issue that I'm having :-(

---

### Post by teaker1s on 2007-02-22
have you tried mouse settings, mine's a little jumpy-but certainly better since I played with settings

---

### Post by karl_forshaw on 2007-02-22
I had a DV6000 and the touchpad problems were due to me using the bcm43xx wireless drivers. I blacklisted the driver and started using ndiswrapper with the windows drivers and this problem disappeared.

---

### Post by teaker1s on 2007-02-22
this too could be why mine settled down, problem is I've done so many changes i find it hard to remember which was when:confused:

---

### Post by dbee on 2007-02-26
Yeah, I've fiddled with the mousepad settings already. But it didn't do any good.

I don't seem to have the bcm43xx drivers installed. Nor do I have the ndiswrappers installed.

I've done a check for the package names, and they don't register as being installed...
```

$ apt-cache search bcm43
$ apt-cache search ndiswrapper

```
How do I find out which drivers my touchpad and wireless connection are using ?

Should I really go messing with my wireless if it already works ? The touchpad issues could be solved by the wireless drivers ? Does that seem a little strange ?

Also, should I install the broadcom ndiswrappers, or should I install the windows ndiswrappers ... ?

Thanks guys :-)

---

### Post by karl_forshaw on 2007-02-26
The bcm43xx is installed by Ubuntu but you usually have to run the FirmWare cutter to get it working, did you have to do this or did your wireless just work? Which version of Ubuntu are you running?

It does sound strange but its been complained about a lot. Perhaps our laptops are different, I will double check the model number when I get home later.

---

### Post by dbee on 2007-02-26
Thanks Karl_forshaw,

I'm running edgy.

I'm fairly sure that the wireless just pretty much worked when I installed ubuntu. 

I had nvidia driver issues, also I have on-going microphone sound issues as well as this touchpad issue (maybe some other stuff as well - I can't remember).  I don't remember anything about  a firmware cutter though.

It seems that the dv6000 is a bit of a hodge podge when it comes to hardware :-(

How exaclty did you blacklist the drivers ? ... just remove them ?

---

### Post by karl_forshaw on 2007-02-27
Lol, call me Karl.

On second glance my laptop is a DV8000 Series, so your touch pad issues probably have nothing in common to mine.

However, I've set up Ubuntu on five HP laptops now and more often than not I had to disable APIC, APCI, and/or SMP at boot time. Have you tried doing this?

Also I found this link for you to have a look at.

[http://www.pbm.com/~lindahl/dv6110us.html](http://www.pbm.com/~lindahl/dv6110us.html)

Let me know if you need anything else.

---

