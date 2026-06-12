---
title: "howto install 7664 Nvidia Driver"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by Snipersnest on 2005-06-12
Does anybody know how to install the new Nvidia drivers??

I talked with BFG and a lot of my 3D gaming problems are coming from the 7174 drivers that I'm using now. 

I've only found information on compiling the 7174 driver....that doesn't do me much good.

---

### Post by Xian on 2005-06-12
I haven't done it manually on Ubuntu, but on other systems you basically just make sure you have the appropriate kernel source, headers, & modules installed (all these are available in Synaptic), make your 'linux' symlink to the kernel source in /usr/src and then execute the driver package while logged out of X.

Be sure to follow the [instructions](http://www.nvidia.com/object/linux_display_ia32_1.0-7664.html) and view the [Readme](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt) to setup your xorg configuration.

---

### Post by sol77 on 2005-06-12
How do one find the kernel source etc? My kernel is 2.6.10-5-386. 
Also is it worth the trouble to install the latest drivers? Will I notice a difference in performance versus the nvidia package that came with houry? I am using a GeForce 6880 GT and plan on using window shadows and lots of unnecessary bling-bling. :)

---

### Post by Snipersnest on 2005-06-12
I have a 6800 GT and the 7174 drivers screwed my 3D games up...According to BFG the 7664 drivers will fix the problems I'm having. 

But like he said... I thought I had all the kernel headers and stuff but I guess I'm missing something somewhere because it still won't let me install it.

Can anyone give us a good run down on "howto" install the 7664 drivers?

---

### Post by Xian on 2005-06-12
[QUOTE=Snipersnest] thought I had all the kernel headers and stuff but I guess I'm missing something somewhere because it still won't let me install it.[/QUOTE]
Do a search in Synaptic. Does it show that they are installed?
Including the kernel source, headers, and modules?

Again, you need to view the [README](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt).
It has information on what you need installed plus making the symlink.

*"You will need the required support files installed on your system. On most systems, this means that you will need to locate and install the correct kernel-source or kernel-headers package. Note that linking of the kernel interface (in the case that the interface was downloaded or compiled at installation) requires you to have a linker installed on your system....you must install a linker prior to installing the NVIDIA driver."*

---

### Post by Snipersnest on 2005-06-12
I don't have anything in Synaptic for kernel-source besides one that isn't installed called kernel-source-2.4.27 .... linux-kernel-headers 2.5.999-test7-bk-17  is what I have installed there...

I don't know where else to find them besides searching in there

---

### Post by sol77 on 2005-06-12
[QUOTE=Snipersnest]I don't have anything in Synaptic for kernel-source besides one that isn't installed called kernel-source-2.4.27 .... linux-kernel-headers 2.5.999-test7-bk-17  is what I have installed there...

I don't know where else to find them besides searching in there[/QUOTE]
 Try searching for "linux-source". I haven't installed the package yet but atleast it yielded something that looked useful. I will try it later when I'm by my computer.

---

### Post by Snipersnest on 2005-06-12
ok there I already have linux-source-2.6.10 installed...but still a no go on getting that driver installed

---

### Post by crane on 2005-06-12
I installed the new one but don't quite remember how. I think you need to install the nvidia kernel headers or something like that. I did a search on the forums and found out how. I just don't remember what found exaxtly and would hate to screw things up for you. 

 Should be able to find the answers doing a simple search. Good Luck.

---

### Post by Snipersnest on 2005-06-12
Ok I got a bunch of other things installed now...looks like it might work... I just can't remember how to kill X ... I thought it was CTRL ALT BACKSPACE ...but it restarts it self when I do that.

---

### Post by sol77 on 2005-06-12
I think it was:
ctrl+alt+F1. 
sudo su
invoke-rc.d gdm stop

---

### Post by skoal on 2005-06-12
You don't need kernel-source to build the Nvidia binary, you just need the kernel-headers for your particular version.  Just make sure you don't have any Ubuntu nvidia packages still installed before you run the Nvidia installer.  Then, drop out of an X session, compile, start X (or reboot) and you're good to go...

\\//_

---

### Post by Snipersnest on 2005-06-12
ya I got it all figured out already....bad thing is I still have the same problem in Counter-Strike Source that I did before I upgraded... so it turned out to be a little pointless. My CS:S crashes when people throw any type of nade near me... mostly flashes. My CS:S goes all polygon looking...Doom3 even did it too.

On the bright side CS 1.6 went up 20fps with the new driver... GLXGEAR Scores up about 600 for me from about 12600(7174) to 13270(7664)

---

