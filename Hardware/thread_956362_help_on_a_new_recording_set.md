---
title: "help on a new recording set"
date: 2008-10-23
forum: Hardware
---

### Post by luponemannaro on 2008-10-23
Hi 
Marco's writing
I'm a new user of Ubuntu studio (new linux user too).
maybe someone can help me with some malfunction:
1)Ubunto recognize wi-fi (Ateros comunications AR242x 802.11 abg wireless)on my notebook but it doesn't work I think it need  linux drivers )
2)I have a dynamode 1394A express card But I didn't remind to plug it when I installed Ubuntu there is a way to install it now?

3)I have a focusrite saffire firewire, it need a particular driver to be seen ?

thanks for your help
                       Marco

---

### Post by pointfive on 2008-10-26
I'm still stuggling with getting my Saffire LE to work with Ubuntu (doesn't work well on Vista either; XP is fine, however). Once I get it working, I'll share my experiences here. In the meantime, I found this thread which explains how to get it working: [http://ubuntuforums.org/showthread.php?t=795058](http://ubuntuforums.org/showthread.php?t=795058) . Look for the post by **jenny_thinkpad_t61p**

My understanding of what needs to be done:

1) Uninstall freebob drivers and jackd.
2) Download and compile ffado firewire drivers: [http://www.ffado.org/?q=node/613](http://www.ffado.org/?q=node/613)
3) Compile jackd from source (compiling it after ffado is working will allow you to select the Saffire as your "soundcard" in jack)

Hope this helps a little. Let me know what you experience, I'll do the same.

---

