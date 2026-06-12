---
title: "How to force cpu fan to run 100% all the time on laptop?"
date: 2012-04-27
forum: Hardware
---

### Post by Goddchen on 2012-04-27
Hey everyone,
i have an Alienware m9700 Laptop.

I have just installed Ubuntu 12.04 64bit and now i have the problem that the laptop overheats pretty quick (reaching 95°C). It is not a cooling paste issue or dust, i double checked everything and on windows the laptop runs just fine for hours, even a cpu stress test doesn't make it overheat.

I don't really want to 100% fix this, i just need it to work. So i thought about forcing the fan to run 100% speed all the time. But i'm unable to figure out how to do this.

I have done much research regarding fancontrol, pwmconfig, lm-sensors etc but it seems like the fan simply cannot be controlled/recognized by pwmconfig...

So i reach out to you guys, is there any way that i can force the fan to run at 100% speed all the time?

Goddchen

---

### Post by Strojar on 2012-05-01
i would try with another distro, boot it live from usb and see if it heats anyway.
maybe it's a bug from the new distro...
you could limit the cpu, ith took of about 10 degrees of my compaq, lifted it about 1 cm from the surface and it took away another few degrees, got rid of some dust witch took another 10 degrees.

but if you checked for dust maybe it's the distro...

you could also run the laptop plugged in ac without the batery, that should take of smoe heat also...

don't know about fan hitting 100% all the time.

hope something helped :)

---

### Post by Goddchen on 2012-05-01
thanks for the hints, but none of them is efficient enought to let the temperature settle under the 95°C. I just installed Ubuntu 32bit (used to use x64) but that didn't make any difference either...

Is there really no way to disable all fancy automatic fan controls and simply set it to 100%?

---

### Post by ahallubuntu on 2012-05-01
Have you installed the correct graphics driver?  Maybe the GPU is overheating, not the CPU...

Just cranking the fan up may not be a great long-term solution.

---

### Post by Goddchen on 2012-05-01
i'm using the proprietary nvidia drivers that ubuntu offered after the first boot after installation.

---

### Post by Goddchen on 2012-05-01
just tried a fresh install of debian x64, same result...

---

### Post by Goddchen on 2012-05-02
just to inform you, official Alienware Support response is: It is not compatible with any Linux distro.

But hey, i just wanna force the fan to run at 100%, not fully enable automatic fan control or anything...

Does really noone know how to make a fan run 100% all the time?

---

### Post by Strojar on 2012-05-03
maybe this will help?
[http://askubuntu.com/questions/36401/modify-manually-pwm-of-my-fan-fan-speed](http://askubuntu.com/questions/36401/modify-manually-pwm-of-my-fan-fan-speed)

---

### Post by Goddchen on 2012-05-04
unfortunately not :( I don't have the "/device/" folder under that directory :( Any ideas?

---

### Post by Strojar on 2012-05-04
unfortunatley out of ideas :(
maybe another option could be to buy a cooling platform, or build one, i got two 12V fans for my project, they blow pretty good, yust need to make a platform for the laptop.

---

### Post by marcelopernambuco on 2012-09-24
Hello,

I actually have a faulty sensor on my laptop and would like to know if it is possible to override sensor verification for determining fan speed, as in my laptop it sometimes reports 0C cpu temp (of course is wrong temp sensor report) and the fan simply turns off.

[IMG]http://imageshack.us/a/img41/8136/screenshotfrom201209241.png[/IMG]


Is there some way of makinf my cpu fan always on, always, independently from the temp sensor. Is that possible?

Thanks a lot!
Marcelo

---

### Post by marcelopernambuco on 2012-10-01
> **marcelopernambuco said:**
> 
Is there some way of makinf my cpu fan always on, always, independently from the temp sensor. Is that possible?

Thanks a lot!

I still cannot believe this is not possible. Come on, please help!!!!

Txs

---

