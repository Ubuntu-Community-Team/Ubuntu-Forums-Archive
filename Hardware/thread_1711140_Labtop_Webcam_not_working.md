---
title: "Labtop Webcam not working"
date: 2011-03-20
forum: Hardware
---

### Post by Joe_Ib on 2011-03-20
Hey I am curious as to how to get my web cam that is built into my laptop to work with ubuntu.  If you need to know any specific information about anything let me know I just don't know what you need to know to help me figure this out.  

I have a HP pavilion dv7-1245dx entertainment notebook.  (thats all the info i know so far sorry)

---

### Post by mikewhatever on 2011-03-21
Post the output of **lsusb** just to see if the device is recognized at all.
Check out the troubleshooting howto as well.
[https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)

---

### Post by Joe_Ib on 2011-03-21
how do you do that?

---

### Post by mikewhatever on 2011-03-21
Applications->Accesories->Terminal, type **lsusb** in the window that opens, then hit enter. The output should show all detected usb devices.

---

### Post by Joe_Ib on 2011-03-21
Here is the output.

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:c107 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


does it matter that the webcam is built into the laptop?

---

### Post by mikewhatever on 2011-03-21
Thanks. 
Most webcams are internally connected via USB, so it shouldn't matter. In the worst case (if that wasn't a usb webcam), it wouldn't show up.
That's the webcam, by the way.
```
Bus 001 Device 002: ID 064e:c107 Suyin Corp.
```

---

### Post by Joe_Ib on 2011-03-21
okay i looked at the troubleshooting link you posted but doesn't seem to help me and now i know that the webcam is detected correct?  what should i do next?

---

### Post by Joe_Ib on 2011-03-21
Bump 

How can I even test to see if webcam is working now?

---

### Post by mikewhatever on 2011-03-22
Well, if you haven't tested the webcam yet, try Cheese or Skype. I've searched the inernet for tips, but, apparently, no one reported webcam problems with your laptop model.

---

### Post by bent12 on 2011-03-22
Score proven updating the webcam utility? Crack the manufacturers websites for the fashionable update for your method.

---

### Post by Joe_Ib on 2011-03-29
sorry it took so long to reply but figured the problem out web cam working perfectly with cheese and other apps.  thank you for the help very much appreciated

---

