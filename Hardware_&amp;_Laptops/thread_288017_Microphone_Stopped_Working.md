---
title: "Microphone Stopped Working"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by Chiaro on 2006-10-29
I just upgraded to Ubuntu 6.10. I tried recording my voice on the voice recorder. Doesn't work. I tried using the Skype test call. Doesn't work.

It was working on 6.10 LTS...why did it stop?

---

### Post by zgornel on 2006-10-29
Get aumix (sudo apt-get install aumix), run it and got to the IGain slider. Put it at about 70%, save (S) and exit (Q). It should work. I do not know why this problem appeared.

---

### Post by Chiaro on 2006-10-29
I installed aumix. Ran it from the terminal, and went to the slider. It was at full. I moved it to 70%, saved and exited.

Still no recording/Skyping.

---

### Post by zgornel on 2006-10-30
Mine works. Now it's without +20db gain and mic capture and set on mute from gnome audio properties panel. Strange...

---

### Post by jis on 2007-10-29
Mine stopped working after couple of days after installing Gutsy. It had same problem in Feisty, though. Microphone works in Windows, I have to use mic boost, though.

Here's some data:

# Soundcards recognised by ALSA
# -----------------------------
#  
# 0 [ICH6           ]: ICH4 - Intel ICH6
#                      Intel ICH6 with ALC655 at irq 17
#  
#  
# PCI Soundcards installed in the system
# --------------------------------------
#  
# 00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
#  

Manual of the laptop says, it supports Intel® High-Definition sound and is Sound Blaster Pro and MS Sound compatible. My bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/137992](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/137992)

---

