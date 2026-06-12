---
title: "NVidia GeForce4 on 8.10"
date: 2008-11-01
forum: Hardware
---

### Post by carloshiga on 2008-11-01
[COLOR="Blue"]Hi friends,

it seems that a lot of people are having trouble with the NVidia card after upgrade to 8.10. I am one of these people and I've search de entire forum for answers... I already tried to

- Install the driver manually as I did in previous versions of Ubuntu which says "Error: Unable to build the NVidia kernel module".
- Install using Envy. I though that it was going to work, but when I restarted my computer it halts and I'm forced to restore the old configuration (of xorg.conf, i guess).
- I did a full update of the system.
- I did that "third part software" thing... did not work too.
:(

So, I think that this problem don't have a solution yet because the video card is not compatible with the new kernel. The only thing I have to do is wait...
Am I right or somebody found the solution (perhaps in other topic)?
My video card is a NVidia GeForce4 MMX 440 AGP8X

Thanks![/COLOR]

---

### Post by vmatherly on 2008-11-01
I am also having an issue with that same card. I tried the driver in the repos, EnvyNG, and the installer on the nvidia site and got the same results :confused:

I am sure a solution will surface soon. I have faith in the ubuntu community :)

---

### Post by TiberiusDRAIG on 2008-11-01
I installed the beta Nvidia driver for 8.10 and it kind of worked except I lost all of the decorations on my windows, and for some reason I can't change theme managers anymore. Can't work out how to revert back to the more stable nv driver without killing my system >_<

---

### Post by vmatherly on 2008-11-01
> **TiberiusDRAIG said:**
> I installed the beta Nvidia driver for 8.10 and it kind of worked except I lost all of the decorations on my windows, and for some reason I can't change theme managers anymore. Can't work out how to revert back to the more stable nv driver without killing my system >_<

You just need to edit your /etc/X11/xorg.conf file 

change 

```

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 4"
EndSection

```

to 

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 4"
EndSection

```

or at the command line run 

```
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by solitaire on 2008-11-03
The new Ubuntu packaged Nvidia drivers have been put in the repository today!

The drivers should be working now. I installed it using EnvyNG an hour ago and it's fine, I'm not sure about Compiz since I've removed it (my graphics card can't handle it ):(

---

### Post by vmatherly on 2008-11-04
> **solitaire said:**
> The new Ubuntu packaged Nvidia drivers have been put in the repository today!

The drivers should be working now. I installed it using EnvyNG an hour ago and it's fine, I'm not sure about Compiz since I've removed it (my graphics card can't handle it ):(

Still not working for me

---

### Post by ergosteur on 2008-11-07
I have a GeForce4 4200 Go (Dell mobile version). The Hardware Drivers utility doesn't list the nvidia driver. I tried using apt-get to install nvidia-glx-96, but got 

The following packages have unmet dependencies:
  nvidia-glx-96: Depends: nvidia-96-kernel-source (>= 96.43.05) but it is not going to be installed

nvidia's binary installer fails to compile the kernel....

Everything was working fine in hardy (1920x1200, compiz, vga out).

---

### Post by Spuz on 2008-11-10
I have a Geforce4 Ti 4800 and was having the same problem, I just changed my session to KDE 4.1 and uninstalled the Hardware Drivers program, launched EnvyNG, it downloaded 96 for me, I clicked apply, restarted, reinstalled Hardware Drivers (while in the ubuntu session), and after that I believe an update appeared, I downloaded all the updates, and then launched Hardware drivers, and there they were, the drivers needed, just installed them and restarted and everything seemed to works.

---

### Post by vmatherly on 2008-11-10
There is a Beta Driver in the repos. See link for instructions on how to enable it:

[http://ubuntuforums.org/showpost.php?p=6102187&postcount=10](http://ubuntuforums.org/showpost.php?p=6102187&postcount=10)

the Nvidia drivers work with my GeForce4 440 however compiz doesn't work correctly. Hopefully this will be fixed once the driver is released.

---

### Post by TiberiusDRAIG on 2008-11-10
I've got my 4400ti working with the beta drivers and compiz *seems* to be working fine for me, what problems are you having with it? The only thing i ran into initially was that window decorations didn't show up, but it was an easy fix.

---

### Post by waza456 on 2008-11-10
i also have a GeForce4 MX 440. certain programs like googleearth won't run correctly, neither will compiz. i'm not sure what exactly the problem is, but i think it has to do with 3d acceleration not being enabled. can anyone tell me which drivers i should install and how to do it? btw, the only entries in my xorg.conf are the following
> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

and the > sudo dpkg-reconfigure xserver-xorg doesn't change a thing. should i do it manually? thanks in advance

---

