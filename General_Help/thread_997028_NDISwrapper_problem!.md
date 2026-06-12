---
title: "NDISwrapper problem!"
date: 2008-11-29
forum: General Help
---

### Post by nevercroft on 2008-11-29
I'm trying to install NDISwrapper 1.53 in Intrepid, but when I run "make" I get this long line of errors, here's the terminal output:
```
groff@groff-desktop:~$ cd /media/G/ndiswrapper-1.53
groff@groff-desktop:/media/G/ndiswrapper-1.53$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
groff@groff-desktop:/media/G/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/media/G/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic M=/media/G/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /media/G/ndiswrapper-1.53/driver/iw_ndis.o
/media/G/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/media/G/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/media/G/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/media/G/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/media/G/ndiswrapper-1.53/driver'
make: *** [all] Error 2


```

Note that i'm relatively new to linux and if I'm doing something blatantly wrong here don't get too frustrated at me.

---

### Post by cdtech on 2008-11-29
You should uninstall the old using the Package Manager or from a command line:
```
sudo apt-get remove --pruge "package name"
```
Then build the new package.

**UPDATE::.**
To remove a self installed package (not listed in the Package Manager) you would use the command:
```
sudo dpkg --remove --purge "package name"
```

---

### Post by caljohnsmith on 2008-11-29
Have you tried the ndiswrapper that is in the repositories first? Unless that doesn't work, you shouldn't have to download and compile ndiswrapper manually like you are trying to do. Just do:
```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```
And that should install ndiswrapper for you. How about giving that shot and let me know if you run into problems. :)

---

### Post by icanfly0307 on 2008-11-29
I can see that you're trying to compile ndiswrapper from source. Why would you do that when you can get it from the repositories? Just type this a terminal and you should have it up and running:

[FONT="Courier New"]sudo apt-get install ndiswrapper[/FONT]

---

### Post by cdtech on 2008-11-29
I think the repos had the 1.52 and he wants the 1.53, I think thats whats going on. lol

---

### Post by icanfly0307 on 2008-11-29
Wonder why... There really can't be that much of a difference between 1.52 and 1.53 can there?

---

### Post by nevercroft on 2008-11-29
I should have made this clear, I'm dual booting xp and ubuntu on the same hard drive and  trying to get the driver for my wireless card to work on ubuntu that I'm currently using for my windows install. 

I don't have any internet access on my ubuntu install.

I absolutely hate windows, and this is the only thing holding me back from the a complete switch to ubuntu.

---

### Post by caljohnsmith on 2008-11-29
How about just downloading ndiswrapper-utils-1.9 and ndiswrapper-common from:

[http://packages.ubuntu.com](http://packages.ubuntu.com)

Put them on your Ubuntu desktop, and then do:
```
sudo dpkg -i ~/Desktop/ndis*.deb
```
And I think that should work. How about giving that a shot and let me know how it goes.

---

### Post by icanfly0307 on 2008-11-29
To add a bit more detail and ease to caljohnsmith's idea, follow this HOWTO. It worked for me when I didn't have Internet access on Ubuntu. :)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Of course, you can always download the packages from Windows and install them over in Ubuntu. Good Luck!

---

### Post by nevercroft on 2008-11-29
Ok, ndiswrapper is installed now, theres just one more problem
I run modprobe ndiswrapper but this FATAL error comes up.
The documentation said that there is a known bug that states
"FATAL: Module ndiswrapper not found"
but this is different, here's the output

```
groff@groff-desktop:~$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory
groff@groff-desktop:~$ 

```

can this be fixed by just finding ndiswrapper.ko and placing it in that directory?

---

### Post by icanfly0307 on 2008-11-29
Try rebooting your computer. I assume that you didn't do that after installing ndiswrapper. Also the command is *sudo modprobe ndiswrapper* and not *modprobe ndiswrapper*.

Again, don't try this until you reboot your computer.

---

### Post by nevercroft on 2008-11-29
Ok, I rebooted my computer and re-tried sudo modprobe ndiswrapper but I still get this same "ndiswrapper.ko" problem. Any solutions?

---

### Post by cdtech on 2008-11-29
What do you get when you "ls" the location?
```
ls /lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/
```
How did you get the install to work?

---

### Post by nevercroft on 2008-11-29
I installed the three packages at this url:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
under "installing ndiswrapper with another computer with internet access" 

when I run that I get
```

groff@groff-desktop:~$ ls /lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/
groff@groff-desktop:~$ 

```

no output

---

### Post by icanfly0307 on 2008-11-29
Whoa! Hang on. Did you install the drivers for your USB wireless device, already? If not, download the drivers, and install them with:

*sudo ndiswrapper -i **yourdriver.inf***

Then, enter this into the terminal. It might take a while so be patient. :)

*sudo apt-get install --reinstall linux-image-2.6.27-7-generic*

---

### Post by nevercroft on 2008-11-29
Yep I installed my drivers but when I run that I get this:
```

groff@groff-desktop:~$ sudo apt-get install --reinstall linux-image-2.6.27-7-generic
[sudo] password for groff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-image-2.6.27-7-generic is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
groff@groff-desktop:~$ 

```

---

### Post by icanfly0307 on 2008-11-29
What's the output of sudo ndiswrapper -l? And have you tried sudo ndiswrapper -m yet?

---

### Post by icanfly0307 on 2008-11-29
Alright, this seems to be a bug with kernel 2.6.27 and ndiswrapper. Do you have direct (wired) internet access on your lappy right now? I'm asking this because you'll need to downlaod a few things first to get ndiswrapper working.

---

### Post by nevercroft on 2008-11-29
I'm dual booting xp and ubuntu, the wireless card works in windows so I have internet
Here's the output for ndiswrapper -l and - m 
-m i've already done
-l my linksys usb wireless adapter

```

groff@groff-desktop:~$ sudo ndiswrapper -l
[sudo] password for groff: 
netmw245 : driver installed
	device (13B1:0029) present

groff@groff-desktop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

groff@groff-desktop:~$ 

```

---

### Post by icanfly0307 on 2008-11-29
Yeah but you can't sudo apt-get install to Ubuntu from Windows can you? :) Again, can you wire Ubuntu directly to your router?

---

### Post by nevercroft on 2008-11-29
I'm on a desktop, I should have clarified that, my router it downstairs so I can't string a ethernet cable to it, and I'm forced to use wireless.

---

### Post by icanfly0307 on 2008-11-29
Oh well. That's fine. Did you download ndisgtk from Ubuntu's repository like how the HOWTO directed? If you did, install it and run it from System > Administration > Windows Wireless Drivers. Does it open up alright or does throw an error?

---

### Post by nevercroft on 2008-11-29
It opens fine.

---

### Post by icanfly0307 on 2008-11-29
Wow... This is getting complicated. The first thing that I would do in this situation is uninstall NDISwrapper. *sudo apt-get remove ndiswrapper*. Then try reinstalling it from the packages that you downloaded earlier.

---

### Post by icanfly0307 on 2008-11-29
PS. I might not be back until tomorrow because I have to go out somewhere. In the mean time, try googling around your error and see if you find anything. I'll check back soon to see what happens.

Until then, Good Luck! :)

---

