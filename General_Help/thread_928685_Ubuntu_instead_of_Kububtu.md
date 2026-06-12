---
title: "Ubuntu instead of Kububtu"
date: 2008-09-24
forum: General Help
---

### Post by Slench on 2008-09-24
Hi everyone... I just recieved my Ububtu cd by mail, tried it out and now I want to install the Ubuntu on my computer instead of the already installed Kubuntu.
Every time I try to install the OS the screen either just blacks out freezes or the computer completely stops responding.

What shall I do???

---

### Post by Xnst on 2008-09-24
Hi,

Since you already have kubuntu installed you can use synaptic to install the ubuntu-desktop package. Then you can choose what session to use when you login, Gnome or KDE.

---

### Post by gjoellee on 2008-09-24
There are several ways to install Ubuntu from Kubuntu. 

1.The easiest will be to go to this page: [http://kshoster.net/index.php?c=downloads&x=apturl](http://kshoster.net/index.php?c=downloads&x=apturl) and simply find "Ubuntu".


2.In Kubuntu open the Terminal/Konsole and add the command below:
```
sudo apt-get install ubuntu-desktop
```

3. Install "ubuntu-desktop" from Synaptic pakgage manager.

When the install is finished log out. Click on "Sessions" in the log in window and find "GNOME". Select it and log in.



Now if you want to delete Kubuntu (includes all about all KDE software) afterwards. Go to the Terminal program and add the code below:
```
sudo apt-get update && sudo apt-get remove kde* && sudo apt-get remove kubuntu-desktop && sudo apt-get auto-remove
``` this will remove all packages you don't need anymore as well.

If end up with one broken package just install the package again.

---

### Post by Slench on 2008-09-24
well gjoellee, 3 new problems!
1st the computer doesn't have any connection to the internet
and
2nd ubuntu is on a disc
and
3rd it says it can't find the ubuntu-desktop package

NOTE: When I searched for Ubuntu on the site you recommended me I got 4 results so I didn't pick any

---

### Post by swisscow on 2008-09-24
I have had a similar situation. I have an AMD 64 bit pc which loads 64 bit ubuntu no problems, 32 bit kubuntu no problems but cannot load 32 bit ubuntu.

Perhaps you are suffering the same? do you use a 64 bit machine?

If not you can also change the boot options of the live cd at the initial boot - try stopping acpi and the other one (can't remember what it is called)

---

### Post by Slench on 2008-09-25
> **swisscow said:**
> I have had a similar situation. I have an AMD 64 bit pc which loads 64 bit ubuntu no problems, 32 bit kubuntu no problems but cannot load 32 bit ubuntu.

Perhaps you are suffering the same? do you use a 64 bit machine?

If not you can also change the boot options of the live cd at the initial boot - try stopping acpi and the other one (can't remember what it is called)

no I don't have any 64 bit computers.

---

### Post by xeth_delta on 2008-09-25
Are the installed and CD versions the same, e.g. 8.04, 7.10, etc?

---

### Post by Slench on 2008-09-26
I think so...

---

### Post by xeth_delta on 2008-09-26
> **Slench said:**
> I think so...

You can make sure with:
```
lsb_release -a
```
Both in the HDD and cd environment. If they are the same, then you can re-enable the CD in the repositories file and install fromthe CD like you would from the internet. The condition, of course, is for the package (in your case, ubuntu-desktop) to be on the cd. First make a backup:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list-bk
```
open it
```
sudo gedit /etc/apt/sources.list
```
and uncomment the line starting with "deb cdrom". Save and run:
```
sudo apt-get update
```
Once installed what you need, undo the changes to the reposiories file and update again.
Let us know how it goes.

---

### Post by Slench on 2008-09-26
OK I'll try...

---

### Post by Slench on 2008-09-28
well I found out htat the kubuntu was ver. 7.4 and the ubuntu was 8.4 and then it froze after I entered this code: sudo cp /etc/apt/sources.list /etc/apt/sources.list-bk

so I'm kinda stuck... any ideas?

---

### Post by xeth_delta on 2008-09-28
> **Slench said:**
> well I found out htat the kubuntu was ver. 7.4 and the ubuntu was 8.4 and then it froze after I entered this code: sudo cp /etc/apt/sources.list /etc/apt/sources.list-bk

so I'm kinda stuck... any ideas?

You won't be able to update properly if the versions are different. If you still don't have access to an internet connection and want to install from CD, you will either need to to get a 7.04 CD, or make a CD with packages (for which you will need a connection from somewhere).

---

### Post by Slench on 2008-09-28
can't I just get a windows emulator, run the cd like I do it on the windows and install it that way???

---

### Post by Slench on 2008-09-29
well I got an 8.04 kubuntu cd but it somehow can't install when I start the computer with the cd inserted in the same way as ubuntu

---

### Post by xeth_delta on 2008-09-30
> **Slench said:**
> well I got an 8.04 kubuntu cd but it somehow can't install when I start the computer with the cd inserted in the same way as ubuntu

It seems to me the signs of some incompatibility. A previous user suggested disabling acpi from the CD boot screen. Have you tried that?

---

### Post by Slench on 2008-09-30
funny you say that it had been disabeled all the time!

---

### Post by Slench on 2008-09-30
oh wait I think I replyed too quick  you had to check mark it first... sorry

---

### Post by Slench on 2008-09-30
but then it still doesn't work

---

