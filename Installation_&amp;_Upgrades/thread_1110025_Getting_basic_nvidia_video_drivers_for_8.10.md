---
title: "Getting basic nvidia video drivers for 8.10"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by neander on 2009-03-29
I have a new installation of 8.10 ubuntu. It's running at 800x600. I have 21" monitors and a geforce 7800gs video card. I don't need anything fancy like dual monitors I just need a decent screen res. It's running inside a virtualbox vm.

I cannot find a coherent explanation of what to do. Some posts seem to imply that the install should have come up with better res than 800x600, and maybe that means there is some problem? With older ubuntu releases I know the specific driver had to be installed before the res was better than 800x600. 

I look in the System-->Administration--->Hardware Drivers and there is nothing listed and no way to add any. I read that that list is supposed to list only proprietary hardware drivers? If so the name should be changed to something like "Proprietary Hardware Drivers".

I look in synaptics package manager and there are 78 listings if I search for nvidia video driver. It does not make any sense to install one over the others, as the descriptions are not very clear unless you already know what they mean.

Also since some people seem to say that new 8.10 installs may come with better res support than I seem to have, I don't know if I should be troubleshooting or just installing the basic driver.

I am surprised that this is so difficult, still.

---

### Post by neander on 2009-03-29
In the 8.10 ubuntu guide it states

>>>>
Install Latest Nvidia/ATI drivers

Upon initial installation and after the first reboot, you will be prompted whether to use the current proprietary nVidia drivers. If you wish to use them, follow the prompts.
>>>>

No, that never happened. So what course do I take now? I would like to manually emulate whatever the normal process should have been.

---

### Post by norwoods on 2009-03-29
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

### Post by neander on 2009-03-29
OK; thank you for that. I am hoping that someone can point me at a single basic package to try...I am not eager to install an entire set of packages when only one might be needed.

Someone must know the answer, or several of them, to this most basic question about nvidia drivers?

---

### Post by neander on 2009-03-30
Someone please lend a hand with this?

---

### Post by VastOne on 2009-03-30
> **neander said:**
> Someone please lend a hand with this?

Norwoods gave you the complete solution

---

### Post by neander on 2009-03-30
He said he installed a mass of packages which seemed to solve it for him, but it wasn't clear to him or me that all of those needed to be installed. I had asked if anyone knew if all of those were required...do you know that they are?

Also, can you or anyone explain why ubuntu didn't offer to use these or related drivers after my initial install? I just want to know, I don't install ubuntu very often. It's supposed to have offered, right?

And who is avenard? It just seems weird that the basic video drivers would be delivered via such a manner. How do I know anything about avenard? Are those regular drivers or advanced/gamer drivers? Doesn't ubuntu have some basic drivers for nvidia they recommend?

---

### Post by VastOne on 2009-03-30
> **neander said:**
> He said he installed a mass of packages which seemed to solve it for him, but it wasn't clear to him or me that all of those needed to be installed. I had asked if anyone knew if all of those were required...do you know that they are?

Also, can you or anyone explain why ubuntu didn't offer to use these or related drivers after my initial install? I just want to know, I don't install ubuntu very often. It's supposed to have offered, right?

And who is avenard? It just seems weird that the basic video drivers would be delivered via such a manner. How do I know anything about avenard? Are those regular drivers or advanced/gamer drivers? Doesn't ubuntu have some basic drivers for nvidia they recommend?

Norwood gave the base install of the nVidia drivers and also said he was not sure if the files he had installed additionally were needed by you but gave them as a fail safe ( I am guessing he looked at all nVidia files installed in synaptic)

They are not installed or offered because of the proprietary nature of these files.  I will agree that video driver installation is something that could definitely improve in Ubuntu, but it is 10,000 leagues better than it used to be.

Avenard is a repository.  Repositories are the backbone of unix/linux/Ubuntu and how updates and files flow.  Avenard is one that is focused on nVidia and multimedia in general and is a very very good one.  I use it to update my nvidia just as Norwood outlined. 

This is new to you now, nut give it time and continue to ask these types of questions, and you will master it in no time...

VastOne

---

### Post by neander on 2009-03-30
OK, thank you for explaining.

here is what that page says, I want to make sure I have the idea

>>>>
To use this repository, first add the signing key

wget [http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key](http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key) && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key

Then add the following line to you /etc/apt/sources.list:

Release/Stable packages: (browse)
deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) intrepid release

etc...
>>>>

The wget line is to be run at the command prompt just as show above? Is that right? The there is a .list file at that location which I add the two line to?

And suddenly I'll have a working nvidia driver kit? Or am I supposed to use synaptic after that?

