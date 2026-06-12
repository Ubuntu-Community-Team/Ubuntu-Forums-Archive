---
title: "Screen Resolution Issue.... Again.  8.10 Ibex"
date: 2008-11-05
forum: General Help
---

### Post by Nylo on 2008-11-05
On 8.04 Hardy it took me a bit but I finally got 1024x768.  Now with 8.10 Ibex I'm clueless.  Ive Google lots of info but it seems that everyone has a different idea on what to do.  The last suggestion caused me to re-install 8.10 Ibex.  There is no other choice other than 800x600 and 640x480 in Ibex screen resolution settings.  No drivers are reported.

"sudo gedit /etc/X11/xorg.conf" gets me the below.

########################
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
###############################

Any help would appreciated.

Sony Vaio (laptop) PCG-R505JL/C
10.4" screen, 60 re-fresh
Intel(R) 82815 graphics controller

---

### Post by bscbrit on 2008-11-05
[http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

Try this thread.  Doesn't work for everybody, though.

---

### Post by Peter09 on 2008-11-05
Try booting into recovery mode. In the menu that is displayed take the xfix option.

---

### Post by bscbrit on 2008-11-05
Peter09

Yes, you are correct in that your suggestion is the approved mode of changing the xorg settings.  The problem that I have found is that, if the automatic process on installation does not correctly identify the video card and display, then neither will it do so using xfix.  The change to xorg7.4 has also resulted in the removal of a simple way for the user to **tell** the computer which video card and display are actually fitted.

I understood the previous system of using dpkg-reconfigure xserver-xorg (with -phigh if necessary) but the system is now entirely automatic.  The user is not prompted to input anything.  This is all well and good until an error occurs and then the user is left with a sub-optimal system at best or an unusable system at worst.  I found that by installing the displayconfig-gtk package issued with Hardy I could at least tell the system what to do.  I know it is not the correct way of doing it but it was the only thing I could find that solved the problem.  There are some with specific graphic card driver problems such that even when the correct driver is installed it still will not function as it did under 8.04.  My solution will not help them.  I've 'upgraded' 4 computers so far from 8.04 to 8.10 and on 2 of those the new xorg package cannot set up the display correctly.  It doesn't matter whether it is a new install or an upgrade, the end result is a non-functioning system.

If anyone can direct me to the 'approved' method of inputting video and display data I would much appreciate it.

---

### Post by Peter09 on 2008-11-05
Hi bscbit,
I agree with you here. However I made the suggestion initially because I have noticed that often the initial install will not identify the correct card and drivers but a simple attempt at xfix from recovery mode will. 

It does not always happen but it is simple enough to do as a first pass.

I think I agree with you on the automation bit. I think we try to be too clever, attempting to identify the users graphics capabilities automatically. This seems to fail across quite a few installations.

Using windows as an example - it, in the end, lets the user configure to what he wants through a straightforward display setup. It does not restrict the user to any great degree. 

Why we do not have a utility that lets us set screen resolution etc I do not know. It is a cause of a significant number of problems in these forums.

---

### Post by bscbrit on 2008-11-05
> **Peter09 said:**
> Hi bscbit,
It does not always happen but it is simple enough to do as a first pass.


Yes, I was perhaps a bit hasty in my suggestion, let's get the simple solutions out of the way first.  Thank you.  I was seeing the OPs problem as identical to mine, which it might or might not be.

The missing configuration tool is one reason why I left comments on the 'Has Intrepid been rushed?' thread but nowadays there seems to be a tendency for some to believe that, if everything is working on their own system, nobody else should have problems either. :-)

See you around the forums.

bscbrit

---

### Post by Nylo on 2008-11-05
> **Peter09 said:**
> Try booting into recovery mode. In the menu that is displayed take the xfix option.

Didn't work.    :confused:

---

### Post by Peter09 on 2008-11-05
Can you post of the terminal command

```
lshw -C display
```

---

