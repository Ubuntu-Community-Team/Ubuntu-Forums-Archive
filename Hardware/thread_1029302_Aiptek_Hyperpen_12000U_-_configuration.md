---
title: "Aiptek Hyperpen 12000U - configuration"
date: 2009-01-03
forum: Hardware
---

### Post by VojtaW on 2009-01-03
Hi,
I've got a problem with this Aiptek tablet. I've installed the aiptek driver using Synaptic on a fresh version of intrepid ibex on my laptop. The tablet didn't work properly, so I tried to configure it using this setting:[https://help.ubuntu.com/community/AiptekTablet]("https://help.ubuntu.com/community/AiptekTablet"). But it doesn't change *anything*. :( 

The tablet seems to work in at least some way though - The movement of the stylus above the tablet is recognized and makes the cursor move in the absolute mode(not as a mouse), but the resolution is weird. Plus the mode changes after first touching the tablet by the pen after startup - the cursor then moves only when touching the surface and it moves in the relative mode(as a mouse).

So there **is** a recognition of the movement above the tablet and of the touch of the pen on the surface to say at least. Hence it should be just a matter of right configuration.:D Could someone please help me with this?

---

### Post by VojtaW on 2009-01-04
Does anyone have any ideas?

---

### Post by ssam on 2009-01-04
have you tried installing
```
wacom-tools_0.8.1.6-1ubuntu2_i386.deb
xserver-xorg-input-wacom_0.8.1.6-1ubuntu2_i386.deb
```
from
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

they help for a aiptek (trust tb-3100) for me

---

### Post by VojtaW on 2009-01-04
Just tried to do so, after setting up the .fdi file there seemed to be no problem until touching the surface of the tablet again - the absolute tracking works, but when I touch the tablet, it just stops interacting completely. Suppose the wacom driver has to be set up specially for the aiptek tablets, any hints?

And another update, the error which keeped the originally anounced aiptek driver from taking effect was a whitespace in one parameter. Everything works great with the tablet as far - absolute tracking, click reaction when touching the surface. But I can't go further than the log screen on startup. Everytime I try to login, it seems that it will start normally, but returns back to the log screen after a while. It sure is the driver which at least initially causes it, because when I use my livecd to delete the .fdi file, everything works just normal again. Has anyone got any experience with the aiptek driver behaving like that? 

Maybe its the configuration .fdi file which makes it go wrong, so I'm posting the whole content.
```
<?xml version="1.0" encoding="UTF-8"?> 
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
    </match>
  </device>
</deviceinfo>
```

---

### Post by poltiser on 2009-01-28
I had the same problem, than I downloaded aiptek driver with synaptic and somehow everything works... but I cannot start Ubuntu 8.1 with usb connected (of the tablet) it comes back to the user & Password dialog... (bug ???) only when I disconnect the tablet for start up - system loads and I can connect and use the tablet...
I copied the above... as well. 
All other drivers and files must be out of the system... no hyperpen, no wacom, no anything...
Can I improve the behaviour of Ubuntu?

---

### Post by Masquerade on 2009-05-03
> **poltiser said:**
> I had the same problem, than I downloaded aiptek driver with synaptic and somehow everything works... but I cannot start Ubuntu 8.1 with usb connected (of the tablet) it comes back to the user & Password dialog... (bug ???) only when I disconnect the tablet for start up - system loads and I can connect and use the tablet...
I copied the above... as well. 
All other drivers and files must be out of the system... no hyperpen, no wacom, no anything...
Can I improve the behaviour of Ubuntu?

yes, this is a bug claimed [here]("https://help.ubuntu.com/community/AiptekTablet")

---

### Post by adamorjames on 2009-05-19
I'm having the touching problem too. Anyone out there know a fix?

EDIT: Ah, I see what the OP meant. I had a mistake in mine too (copied the line before the config on the Ubuntu doc site on accident). Touching the tablet now works.

---

