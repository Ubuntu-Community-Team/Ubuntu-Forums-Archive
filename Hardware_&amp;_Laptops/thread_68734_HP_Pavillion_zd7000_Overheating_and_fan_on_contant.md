---
title: "HP Pavillion zd7000 Overheating and fan on contantly"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by daniel@dpr on 2005-09-24
Hi there,
I know there are a few posts about fans on all the time, and something called "powernowd" but I cant make sense of them (I am a total newb.)

My problem is my laptop is overheating, and the laptop has shut down due to this a few times now.

The fan is on Fully all the time.

I dont know how to check temps etc of anything. I am ignorant to the ways of ubuntu.
I tried installing [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

but the sensor detect section found nothing.

Has anyone had any issues with a ZD7000?

What can I try (in simple instructions please) to keep my CPU usages down and fan usage less as a result.
Thanks

Daniel

---

### Post by david marcus on 2006-10-23
Dear Daniel,

I have just found your email re overheating laptop, fan going crazy etc....  I know you sent your message over 1 year ago, but did you resolve the problem?  If you have a moment, I would appreciate any advice.

Thanks,

David

---

### Post by daniel@dpr on 2006-10-23
Sorry, I did not find a fix.
It was out of control, and I thought my notebook was going to crash.
I went back to xp.

I have not encountered it happening again since.

I have heard of some people tuning their cpu to "battery mode" in XP to cut down on heat, but have no idea on how to do that in Ubuntu.

---

### Post by biodiesel-bri on 2007-04-21
I had the same issue and had the fans cleaned and the problem went away (in my case the fans had sucked up a ton of cat hair).  zd7000s seem to have this problem.

---

### Post by kingkookie on 2007-04-23
I have an HP Pavilion ze4547wm with the same issue.  I've used Dapper, Edgy, and now Fiesty, but the issue still remains.  My research shows that this issue is a problem with Ubuntu only.  Other Linux OSes do not seem to suffer from this problem.  I haven't proven that though.  I'm downloading another Linux Distribution to find out.  We shall see.

---

### Post by Wulfrunner on 2007-04-30
This is still a problem -- and it's not because of a dirty fan. With a new Thinkpad T60p, the fan is on constantly even though the temperature reading in /proc/acpi/ibm/thermal has the cpu under 45 and the gpu under 60 (both normal operating temperatures). I had Gentoo going on this thing but the problem was still there. I am going to try Fedora Core 6 now and see if it makes a difference.

---

### Post by dangermouse28 on 2007-06-12
I have a ZD7000 running Ubuntu 7.04.

Yes, these laptops have a design-related heat "issue" - who ever thought of putting fans in the base of a laptop needs taken out and shot!

However, my ZD7000 runs cool and quiet (relatively ;))

The problem is that with a default install of Ubuntu, there is no CPU frequency management which means that it will run at 3GHz all day even when it's doing nothing - which is why it gets hotter and hotter.

The solution is to configure the CPU frequency management (this is an excellent guide - [http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"))

Now my ZD7000 will sit at 375MHz all day, until it's needed when it ramps up and down through the frequencies as required!

Good Luck!

---

### Post by drummingpariah on 2007-06-12
> **dangermouse28 said:**
> I have a ZD7000 running Ubuntu 7.04.

Yes, these laptops have a design-related heat "issue" - who ever thought of putting fans in the base of a laptop needs taken out and shot!

However, my ZD7000 runs cool and quiet (relatively ;))

The problem is that with a default install of Ubuntu, there is no CPU frequency management which means that it will run at 3GHz all day even when it's doing nothing - which is why it gets hotter and hotter.

The solution is to configure the CPU frequency management (this is an excellent guide - [http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"))

Now my ZD7000 will sit at 375MHz all day, until it's needed when it ramps up and down through the frequencies as required!

Good Luck!

hmmm, this looks like pretty good info.  I'd think that anybody with a laptop would want this.  I've been wondering about my Asus lately...  <runs off to read the link>

---

### Post by CrispyFried on 2007-06-12
> **daniel@dpr said:**
> 
I dont know how to check temps etc of anything. I am ignorant to the ways of ubuntu.
I tried installing [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

but the sensor detect section found nothing.


I couldnt get lm-sensors to work either using that thread too ("no sensors found!") but "acpi -t" at the cl works to check them.

---

### Post by angelogladding on 2008-04-28
I too have spent countless hours over the last year trying to figure out just why my fans were going so hard despite frequency scaling and using a laptop fan station in a heavily air-conditioned room. I understand this is an old thread but I thought I'd share my recent success story for any Googlers still trying to tame this beast of a laptop. 

biodiesel-bri talks about cat hair.. DO NOT DISREGARD! :)

I just whipped out my microtop phillips screwdriver, ripped off the fan panel from the bottom of the laptop, lifted the fans, lifted the plate, and vacuumed out cake. Dust cake. Dust cake with animal hair frosting..

Now it's silent. Try it. Good luck.

---

### Post by schwinn on 2008-05-02
My zd7000 seems to run fine on 7.10. I do remember having to do some power management stuff, and currently I have powernowd running. I also have Gnome's temperature monitor running in the top-bar, showing me a temp of 45C at the moment (no load). If I block the fan with my left leg, it certainly goes up, though I usually notice it before it gets any higher than 55C.

I had another CPUFreq program running in Gnome at one point, but it kept crashing out on me. Still, from there, I could set a higher CPU rate, or a lower one, or auto... and it seemed to work pretty well, too.

I'm still wondering if 8.04 will work properly, so I'm holding off for now until I see some good news on that front... anyone have any good experiences with the upgrade?

---

### Post by Aris384 on 2008-05-04
I have the same problem with Hardy and with Debian Lenny, the solution for me is to pass at boot time the option "acpi=off" to the kernel. That works for Hardy, Lenny and the Hardy LiveCD too.  Edgy just works fine without that option, an ACPI bug perhaps? My Laptop is an HP Pavillion ZD7000.

Hope it helps.

---

