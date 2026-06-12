---
title: "Wich VM???"
date: 2008-09-16
forum: General Help
---

### Post by opossumjack on 2008-09-16
Hi everybody...
I'm gonna install VirtualBox OSE to use with win xp under ubuntu...

I just wanna ask you which VM do you think is the best.. I also need to run the VM in invisible mode..

Thanks in advance for your comments

---

### Post by Elfy on 2008-09-16
Personally I use the vbox puel - not sure about usb support on the ose. Used vmware once which probably isn't sufficient to make objective comments. Never use the other.

---

### Post by tuxxy on 2008-09-16
VirtualBox 2.0 PUEL

---

### Post by eggdeng on 2008-09-16
VirtualBox PUEL

---

### Post by Greyed on 2008-09-16
VBox 2.02 PUEL, but my host is WinXP and not Linux; which is how it should be.  When running Linux there's nothing in WinXP I need that will run in VBox.  When running Windows there is lots that I need that runs under Linux.  ;)

---

### Post by jespdj on 2008-09-16
Note that there is a separate [forum about virtualization](http://ubuntuforums.org/forumdisplay.php?f=308) here.

---

### Post by opossumjack on 2008-09-16
> **jespdj said:**
> Note that there is a separate [forum about virtualization](http://ubuntuforums.org/forumdisplay.php?f=308) here.
Thanks a lot... I did not notice it... 

:D

PS Is there a way I can move my thread to that forum?

---

### Post by BlueSkyNIS on 2008-09-16
VirtualBox 2.0 PUEL

---

### Post by Elfy on 2008-09-16
You'd need to report it and ask a mod to do it, I'd be inclined to not worry too much about it now. It'll either get seen and moved or be on the second page or more.. :)

---

### Post by opossumjack on 2008-09-16
I was thinking now about 3D support... It is present in VirtualBox?And what about VMware?

---

### Post by Greyed on 2008-09-16
No, and No.  And not for quite a while, either.

---

### Post by opossumjack on 2008-09-17
> **Greyed said:**
> No, and No.  And not for quite a while, either.
:( Thanks for the sad info...

---

### Post by Greyed on 2008-09-17
Blah, I must have been short for time when I wrote that.  The problem is that virtualizing the 3-D still means it is done in software.  To get 3-D to work requires some magic on the hardware.  This is all non-technical so pardon any gross inaccuracies but the concept should be sound.  The issue is that they virtualizer will need to detach the video card from the host and attach it to the guest.  Then when the guest is done with it, do the reverse.  The capability on the hardware level doesn't exist yet; only the idea of what needs to be done.  So we'll need to hardware to be able to do it then have the software written to take advantage of it.

---

### Post by opossumjack on 2008-09-19
Ok... I've got the point... :D

I'm gonna use VirtualBox and no matter if it has not 3D capabilities... It would be great if so... But now I'm looking for a VM that let me test other distros and software... 
So I think Virtual Box would be ok...

Thanks a lot :)

---

### Post by Greyed on 2008-09-19
In that regard VBox is excellent.  Though do take it with a grain of salt.  Recently Ibex had a problem with VBox.  It was supposed to be fixed in VBox v2.0.2 but when I tried Ibex (KUbuntu) 2 days ago it would not install.  Also Pardus 2008 didn't get far at all; crashed out with a Python error while setting up to install packages.  On the other hand I run KUbuntu 8.04 inside a VBox VM on a near daily basis without a hitch.  :D

---