### Post by Nylo on 2008-11-05
> **bscbrit said:**
> [http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

Try this thread.  Doesn't work for everybody, though.

This sounds great but I'm wondering if anyone else out there has done this with success.  The last time I took advice I had to re-install 8.10 Ibex.  Just being cautious.

---

### Post by Nylo on 2008-11-05
> **Peter09 said:**
> Can you post of the terminal command

```
lshw -C display
```

Here it is.

#####################
WARNING: you should run this program as super-user. 
  *-display UNCLAIMED     
       description: VGA compatible controller 
       product: 82815 Chipset Graphics Controller (CGC) 
       vendor: Intel Corporation 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 11 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
######################

---

### Post by bscbrit on 2008-11-05
Nylo

I certainly wouldn't recommend my solution as the first option but, when you have tried all the others and had no success, you might as well give it a try before re-installing 8.04 again.  I've raised the problem as a formal bug (294202) but there is no saying when it might be fixed.

If you have a backup copy of your 8.04 xorg.conf file, then I would suggest installing that first in 8.10 as it has been more successful that my solution above but, if you haven't got one, then you are rapidly running out of options.

If you do try it, please let me know how you get on by posting on this thread.  If it doesn't work for anyone else but me then I will stop offering it as a potential solution.

Good Luck.

---

### Post by Peter09 on 2008-11-05
Can you look at this thread

[http://ubuntuforums.org/showthread.php?t=693315](http://ubuntuforums.org/showthread.php?t=693315)

---

### Post by Nylo on 2008-11-05
> **Peter09 said:**
> Can you look at this thread

[http://ubuntuforums.org/showthread.php?t=693315](http://ubuntuforums.org/showthread.php?t=693315)

Thanks Peter09, Ill give it a shot.

---

### Post by Nylo on 2008-11-05
> **bscbrit said:**
> Nylo

I certainly wouldn't recommend my solution as the first option but, when you have tried all the others and had no success, you might as well give it a try before re-installing 8.04 again.  I've raised the problem as a formal bug (294202) but there is no saying when it might be fixed.

If you have a backup copy of your 8.04 xorg.conf file, then I would suggest installing that first in 8.10 as it has been more successful that my solution above but, if you haven't got one, then you are rapidly running out of options.

If you do try it, please let me know how you get on by posting on this thread.  If it doesn't work for anyone else but me then I will stop offering it as a potential solution.

Good Luck.

Im running 8.10, not 04.

---

### Post by Nylo on 2008-11-05
> **Peter09 said:**
> Can you look at this thread

[http://ubuntuforums.org/showthread.php?t=693315](http://ubuntuforums.org/showthread.php?t=693315)

Didn't work.  Anyone else?

---

### Post by bscbrit on 2008-11-05
Nylo

I think that you misunderstood me - I know that you are running 8.10.

The problem is that you cannot configure your xorg.conf under 8.10 because the automatic method fails and the tool to manually configure it has been removed.

BUT, if you have a copy of an old working 8.04 version of xorg.conf and you copy it over your 8.10 version everything works again!  The old 8.04 version stills contains the graphic card and display parameters that are not now included in the new version.

---

### Post by Nylo on 2008-11-05
> **bscbrit said:**
> Nylo

I think that you misunderstood me - I know that you are running 8.10.

The problem is that you cannot configure your xorg.conf under 8.10 because the automatic method fails and the tool to manually configure it has been removed.

BUT, if you have a copy of an old working 8.04 version of xorg.conf and you copy it over your 8.10 version everything works again!  The old 8.04 version stills contains the graphic card and display parameters that are not now included in the new version.

I don't have a copy....  Do you?    :mrgreen:

---

### Post by bscbrit on 2008-11-05
Not that will suit your graphics card and monitor - lol.

I don't know what backups you might have lying around.  If you are like me, you will have backups of your data but not of the OS.  From now on, I'm going to backup my xorg.conf (or future equivalent) and my network configuration.  They are both things that 8.10 got badly wrong and will not let me correct easily.

---

### Post by uboss on 2008-11-05
I'm having the same problem. It's been three days trying to configure it to work on an old Compaq Desktop with no success.
 I intalled Suse 11 and it installs perfectly it detected all the hardware perfectly with Suse 11 the system runs very smooth.

 I tried Mint and it was giving the same problem which I configured through sudo displayconfig-gtk. Still it did not had my graphics card or my monitor driver available.  I chose the best closest name I could guess. Though it was not a perfect solution but what it did was that it made xorg.conf which I manually changed later for color depth and display. which I saw from the xorg.conf of Suse 11. I took out mint as it was running very slow compared to Suse 11.

With ubuntu it has been terrible I downloaded "guidance backends" and "displayconfig-gtk" and since yesterday trying to configure like I did with Mint it just refuses to. The DisplayConfig-gtk was only able to write once on xorg.conf I don't know what is wrong it is not writing the xorg.conf and even if I change and add manually it is not working. 

I don't want to go other than Ubuntu as I'm used to Ubuntu stuff but this thing is really annoying. I wonder how can the development team forget to add such  an important aspect of an operating system to be able to configure your hardware drivers or similar settings. 

I really don't want to use Suse on this system as I'm not used to Suse and Mint was slow and resource hungry on the system may be some other config went wrong there but this thing is really bad I want to istall Ubuntu and I can't. If somebody has another solution please let us know.

---

### Post by bscbrit on 2008-11-05
uboss

Have you tried copying the working xorg.conf from either your Suse or Mint installation to replace the one that 8.10 is generating?

---

### Post by uboss on 2008-11-05
I copied the xorg.cof of Suse it did made the display right 1280-1024 but whenever I start Ubuntu it gives warning and options to start at low quality and reconfigure xorg.conf and starts after answering couple of setting questions. I think it is probably not compatible with ubuntu hardware drivers. Now I'm istalling Mint again to take the xorg.conf and take it out because I forgot to copy the modified file from there when I first tried Mint. Plus Ubuntu is not detecting the Audio drivers aswell do you have some Idea what can I copy from Mint for audio drivers. 
Well this would my last try unless I find a proper solution. And I'm saying this since 2 days now :)

---

### Post by wgrant on 2008-11-05
See [the resolution fixing documentation](https://wiki.ubuntu.com/X/Config/Resolution).

---

### Post by wgrant on 2008-11-05
Also, **FILE BUGS!**

We can't fix problems that we don't know about.

---

### Post by bscbrit on 2008-11-06
It is already reported as a bug (#294202).

---

