---
title: "&quot;2 Graphics Hardware Configuration&quot;"
date: 2010-10-12
forum: Hardware
---

### Post by maizuddin35 on 2010-10-12
Hellp guys.
I hope this thread in the right section.

Just want to ask...

Is there a way to configure 2 graphics harware in one ubuntu system?

I hope you guys will understand, in other ways...in my situation.

I have an external HDD , in it ,contain my ubuntu 10.04. When I want to use my ubuntu , instead windows somewhere else , I just plug in my external HDD in to that computer, but the thing is, the graphic configuration, is configured for my home desktop pc only. 

Is there a way to make it the way I said?

thank you in advanced

---

### Post by maizuddin35 on 2010-10-13
now, what I have found out is, 
When that particular computer have internet connection, I just can download and install the hardware drivers . But when I went back to my home pc, i need to change back by downloading the hardware drivers back .

---

### Post by efflandt on 2010-10-13
One issue may be the hardware accelerators.  For example if I "activate" nvidia drivers for a PC with nvidia and them boot my USB hard drive on another PC with legacy ATI video, it will complain, but still boot and mostly work.  But installing/activating nvidia drivers apparently changes something to point to its hardware glx module, so the mesa glx for default drivers does not work, which can make 3D slower for the default ATI driver than if the nvidia specific drivers are removed.

So it sort of depends what you are doing with the computer, whether you can get by with the default video drivers (which cooperate with each other) for everything, or if you need proprietary drivers for something.

It would be nice if there was some way to switch or disable proprietary video drivers on the fly, like with a kernel boot parameter or something else in grub.  But I do not think it is that simple.

---

### Post by maizuddin35 on 2010-10-14
Yes. I agree with you. just, now, I have no problem dealing with it when I connected with the 'other' computer , just the problem may occur , sometimes.

---

