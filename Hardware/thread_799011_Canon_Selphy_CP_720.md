---
title: "Canon Selphy CP 720"
date: 2008-05-18
forum: Hardware
---

### Post by PippoFranco on 2008-05-18
I have connected a Canon Selphy CP 720 postcard printer to my laptop (I use Hardy and cups).

Cups detected the new printer as soon I powered it up and installed the proper driver:

Canon SELPHY-CP-720 - CUPS+Gutenprint v5.0.2 Simplified.

Unfortunately the printer doesn't work properly: the printing process stops after the first postcard is loaded.

Any suggestion?

Franco

---

### Post by ibizatunes on 2008-06-23
I to have this problem, does anyone know how to fix it?

---

### Post by whoop on 2009-02-19
Anybody tried newer drivers? The repository drivers are over a year old.
[http://gimp-print.sourceforge.net/](http://gimp-print.sourceforge.net/)

I can't try it myself cause I ain't got the printer on me at the moment.

---

### Post by Domas on 2009-05-13
Same problem here with cp760.

---

### Post by whoop on 2009-05-13
> **Domas said:**
> Same problem here with cp760.
What version of ubuntu are you running?

---

### Post by Domas on 2009-05-14
I am using 9.04 ubuntu. Have you got it running?

---

### Post by whoop on 2009-05-14
> **Domas said:**
> I am using 9.04 ubuntu. Have you got it running?

I will be trying to get the canon selphy 720 to work under 8.04 and 9.04 this sunday.
The fact that you are running 9.04 concerns me as 9.04 uses the latest gutenprint driver. However you seem to have a newer printer model (760) which is not known to be supported under gutenprint (as far as I can tell). It could be that it uses the same firmware and has the same interface as the 750 (then we are in trouble), but I don't know about that.

In the meantime I am keeping this bug alive at: [https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/292016](https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/292016)

Hopefully more (good) news on sunday (from me).

---

### Post by Domas on 2009-05-14
Fingers crossed and waiting for the news, thanks !

---

### Post by whoop on 2009-05-17
Tried running the cannon selphy 720 on a Jaunty machine today... No go :(
I have updated the launchpad bugreport.
Will be trying it on Hardy soon with newer drivers.

---

### Post by Domas on 2009-05-19
Hi whoop,

If you need any test with my 760 on Jaunty let me know, would be glad to help.

---

### Post by whoop on 2009-05-24
> **Domas said:**
> Hi whoop,
If you need any test with my 760 on Jaunty let me know, would be glad to help.
Hey man, if I am not mistaken the gutenprint drivers (which we are using) should work with all Selphy machines (where just not having any luck).
Could you do me a favour and try to print something with different paper sizes on your machine? Like Postcard, 4x6 and the like. Could be that the printer doesn't know what to do because we didn't configure the printer settings correctly.

---

### Post by Domas on 2009-05-25
Hi,

I will give a try on Wednesday, sorry for keeping so long, but too busy days at the moment... Hope something will work.

Cheers.

---

### Post by whoop on 2009-05-25
> **Domas said:**
> Hi,

I will give a try on Wednesday, sorry for keeping so long, but too busy days at the moment... Hope something will work.

Cheers.
No worries man, I also posted a bugreport on the developer site of gutenprint, so we'll see what that brings us.

---

### Post by whoop on 2009-11-02
Can anybody confirm if Canon Selphy CP-720 is working with ubuntu 9.10?
As this version of ubuntu contains updated gutenprint drivers --> 5.2.4.

---

### Post by mikesmithv on 2010-01-24
I can confirm the Canon Selphy CP-600 is NOT working with ubuntu 9.10 (same symptoms as reported with the CP-720).  There is not much chatter about the CP-720 lately, but I would be glad to pursue this with the CP-600 if you want.  It appears to use the same basic driver code base.

When I want to print photos I have to reboot under Windows.  This is the last remaining thing that requires Windows so I am motivated to fix this!

---

