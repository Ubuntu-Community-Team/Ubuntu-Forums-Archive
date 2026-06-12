---
title: "ATI Radeon Xpress 200M on Ubuntu 9.04 S-Video problem"
date: 2009-10-10
forum: Hardware
---

### Post by AgentY on 2009-10-10
I recently installed a clean install of Ubuntu 9.04 and am very impressed. Ive managed to get my ATI Radeon Xpress 200M GPU working following the following steps (used on my Laptop: HP Pavilion DV5000 Series);

First off we will want to backup your current “sources.list” (the file that contains all of the repository information), so simply run the command:
[COLOR=Red]**sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak**[/COLOR]

Now, we will open up the original “sources.list” file and set it all back to the intrepid repositories. This can easily be done with Gedit’s replace tool. You can, of course, use any other text editor. To open the file in Gedit, just type the following into a terminal.
[COLOR=Red]**sudo gedit /etc/apt/sources.list**[/COLOR]

[COLOR=Red]**In gedit, simply select the word “jaunty” anywhere in the file and click on “Replace” on the tool bar. When the dialogue box comes up, type “intrepid” into the box labeled “Replace With:” and click “Find” then “Replace All”**[/COLOR]


 After replacing “jaunty”, save the file and close out of Gedit (or what ever text editor you used), and go back to a terminal and type:
[COLOR=Red]**sudo apt-get update**[/COLOR]

Once the repositories are updated, make sure all ATI drivers are uninstalled.
 Now we will uninstall the current version of the xserver using the following command. (Note that gnome-session and fast-user-switcher-applet are specific to Ubuntu. Variants like Kubuntu and Xubuntu will not need to remove these because they are not installed)
[COLOR=Red]**sudo apt-get autoremove xserver-xorg gnome-session fast-user-switch-applet**[/COLOR]

This may take a minute or so. After it completes, we will reinstall the xserver and also install the ATI drivers. (Note that gnome-session and fast-user-switcher-applet are specific to Ubuntu. Variants like Kubuntu and Xubuntu will not need to install them because they are not part of your desktop environment)
**[COLOR=Red]sudo apt-get install xserver-xorg fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx libdrm2=2.3.1-0build1 gnome-session fast-user-switch-applet=2.24.0-0ubuntu6[/COLOR]**

When everything is finished installing, you will want to open up**[COLOR=Red] Synaptic Package Manager and lock all of the xserver-xorg*, fglrx*, xorg-driver-fglrx, libdrm2, gnome-session, and fast-user-switch-applet packages at their current version.[/COLOR]** This is done by selecting the package then going to the “Package” menu and clicking on “Lock Version”. You can also do this in the terminal by running:
[COLOR=Red]**sudo su**[/COLOR]

then
**[COLOR=Red]echo 'package-name hold' | dpkg --set-selections[/COLOR]**

Make sure to repeat the last command for each package that was installed by the previous commands. (This should total to about 47 packages or so.)


 Once all of the xserver and ATI driver packages have been locked, run
**[COLOR=Red]sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list[/COLOR]**
and restart your computer.



This has worked a charm and 9.04 detects the ATI card. Everything works perfect, apart from I cannot get the S-Video out connection to work.


Hope someone can help! 

thanks in advance,

Y.

---

### Post by Aimen on 2009-10-10
Thanks but I've a problem...

When I try to boot Ubuntu so can I see the boot picture but after when it's load done, the picture look so wired... No, I didnt update but first it's black, then it come some wired stuff on the screen, how can I fix that?

I'm new here and sorry for my bad english, I'm from Sweden!

---

### Post by AgentY on 2009-10-10
Hi. Im not sure if this is the problem you're encountering, but thought I'd post the following just incase. (I installed my ATI 200M without needing to do this, but someone had posted the comments I have pasted below).




 After you restart, make sure to go to the Hardware Drivers manager under the &#8220;System&#8221; menu: Administration > Hardware Drivers and enable that ATI driver and reboot again.

Comment from user:[INDENT]

I did run into one issue- after activating the ATI driver and rebooting, I got a great big watermark in the bottom right corner of my screen with an AMD/ATI logo warning me of &#8220;Unsupported Hardware&#8221;.  If anybody else runs into this, this is how I fixed it:
 1. Download the 9.3 legacy driver package from ati at this page:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&amp;product=2.7.4.3.3.3.1&amp;lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&amp;product=2.7.4.3.3.3.1&amp;lang=English)
 2.  Extract (don&#8217;t install!) the files from the 9.3 package to a folder with a command like:
sh ati-driver-installer-9-3-x86.x86_64 &#8211;extract driverfiles 
3.  Replace your ATI &#8216;control&#8217; file with the one from this 9.3 package:
 First back up your existing file just in case:
sudo cp /etc/ati/control /etc/ati/control.backup
 Then copy the new file in place:
sudo cp driverfiles/common/etc/ati/control /etc/ati
 4.  Reboot and profit!  No more watermark.




Let me know if this resolved your problem or not, or supply a screenshot if possible.


Best of luck, Y.


[/INDENT]

---

### Post by Aimen on 2009-10-10
> **AgentY said:**
> Hi. Im not sure if this is the problem you're encountering, but thought I'd post the following just incase. (I installed my ATI 200M without needing to do this, but someone had posted the comments I have pasted below).




 After you restart, make sure to go to the Hardware Drivers manager under the “System” menu: Administration > Hardware Drivers and enable that ATI driver and reboot again.

Comment from user:[INDENT]

I did run into one issue- after activating the ATI driver and rebooting, I got a great big watermark in the bottom right corner of my screen with an AMD/ATI logo warning me of “Unsupported Hardware”.  If anybody else runs into this, this is how I fixed it:
 1. Download the 9.3 legacy driver package from ati at this page:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&amp;product=2.7.4.3.3.3.1&amp;lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&amp;product=2.7.4.3.3.3.1&amp;lang=English)
 2.  Extract (don’t install!) the files from the 9.3 package to a folder with a command like:
