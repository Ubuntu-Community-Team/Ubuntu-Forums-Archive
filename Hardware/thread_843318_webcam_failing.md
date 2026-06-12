---
title: "webcam failing"
date: 2008-06-28
forum: Hardware
---

### Post by dboes on 2008-06-28
Ubuntu 8.04 Hardy Heron
Webcam Trust WB 3500T

lsusb
Bus 005 Device 004: ID 04a9:221c Canon, Inc.
Bus 005 Device 003: ID 0d49:3200 Maxtor
Bus 005 Device 002: ID 2770:930c NHJ, Ltd (this is the webcam)
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 03f0:0004 Hewlett-Packard DeskJet 895c
Bus 001 Device 001: ID 0000:0000

lsmod | grep videodev

this command returns nothing.
But the light on the webcam goes on.
After that again nothing
No image in Camorama or Ekiga and so on.

Someone that have installed this particular webcam or webcam with simular hardware id?

Edit: I believe i should use the driver sq930c (sq930x) but dont know if that driver can already be used. Someone have experience with it?
Besides that i don't know how to install it in Ubuntu 8.04

Please tell me how.

Tnks

---

### Post by AlexBellisBrown on 2008-06-28
Have you tried a webcam viewing program? Like Cheese? See if it works with one of them. (EDIT: I see you already did, did it give error messages or just a black screen?) You can get it from the Add/Remove programs.

---

### Post by dboes on 2008-06-29
Tested many programs.
Under cheese:
black screen
even under gstreamer-properties.
He cannot find the device

---

