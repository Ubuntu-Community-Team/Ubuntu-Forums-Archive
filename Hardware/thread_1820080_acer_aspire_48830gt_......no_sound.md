---
title: "acer aspire 48830gt ......no sound"
date: 2011-08-07
forum: Hardware
---

### Post by naifnoon on 2011-08-07
good day everyone

i'm new to linux and i installed ubuntu 11.04 to my laptop Acer Aspire 4830TG

it is great except the sound.

i have no sound at all.

any help plz.


thanks

---

### Post by SalHelder on 2011-08-07
Type in the terminal:

gnome-volume-control

On the window that opens tweak options accordingly.

---

### Post by naifnoon on 2011-08-07
i tried it before

nothing

---

### Post by SalHelder on 2011-08-07
That's strange.

Try typing in the terminal:
gstreamer-properties

And change all options to ALSA, reboot and see if it solves it.

---

### Post by fdrake on 2011-08-07
> **naifnoon said:**
> i tried it before nothing
by "nothing" it means that a windows pops up and u can change the volume but it does not work? or it does not show the pop up window, but instead an error msg?

---

### Post by naifnoon on 2011-08-07
> **SalHelder said:**
> That's strange.

Try typing in the terminal:
gstreamer-properties

And change all options to ALSA, reboot and see if it solves it.

i did it

i reboot 2 times no sound

---

### Post by naifnoon on 2011-08-07
> **fdrake said:**
> by "nothing" it means that a windows pops up and u can change the volume but it does not work? or it does not show the pop up window, but instead an error msg?

the window pop up and i can change

no sound

---

### Post by SalHelder on 2011-08-07
Are you sure you're computer model is Aspire 48830gt? I don't seem to find it anywhere to see the specs of it.

---

### Post by naifnoon on 2011-08-07
> **SalHelder said:**
> Are you sure you're computer model is Aspire 48830gt? I don't seem to find it anywhere to see the specs of it.

sorry it is one 8:

Acer Aspire 4830TG Timelinex

---

### Post by fdrake on 2011-08-07
output of :
```
lspci -vvv | nl | grep Audio
```

---

### Post by naifnoon on 2011-08-07
> **fdrake said:**
> output of :
```
lspci -vvv | nl | grep Audio
```

[COLOR=Red]**52    00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)**[/COLOR]

---

### Post by fdrake on 2011-08-07
see if this works..

```

ops!
sorry i just noticed the difference in the model u r using

```
reboot and test. 

source : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/783582](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/783582)

---

### Post by fdrake on 2011-08-07
```

wget -O run.py http://www.alsa-project.org/hda-analyzer.py
sudo python run.py

```
select enable EAPD in Node[0x1b]

reboot and test. 

source : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/783582](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/783582)

---

### Post by naifnoon on 2011-08-07
> **fdrake said:**
> ```

wget -O run.py http://www.alsa-project.org/hda-analyzer.py
sudo python run.py

```select enable EAPD in Node[0x1b]

reboot and test. 

source : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/783582](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/783582)


thank u very very very much man

it  works finally

---

### Post by fdrake on 2011-08-07
> **naifnoon said:**
> thank u very very very much man

it  works finally
I am happy for you.
make sure to mark this thread as "SOLVED" so someone else with your problem will find it.

---

### Post by ahref on 2011-08-07
Hello,

Been following this thread enabling EAPD on the node solves the problem but only for one boot cylcle, on reboot I need to renable it to get sound back.

Is there a way to enable this on startup some sort of script or something. Perhaps the alsa conf file in modprobe could do it.

Anyone know of a way?

Thanks

---

### Post by fdrake on 2011-08-07
> **ahref said:**
> Hello,

Been following this thread enabling EAPD on the node solves the problem but only for one boot cylcle, on reboot I need to renable it to get sound back.

Is there a way to enable this on startup some sort of script or something. Perhaps the alsa conf file in modprobe could do it.

Anyone know of a way?

Thanks

what release?
output
```
lsb_release -a
```

by the way I suggest you to open a new thread with your info. it will get you quicker to a solution.

---

### Post by ahref on 2011-08-07
Exactly the same as the guy posting, I didnt think i should make a new thread when this one has a solution and had active posts.

so to reiterate:

Ubuntu Natty, Acer Aspire Timeline X(4830G), Following the steps in this thread enables sound for ONE boot. Is there a more permanent solution :D?

---

### Post by fdrake on 2011-08-07
> **ahref said:**
> Exactly the same as the guy posting, I didnt think i should make a new thread when this one has a solution and had active posts.

so to reiterate:

Ubuntu Natty, Acer Aspire Timeline X(4830G), Following the steps in this thread enables sound for ONE boot. Is there a more permanent solution :D?

well the thing is that this may depend on the release you are using, since the links i checked did not describe this problem.
beside if you are looking for help ppl won't search for a thread tagged as "solved" unless the "naifnoon" user changes it.

provide a link to your new thread in here so ppl will know..

---

### Post by lmm5247 on 2012-06-25
> **SalHelder said:**
> That's strange.

Try typing in the terminal:
gstreamer-properties

And change all options to ALSA, reboot and see if it solves it.

had the "no sound" problem, running 12.04 64-bit on a 4830t, kernel 3.2.0-23. used the above command, changed plugin to ALSA, rebooted, and it works! :D speakers and headphones work, no mic yet though...

---

