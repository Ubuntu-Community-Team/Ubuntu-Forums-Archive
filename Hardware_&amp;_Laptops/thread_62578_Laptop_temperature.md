---
title: "Laptop temperature"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by ssck on 2005-09-05
Hi,

I am using Acer Travelmate 2300.

The laptop temperature monitor reports an average of mininum 56 degrees celcius and no more than 70 degrees celcius.Does your laptop report the same range of temperature as well ? Is it normal ?

Thanks.

---

### Post by minio on 2005-09-05
On my laptop (Prestigio) temperature monitor shows 11 degrees celsius 24/7  :)

---

### Post by fredricsolstad on 2005-09-05
Hi, 

Since I'm a newbie when it comes to Linux I was wondering where you get the app that shows the temp.. 

I'm using a Acer TravelMate 2350

Cheers!

---

### Post by minio on 2005-09-05
This applet i've take [here](http://www.gnomefiles.org/app.php?soft_id=1065).

---

### Post by ssck on 2005-09-05
[QUOTE=fredricsolstad]Hi, 

Since I'm a newbie when it comes to Linux I was wondering where you get the app that shows the temp.. 

I'm using a Acer TravelMate 2350

Cheers![/QUOTE]

maybe you could install the applet and post your results here.

thanks

---

### Post by cbudden on 2005-09-06
Getting 43 degrees from a fresh turn on.

---

### Post by ssck on 2005-09-06
[QUOTE=cbudden]Getting 43 degrees from a fresh turn on.[/QUOTE]

my laptop's fresh turn on is approx 55 degrees

---

### Post by TheSavage on 2005-09-06
[QUOTE=ssck]my laptop's fresh turn on is approx 55 degrees[/QUOTE]

About the same over here. (Compaq R3055CA)

---

### Post by ssck on 2005-09-06
[QUOTE=TheSavage]About the same over here. (Compaq R3055CA)[/QUOTE]

is approx 55 degrees normal ?

---

### Post by vkkim on 2005-09-07
[QUOTE=ssck]is approx 55 degrees normal ?[/QUOTE]

Depends on your CPU.  I have a Pentium M Dothan 1.2 GHz, and I've seen it go up past 65 degrees and slightly below 50, depending on what I'm doing at the time.  But the Pentium M was made to withstand high temperatures.  I'm not sure exactly what the standard operating temperatures for the Pentium 4 line of processors, but I do know that they start to slow down at a certain temperature.  So you might want to Google that.

It would help to know what kind of processor you had, and not just your model number.  I'm not going to go look it up... ;-)

---

### Post by ssck on 2005-09-07
[QUOTE=vkkim]Depends on your CPU.  I have a Pentium M Dothan 1.2 GHz, and I've seen it go up past 65 degrees and slightly below 50, depending on what I'm doing at the time.  But the Pentium M was made to withstand high temperatures.  I'm not sure exactly what the standard operating temperatures for the Pentium 4 line of processors, but I do know that they start to slow down at a certain temperature.  So you might want to Google that.

It would help to know what kind of processor you had, and not just your model number.  I'm not going to go look it up... ;-)[/QUOTE]

the cpu of my laptop is a pentium m 1.5 ghz

---

### Post by vkkim on 2005-09-07
[QUOTE=ssck]the cpu of my laptop is a pentium m 1.5 ghz[/QUOTE]
 In that case, yes, 55 degress is perfectly fine.  As a matter of fact, mine is running at 56 right now.

---

### Post by c0rderr0y on 2005-09-07
My Centrino 1.6 is getting 36 idle....

---

### Post by ssck on 2005-09-07
[QUOTE=c0rderr0y]My Centrino 1.6 is getting 36 idle....[/QUOTE.]

why is there such a vast difference ? mine runs on an average of 55 deg,is there something i need to look at ?  #-o

---

### Post by c0rderr0y on 2005-09-07
Do you have speed step enabled?

---

### Post by FatherDale on 2005-09-07
[QUOTE=ssck]maybe you could install the applet and post your results here.

thanks[/QUOTE]

I thought that was a great idea, so I went off to find the applet. Tried to dpkg it in, no joy. Unmet dependencies. Hm, thought I had all that stuff. Go back to the site to see what I missed. Hmmm. Thought I *had* all that stuff.... Try again. Lessee, where's GTK+.... Nope, not there. Not showing up in Synaptic, either. OK, fellas, what am I missing here?

Ah, ok, Python-gnome2-extras. Shows as unstable. <headscratch> Really?

f3d

---

### Post by vkkim on 2005-09-07
[QUOTE=c0rderr0y]My Centrino 1.6 is getting 36 idle....[/QUOTE]
 How is your laptop constructed?  Do you have a fan?  What is the ambient room temperature?

I have speed step enabled, but my laptop is a Panasonic Let's Note R3, ~900g with battery and 10" screen so no space for a fan or big heatsink...

---

### Post by mlord on 2005-09-07
[QUOTE=FatherDale]I thought that was a great idea, so I went off to find the applet. Tried to dpkg it in, no joy. Unmet dependencies.[/QUOTE]

      cat /proc/acpi/thermal_zone/THM/temperature

---

### Post by John.Michael.Kane on 2005-09-07
What if ----->/proc/acpi/thermal_zone is empty eg: these files not in there THM/temperature.. laptop is centrino based 1.3ghz

---

### Post by ssck on 2005-09-08
[QUOTE=c0rderr0y]Do you have speed step enabled?[/QUOTE]

sorry newb question :-  how do i  check if speedstep is enabled ? :-k

---

### Post by vkkim on 2005-09-08
[QUOTE=SD-Plissken]What if ----->/proc/acpi/thermal_zone is empty eg: these files not in there THM/temperature.. laptop is centrino based 1.3ghz[/QUOTE]
 try cat /proc/acpi/thermal_zone/TZC/temperature
there are different kinds of sensors

---

### Post by John.Michael.Kane on 2005-09-08
/proc/acpi/thermal_zone/ folder is empty nothing there..... any idea why?

Thanks

---

