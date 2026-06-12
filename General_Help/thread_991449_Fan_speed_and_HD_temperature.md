---
title: "Fan speed and HD temperature"
date: 2008-11-23
forum: General Help
---

### Post by ozguitarplayer on 2008-11-23
Hi,

I've recently installed Ubuntu on a second hard drive, with windows on the original drive. Since doing this I can hear the CPU fan increase it's speed quite a bit (it used to be quite, now noisy) 

Is this a result of having two operating systems? and can it cause the hard drives to run hotter.
PS I have only just added software to monitor temp fan speed etc so I don't have any reference to what was before the second HD was installed.

Now fan runs around 4500rpm, the ubuntu HD 42 degrees and the windows HD about 50 degrees

any comment are appreciated

---

### Post by Yellow Pasque on 2008-11-23
The fan speed shouldn't be affected by HD temp. The CPU fan is either going to be controlled by the BIOS or by fan-control software. 

Some ?'s:
- Do you have any sort of fan control options in your BIOS? If so, are they enabled?
- Is the fan now running faster in Windows as well? If so, can you slow it down with Speedfan? (google for it; it's a great freeware app)

To me, it sounds like your fan is controlled by some software in Windows, and when you use Linux, nothing is controlling the fan and it runs at full speed (you might be able to install lm-sensors and use pwmconfig to control it if that's the case)

---

### Post by frankleeee on 2008-11-23
I am using GKrellM from synaptic to auto or maual control the fans in my laptop per cpu temp, it has a fairly straight forward gui to adjust things and a modern looking display for you desktop. I put it in the auto start part of sessions so that it runs automatically.

---

### Post by ozguitarplayer on 2008-11-24
thanks for the response,
I don't know about fan control in the bios I've not looked before, however I will.
The higher fan speed has only started since I added the 2nd HD and installed Ubuntu, and I'll follow through on the other suggestions ....

---

### Post by swoody on 2008-11-24
> **frankleeee said:**
> I am using GKrellM from synaptic to auto or maual control the fans in my laptop per cpu temp, it has a fairly straight forward gui to adjust things and a modern looking display for you desktop. I put it in the auto start part of sessions so that it runs automatically.

How do you use gkrellm to control the fans? I downloaded it, but it looks like just a display, and there's no options for fans?

---

### Post by frankleeee on 2008-11-24
> **woody86 said:**
> How do you use gkrellm to control the fans? I downloaded it, but it looks like just a display, and there's no options for fans?

If you right click on the desktop display it opens a gui which has controls, you also probably have to enable lm sensors or whatever sensors are intrinsic to your computer. once it is set up and reading the sensors you can click on the fan part and make the fans manual and turn them on and off. I have it set to run automatically because in the control gui you can change the stop and start times for the fans per temp. It is a little confusing at first but the gui is the main control part.

---

### Post by tulcak on 2010-07-09
> **Temüjin said:**
> The fan speed shouldn't be affected by HD temp. The CPU fan is either going to be controlled by the BIOS or by fan-control software. 

Some ?'s:
- Do you have any sort of fan control options in your BIOS? If so, are they enabled?
- Is the fan now running faster in Windows as well? If so, can you slow it down with Speedfan? (google for it; it's a great freeware app)

To me, it sounds like your fan is controlled by some software in Windows, and when you use Linux, nothing is controlling the fan and it runs at full speed (you might be able to install lm-sensors and use pwmconfig to control it if that's the case)
lm-sensors and pwmconfig are absolutely WORTHLESS.

---

