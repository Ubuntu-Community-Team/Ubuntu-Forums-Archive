---
title: "Cannot activate video driver"
date: 2011-12-14
forum: Hardware
---

### Post by LWard on 2011-12-14
Thus far this is my second, help me I'm new post.

I recently installed Ubuntu 11.10 on my Toshiba Satellite L500D laptop. When I go into the additional driver menu, it comes up that there is a video driver for me to activate. 

I have two options:
1) ATI/AMD proprietary FGLRX graphics driver (post-release updates)
2) ATI/AMD proprietary FGLRX graphic driver.
This is what is says about the drivers:
"3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards."

Now when I try to activate either of these drivers I get an error stating "Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

What is that saying to me and is it really neccessary to activate either of these drivers?

Thank you in advance.

---

### Post by mikewhatever on 2011-12-14
There is no secret sub-text in there. The driver installation is advised, but not required or necessary.

/var/log/jockey.log is the driver installation log that may provide some useful info.

---

### Post by LWard on 2011-12-14
How do I access the /var/log/jockey.log to see what it has to say?

Thank you for confirming my thinking of not needing the driver install.

---

### Post by mikewhatever on 2011-12-14
'less /var/log/jockey.log' should do, and if you want something prettier, 'gedit /var/log/jockey.log'.

You may or may not need to install the ATI driver, I can't decide that for you. :~)

---

### Post by LWard on 2011-12-14
I'll have to look at that log tomorrow morning after work and will post what is says. Thanks for the help mikewhatever.

---

### Post by BC59 on 2011-12-14
If the installation through Jockey is not working you can install the driver through Synaptic.

First install the app Synaptic through Ubuntu Software Center.

Then open Synaptic and search (on the right Search with the lens) for the word FGLRX. Then install the driver according to your computer architecture. Install the packages fglrx and fglrx-amdcccle for a 64bit computer or fglrx and fglrx-amdcccle:i386 for a 32bit computer. Then close and reboot.

---

### Post by LWard on 2011-12-14
Thanks for that info BC59. I'll have to give that a whirl.

---

### Post by coffeecat on 2011-12-15
@LWard, if the default open source driver is working well enough for you, I suggest you consider not installing the fglrx driver. Note what Jockey is telling you:

> This driver is required to fully utilise the 3D potential of **some** ATI graphics cards, as well as provide 2D acceleration of newer cards.

Emphasis (mine) on "some". The fglrx driver may or may not perform better for you with your particular GPU. Indeed, some people's experience of the fglrx driver, depending on GPU, has been less than happy.

---

### Post by LWard on 2011-12-15
Very good point coffeecat. As it is at this moment I don't need to fully utilise the 3D potential. I'll consider this matter closed and will revisit it if and when the time arrised that is may be needed.

---

