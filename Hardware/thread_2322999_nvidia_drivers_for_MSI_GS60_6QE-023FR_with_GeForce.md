---
title: "nvidia drivers for MSI GS60 6QE-023FR with GeForceGTX 970M"
date: 2016-05-02
forum: Hardware
---

### Post by GDZ on 2016-05-02
[COLOR=#000000][FONT=Arial]Hi all,[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]A few months ago, I bought a new computer, the MSI GS60 6QE-023FR Ghost Pro with windows 10, and I was able to install ubuntu 15.10 after some tweaking.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]I was able to boot and lauch the install with the nomodeset kernel option. The wifi didn’t work at first but an apt-get update && upgrade fixed it.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have 2 drives, and installed both OS on  the same flash drive, and my home and swap are on the 2nd drive.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I am able to boot to ubuntu, but I have big troubles with the graphics and my nvidia graphic card. My objective is being able to use it for intensive numerical computations. The card is a GeForce GTX 970M.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Right now, when I install the nvidia driver, I can’t lauch Unity, I get sent back to the login screen. I tried installing other desktops. I usually like to use Cinammon, but it keeps falling back to a safe mode. I can only have a decent working environement with Gnome and Metacity. Gnome alone send me back to the login screen as Unity does.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Now when I’m on Gnome (Metacity), the first thing I see is a dialog box with the following message :[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]none of the selected modes were compatible with the possible modes:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Trying modes for CRTC 623[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]CRTC 623: trying mode 1920x1080@0Hz with output at 800x600@75Hz (pass 0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]CRTC 623: trying mode 1920x1080@0Hz with output at 800x600@75Hz (pass 1)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]As a bonus, my battery life is extremely low on ubuntu, with only 1h instead of 3h on windows when I’m doing nothing.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I was hoping that the new ubuntu would solve my problems but it didn’t change a thing. I did an update to 16.04 but I’m still with the same problems.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I also tried some boot options that i found elsewhere, like i915.preliminary_hw_support=1, but I didn’t help.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I would like a real scientific method to make everything work, and not voodoo tricks. And for that, I need some guidance to understand how everything works, where are the informations I need to make right choices, or at least educated guesses, and expert advices on graphics.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]If possible, I would like not to go through the process of reinstalling everything and doing random stuffs, like this guy did : [/FONT][/COLOR][COLOR=#1155cc]_[http://askubuntu.com/questions/692673/getting-ubuntu-working-properly-on-msi-ge62-6qf](http://askubuntu.com/questions/692673/getting-ubuntu-working-properly-on-msi-ge62-6qf)_[/COLOR]

[COLOR=#000000][FONT=Arial]So where do I start ?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]As I’ve seen people using these commands, here they are with there outputs :

[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]> ubuntu-drivers devices[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]== cpu-microcode.py ==[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]driver   : intel-microcode - third-party non-free[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]vendor   : NVIDIA Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]modalias : pci:v000010DEd000013D8sv00001462sd00001158bc03sc02i00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]model[/FONT][/COLOR][COLOR=#000000][FONT=Arial]: GM204M [GeForce GTX 970M][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]driver   : xserver-xorg-video-nouveau - distro free builtin[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]driver   : nvidia-361 - third-party non-free recommended[/FONT][/COLOR]



[COLOR=#000000][FONT=Arial]> dkms status[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]bbswitch, 0.8, 4.4.0-21-generic, x86_64: installed[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]nvidia-361, 361.42, 4.4.0-21-generic, x86_64: installed

[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]With all my love :)[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-05-02
GDZ; Hello;

Here is the process from my understanding.
Does bios hand off to the operating system what the graphic's hardware is, AND does the system recognize the hardware ?
```

lspci -k | grep -EA2 'VGA|3D'

```  to know that the system is aware of both sets of graphic's devices.

Next is there appropriate Nvidia drivers installed - Intel takes care of it's self  ?
```

dpkg -l | grep -i nvidia

```
You will need some means to control which graphic set in in use .,.. nvidia-prime is the recommended utility; make sure it is installs.
Nvidia/Intel require differing config files . Does the switching take place ? Is the proper config file persistent ?
```

cat /etc/X11/xorg.conf

```

Also one can read the log of what is taking place with the X layer :
```

cat /var/log/Xorg.0.log

```
And perhaps what is taking place in the Display Manager's realm:
```

cat .xsession-errors

```

That driver is the interface between the hardware and the kernel. As you can see it is a complex system and many things can be wrong. It is always in the sphere of fault isolation to find the cause.

[INDENT][INDENT]It's 'buntu
[INDENT][INDENT][INDENT]always fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anon24 on 2016-05-07
Just so you know, getting that particular Nvidia card to work right with Ubuntu is pretty much impossible right now. 

 I have the same model and I get severe tearing in Ubuntu when I try to use the Nvidia driver. 

No one here has answers, and neither does anyone on the Nvidia forum.

I would suggest sticking with Windows for now until they fix this.

---

### Post by GDZ on 2016-08-16
Hi, I finally decided to wait a little, and reinstalling everything from scratch worked very well.
So now I have a working ubuntu 16.04 with the following kernel 4.4.0-34-generic and the 361.42 nvidia driver.

Thanks anyway for the help.

---

### Post by Bashing-om on 2016-08-16
GDZ; Outstanding .

Pleased that 16.04 is working our for you . And also, that you provided to the community your experience .

[INDENT][INDENT]one for all
[INDENT][INDENT][INDENT]all for 1
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

