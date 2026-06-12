---
title: "Black screen after reboot!"
date: 2010-10-10
forum: Hardware
---

### Post by fallenshadow on 2010-10-10
I installed the Nvidia proprietary driver in Ubuntu 10.10 64bit and after rebooting I get a black screen.

Any ideas as to what I can try to fix this? I am posting from the Live-CD at the moment.

---

### Post by fallenshadow on 2010-10-10
Ok I deleted my xorg.conf by using the live cd. Now I got back into my install.

However even though my Nvidia driver is installed I don't have any 3D functionality. :(

Is there a way to make it work?

---

### Post by fallenshadow on 2010-10-11
Im pretty sure its actually a hardware issue... although Im not sure is it the graphics card or something else.

I will try and figure out whats wrong...

---

### Post by Torrino on 2010-10-11
[FONT=Century Gothic]You could try re-installing Ubuntu and try to find some other drivers that are compatible with it.[/FONT]

---

### Post by fallenshadow on 2010-10-14
Can't seem to find anything wrong with the card. The fan works... the GPU bios outputs to screen at bootup and I don't have any missing pixels or anything.

Does anyone have a Nvidia 9800GT working on Ubuntu 10.10?

---

### Post by fallenshadow on 2010-10-23
I think my problem relates to this bug:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596)

Seems like I will just have to wait and see does it get sorted. :(

---

### Post by fallenshadow on 2011-04-29
Ive installed 11.04 but I still got the same issue. However I think I have found the problem.

I did the Ubuntu checking system but it has not detected any port such as:

	> video-vga	
	video-dvi		
	video-displayport	
	video-hdmi	
	video-svideo		
	video-rca	

Any ideas as to what to do? :confused:

---

