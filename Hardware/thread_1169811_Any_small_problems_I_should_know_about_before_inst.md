---
title: "Any small problems I should know about before installing?"
date: 2009-05-25
forum: Hardware
---

### Post by moebob24 on 2009-05-25
So I am so ready to install Ubuntu 9.04 Netbook Remix on my Asus 901 Eee PC. But before I do I want to know about any little problems that it has. I read on the Ubuntu site that:

> Asus Eee 901

Everything works well apart from the sleep button, wireless on/off button, special-purpose buttons, and problem with wireless connect.

Known issues:

    *

      339891 - wireless rt2860 not connecting to some WPA (Enterprise does not work out-of-box). Working patch is issued at link. 


So my question is what "special-purpose buttons" are being talked about, and how big of a problem is the wireless connection.

I have never used Ubuntu on a laptop before, only desktops and I want to know about anything I may run into. 

Thanks a lot, and if there is something else I didn't mention that I should know, please let me know.

---

### Post by fishyf on 2009-05-25
I installed it on a 901 and the wireless didn't work out of the box, but connected to the wired network, downloaded updates and it worked fine. The wireless encryption was WEP.


I also installed it on an EEE 1000 and the wireless didn't connect to a WPA network. Changed the router configuration from "WPA & WPA personal 2" to WPA tkip (not sure, going from memory) and it worked fine.

In other words to get WPA to work, I had to change the WPA settings in the router.

---

### Post by moebob24 on 2009-05-25
> **fishyf said:**
> I installed it on a 901 and the wireless didn't work out of the box, but connected to the wired network, downloaded updates and it worked fine. The wireless encryption was WEP.


I also installed it on an EEE 1000 and the wireless didn't connect to a WPA network. Changed the router configuration from "WPA & WPA personal 2" to WPA tkip (not sure, going from memory) and it worked fine.

In other words to get WPA to work, I had to change the WPA settings in the router.

Cool, thanks for the heads up. On the bright side, this OS is only going to get better. I mean it is pretty much perfect now, it is just these small things that will be fixed soon.

I'm going to write it to a USB and boot from that to give it a try.

---

### Post by rehilliard on 2009-05-25
i was running it a week or two ago, and there was a problem with the desktop switcher (to switch to *standard* desktop and back). It wouldn't completely restore the task panel at the top of the netbook  desktop.

I found a new version here: [https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519/comments/59](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519/comments/59)

Fixed it.

---

### Post by moebob24 on 2009-05-25
> **rehilliard said:**
> i was running it a week or two ago, and there was a problem with the desktop switcher (to switch to *standard* desktop and back). It wouldn't completely restore the task panel at the top of the netbook  desktop.

I found a new version here: [https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519/comments/59](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519/comments/59)

Fixed it.


Wow! I have that exact same problem on my desktop version of 9.04. I can't figure it out. At first I thought it was Compiz messing up but it did it in Metacity too. Oh well, thanks for the heads up.

---

