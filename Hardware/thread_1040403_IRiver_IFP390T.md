---
title: "IRiver IFP390T"
date: 2009-01-15
forum: Hardware
---

### Post by amheuwr on 2009-01-15
Have resurrected my old MP3 player from the drawer as I have started exercising again. Last  time i used it was on Windows XP. Thought that I would be able to just plug it straight into 8.10  and it would be recognised. Nothing doing.
Have started disk manager and nothing showing.
lsusb shows the following
```
Bus 003 Device 002: ID 1058:0903 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 4102:1003 iRiver, Ltd. iFP-300 series mp3 player
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 056a:0017 Wacom Co., Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
Third line down shows that it is connected, but it just  won't  show as a mountable device.
Have trawled the forums with several suggestions but none have worked. 
Tried using gparted but device not seen either.
Any ideas?

---

### Post by Denestria on 2009-01-15
> Have trawled the forums with several suggestions but none have worked. 

Kind of hard to suggest something for you to try when you don't explain what hasn't worked for you.

Did you search Synaptic for ifp?  I have an iRiver ifp799.  I don't use it anymore but when I did it mounted, updated the firmware, formatted and copied files great with the  ifpgui program.

---

### Post by amheuwr on 2009-01-15
Obviously I didn't trawl enough, although I did trying searching Synaptic several times for Iriver and just river. Had not crossed my mind to search for ifp which of course returned several packages. In fact while searching for just the word river in synaptic caused synaptic to crash. I have downloaded the GUI and will try it later. Thanks

---

