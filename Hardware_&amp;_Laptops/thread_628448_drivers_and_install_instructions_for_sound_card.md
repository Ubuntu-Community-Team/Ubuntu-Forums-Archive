---
title: "drivers and install instructions for sound card"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by eeeandrew on 2007-12-01
hi guys, I've now been running ubuntu about a month still trying to get my head around the terminal. My sound card hasn't worked on ubuntu and I thought it was impossible to get drivers for this particular card because the windows output gave it a name only windows drivers are made for. the other day I discovered the "sudo lspci" command and I have now found its a common intel chip. Does anyone know where to get the drivers and how to install them? it would also be helpful to post a short explanation of any terminal commands used so I can start to work this stuff out myself.

sudo lspci gave:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


thanks in advance,
Andrew

---

### Post by linuxonbute on 2007-12-01
> **eeeandrew said:**
> hi guys, I've now been running ubuntu about a month still trying to get my head around the terminal. My sound card hasn't worked on ubuntu and I thought it was impossible to get drivers for this particular card because the windows output gave it a name only windows drivers are made for. the other day I discovered the "sudo lspci" command and I have now found its a common intel chip. Does anyone know where to get the drivers and how to install them? it would also be helpful to post a short explanation of any terminal commands used so I can start to work this stuff out myself.

sudo lspci gave:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


thanks in advance,
Andrew
Right, I don't have this in my machine but I can see you are new to this.
Here is what you need to look at
[http://thio4linux.wordpress.com/2007/10/06/intel-hda-intel-corporation-82801g/](http://thio4linux.wordpress.com/2007/10/06/intel-hda-intel-corporation-82801g/)

This is what I did to find it :
I went to this site:
[http://www.google.com/linux?hl=en&q=&btnG=Search](http://www.google.com/linux?hl=en&q=&btnG=Search)

which brings up a search box.

I put 
 Intel Corporation 82801G
 in the search box and saw the result I am posting to you.

There were more but that was the first one.
Hope it works.
If not try some of the others.
If you have problems get back to us.

---

### Post by eeeandrew on 2007-12-01
sorry should have edited my post...the driver is now installed after I visited the IRC channel earlier this evening. unfortunately the card still doesn't work properly. It likes to whistle out of the left speaker while playing music and randomly cuts out.

After a couple of hours playing around with the volume controls and individual channel mutes helped along by the IRC channel, I am still no closer to a solution.

thanks for taking the time to get back to me,
Andrew

---

