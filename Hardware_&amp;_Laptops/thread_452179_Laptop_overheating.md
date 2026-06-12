---
title: "Laptop overheating"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by tme on 2007-05-23
Hello!

My laptop ASUS F3Tc gets superhot almost anytime with Ubuntu Feisty, even if computer idles.
It's most warmest on right side of mousepad, I think if hard drive is placed there.

```

tme@tme-laptop:~$ acpi -V
     Battery 1: charging, 98%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 60.0 degrees C
     AC Adapter 1: on-line

```

Now it's much colder than sometimes when I really do something with that laptop.

Does anyone know how I should solve this problem?

Thanks :)

---

### Post by Barnable on 2007-05-23
[QUOTE=tme;2705027]Hello!

My laptop ASUS F3Tc gets superhot almost anytime with Ubuntu Feisty, even if computer idles.
It's most warmest on right side of mousepad, I think if hard drive is placed there.

```

tme@tme-laptop:~$ acpi -V
     Battery 1: charging, 98%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 60.0 degrees C
     AC Adapter 1: on-line

```

QUOTE]

What is an acceptable temperature? My Fujitsu-Siemens regularly goes at about 50-53 degrees C.

Mine also has the fan going like a rocket even when chugging along at lowest CPU speed (800MHz), and shut itself down last night...!

Oh, and I can't seem to change the CPU frequency anymore, whether using the cpufreq applet or by forcing it on the command line.

B.

---

### Post by kaede on 2007-05-23
seems like this laptop overheating issue really happen almost for some brand. 

hope there's a sollution soon. i do get some around 75 degrees with my asus l3c

---

### Post by badboy_24u on 2007-05-23
[SIZE="3"]it is a common problem on laptops. and in some cases, in desktops also.

that's because, unlike windows, ubuntu doesn't provide the processor a better file handling system like windows do. to make things short, ubuntu just uses the entire cpu capacity whenever needed. even if your just trying to open a web browser or text editor. it still uses the whole power of your pc.
[/SIZE]

---

### Post by eejk on 2007-05-23
> **badboy_24u said:**
> [SIZE="3"]it is a common problem on laptops. and in some cases, in desktops also.

that's because, unlike windows, ubuntu doesn't provide the processor a better file handling system like windows do. to make things short, ubuntu just uses the entire cpu capacity whenever needed. even if your just trying to open a web browser or text editor. it still uses the whole power of your pc.
[/SIZE]

LOL

---

### Post by hardyn on 2007-05-23
hardware specs please

---

### Post by Death_Sargent on 2007-05-23
ok im gona give you the strangest advice you may ever hear

find your exaust fans. 

get a vacum cleaner.

takes about 30 minnutes to get out the stuff in there. 

or if you feel you are up to it. open her up and manually remove the lint and dust. you will be surprised at how much is there.

---

### Post by eejk on 2007-05-24
I had an over heating problem on my hp nx9420. Because speedstep was not properly working I manually set my clockspeed to 1.8 GHZ all the time. Apparently this made the laptop fan run at full speed ALL the time. I didn't realize that was the problem until I purchased a new laptop and noticed when the speedstep was running and it got bumped to max speed the fans increased speed. So you might want to check if speedstep is working properly.

---

### Post by Brinstar on 2007-05-24
uncomment acpi_cpufreq in /etc/rc.d/rc.modules

---

### Post by tme on 2007-07-13
Hello.

I don't have file _/etc/rc.d/rc.modules_. I'm running Ubuntu Feisty.

I purchased this laptop about two months ago, so the fan cannot be dirty.
My laptop is always on the table and I clean up my room once a week.

---

### Post by Steveway on 2007-07-13
It's not dirt. It's dust and a fan can get a lot of dust in 2 months.

---

### Post by Skidpad on 2007-07-13
**Disclaimer:**  Try this at your own risk!

I use my air compressor to blow my cooling systems/computers out.  Works great, but ya' gotta be careful to avoid damaging fans, etc.

---

### Post by nebbe on 2007-09-05
Hi.

I read this thread and as faar as i can see no one has got a solution to this problem.

Since "TME" wrote that he fairly recently bought his laptop, giving him an instruction-manual on howto clean the fan and **** isnt the main issue here :)
Im pretty sure that all computer-nerds knows when its time to do some cleaning of their desks and computer fans since thats the Only thing we ever clean ;)

Ive bought this Asus F3Tc yesterday, and its very hot on the right hand side close to the touchpad-area, as "TME" previously described it.

Has anyone got a clever idea on howto actually reduce the heat without lowering or having to monitor the CPU-speed?

(And no, my lap is not filthy, but its burning up)

Cheers!

---

### Post by nebbe on 2007-09-05
> **badboy_24u said:**
> [SIZE="3"]it is a common problem on laptops. and in some cases, in desktops also.

that's because, unlike windows, ubuntu doesn't provide the processor a better file handling system like windows do. to make things short, ubuntu just uses the entire cpu capacity whenever needed. even if your just trying to open a web browser or text editor. it still uses the whole power of your pc.
[/SIZE]

Dont drink and drive

---

### Post by brittai on 2007-09-05
I've got an HP dv9574 less than 2 weeks ago and i have the same problem (to the left of the mouse pad).

I've been reading other threads and there seems to be some kind of problem with multiprocessor kernels (as in "dual core") and/or some acpi settings that cause the overheating, and, as far as i've seen, this happens on many notebooks (manufacturers and/or models).

The fan may be on/off all the time (meaning: draining battery/overheating). This happens depending on who knows what (even similar models show different behavior).

I'm not aware of any solution yet...

Regards.

---

### Post by torstenaf on 2007-09-05
I just solved this problem for my Sony VAIO 505. See:

[http://ubuntuforums.org/showthread.php?t=539365]("http://ubuntuforums.org/showthread.php?t=539365")

---

### Post by frith on 2007-09-05
Okay, I am a little bit of a newbie, but I do have a suggestion.

I installed ubuntu on my toshiba m200 and it installed and ran fine - except I would get about an hour out of a battery that lasts four hours in windows.

The problem was that in the default install there was no cpu scaling, so it was running full tilt the whole time. This is often the case when playing movies or games on windows, but when you are just surfing the net or writing posts to a forum, speedstep is supposed to throttle back the cpu. On my particular machine, if I am compiling a bunch of stuff or running cpu intensive programs it gets pretty warm and the fans switch on.

So my suggestion to you is to install a cpu speed controller (eg. [http://www.deater.net/john/powernowd.html](http://www.deater.net/john/powernowd.html)) I think the one I use is cpufreq-utils (sudo apt-get install cpufreq-utils). A short google or forum search for info on cpu scaling should yield the desired results.

Frith.

---

### Post by bernardpatteeuw on 2007-09-30
I have a M6000 Asus and I have the same problem. Laptop is very hot at the right side of the mouse pad.
Hope there is a solution...

---

