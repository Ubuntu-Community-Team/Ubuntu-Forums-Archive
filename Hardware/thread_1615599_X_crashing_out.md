---
title: "X crashing out"
date: 2010-11-07
forum: Hardware
---

### Post by pratikk on 2010-11-07
Hi, I'm posting a new thread because this problem was reported in [http://ubuntuforums.org/showthread.php?t=1413061](http://ubuntuforums.org/showthread.php?t=1413061) while Lucid was in beta. This is now closed.  

X exits arbitrarily to low graphics mode -- box on a black screen with radio buttons for restarting X, changing settings, etc. But on clicking them, the machine logs me out and exits to a terminal login prompt. No option but to restart and lose work. The error reported is the same as in the closed beta thread:

"Fatal Server Error:
Failed to submit batchbuffer
Input/output error."

Oddly, this has always happened while using Firefox, never while using graphics-intensive stuff like Gimp or Scribus. However, the active tab in FF never had Flash elements. 

Another oddity: My system does not have a xorg.conf, only /etc/X11/xorg.conf.failsafe, a file of only about 10 lines. Is this normal?

Hardware: Intel Mobile 915GM/GMS/910GML Express Graphics Controller on Compaq Presario V2000.

Grateful for ideas on how to resolve this. 

Pratik

---

