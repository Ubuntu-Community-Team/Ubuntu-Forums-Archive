---
title: "Desktop effects on ubuntu 8.10 64bit"
date: 2009-02-13
forum: Hardware
---

### Post by urke87 on 2009-02-13
[IMG]http://img440.imageshack.us/img440/1653/93034973zo2.png[/IMG]

Please help---:confused:

---

### Post by cdtech on 2009-02-13
Look under "System > Administration > Hardware Drivers" and see if your graphics driver is listed....

---

### Post by urke87 on 2009-02-13
[IMG]http://img520.imageshack.us/img520/8522/hardwaredriversvw1.png[/IMG]

My computer is Notebook hp550, intel GMA x3100...

---

### Post by cdtech on 2009-02-13
Be sure you have "System > Administration > Software Sources" at the Ubuntu Software tab "Proprietary" and "Software restricted by copyright or legal issues" selected.

Then do a:
```
sudo apt-get update
```

---

### Post by urke87 on 2009-02-13
[IMG]http://img16.imageshack.us/img16/45/softwaresourcesce7.png[/IMG]

CONSOLE:

[SIZE="3"][SIZE="1"]Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid Release.gpg
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/main Translation-sr
Ign [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/restricted Translation-sr
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/universe Translation-sr
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/multiverse Translation-sr
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/main Translation-sr
Ign [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/restricted Translation-sr
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/universe Translation-sr
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/multiverse Translation-sr
Get:1 [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security Release.gpg [189B]
Ign [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/main Translation-sr        
Ign [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/restricted Translation-sr
Ign [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/universe Translation-sr
Ign [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/multiverse Translation-sr
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid Release
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates Release
Get:2 [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security Release [44,0kB]
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                          
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/main Packages
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/restricted Packages
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-sr
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/main Sources
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/universe Packages
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/universe Sources
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-updates/multiverse Sources
Get:3 [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/main Packages [66,1kB]
Ign [http://download.skype.com](http://download.skype.com) stable Release         
Get:4 [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/restricted Packages [2066B]
Get:5 [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/main Sources [19,2kB]
Get:6 [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/restricted Sources [563B]
Get:7 [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/universe Packages [25,8kB]
Get:8 [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/universe Sources [5128B]
Get:9 [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/multiverse Packages [1345B]
Get:10 [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com) intrepid-security/multiverse Sources [584B][/SIZE][/SIZE]
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Packages                         
Err [http://download.skype.com](http://download.skype.com) stable/non-free Packages
  404 Not Found [IP: 204.9.165.82 80]
Fetched 165kB in 1s (116kB/s)
W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 204.9.165.82 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cdtech on 2009-02-13
Is it listed in "System > Administration > Hardware Drivers" now?

That error is just for your skype........

---

### Post by urke87 on 2009-02-13
:confused::confused::confused::confused:
[IMG]http://img520.imageshack.us/img520/8522/hardwaredriversvw1.png[/IMG]


](*,)

---

### Post by cdtech on 2009-02-13
Which video card are you using:
```
lspci | grep VGA
```

---

### Post by urke87 on 2009-02-13
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)



My automatic update dont work, maybe that is the reason... it started itself this morning, downloaded something and reported some erors	](*,)

---

### Post by densou on 2009-02-14
Go here: 
[https://launchpad.net/~intel-gfx-testing/+archive/ppa](https://launchpad.net/~intel-gfx-testing/+archive/ppa)

Before you must paste here your xorg.conf
{ digit into a terminal window: *sudo gedit /etc/X11/xorg.conf* }

I assume you're under the generic 'vesa' server, edit these sections into (quite safe):

```
Section "Device"
        Identifier 	"intel"
        Driver     	"intel"
EndSection

Section "Screen"
        Identifier 	"Default Screen"
	Device 		"intel"
EndSection
```

reboot (or press Ctrl+Alt+Bckspace to reboot X)


However, Compiz+Intel doesn't match well, if I suggest to use Metacity instead ;)

---

### Post by urke87 on 2009-02-15
Section "Device"
	Identifier	"intel"
EndSection

Section "Monitor"
	Identifier	"Configured"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"intel"
EndSection


Like that ????

---

### Post by urke87 on 2009-02-15
Nothing !!!!:confused:](*,)  ](*,)

---

### Post by densou on 2009-02-21
are you confused ? 
Have a look to one of my tested xorg.conf 
It should be helpful:
[http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new)

Driver provided with Intrepid by default, doesn't support OpenGL 2.x with Intel video cards 3x00 and 4x00 series

Just add these repositories into Synaptic: (there's a HOW TO on this page)
[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)

---

### Post by OwnName on 2009-09-08
I got the same problem when trying to set up dual monitors, and ended up understanding it's a virtual resolution problem (read: bug).
To enable virtual resolution bigger than 2048, follow the instructions to fix the mesa bug, as suggested by Ludovico Cavedon (thanks!):

[https://bugs.launchpad.net/ubuntu/+s...sa/+bug/146298](https://bugs.launchpad.net/ubuntu/+s...sa/+bug/146298)

briefly, for impatients, what I did on Ubuntu 9.04 Jaunty 64-bit, hp550 and obviously Intel GMA x3100:

1) System > Administration > Software Sources, add both Ludovico's Personal Package Archives entries:
deb [http://ppa.launchpad.net/cavedon/ppa/ubuntu](http://ppa.launchpad.net/cavedon/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/cavedon/ppa/ubuntu](http://ppa.launchpad.net/cavedon/ppa/ubuntu) jaunty main
and accept the warning.

2) Authenticate the PPA:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 426FF7FA

3) Update and install the patched mesa packages:
sudo apt-get update
sudo apt-get install | grep mesa
sudo apt-get install mesa-common-dev mesa-utils libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa

4) Shut down, connect the second monitor and start it up again.

5) Now my virtual resolution is 2560 x 1024:
sudo gedit /etc/X11/xorg.conf

SubSection "Display"
Virtual 2560 1024
EndSubSection

---

