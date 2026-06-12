---
title: "Nvidia drivers from repository complete cleanup"
date: 2011-05-30
forum: Hardware
---

### Post by kacperpl1 on 2011-05-30
I'm trying to clean whatever nvidia drivers(nvidia-current) from repository left after uninstall because I want to test nouveau driver, however after removing the proprietary driver I get this:
```
$ glxinfo 
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig
```

I know its proprietary drivers problem because I've made this twice like this:
1st time
1) Fresh install of Natty formatting over maverick - nouveau works, glxinfo shows software rasterizer
2) Compiling my own latest nouveau from git - glxinfo still the same info.
3) Found out something like - "try to install proprietaries and force the nouveau driver in xorg.conf" so tried it out and it didn't even start xorg(that was obvious but whatever)
4) proprietaries removal - glxinfo throws error shown above

2nd time
1) Fresh install of Natty, formatting over last one - I thought that I could screw something up while compiling and installing my own compilation so I reinstalled - glxinfo shows software rasterizer
2) Xorg-edgers added and complete upgrade - glxinfo shows the same output
3) Nvidia proprietary install from repo(I need my acceleration for OpenCL developement)
4) I want to check some new info about how to run nouveau on my card so I remove the proprietaries and I'm again at the same place.

I've got only some info from some guy stating "This sounds like what happens if there's bits of the NVIDIA binary
driver laying around still (usually their libGL.so or libglx.so)" But he wouldn't be precise about how to solve this because he's using the different distro(yet I think he's reliable cause he's committing some patches for nouveau)

So how to resolve this problem? How to completely flush proprietaries?
EDIT: Btw is there a possiblity of running both drivers at the same time?
I mean I'd like my OpenCL accelerator work in background while still having xrandr support and little acceleration in the foreground.

---

### Post by lidex on 2011-05-30
How about looking for them:
```
sudo updatedb
```
```
locate libglx
```

---

### Post by kacperpl1 on 2011-05-31
I only get this
```

$ sudo updatedb
$ locate libglx
/usr/lib/xorg/modules/extensions/libglx.so

```
So probably I am missing mesa's libglx.so??

EDIT:

OK I found out the solution - xorg.conf configured by nvidia-settings which I used with swapping just nvidia to nouveau in driver section was missing module section. Adding this
```
Section "Module"
        Load  "glx"
EndSection
```
fixed the glx problem

---

