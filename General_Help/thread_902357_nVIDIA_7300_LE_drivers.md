---
title: "nVIDIA 7300 LE drivers"
date: 2008-08-27
forum: General Help
---

### Post by Whisper45 on 2008-08-27
I want to update my graphics card drivers, so I goto nVIDIA website, download the right drivers to desktop. I double click it and it says Cannot open.

I also read:

[QUOTE=from 'how to install on nVIDIA page]STEP 3: Install
Type "sh NVIDIA-Linux-x86-173.14.12-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X server config....[/QUOTE]

so I type that "sh NVIDIA-Linux-x86-173.14.12-pkg1.run" into Terminal (without the "") and it still says cannot open.

Does anyone know why this is? Thanks.

Yours,
Whisper

P.S, if you know a link to a driver download for my graphics card that definately works, please post it!

---

### Post by Elfy on 2008-08-27
This thread should help you run the file, but have you tried hardware drivers or envy first - not sure but I think you would need to run it eachtime the kernel gets updated if you use the nvidia file - but as I sadi not too sure about that.

[http://ubuntuforums.org/showthread.php?t=75345](http://ubuntuforums.org/showthread.php?t=75345)

---

### Post by Whisper45 on 2008-08-27
I did that thing, alt ctrl and f1, then sudo /etc/init.d/gdm_stop, and it said something like it had worked, but then I couldnt close it, and kept pressing escape. Something asked me y/n I pressed y, then when I looked back, I'd just said yes to stop all 2038 (or something) possibilities.

1st, what did this do?
2nd, I run terminal again, put the thing nVIDIA says to put and I get:
sh: Can't open NVIDIA-Linux-x86-173.14.12-pkg1.run

---

### Post by Elfy on 2008-08-27
Once you have Ctrl+Alt+F1 to get out it's Ctrl+Alt+F7 - you have to make sure that you are at the file location or use the path.

Once you have left gnome and are in the terminal if you are not in your home/Desktop if that is where the file is it won't work 

```
sudo /etc/init.d/gdm_stop
``` - stops gdm to start it again ```
sudo /etc/init.d/gdm_start
```

But you would be better of trying the other 2 options first IMO, unless of course you already have.

---

### Post by Elfy on 2008-08-27
Read this - particularly atrificial intelligences comments - [http://ubuntuforums.org/showthread.php?t=894142](http://ubuntuforums.org/showthread.php?t=894142)

---

### Post by Whisper45 on 2008-08-27
But when I open it it doesnt say anything about x?

---

### Post by Elfy on 2008-08-27
What doesn't ?

---

### Post by nbayiha on 2008-08-27
Follow this thread and you should have your card fixed. Read carefully all the thread before  choosing your method. As for what i read above i will recommend you to follow **_the tricky way_**. downloading your own driver for nvidia.com
Here is the thread 
[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy)

---

### Post by Elfy on 2008-08-27
Nice tut nbayiha - I'll bookmark it :)

---

### Post by Whisper45 on 2008-08-27
Thanks, but I have Ubuntu Kernel? And nVIDIA 7 series. Does that matter?

---

### Post by Elfy on 2008-08-27
If you haven't tried to install with the hardware driver tool or envy they are your best option I think, after that try to follow the tutorial; you have hardy if you downloaded it after April 2008 the nvidia series makes a difference to which driver you will need.

But I do styrongly suggest that you try the 2 easier methods first if you haven't already done so.

---

### Post by Whisper45 on 2008-08-27
1, I didnt download it since april 2008, I had it on a cd. I know for a fact I have Kernel. I also tried following your 'tricky way' tutorial, and its messed up my computers resolution, and the smallest it can get is 640x640, meaning its so big that I cant see to press OK/cancel buttons on popups and stuff!! Also, the reason I wanted the graphics card driver was to make my game (gta) run faster, and now it doesnt run at all!!!

---

### Post by Elfy on 2008-08-27
I know you have kernel - they all have a kernel, everyone of them but different ones. it's what version of ubuntu you have which might make a difference and is important - they get released every 6 months - current is 

Hardy - version 8.04, previous was
Gutsy - version 7.10 - we can find out if you open a terminal and run

```
lsb_release -a
``` this will tell you what version you are running; ```
 uname -r
``` will tell you what version kernel you are running. You should alos be able to get that information in About > System.

It isn't my sticky and twice I've said you would be better of using either of the other 2 methods and have asked you if you have tried - neither got a response, I also showed you another thread which reiterated the point that you should use hardware drivers or envy to install it as your first options.


Open nvidia-settings from a terminal, run this command

```
gksudo nvidia-settings
``` you should be able to set up your resolution from there.

If that doesn't help - uninstall the nvidia driver using synaptic - search for nvidia - find the driver which is installed, right click and choose complete removal. You will probably need to reboot, once you have done that use HArdware Drivers in the system >admin menu to install.

---

