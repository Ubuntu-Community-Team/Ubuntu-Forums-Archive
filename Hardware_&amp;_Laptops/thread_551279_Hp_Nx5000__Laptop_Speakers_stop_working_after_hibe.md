---
title: "Hp Nx5000  Laptop Speakers stop working after hibernate"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by jords on 2007-09-15
Hi,

I've got a weird problem with my HP Nx5000 laptop and Kubuntu 7.04. The laptop speakers work great after boot, but If I suspend or hibernate the laptop the built-in speakers stop working. The Mic port still works after hibernate.

None of my mixer settings seem to change while hibernating....

2 strange things:
1) The laptop has a volume control and mute buttion for the speakers. These don't affect the Mic port. The buttions still make a volume bar come up on the screen when pushed even when the speakers are'nt working.

2) There is a LED light under the mute buttion on the laptop. Normally this never comes on in linux, but it does in the other os when the speakers are muted. I don't paticularly care about having the light come on, but I've noticed that while hibernating, the light comes on, seeming to suggest that the speakers have been muted somehow. The light goes off again once the computer has finished hibernating.

The hotkeys for turning off and on wireless etc still work after hibernation.

Aside from this and the light to show if wireless is on not working in linux, I've been really impressed at how well ubuntu supports all my hardware :)

Thanks, Jordan

EDIT: This was resolved by installing the restricted driver for the software modem in my laptop. It must have code to reactivate the speakers after a hibernate.

---

### Post by jords on 2007-09-15
I tried using uswsusp to hibernate instead, but still no sound after hibernate.

---

### Post by jords on 2007-09-18
Any Ideas?

---

### Post by zydrome on 2008-03-27
Hi,
Well I've got Ubuntu 7.10 on my hp Pavilion dv6500. The sound works fine after resuming from suspend, but I was willing to know how Ubuntu manages to turn off the speakers on hibernate so I would be able to do the same thing when turning off (to prevent the speakers being damaged from the power off).
So anybody here know the script or whatsoever that does this?

Thanks

---

