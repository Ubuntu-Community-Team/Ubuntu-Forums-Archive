---
title: "Graphic Geforce 7300le"
date: 2015-12-06
forum: Hardware
---

### Post by angel mike on 2015-12-06
I want to replace my old graphics card Geforce 7300le with a more upto date one. Just for general use not gaming. I have a spare slot for a PCIe-16 in my Gateway PC GM5660b.

---

### Post by Vladlenin5000 on 2015-12-06
OK, and your question is...?

---

### Post by angel mike on 2015-12-07
A low power and reasonable price which is Ubuntu friendly. My existing card still give problems some time on booting up with lines across the screen.

---

### Post by mörgæs on 2015-12-07
If you can accept X/Lubuntu in stead of Ubuntu the 7300 will be fine. 

The drivers have improved a lot lately so I recommend 15.10 in which you choose additional/closed-source drivers during the install.

---

### Post by angel mike on 2015-12-07
Thanks morgaes for that useful response - I will give it a try. Mike

---

### Post by angel mike on 2015-12-07
Ps - did you mean LXLE version ?

---

### Post by mörgæs on 2015-12-07
No, go for the latest release, which is a standard Lubuntu 15.10.
LXLE is built on 14.04 and has older drivers.

---

### Post by Yellow Pasque on 2015-12-07
> My existing card still give problems some time on booting up with lines across the screen.
plymouth (the module that produces the startup boot splash screen with the Ubunto logo) is known to have issues with binary drivers. You can try disabling the splash screen: [https://wiki.ubuntu.com/Plymouth#Toggling_to_Traditional_Text-based_Boot](https://wiki.ubuntu.com/Plymouth#Toggling_to_Traditional_Text-based_Boot)
That page also contains other tips for troubleshooting issues with the splash screen.

> A low power and reasonable price which is Ubuntu friendly. 

A RadeonHD 6450 seems ideal for that. It should work out of the box with open source drivers on modern versions of Ubuntu (>= 14.04) and it's got more than enough 3D power to run Unity smoothly. As a bonus, you get good video decode acceleration with mesa-vdpau-drivers package.
Really though, I wouldn't buy a new card if the boot splash screen was the only thing giving me problems (or maybe I've misread your post and the problem is more serious).

---

### Post by Yellow Pasque on 2015-12-07
> **Vladlenin5000 said:**
> OK, and your question is...?

"Sorry, but your response was not in the form of a question."
Alex Trebek, is that you?!

---

### Post by angel mike on 2015-12-11
Thanks for your responses Temujin/Morgaes - I will try both without a card change although I was looking forward to the challenge of looking inside my pc ! Mike

---

