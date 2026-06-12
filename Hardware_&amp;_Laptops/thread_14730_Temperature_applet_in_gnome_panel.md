---
title: "Temperature applet in gnome panel"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by ming0 on 2005-02-09
Does anyone know of a temperature applet that runs in the gnome panel? 

I'd like to have something that reads the acpi temp and then reports it on the panel...

Thanks :-)

---

### Post by ming0 on 2005-02-10
Wow, I've answered my own question--there's a great applet, called emifreq-applet, that will monitor your cpu speed, temperature, and allow you to adjust the speed of the proc (as long as userspace switching is enabled--which I'm not sure is enabled by default?).

It looks fine, and works off of acpi--so there's no configuration at all :)

Check it out here: [http://zzrough.free.fr/emifreq.php#screenshots](http://zzrough.free.fr/emifreq.php#screenshots)

Get it w/ synaptic or:
sudo apt-get install emifreq-applet

---

### Post by fizgig on 2005-02-24
[QUOTE=ming0]Wow, I've answered my own question--there's a great applet, called emifreq-applet, that will monitor your cpu speed, temperature, and allow you to adjust the speed of the proc (as long as userspace switching is enabled--which I'm not sure is enabled by default?).

It looks fine, and works off of acpi--so there's no configuration at all :)

Check it out here: [http://zzrough.free.fr/emifreq.php#screenshots](http://zzrough.free.fr/emifreq.php#screenshots)

Get it w/ synaptic or:
sudo apt-get install emifreq-applet[/QUOTE]

Thanks ming! I installed it and it works great.

---

### Post by ming0 on 2005-02-25
[QUOTE=fizgig]Thanks ming! I installed it and it works great.[/QUOTE]

It's odd, it worked well for me before I rebooted, but once I did a reboot, it had some sort of cpu freq changing driver that would conflict with ubuntu's built in solution--when you disable their driver, the applet complains about it's cpu freq driver not starting. 

I suppose I could live with the "OUR DRIVER ISN'T ON!!!" error every time I restart Gnome, but I just turned the applet off  :| 

Let me know if you start having the same problem--maybe we can come up with a fix.

---

### Post by drabikmr on 2005-03-08
[QUOTE=ming0]Wow, I've answered my own question--there's a great applet, called emifreq-applet, that will monitor your cpu speed, temperature, and allow you to adjust the speed of the proc (as long as userspace switching is enabled--which I'm not sure is enabled by default?).

It looks fine, and works off of acpi--so there's no configuration at all :)

Check it out here: [http://zzrough.free.fr/emifreq.php#screenshots](http://zzrough.free.fr/emifreq.php#screenshots)

Get it w/ synaptic or:
sudo apt-get install emifreq-applet[/QUOTE]

I would just love to have this applet as I really like to keep tabs on the cpu's temperature, but I have tried to use apt-get to install it and this is what I get:

Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package emifreq-applet


And yes  - I did 'apt-get update' and yep ubutu updates alright, but I still get the same message when I try the apt-get install command.

And further yes - I have also used apt-get upgrade too - no change.

And further, further, yes - I also updated the  respositories as per the Ubunutu Starter Guide - and still no change.

So, when Plan A fails - try Plan B - - download the tarball & try install it.

Hey the tarball  downloaded and extracted just fine into the folder I created on my desktop for downloads (called - downloads)  and then I ran the usual './configure' and after getting about a gazillion errors having to do with not having 'gcc' installed and with uninstalled libraries -- which I promptly installed I finally got './configure' to work  and THEN I did 'make' and 'twas made - - - - -

uuhhh - expect everything for the applet got 'made' in the downloads directory I have on my desktop instead of in the proper Linux directories.

Yes, yes, I'm a bit of 'noober' on installing software from a tarball -- but I ain't exactly a klutz as I am using FoxFire 1.0.1 which as far as I can tell hasn't even reached the Ubuntu "Backports" project. Indeed I installed Foxfire 1.0.1 in the very same downloads directory I have this applet's tarball in. It works like a charm  and I am using it right this very minute.

Soooo - if anybody has any suggestions, comments as to what I am doing wrong or am not doing right enough to get this applet installed - I sure would appreciate it.

Cheers! :p

---

### Post by ming0 on 2005-03-08
I'm using hoary, so I suppose I can't give you much advice... Have you tried gkrellm? (I'm pretty sure that's what it's called) It can monitor your temp, along with a LOT of other stuff. It needs something called lm_sensors, which is a bit tricky to set up, but if you follow the howto, it's not too bad...

[http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors+howto](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors+howto)

Good Luck :)

---

### Post by drabikmr on 2005-03-08
[QUOTE=ming0]I'm using hoary, so I suppose I can't give you much advice... Have you tried gkrellm? (I'm pretty sure that's what it's called) It can monitor your temp, along with a LOT of other stuff. It needs something called lm_sensors, which is a bit tricky to set up, but if you follow the howto, it's not too bad...

[http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors+howto](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors+howto)

Good Luck :)[/QUOTE]

Thanks for that suggestion.  I was able install to gkrellm and lm-sensors and get both configured to my tastes.

It's not ideal - I really would have liked to have that applet, but apparently since it that seems to only run on Hoary I'm out of luck. At least I have a means to monitor the system temps now in both a GUI based program or in a terminal.

Just a noob question: 'hoary' means the Ubuntu development version - is that right?

---

### Post by CameronCalver on 2006-05-21
when i download it i dont get a preferences opting when do a right click?

---

### Post by huygens on 2007-06-11
There is an applet that just does this for the Gnome desktop: [Computer Temperature Monitor]("http://www.berthon.eu/ice_and_fire/?p=17")
The blog post even mention that if you install the package hddtemp, then you can use the applet to monitor your CPU temperature and/or your hard disk temperature.

---

