---
title: "Cannot open NVIDIA-Linux-x86-185.18.36-pkg1"
date: 2009-09-10
forum: Hardware
---

### Post by hihihi100 on 2009-09-10
Hi there:

Im trying to install those graphics card drivers (185.18)  in my laptop, but when I try to open it, this is what appears:

Could not open the file /home/hihihi100/Desktop/…ux-x86-185.18.36-pkg1.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

I also tried it via terminal with:

$ cd /usr/src && sh NVIDIA-Linux-x86-185.18.36-pkg1.run
sh: Can't open NVIDIA-Linux-x86-185.18.36-pkg1.run

Any tips please?

---

### Post by raygj on 2009-09-10
open a terminal window
cd /home/hihihi100/Desktop
sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg1.run

---

### Post by wojox on 2009-09-10
Why don't you just download it from synaptic package manager and save yourself the headaches?

---

### Post by Whiffle on 2009-09-10
First install the build-essential package, then its best to get out of X.    To do that, close all your programs, logout.  Hit "Ctl+ Alt+F2", and login there.  Then do 
```

sudo /etc/init.d/gdm stop
chmod +x /usr/src/NVIDIA-blah
sudo /usr/src/NVDIA-blah
sudo /etc/init.d/gdm start

```

And hopefully X will start and all will be well.  If not, well...I guess we'll figure that out later.  

The NVIDIA installer is really pretty nice and simple.  Just remember that anytime you get a kernel update, you will have to reinstall your nvidia drivers.

---

### Post by hihihi100 on 2009-09-11
Thx for all the answers, but Im starting to freak out

If X means that totally blank screen with letters and numbers (like a terminal, but out of Ubuntu), well, thats not for me, given my extremely poor knowledge of it, plus my password has an @, and it seems i cannot write that in X, correct me if wrong

I have tried synaptic too, downloading all nvidias 180-185, and yes, Ubuntu now recognizes some hardware drivers (without numbers, no 180 or 170), and a new Icon has appeared (system admin Nvidia x server settings). When I click that icon:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

So I open a terminal, type that and get:

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.

So I type:

gksudo gedit /etc/X11/xorg.conf

type the password and get:

Section "Device"
    Identifier    "Configured Video Device"  (I MUST WRITE SOMETHING HERE)
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "true"
EndSection

now, can any of you tell me what do I have to type right after "Configured Video Device"?

And I dont know if I am double installing or making redundant copies that I dont need

Hope you can help me

cheers

---

### Post by hihihi100 on 2009-09-11
Retrying this way:

When I write "chmod +x /usr/src/NVIDIA-blah" being out of x it says "not such file or directory"

Am I doing something wrong?

Cheers

---

