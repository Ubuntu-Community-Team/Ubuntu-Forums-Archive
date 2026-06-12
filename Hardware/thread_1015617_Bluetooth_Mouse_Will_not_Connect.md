---
title: "Bluetooth Mouse Will not Connect"
date: 2008-12-19
forum: Hardware
---

### Post by TRD-USA-INTERN on 2008-12-19
Hey guys/gals. My bluetooth mouse will not connect to my computer at all. I can sync my Motorola Q, but my mouse spits out errors like nobody's business. It is the "Microsoft Bluetooth Notebook Mouse 5000" and I am running it on a DELL XPS (I don't think that matters though). I have attached a screenshot for you reference. Thanks in advance!

-INTERN

---

### Post by HyRax on 2008-12-26
I use a Microsoft Bluetooth Notebook Mouse 5000 as well on Intrepid with no issues (other than the current reconnection bug in Intrepid which I employ a workaround for). Here's my [blog entry](http://www.serenux.com/?p=265) detailing how to pair it - see if you're doing something different.

---

### Post by gjosef on 2009-01-20
Looks like you are using the Browse Device command, but it is not meant for attaching mice and keyboards. More for browsing file systems on a smartphone if I've got it right. Instead you should right-click the bluetooth icon and go to the preferences screen. There, look at the Services tab and click on Input ervice, then Add.

---

### Post by thundaraptor on 2009-03-22
Am trying to follow directions with same mouse.  not working.  i don't have the services tab once i right click on the bluetooth icon.  ideas?

---

### Post by gjosef on 2009-04-10
> **thundaraptor said:**
> Am trying to follow directions with same mouse.  not working.  i don't have the services tab once i right click on the bluetooth icon.  ideas?

The description I gave is valid for Ubuntu 8.04. In Ubuntu 8.10, the bluetooth screen is a little bit changed. Here, I right-click the bluetooth icon and choose "Setup new device..." to attach my bluetooth mouse. It doesn't always appear on the first try, so sometimes I have to restart the wizard and click the connect button of my mouse again before it appears.

Right now I am using a Logitech mouse (M-RBB93) with Ubuntu 8.10, and it connects well but loses its connection once the computer restarts or falls into sleep mode. I then have to remove the matched bluetooth device and re-attach it. This wasn't necessary in Ubuntu 8.04.

---

### Post by gjosef on 2009-04-11
> **gjosef said:**
> Right now I am using a Logitech mouse (M-RBB93) with Ubuntu 8.10, and it connects well but loses its connection once the computer restarts or falls into sleep mode. I then have to remove the matched bluetooth device and re-attach it. This wasn't necessary in Ubuntu 8.04.

Small addition: This problem actually was solved yesterday, when I applied the latest ubuntu updates. The mouse works well now, no pairing problems anymore.

---

