---
title: "webcam won't work"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by 1002285 on 2007-04-13
I have Dell XPS M1210 and I currently use Feisty.
I have never got the built-in webcam to work (neither in Ubuntu nor in LinuxMint, Edgy, Dapper, Feisty, whatever).
The camera works in Windows.

Output of lsusb shows Logitech:
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:8126 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:08c6 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000

---

### Post by brsseb on 2007-04-15
Try

[http://digilander.libero.it/demarchidaniele/qcamvc/quickcam-vc.html](http://digilander.libero.it/demarchidaniele/qcamvc/quickcam-vc.html)

I got a picture from my cam on my m1210, but no sound (and the quality was terrible).

But webcam support under linux is pretty bad. Even if the cam works, I have found almost no applications that let me use it for anything usefull. No webcam support in either Gaim or Skype.

---

### Post by 1002285 on 2007-04-16
> **brsseb said:**
> Try

[http://digilander.libero.it/demarchidaniele/qcamvc/quickcam-vc.html](http://digilander.libero.it/demarchidaniele/qcamvc/quickcam-vc.html)

I got a picture from my cam on my m1210, but no sound (and the quality was terrible).

But webcam support under linux is pretty bad. Even if the cam works, I have found almost no applications that let me use it for anything usefull. No webcam support in either Gaim or Skype.

AMSN and Kopete have webcam support. I have seen a picture of myself in my webcam now, but the other party in the conversation (either with AMSN or Kopete) have not received it for some reason. Of course it's a pity that Skype does not have video in Linux.

And I have not got the sound to work either.

---

### Post by tommi on 2007-04-16
here with kubuntu feisy sound worked out of the box with skype. the webcam does work, too. this wrks since UVC driver is integrated in feisty. USB Video Class is a driver for the Integrated Dell Webcam. U can google for it. in Kopete u see only a green screen, thats a bug of kopete. this will be fixed later.

---

### Post by Mega_slayer on 2007-08-02
But skype on linux does not have video right? So how can your webcam work with skype in linux?

---

### Post by hardysmiles on 2007-08-06
Hi,
I also have a xps M1210, and though I didn't get one with a webcam, i haven't yet been able to get the mirophone to work correctly (i'm running fiesty). If anyone has successfully gotten the micro going, could you please let me know how, or send me the link? 

thanks!

---

### Post by 1002285 on 2007-08-07
> **Mega_slayer said:**
> But skype on linux does not have video right? So how can your webcam work with skype in linux?
I think Tommi meant that "sound worked with skype".
For me, the webcam, both sound and picture, work now. I use LinuxMint Bea and I guess it has this UVC driver, too.

---

### Post by codemills on 2007-08-07
ya , skype video  is "work in progress' , so anyone wanting to test voip with video "waters" , get Openwengo.org , works flawless (but crappy cam quality) :D

---

