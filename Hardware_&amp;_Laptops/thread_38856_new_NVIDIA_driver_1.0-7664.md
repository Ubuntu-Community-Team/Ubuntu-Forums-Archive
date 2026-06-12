---
title: "new NVIDIA driver 1.0-7664"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by thierry13 on 2005-06-02
a new nvidia driver had been released yesterday, does somebody know how to install it?

thanks

Thierry

---

### Post by oritpro on 2005-06-04
Well, let me start off by saying that I just got done recovering from trying to install the new nvidia drivers over the nvidia drivers I had installed through synaptic, which fried OpenGL. So, installation will depend on what driver you currently have and how it was installed. 

The new drivers are giving me an additional 1000 fps on glxgears though, around 7500 fps on a 6600gt which isn't to bad. UT2004 already ran smooth but is running even better now so it was worth the effort.

Let me know what your setup is, if you are currently running an accelerated nvidia driver, how it was installed and I'll try and help you out.

---

### Post by crane on 2005-06-04
I was wondering this as well. When I tried to install the driver I was told I needed the kernel source. 
I tried apt-get install kernel-source and it install source for 2.4!!! ](*,)

---

### Post by hardwarder on 2005-06-04
I finally got it installed. What I installed was the linux-headers-2.6.10-5 package. After that, the installation ran smoothly.

---

### Post by thierry13 on 2005-06-06
I finally installed it too but it doesn't work anymore after a reboot, seems I need to reinstall it each time or go back to driver nv

what's wrong?

thanks

---

### Post by Khannie on 2005-06-07
[QUOTE=thierry13]I finally installed it too but it doesn't work anymore after a reboot, seems I need to reinstall it each time or go back to driver nv

what's wrong?

thanks[/QUOTE]

Did you get a resolution to this? 

Mine seemed to install (though I had to do it through "make install") and I got a 3% increase in my glxgears score but it's not working any more. I had to apt-get uninstall something too (can't remember what now but I'm not at the machine).

---

### Post by thierry13 on 2005-06-08
I still have the problem, I have no choice to stay without 3d accel for the moment, (I have a 6200FX AGP which is only recognized by the new driver!)

if anyone as a solution, please help me !

bye

---

### Post by gcranston on 2005-06-08
[QUOTE=thierry13]I finally installed it too but it doesn't work anymore after a reboot, seems I need to reinstall it each time or go back to driver nv

what's wrong?

thanks[/QUOTE]


in /etc/X11/xorg.conf under modules did you comment out
Load "GLCore"       and
Load "dri"

as well as add in

Load "glx"    ?


try this then check 

/usr/share/doc/NVIDIA_GLX-1.0/README.txt


Good luck.

---

### Post by thierry13 on 2005-06-09
I already checked that, itt's ok because the driver works after installation, 

the problem is that kdm doesn't start anymore after a reboot

---

### Post by thierry13 on 2005-06-09
Actually I found a problem, I have a message during the boot which says:

REMOVING NVIDIA TLS links...

after that, I have no more the libnvidia.so.1.0.7664 in /usr/lib and /usr/lib/tls

but I don't know WHAT is doing that...

any ideas ?

---

### Post by dtessier on 2005-06-09
[QUOTE=thierry13]Actually I found a problem, I have a message during the boot which says:

REMOVING NVIDIA TLS links...

after that, I have no more the libnvidia.so.1.0.7664 in /usr/lib and /usr/lib/tls

but I don't know WHAT is doing that...

any ideas ?[/QUOTE]

There's an init script called nvidia_glx which does this. If you're using a self-installed driver, it will interfere. To get rid of it, simply type ```
sudo update-rc.d -f nvidia_glx remove
```

---

### Post by gcranston on 2005-06-09
Sorry, I'm out

---

### Post by thierry13 on 2005-06-10
Thanks you, now it works perfectly !

This new driver is very cool because it allows overclocking to boost 2d and 3d performance, good job nvidia !

bye

---

### Post by MemoryDump on 2005-06-10
[QUOTE=thierry13]a new nvidia driver had been released yesterday, does somebody know how to install it?

thanks

Thierry[/QUOTE]

so where can I get this new driver? and how's the best way to install it from start to finish? I just applied the latest kernel release today (using apt-get) so I don't know how that'll affect anything. I haven't rebooted yet. (oh and I'm using the old nvidia drivers right now I got from apt-get)

thxs
-MD

---

### Post by thierry13 on 2005-06-10
So,
1/Get the driver from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

2/you have to run kynaptic by the menu and remove all the nvidia related programs, nvidia-glx and so on.
+install linux-headers-yourkernel (see with uname -r)

3/CTRL-ALT-F1
4/sudo /etc/init.d/kdm stop for kde or
   sudo /etc/init.d/gdm stop for gnome

5/sudo sh NVIDIA-Linux-x86-1.0-7664-pkg1.run

6/update /etc/X11/xorg.conf and change driver "nv" by driver "nvidia"

7/sudo /etc/init.d/kdm start (or gdm)

let me know

---

### Post by chenel on 2005-12-31
[QUOTE=thierry13]Actually I found a problem, I have a message during the boot which says:

REMOVING NVIDIA TLS links...

after that, I have no more the libnvidia.so.1.0.7664 in /usr/lib and /usr/lib/tls

but I don't know WHAT is doing that...

any ideas ?[/QUOTE]

Dunno if you fixed this, but I'm guessing you probably have an old ```
nvidia-glx
``` or ```
nvidia-glx-legacy
``` initscript in /etc/init.d.  Either remove it or chmod -x so that it can't execute, then rebuild (or re-install from synaptic) the NVIDIA module and things should go.

**EDIT**  Whoops, didn't see the response from **dtesser**... sorry...

---

