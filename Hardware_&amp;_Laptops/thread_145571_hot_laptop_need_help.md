---
title: "hot laptop need help"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by pestypest on 2006-03-16
im just wondering if i can monitor my laptops temp. and if anyone knows the "normal" temp i should look for in a laptop.

Amd X2 4600+
2 GB Ram
100GB HD  win
60GB HD breezy
7800 Go Gtx

any programs and such thanks :D

---

### Post by cbudden on 2006-03-16
If you do acpi -V in a terminal you should get your CPU temp.

---

### Post by earobinson on 2006-03-16
acpi can give you battery temp - man acpi for more info

i know there are others cant seem to find them right now ... ill look later. just got a laptop 2 btw

---

### Post by pestypest on 2006-03-16
[QUOTE=cbudden]If you do acpi -V in a terminal you should get your CPU temp.[/QUOTE]
sweet thanks, man im running hot 58.3 C thats not good:(

---

### Post by earobinson on 2006-03-16
earobinson@NaN:/media/data/work/array/call up 3/addns_callup_3$ acpi -V
     Battery 1: charging, 65%, 00:38:08 until charged
     Thermal 1: ok, 47.0 degrees C
  AC Adapter 1: on-line


gives you something to compair 2 ... been on all day but not doing much

---

### Post by pestypest on 2006-03-16
[QUOTE=earobinson]earobinson@NaN:/media/data/work/array/call up 3/addns_callup_3$ acpi -V
     Battery 1: charging, 65%, 00:38:08 until charged
     Thermal 1: ok, 47.0 degrees C
  AC Adapter 1: on-line


gives you something to compair 2 ... been on all day but not doing much[/QUOTE]
jason@jason:~$ acpi -V
     Battery 1: charged, 100%, rate information unavailable.
     Thermal 1: ok, 56.0 degrees C
  AC Adapter 1: on-line
i had to reboot once and it went down 2 from when i first ran the command. any suggestions on how to lower the temp?

---

### Post by engineering.concepts on 2006-03-19
Hello,
Does anyone know of a GUI that would display the CPU Temp information? 
Should I be concerned about by IBM T22 Laptop temp?
acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 85.0 degrees C
  AC Adapter 1: on-line

It say's that the Thermal is OK, but everyone is reporting 45C - That is starting to scare me.......:confused:

---

### Post by sn123 on 2006-03-19
[QUOTE=engineering.concepts]Hello,
Does anyone know of a GUI that would display the CPU Temp information? 
Should I be concerned about by IBM T22 Laptop temp?
acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 85.0 degrees C
  AC Adapter 1: on-line

It say's that the Thermal is OK, but everyone is reporting 45C - That is starting to scare me.......:confused:[/QUOTE]

If am not wrong the maximum cpu temperature for Intel Pentium M is like 100 deg C, so that way 85 should be within limits but I don't know whether it really should be 85 degrees, even mine (a Dell) averages between 40-48.

S

---

### Post by byen on 2006-03-19
If you guys are looking for a laptop temperature monitor that sits on the taskbar...here is [one]("http://www.gnomefiles.org/app.php?soft_id=1065"). Works well and does the job.

---

### Post by engineering.concepts on 2006-03-19
I download the application, but I am getting this error -- 
maximus@Maximus:~/CPUmonitor$ tar xzf laptoptemp-0.5.0.tar.gz
maximus@Maximus:~/CPUmonitor$ cd laptoptemp-0.5.0
maximus@Maximus:~/CPUmonitor/laptoptemp-0.5.0$ ./configure --prefix /usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... configure: error: Package requirements (pygtk-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the PYGTK_CFLAGS and PYGTK_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
maximus@Maximus:~/CPUmonitor/laptoptemp-0.5.0$ make
make: *** No targets specified and no makefile found.  Stop.
maximus@Maximus:~/CPUmonitor/laptoptemp-0.5.0$ sudo make install
make: *** No rule to make target `install'.  Stop.

I know I hve Python 2 installed I just checked my Synaptic package manager - any help would be appreceiated.
Thanks,

---

### Post by Greg2 on 2006-03-20
[QUOTE=engineering.concepts]I download the application, but I am getting this error -- 
maximus@Maximus:~/CPUmonitor$ tar xzf laptoptemp-0.5.0.tar.gz
-snip-
[/QUOTE]
Is there some reason you don't install the Debian/Ubuntu package/deb? It works very well on my laptop. :)

---

### Post by pestypest on 2006-03-20
[QUOTE=Greg2]Is there some reason you don't install the Debian/Ubuntu package/deb? It works very well on my laptop. :)[/QUOTE]
Greg, when it comes to installs im a noob. wondering if u could give a short HOW-TO on this. also was wondering if this works with AMD 64 bit systems? thanks

---

### Post by Greg2 on 2006-03-20
[QUOTE=pestypest]Greg, when it comes to installs im a noob. wondering if u could give a short HOW-TO on this. also was wondering if this works with AMD 64 bit systems? thanks[/QUOTE]
Download the laptoptemp-0.6.0-1_all.deb from here:
[http://infinito.f2o.org/laptoptemp/](http://infinito.f2o.org/laptoptemp/)
to your home directory.

Then in terminal do:```

sudo dpkg -i laptoptemp_0.6.0-1_all.deb
killall gnome-panel
```After your panel reloads; right click on your panel and click on 'Add to Panel', go to 'System & Hardware' and select 'Laptop Temperature Monitor', click on Add. Now you can right click on your monitor and move it to your desired location, and set your preferences.

For the record, mine runs about 53 degrees C without any problems.

I'm not 'sure' if this will work on your 64 bit system... but I don't see a problem in trying it out.

---

### Post by engineering.concepts on 2006-03-20
Thanks Greg,
That tutorial is what I needed, My (very hot CPU @85 degrees C) is being updated every few seconds on the panel. \\:D/ 

The original reason I did not install the ubuntu version is b/c there was no tutorial for the install, I have been using WinXP for the last few years, but I am excited to convert to UBUNTU, (There is a lot more command prompt entry the Windows - but I have made a promise to keep UBUNTU on my laptop for at least 2 months, and every day I am enjoying the experience more and more!!!)  

Thanks for everyone in the forums for putting up with my silly noobie questions and getting my system up and running ASAP :-D

---

### Post by Greg2 on 2006-03-21
[QUOTE=engineering.concepts]
My (very hot CPU @85 degrees C) is being updated every few seconds on the panel. [/QUOTE]
I would be 'very' concerned if my laptop cpu was running at 85 degrees C / 185 degrees F!

I would recommend doing a search for IBM T22 (with whatever cpu you have) and find the safe operating temperatures for it.

I would also check to be sure that your cpu cooling fan is running, and runs at full speed when needed... you may need to use a boot parameter (or two) to make your fan/fans work properly?

I don't have an IBM so I can't give you any 'specific' help on this. I would however suggest checking out this for more info:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM)
It suggest trying 'acpi=off nolapic' as a boot parameter (on a Hoary install?), if you haven't already done so. I would also suggest trying apm=on (with the others) 'if' you are still having fan problems.

If you are not sure how to add a boot parameter do:```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
sudo gedit /boot/grub/menu.lst
```now you have a backup file, and you can safely edit your kernel boot line.

Please search 'kernel boot parameters' for more info.

---

### Post by engineering.concepts on 2006-03-24
[QUOTE=Greg2]I would be 'very' concerned if my laptop cpu was running at 85 degrees C / 185 degrees F!

I would recommend doing a search for IBM T22 (with whatever cpu you have) and find the safe operating temperatures for it.

I would also check to be sure that your cpu cooling fan is running, and runs at full speed when needed... you may need to use a boot parameter (or two) to make your fan/fans work properly?

I don't have an IBM so I can't give you any 'specific' help on this. I would however suggest checking out this for more info:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM)
It suggest trying 'acpi=off nolapic' as a boot parameter (on a Hoary install?), if you haven't already done so. I would also suggest trying apm=on (with the others) 'if' you are still having fan problems.

If you are not sure how to add a boot parameter do:```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
sudo gedit /boot/grub/menu.lst
```now you have a backup file, and you can safely edit your kernel boot line.

Please search 'kernel boot parameters' for more info.[/QUOTE]
Hi Greg, 
Thanks for the additional info, I started to dig on the Ubuntu forums for hot laptops and after searching on my computer, I found out that I had messed up an install of oostay (tried to get open office to start faster) and oostay was taking up 100% of my resources 100% of the time!!! I thought my CPU monitor was broken because it ALWAYS showed 100% cpu usage. 
Once I killed oostay and removed it from the start up my laptop was able to relax a little bit a my temp now ranges from 60 deg C to 73 deg C (It will only stay at 73 deg C for a few seconds if I have a few torrents open and loading up)

I am very impressed with UBUNTU as I have been running like this for 2 weeks and complaining that UBUNTU is slow - I am amazed that I could even open any of my programs and work correctly (WINXP would have killed itself!!!)

My laptop is much faster now and much cooler!

[COLOR="Red"]A BIG THANKS TO EVERYONE ON THE UBUNTU FORUM< WITHOUT EVERYONE'S HELP (AND OF COURCE GREG'S) I would have cooked my laptop in another few days!!![/COLOR]

---

