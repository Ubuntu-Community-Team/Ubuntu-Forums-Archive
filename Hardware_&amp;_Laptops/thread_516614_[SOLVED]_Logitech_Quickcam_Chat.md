---
title: "[SOLVED] Logitech Quickcam Chat"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by carlosjoan91 on 2007-08-03
Hi, i have the logitech quickcam chat, in ubuntu Feisty, it supposedly should work out of the box according to this site [https://help.ubuntu.com/community/Spca5xx#head-032065f8a5fb6a485a7985ddb3a40262a0629fe5](https://help.ubuntu.com/community/Spca5xx#head-032065f8a5fb6a485a7985ddb3a40262a0629fe5) but it doesntnt get detected, it just stays with the led on, and it doesnt work in any program that i could use it, just as if it wasnt plugged in, does anyone know how can i get it to work?

ps: this is the lsusb output:
Bus 002 Device 004: ID 046d:092e Logitech, Inc. 

thanks in advance

---

### Post by w4ett on 2007-08-03
I believe you will have to install the driver spca5xx for that particular camera.  Additionally from the Synaptic Package Manager, instal the program [COLOR="Red"]camstream[/COLOR].  It sometimes works when all others fail.  You launch it via the terminal: camstream.

---

### Post by carlosjoan91 on 2007-08-03
im sorry if this is a silly question, but how do i install the spca5xx driver, i triedinstalling spca5xx-source from synaptic, but it didnt help, the camera is still unrecognized, and when i try to start camstream it tells me:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Failed to open configuration file for reading.

thanks in advance =D

---

### Post by w4ett on 2007-08-03
I never had to do it myself, so I'll refer you to the Ubuntu Wiki for the install proceedures:

[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

---

### Post by carlosjoan91 on 2007-08-04
in that site says feisty should have it installed, and if i try to follow the other instructions (for  older versions) i get errors, and at last where it says that if it doesnt work in versions it should, reinstall following instructions, i click it, and the link takes me nowhere ><, im getting really frustrated because i know the webcam is supported, and i cant get it to work, and is the only thing stopping me from going completely to ubuntu, thanks in advance

---

### Post by w4ett on 2007-08-04
OK, lets try another application.  In Applications>Add/Remove search for and install an application called Camorama.  It will install an icon under Applications>Graphics.....Run it and see if it detects your webcam.

---

### Post by carlosjoan91 on 2007-08-04
greaat! it detekts it, and amsn does also, so its fine for me, THANK YOU VERY MUCH! =D, is it okey if i ask here how to install the snack librery for audi functions, or should i make a new topic for that?

edit:also, is it normal that the webcam led satys on after the fisrst time i use it, its not really an issue just want to know if its fixable

---

### Post by w4ett on 2007-08-04
I suspect that  the LED will remain on while powered, though I haven't had any experience with your particular camera.  Glad we got it working for you :)

The audio issue should be addressed in a new thread. , so mark this one solved and we'll get to work on the new issue in a new thread.

---

### Post by Cohh on 2007-10-17
Hello!

I just recently purchased a Quickcam Chat after reading this thread =D

However, i'm encountering a problem with it and Camarama. It picks it up correctly, and i see an image; however if i try to make the image Large from Medium, I get an error saying Camera Input Not Supported. If I try to make it small from medium, same thing. I can't manually adjust the image either and it's left as a near unreadable teensie tiny image. 

Anyone know anyway around this?

---

