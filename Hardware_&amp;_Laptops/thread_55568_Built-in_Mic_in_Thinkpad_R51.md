---
title: "Built-in Mic in Thinkpad R51"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by NMUrugbysteve on 2005-08-09
Does anyone know how to enable the built-in mike in the thinkpad R51? Thinkwiki doesn't seem to have any info on this (hell, it doesn't even say the thing has one!) Also, I'm using ALSA as my sound server.

If I can get this working, I'm one step closer to dropping windows.

I need this because a good friend is studying abroad in South Africa and we want to use skype to keep in touch.

---

### Post by NMUrugbysteve on 2005-08-11
Wow, maybe I was a little too specific in my title. Has anyone had any success with ANY built in microphones in their laptops?

---

### Post by s_p_a_r_k_y on 2005-08-11
I have the same problem in my laptop. It worked with Suse (which the laptop was bundled with). I can hear the microphone if I tap it, but for some reason the  no applications seem to be able to use it. I have to plug in a mic to record anything. I too would love a solution to this

---

### Post by NMUrugbysteve on 2005-08-12
[QUOTE=s_p_a_r_k_y]I have the same problem in my laptop. It worked with Suse (which the laptop was bundled with). I can hear the microphone if I tap it, but for some reason the  no applications seem to be able to use it. I have to plug in a mic to record anything. I too would love a solution to this[/QUOTE]
 Good to know someone else is having this prob. You can at least be happy that you're farther along with this than I am, tapping my mic does nothing at all.

---

### Post by jeremytaylor on 2005-08-14
hi there. I got the mic working on my asus laptop.

Firstly I followed the howto at [http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753) this sets up the system to work properly with alsa.

next, this is a little unscientific..., fiddle with the mixer. If you type alsamixer at at prompt it brings up an ugly mixer that has much more functionality that the gnome one. make sure your capture devices are both set to the built in mic and aren't muted. to do this move to the right section and use the up/down keys to set them to the right device. It worked for me but I'm not really sure why.

hope this is some help
Jeremy

---

### Post by NMUrugbysteve on 2005-08-14
[QUOTE=jeremytaylor]hi there. I got the mic working on my asus laptop.

Firstly I followed the howto at [http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753) this sets up the system to work properly with alsa.

next, this is a little unscientific..., fiddle with the mixer. If you type alsamixer at at prompt it brings up an ugly mixer that has much more functionality that the gnome one. make sure your capture devices are both set to the built in mic and aren't muted. to do this move to the right section and use the up/down keys to set them to the right device. It worked for me but I'm not really sure why.

hope this is some help
Jeremy[/QUOTE]
 Thanks so much man! My mic is working fine and dandy. I'd seen that post before but I used the fix from the other HOWTO about duplex sound with ALSA.

---

