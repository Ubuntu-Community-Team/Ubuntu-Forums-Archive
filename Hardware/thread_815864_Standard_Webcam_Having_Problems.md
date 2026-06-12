---
title: "Standard Webcam Having Problems"
date: 2008-06-02
forum: Hardware
---

### Post by money2themax on 2008-06-02
I can't seem to get my webcam to work i bought it off amazon.com heres the link if that helps it works with 95-Vista
[URL="http://www.amazon.com/gp/product/B0015TJNEY"]
http://www.amazon.com/gp/product/B0015TJNEY[/URL]

---

### Post by linuxwizard on 2008-06-02
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If cam does not work post the results of the command > lsusb

---

### Post by money2themax on 2008-06-02
here's the outcome

```

money2themax@MX-UBUNTU-000:~$ lsusb
Bus 003 Device 008: ID 05ac:1261 Apple Computer, Inc. 
Bus 003 Device 006: ID 1058:0702 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 1c4f:3000  
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 002: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

```

---

### Post by new2linux2008 on 2008-06-02
you my want to try out this link:

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by money2themax on 2008-06-02
no luck it works with windows flawlessly

---

### Post by money2themax on 2008-06-11
now its not working flawlessly with windows

---

### Post by money2themax on 2008-06-25
more
```

money2themax@MX-UBUNTU-000:~$ lsusb
Bus 003 Device 003: ID 1058:0702 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
[COLOR=Red]Bus 001 Device 008: ID 0572:0001 Conexant Systems (Rockwell), Inc. Ezcam II WebCam[/COLOR]
Bus 001 Device 005: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 002: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```and the next instance with the other webcam
```

money2themax@MX-UBUNTU-000:~$ lsusb
Bus 003 Device 003: ID 1058:0702 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
[COLOR=Red]Bus 001 Device 014: ID 1c4f:3000 [/COLOR] 
Bus 001 Device 013: ID 1131:1004 Integrated System Solution Corp. 
Bus 001 Device 005: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 002: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

```
it didn't show up with a name

---

