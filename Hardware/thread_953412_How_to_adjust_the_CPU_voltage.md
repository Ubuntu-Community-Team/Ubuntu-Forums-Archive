---
title: "How to adjust the CPU voltage?"
date: 2008-10-20
forum: Hardware
---

### Post by Markstar on 2008-10-20
Hi,

I have installed the *CPU Frequency Monitor* applet and it works nicely with my AMD X2 4850e. However, I would also like to adjust the voltage, but sadly I have no idea how to do this.

Thank you in advance!

Kind regards
  Markstar

---

### Post by Kevbert on 2008-10-20
When you first boot up you need to go into the bios and it will probably be an advanced setting. Adjust with care as you could damage a few important components if you set the values wrongly.

---

### Post by Markstar on 2008-10-20
No, that doesn't really work. In the BIOS I can only set one voltage for the CPU and not one voltage for every CPU frequency (under Windows, I had 0.85V @ 1GHz and 1.1V @ 2.5GHz).

---

### Post by darrelljon on 2008-10-20
90% of BIOSes are locked to CPU voltage, 10% of top-end motherboards might have adjustable voltages. To unlock the bios you need to change some switches on your motherboard I think.

---

### Post by Markstar on 2008-10-20
As I said, **it does work under Windows** so it's definitely not the BIOS (I'm pretty experienced with under-/overclocking under Windows, just not in Ubuntu :().

---

### Post by Markstar on 2008-10-27
Alright, I got it working using [cpupowerd]("http://sourceforge.net/projects/cpupowerd").

However, now I have to figure out how to permanently stop daemons and how to start the programs at startup (at startup, I want to run "cpupowerd -d -c /home/cpupowerd.conf"). :rolleyes:

---

### Post by smax3 on 2008-10-29
> **Markstar said:**
> However, now I have to figure out how to permanently stop daemons and how to start the programs at startup (at startup, I want to run "cpupowerd -d -c /home/cpupowerd.conf"). :rolleyes:

In few days, cpupowerd 0.2.0 will be released with a linux start script.

---

### Post by Markstar on 2008-10-29
> **smax3 said:**
> In few days, cpupowerd 0.2.0 will be released with a linux start script.Wow, a reply from the master himself! :razz:

I must say though that I am a total Ubuntu newbie and had a hard time installing cpupowerd with [your original guide]("http://www.meisterkuehler.de/forum/linux-unix/20124-cpupowerd-ein-tool-fuers-cpu-undervolten-unter-linux.html"). 

So it is more of a general problem for me, I would really like to know how to start programs at startup. :oops:

---

### Post by anamorgan on 2008-10-29
Mister, keep in mind one thing, NEVER PLAY WITH VOLTAGES !!
what is voltage doing to you any ways? Do with cpu speed and and all those, why alter the voltage stuffs ?
You could have done with teh voltage stuffs if you like shift your AMD to countries that use 110 V or 220 V , dont simply change teh volts for no reason !!

---

### Post by JMorg on 2008-10-29
> **anamorgan said:**
> Mister, keep in mind one thing, NEVER PLAY WITH VOLTAGES !!
what is voltage doing to you any ways? Do with cpu speed and and all those, why alter the voltage stuffs ?
You could have done with teh voltage stuffs if you like shift your AMD to countries that use 110 V or 220 V , dont simply change teh volts for no reason !!

Well, altering the voltage is how you overclock the hardware :). For example, by raising the voltage on the CPU you can "overclock" it to run a bit faster for better performance. Raising the voltage doesn't mean 110 V to 220 V, it's a matter of raising each by .1 or so and testing stability! Overclocking is not always necessary, but it can give someone a bit of an edge on performance if done correctly. You can overclock RAM, as well as certain video cards (GPU's) if permitted by the manufacturer.

---

### Post by Markstar on 2008-10-30
> **JMorg said:**
> Well, altering the voltage is how you overclock the hardware :).Not only that, but also you can seriously underclock the PC. This way, my computer in the signature only needs ~40W (with the onboard graphic card and without the 4870). :)

Adjusting the CPU voltage alone gives me around 20W under load (in addition to the underclocking itself). 

I have another thread which is about underclocking the graphic card under Ubuntu - sadly this does not seem to be possible as of now. 

...but you guys still haven't answered me how I can run cpupowerd (or any other program) at startup! :eek:

---

### Post by smax3 on 2008-11-02
> **Markstar said:**
> ...but you guys still haven't answered me how I can run cpupowerd (or any other program) at startup! :eek:
I think google is your friend.

Today, I have cpupowerd 0.2.0 released.

A start script for linux is now available.
For more details read the CHANGELOG and README files.

Download cpupowerd under [sorceforge]("http://sourceforge.net/project/showfiles.php?group_id=227607").

---

