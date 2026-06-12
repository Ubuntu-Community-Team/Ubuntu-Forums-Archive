---
title: "Pny / nvidia video card"
date: 2018-03-16
forum: Hardware
---

### Post by mikealte2468 on 2018-03-16
I recently bought a new pc with the intention of installing Ubuntu 64, 16.04 LTS. Linux is installed but I am limited to 640 x 480 resolution. When I open 'system settings, display' all I get is part of the screen and there is no way to change resolution. 

Previously I found some information about installing a new driver on the NVIDIA web site - doesn't appear to be there anymore.

The PNY model # is GMG103WN3H2CX1KTP4AFA and NVIDIA # is VCGGT10302PB.

Any suggestions would be appreciated.

Thanks,

Mike

---

### Post by Yellow Pasque on 2018-03-16
It's a GT1030.
You can get the 390.xx driver using: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by SeijiSensei on 2018-03-17
Did you run the Driver Manager application yet?  It should find the video card and download and install the proper packages for it automatically.  I'd do that before taking the PPA route Temüjin suggests.

---

### Post by Yellow Pasque on 2018-03-17
> **SeijiSensei said:**
> Did you run the Driver Manager application yet?  It should find the video card and download and install the proper packages for it automatically.

I don't think the info in 16.04's driver database is new enough to detect the GT1030. Don't quote me on that though.

---

### Post by mikealte2468 on 2018-03-21
I appreciate the responses but I'm somewhat of a newbie and have difficulty understanding Linux lingo.

It would be appreciated if anyone could provide a plain language response so I can get this machine up and running.

Would it help if I downloaded a newer version of Ubuntu?

Mike

---

### Post by Bashing-om on 2018-03-21
mikealte2468; Hey hey ...

> 
Would it help if I downloaded a newer version of Ubuntu?


Maybe, but - for now how about we work with what you have ; 16.04.4 ( to be ??) . It is recommended that the LTS ( Long Term Support) - 16.04 - be the operating system installed for a  new user to linux.

Let's install the 390 version nvidia driver on your current install;
Giving directions for a terminal installation is prefered, though one may also do so from the GUI .. terminal is universal for all observers and users.

Activate a terminal from the desktop: key combo ctl+alt+F1 
copy and paste these terminal commands:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall
sudo reboot

```

when you come back up from the reboot, I do expect that the system chose the 390 version driver to "autoinstall' .

[INDENT]ubuntu
[INDENT][INDENT]easy as falling out of bed wide awake
[/INDENT][/INDENT][/INDENT]

---

### Post by mikealte2468 on 2018-03-22
Thank you Bashing-om,

It all worked!!

Mike

---

### Post by Bashing-om on 2018-03-22
mikealte2468; Great !

Pleased it was an easy solution.
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

