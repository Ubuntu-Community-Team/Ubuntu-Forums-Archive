---
title: "[SOLVED] Can't pair with Bluetooth headset"
date: 2008-07-13
forum: General Help
---

### Post by The Foz on 2008-07-13
Maybe someone can help me. I have searched through the existing posts, and can't find the answer.

I have a Bluetrek Bizz headset. I know it works, as I can use it with my mobile phone.

What I can't do is pair it with my Ubunutu 8.04 PC (I have been trying for several weeks now). I know that my bluetooth on the PC (I have a USB bluetooth adaptor) is working, as I can also pair with my mobile phone and synchronise my contacts list.

I have tried connecting using the bluetooth applet. I at least now have the headset in the list of known devices, but "connecting" with the applet throws an error (of course). There are no options (no buttons or menus) to add an audio device in the Preferences->Services pane.

I have had absolutely no success with hcitool. Scanning does not show my headset (yes, I put it in pairing mode first); trying to connect gives an error: "Can't create connection: Input/output error".

Any suggestions would be welcome.

---

### Post by fragos on 2008-07-13
Try installing the GUI bluetooth manager blueman. It helped me get my Plantronics headset paired.

---

### Post by AmericanYellow on 2008-07-13
I think Ubuntu doesn't install the different protocols for bluetooth that actually allow you to use it. I don't know what bluetooth protocol is used by bluetooth headsets, but you can search online and find out. You can try installing the standard protocols and see if any of them work. If you go to Synaptic Manager you can try installing obexpushd, or obexfs, or obexftp. 

sudo apt-get install obexpushd  #if you are using the terminal


Try them one at a time.

Good luck.

---

### Post by The Foz on 2008-07-16
Thanks, fragos.

I installed Blueman, and got the headset working with Skye.

Blueman has exactly the functionality that I had expected in the bluetooth applet.

---

### Post by DarchAengel on 2008-08-15
I downloaded the blueman so that I can connect my plantronics.  I seem to have got it connected.  But how do I direct the sound to the headset as opposed to the speakers on the laptop?

---

