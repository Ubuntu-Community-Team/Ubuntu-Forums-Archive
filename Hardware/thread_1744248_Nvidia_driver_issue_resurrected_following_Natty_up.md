---
title: "Nvidia driver issue resurrected following Natty upgrade"
date: 2011-04-30
forum: Hardware
---

### Post by Khodeir on 2011-04-30
Hello all, 

So I upgraded to Natty last night. I hate myself for it... When I'm lucky, i get to  ctrl+alt+F1 into another session and look at the log file.. only to find:

Fatal error: no screens found

Of course... I checked my xorg.conf ... it's the same one i was using with 10.10 and 10.04. 

So i figured they probably did something to a driver i have installed and caused some compatibillity issues. So i moved my xorg.conf to my home folder and restarted. 

Sure enough, this time i got all the way past the login screen. Of course, the resolution was horrible and you couldnt even access the menu without lagging, but its progress, i guess.

Now i'm stuck. I remember i had to do mess around with the xorg.conf and some nvidia-glx drivers the very first time i installed ubuntu on this PC. I don't remember what i did to get it set up though. Does anyone have any ideas? :D

Thanks, 
Khodeir

---

### Post by sikander3786 on 2011-04-30
First try removing and re-installing your graphics drivers. Don't forget to reboot in between.

If that doesn't solve the issue, try reconfiguring your graphics.

```
sudo dpkg-reconfigure xserver-xorg
```

Let us know how that goes.

---

### Post by Khodeir on 2011-04-30
One more thing, the OS seems to think my PC is a laptop because sometimes, instead of the GUI loading screen i get the startup script (if that's what you call it) and it always stops on "Checking battery state...". Just thought that was weird.

---

### Post by Khodeir on 2011-04-30
Thanks for the quick reply, sikander. 

I removed the nvidia drivers from the package manager and then ran: 

```
sudo apt-get install nvidia-current
sudo nvidia-xconfig 
sudo reboot 

```

It came back up and again, i didn't get past the Ubuntu loading screen. It seems that i only get past this screen if i don't have a xorg.conf file, i.e if i let it use default settings. What am i missing? :'(

---

### Post by marek_online on 2011-04-30
I had this problem, and it went away after I installed the right kernel headers. For whatever reason it looked like a DKMS issue - the building of the drivers was failing quietly.

I also uninstalled everything nvidia related and reinstalled nvidia-current.

---

### Post by cigtoxdoc on 2011-04-30
Please explain "right kernel headers"

Thank you,

John

---

### Post by Khodeir on 2011-04-30
I pretty much uninstalled anything nvidia related too (nvidia-settings, nvidia-common, nvidia-currrent and nouveau). I'm not sure what you mean when you say linux headers, but i'll try anything at this point. 

Also, I tried a couple of "fixes" off the web although they were predominantly *old* fixes.. like for ubuntu 6.06. One of them said that the driver "nvidia" was not recognized and advised to change the xorg.conf to "nv" instead. That actually worked, but only to the extent that it brought me into the GUI with  640x480 resolution. I'm pretty sure that all that did was have the x-server ignore my graphics card.  HOWEVER, this is the only way I've been able to boot into the GUI without removing the xorg.conf file completely, so.. hooray! :D

I'm missing a driver or something, right? What is it?:confused:

---

### Post by Khodeir on 2011-04-30
Cursory google search brought me here: [http://ubuntuforums.org/showthread.php?p=10742944](http://ubuntuforums.org/showthread.php?p=10742944) <-- This what you mean?

Have you tried this? I don't particularly like running commands i don't understand, so i don't wanna jump the gun here.

Edit:
I think its supposed to reinstall the "headers" on my GRUB menu.

---

### Post by Khodeir on 2011-04-30
marek_online <-- This man is a genius. 

I'm entirely unsure what reinstalling the headers means, but i know it worked! :D

Fix:
1. Get to a command prompt (either via root access in recovery mode or ctrl+alt+F1)
2. ```
sudo apt-get install --reinstall linux-headers-'uname -r'
sudo apt-get install --reinstall linux-image-'uname -r'
sudo apt-get install dkms (You probably have this one.. but just in case)
```3. Reboot and enter another command prompt 
```
sudo nvidia-xconfig
```4. Reboot or restart x. (At this point you will be brought into the GUI :D. If you're happy with the resolution at this point, you dont need to continue.)

5. If your preferred resolution is still not available you can add it to your xorg.conf file maually. Just open it up in an editor, it is located in /etc/X11/xorg.conf. You will have to add the resolution to the "Monitor" and "Device" sections.. or at least, i had to. There is a very good guide on how to add custom resolutions here: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973).

Thank you all for helping me out,
Khodeir

---

### Post by marek_online on 2011-04-30
Glad it worked for you Khodeir.

The kernel headers are bits of programming code that things such as drivers need to work with you particular kernel. Because there are so many different kernels out there many drivers aren't pre-compiled, but compile themselves as they are installed - and that's when they need the headers.

I was using the 2.6.38-8-pae kernel too, as it happens, so perhaps the problem lies in the headers of that kernel in particular not getting installed properly.

Anyway, happy everything's up and running!

---

### Post by Khodeir on 2011-05-04
Hey all, 

Hadn't seen your reply till now, marek, thanks for the kind words. I just thought i'd update this seeing as a ubuntu update has moved me up to the  2.6.38-9-pae kernel and brought this issue back. Thankfully, i knew what the problem was this time! :D

So anyway, i'll edit the fix to use uname -r instead of a specific kernel module.

Thanks again, 
Khodeir

---

### Post by neutro on 2011-05-13
Ok that did solve the major headache I had since upgrading to Natty from Maverick. Is there a way to give karma or reputation or bump this thread :)

An addition to the solution presented is this thread: I think (not sure, am I right?) that installing the linux-headers-pae package will make all future linux-headers-pae-2.6.xx.y-z packages to be installed automatically.

When dkms is there and functionning, installing the specific linux-headers package for a given kernel automatically compiles and installs the nvidia-driver for that kernel. 

I can't believe that Khodeir and me are the only people with this problem. It's major because the default kernel in GRUB does not yield a graphical user interface at all (there is no fallback to Classic since the nvidia card is detected and the nvidia-driver package is installed). I suspect that many people got bit by that upgrading from Maverick, and were forced to perform a clean install from disk or something similar after this problem showed up. Or worse, abandoned Ubuntu altogether...

So I suggest making sure this thread doesn't go away in the bowels of Ubuntu Forums...

---

### Post by diaco on 2011-05-16
After a clean installation of natty, I can't get my nvidia dirvres working.
Jokey says "This driver is activated but not currently in use". 
None of this thread's (and other thread's) methods could fix the problem. 
I've tryed nvidia-current and nvidia (ver173) from repositories and nvidia driver at nvidia.com.  
There wasn't any problem with 10.04.
Can anyone suggest a solution or at least a method that lead me to identify the source of this problem?
Thank you.

