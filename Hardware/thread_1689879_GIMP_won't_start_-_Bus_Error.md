---
title: "GIMP won't start - Bus Error"
date: 2011-02-17
forum: Hardware
---

### Post by banago on 2011-02-17
Hi there,

I run Ubuntu 10.10 (fresh install) in Compaq Presario F700. I got GIMP yesterday and it worked great. Today it won't start. It hangs and loads the processor to much at:

> Looking for data files - Documents

When I run it form Terminal I get: 

> Bus Error

How can I solve this - please help!

---

### Post by banago on 2011-02-17
This worked for me:

   1. Make sure that gimp isn't running (check with "ps -ef | grep gimp", or use the system monitor)
   2. Back up any custom brushes and whatever you want to keep from ~/.gimp-2.6
   3. Delete the .gimp-2.6 folder from your home folder.
   4. Start gimp

---

