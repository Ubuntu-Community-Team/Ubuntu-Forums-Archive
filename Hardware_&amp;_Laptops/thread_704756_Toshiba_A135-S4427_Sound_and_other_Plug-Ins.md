---
title: "Toshiba A135-S4427: Sound and other Plug-Ins"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by StephenJoMo on 2008-02-22
I am running the trial CD of UBUNTU on my Toshiba A135-S4427.  It seems not to recognize the sound system.  I'm hoping you folks can recommend a fix that's clear and readily installed.

I've found it links up to my WiFi quickly and easily, runs most aplications I need, and is a great alternative to Vista-ughh (the only version of Windows supported on this machine).

I'd also like to install it on my little girl's machine.  It's an old Win98 vintage machine -- 400MHz, 10GB disk, 1/2GB memory, etc.  It seems it would run nicely when all she wants to do is on the web, or use drawing/paint programs to create designs and greeting cards; and Open Office will suffice nicely for everything else.

 Recognizing that I'm a user, not a LINUX maven, please let me know how to introduce my sound card to ubuntu.

Thanks,
S

---

### Post by VMan on 2008-02-22
Greetings and welcome to the[COLOR="Blue"]**[SIZE="5"] Wonderful World of Ubuntu[/SIZE]**[/COLOR].:KS

Your problem is a common one.  There are several ways of making it work.  Currently, I have sound working, but when I plug in my headphones, the speakers don't shut off.  They do get quite a bit quieter though.  I have a very similar laptop.  I have a small page up on the [Laptop Testing site]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA135").  The details are posted there along with other details.

To get sound working:
Add the following line to /etc/modprobe.d/alsa-base:
options snd-hda-intel model=3stack
You will have to do this as root (sudo) in order to edit the file.

There are several other variations on this.  I have tried several and almost all have worked.  I think this is the one I am currently using.

Feel free to PM me if you need further assistance or have any other questions.  As to your daughter's machine, I am running Ubuntu 7.10 on a machine with even less specs than that one.  It runs, but slowly.

---

