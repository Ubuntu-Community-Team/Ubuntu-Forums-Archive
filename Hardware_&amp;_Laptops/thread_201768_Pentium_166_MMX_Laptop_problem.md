---
title: "Pentium 166 MMX Laptop problem"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by Hopelessness on 2006-06-22
I have been trying to install dapper drake on my laptop, but just as the gui loads the machine hangs. It does this on breezy badger too, whether i am using a live or install cd. Any ideas?

---

### Post by Hopelessness on 2006-06-22
ok so now i have got it to stop hanging [dirty pin on the cpu] but now it just sits spinning up the cd, reading, and stopping the cd with the background black,  and a cursor, which i can move with the mouse. annoying, because i can't do anything with it. i have left it for about an hour now! any ides on this?

---

### Post by compmodder26 on 2006-06-22
It would be tough for any gui to work with a Pentium 166.  Perhaps you should try Xubuntu.  XFCE is the desktop in that.  It is significantly more lightweight than Gnome or KDE.  Not sure if even that will work though.  Have you been able to get other distros to work on it?

---

### Post by Hopelessness on 2006-06-22
not that i can think of, i have had windows 2000 and a nLited version of windows XP on there too [takes away system restrictions]. how much difference is there between ubuntu and Xubuntu?

---

### Post by compmodder26 on 2006-06-22
Just the desktop as far as I know.  The ubuntu base system is the same across all versions of ubuntu (Ubuntu, Kubuntu, Xubuntu).  I haven't personally used Xubuntu but I do know that the XFCE desktop is very lightweight.

---

### Post by Hopelessness on 2006-06-22
while i have been talking, the laptop has actually loaded up the entire gui. looks very nice, but an hour or so loading time might be a tad excessive! i have started downloading the xubuntu image now so i will report back in a bit

---

### Post by az on 2006-06-22
[QUOTE=Hopelessness]not that i can think of, i have had windows 2000 and a nLited version of windows XP on there too [takes away system restrictions]. how much difference is there between ubuntu and Xubuntu?[/QUOTE]
How much ram do you have?  You need 64 megs of ram (sometimes more) to run the alternate installer and 256 megs of ram to run the Desktop installer.

I would suggest that xfce is even too ressource-hungry for a pentium one.

I run Ubuntu on a laptop like that.  166 Mhz with 96 megs or ram.

I would use the alternate cd, and pick the server option to install.  Then I would boot into my new system, edit the source.list by hand (sudo nano /etc/apt/sources.list) and uncomment universe.  The I would install a basic fast system:

sudo apt-get install x-window-system-core icewm menu wdm mozilla-firefox synaptic xterm

---

### Post by Hopelessness on 2006-06-22
i have 128mb of ram

could you run me though that step by step? i am quite new to linux, i have used suse before, but i am a total noob at command line stuff! thanks

---

### Post by az on 2006-06-22
[QUOTE=Hopelessness]i have 128mb of ram

could you run me though that step by step? i am quite new to linux, i have used suse before, but i am a total noob at command line stuff! thanks[/QUOTE]
Boot the alternate installer cd.  Pick "server".  Wipe the drive.  When your install is copleted, log in.  Type

sudo nano /etc/apt/sources.list

delete the comment (the "#" symbol) at the beginning of the line which is for the universe repo (read the comments before each paragraph)
Save and exit.  Then tun

sudo apt-get update
sudo apt-get install x-window-system-core icewm menu wdm mozilla-firefox synaptic xterm

---

### Post by Hopelessness on 2006-06-22
thanks a lot dude

---

### Post by Hopelessness on 2006-06-22
ok i have installed the server install, and typed in
sudo nano /etc/apt/sources.list
but it has come up with this:
sudo: unable to lookup ubuntu via gethostyname()
i have no idea what this means so has anyody got any ideas?

---

### Post by Hopelessness on 2006-06-22
i would really appreciate help here because ubuntu on my laptop is being rendered useless - you don't want me going to windows again do you...?

---

### Post by Hopelessness on 2006-06-23
well i didn't get a reply yesterday so i am hoping i might get one today :)

---

### Post by az on 2006-06-23
Did you set the name of your computer during the install?

Boot into recovery mode and run
hostname ubuntu

that will set the hostname to ubuntu.  Set it to whatever you want.


then run
init 2
to boot into the GUI.

---

### Post by Hopelessness on 2006-06-24
i installed the server version as i was advised by other members of the forum, and set the name as ubuntulaptop

---

### Post by Hopelessness on 2006-06-24
[QUOTE=azz]delete the comment (the "#" symbol) at the beginning of the line which is for the universe repo (read the comments before each paragraph)[/QUOTE]

what is the universe repo?

---

### Post by az on 2006-06-24
[QUOTE=Hopelessness]what is the universe repo?[/QUOTE]
Free-libre software is written by lots of people. The stuff grows like plants.  Never stops and gets bigger all the time.  That's upstream.

People from various distributions take the upstream software and package it (tweak it to work together, compile it and distribute it).  The more packages you support, the harder it is to keep everything in sync and working happily together.  Debian has more than 15 000 packages.  They have a slow release cycle.

Ubuntu only supports a small portion of those packages (Ubuntu is based on Debian).  The other 13 500 or so work fine, but there is no manpower paid by Canonical to support it like there is for the core packages that are in the main repository.  There is a team of community people who maintain these packages.  That's the universe repository.



from /etc/apt/sources.list:
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe 





You would uncomment that line.

---

### Post by platypuss72 on 2007-11-11
i am trying to do the same now ..... a good year later ... could you advice me on which server to load 6.10 or 7.04 ???? 

any idea if all the instuctions still work ????

cheers luke

:confused::confused::confused:

---

### Post by az on 2007-11-12
These links should help:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[https://help.ubuntu.com/community/LowEndSystemSupport](https://help.ubuntu.com/community/LowEndSystemSupport)
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

I don't know if there is any reason to not use the latest 7.10 version.  I would use the alternate cd, since the server cd will install a server kernel and the generic kernel would work better.

---

