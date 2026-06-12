---
title: "Laptop problems - sound and powermanagment"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by cimnik on 2006-11-10
I have just installed Ubuntu 6.10 on my new HP Pavilion dv6000 (i think its the z, it has the AMD Turion processor). Anyways, when I popped in the live CD, I was amazed to see that it seemed to properly pick up all the hardware in my laptop (except video card... not supported yet, too new from what I heard?). Sound worked, power management worked. I didn't try the wireless but it shows up.

So, excitedly, I install it on my hard drive. I boot up, only to discover that neither sound nor power management worked anymore. Sound doesn't work and there is no more battery life indicator / dim screen on battery etc. However I do still have a (dead) volume control.

How can I re-enable these features. Besides lack of support for the video card it works like a dream. ](*,)

Simon

---

### Post by cimnik on 2006-11-10
Right. This is just me being stupid. I had to boot with acpi=off, which would mean that there would be no power management, sound, etc... grrr. Are there any workarounds to this?

Simon

---

### Post by hyby on 2006-11-10
Howdy,

With sound issues, there many solutions you can try. 

- go into ALSAMIXER and make sure everything is unmute especially PCM and MAASTER volumes
- make sure you have the external amplifier turned off. 
- Search the forum for solutions, many people have found different methods in getting sound to work, i.e. doing a sun-dance or using the laptop nude. 

Usually, the first two methods solve above 80 % of ubuntu users sound issues. I know this because i still dont have sound due to codec problems.

---

### Post by cimnik on 2006-11-10
nope. alsamixer levels are fine. From what I found on the internet, if acpi is off, then my sound card also won't work alongside my wireless.

---

