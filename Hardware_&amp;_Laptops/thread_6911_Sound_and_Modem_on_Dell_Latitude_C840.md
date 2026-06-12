---
title: "Sound and Modem on Dell Latitude C840"
date: 2004-12-02
forum: Hardware &amp; Laptops
---

### Post by Randy Winchester on 2004-12-02
Hi all,

My first post here . . . I just discovered Ubuntu about two weeks ago.

I had the pleasure of installing ubuntu Warty on a Dell Latitude c840, 2.0G, 512M, last weekend.  Everything went nicely and just about everything works except the sound and the modem.

The hardware manager reports a
Cirrus Logic 82801CA / CAM AC '97 Audio Controller and a
82801 CA / CAM AC '97 Modem Controller.  

The devices are a
Crystal WDM Audio Codec at PCI bus 0, device 31, function 5 and a
Dell Inspiron 2100 Internal Modem at PCI bus 0, device 31 function 6

Under XP, the modem is set up on COM 3.  I can't locate it with the PPPConfig and alsactl reports "load_state: 1134: No soundcards found..."

I haven't been able to locate any references to this.  Does anyone have any suggestions where I might start poking around?  It's a nice looking set up, but not of much use without the modem.

I also set up a Dell OptiPlex GX400.  It's working great!  No problems so far!

---

### Post by Magneto on 2004-12-02
search for linmodems wintel pc modem in the forums and google and you will see all the posts on the topic

[http://www.ubuntuforums.org/showthread.php?t=5464&highlight=audio+irq](http://www.ubuntuforums.org/showthread.php?t=5464&highlight=audio+irq)

what have you been searching for? there really are a whole lot of posts about both of these topics, you should check how you are searching

---

### Post by Randy Winchester on 2004-12-03
[QUOTE=Magneto]search for linmodems wintel pc modem in the forums and google and you will see all the posts on the topic

[http://www.ubuntuforums.org/showthread.php?t=5464&highlight=audio+irq](http://www.ubuntuforums.org/showthread.php?t=5464&highlight=audio+irq)

what have you been searching for? there really are a whole lot of posts about both of these topics, you should check how you are searching[/QUOTE]

Looking for love in all the wrong places . . .   :mrgreen: 

Thanks for putting me on the fast track.  I got the sound working right away.  That's a good first step.  I didn't realize that the modem driver might be such a convoluted mess.  I'm going to attempt to compile / install a 537EP driver I found on the Intel site.  I'll report back if all goes well.

---

### Post by donely on 2005-05-02
Before I try installing hoary on my latitude c840, is there anyone who has had any success with it?

---

