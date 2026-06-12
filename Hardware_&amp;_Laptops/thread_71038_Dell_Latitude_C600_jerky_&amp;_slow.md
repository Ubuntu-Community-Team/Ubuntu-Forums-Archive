---
title: "Dell Latitude C600 jerky &amp; slow"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by jonasforssell on 2005-10-02
Hi,
Just bought a Dell Latitude C600 and installed Ubuntu on it. In fact, it was the only distro which managed to install properly (tried Gentoo, Debian, Knoppix ..)
Only remaining problem for me now is that the mouse is a bit jerky and the CD-ROM is really slow. I cannot play music CD:s on it due to constant disruption. Not surprisingly, the DMA is not enabled, but turning it on makes the CD inaccessible. Any experience on how to solve this?
The jerky mouse is related to the system freezing every 5:th second or so. The freeze is only for a fraction of a second, but enough to be bothersome. Harddrive DMA is on and working properly so this is not the issue. I'd really appreciate support on this as well.
Thanks
/Jonas Forssell, Gothenburg, Sweden

---

### Post by HydroSan on 2005-10-02
I'm confirming this behaviour. I had Gentoo on it for the longest time and it was fine, as well as Ubuntu 5.04... but as soon as I tried 5.10, it started doing this. Studdering music, frozen keyboard, etc. I've tried different X settings, disabled unwanted services, enabled DRI for the video card and DMA on my hard disks... nothing. Keeps doing it.

I have no idea what the christ is wrong with it. Other flavours of Linux (even the newest ones like SuSE 10.0 RC1 and Fedora Core) run fine... but not Ubuntu 5.10. 5.04 runs great, however.

---

### Post by poofyhairguy on 2005-10-02
Honestly (this might not sound like something a mod would say) but its probably an Ubuntu problem. For laptops, I recommend SUSE. Have you tried it yet?

[http://www.novell.com/products/linuxprofessional/](http://www.novell.com/products/linuxprofessional/)

---

### Post by HydroSan on 2005-10-02
[QUOTE=poofyhairguy]Honestly (this might not sound like something a mod would say) but its probably an Ubuntu problem. For laptops, I recommend SUSE. Have you tried it yet?
[http://www.novell.com/products/linuxprofessional/](http://www.novell.com/products/linuxprofessional/)[/QUOTE]


I have, and it's alright. But I prefer Ubuntu. Are there any bug reports? Is there anything we can do to fix this?

---

### Post by jonasforssell on 2005-10-03
Thanks for the feedback!

Can this behaviour be reported as a bug somwhere?

/Jonas

---

### Post by HydroSan on 2005-10-03
[QUOTE=jonasforssell]Thanks for the feedback!
Can this behaviour be reported as a bug somwhere?
/Jonas[/QUOTE]


Well, first we have to figure out where this bug comes from. E.g: component, configuration, etc.

I've gone a-hacking with the modules, taking some out to see if that'd fix it. I disabled all non-essential services, took out the synaptics driver from xorg.conf (it has caused problems for me before), and killed many processes in top. None of those seem to fix with sticking error. So I don't know what to do.

---

### Post by jackmacokc on 2005-11-01
I have a C600 myself that I've been messing with..and I'm pretty sure I'm getting the same problems - and they are related to speedstep and the processor. I think the powernowd module is not working correctly.

---

### Post by slomrtwo on 2005-11-05
I have the same problem on 5.1 with my Inspiron 4000 that uses the same motherboard. :(

---

### Post by slomrtwo on 2005-11-05
I just tried the speedstep fix from this post and no more jerky problems for me.

[http://ubuntuforums.org/archive/index.php/t-75598.html](http://ubuntuforums.org/archive/index.php/t-75598.html)

---

### Post by Elling on 2005-11-08
I'm not sure about the C600, but the C610 has a general synaptic touch-pad issue with any OS -- including windows. Check it out in the online Dell support forums (you have to join).

Like I said, it may or may not apply to the C600, but the 610 has a known problem where the mouse cursor will drift on its own. It's usually worse when your palm(s) or any weight is on either side of the touch-pad. I’ve read that newer model touch-pads/keyboards fixed the issue (some people think it's the combination touch-pad/pointer stick behind the problem). One thing that helps on Windows is to download the latest synaptic drivers, disable the track-pointer and fiddle with other settings to minimize the drift, or jerkiness, of the cursor. It’s a pain, for sure -- I know; I've been there :( 

Good luck

---