sh ati-driver-installer-9-3-x86.x86_64 –extract driverfiles 
3.  Replace your ATI ‘control’ file with the one from this 9.3 package:
 First back up your existing file just in case:
sudo cp /etc/ati/control /etc/ati/control.backup
 Then copy the new file in place:
sudo cp driverfiles/common/etc/ati/control /etc/ati
 4.  Reboot and profit!  No more watermark.




Let me know if this resolved your problem or not, or supply a screenshot if possible.


Best of luck, Y.


[/INDENT]

I can't see the deskop after bootup
[http://ubuntuforums.org/showthread.php?t=1287749](http://ubuntuforums.org/showthread.php?t=1287749)
Have made a own thread and maybe gonna make a video what happend.

---

### Post by AgentY on 2009-10-10
Did you follow the steps EXACTLY? Did you [B][COLOR=Red]lock all of the xserver-xorg*, fglrx*, xorg-driver-fglrx, libdrm2, gnome-session, and fast-user-switch-applet packages at their current version.

There are about 47 packages or so..
[/COLOR][/B][COLOR=Red]
[COLOR=Black]It may be best to paste exaclty what you did prior to your problem on your post to get better feedback.[/COLOR][/COLOR][B][COLOR=Red]
[/COLOR][/B]

---

### Post by AgentY on 2009-10-10
Has anyone managed to get thier S-Video connection to work yet on old ATI cards with the OLD driver set? (as details in opening post).

---

### Post by AgentY on 2009-10-13
Bump...  I'd really appreciate some help on this one. Tried a few ideas and none so far have worked.

Is this just a problem on older ATI cards or a general ATI or GPU problem?

---

### Post by Maeda_Keiji on 2009-10-14
Hi mates, how can i do this so it can work on Kubuntu? 
 
Many thanks AgentY i was getting a little nervous for not being able to use my laptop with it's full capacity :)

---

### Post by Maeda_Keiji on 2009-10-14
I haven't tested the S-Video but I do know that glxgears runs bether now, it gives me 1040fps :DD while using the ati driver in Kubuntu 8.04 it doesn't go past 700fps not even close :s

I am receiving some erros while loading and exiting the glxgears:

Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
4209 frames in 5.0 seconds = 841.747 FPS
5085 frames in 5.0 seconds = 1016.999 FPS
5205 frames in 5.0 seconds = 1040.389 FPS
5175 frames in 5.0 seconds = 1034.929 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 58 requests (57 known processed) with 0 events remaining.

Does anyone nows how to solve this?? 
Thanks for the post AgentY i didn't get the watermark but I changed the files anyway :):):)

---

### Post by AgentY on 2009-10-15
I'm glad this helped someone other than me! Unfortunatley, its been a long time since I've run Ubuntu (about 5 years!) and most of what i remember is irrelevant to this release. Im still working on my S-Video out though, once I get this working i will update how I did it. If anyone can help either of us please do ;)

---

### Post by Maeda_Keiji on 2009-10-17
It's running very nice, i can run urban terror great, the never putt game also runs great xDDD lolol but i have a problem it seems my laptop response got worst, like switching from directory A to B with alt+tab or while surfing in Firefox and scrolling down, sometimes firefox gets dark before continuing, is it because i'm using JFS instead of EXT3 in a laptop with only 512Mb shared memory?

Thanks for all the help :)

Cheers,
Maeda

---

### Post by virtudtierra on 2009-11-01
> **Maeda_Keiji said:**
> I haven't tested the S-Video but I do know that glxgears runs bether now, it gives me 1040fps :DD while using the ati driver in Kubuntu 8.04 it doesn't go past 700fps not even close :s

I am receiving some erros while loading and exiting the glxgears:

Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
4209 frames in 5.0 seconds = 841.747 FPS
5085 frames in 5.0 seconds = 1016.999 FPS
5205 frames in 5.0 seconds = 1040.389 FPS
5175 frames in 5.0 seconds = 1034.929 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 58 requests (57 known processed) with 0 events remaining.

Does anyone nows how to solve this?? 
Thanks for the post AgentY i didn't get the watermark but I changed the files anyway :):):)
hi,
fglrx works on ati Xpress 200m at ubuntu Karmic?

I hope for you answer because i've ubuntu 8.10, and I want to upgrade.
best regards

Jorge, from Chile

---

### Post by AgentY on 2009-11-01
Due to the fact that there are massive problems with Java Programming in 9.04 and s-video problems, I decided to give 8.04 LTS version a try....

EVERYTHING now works perfect without too many tweaks on my graphics driver set. I'd advise anyone with older hardware to use 8.04 rather than jaunty (9.04).

I know this isn't a fix but thought I'd let others know the EASIEST way to run Ubuntu on older systems.

Best of luck!

Y.

---

