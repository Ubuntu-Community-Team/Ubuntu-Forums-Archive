---
title: "HElP WITH DRIVERS"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by dharmil007 on 2009-10-07
i m using UBUNTU 9.04.
Just installed few days back.

But i m having problem with its VIDEO-DRIVERS.
i M having nVIDIA GeForce 7100GS video-card.

For that i got the drivers also, but i do not know how to INSTALL THAT DRIVERS.

THe drivers have an extension [FONT=Georgia][SIZE=3]*.run*[/SIZE][/FONT]

When i try to open it, it opens in something diff format.
i do not know how to install it.

Can anybody PlS. help me out with these problem ?

---

### Post by tommcd on 2009-10-07
Ubuntu has the nvidia drivers in the Ubuntu repositories. First, try going to: system > administration > hardware drivers, and see if it offers you to install the nvidia driver and enable it. Then reboot.
If this doesn't work we can try to install the driver manually.

And welcome to the Ubuntu forums!

---

### Post by dharmil007 on 2009-10-07
[I]> **tommcd said:**
> Ubuntu has the nvidia drivers in the Ubuntu repositories. First, try going to: system > administration > hardware drivers, and see if it offers you to install the nvidia driver and enable it. Then reboot.
If this doesn't work we can try to install the driver manually.

And welcome to the Ubuntu forums!

i Have tried tAt too, but it doesnt have it.
i Need to install it manually.
So can u pls. tel me the method how to install it manually ?


[/I]

---

### Post by tommcd on 2009-10-07
> **dharmil007 said:**
> 
i Have tried tAt too, but it doesnt have it.
i Need to install it manually.
So can u pls. tel me the method how to install it manually ?
I was afraid of that. There was another thread around here recently about the nvidia 7100.
[http://ubuntuforums.org/showthread.php?t=1270112](http://ubuntuforums.org/showthread.php?t=1270112)
He did not have the GS version though. It was the nvidia 7100.
From what I managed to learn about the nvidia 7100 series in Ubuntu, it seems the best way to install the nvidia driver for the 7100 series is to use the driver from nvidia.com. The easiest way for you to use the driver from nvidia.com is to install **envyng**. This is a program that will automatically download and install the proper nvidia driver for your video card. It will also reinstall the driver whenever there is a kernel update.
To get envyng open up synaptic package manager, click the reload button to update the repos, and search for envyng and install it. 
See this site to learn how to use envyng:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Hope this helps.

---

### Post by dharmil007 on 2009-10-07
[I]> **tommcd said:**
> I was afraid of that. There was another thread around here recently about the nvidia 7100.
[http://ubuntuforums.org/showthread.php?t=1270112](http://ubuntuforums.org/showthread.php?t=1270112)
He did not have the GS version though. It was the nvidia 7100.
From what I managed to learn about the nvidia 7100 series in Ubuntu, it seems the best way to install the nvidia driver for the 7100 series is to use the driver from nvidia.com. The easiest way for you to use the driver from nvidia.com is to install **envyng**. This is a program that will automatically download and install the proper nvidia driver for your video card. It will also reinstall the driver whenever there is a kernel update.
To get envyng open up synaptic package manager, click the reload button to update the repos, and search for envyng and install it. 
See this site to learn how to use envyng:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Hope this helps.

[/I]
[FONT=Georgia][SIZE=3]What i m telling u is that i Have the driver with me.[/SIZE][/FONT][SIZE=3]
[/SIZE][FONT=Georgia][SIZE=3]But it is in[/SIZE][/FONT][FONT=Book Antiqua][SIZE=4]*** .run***[/SIZE][/FONT][FONT=Georgia][SIZE=3] format, so it is not opening.[/SIZE][/FONT][SIZE=3]
[/SIZE][FONT=Georgia][SIZE=3]When i refered to HELP nVIDIA PAGES, it told that i need to install the driver through TERMINAL.[/SIZE][/FONT][SIZE=3]
[/SIZE][FONT=Georgia][SIZE=3]So its  a BiG problem, 'coz i dont know TERMINAL.[/SIZE][/FONT][SIZE=3]
[/SIZE][FONT=Georgia][SIZE=3]So can u help me with it[/SIZE][/FONT]

---

### Post by tommcd on 2009-10-07
I suggested using envyng because I thought it would be easier for you. If you want to install the driver the manual way in the terminal, here it is:
First update the repos:
```
sudo apt-get update
```
Then install the build-essential package and the linux headers for your kernel:
```
sudo apt-get install build-essential linux-headers-$(uname -r)

```
Make sure the nvidia driver you downloaded is in your home directory.
Then hit ctrl + alt + F2 to get to a virtual terminal, and login.
Then stop the X-server:
```
sudo /etc/init.d/gdm stop
```
Then backup your xorg.conf just for safety:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
If it complains that there is no such file, don't worry about it.
Then run the nvidia driver:
```
sudo sh NVIDIA
```
Then hit the **tab** key. This should autocomplete the name of the nvidia driver. Then hit enter. You could also just type the exact name of the driver you downloaded and then hit enter.
When it asks you if you want to download the kernel modules from nvidia.com, answer no. It never finds them anyway, so there is no point in answering yes. It will then build the modules for you.
Then when it asks you if you want to let the installer configure the driver, answer yes.
When it is all finished, reboot the Computer:
```
sudo reboot
```
When you reboot the driver should be working. To check this run in terminal:
```
glxinfo | grep -i direct
```
It should answer yes.
Note that you will have to reinstall the nvidia driver whenever there is a kernel update if you do it the manual way I just described.

---

### Post by dharmil007 on 2009-10-07
HEy if i want to leanr about the TERMINAL of UBUNTU, where can i learn it ?

---

### Post by Mark Phelps on 2009-10-07
The "terminal of Ubuntu" is an app that opens a window containing a command line interface, from which you can enter GNU/linux commands.

Suggest you look for online info or books about using Linux from the command line.  But be prepared for a LOT of information.  It's based a lot on UNIX and is not designed to be user-friendly (as in point-and-click).

---

### Post by tommcd on 2009-10-08
> **dharmil007 said:**
> HEy if i want to leanr about the TERMINAL of UBUNTU, where can i learn it ?
If you want to learn how to use the terminal in linux here is a great beginner tutorial:
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
Work your way through the tutorial. You can safely practice the commands by creating some test files and folders in your home directory. This is how I began to learn terminal commands.
Here is a more in depth tutorial that gets into writing scripts and stuff. (Something I should take the time to learn!):
[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)
It is smart move that you want to learn how to use the terminal. This will help you learn linux and will serve you well in the long run. If you ever try out other distros, a knowledge of terminal commands is a big help, since the commands are more or less consistent between distros. Plus, using the terminal is usually faster and more versatile than doing the same things with graphical tools.

So did you get the nvidia driver installed ok?

---

### Post by dharmil007 on 2009-10-08
[I]> **tommcd said:**
> If you want to learn how to use the terminal in linux here is a great beginner tutorial:
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
Work your way through the tutorial. You can safely practice the commands by creating some test files and folders in your home directory. This is how I began to learn terminal commands.
Here is a more in depth tutorial that gets into writing scripts and stuff. (Something I should take the time to learn!):
[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)
It is smart move that you want to learn how to use the terminal. This will help you learn linux and will serve you well in the long run. If you ever try out other distros, a knowledge of terminal commands is a big help, since the commands are more or less consistent between distros. Plus, using the terminal is usually faster and more versatile than doing the same things with graphical tools.

So did you get the nvidia driver installed ok?

[/I][FONT=Book Antiqua][B]oh yes.
Thanks for your help.
But i dint try it your way, i just gone to PREFERENCES>APPEREANCE>VISUAL EffECTS.
& in that selected EXTRA.So it automatically found the driver & installed it for me.
[COLOR=Red][U][SIZE=4]
Hey but THANKS FOR your help.[/SIZE][/U][/COLOR][/B][/FONT]

---

### Post by dharmil007 on 2009-10-08
Hey i wanna ask 1 more QUESTION.

i Have 2 OPERATING SYSTEMS.
1} Win 7
2} UBUNTU 9.04
& Recently i updated UBUNTU.