---

### Post by VastOne on 2009-03-30
> **neander said:**
> OK, thank you for explaining.

here is what that page says, I want to make sure I have the idea

>>>>
To use this repository, first add the signing key

wget [http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key](http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key) && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key

Then add the following line to you /etc/apt/sources.list:

Release/Stable packages: (browse)
deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) intrepid release

etc...
>>>>

The wget line is to be run at the command prompt just as show above? Is that right? The there is a .list file at that location which I add the two line to?

And suddenly I'll have a working nvidia driver kit? Or am I supposed to use synaptic after that?

Yes, run the wget line from terminal

You add the deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) intrepid release to third party software in Synaptic under Setting -Repositories - Third-Party Software

Just click add and then copy that line (deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) intrepid release) and then reload

You will then see that you will have new packages to be installed.  Allow them to be installed and you should be good to go.

If not answer to me here again and I will assist you

---

### Post by neander on 2009-03-30
Thank you so much...I'll give it a shot, does not sound too hard.

---

### Post by neander on 2009-03-30
I did everything. wget succeeded. added the url or whatever it was to the repository. Nothing came up to be installed after reloading. I have searched in the synaptics thing for some of the items that the first reponder listed and most have a solid green box next to then and offer to reinstall...not install.

Well I sure don't get this.

I wonder if the fact that I'm running this ubuntu in a vm (virtualbox) is making is so difficult?

---

### Post by drew2222 on 2009-03-30
I did a test install of 8.10 last week on my system. I used cd install after downloading and burning the iso. I searched for nvidia linux drivers beforehand and saved them to file. As mentioned, after install and reboot, ubuntu offered to install nvivia drivers for me. I did this OK. I am not sure if ubuntu found the drivers on my system or got them from the cd?  Drivers are at:[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html). My install went ok but I am now having probs with dual boot and winxp. Hoping to find an answer here somehwere.

---

### Post by sadicote on 2009-03-30
This is what did it for me; please note that it is not a guaranteed solution but a series of steps that i was very patiently guided to use in my particular case, by the forum members:
I will assume here that you have added the APT lines that are needed to the Software Source in the Third Party Software category.
Go to terminal, type "sudo apt-get update" Press "Enter"
type " sudo apt-get install nvidia-glx-180" press "Enter"
exit terminal and restart.

On restart, open terminal and type "sudo nvidia-xconfig" press "Enter"

exit terminal and restart after saying 3 "Hail Ubuntu"s.:)

---

### Post by neander on 2009-03-30
I tried what sadicote wrote (thanks, and to drew too) and while all the command line stuff seemed to work, after the 2nd reboot I get

(EE) Filed to load module type1 (module does not exist,0)
(EE) No devices detected

I tried some options offered like reconfig nothing helped.

---

### Post by neander on 2009-03-30
Help?

---

### Post by eskararriba on 2009-03-30
thanks to everyone in this thread, seems as if, finally, I could install the 180-driver. 
BUT: after following the steps sadicote mentions, I get the following output: 

-------------------------------
XXX@parker:~$ sudo nvidia-xconfig
[sudo] password for XXX: 

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
----------------------------------
is that what it should look like? is that okay? or what am I supposed to do?

and then: the the 173 and 177-drivers are disabled now, but the 180 doesn't appear under "system-admin-hardware drivers"; should it be there? 

and finally: synaptic shows that the 180-driver and kernel source are installed, while the modaliases and the nvidia-xconfig aren't - should I install them (I don't really know what they are good for, though...)

thanks for your help everyone

---

### Post by neander on 2009-03-30
Can someone who knows about this stuff comment on the idea of trying what drew2222 suggested? Esp after trying the sadicote routine (which has worked for two of us, it seems). I mean is it safe to try that one after attempting the other one, or are they contradictory approaches in any manner?

---

### Post by sadicote on 2009-03-30
You can do a "gksudo gedit /etc/X11/xorg.conf", scroll down to Section "Device" and if nvidia is mentioned as the Driver, you are good to go.

---

### Post by neander on 2009-03-31
It only says

Section "Device"
    Identifier    "Configured Video Device"
EndSection

What would 'good to go' mean? Nothing is good to go, I still have a screen res about the size of a postage stamp! :lolflag:

---

### Post by VastOne on 2009-03-31
> **neander said:**
> It only says

Section "Device"
    Identifier    "Configured Video Device"
EndSection

What would 'good to go' mean? Nothing is good to go, I still have a screen res about the size of a postage stamp! :lolflag:

This implies that you do not have the nVidia drivers installed.

Go to Synaptic and search for nVidia and let me know if nvidia-180-libvdpau is an option

