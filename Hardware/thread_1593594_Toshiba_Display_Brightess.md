---
title: "Toshiba Display Brightess"
date: 2010-10-11
forum: Hardware
---

### Post by jessidvelez on 2010-10-11
Hello friends. I have been an Ubuntu user since release 5.04 or so...I love this OS. I own a Tosshiba Laptop Satellite U505-S2930 and unfortunately about a year ago I had been in the painful situation of using MS Windows because specifically two important parts of the laptop arent supported:
The first is the cooler: I have already fixed this one, in a very ridiculous way: I have to suspend the laptop and after the suspension, the cooler begins to work....

The second one, and the reason I am asking for help is the display brightess. Since Ubuntu 10.04 it cant be changed!!! It is at 100% and I thought that this problem was going to be solved in this new release....but nothing... I am sick of Windows and I have to be away from the OS I love, just because it seems it is going to make me blind!!!

How can I solve this? Is there a way to report this problem and let the developer to be aware of this??? I repeat: I am sick of using Windows and it seems toshiba has its hands tied by MS not allowing them to give support...(well, this would not be the first time something like that happens) Please help me!! Thanks a lot!

---

### Post by ubunterooster on 2010-10-11
By "cooler" do you mean "cooling fan"?

Add to panel> brightness applet. Does that help for the brightness?

---

### Post by jessidvelez on 2010-10-11
Hi Thanks for answering. Adding the gnome applet does not work. I had already tried that...

---

### Post by snafu006 on 2010-10-11
are you sure the brightness applet will not work your system is very close to mine and it works on my satellite L355-S7907 in synaptic do a serch for intel and should pop up alot of package. The ones i have install are intel-gpu-tools, intel-microcode. xserver-xorg-video-intel and xserver-xorg-video-intel-dbg.

 You can also try updating your bios that can help a little bit with the brightness applet in the deskbar i have to use the up and down key but it does work for me.

---

### Post by jessidvelez on 2010-10-12
Hello Snafu006. Thanks a lot for answering. In deed I was missing one of the packages you told me; I have installed all of them, but the truth is I am still stuck with the same problem.  Part of the output given by lspci is this:

[U]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/U]

I dont know if this can be useful to help me with the issue. Thanks again!

---

### Post by snafu006 on 2010-10-12
Lets try to narrow down subsystems can be found here [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze) try the nerrow down subsystems 

Often lockups occur due to code in a specific subsystem within the xserver or video driver. You can sometimes narrow the problem down usefully by testing with different things turned off. This is done via your xorg.conf. Common things to test include (try each one at a time!):

Option "AccelMethod" "xxx" - Try "XAA", "EXA" (ignored on -intel > 2.8.0)
Option "Accel" "Off" - turns off the 2D acceleration (ignored on -intel except for i810 and i815 chipsets)
Option "DRI" "Off" - turns off the 3D acceleration
Option "AIGLX" "Off" - turns off OpenGL indirect rendering acceleration
Option "PM" "Off" - turns off power management events
Option "NoMTRR" - turns off Memory Type Range Register support, which greatly improves performance so is usually on, but some hardware has buggy support for it
Other options can be found in man xorg.conf, man intel, man radeon, et al.

Sometimes adjusting settings (such as reducing video memory) can make a freeze more (or less) easily reproduced. This can be instrumental in helping debug the problem.


There is a program in Ubuntu sofware center called DRI 3D Acceleration download that. Open it and in the Image Quality tab And enable the S3TC(from no to yes) and in the debug play around with that.

---

### Post by Alver on 2010-10-12
> **jessidvelez said:**
> Hello friends. I have been an Ubuntu user since release 5.04 or so...I love this OS. I own a Tosshiba Laptop Satellite U505-S2930 and unfortunately about a year ago I had been in the painful situation of using MS Windows because specifically two important parts of the laptop arent supported:
The first is the cooler: I have already fixed this one, in a very ridiculous way: I have to suspend the laptop and after the suspension, the cooler begins to work....

The second one, and the reason I am asking for help is the display brightess. Since Ubuntu 10.04 it cant be changed!!! It is at 100% and I thought that this problem was going to be solved in this new release....but nothing... I am sick of Windows and I have to be away from the OS I love, just because it seems it is going to make me blind!!!

How can I solve this? Is there a way to report this problem and let the developer to be aware of this??? I repeat: I am sick of using Windows and it seems toshiba has its hands tied by MS not allowing them to give support...(well, this would not be the first time something like that happens) Please help me!! Thanks a lot!

Although I do not have the same Toshiba model (Satellite L505-10M) in my 10.04.1 64b installation I can and do use the Fn/F5-6 keys to change the screen brightness. I recently installed the Cairo dock and to my pleasant surprise the dock brightness applet is fully functional and allows for continuous change in a far greater range than the Fn keys. Hope this helps.

Alver

---

### Post by jessidvelez on 2010-10-12
hello snafu006. I have been reading the article you linked, but I think this has nothing to do with the problem I am talking about. The laptop neither freezes or stop working... the problem is that display brghtness remains the same, no matters if I slide the brightness applet. Any way I installed the DRI program but...dont see any thing I should reconfigure. Thanks a lot for your interest!!!

PD: What I think is the most annoying about all this, is that 2 versions ago it worked well...

---

### Post by jessidvelez on 2010-10-12
alver thanks a lot for answering. I have installed as you said, but any way, the problem persists....

---

### Post by jessidvelez on 2010-10-13
Hello friends. Thanks a lot for trying to help me. I have solved this problem. Not in a very elegant way, but now I can change display brightness: I followed instructions given here 
[http://wilmor24.wordpress.com/2010/05/11/change-screen-brightness-from-terminal-ubuntu-10-04/](http://wilmor24.wordpress.com/2010/05/11/change-screen-brightness-from-terminal-ubuntu-10-04/)

And wrote a very little program in Java... What does the job is this:
Runtime.getRuntime().exec("sudo setpci -s 00:02.0 F4.B=" + Integer.toHexString(_brillo));
where _brillo is an int between 0 and 255 formatted as and hex string

After that, I wrote a very small shell script like this:
java -jar /home/jessid/NetBeansProjects/Brillo/dist/Brillo.jar

saved it in /usr/bin as "brillo" and gave it the exec permission.

To execute it, i press alt+f2 and write:
gksu brillo

and... taraaaa the magic is done (This might not be magic for most of you, but it is for me).

Again: thank you very, very much

---

### Post by snafu006 on 2010-10-13
hey even tho you got it to work i forgot to tell you in synaptic type toshiba look for FNfxd for the FN key and acpi-support

---

### Post by Alver on 2010-10-14
> **snafu006 said:**
> hey even tho you got it to work i forgot to tell you in synaptic type toshiba look for FNfxd for the FN key and acpi-support
I forgot to mention that I installed, via Synaptic, fnfxd, toshutils and toshset long before I installed the Cairo dock on my Satellite L505-10M (U 10.04.1 and W7 64b in dual boot mode).

Alver

---

### Post by jessidvelez on 2010-10-15
Snafu006, Alver thanks a lot... I have looked in the synaptic package manager and they are already installed.... Any way.... thanks a lot for your interest!!!!!!! I am (again) a happy Linux user :)

---

