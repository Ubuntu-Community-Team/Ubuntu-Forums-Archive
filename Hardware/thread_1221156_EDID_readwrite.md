---
title: "EDID read/write"
date: 2009-07-23
forum: Hardware
---

### Post by SupMario on 2009-07-23
hi,

I want to read from and write in an_ [COLOR=Red][EDID memory]("http://en.wikipedia.org/wiki/Extended_display_identification_data")[/COLOR] _of a display monitor. In fact, the EDID is used to describe the sink capabilities (sink supported resolutions, etc...) to the source graphics card. The link between the source and the sink should be an _HDMI_ link because I am dealing with an HDMI stream. _[COLOR=Red][Here is an illustrative diagram]("http://rapidshare.com/files/258659813/HDMI_architecture.JPG.html")[/COLOR]._

Since the EDID EEPROM memory is often not writable, my idea consists in interfacing a PC and use a zone of its RAM memory as an EDID. _The EDID of the sink will be ignored_. 
_[COLOR=Red][The following diagram explain what I aim to do]("http://rs266l32.rapidshare.com/files/258662773/5229162/aim.JPG")[/COLOR]._
The problem is that I have no idea about the nature of the link that I should make between the source HDMI connector and the PC (perhaps I should have a USB==>I²C adapter like _[this]("http://www.harbaum.org/till/i2c_tiny_usb/index.shtml") _. Moreover, I wonder what kind of software should I have on my [COLOR=Red]Ubuntu[/COLOR] laptop so that the source can read the EDID (perhaps a linux USB driver installed in my PC since the DDC channel is based on I²C bus technology ?)

Thanks.

---

### Post by SupMario on 2009-07-23
hi,

I want to read from and write in an_ [COLOR=Red][EDID memory]("http://en.wikipedia.org/wiki/Extended_display_identification_data")[/COLOR] _of a display monitor. In fact, the EDID is used to describe the sink capabilities (sink supported resolutions, etc...) to the source graphics card. The link between the source and the sink should be an _HDMI_ link because I am dealing with an HDMI stream. _[COLOR=Red][Here is an illustrative diagram]("http://rapidshare.com/files/258659813/HDMI_architecture.JPG.html")[/COLOR]._

Since the EDID EEPROM memory is often not writable, my idea consists in interfacing a PC and use a zone of its RAM memory as an EDID. _The EDID of the sink will be ignored_. 
_[COLOR=Red][The following diagram explain what I aim to do]("http://rs266l32.rapidshare.com/files/258662773/5229162/aim.JPG")[/COLOR]._
The problem is that I have no idea about the nature of the link that I should make between the source HDMI connector and the PC (perhaps I should have a USB==>I²C adapter like _[this]("http://www.harbaum.org/till/i2c_tiny_usb/index.shtml") _. Moreover, I wonder what kind of software should I have on my [COLOR=Red]Ubuntu[/COLOR] laptop so that the source can read the EDID (perhaps a linux USB driver installed in my PC since the DDC channel is based on I²C bus technology ?)

Thanks.

---

### Post by Sef on 2009-07-23
merged threads.

---

### Post by SupMario on 2009-07-24
Is anyone here ?

---

