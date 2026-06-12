---
title: "'tap' issues on Dell Inspiron 2200"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by baza41 on 2005-07-29
OK, this is the situation. I've put Ubuntu 5.04 on the above laptop. All works fine, even the wireless. The only problem is with the 'tap' option on the touch pad. It -appears- to be emulating the middle button on a mouse, tappping on the 'close' X flips the window into the background rather than closing it for instance.

Any help to get this sorted would be most welcome.

B

---

### Post by nic2 on 2005-07-30
The following solved this problem on the touchpad of my HP Compaq nx6110:

In my xorg.conf file I set the following options:

Option     "TapButton1"     "1"
Option     "TapButton2"     "1"
Option     "TapButton3"     "1"

Follow this link to read the SynapticsTouchpadHowto located on the Ubuntu Wiki: [https://wiki.ubuntu.com/SynapticsTouchpadHowto?action=fullsearch&value=linkto%3A%22SynapticsTouchpadHowto%22&context=180](https://wiki.ubuntu.com/SynapticsTouchpadHowto?action=fullsearch&value=linkto%3A%22SynapticsTouchpadHowto%22&context=180)

Also view the README on the Synaptics Touchpad driver for some interesting options to use.

---

### Post by baza41 on 2005-07-30
Brill! Thanks that's fixed it.

Question: Why didn't install detect and configure the touchpad right, is this a bug?

B

---

### Post by nic2 on 2005-07-31
From what I read this is a hardware issue which relates to built-in features etc.  Apparently the default driver works fine on most touchpads and needs some configuration on others (the later being our classification).

---

### Post by mobo on 2005-08-08
Are you saying it detected the wireless automatically ? That would be fantastic. I have a 2200 model here as well and have been contemplating some linux version as well for it.

---

### Post by baza41 on 2005-08-09
No, but it was very easy to get nidswrapper to load the windows driver. I used the info on this forum and got it working in about 20 mins, and I'm no expert!

B

---

### Post by mobo on 2005-08-09
You wouldn't have any idea where you got the info do you ?

---

### Post by mobo on 2005-08-09
I have found this thread and im going to give it a go in a bit.

[http://www.ubuntuforums.org/showthread.php?t=50607&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=50607&highlight=ndiswrapper)


Now a question about the touchpad etc/X11 file that you had to edit. Did you have to login as root to edit that  I hope not because I dont know the root password..

---

### Post by raghav_p on 2005-08-09
why would you use ndiswrapper for ipw2200 when there is a perfectly good linux driver for it?

[HTML]http://ipw2200.sourceforge.net/[/HTML]

---

### Post by raghav_p on 2005-08-09
why would you use ndiswrapper for ipw2200 when there is a perfectly good linux driver for it?



[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

### Post by mobo on 2005-08-09
It isnt a pro wireless 2200. Its an inspiron 2200 laptop with a 3700 wireless card..

---

### Post by nic2 on 2005-08-10
[QUOTE=mobo]I have found this thread and im going to give it a go in a bit.

[http://www.ubuntuforums.org/showthread.php?t=50607&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=50607&highlight=ndiswrapper)


Now a question about the touchpad etc/X11 file that you had to edit. Did you have to login as root to edit that  I hope not because I dont know the root password..[/QUOTE]

You have to use the sudo command.

---

### Post by mobo on 2005-08-10
Got it, thanks..

---

