---
title: "What Laptop will work with Ubuntu OUT THE BOX?"
date: 2008-05-09
forum: Hardware
---

### Post by Coderoid on 2008-05-09
Hi Guys,

Okay ive had some installation hell with my AMD Turion TL-58 64x2 powered HP notebook and Ubuntu - see this thread:

[http://ubuntuforums.org/showthread.php?t=786463&page=2](http://ubuntuforums.org/showthread.php?t=786463&page=2)

I want to try to purchase another notebook that wont sap my enthusiasm with installation... what do you recommend? I was thinking ASUS, but i'm open to suggestions.

Best Regards,

Lloyd Dube

---

### Post by hallgeirl on 2008-05-09
My ASUS F3Ja works perfectly out of the box (no driver installs required). Granted, it's an aging laptop of a bit over 1 year. I'm not sure how the newer laptops are behaving though.

---

### Post by hermes0710 on 2008-05-09
HP dv9770ev works just fine, no manual hardware configurations needed

---

### Post by eurgain on 2008-05-09
I have both Dell Latitude X1 tiny machine and HP nx7400 desktop replacement, and both work completely with the default install of [XK]Ubuntu and SUSE10.3.  The only exception is the modem (which I don't use) but have had working with the Linuxant drivers.  Apart from that, it is all go.

Both are Intel through-and-through, which, seems to be a Good Thing for ease of installation.

A

---

### Post by mindracer on 2008-05-09
Hi im sort of a newbie, I got a new HP Compaq 6710b at work, put ubuntu 8.04 on it and everything worked! Wireless, video, everything.  The only problem I have it getting the s-video tv out to work in ubuntu, not a major thing but im used to connecting my tv daily to my laptop to watch shows.

I was really surprised it worked out of the box! Happy free customer :)

---

### Post by anars on 2008-05-09
My Lenovo Thinkpad T61 also works out of the box :-) Heck of a laptop.

Minor tweaking needed in order to make the fingerprint reader work, though.

---

### Post by Zorael on 2008-05-09
My Acer Aspire 9815 required minor tweaks (which took some time to figure out, heh.) So may want to stay away from that one unless you like tinkering.

Namely:
[list][*]**WLAN**: Adding a file located and named [FONT="Courier New"]/etc/modprobe.d/iwl3945[/FONT] with the following content:
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1
```
Alternatively compiling own drivers from [http://linuxwireless.org/](http://linuxwireless.org/). I'm running the 2008-05-02 git snapshot now, with which I no longer need the [FONT="Courier New"]disable_hw_scan=1[/FONT] option.


[*]**SOUND**: Adding a line to the bottom of [FONT="Courier New"]/etc/modprobe.d/alsa-base[/FONT] saying:
```
options snd-hda-intel model=acer
```[/list]

The only unresolved issue yet is fan speed after resuming from suspend.

**This is the case with Hardy**; sound worked out-of-the-box in Gutsy. As for the fan speed, I can't recall.

---

### Post by Coderoid on 2008-05-09
hmmm...thanks to you all for these responses :)

i am currently Googling all these options and sizing things up...
i don't know if i should try again with this AMD powered HP or just give up and trade in.

---

### Post by housam on 2008-05-09
My HP Compaq nx7400 is just working fine with 3 OS onboard, xp, hardy ubuntu / kubuntu .

---

### Post by Coderoid on 2008-05-09
Guys, how do i get to the boot: prompt when the Live Disk runs? I found out how i can pass Live Acpi=NOACPI at that prompt but i just need to get there!

Thanks :)

Lloyd Dube

---

### Post by jespdj on 2008-05-09
Dell XPS M1530.

---

### Post by cb951303 on 2008-05-09
lenovo t61 is a linux monster :guitar:

---

### Post by swisstone on 2008-05-09
hmm... my Acer Aspire 2414 Installs out-of the box, so does the NEC M300, Dell D630,510,520 

Just be careful what chipset your wireless & onboard gfx are based on if you want easy installs.

---

### Post by cacycleworks on 2008-05-15
> **swisstone said:**
> hmm... my Acer Aspire 2414 Installs out-of the box, so does the NEC M300, Dell D630,510,520 

Just be careful what chipset your wireless & onboard gfx are based on if you want easy installs.

I've got a D630. Hardy was the first 64 bit OS to install perfectly for me. 

I blather on more about it here:
[http://ubuntuforums.org/showpost.php?p=4967469&postcount=44](http://ubuntuforums.org/showpost.php?p=4967469&postcount=44)
[http://ubuntuforums.org/showpost.php?p=4961282](http://ubuntuforums.org/showpost.php?p=4961282)

Basically, I've learned that you google about the choices in hardware for your targeted laptop. For my D630, I chose intel graphics and intel 3945 wireless.

:) Chris

---

### Post by Coderoid on 2008-05-16
Hey guys, thanks all for the words of advice!

I've actually been eyeing a Dell XPS 1330m - and yes, after surfing around on various fora i've learned one shouyld be careful when choosing graphics and wireless!

The price of an XPS 1330. just shot up over here by over 25% while i was organizing cash :|...anyway...lol

Regards,

Lloyd Dube

---

### Post by anthonyp on 2008-05-16
toshiba satellite m30 works, although slow, i did not require anything except activating the nvidia driver.

BUT

sleep/hibernate & suspend never worked.... shame really.

---

### Post by Fatman_UK on 2008-05-16
My Alienware Area-51 m5550 is awesome with Ubuntu. Couldn't say about suspend/hibernate though, I never use them anyway.

---

### Post by tommcd on 2008-05-16
If you are in the market for a new linux laptop:
[http://system76.com/index.php?cPath=28](http://system76.com/index.php?cPath=28)
[http://www.zareason.com/shop/home.php](http://www.zareason.com/shop/home.php)
Or for general laptop compatibility info:
[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

### Post by Coderoid on 2008-05-16
Thanks all for your feedback on experiences and ultra-useful links!

---

### Post by chriswyatt on 2008-05-16
My HP DV2058ea worked out of the box, did need a bit of messing about on the earlier versions of Ubuntu, easier to install than Windows now!

---

### Post by Coderoid on 2008-05-16
@@chriswyatt - interesting! are you running 8.04?

Maybe i should hold out and get my 8.04 disks...might install well.

---

### Post by kuyote on 2008-05-16
I just installed 8.04 on my asus U6S. The install was flawless, I still have to look into the finger scanner, but haven't tried to mess with it yet.

---

