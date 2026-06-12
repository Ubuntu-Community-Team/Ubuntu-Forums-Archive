---
title: "NVIDIA Driver issues"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by Saptarshi Guha on 2005-04-08
Hello,
I am running Hoary on a ZV5000z laptop with the Nvidia GForce 440M graphics card. I saw the xorg.conf file and noticed that nv driver is loaded - is this the nvidia driver? 
Assuming it is, i installed the nvidia-settings program through synaptic - but when i run it this is what i get
ERROR: NV-CONTROL extension not found on this Display.


Could someone help me?

Also, what is the GLX extension - does it make my system smoother/faster?

Many thanks
Saptarshi

---

### Post by nad on 2005-04-08
The nv driver is the open source nVidia driver.  As politically correct as ubuntu is, the closed source, binary only, driver from nVidia is available as a deb package. The reasoning being that as more powerful graphics has traditionally been a driving force in the advancement of computer use, nVidia has every right to keep their technology secret. Let the flame wars begin (tm).

Is the manufacturers driver better than the open source driver? At doing what? If surfing the web, using an office suite, email and light gaming, no. Moderate gaming maybe. Heavy gaming and multicard systems will require it. In the end, it is your choice as this is what linux is all about.

The package is available through the synaptic package manager or apt-get, nvidia-glx (?). However, be aware that there have been known issues with the closed source installer and driver. Only nVidia can fix this.

From Wikipedia, the free encyclopedia.

GLX (acronym for "OpenGL Extension to the X Window System") provides the glue connecting OpenGL and the X Window System: it enables OpenGL 3D programs to draw to a window of the X Window System. GLX consists of three parts...

Dan M

Edit: The nVidia settings program is only for the closed source driver I believe.

---

### Post by Saptarshi Guha on 2005-04-09
Hello,
 Thank you for a very informative and helpful answer. I somehow find the Ubuntu forums much more organized and helpful than those of Fedora (maybe because the former is centralized).

Thanks
Saptarshi

P.S No offence to Fedora fans or help sites.

---

### Post by skagedal on 2005-05-08
Hi!

I am running Hoary with a NVIDIA GeForce2 MX/MX 400. I have a similar problem as the original poster, I get that same error message: "ERROR: NV-CONTROL extension not found on this Display."  - but I have installed the nvidia-glx package, and I also ran "sudo nvidia-glx-config enable" as described on the [BinaryDriverHowto](http://ubuntulinux.org/wiki/BinaryDriverHowto)... I restarted X (logged out/in), and as far as I can tell, the nvidia-driver is now running:

```

$ lsmod | grep nv
nvidia               3923388  0
agpgart                31784  2 nvidia,intel_agp
$

```

"nvidia-settings" does open up some kind of program, but all I can do there is "Help" and "Quit"...

Any ideas? 
Thanks, Simon

---

### Post by Saptarshi Guha on 2005-05-08
Hi,
Nice to see you got it working. I hope your screen has come out ok(i.e no blank band to the right - happened to my Hp zv5000z).
The nvidia-settings can be used to play around with some options of the card - such as colour settings(incl. gamma correction) and other options - most of which i'm not familar with. 
you could see the NVIDIA refence manual /usr/share/doc/NVIDIA_GLX-1.0/nvidia-settings-user-guide.txt

it might help.
Thanks
Sapsi

---

### Post by Saptarshi Guha on 2005-05-08
Oh yes, i forgot, is your xorg.conf using the nvidia drivers?
Heres my xorg.conf.

---

### Post by spartus4 on 2005-05-11
[QUOTE=skagedal]Hi!

I am running Hoary with a NVIDIA GeForce2 MX/MX 400. I have a similar problem as the original poster, I get that same error message: "ERROR: NV-CONTROL extension not found on this Display."  - but I have installed the nvidia-glx package, and I also ran "sudo nvidia-glx-config enable" as described on the [BinaryDriverHowto](http://ubuntulinux.org/wiki/BinaryDriverHowto)... I restarted X (logged out/in), and as far as I can tell, the nvidia-driver is now running:

```

$ lsmod | grep nv
nvidia               3923388  0
agpgart                31784  2 nvidia,intel_agp
$

```

"nvidia-settings" does open up some kind of program, but all I can do there is "Help" and "Quit"...

Any ideas? 
Thanks, Simon[/QUOTE]

Your nvidia kernel module is loaded, but not being used.  Make sure you change your xorg.conf file.

---

