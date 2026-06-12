---
title: "Problem Switching Console + Log Out"
date: 2004-12-27
forum: Hardware &amp; Laptops
---

### Post by walter on 2004-12-27
Hi there,

  I've just installed Warty 4.1 on my Dell Inspiron 2650 and am facing the following problems.

1) Cannot switch virtual consoles. Everytime I do this, the screen goes blank and
    I have to do a hard reset.

2) I also encounter an *IMMEDIATE* blank screen if I were to   
    [logout/shutdown/reboot] from 
     a) Gnome session (if I'm logged in)
     b) Gnome login screen (if I'm not logged in) 
 
After reading most of the posts here, I've tried the following:
1) Enable acpi=force in my grub startup
2) Enable acpi=off, apm=power-off, pci=noacpi in different permutations
    in my grub and still the problem remains.
3) I've done 'modprobe apm' from the console but that doesn't work too
  
I'm nearing my wits end and have decided to do an upgrade of the kernel to 2.6.9
but I do not know how to do that. I tried dist-upgrade after dist-update but that 
only allowed me to upgrade to 2.6.8.1-4-386.

My question is this:
  How can I upgrade *only* my kernel to 2.6.9 using apt?


PS: My nVidia graphics card has been successfully installed without any problems.

Dell Settings
--------------------
Available at :   
  [http://reviews.zdnet.co.uk/hardware/notebooks/0,39023984,10001414,00.htm](http://reviews.zdnet.co.uk/hardware/notebooks/0,39023984,10001414,00.htm)

Thanks a lot for any help.

---

### Post by rbran100 on 2004-12-27
Have you checked to see what resolution it is trying to kick into during these times?  It may be that your monitor or graphics card is unable to display that low of a resolution.  Just something to check before you do something hard :-).

---

### Post by iltofa on 2004-12-27
I had the same problem.

Try this:

first install with synaptic or apt get install the nvidia-glx pack
then "sudo nvidia-glx-config enable"
if you obtain an error message about a modified config, try to
modify the /etc/X11/XF86Config-4

where you should have:

Section "Device"
	Identifier	"00e6"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

put "nvidia" instead of "nv"

....

Hope this help, let me know!

Bye
Il Tofa

---

### Post by muzzy on 2004-12-27
[QUOTE=walter]
  How can I upgrade *only* my kernel to 2.6.9 using apt?
[/QUOTE]


```

apt-get install kernel-image-2.6.9-1-686

``` 
or
```

apt-get install kernel-image-2.6.9-1-386

``` 
That's all, folks

---

### Post by walter on 2004-12-27
Hi,

  1) I've checked my screen resolution (1024x768@60Hz) and it runs fine.
  2) I've also checked that my XF86Config-4 and it has a default of "nvidia"
  3) I tried the command to upgrade to kernel 2.6.9 but it doesn't work for me
      I guess I have to read up a lot more on Linux and apt to get it to work.
      
I'm considering moving to Hoary but seems like there are some problems with
the nVidia drivers support there too (after reading the forum) ... So I guess, I'll just hold everything for the moment and just live with the pain of an immediate blank screen. Anyway, the system still functions alright except for this pesky problem.  

I can live with that coz I really *LOVE* Ubuntu.  :D 

Btw, I've also tried the following without success :
 - Commented out "DPMS" and "dri" from my XF86Config file  
after reading this:
  [http://www.rengels.de/computer/linux/linux-nvidia.html](http://www.rengels.de/computer/linux/linux-nvidia.html)

Thanks for all the help!

---

### Post by iltofa on 2004-12-28
May be my reply is silly (I'm a newbie, don't forget!), but I think it can helps:

first: for AthlonXP you should use "linux-image-2.6.8.1-4-k7"

second: 2.6.9 is not a stable release, is it?

third: if you use a terminal window as user, you have to log as root to install

[I]sudo -s
password: ******
[/I]

now you are root...
[I]
apt-get install linux-image-X.X.X[/I]

fourth: the package you are willing to install, must be available and its URI must be listed in archives' list

Bye bye
Il Tofa

---

### Post by walter on 2004-12-28
Thanks for the suggestion but luckily I've found the solution after stumbling upon this thread and doing some tweaking -

  [http://www.nvnews.net/vbulletin/showthread.php?t=15603&page=1&pp=15&highlight=logout](http://www.nvnews.net/vbulletin/showthread.php?t=15603&page=1&pp=15&highlight=logout)
    

My solution is as below:

Steps :
======
1) Go to BIOS to change display type to "LCD" instead of the default "Simul"
    
    [Mine is a Dell Inspiron 2650 laptop whose BIOS is accessed via "F2" func. key]


2) Edit the file "/etc/X11/XF86Config-4" as below:

     Section "Device"
        Identifier      "NVIDIA Corporation NV11 [GeForce2 Go]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "IgnoreDisplayDevices"  "TV"      [COLOR=Red]<------------- Add this line !!![/COLOR]
     EndSection

    [I do not have a TV out on my laptop but still the line above helps.]


Heartfelt thanks to everyone!

---

### Post by roadking6044 on 2007-05-15
> **iltofa said:**
> May be my reply is silly (I'm a newbie, don't forget!), but I think it can helps:

first: for AthlonXP you should use &quot;linux-image-2.6.8.1-4-k7&quot;

second: 2.6.9 is not a stable release, is it?

third: if you use a terminal window as user, you have to log as root to install

[I]sudo -s
password: ******
[/I]

now you are root...
[I]
apt-get install linux-image-X.X.X[/I]

fourth: the package you are willing to install, must be available and its URI must be listed in archives' list

Bye bye
Il Tofa


[Equity Loans Girls Loans solar Equity Line Credit](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