---

### Post by diaco on 2011-05-16
Is this a kernel related problem or X.org?

---

### Post by Neobuntu on 2011-05-19
1. I tried (TEST basis only) Natty, and this REGRESSION of nvidia was not working, and so also Unity, or any other direct 3D was not working.

2, NOW, I have the predicament, of whether or not to try again, or wait a while.

3. There's no way to gauge, how many faithful Ubuntu users we have lost, and over this. If you think they don't matter, then you may be part of the problem.

Leave stuff as Beta, until it's fixed! Especially, do not use pop-ups to ask them to (managed)dist-upgrade, the more risky way.

**ADD:** The problem is not only the non-free Nvidia drivers, but Compiz, Emerald, and unity being buggy. I now have one upgrade (don't do it), and on clean install partly working, with limited Compiz function. Pick the wrong combo, and it's crash city. What a nightmare.

[B]For all the smart tail know it alls' that keep saying we should have stayed with the LTS, no we can't, unless we want to get left behind. AKA, lost benefits, or regressions. In other words, some peripheral things that people want to get done, are a not readily available, for anything but the mainstream Ubuntu versions, at the time. The idea of LTS, does not work, unless you hardly use your computer.

I'm back to my recommendation to NOT NOT NOT upgrade to a whole new Ubuntu release tier, until at least 3 month after it's "official"; unless you're just testing. This is only because we can choose Ubuntu "classic", and not Unity. Unity may not be sorted out (stable and non-conflicting) until 11.10, or later.[/B]

---

