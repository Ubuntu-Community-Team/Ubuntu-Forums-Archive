---
title: "Codeweavers lame duck Challenge Problem"
date: 2008-10-28
forum: General Help
---

### Post by iampriteshdesai on 2008-10-28
Hi!
I have tred to download the software and I found it to be a .SH file. Am i downloadsing the correct file? Is this the right file?
Shouldn't it be .deb?

---

### Post by snova on 2008-10-28
No. It is .sh. It's a script, probably one that installs itself when you run it. (As in, I don't know what else it could possibly be.)

PS. What's the difference between Game edition and Pro?

---

### Post by Sam on 2008-10-28
Pro = Crossover Office I think...


EDIT: Nope, found [here](http://en.wikipedia.org/wiki/Codeweavers)
> The Company's products include CrossOver Pro Linux, CrossOver Pro Mac, CrossOver Games for Linux, and CrossOver Games for Mac. **CrossOver Server was discontinued in 2007 as CrossOver Pro replaced its functionality**.

---

### Post by cariboo on 2008-10-28
To run the file, assuming you downloaded to your desktop, in a terminal type:

```
cd ~/Desktop
```

Next make the file executeable:

```
chmod +x install-crossover-pro-demo-7.1.0.sh
```

You should now be able to install the program:

```
sudo ./install-crossover-pro-demo-7.1.0.sh
```

Jim

---

### Post by Valok on 2008-10-28
Thanks for the help!

---

### Post by RedMartin on 2008-10-28
> **cariboo907 said:**
> To run the file, assuming you downloaded to your desktop, in a terminal type:

```
cd ~/Desktop
```

Next make the file executeable:

```
chmod +x install-crossover-pro-demo-7.1.0.sh
```

You should now be able to install the program:

```
sudo ./install-crossover-pro-demo-7.1.0.sh
```

Jim

Did all that and got this:
'/home/martin' must exist and belong to you in order for the installation to proceed.
If installing as root, you may need to log in as root, use 'su -' or 'sudo -H'.

I'm a bit of a Linux noob so what do I do now?

---

### Post by jabeez on 2008-10-28
> **RedMartin said:**
> Did all that and got this:
'/home/martin' must exist and belong to you in order for the installation to proceed.
If installing as root, you may need to log in as root, use 'su -' or 'sudo -H'.

I'm a bit of a Linux noob so what do I do now?

getting the same thing here, on both an Ubuntu Hardy install and a Kubuntu Ibex machines.......

---

### Post by jabeez on 2008-10-28
sorry to bump, but any ideas? I've got my mom's laptop all freshly Hardy'd but would like to have this set up with limited time..............

---

### Post by wormeyman on 2008-10-28
I took the easy route and right clicked on the files selected make executible on the permissions and then double clicked and selected run in terminal.

---

### Post by cariboo on 2008-10-28
Do you have the file saved on your desktop? Or somewhere else?

Jim

---

### Post by RedMartin on 2008-10-28
After doing all the terminal stuff I double clicked on the .sh file out pf sheer frustration.

It ran and installed. Who'd have thought it?

---

### Post by SuperSonic4 on 2008-10-28
If it's executable then me :p

I installed mine as user.

---

### Post by jabeez on 2008-10-28
ok, I got it to install using no root permissions from my /home, but apparently it installs only in a hidden .home directory?

---

### Post by dburnett77 on 2008-10-28
> **jabeez said:**
> ok, I got it to install using no root permissions from my /home, but apparently it installs only in a hidden .home directory?

try recover on boot, and re-type re-typed ro and yes that's an alphabetic character, not zero 0.

yeah, that's what i did.

---

### Post by la3875 on 2008-10-29
:) I follow code above, then went back to desktop icon and ran in terminal and success!

---

### Post by kryos on 2008-10-29
As they were getting hammered I followed the advise to download the demo and register to full version.  Demo download page has option of distro specific packages (rpm, deb, ?)  Install can't get any easier than that!

---

