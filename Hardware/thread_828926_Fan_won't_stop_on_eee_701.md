---
title: "Fan won't stop on eee 701"
date: 2008-06-14
forum: Hardware
---

### Post by golovan on 2008-06-14
Hi

I have installed the new Ubuntu eee (gold) on my eee 701 4G.
After about ten minutes of regular use (i.e just surfing with firefox) the fan starts up, and then it's always on. What's wrong? 

I have run the ubuntutweeek-script for hardy (and it fixed sound issues etc), but I can't remember if the fan-issue was there pre to running the script.

Anyone else having this?

---

### Post by mrarsoft on 2008-06-14
Have you enabled the processor scaling?
Check 
[http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly)
for details about how to do it.

---

### Post by golovan on 2008-06-14
Can't see that enabling processor scaling would help?
According to the link you gave, it will run at full power mode anyways when on ac-power. My fan kicks in on both battery and ac after approx ten minutes and won't stop running after that. I guess it kicks in on a given temperature, but then it won't cool down and the fan keeps running  and running. It wasn't like this on xandros. Anyone else with Ubuntu eee gold having this problem?

[edit]I enabled processor scaling, but it didn't help. Cpu jumped from 630 to 900 instead of going down.[/edit]

---

### Post by golovan on 2008-06-14
Hm can this be a bios-issue? I did an upgrade when on xandros, but the fan-issue didn't appear before I installed ubuntu eee.

I now have Asus 701 ACPI BIOS Revision 0910

Is it worth trying to revert to 0401? And if so, how do I do this in Ubuntu? 
Is this safe: unzip 401 (from asus site) to usb and reboot?

[edit]Beginning to think this is normal:) Been checking the temperature with acpi -t and it is about 54-57. The fan kicks in around 51 or something according to a wiki on google.code (can't remember the url right now). It also states that it is normal and that the fan won't go silent until the temperature is about 46, which  it most likely won't be until you turn it off for a while. So I'll leave everything like it is for now:)[/edit]

---

### Post by efjen on 2008-06-25
I had the same problem with my eee 900. You are correct in that this is the fan controller's default behaviour. I believe it is causing a problem with other distros than the stock Xandros, because they tend to draw a little more power over all.

I believe the page you were referring to is this: [http://code.google.com/p/eeepc-linux/wiki/EmbeddedController](http://code.google.com/p/eeepc-linux/wiki/EmbeddedController)

The fan turns on at 55 C and off at 46 C. However, it is only run with 40% power at this stage. In practise, the fan would turn on when I viewed my first youtube video, and never turn off. I found this very annoying, as the temperature would only peak to 55 when I was watching youtube videos, and decrease to a stable 50-52 when I was browsing regular pages. 
Hence, the temperature would actually be well below Asus' threshold of 55 C most of the time, but with the fan constantly drawing power and making noise.

Now I've installed the experimental kernel module (eee.ko) which allows you to read the temperature and set the fan speed manually. I've written a small program which watches the temperature and turns the fan to 80% at 60 C and turns if off at 56 C. This seems to be a very good solution for me. The fan turns on whenever the CPU gets stressed, and turns off a few seconds after the demanding process is finished. The temperature mostly often hovers around 54-56 now, with the fan off.

Risky? Maybe. I personally don't think 60 C will harm the CPU at all, considering that Asus' default behaviour runs the fan at a lazy 40% power until 69 C.

---

### Post by MrChezedoodle on 2008-06-26
Dude had the same issue.  don't worry just do this...

1) unplug from power source and remove battery from the back
2) open the computer and hold the power button for about 30 seconds
3) reboot your computer and it should be running fine!

theres a problem in the wiring where the energy gets built up in capacitors and never leaves creating the 100% fan issue.  This clears everything out.  

let me know if it worked for you

steve

---

### Post by tedrow on 2008-06-27
Wonder rif this will cure the same behavior ini my Dell Lat D630 - which has changed fan running dynamics since installing hardy.  I'll try and re-post later.

---

### Post by MrChezedoodle on 2008-06-27
give it a trydude. the same concept should work

---

### Post by golovan on 2008-06-29
> **efjen said:**
> I had the same problem with my eee 900. You are correct in that this is the fan controller's default behaviour. I believe it is causing a problem with other distros than the stock Xandros, because they tend to draw a little more power over all.

I believe the page you were referring to is this: [http://code.google.com/p/eeepc-linux/wiki/EmbeddedController](http://code.google.com/p/eeepc-linux/wiki/EmbeddedController)

The fan turns on at 55 C and off at 46 C. However, it is only run with 40% power at this stage. In practise, the fan would turn on when I viewed my first youtube video, and never turn off. I found this very annoying, as the temperature would only peak to 55 when I was watching youtube videos, and decrease to a stable 50-52 when I was browsing regular pages. 
Hence, the temperature would actually be well below Asus' threshold of 55 C most of the time, but with the fan constantly drawing power and making noise.

Now I've installed the experimental kernel module (eee.ko) which allows you to read the temperature and set the fan speed manually. I've written a small program which watches the temperature and turns the fan to 80% at 60 C and turns if off at 56 C. This seems to be a very good solution for me. The fan turns on whenever the CPU gets stressed, and turns off a few seconds after the demanding process is finished. The temperature mostly often hovers around 54-56 now, with the fan off.

Risky? Maybe. I personally don't think 60 C will harm the CPU at all, considering that Asus' default behaviour runs the fan at a lazy 40% power until 69 C.

Hi and tnx for your reply! I'm not sure if I run the eee.ko-module stuff. Just a plain Ubuntu Eee 8.04 install +automatic script. But your little program sounds like a great app. How did you do it? I've decided to not mind the fan, because it really aint that much of a noise (only goes to 40%). That said, quiet is always better:)
Btw. yes it was that googlecodepage.

---