So now Whenver i start my PC, There it shows 6 CHOICES of OSes.
They are :
1} UBUNTU KERNEL 9.0.15
2} UBUNTU KERNEL 9.0.15 {recovery mode}
3} UBUNTU KERNEL 9.0.14
4} UBUNTU KERNEL 9.0.14 {recovery mode}
5} UBUNTU MEMTEST+
6} WIN 7.

i Dont want all these options.

i Just WANT 2 SIMLE THINGS. i.e 
1}  UBUNTU 
2} WIN 7.

How can i do this thing ?

Can anybody PlS. help me out

---

### Post by tommcd on 2009-10-09
> **dharmil007 said:**
> 
i Just WANT 2 SIMLE THINGS. i.e 
1}  UBUNTU 
2} WIN 7.
How can i do this thing ?

This is normal. Whenever there is a kernel update for Ubuntu, the newest kernel is placed at the top with the older kernels after that. All kernels include a recovery mode option to be used for troubleshooting and system recovery.
Memtest is there as an option also.
It is good to have at least 1 backup kernel in the grub menu. If a new kernel won't boot or causes problems you can always revert to the older kernel. Leaving the recovery mode option there is a good idea also in case you ever need it.

If you want to get rid of the memtest option, you can edit /boot/grub/menu.lst with a text editor. An easy one is gedit. You can launch it with root privileges like this:
```
gksudo gedit /boot/grub/menu.lst
``` 
Then scroll down to this section:
```

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

```
and change the last line #memtest86=true to #memtest86=false.
To stop grub from creating recovery mode options with kernel updates, go to this section:
```

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true 

``` 
and change the last line #alternative=true to #alternative=false.
In both cases leave the hashes (#). Don't remove them. (FYI, removing the hashes is called "uncommenting" in linux).
To have just 1 Ubuntu kernel present in the list, go to this section:
```

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

```
And change the last line #howmany=all to #howmany=1
Save and exit the file.
You can then run **sudo update-grub** in the terminal and when you reboot the grub menu should be as you want it.
Again, I would recommend leaving at least 1 extra kernel (eg, howmany=2) and the recovery mode options there, but it is your system and your choice.
Here is a good tutorial on grub:
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)
Before you edit grub's menu.lst you should make a backup copy for safety like this in the terminal:
```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak 
```

---

