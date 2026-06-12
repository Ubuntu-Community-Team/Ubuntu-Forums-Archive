---
title: "linux distro on Archaic laptop ?"
date: 2010-07-30
forum: Hardware
---

### Post by decypher1123 on 2010-07-30
Hey guys 
Just found an old (i mean really old :| ) laptop, goes by the name of Compaq presario 1685.
Specs

AMD k6-2 380 Mhz (chomper)
128 mb RAM
20GB HD space 
ATi Raedon 3DRage 8mb graphics
Compaq 0548h Motherboard with Phoneix BIOS
Currently running Windows 2000 pretty well 

Suggestions for a linux OS ? Cause im going to delete the entire windows partition and make it a fullfledged Linux desktop (or in this case laptop) so that i get used to the linux interface (newbie here :P ).

PS: I did find a thread related to the same laptop with slightly different specs but the user bought a new laptop  (and the thread was rather old)  and i didnt want to bump an old thread.

All suggestions welcome (except plans to burn and thrash the laptop :P ) 
Cheers

---

### Post by niitsu on 2010-07-30
You could try installing Lubuntu first. If you think it's slow, give Puppy Linux a try. If you still think it's slow, stick with Slitaz, this one will work for sure.

Regards!

---

### Post by snowpine on 2010-07-30
+1 to Puppy or SliTaz.

---

### Post by linux18 on 2010-07-30
I've got my own distro ( see sig ) and it runs super-fast and installing lxde over it still keeps disk usage below 1GB . it's 64-bit only right now but I intend to have a 32-bit version soon ( I have a release schedule of one version or program a week ) It could always use more support.

---

### Post by decypher1123 on 2010-07-30
first things first... thanks for the super fast replies guys :D 

@linux18 im still very new to linux , so once im familiar with the CLI ill definetely give your distro a shot 

Lubuntu looks great and sort of a "fuller" desktop compared to Puppy or Slitaz. Going to give it a try.

Will post the results.

Cheers

---

### Post by linux18 on 2010-07-30
> **decypher1123 said:**
> first things first... thanks for the super fast replies guys :D 

@linux18 im still very new to linux , so once im familiar with the CLI ill definetely give your distro a shot 

Lubuntu looks great and sort of a "fuller" desktop compared to Puppy or Slitaz. Going to give it a try.

Will post the results.

Cheers
in a few weeks I'll have the openbox script ready for my distro, so you just need to follow the prompts and the next thing you know your in a pseudo-lxde environment ( openbox, lxpanel, feh, network-manager-gnome, pcman, geany  - thats all you need to imitatate lxde but with even less bloat ) If anyone interested is reading this feel free to send a private message.
Ok, now im just advertising :)

---

### Post by PresenceofMind on 2010-07-30
Pick one:

Lubuntu, Xubuntu or Puppy Linux....

---

### Post by decypher1123 on 2010-07-30
Upon further googling i found 2 additional distros which seem decent enough

VectorLinux and Crunchbang Linux

Views on these?

---

### Post by snowpine on 2010-07-30
> **decypher1123 said:**
> Upon further googling i found 2 additional distros which seem decent enough

VectorLinux and Crunchbang Linux

Views on these?

I have not used Vector Linux.

CrunchBang is my primary distro. It might install with only 128mb of RAM but will be very, very slow: [http://crunchbanglinux.org/forums/topic/2504/lighten-crunchbang/](http://crunchbanglinux.org/forums/topic/2504/lighten-crunchbang/)

Please understand your hardware specs are very low and your options are limited. :( Even the lightest possible Ubuntu install (a text-only server install) requires a 300mhz processor and 128mb ram. If you want a GUI, web browser, etc. you should be looking at the "micro" distros like Puppy, SliTaz, TinyCore, etc. in my opinion. If you can increase your RAM, you'll have more options (though your slow processor will still be a bottleneck).

---

### Post by decypher1123 on 2010-07-31
After further googling i found out that with 128mb its not possible to do live cd installs 
[http://crunchbanglinux.org/forums/topic/1563/using-xubuntu-thinking-about-switching/](http://crunchbanglinux.org/forums/topic/1563/using-xubuntu-thinking-about-switching/)

and also as snowpine said , i doubt Crunchbang working with the hardware specs.

So how do i install without live cds  ? and what OS ? puppy?

---

### Post by snowpine on 2010-07-31
Puppy is a good choice. It is a small download, try it today! You need to jump in and start trying some distros; you've had a lot of good suggestions. :)

---

### Post by decypher1123 on 2010-07-31
Live CDs wont work on a 128mb RAM i believe , so I hope Puppy is not a live CD ? 

I shall try it straight away if its not . (cause i dont want to have another coaster , because i had already burned Crunchbang :| only to find out that the laptop cannot run live CDs )

Cheers

---

### Post by linux18 on 2010-07-31
puppy is a live cd but it runs in ram, if you have 128MB puppy will fully load into ram and you can take out the disk! it will run in as little a 32 MB of ram from a live cd.

---

### Post by snowpine on 2010-07-31
> **decypher1123 said:**
> Live CDs wont work on a 128mb RAM i believe , so I hope Puppy is not a live CD ? 

I have no idea where you are getting this information but the Puppy Live CD is well documented to run with 128mb. An *Ubuntu* Live CD certainly will not work with only 128mb, but every distro has its own system requirements (which you should *always* read to avoid wasting CDs).

If you can't boot from a Live CD because your laptop's CD drive is busted or something, that is a different story. :(

---

### Post by decypher1123 on 2010-07-31
Well the CD drive is working fine cause i checked it.

I downloaded , burned the Puppy CD (5.01) changed the boot priority in the BIOS and still its refusing to boot from CD and straightaway starts booting into windows 2000.

Any idea whats going on here ? ive been on this for the past 1 hour

---

### Post by decypher1123 on 2010-08-02
ok good news guys

Finally got it to work , but not by burning a CD , through USB booting.

Im posting this because it might help someone 

The BIOS was not supporting USB booting , so i used Plop to boot through USB and run puppy 5.01.

Its a bit slow , but still very manageable , theres still 49mb left out of the 128mb 

cheers

---

