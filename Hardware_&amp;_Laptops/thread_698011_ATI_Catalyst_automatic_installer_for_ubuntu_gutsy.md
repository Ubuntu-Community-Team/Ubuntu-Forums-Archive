---
title: "ATI Catalyst automatic installer for ubuntu gutsy"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by DoDoENT on 2008-02-15
Hello everyone!

It's almost 2 am, but I am proud to present my newest bash script - it will install the ATI 7.12 or 8.2 driver automatically using the "manual" way described on [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

The script works best on fresh install of the gutsy or if the last driver installation was made by the manual way described on the [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

The script can easily be modified to work for other ubuntu versions.

Btw., the 8.2 driver works quite well for me - it's a lot faster than the 7.12 (I jumped over the 8.1 driver because it had bug that prevented the logout of GDM while atieventd was running - that was quite annoying) .

Here is the link for downloading the script: [http://www.box.net/shared/olkfdvyscg](http://www.box.net/shared/olkfdvyscg)

P.S. Sorry for the eventual language mistakes - I'm not the native English speaker.

---

### Post by circle on 2008-02-15
Hi!

I found the driver from ATI's driver page too. I have just tried to install the server but did not notice it is that new (release just a few days ago), I am just upgrading from old old version to see if I can play compiz with AIGLX.

But I may have faced some problems. I cannot modprobe the fglrx module, running the command seems to have no effect. I just cannot see it by lsmod | grep fglrx. Running modprobe -l | grep fglrx returns /lib/modules/2.6.22-14-generic/updates/dkms/fglrx.ko so I expect the module exists.

I have followed the instructions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a") (only different is the latest driver I use, v8.45.5 come with catalyst 8.2), and before doing so I have followed the instructions [here]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support") to remove/disable the old fglrx driver. All seems to be successful.

My xorg.conf looks normal, the device with the fglrx driver is configured. Sorry about that.

But it's really strange that fglrxinfo still show me the Mesa driver..
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```Any hints? Thanks so much.

Oops... Seems that I have replied to a wrong thread. I am not using the script yet. Please ignore the message...

---

### Post by inphektion on 2008-02-15
DoDoENT, I will try your script... as nothing else has worked even when I followed those instructions myself.

Circle, I seem to be having same problem as you, let me know if you figure anything out...

---

### Post by DoDoENT on 2008-02-16
Circle, I used to have the same kind of problem. Unfortunately, my script cannot solve that so far. Try this:
```
sudo gedit /etc/modprobe.d/blacklist-restricted
```
Put a # in front of the line "blacklist fglrx", if it is present.
Save the file.
Restart your computer. If this doesn't help, consult this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#A_possible_problem_with_fglrx.ko_conflicts](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#A_possible_problem_with_fglrx.ko_conflicts)
This solved my problem on a pentium based computer, but it wasn't necessary on my laptop.

---

### Post by circle on 2008-02-19
oops...
That line was there and by commenting it out the problem is solved!
I guess the line was added when removing the driver in the restricted driver manager...

Great thanks!

P.S. Have glance through your script and it looks really handy enough. It's a installer so don't blame it for not checking whether the previous un-installation being success or not :) Very great job already!
:guitar:

---

### Post by DoDoENT on 2008-02-19
Thanks! As soon as I learn more BASH, I'll improve it! (It was one of the first bash scripts I've ever written.)

---

