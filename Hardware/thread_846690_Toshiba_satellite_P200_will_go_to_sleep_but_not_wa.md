---
title: "Toshiba satellite P200 will go to sleep but not wake up."
date: 2008-07-01
forum: Hardware
---

### Post by m9365428 on 2008-07-01
Hi I'm running Ubuntu 8.04 on a Toshiba Satellite P200 and have only one problem.
Hibernate Works fine but when I put the computer to sleep it will not wake up.
Well actually the computer's indicator lights turn back to the normal blue color instead of the orange sleep mode collor but the monitor never turns back on. 
I'm fairly good at code and can mess around with my BIOS so if you need any other information just tell me where to look and what codes to use to find the info.

Thanks for the help this may be a small thing but I lived in sleep mode with windows (lowercase on perpose as a dis. (if i could find a smiley throwing the bird i would us it))
M

---

### Post by phidia on 2008-07-01
Check the settings carefully in your System>Preferences>Power Management section from the top panel menu. Sometimes config files need to be edited to get suspend/sleep working right.
It helps to know your hardware specs and what drivers you have set up for instance ndiswrapper and 3D video drivers can cause problems with suspend.
You might want to look at [this]("http://www.winterdom.com/weblog/2007/10/23/FixingSleepInUbuntu710.aspx") too since /etc/default/acpi-support is an important file for getting what you want working.

---

### Post by m9365428 on 2008-07-02
Thanks for the reply phidia
I just noticed that I was not using the driver listed under hardware drivers so I installed it. That seems to have fixed the problem but I will get back to report on my status in a few days.

Thanks alot,
M

---

### Post by m9365428 on 2008-07-07
Just a conformation that the driver fixed my problems. sorry to use web space on this matter.

end of post
M

---

### Post by matt.cohenprice on 2009-01-04
M,

I am having a similar problem with my Satellite M55, but unsure where to find that driver information that solved your problem. 

What exactly did you change?

Thanks!

---

### Post by m9365428 on 2009-01-06
> **matt.cohenprice said:**
> M,

I am having a similar problem with my Satellite M55, but unsure where to find that driver information that solved your problem. 

What exactly did you change?

Thanks!

I installed the restricted drivers for my graphics card and updated everything else.
Just stay the course and someone will release a driver update for your card. Just be sure to use the restricted driver and not the default ones. 
The restricted driver allows the system to use the advanced power controls and 3d rendering engines on the card that otherwise can't be used.

M

---

