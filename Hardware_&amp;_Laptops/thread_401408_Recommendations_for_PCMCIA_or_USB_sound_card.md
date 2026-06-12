---
title: "Recommendations for PCMCIA or USB sound card?"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by adamklempner on 2007-04-04
The audio jack in my laptop is starting to fail and I am looking for another way to get the music out :).  So, I guess I am looking for either a pcmcia or usb sound card.  Does anyone have any recommendations as to which ones "just work" with [K]Ubuntu?  I don't require anything fancy, I just want simple, cheap, and functional.

Thanks!

---

### Post by nofrak on 2007-04-04
Would love an answer to this one myself.  I'd also like to know whether built-in laptop speakers can work with such a sound card

---

### Post by adamklempner on 2007-04-04
> **nofrak said:**
> I'd also like to know whether built-in laptop speakers can work with such a sound card

I am going to guess the answer to this is "no", or at least not easily.

---

### Post by stokedfish on 2007-04-04
An audigy usb works, but only with a custom alsa conig.

---

### Post by adamklempner on 2007-04-05
I just bought the Griffin iMic from Newegg for $23 +s/h.  [Here it is.]("http://www.newegg.com/Product/Product.asp?Item=N82E16812999078")

I've read that it seems to work with Linux, so I'll give it a shot and let everyone know how it goes.

---

### Post by adamklempner on 2007-04-11
So now I have it and it works with Edgy!  Since I have no option in my laptops bios to turn off the built in soundcard, I had to follow the instructions here for "Configuring default soundcards / stopping multiple soundcards from switching":

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

to get it to use the USB sound card by default.

---

### Post by adamklempner on 2007-10-31
Update to this thread for Kubuntu 7.10...

The above mentioned fix no longer works but I came up with an easier solution:

```
$ cat /proc/asound/cards
 0 [A5451          ]: ALI5451 - ALI 5451
                      ALI 5451 at 0x8400, irq 5
 1 [system         ]: USB-Audio - iMic USB audio system
                      Griffin Technology, Inc iMic USB audio system at usb-0000:00:02.0-2, full speed

```

Then, in the KDE "System Settings" go to the "Sound System" and in the "override device location" box enter:

```
hw:system
```

then apply and test.  Note that what is entered is the name of the sound card that you wish to use in [  ]'s of  cat /proc/asound/cards.

EDIT:  I just found out that this only seems to get the KDE sounds to come out of the usb sound card.  To get Amarok to output to it, I had to configure its xine engine to use alsa instead of "auto", then in the mono and stereo boxes put in "hw:system" (the name of the sound card).  Firefox still uses the internal card and I bet most other programs will.

Is there a better solution?  I don't want to have to configure every program.

---