This is how I install my nVidia drivers

1. removing all nvidia related packages (which allowed X to realize why it wasn't working and build a barebones xorg.conf)

Code:

sudo apt-get remove --purge nvidia*

(to clean all nvidia beforehand)

Go to this site to get hte latest nVidia drivers  

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Make sure you select either the correct architect 32 or 64 bit

Save the file to your desktop

Once the package was downloaded, do ctrl+alt+F1 or ctrl+alt+f2 in order to get to a command line outside of x and stopped x with

Code:

sudo /etc/init.d/gdm stop

code:

CD Desktop

Code:

sudo sh NVIDIA(then I press TAB so I don't have to type the whole filename out)

Then follow the on screen instructions answering yes to every question

once it tells you that you have installed the drivers you will need to turn X back on with

Code:

sudo /etc/init.d/gdm start

This will prompt you to log back in

Go then to System Preferences and Screen Resolution to see of you can change to a higher resolution

Let me know....

---

### Post by drew2222 on 2009-03-31
> **neander said:**
> Can someone who knows about this stuff comment on the idea of trying what drew2222 suggested? Esp after trying the sadicote routine (which has worked for two of us, it seems). I mean is it safe to try that one after attempting the other one, or are they contradictory approaches in any manner?

Neander,
How are you getting on with this? Is your graphics card an SLI card? Mine is, (mainboard ASUS A8N-SLI)and there is a setting in BIOS to select which card slot to use first, just a thought.

---

### Post by neander on 2009-03-31
Hi you guys. I won't have time to try anything for another half day or so, but when I do I'll report back with the results...thanks for helping.

---

### Post by sadicote on 2009-03-31
For full details of how i finally managed to get those drivers in, go to [http://linuxbasics.org/forum/index.php?PHPSESSID=f7547d1f3296957712d26983f9eb6c9c&topic=358.msg1503#new](http://linuxbasics.org/forum/index.php?PHPSESSID=f7547d1f3296957712d26983f9eb6c9c&topic=358.msg1503#new). I refrained from citing this link before as i thought it might confuse you. Hope it helps.

---

### Post by neander on 2009-04-01
I had network interface issues with virtualbox but those are (maybe) resolved now, will get back to trying the nvidia fix.

---

### Post by thenewmexican on 2009-04-02
Did anyone here actually get the new NVIDIA X64 drivers to work ??

I have come to the conclusion that the NVIDIA X64 drivers simply will
not work. Its a waste of time attempting any permutation of instructions.

I did an install of 8.10, the 32bit version. Then. Installed the newest
NVIDIA 32bit version. Guess what. No problems what so ever.


So. There you have it.

---

### Post by neander on 2009-04-02
The card in the system is a GeForce 7600GS. I got the the part in VastOne's instructions where the nividia 180.44 package is being run. But immediately I see a warning that I don't have a nvidia gpu which is supported by the nvidia linux driver. But this 180.44 is the one recommended by the nvidia site for my card.

I'm not sure if I should proceed with the install...probably not. I'll see if I can find a better nvidia file to work with. The readme file for 180.44 says the GeForce 7600 GS is supported. I don't get it. I tried letting this driver compile a custom mix or whatever the term might be and that failed too.

---

### Post by dragondrop on 2009-04-03
The --purge option did the trick.
The only additional thing I had to do was to put in the "BusID "X:X:X"" in xorg.conf for the graphic card output by command lspci.

---

### Post by neander on 2009-04-04
Still stuck on this. I've ordered a new video card, but still curious to know if there might be a fix?

---

### Post by Anbin89 on 2009-04-05
Hey guys. I am using Jaunty at the moment. At first the graphics was working fine until i installed the latest drivers. Nothing works for me including 'nvidia-xconfig'. I tried to follow the method above. But i get errors saying something about cannot find kernel source path or something

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Apr  5 22:25:04 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID
   '20902' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).

this was what inside the log. Any help is deeply appreciated! Thanks in advance

---

### Post by neander on 2009-04-07
To change tactics a bit - isn't there some way to get better than 800x600 using plain, non-nvidia drivers? I don't need more than a couple of steps better than 800x600.

---

### Post by onering on 2009-04-07
> **neander said:**
> To change tactics a bit - isn't there some way to get better than 800x600 using plain, non-nvidia drivers? I don't need more than a couple of steps better than 800x600.

I have not done this in a while and am not in front of my Ubuntu box right now but it goes somehting like this...

Edit your xorg.conf file like this: "gksudo gedit /etc/X11/xorg.conf"

Then scroll down to section where all of the screen resolutions are.  In your case you will probably only have one or two. Then manually add in a few more like 1024x768 and 1280x1024.  I can't remember if you can set the default right there in the xorg.conf file to be 1024x764.  If you don't see a spot to set the default then just save the file and reboot.  You should them see the added resolutions in Ubuntu when you go to change the screen resolution.

Hope this helps.

---

### Post by neander on 2009-04-07
This is the content of that file, has nothing in it about screen res:

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

I'll fish around for whatever I can find about manually setting screen res options, but just in case you can remember what it is...Thanks for your input.

---

### Post by onering on 2009-04-07
> **neander said:**
> This is the content of that file, has nothing in it about screen res:

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

I'll fish around for whatever I can find about manually setting screen res options, but just in case you can remember what it is...Thanks for your input.

This is what I'm talking about but your file does not have anything like this.  I need to look into this some more.
```

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes   "1024x600" "800x600" "640x480"
                Virtual 2048 2048
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes   "1024x600" "800x600" "640x480"
                Virtual 2048 2048
        EndSubSection
EndSection

```

---

### Post by neander on 2009-04-07
Thanks...I've tried a couple of variations based on what I found here in the forums but no luck so far. I will be interested to hear any more you find out about this.

Question, is 8.10 more difficult to configure video for that say 8.4? Honestly, it's kind of freaking me out that just getting a decent screen res takes a week or two, if the effort even ends in success. If there is an active ubuntu that will just work at any decent screen res, I will consider starting from scratch. I think I had 7.4 working without anything like this kind of toil, and I while I'd prefer to have a shiny new version of U, right now I just need one that works.

---

### Post by norwoods on 2009-04-08
i finally get it, you are setting this up in a virtual environment, not as the host. you need to install a VirtualBox Guest Additions video driver aqs described in the following VirtualBox documents.

from VirtualBox Frequently Asked Questions for end users (User FAQ)

  * "How come it doesn't detect my nVidia/ATI/whatever graphics card?" 
    Because the guest sees a virtual graphics card, not the host graphics card. The virtual graphics card provides the necessary VESA and VGA features to make the guest operative systems work OK. Additional features, like higher resolutions, is provided by the graphics driver included with the guest additions. More details on how to install guest additions and features of the virtual graphics card can be found in the manual.

from VirtualBox User Manual
4.1 Introduction
As said in chapter 1.1, Virtualization basics, page 8, the Guest Additions are designed to be installed inside a virtual machine. They consist of device drivers and system applications for the guest operating system that optimize the guest for better performance and usability.  The VirtualBox Guest Additions for all supported guest operating systems are provided as a single CD-ROM image file which is called VBoxGuestAdditions.iso.  To install the Guest Additions for a particular VM, you mount this ISO file in your VM as a virtual CD-ROM and install from there.
Please see chapter 1.5, Supported guest operating systems, page 15 for details on what guest operating systems are fully supported with Guest Additions by VirtualBox.  The Guest Additions offer the following features:
Better video support While the virtual graphics card which VirtualBox emulates for any guest operating system provides all the basic features, the custom video drivers that are installed with the Guest Additions provide you with extra high and non-standard video modes as well as accelerated video performance. In addition, with Windows and recent Linux, Solaris and OpenSolaris guests, when the Guest Additions are installed, you can resize the virtual machine’s window, and the video resolution in the guest will be automatically adjusted (as if you
had manually entered an arbitrary resolution in the guest’s display settings).  For Linux and Solaris guests, the Xorg server version 1.3 or later is required for automatic resizing (the feature has been disabled on Fedora 9 guests due to a bug in the X server they supply). The server version can be checked with Xorg -version.

---

### Post by neander on 2009-04-08
Oh. Well let me check that out and see what happens. Thanks again.

---

### Post by neander on 2009-04-08
norwoods, you saved the day. Thanks.

I get some ok screen resolution now (up to 1360x768). My xorg.conf is still more or less naked ie does not ref nvidia anything. I'd be ok with what I have now, but just for fun, what would be the simplest way to try to get nvidia drivers at this point? This one, offered by sadicote a week ago or so?

>>>>
I will assume here that you have added the APT lines that are needed to the Software Source in the Third Party Software category.
Go to terminal, type "sudo apt-get update" Press "Enter"
type " sudo apt-get install nvidia-glx-180" press "Enter"
exit terminal and restart.
On restart, open terminal and type "sudo nvidia-xconfig" press "Enter"
exit terminal and restart
>>>>

---

### Post by norwoods on 2009-04-09
what you referenced is an easy way to get an nvidia driver but you cannot access the nvidia hardware directly in a virtualbox guest so i do not know what you want an nvidia driver for.

---

