---
title: "Trouble installing Nvidia drivers"
date: 2008-07-19
forum: General Help
---

### Post by darkdude07 on 2008-07-19
I have recently installed Ubuntu 8.04 32-bit( for the first time ^^' ) . I have an NVidia 8500GT graphics card, so I looked for a tutorial to help me install the drivers. I have found and followed this one: [HOWTO: Hardy + NVIDIA drivers]("http://ubuntuforums.org/showthread.php?t=797270")

Everything seems to go well until I have to run the command:

```

sudo sh NVID[tab]

```

Normally, this should start an install process ( I think ). However, I get an error:

```

sh: can't open NVID[tab]

```

I have downloaded the latest Nvidia drivers for Linux, [173.14.09]("http://www.nvidia.com/object/linux_display_ia32_173.14.09.html") and have placed them in the Home directory. 

I hope I included all the information needed. If not, please tell me what else should I post.

Thanks in advance,
darkdude

---

### Post by Vivaldi Gloria on 2008-07-19
Why don't you enable them from 

```
System menu > admin. > hardware drivers
```

---

### Post by darkdude07 on 2008-07-19
There's nothing in that list...

---

### Post by PmDematagoda on 2008-07-19
About the Nvidia driver file, try doing:-
```
sudo chmod +x NV[TAB]
```
and then try executing the installer. But like Vivaldi Gloria mentioned, you may want to try using Hardware Drivers or Envy to install the Nvidia drivers, especially if you are new to Ubuntu.

---

### Post by Vivaldi Gloria on 2008-07-19
> **darkdude07 said:**
> Everything seems to go well until I have to run the command:

```

sudo sh NVID[tab]

```


You write

```

sudo sh NVID

```

and press the TAB key at that point to autocomplete the name. To be able to do this you must first cd to the folder where the script is. If it's in your home folder than "cd ~" will take you there. Now write the command and press the tab key to autocomplete the name. Then press enter.

---

### Post by darkdude07 on 2008-07-19
Darn.. I didn't know "tab" actually meant pressing TAB... :oops:

---

### Post by Vivaldi Gloria on 2008-07-19
> **darkdude07 said:**
> Darn.. I didn't know "tab" actually meant pressing TAB... :oops:

It happens. :-)

TAB key autocompletes commands and names. Very useful.

Have fun.

---

### Post by darkdude07 on 2008-07-19
Thanks for the support, but now I have another problem.. Actually two, since I tried two ways to install the drivers. 

The NVidia installer seems to require a precompiled kernel interface. When it tries to generate it is says it's missing some libc header files and the installation cannot be complete.

I also tried using Envy. I installed it, but I can't find a way to actually use it, since it doesn't appear in the list of all installed applications. :(

---

### Post by jerome1232 on 2008-07-19
As far as the NVIDIA installer goes, there is no precompiled one for Ubuntu, so it will try and compile one itself, to do that it requires the build-essential package. to install it:

```
sudo apt-get install build-essential
```

although using nvidia's installer is really only needed if you absolutely need the latest nvidia drivers. Plus it's a pain 'cuz you have to redo it every kernel update.

---

### Post by darkdude07 on 2008-07-19
So if nvidia's installer isn't that good, what else could I use?
( I don't really need the latest drivers )

---

### Post by jerome1232 on 2008-07-19
I would just use Ubuntus, to do that make sure restricted repositories are enabled

System>>Administration>>Software Sources  Check Restricted

```
sudo apt-get update
sudo apt-get install nvidia-glx-new
```

or if you have an older card like a TNT or geforce1 or 2
```
sudo apt-get install nvidia-glx-legacy
```

---

### Post by nikgare on 2008-07-19
I too have a 8500GT
I installed **nvidia-glx-new** via synaptic and everything worked fine

---

### Post by darkdude07 on 2008-07-19
Using the commands suggested by jerome1232 brings up lots of errors. For some weird reason, I can't access the wireless internet with Ubuntu. ( I'm in XP right now and keep rebooting into Ubuntu to test out the various solutions )

---

### Post by jerome1232 on 2008-07-19
can you post the output?

Or is it just not hitting the repos.

---

### Post by darkdude07 on 2008-07-19
Doesn't sudo apt-get update try to update the software from the internet? Because I don't have internet in Ubuntu...

And those errors said something about not being able to connect to a server or something...

---

### Post by jerome1232 on 2008-07-19
yeah they get everything from internet, I'd suggest getting a separate thread going for you're wireless and then install that driver

---

### Post by darkdude07 on 2008-07-19
I have some tutorials on getting wireless to work. 
Anyway, I was hoping to find an off-line way to install the drivers from the file I downloaded from the Nvidia site through windows.

---

### Post by darkdude07 on 2008-07-19
( I'm terribly sorry for double-posting. My internet is slow and I can't seem to be able to delete the duplicate post )

---

### Post by jerome1232 on 2008-07-19
If you goto that site you can manually download packages then transfer them to Ubuntu via usb drive or cd.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

problem with that is apt-get automatically resolves dependencies, that will only tell you what's need when you attempt to install it.

build-essential is actually a virtual package that downloads alot of other packages so i'm not sure what the actuall packages you need to build the nvidia driver
Iit's probably easier to download that nvidia-glx-new package hopefully it doesn't have dependencies, if it does they should be relatively few.

---

### Post by darkdude07 on 2008-07-20
I'll probably buy a reeeally long ethernet cable to reach my computer all the way from the router and install what I need ( video drivers and make the wireless network work ) because the wireless network setup tutorial for my wireless card requires an ethernet connection anyway...

---

