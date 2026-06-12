---
title: "how to uninstall splashy?"
date: 2008-08-11
forum: General Help
---

### Post by bulletprooflama on 2008-08-11
I decided to start messing around with creating splash screens today, and the easiest method seemed to be to use splashy. Now I've installed splashy and made my theme, but I really have no idea what I've been doing. Could I get some help with uninstalling splashy and getting back the default? Is there any command that can do that?

PS: Yeah, I'm a n00b

---

### Post by anotherdisciple on 2008-08-11
You should be able to uninstall splashy by opening your terminal (Applications > Accessories > Terminal) and typing this:

```
sudo aptitude remove splashy
```

Or you can do it the GUI way... open (System > Administration > Synaptic Package Manager), search for splashy, right click on it ans select "completely remove" and then hit apply.


As far as getting your old Usplash back... Open the terminal again and type this:

```
sudo update-alternatives --config usplash-artwork.so
```

It will ask you which usplash you want to use... just select the ubuntu one.


I think you can also type:

```
sudo aptitude reinstall usplash-theme-ubuntu
```


Hope that helps!

---

### Post by bulletprooflama on 2008-08-11
I've uninstalled Splashy but the second command gets me this:

mila@MILAptop:~$ sudo update-alternatives --config usplash-artwork.so

There is no program which provides usplash-artwork.so.
Nothing to configure.

And the third one gets me this:

mila@MILAptop:~$ sudo aptitude reinstall usplash-theme-ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
usplash-theme-ubuntu is not currently installed, so it will not be reinstalled.
usplash-theme-ubuntu is not currently installed, so it will not be reinstalled.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

What should I do now?

---

### Post by bulletprooflama on 2008-08-11
somebody?

---

### Post by anotherdisciple on 2008-08-11
It says that it's not currently installed... so reinstall won't work. Try this:

```
sudo aptitude install usplash-theme-ubuntu
```

let me know how that works... notice... install vs reinstall

---

