---
title: "modprobe is looking at the wrong version!"
date: 2008-08-06
forum: Hardware
---

### Post by water_foul on 2008-08-06
This all started when my touchpad stopped working one morning. It was like any other morning till i hit the ubuntu login screen and my touchpad did not move the mouse. So i logged in thinking that would fix it and still no dice. I then had to leave for work and left my laptop in my mother's capable hands. When i come home she has figured out that usb mice would work but only if you plug them in pre-boot. So i booted up with my backup usb mouse and found that my wireless card no longer worked! ](*,) I finnally figured out that the module (in this case bcm43xx) wasn't loaded so i thought "It worked before so lets try it" and ran "sudo modprobe bcm43xx" and got 

FATAL: Module bcm43xx not found.

So with a confused look on my face i ran uname -r to get my kernel version (2.6.22-14-generic) started digging in /lib/modules/2.6.22-14-generic. Low and behold it was at

/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

](*,)
I then went digging in the man page for modprobe and found --set-version and ran "sudo modprobe --set-version 2.6.22-14-generic bcm43xx" and was FINNALLY able to get my wireless back. That is what led me here and I would like to know two things preferably in order.

1. How can i set a temporary fix so that modprobe looks at 2.6.22-14-generic modules
2. What is actually happening so that we can fix it in modprobe so that others done have to go through a similar situation

If you want more info please just ask

P.S. Before all this happened i was trying to get the nvidia restricted drivers working so that may have caused the problem, I don't think it did but its the only thing i can think of.
P.P.S. My touchpad does work in my dual-booted XP

---

### Post by water_foul on 2008-08-06
OK, i now have some good new and some bad news. First, the good news, my computer is now back to normal....... Next, the bad news, now i don't think we can find out what happened and fix it...... The computer died cause it ran out of battery (hard shutdown, not soft shutdown) and when it came back up everything was back to normal

:lolflag:](*,):lolflag:](*,):lolflag:](*,):lolflag:](*,)

---

### Post by mrsteveman1 on 2008-08-06
Did this just appear out of nowhere? no changes, updates or custom installed kernels?

I can't remember exactly but isn't this sort of what depmod is for?

---

### Post by water_foul on 2008-08-06
depmod didn't work when the problem was happening and like i said, the only thing i did was try to get the nvidia thing working

---

