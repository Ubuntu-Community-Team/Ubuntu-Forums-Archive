---
title: "HOW TO Install Nvidia driver Hardy 8.04"
date: 2008-08-05
forum: General Help
---

### Post by nbayiha on 2008-08-05
[SIZE="2"]**After realizing that a lot of person had problem installing NVIDIA Driver series 8 and 9 on Hardy . I decide to open this Thread. Even if you don't find it useful , at least i hope it will be the only place where you will post the problem you encounter during the installation , so i(we) will try to resolve it , instead of having a thousand of thread around .**[/SIZE]

**I.** [SIZE="2"]**_Prerequisites_**[/SIZE]
[LIST]
[*]NVIDIA Graphic Card
[*]Hardy Heron installed 8.04
[*]Internet Connection
[/LIST]
**How to know if you have a NVIDIA graphic card . Paste the command under in the terminal** ```
lspci | grep -i nvidia 
```
**It should printed out a line of text with the name of your card.**

**II.** [SIZE="2"]**_Driver Version_**[/SIZE]
There are three version of the restricted driver in the repositories
[LIST]
[*]Nvidia-glx-legacy
[*]Nvidia-glx
[*]Nvidia-glx-new
[/LIST]

**III.** [SIZE="2"]**_Faster/Easier Way to Install_**[/SIZE]

[LIST=1]
[*]Go to **[SIZE="2"]System[/SIZE]->[SIZE="2"]Administration[/SIZE]->[SIZE="2"]Hardware Driver[/SIZE]** and check the box to enable the driver **_*if it's provided*_** .
You can check Here Visually how to do it .
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)


[*]If the driver are not provided , then **_try to install them throw Envy_**.
```
sudo apt-get install envyng-gtk
envyng-t
```
then press 1, install and reboot .
And You are good to go :)
[/LIST]

**IV.** [SIZE="2"]**_ Tricky Way After Clean Installation_**[/SIZE]

**_ PS _: *If the first and the second method didn't work then you can use this one. Otherwise i recommend you to try them first. Cause they are easier and you don't need to do some manual change*.**

So we understand that the method above didn't work, so You should start by..

[LIST=1]
[*]First uninstall the envy package if you installed them, otherwise just skip this step . ```
 sudo apt-get remove envyng-gtk 
```
[*]Make sure you have the build-essential installed ```
sudo apt-get install build-essential 
```
[*]Download from NVIDIA the latest driver of you card.

_**For the 8 series(8xxx) is this one :**_  [SIZE="2"] _[http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)_ or this one _[http://www.nvidia.com/object[/SIZE]_/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object[/SIZE]_/linux_display_ia32_173.14.12.html)

_**For the other series(9xxx,7xxxx) : ** _Just go to this web page and download the one for you [SIZE="2"]_[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)_[/SIZE].

 
[*] We are going to kill the gdm (gnome), so i will advice you to write down a paper the following command. 
```
sudo /etc/init.d/gdm stop
``` that will kill gnome or ctrl+alt+F1.
You should now log in + password.


[*] Go where you downloaded the NVIDIA driver. Mine was in the desktop so i had to do this 
```
 cd /home/nbayiha/Desktop 
``` But yours can be in your home directory . Just use the command ```
ls
``` to be sure that the driver are in the right directory.


[*] Then ```
sudo sh NVIDIA*
``` 
Accept the configuration and the backing up of the xorg files.

*[SIZE="1"]_PS:_ If you had in this step some problem with telinit just do ```
sudo telinit 3 
```[/SIZE]*


[*] After the installation is complete just restart gdm 
```
 sudo /etc/init.d/gdm start 
```

[*] Now we will edit your xorg.conf go to .
[SIZE="2"][B]Application->System Tool->NVIDIA X Server Settings->X server Display configuration-> Save to X Configuration File(click on it,down on you right)->show preview (copy all the text inside preview).
[/B][/SIZE]


[*]Now backup your xorg.conf 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backUp 
```


[*]```
gksudo gedit /etc/X11/xorg.conf
```

And delete all the file and paste what you copy in step 8 . 

Save and You are Good to go .
[/LIST]

**V.** [SIZE="2"]**_ Tricky Tricky Way After Mainly attempt :KS _**[/SIZE]

[LIST=1]
[*]
First make sure everything **_comporting NVIDIA is uninstall_**, if so uninstall them from the repository(nvidia-setting nvidia-glx nvidia-glx-new....) , just remove all of them.
now follow those command step by step , better if u write it down cause we are going to kill the server. 

[*]Download the NVIDIA driver from the web page [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and save them in your home directory.

[*]We are going to  disable the NVIDIA driver in the repository ,so they won't have conflicted problem with the one we download.
```
gksudo gedit /etc/default/linux-restricted-modules-common 
```
 edit the DISABLED_MODULES line so it will look like this

> DISABLED_MODULES="nv nvidia_new" 

[*]Note in a Paper the following command cause we are killing gdm .
```
sudo /etc/init.d/gdm stop 
``` or ctrl+alt+f1 Log+passwd 

[*]```
sudo telinit 3 
```
go to the folder where you downloaded the NVIDIA driver.

[*]```
sudo sh NVIDIA* 
``` 
accept everything.

[*] Reboot and you are good to go .
[/LIST]

 [SIZE="2"]**_ Problems_**[/SIZE]

1- For those who lost their old xorg.conf just do it to get it back 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 

2- For those using Laptop(Notebook) with a Geforce Go card , if you hear the startup sound without nothing appearing on the screen , then you should check your xorg.conf and edit it that way *_(just do it after trying the three way provide above )_* 

     *Reboot and use recovery mode , log in +passwd 

     *```
sudo nano /etc/X11/xorg.cong
``` Find the line with Section "Screen"  insert a new line that say 
Option "UseDisplayDevice""DFP" 
Save the file and reboot .


[SIZE="2"]If one of the method work partially or didn't work at all , report in which level you encounter the problem and we will figure out what to do :lolflag: . [/SIZE] 

Have A good Day :guitar:

---

### Post by NT4usB on 2008-08-05
> 

1- For those who lost their old xorg.conf just do it to get it back 
```
sudo dpkg-reconfigure -phihg xserver-xorg
``` 


s/b -phi**gh**

---

### Post by nbayiha on 2008-08-05
Thanks Dude :)

---

### Post by logos34 on 2008-08-05
nbayiha,

Nice tut.

Do you know why my driver install (NVIDIA-Linux-x86_64-173.14.09-pkg2.run) successfully builds the kernel interface module but consistently fails at the last, complaining about 'libnvidia.173...so.1' and libGL* files not being in expected place?  It's killing me because I just compiled a custom kernel the other day, managed to install the -.09 driver, but when I attempted it two days later on another installation it kept failing.

her are the two messages:

-> > done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
ERROR: The runtime configuration check failed for the library
       'libnvidia-tls.so.173.14.05' (expected:
       '/usr/lib32/tls/libnvidia-tls.so.1', found:
       '/usr/lib32/libnvidia-tls.so.1').  The most likely reason for this is
       that conflicting OpenGL libraries are installed in a location not
       inspected by `nvidia-installer`.  Please be sure you have uninstalled
       any third-party OpenGL and/or third-party graphics driver packages.
-> done.
-> Runtime sanity check failed.and 
> 
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 Invalid module format

it can't be because of a GCC version mismatch, because the kernel sources match the current one.

---

### Post by cowboyup6983 on 2008-08-05
i wonder what drivers i have install then because i use envy to install my drivers and it was way more simpler that stuff above. i have all my 3D effects and everything?

---

### Post by logos34 on 2008-08-05
> **cowboyup6983 said:**
> i wonder what drivers i have install then because i use envy to install my drivers and it was way more simpler that stuff above. i have all my 3D effects and everything?

When I used EnvyNG a week ago the default was 173.14.09

---

### Post by nbayiha on 2008-08-06
@cowboyup6983 If you did succeed to install with envy them you have the 3D effect installed. Don't forget that The first step in this how to mention to use envy first  before trying anything else .

@logos34
> /usr/lib32/libnvidia-tls.so.1'). The most likely reason for this is
that conflicting OpenGL libraries are installed in a location not
inspected by `nvidia-installer`. Please be sure you have uninstalled
any _third-party OpenGL and/or third-party graphics driver_ packages. 
Before doing anything else first uninstall any driver you have installed.  I mean remove first the driver you install in the kernel you compile ,> managed to install the -.09 driver remove them , and then try again to install using the method that suit you.

---

### Post by logos34 on 2008-08-06
Yeah, EnvyNG install was a success (but I haven't tried it again since), but why can't I seem to get the driver in manually?

I did do all the recommeneded steps (I think), like uninstalling nvidia-glx-new and nvidia-settings.  As far as I know, the nvidia graphics drivers are the only ones using openGL.  I even checked /usr/lib directories after uninstalling the (glx) 169... driver, and all the libnv* and libGL.s0* etc files were gone.  Then I tried the manual install of the 173....09 driver and it failed for either of the reasons I gave.  I would then do 'sudo sh NVIDIA* --uninstall', then check the directories for any leftover files.  I think it leaves behind the libGL files, so I took out those and reinstalled.  Same problem. (even with the very latest .12 driver).

As I say, this is perplexing because I successfully installed the .09 driver on a nearly identical test partition with a custom compiled kernel.  But when I tried it again on my regular installation, it failed.

---

### Post by nbayiha on 2008-08-06
@logos34 
I think you have an and old install conflict problem, that's why you can't install the new one. 
> If either of nvidia-glx-legacy/nvidia-glx-new are installed a dotfile is created in /lib/linux-restricted-modules/ . Even after these packages are uninstalled the dotfile will remain and may frustrate efforts to use the nvidia-glx package

Try to do this. 
go to your   ```
cd /lib/linux-restricted-modules
```
then ```
ls -la
```
and there check if you have some hidden nvidia file  something like 
 
> .nvidia_new_installed file
If it's the case remove that file , and after that try again the tricky way .
Hope that will help you.

---

### Post by logos34 on 2008-08-06
ok, thanx, I'll remove it and try again.

---

### Post by nbayiha on 2008-08-06
Don't forget to report if you succeed.

---

### Post by logos34 on 2008-08-06
sorry, didn't work.  

Tried EnvyNG again and it completed successfully, but X server won't start, despite my best efforts to fix xorg.conf

I think there's something wrong with the kernel.  

I'm going to compile a new one.

---

### Post by ellalan on 2008-08-06
Hi
Could you please tell me whether I should install the drivers for Integrated Nvidia GeForce 6150 as well. I am asking because I am getting a Motherboard with Integrated graphics and want to be prepared. Thank you.

---

### Post by nbayiha on 2008-08-06
If you are getting a motherboard with an integrated graphic card. Than i guess it will be the Intel one. cause Nvidia and ATI doesn't come integrated. 
If it's the case then you don't need to install any driver.
But if your are planning to buy a nvidia graphic card, then use one of the method above ,especially the easy and faster one should set You Up :) .

---

### Post by kris99466 on 2008-08-08
Hi, i got a problem installing my NVIDIA 9100G M. Can anyone tell how to get the driver? iam using Hardy...

I also begging for someone that know how i can have my sound card driver...  iam using Acer Aspire 4530... thx for sharing ^^

---

### Post by nbayiha on 2008-08-08
Hi Dude did you read about this ?

[http://www.nvidia.com/object/geforce_9100m_g_mgpu.html](http://www.nvidia.com/object/geforce_9100m_g_mgpu.html)

---

### Post by kris99466 on 2008-08-08
Hmm.. i still don't get it...

---

### Post by nbayiha on 2008-08-08
You can Use this driver Here. 
[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

And if you want to read a little about which driver support those card

[http://packages.ubuntu.com/intrepid/nvidia-glx-173](http://packages.ubuntu.com/intrepid/nvidia-glx-173)

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/173.14.09-0ubuntu4](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/173.14.09-0ubuntu4)

hope that will help you. Don't forget to use the tricky way .

---

### Post by keelon72 on 2008-08-08
Hi,

I have trouble with my Sparkle nvidia 9600 GT (512 mb) card. Did a fresh install of Hardy. It works fine in 2D, but glxinfo displays that there is no GL support, no Direct Rendering anyway.

Updated my system, turned on the Proposed repository, installed EnvyNG. When I tried to install the new driver with EnvyNG, Envy threw an error:

***Exception: EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy’s hardwaredetection failed. You can try the manual installation at your risk.***

A bit strange, I was under the impression that 9600 GT is supported with the 173.14.12 driver :-k.

I went ahead and install the driver manually, but this resulted in a distorted screen, with the low resolution mode window.

Did a rollback on my xorg.conf file with the NV driver and rebooted, no problems, but still no Direct Rendering available.

I also read a bunch of tutorials, but I can’t remember any of them addressing a working Direct Rendering mode, other then via EnvyNG.

I also saw that there was a beta driver from nvidia (177.13), does this help my case in anyway?

The only reason I bought this card was so I could play World of Warcraft through Wine with higher resolution and better performance.

Please, any solutions/pointers anyone?! Hope that I don’t have to wait for Inrepid to get it to work.

lspci -n | grep 300
02:00.0 0300: 10de:0622 (rev a1)

lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)

---

### Post by nbayiha on 2008-08-09
@keelon72
[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

This driver is the one supporting your graphic Card . so i don't know why it's not working. Did you try all the method i mention in the thread ? I mean the tricky way and the tricky tricky way ?

And did you read what @logos34 wrote too before. Maybe you have to the same conflict problem . 

Anyway first try all the method mention in the start of the thread. and report if you have a problem .

---

### Post by keelon72 on 2008-08-09
@nbayiha

Thank you for your reply.

No, I haven't tried the Tricky or the Tricky Tricky way. I must have misunderstood, I thought that thees ways (Tricky & Tricky Tricky) wouldn't get me a working Direct Rendering mode, I thought that only the EnvyNG install could do that. Sometimes ignorance isn't a bliss. Sorry, my mistake.

I'm a bit frustrated, have installed Hardy six times lately after trying various guides. That's why I'm a bit careful with trying before I know IF the guide will give me the desired solution. 

**[SIZE="3"]Question:[/SIZE]**
**Will I get a working Direct Rendering mode if I succeed with either the Tricky or the Tricky x 2?**

[I]
Thank you all for the free time you are giving into the open source community.[/I]

---

### Post by nbayiha on 2008-08-09
One of the way in the thread will set you Up. Especially in you case i will advise you to use the tricky way .

---

### Post by kris99466 on 2008-08-09
Iam here just wanna thank you... It's working, My NVIDIA 9100 m G working ^^ thanks alot dude...

---

### Post by kris99466 on 2008-08-09
Iam too excited that my NVIDIA finaly working, i forgot that i still got problem with my sound card... how can i make it work???

---

### Post by nbayiha on 2008-08-09
which sound card do you have ?

---

### Post by kris99466 on 2008-08-09
How can i check my sound card?? i used lspci and written:
Audio device: nVidia Corporation Unknown device 0774 (rev a1)

---

### Post by nbayiha on 2008-08-10
Follow this thread and you should have all fixed .

[http://ubuntuforums.org/showthread.php?t=766683&highlight=DVD+player](http://ubuntuforums.org/showthread.php?t=766683&highlight=DVD+player)

---

### Post by keelon72 on 2008-08-10
Now I have tried both the Tricky and the Tricky Tricky. But the result is the same .... :( a distorted screen with dialog window for low resolution mode.

I couldn't complete the Tricky guide, because I didn't get a working 2D mode, so I couldn't do step 8, copy info from NVIDIA X Server Settings.

Will the result be the same if I used this command?
#> sudo nvidia-xconfig

What am I doing wrong?! I use LVM2, could this be the problem? 

One thing I did notice was that the kernel module that the nvidia installer created, wasn't recorded in the /etc/modules file. Should it be added to this file? I tried to add a line with 'nvidia' without the quotes. Still nothing.

---

### Post by logos34 on 2008-08-10
new kernel compile does not solve the problem for me.

Just for the heck of it I tried to install the 173...12 version on my regular install, built the kernel interface module against the linux-headers-2.6.24-19-rt.  It did build it, but again failed the 'sanity check' at the end (libGL files errors).  So I ran EnvyNG and that installed the .12 driver fine, BUT I still cannot find a working xorg file--X server refuses to even start.  My old one (i.e. that works with nvidia-glx-new 169. driver) is no good.  

Is there a sample xorg.conf file somewhere I can copy that will work with hardy?  'cause I really don't have the time or patience to do trial-and-error edits the file until it works.  The -glx-new driver is just fine for my needs, but all the same I'd like to know how to fix this in the unlikely event I get a new video card and need the proprietary driver

---

### Post by nbayiha on 2008-08-11
@keleon72
just try to check if there is conflict with old driver nvidia.
if you didnt read all the thread here is something that can interest you.
> 
If either of nvidia-glx-legacy/nvidia-glx-new are installed a dotfile is created in /lib/linux-restricted-modules/ . Even after these packages are uninstalled the dotfile will remain and may frustrate efforts to use the nvidia-glx package


Just check in /lib/linux-restricted-modules and list. 
if you see a dot with nvidia a the end then you should erase that file. so try to uninstall everything with nvidia then try the easier way.

---

### Post by Kouki on 2008-08-11
Hi, I tried you instructions and it was all going well until

```
sudo sh NVIDIA*
```

Then it came up with this stuff:

No precompiled kernel interface was found to match your kernel.

None found on the NVIDIA FTP site.

this means that the installer will need to compile a kernel interface for your kernal.

The CC VErsion check failed

The compiler used to compile the kernel (gcc4.1) does not exactly match the current compiler gcc4.2).  THe linux 26 kernel module loader.


I decided to uninstall gcc4.1 using synaptic and tried again but it returns the same error message.  By the way I have no idea what I'm doing but I've tried all other methods including envy.

---

### Post by Ripfox on 2008-08-11
> **kris99466 said:**
> How can i check my sound card?? i used lspci and written:
Audio device: nVidia Corporation Unknown device 0774 (rev a1)

Same here...tried to switch to oss but they all sound scratchy. I used Envy to install the Nvidia driver which works great.

Compaq CQ50-107NR.

lspci seems to think all of my devices are unknown!

> 00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0845 (rev a2)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I got my broadcom wireless working great with th "wl" driver in Jockey but I had to use the manual install of the first Nvidia driver on the list in Envy, as it did not detect my card automagically.

Help with the scratchy sound! :) I don't want to return another laptop b/c of Hardy support...:(

---

### Post by keelon72 on 2008-08-11
I've got it working at last!! :lolflag: Thank you all for the help!

Asked around and a friend said that when he installed this card (9600 GT) in Windows the Nvidia driver warned that there wasn't enough power to the card.

I bought a bigger PSU 450W, my old was a 350W. Reinstalled Hardy 8.04.1, updated, installed EnvyNG (BTW: the 173.14.12 driver is in the hardy-updates now, no need to activate hardy-proposed) and choose the manual install. And that was that. 

glxinfo | grep direct
direct rendering: Yes

Thanks a bunch for this guide.

---

### Post by Ripfox on 2008-08-11
Do you think that switching to a different Nvidia driver will affect the audio? I hate to uninstall something that even half works...

---

### Post by nbayiha on 2008-08-14
Hi guys sorry for the delay but i am actually not at home , you know it's holiday time :lolflag: so i am answering from a cybercafe. Anyway 

@Ripfox
No it won't affect the audio if you switch. But why do u wan to switch ? Are you having some problem with the actual driver or are you having problem with the audio card ? if it's the case try to search in the forum how to solve problem with audio card.

@Keleon72 
GlaD that you got it worked at the end , and always ready to help you in the future with any problem referring to the installation of Nvidia card.

@Kouki
As for you it seems to me that you got problem with the fact that you kernel was compile gcc4.1. so try those solution in order :
    1 - first do this 
     ```
 sudo apt-get install build-essentials 
```
and remove uninstall any  nvidia you find in the repository and then try the tricky way.
    2-Install the gcc 4.2 and gcc-4.2-base package
and tell me if the problem get solve.
    3- If 1 didn't work so try 
        log as root in the terminal  then .
   ```
 CC=gcc-4.2 
export CC 
```

If you encounter any problem just report here

---

### Post by Ripfox on 2008-08-14
Yes the audio got worse after proprietary Nvidia drivers were installed. I took it back and got an Acer that works OOTB. ATI isn't such a bad option anymore...:)

---

### Post by imneal on 2008-08-21
Hello!  

I was in the same boat as ripfox with my video.  I got the latest nvidia driver installed with Envy, and the video works great.  however, I'm getting a completely scratchy sound.  lspci is same as ripfoxes.  

I'm using the onboard GeForce 8200 that is on my Biostar TF8200 motherboard.  It says it also has a realteck ALC888S sound card that is detected if I try to change the device, but the scratchy sound wont go away. 

I can't change my nvidia card without changing the mother board...  Any ideas?


lspci: 
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075c (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0751 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0778 (rev a1)
00:12.0 PCI bridge: nVidia Corporation Unknown device 075b (rev a1)
00:13.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




Any help would be appreciated!! I don't even know where to begin! 

Thanks, 

Neal

---

### Post by BlockBomb on 2008-08-21
Hello I've tried all three methods and they all install just fine until I have to reset the system. during reboot after the Ubuntu loading screen has finished the whole system freezes. sometimes if I'm lucky it make is to the login screen but it just freezes there.  I'm unable to restart the x server.
I'm running ubuntu 8.04.1, with a Biostar t43 series motherboard, intel core 2 duo E8400, and Nvidia GeForce 8800 GT, with a Western digital S-ATA drive.  

I'm fairly new to this Linux world it is fascinating yet frustrating has all get out:).

-here is my xorg.config file before I start any of the installations I don't know if it will help. 

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
```

---

### Post by nbayiha on 2008-08-23
Hi i just went back home today , and i am exhausted :lolflag: too many beer during vacation, anyway i will try to figure out what is the problem with all of you guys.

@BlockBomb 
You may want to uninstall everything you did till now . I mean we have the same graphic card model ,so it's a kind of weird that the tricky way work with me fine and you didn't manage to make it work.
Anyway try this.
First uninstall everything with nvidia in synaptic and check in the _**restricted module for the dot one**_(if you dont know what i mean just read the answer i gave to @Keleon above).
Then try the tricky way and do exactly _the tricky way_ and add this command a the end(i mean after step 6) do this one instead of what is written in the main thread.
```
 sudo dpkg-reconfigure xserver-xorg
```
```
 startx 
```

Edit: and by the way, i just read your xorg and it really strange , the is no nvidia card recognize. Dude i am tire now :D so just try what i wrote and tomorrow we will see.

---

### Post by Lantay77 on 2008-08-23
sudo apt-get install nvidia-settings

---

### Post by BlockBomb on 2008-08-23
Thank you nbayiha, I've just did a clean install just to be sure that my system is set up correctly, in the event that my previous attempts messed up some files.  Right now I'm visiting my grandmother for her birthday and am away from my desktop at the moment but when I return tomorrow I'll try what you suggested and report back here.

---

### Post by celem on 2008-08-25
**WARNING** - If you have a Nvidia 8200 DO NOT use steps I,II or III. You will totally hose your installation. Instead use step IV and make sure that the package downloaded from Nvidia is the 177.13 package. Following those steps will then work correctly.

For the record, I have a BioStar TF8200 A2+ motherboard e/w on-board Nvidia 8200 video and ALC888S sound (which I don't yet have working correctly on Linux).

---

### Post by Arcanius on 2008-08-29
Hi there, im a complete noob to ubuntu and linux. i installed a couple weeks ago with the tricky way, then, with a system update a few days ago, the whole screen was distorted and screwed up majorly, adn always started up in low graphics.

I finally managed to make time to install the tricky tricky way, low graphic mode is history, but the highest resolution i have available is 640 x 480, but in nvidia-settings and in system-preferences-system resolution.

My 9800GTX is detected right in nvidia-settings, as is my Acer 20" monitor, but the resolution won't change for some reason.

Not that the install a few weeks ago was 173.xx, and now its 177.xx

Any ideas on how i can regain my 1680x1050 resolution?

EDIT: Fixed the problem, finally was able to install EnvyNG, and install a driver (173.xx) but now when i set my resolution to 1680 x 1050, there is a pillar o black on the left side of the screen, and the right side is cut off... How can i move the screen to the left, without doing it directly from the monitor?

EDIT2: Sorry for editing again, i fixed the problem by adjusting my refresh rate (51 down to 50) I think this post is just a waste of space, if anybody wants, they can delete it all.

---

### Post by nbayiha on 2008-08-29
Don't worry about the post if you get your problem fixed :lolflag: .
Glad that you manage it by yourself.

---

### Post by Arcanius on 2008-08-29
Well... it wasn't really by myself, a good friend of mine, who uses Linux permenantly, shared his... ideas with me :D

---

### Post by rme8494 on 2008-08-30
> **celem said:**
> **WARNING** - If you have a Nvidia 8200 DO NOT use steps I,II or III. You will totally hose your installation. Instead use step IV and make sure that the package downloaded from Nvidia is the 177.13 package. Following those steps will then work correctly.

For the record, I have a BioStar TF8200 A2+ motherboard e/w on-board Nvidia 8200 video and ALC888S sound (which I don't yet have working correctly on Linux).

Celem or someone else,
I'm hoping you can help me.  Based on your message I followed step IV (I and II did not work).  Everything works great... the resoultion is fantastic and the color is great.  But after I reboot I get a message "ubuntu is running in low-graphics mode your screen and graphics card could not be detected correctly..."

I am running the integrated 8200 chip set as well on my ASUS mobo board.  Any ideas what is happening?

ASUS M3N78-EMH HDMI AM2+/AM2 NVIDIA GeForce 8200 HDMI Micro ATX AMD Motherboard - Retail 

Thanks,
Ryan

---

### Post by nbayiha on 2008-08-31
@rme8494 
I am sure you didn't follow all the instruction till the end. I mean did you save your xorg.conf file ? Try again the thread and do it till 10. The tricky way from 4-10. read carefully the 8 , 9 and 10 step.
Hope that will help you:) , i will here to help you.:lolflag:

---

### Post by rme8494 on 2008-08-31
> **nbayiha said:**
> @rme8494 
I am sure you didn't follow all the instruction till the end. I mean did you save your xorg.conf file ? Try again the thread and do it till 10. The tricky way from 4-10. read carefully the 8 , 9 and 10 step.
Hope that will help you:) , i will here to help you.:lolflag:

nbayiha,
Thanks for your reply.  I did follow all of the tricky steps, but for safe measure I just did them all again.  This includes copying the config file detail from the system tools area and pasting it into the xorg.conf file (after backing it up).  After rebooting I still got the message below...

[IMG]http://i34.tinypic.com/3307g43.jpg[/IMG]

Interestingly enough the files before and after a reboot look the same except for the comments area at the top... the one after reboot says "# nvidia-xconfig:..." and the one before reboot, after your steps are completed state "# nvidia-settings:..." on the comment lines at top.  Everything else in the files are the same.

One thing I just noticed after rebooting and getting the message above.  I went into the system tools --> nvidia x server settings and got the message below.

[IMG]http://i33.tinypic.com/2lpc93.jpg[/IMG]

Thoughts?
Ryan

---

### Post by nbayiha on 2008-08-31
@rme8494 
I think i where is the problem. First i will advise you to first uninstall all nvidia stuff you have installed. 

1- I mean go to synaptics and uninstall any nvidia stuff installed already, remove them all.
 
2- Then read the quote down here and do the same as i wrote in that quote
> @keleon72
just try to check if there is conflict with old driver nvidia.
if you didnt read all the thread here is something that can interest you.
Quote:
If either of nvidia-glx-legacy/nvidia-glx-new are installed a dotfile is created in /lib/linux-restricted-modules/ . Even after these packages are uninstalled the dotfile will remain and may frustrate efforts to use the nvidia-glx package
Just check in /lib/linux-restricted-modules and list.
if you see a dot with nvidia a the end then you should erase that file. so try to uninstall everything with nvidia then try the easier way.

3- Check if you didn't have nvidia new driver disable . I mean do this 
```
gksudo gedit /etc/default/linux-restricted-modules-common
```
and check if you have a line like this one 
> DISABLED_MODULES="nv nvidia_new"
if it's the case just remove nv nvidia or whatever is around the "".

Then restart you computer and try again the trick way. from step 4-10. I hope that will help you. If not report here and we will try my last shot :lolflag:

---

### Post by BlazinNightSkye on 2008-08-31
( Kubuntu 8.04, KDE4.x ) I have a VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2) graphics card. I am currently stuck in 800x600 resolution. I tried using the proprietary driver first, restarted worked for a few seconds then loaded a uncentered 800x600 res with a crash from Kwin, and my monitor saying the input was not supported. So i uninstalled that and tried EnvyNG-Qt, i got the splash screen, the login manager was correct but when i actually signed in i got the same problem. I uninstalled envy and tried an older version of the driver, and still no luck. :confused: I am hoping someone can help me with this, it is quite annoying to work in a res like this when i am not blind. :P

---

### Post by nbayiha on 2008-08-31
@BlazinNightSkye

try what i wrote above .

---

### Post by rme8494 on 2008-08-31
> **nbayiha said:**
> 
1- I mean go to synaptics and uninstall any nvidia stuff installed already, remove them all.

Looking at Synaptic I am not seeing ANY Nvidia stuff installed, at all!  I'm looking in "Installed Applications Only" at the top and then "All" on the left.  Going in alphabetical order, I see nothing named NVIDIA.  Is this right

> **nbayiha said:**
> 3- Check if you didn't have nvidia new driver disable . I mean do this
```
gksudo gedit /etc/default/linux-restricted-modules-common
```
 

Not disabled either.

Haven't looked into number 2 yet.

Ryan

---

### Post by rme8494 on 2008-08-31
> **nbayiha said:**
> 
 
2- Then read the quote down here and do the same as i wrote in that quote


OK, as for your suggestion number 2.  In the /lib/linux-restricted-modules/ directory I only have one directory, "2.6.24-9-generic.  Within that directory I have 3 other folders called:

nvidia
nvidia_legacy
nvidia_new

Should I delete those directories?  Just wanted to double check before I do something damaging.

Ryan

---

### Post by nbayiha on 2008-09-01
Yes remove them all the three , and then try the tricky way. Don't forget to list > ls -la to see if there is no hiden nvidia folder there.

---

### Post by rme8494 on 2008-09-01
ignore what this post used to say... i'm and idiot :D  

working on your suggestion now.

---

### Post by rme8494 on 2008-09-01
nbayiha,
I think the issue is fixed! As you instructed I removed the three nvidia directories in question.  Just for giggles I decided to reboot after I did the removal.  To my surprise after the reboot everything is fixed!  The nvidia logo displays on boot now and I have a nice 1024 x 768 resolution.  I'm not sure what fixed the issue, but I'm guessing removing those directories cleared up some confusion.  I DID NOT have to do the tricky method again, I'm guessing since I already did it before there was no need.

Thanks for all your help.

Ryan

---

### Post by nightwatchman on 2008-09-02
> **nbayiha said:**
> [SIZE="2"]**After realizing that a lot of person had problem installing NVIDIA Driver series 8 and 9 on Hardy . I decide to open this Thread. Even if you don't find it useful , at least i hope it will be the only place where you will post the problem you encounter during the installation , so i(we) will try to resolve it , instead of having a thousand of thread around .**[/SIZE]

**I.** [SIZE="2"]**_Prerequisites_**[/SIZE]
[LIST]
[*]NVIDIA Graphic Card
[*]Hardy Heron installed 8.04
[*]Internet Connection
[/LIST]
**How to know if you have a NVIDIA graphic card . Paste the command under in the terminal** ```
lspci | grep -i nvidia 
```
**It should printed out a line of text with the name of your card.**

**II.** [SIZE="2"]**_Driver Version_**[/SIZE]
There are three version of the restricted driver in the repositories
[LIST]
[*]Nvidia-glx-legacy
[*]Nvidia-glx
[*]Nvidia-glx-new
[/LIST]

**III.** [SIZE="2"]**_Faster/Easier Way to Install_**[/SIZE]

[LIST=1]
[*]Go to **[SIZE="2"]System[/SIZE]->[SIZE="2"]Administration[/SIZE]->[SIZE="2"]Hardware Driver[/SIZE]** and check the box to enable the driver **_*if it's provided*_** .
You can check Here Visually how to do it .
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)


[*]If the driver are not provided , then **_try to install them throw Envy_**.
```
sudo apt-get install envyng-gtk
envyng-t
```
then press 1, install and reboot .
And You are good to go :)
[/LIST]

**IV.** [SIZE="2"]**_ Tricky Way After Clean Installation_**[/SIZE]

**_ PS _: *If the first and the second method didn't work then you can use this one. Otherwise i recommend you to try them first. Cause they are easier and you don't need to do some manual change*.**

So we understand that the method above didn't work, so You should start by..

[LIST=1]
[*]First uninstall the envy package if you installed them, otherwise just skip this step . ```
 sudo apt-get remove envyng-gtk 
```
[*]Make sure you have the build-essential installed ```
sudo apt-get install build-essential 
```
[*]Download from NVIDIA the latest driver of you card.

_**For the 8 series(8xxx) is this one :**_  [SIZE="2"] _[http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)_ or this one _[http://www.nvidia.com/object[/SIZE]_/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object[/SIZE]_/linux_display_ia32_173.14.12.html)

_**For the other series(9xxx,7xxxx) : ** _Just go to this web page and download the one for you [SIZE="2"]_[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)_[/SIZE].

 
[*] We are going to kill the gdm (gnome), so i will advice you to write down a paper the following command. 
```
sudo /etc/init.d/gdm stop
``` that will kill gnome or ctrl+alt+F1.
You should now log in + password.


[*] Go where you downloaded the NVIDIA driver. Mine was in the desktop so i had to do this 
```
 cd /home/nbayiha/Desktop 
``` But yours can be in your home directory . Just use the command ```
ls
``` to be sure that the driver are in the right directory.


[*] Then ```
sudo sh NVIDIA*
``` 
Accept the configuration and the backing up of the xorg files.

*[SIZE="1"]_PS:_ If you had in this step some problem with telinit just do ```
sudo telinit 3 
```[/SIZE]*


[*] After the installation is complete just restart gdm 
```
 sudo /etc/init.d/gdm start 
```

[*] Now we will edit your xorg.conf go to .
[SIZE="2"][B]Application->System Tool->NVIDIA X Server Settings->X server Display configuration-> Save to X Configuration File(click on it,down on you right)->show preview (copy all the text inside preview).
[/B][/SIZE]


[*]Now backup your xorg.conf 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backUp 
```


[*]```
gksudo gedit /etc/X11/xorg.conf
```

And delete all the file and paste what you copy in step 8 . 

Save and You are Good to go .
[/LIST]

**V.** [SIZE="2"]**_ Tricky Tricky Way After Mainly attempt :KS _**[/SIZE]

[LIST=1]
[*]
First make sure everything **_comporting NVIDIA is uninstall_**, if so uninstall them from the repository(nvidia-setting nvidia-glx nvidia-glx-new....) , just remove all of them.
now follow those command step by step , better if u write it down cause we are going to kill the server. 

[*]Download the NVIDIA driver from the web page [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and save them in your home directory.

[*]We are going to  disable the NVIDIA driver in the repository ,so they won't have conflicted problem with the one we download.
```
gksudo gedit /etc/default/linux-restricted-modules-common 
```
 edit the DISABLED_MODULES line so it will look like this



[*]Note in a Paper the following command cause we are killing gdm .
```
sudo /etc/init.d/gdm stop 
``` or ctrl+alt+f1 Log+passwd 

[*]```
sudo telinit 3 
```
go to the folder where you downloaded the NVIDIA driver.

[*]```
sudo sh NVIDIA* 
``` 
accept everything.

[*] Reboot and you are good to go .
[/LIST]

 [SIZE="2"]**_ Problems_**[/SIZE]

1- For those who lost their old xorg.conf just do it to get it back 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 

2- For those using Laptop(Notebook) with a Geforce Go card , if you hear the startup sound without nothing appearing on the screen , then you should check your xorg.conf and edit it that way *_(just do it after trying the three way provide above )_* 

     *Reboot and use recovery mode , log in +passwd 

     *```
sudo nano /etc/X11/xorg.cong
``` Find the line with Section "Screen"  insert a new line that say 
Option "UseDisplayDevice""DFP" 
Save the file and reboot .


[SIZE="2"]If one of the method work partially or didn't work at all , report in which level you encounter the problem and we will figure out what to do :lolflag: . [/SIZE] 

Have A good Day :guitar:

Hello...
'm trying various options since last week & getting stuck.
After all installations etc...A "green colour" screen comes with black vertical lines.
'm using Ubuntu Hardy 8.04.
Card : FX5200 8X Nvidia.
Last I used EnvyNG to install driver,version 173.XX

it will be very kind if you can help me .....

regards,
~

---

### Post by nightwatchman on 2008-09-03
Hello...
'm trying various options since last week & getting stuck.

As soon as I execute ==> "/etc/init.d/gdm start", a "green colour" screen comes with black vertical lines.
Even I tried installing using Envy & through restricted driver screen.

'm using Ubuntu Hardy 8.04.
Card : FX5200 8X Nvidia.
Last I used EnvyNG to install driver,version 173.XX
Processor : AMD64

Please some-one help me, 'm all stuck.

regards,
~

---

### Post by nbayiha on 2008-09-03
@nightwatchman
 
Hi sorry for answering late. Anyway as i can see you are just new with ubuntu. Welcome first :D .
Now try to follow those command i will give you.

I- First go to synaptic(System->Administration->synaptic packagemanager).
There , uninstall everything with nvidia you installed. I mean search > nvidia and if you see some installed , just remove them. 

II- go to this folder ,
```
cd /lib/linux-restricted-modules/
```
then 
```
 ls -la 
```
to list
Then if you see something with nvidia , just remove it. delete everything you will find with nvidia in this folder , even those starting with (.nvidia(hiden file)).

III- Restart you computer then , and then try to use envy in synaptic.

IV- If it doesn't work, then do again step I and II and in step III follow the _**tricky way**_ in my thread using the drivers i provide you down here.

> For 32bit drivers [http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html) take them from here 
> For 64bit drivers [http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html)

Hope that will help ,if not then we will use my lastshot :lolflag:

---

### Post by EoRaptor013 on 2008-09-04
> **nbayiha said:**
> [SIZE="2"]**After realizing that a lot of person had problem installing NVIDIA Driver series 8 and 9 on Hardy . I decide to open this Thread. Even if you don't find it useful , at least i hope it will be the only place where you will post the problem you encounter during the installation , so i(we) will try to resolve it , instead of having a thousand of thread around .**[/SIZE]


Folks, 
Put your hands up and step away from the computer! This is waaay more than any but extreme users need to do. Hardy comes with nvidia drivers in the restricted (or maybe 3rd party) repository. After installation, go to the source manager, under the Administration menu, and enable (check box) the 3rd party and/or restricted repositories. (Not near my machine, so doing this from memory). Once the repository is enabled, simply run the Driver app, also under Administration. Check the nvidia option, then click OK (install?). About 30 seconds later, the native Heron nvidia drivers will be installed. Reboot and voila! All is well with the world. 

Hope this helps. 

Randy

---

### Post by nightwatchman on 2008-09-04
Thanks for the useful tips.
But even after doing all above wasnt able to make nvidia work.

I tried 5200 on motherboard with intel/nvidia chip-set, there it simply worked. I was amazed. Then I checked the system on which I was originally trying to install the nvidia and found its a VIA chipset. may be some chipset of VIA and nvidia are not that compatible. I didnt investigated further so cannt comment with all assurance about VIA and NVIDIA compatibilty.

Anyway, all the help is great.Thanks again.

---

### Post by ebola15 on 2008-09-11
Hi I have a nvidia 9300 M G. I have tryed almost everything but i hav got no luck. In particular whenever i try to install the nvidia driver i get an message saying that nvidia.ko is missing.
Any help?
kris99466 u installed a 9100 M G can u tell me exactly what did u do? (step by step pleeeeeeeease)

THanks a lot

---

### Post by nightwatchman on 2008-09-11
When I tried installing nvidia driver for 5200 through package manager then the driver it brought from repository was legacy driver "nv.ko".
So, if you need nvidia.ko, go to nvidia site download appropriate driver tar as per your 32/64 bit configuration.Then make it. It will install nvidia.ko.

Cheers!!!

---

### Post by nbayiha on 2008-09-12
@ebola15
did you read this ? cause this is the driver
Those are the one he used.
Try to install using them.
And here you can read a little bit about your motherboard.
[http://www.nvidia.com/object/geforce_9100m_g_mgpu.html](http://www.nvidia.com/object/geforce_9100m_g_mgpu.html)
> **nbayiha said:**
> You can Use this driver Here. 

[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

And if you want to read a little about which driver support those card

[http://packages.ubuntu.com/intrepid/nvidia-glx-173](http://packages.ubuntu.com/intrepid/nvidia-glx-173)

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/173.14.09-0ubuntu4](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/173.14.09-0ubuntu4)

hope that will help you. Don't forget to use the tricky way .

---

### Post by JosephT on 2008-09-13
Ever since I have compiled my new kernel, I lost my NVidia driver.
I've tried all kinds of ways including the graphical EnvyNG all to no avail.
I Opened up a terminal window, followed your instructions, rebooted and whoila!
Thank you !!!

---

### Post by ebola15 on 2008-09-14
I tryed all the possible ways using a new fresh install every time. the ubuntu suggested drivers do not work. Envy do not recognize my video card. And the tricky way get stopped when the installer says that "nvidia.ko" cannot be found.
How can i generate it?Any suggestion???

I am really stuck... 

I also tryed to download the deb packages from [http://packages.ubuntu.com/intrepid/nvidia-glx-173](http://packages.ubuntu.com/intrepid/nvidia-glx-173)

and to install them but of course when i reboot X crash and i go back to my 800x600 (yes after instllation I am at 800x600).
Somebody suggested to download and make the tar from the nvidia website. I ca find only the .run package where can i get a tar???

Thanks a lot

---

### Post by nbayiha on 2008-09-14
> **ebola15 said:**
> I tryed all the possible ways using a new fresh install every time. the ubuntu suggested drivers do not work. Envy do not recognize my video card. And the tricky way get stopped when the installer says that "nvidia.ko" cannot be found.
How can i generate it?Any suggestion???

I am really stuck... 

I also tryed to download the deb packages from [http://packages.ubuntu.com/intrepid/nvidia-glx-173](http://packages.ubuntu.com/intrepid/nvidia-glx-173)

and to install them but of course when i reboot X crash and i go back to my 800x600 (yes after installation I am at 800x600).
Somebody suggested to download and make the tar from the nvidia website. I ca find only the .run package where can i get a tar???

Thanks a lot

Are you using 64bit system or a 32bit one ?  And the problem is because you are not using the right driver for the installation.
So first check which can or processor you have and which version of Ubuntu you installed (32 or 64 bit),and then download the right version of the driver in nvidia web page.

---

### Post by ebola15 on 2008-09-14
I did it already. I have a core 2 duo t9500 (64 bit) ubuntu 64 and i have downloaded the 64 bit driver......

---

### Post by nbayiha on 2008-09-14
@ebola15
Nvidia doesn't support driver for your graphic card , in linux. So the think is you can write a mail , and show them how pissed you are because of that :lolflag: (i did it two year ago , and i didn't work :guitar: but i was relaxed :p ).
Or you  can try this experimental way (above), using > nouveau nvidia, if google it you will find what is it.
But to  make it short, it's an experimental way to make your driver work in Ubuntu, but you won't get the 3D acceleration stuff :D (you can ask that much too)
There is the way to install them 

[http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)
[https://launchpad.net/~raof/+archive](https://launchpad.net/~raof/+archive) (to add them in the repository )

I don't recommended you that method , by the way :lolflag: .
So you are the only responsible , if something goes wrong .

As for me the best thing will be to write a mail to nvidia staff and show them how piss you are. 

Good Day .

---

### Post by ebola15 on 2008-09-14
Here is the installation log file:
> 
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Sep 14 17:12:07 2008
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
-> License accepted.
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-19-generic/build'
-> Kernel output path: '/lib/modules/2.6.24-19-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-19-gener
   ic/build SYSOUT=/lib/modules/2.6.24-19-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-19-generic/build SUBDIRS
   =/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.tmp_
   versions ; rm -f /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/
   nv/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.1
   4.12-pkg2/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.
   nv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include -D__K
   ERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -O2  -mtune=generic -m64 -mno-red-zone -mcmodel=kernel
   -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-time -mn
   o-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args   -fstack-pro
   tector -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-sta
   tement -Wno-pointer-sign   -I/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-p
   kg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subsc
   ripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=kernel -
   mno-red-zone -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG -U_DEBUG -DNDEBUG  -D
   MODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MO
   DNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.1
   2-pkg2/usr/src/nv/.tmp_nv.o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pk
   g2/usr/src/nv/nv.c
   In file included from include/asm/dma-mapping_64.h:9,
                    from include/asm/dma-mapping.h:4,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv.c:14:
   include/linux/scatterlist.h: In function â&#8364;&#732;sg_virtâ&#8364;&#8482;:
   include/linux/scatterlist.h:293: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used 
   in arithmetic
   In file included from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv.c:14:
   include/asm-generic/pci-dma-compat.h: In function â&#8364;&#732;pci_map_pageâ&#8364;&#8482;:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type â&#8364;&#732;void *â
   &#8364;&#8482; used in arithmetic
   In file included from include/linux/compat.h:14,
                    from include/asm/mtrr.h:131,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:121,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv.c:14:
   include/asm/compat.h: In function â&#8364;&#732;compat_alloc_user_spaceâ&#8364;&#8482;:
   include/asm/compat.h:210: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.
   nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include -D
   __KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstr
   ict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impli
   cit-function-declaration -O2  -mtune=generic -m64 -mno-red-zone -mcmodel=ker
   nel -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-time
   -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args   -fstack-
   protector
    -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement
   -Wno-pointer-sign   -I/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -
   Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=kernel -mno-red
   -zone -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -
   DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE 
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAM
   E=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pk
   g2/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg
   2/usr/src/nv/nv-vm.c
   In file included from include/asm/dma-mapping_64.h:9,
                    from include/asm/dma-mapping.h:4,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function â&#8364;&#732;sg_virtâ&#8364;&#8482;:
   include/linux/scatterlist.h:293: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used 
   in arithmetic
   In file included from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/asm-generic/pci-dma-compat.h: In function â&#8364;&#732;pci_map_pageâ&#8364;&#8482;:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type â&#8364;&#732;void *â
   &#8364;&#8482; used in arithmetic
   In file included from include/linux/compat.h:14,
                    from include/asm/mtrr.h:131,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:121,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/asm/compat.h: In function â&#8364;&#732;compat_alloc_user_spaceâ&#8364;&#8482;:
   include/asm/compat.h:210: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.
   os-agp.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include -
   D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impl
   icit-function-declaration -O2  -mtune=generic -m64 -mno-red-zone -mcmodel=ke
   rnel -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-tim
   e -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args   -fstac
   k-protector -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-afte
   r-statement -Wno-pointer-sign   -I/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14
   .12-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-
   subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Wer
   ror -mcmodel=kernel -mno-red-zone -MD   -Wsign-compare -Wno-cast-qual -Wno-e
   rror -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG 
   -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_S
   TR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9131/NVI
   DIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.tmp_os-agp.o /tmp/selfgz9131/NVI
   DIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/os-agp.c
   In file included from include/asm/dma-mapping_64.h:9,
                    from include/asm/dma-mapping.h:4,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function â&#8364;&#732;sg_virtâ&#8364;&#8482;:
   include/linux/scatterlist.h:293: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used 
   in arithmetic
   In file included from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/os-agp.c:24:
   include/asm-generic/pci-dma-compat.h: In function â&#8364;&#732;pci_map_pageâ&#8364;&#8482;:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type â&#8364;&#732;void *â
   &#8364;&#8482; used in arithmetic
   In file included from include/linux/compat.h:14,
                    from include/asm/mtrr.h:131,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:121,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/os-agp.c:24:
   include/asm/compat.h: In function â&#8364;&#732;compat_alloc_user_spaceâ&#8364;&#8482;:
   include/asm/compat.h:210: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.
   os-interface.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/inc
   lude -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wunde
   f -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werro
   r-implicit-function-declaration -O2  -mtune=generic -m64 -mno-red-zone -mcmo
   del=kernel -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at
   -a-time -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args   
   -fstack-protector -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaratio
   n-after-statement -Wno-pointer-sign   -I/tmp/selfgz9131/NVIDIA-Linux-x86_64-
   173.14.12-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -
   Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmod
   el=kernel -mno-red-zone -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__K
   ERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG -U_DEBUG -
   DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_inte
   rface)"  -D"KBUILD_MODNAME=
   KBUILD_STR(nvidia)" -c -o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2
   /usr/src/nv/.tmp_os-interface.o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.1
   2-pkg2/usr/src/nv/os-interface.c
   In file included from include/asm/dma-mapping_64.h:9,
                    from include/asm/dma-mapping.h:4,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function â&#8364;&#732;sg_virtâ&#8364;&#8482;:
   include/linux/scatterlist.h:293: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used 
   in arithmetic
   In file included from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/os-interface.c:26:
   include/asm-generic/pci-dma-compat.h: In function â&#8364;&#732;pci_map_pageâ&#8364;&#8482;:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type â&#8364;&#732;void *â
   &#8364;&#8482; used in arithmetic
   In file included from include/linux/compat.h:14,
                    from include/asm/mtrr.h:131,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:121,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/os-interface.c:26:
   include/asm/compat.h: In function â&#8364;&#732;compat_alloc_user_spaceâ&#8364;&#8482;:
   include/asm/compat.h:210: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.
   os-registry.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/incl
   ude -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef
   -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common
    -Werror-implicit-function-declaration -O2  -mtune=generic -m64 -mno-red-zon
   e -mcmodel=kernel -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -f
   unit-at-a-time -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-
   args   -fstack-protector -fomit-frame-pointer -g  -fno-stack-protector -Wdec
   laration-after-statement -Wno-pointer-sign   -I/tmp/selfgz9131/NVIDIA-Linux-
   x86_64-173.14.12-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wf
   ormat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror
   -mcmodel=kernel -mno-red-zone -MD   -Wsign-compare -Wno-cast-qual -Wno-error
   -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG -U_DE
   BUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os
   _registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9131/NVI
   DIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.tmp_os-registry.o /tmp/selfgz913
   1/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/os-registry.c
   In file included from include/asm/dma-mapping_64.h:9,
                    from include/asm/dma-mapping.h:4,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function â&#8364;&#732;sg_virtâ&#8364;&#8482;:
   include/linux/scatterlist.h:293: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used 
   in arithmetic
   In file included from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/os-registry.c:15:
   include/asm-generic/pci-dma-compat.h: In function â&#8364;&#732;pci_map_pageâ&#8364;&#8482;:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type â&#8364;&#732;void *â
   &#8364;&#8482; used in arithmetic
   In file included from include/linux/compat.h:14,
                    from include/asm/mtrr.h:131,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:121,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/os-registry.c:15:
   include/asm/compat.h: In function â&#8364;&#732;compat_alloc_user_spaceâ&#8364;&#8482;:
   include/asm/compat.h:210: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.
   nv-i2c.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include -
   D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impl
   icit-function-declaration -O2  -mtune=generic -m64 -mno-red-zone -mcmodel=ke
   rnel -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-tim
   e -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args   -fstac
   k-protector -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-afte
   r-statement -Wno-pointer-sign   -I/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14
   .12-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-
   subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=ker
   nel -mno-red-zone -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL_
   _ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG -U_DEBUG -DNDEBU
   G  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"
   KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9131/NVIDIA-Linux-x86_64
   -173.14.12-pkg2/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz9131/NVIDIA-Linux-x86_64
   -173.14.12-pkg2/usr/src/nv/nv-i2c.c
   In file included from include/asm/dma-mapping_64.h:9,
                    from include/asm/dma-mapping.h:4,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function â&#8364;&#732;sg_virtâ&#8364;&#8482;:
   include/linux/scatterlist.h:293: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used 
   in arithmetic
   In file included from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-i2c.c:8:
   include/asm-generic/pci-dma-compat.h: In function â&#8364;&#732;pci_map_pageâ&#8364;&#8482;:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type â&#8364;&#732;void *â
   &#8364;&#8482; used in arithmetic
   In file included from include/linux/compat.h:14,
                    from include/asm/mtrr.h:131,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:121,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-i2c.c:8:
   include/asm/compat.h: In function â&#8364;&#732;compat_alloc_user_spaceâ&#8364;&#8482;:
   include/asm/compat.h:210: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.
   nvacpi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include -
   D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impl
   icit-function-declaration -O2  -mtune=generic -m64 -mno-red-zone -mcmodel=ke
   rnel -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-tim
   e -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args   -fstac
   k-protector -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-afte
   r-statement -Wno-pointer-sign   -I/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14
   .12-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-
   subscripts -Wparentheses -Wpointer-arith -Wno-
   multichar -Werror -mcmodel=kernel -mno-red-zone -MD   -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14
   .12\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BAS
   ENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/
   selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.tmp_nvacpi.o /tmp/
   selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/nvacpi.c
   In file included from include/asm/dma-mapping_64.h:9,
                    from include/asm/dma-mapping.h:4,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function â&#8364;&#732;sg_virtâ&#8364;&#8482;:
   include/linux/scatterlist.h:293: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used 
   in arithmetic
   In file included from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nvacpi.c:15:
   include/asm-generic/pci-dma-compat.h: In function â&#8364;&#732;pci_map_pageâ&#8364;&#8482;:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type â&#8364;&#732;void *â
   &#8364;&#8482; used in arithmetic
   In file included from include/linux/compat.h:14,
                    from include/asm/mtrr.h:131,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-linux.h:121,
                    from /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nvacpi.c:15:
   include/asm/compat.h: In function â&#8364;&#732;compat_alloc_user_spaceâ&#8364;&#8482;:
   include/asm/compat.h:210: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in arit
   hmetic
     ld -m elf_x86_64   -r -o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg
   2/usr/src/nv/nvidia.o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr
   /src/nv/nv-kernel.o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/s
   rc/nv/nv.o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/nv-
   vm.o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/os-agp.o 
   /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/os-interface.o
   /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/os-registry.o 
   /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/nv-i2c.o /tmp/
   selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/nvacpi.o
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.24-19-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.24-19-generic/Modu
   le.symvers -I /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/
   Module.symvers -o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src
   /nv/Module.symvers -w -s
   WARNING: could not find /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/u
   sr/src/nv/.nv-kernel.o.cmd for /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12
   -pkg2/usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/.
   nvidia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/inclu
   de -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef 
   -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-
   implicit-function-declaration -O2  -mtune=generic -m64 -mno-red-zone -mcmode
   l=kernel -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a
   -time -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args   -f
   stack-protector -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-
   after-statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME
   =KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -DMODULE -c 
   -o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/usr/src/nv/nvidia.mod.
   o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pkg2/
   usr/src/nv/nvidia.mod.c
     ld -r -m elf_x86_64  --build-id -o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173
   .14.12-pkg2/usr/src/nv/nvidia.ko /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.
   12-pkg2/usr/src/nv/nvidia.o /tmp/selfgz9131/NVIDIA-Linux-x86_64-173.14.12-pk
   g2/usr/src/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   55.576365] wlan0: authenticate with AP 00:18:4d:61:ad:c2
   [   55.579054] wlan0: Initial auth_alg=0
   [   55.579064] wlan0: authenticate with AP 00:18:4d:61:ad:c2
   [   55.579112] wlan0: RX authentication from 00:18:4d:61:ad:c2 (alg=0
   transaction=2 status=0)
   [   55.579117] wlan0: authenticated
   [   55.579122] wlan0: associate with AP 00:18:4d:61:ad:c2
   [   55.579139] wlan0: authentication frame received from 00:18:4d:61:ad:c2,
   but not in authenticate state - ignored
   [   55.581365] wlan0: authentication frame received from 00:18:4d:61:ad:c2,
   but not in authenticate state - ignored
   [   55.581955] wlan0: RX AssocResp from 00:18:4d:61:ad:c2 (capab=0x461
   status=0 aid=3)
   [   55.581962] wlan0: associated
   [   55.593521] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
   [   58.134333] wlan0: no IPv6 routers present
   [  202.087308] warning: process `nvidia-installe' used the deprecated sysctl
   system call with 1.23.
   [  202.087315] warning: process `nvidia-installe' used the deprecated sysctl
   system call with 1.23.
   [  202.225103] nvidia: module license 'NVIDIA' taints kernel.
   [  202.482521] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) ->
   IRQ 16
   [  202.482526] NVRM: This PCI I/O region assigned to your NVIDIA device is
   invalid:
   [  202.482527] NVRM: BAR1 is 256M @ 0x00000000 (PCI:0001:00.0)
   [  202.482529] NVRM: This is a 64-bit BAR mapped above 4GB by the system
   BIOS or
   [  202.482530] NVRM: Linux kernel. The NVIDIA Linux graphics driver and
   other
   [  202.482531] NVRM: system software do not currently support this
   configuration
   [  202.482532] NVRM: reliably.
   [  202.483047] nvidia: probe of 0000:01:00.0 failed with error -1
   [  202.483134] NVRM: The NVIDIA probe routine failed for 1 device(s).
   [  202.483136] NVRM: None of the NVIDIA graphics adapters were initialized!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).



At the end it seems to me that it is complaining about the PCI I/O address of the card. This laptop (asus w7sg) comes with vista pre installed. I put xp and i found a similar issue. In fact to install the video card driver under XP one has to disble an Express route ports ([http://forum.notebookreview.com/showthread.php?t=260996](http://forum.notebookreview.com/showthread.php?t=260996))
> 
On the W7Sg with 3GB or RAM, XP exhibits a bug whereby the GPU isn't detected due to a conflict with one of the Express Root ports otherwise the video crad is not recognized at all. In my particular case, this root port was:

Intel(R) ICH8 Family PCI Express Root Port 2 - 2841

This is how the device would be identified if you didn't install the chipset drivers:
PCI bus 0, device 28, function 1

Can it be a similar probelm in ubuntu too? 

Thanks

---

### Post by ebola15 on 2008-09-14
> 
@ebola15
Nvidia doesn't support driver for your graphic card


Thanks but

here 

([http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/README/appendix-a.html))

it clearly says that my video card is supported... GeForce 9300M G....I am losing hope...

---

### Post by nbayiha on 2008-09-14
did you tried one of the driver listed in the link you send me ?

[http://www.nvidia.com/object/linux_amd64_display_archive.html](http://www.nvidia.com/object/linux_amd64_display_archive.html) 

If you know tried to remove everything with nvidia , even the hidden nvidia fille in restricted modules (if you dont know what i mean i explain how to remove those hidden nvidia file in the thread,) , and then try the tricky way with the latest driver in the page i gave u up.

---

### Post by Whisper45 on 2008-09-19
it doesnt work. It has an error, for some reason. I do everything in the Tricky way after clean installation.

---

### Post by nbayiha on 2008-09-19
Which error he has ?

---

### Post by jacksnbox on 2008-09-19
I have installed the drivers for a 8400 GS about 10 times. I have installed the default driver, ones through Envy and ones direct from Nvidia. Each time, when I reboot, I get a black screen and the monitor says no signal. I have to restore the x server to get a screen back.
xorg config:
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Jul 17 18:39:00 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by ebola15 on 2008-09-28
> 
Or you can try this experimental way (above), using
Quote:
nouveau nvidia
, if google it you will find what is it.
But to make it short, it's an experimental way to make your driver work in Ubuntu, but you won't get the 3D acceleration stuff (you can ask that much too)
There is the way to install them

[http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)
[https://launchpad.net/~raof/+archive](https://launchpad.net/~raof/+archive) (to add them in the repository )

I don't recommended you that method , by the way .
So you are the only responsible , if something goes wrong .



what do you mean with "goes wrong"? If the danger is to mess up the ubuntu installation I have no prob while if the problem might be frying the video card I will not do that.....

---

### Post by timosa on 2008-10-02
> **keelon72 said:**
> Asked around and a friend said that when he installed this card (9600 GT) in Windows the Nvidia driver warned that there wasn't enough power to the card.

I had similar problem with GeForce 9600 GT + Hardy Heron. When the "extra" power connector wasn't attached the computer booted successfully and lspci showed correct information but X wasn't able to find driver even if I installed the latest nvidia drivers. After connecting the power connector the card was detected successfully and worked like a dream.

---

### Post by TeXtonyx on 2008-10-02
Hi I tried the tricky way and it worked. There was a problem with
sudo /etc/init.d/gdm stop ,  I never got to a text login screen. Because I
dual boot? So I tried sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/D30gdm which
makes Ubuntu boot to a black-screened command line. Then everything worked,
and I renamed D30gdm back to S30gdm before starting gdm again. I didn't use
the option to write to xorg.conf during the build of the 173.14.12 driver, 
but after booting up used Applications->System Tools->Nvidia X server settings. 
And then wrote to xorg.conf from that utility after manually backing up.
So building the driver worked out quite well, thanks. Also I followed the advice about cutting and pasting the xorg.conf that is shown in "preview"; otherwise saving/merging the new configuration to xorg.conf doesn't seem to work.

---

### Post by carra on 2008-10-02
Hi there,
I run a fresh Ubuntu 8.04 on HP Pavilion Tx 1250el and I installed the nvidia drivers through the easy way.
I cannot go to console mode through the usual short cut Ctrl-Alt-F*: only Ctrl-Alt-F7 works, enabling the graphic screen. 
Moreover, every time the screen shuts down, either by power management or closing the laptop, I'm unable to access the graphic session and the screen is blank. 
At this point I must remove the AC adapter to shut down the laptop, the brutal way!
At the moment, I modified xorg.conf changing "nvidia" with "nv", as I read elsewhere in this forum, and everything works in old-fashioned 2D mode, but I would like to make use of the wonderful Compiz Fusion...
Anyone succeded with "nVidia Corporation C51 [Geforce 6150 Go] (rev a2)"?
Thanks to anyone helping...

---

### Post by Zaff on 2008-10-02
> I cannot go to console mode through the usual short cut Ctrl-Alt-F*: only Ctrl-Alt-F7 works, enabling the graphic screen. 
Does your laptop have some Fn key ? Some laptop require the Fn key to be pressed for the F1 key to be activated so try doing Ctrl+Alt+Fn+F1 and see if that'll take you to an other console, then try to install the driver from there as explained.

---

### Post by carra on 2008-10-02
The Fn key is not my problem: I can access the console with binding Ctrl-Alt-F* when I don't run the nvidia driver.
So should I uninstall the nvidia driver and reinstall it from console?
Before doing this, I would like to know if there is a way to tweak xorg.conf and solve my problem, i.e. blank screen after screen shut down....

---

### Post by JoyousDeath on 2008-10-25
Thank you for this post. It helped very much! :)

---

### Post by AeroTITAN on 2008-12-30
If anybody follows this post anymore I'm having a problem with an 8400 gs.

I had 7.10, but I upgraded to 8.04 to get the card to work - which it did and I did not keep a record of the procedure I used to do that.  It also works in Windows XP SP3 which is blazing fast right now.

My problem is I installed 2x1GB memory sticks and fresh installed 8.10.  Now, Ubuntu will not boot with the 8400 gs card.  The memory shows up with "$ free" and I can boot with the memory and the old graphics card.  It just seems there is a problem with the graphics card and the mem sticks sharing the memory... it always crashes with a SEG Fault.

I have downloaded the drivers, but as I cannot boot up with the new card, the drivers will not detect a nvidia driver and therefore not install it.  I have tried many, many, MANY posts here and I no matter what the instructions, somewhere down the line I can't complete them because eventually it comes down to booting with the 8400 card in order for the OS to recognize my card.

I've done the envy path, xconf configuration, etc and no joy.  I have also tried to boot from the liveCD and it hangs at the same spot as the regular boot.  I also can't use the LiveCD to do a fresh install with the 8400 physically installed.

This is the first time my Windows has beaten Ubuntu which is ironic.  I'm pulling out what little hair I have left, so ANY advice would be great.

Currently:
8.10
32-bit
HP Pavilion a749c
2.5GB SDRAM
XP SP3 dual boot

---

### Post by rcshah on 2009-02-03
Thanks!  This worked for me using a Toshiba Satellite with
GeForce4 420 Go video card (after modifying the conf file as detailed in the first post).

---

### Post by tachibana on 2009-02-08
Hi,
I installed the driver told as first post. I have hp pavilion 5198 with GeForce Go 7400. After installed compiz is enabled but images and color passings looks as how drivers are not installed. In conf file color depth is 24(16.7 million color)bits. Here is a photo i take it with webcam.

[[IMG]http://img502.imageshack.us/img502/2133/sdsdbx5.th.png[/IMG]](http://img502.imageshack.us/my.php?image=sdsdbx5.png)

---

### Post by Dieseler on 2009-02-16
The tricky way worked for me on emachine T3025 with Nvidia mx on board video. The Gnome desktop looks great on this machine now.
Thanks for the how to.
This was a horrible experience until I found it.
I'm using 8.04 Hardy on this machine by the way. I was unable to find joy with Nvidia using Intrepid 8.10.

---

### Post by deceaseddolphin on 2009-07-13
> **nbayiha said:**
> [SIZE=2]**After realizing that a lot of person had problem installing NVIDIA Driver series 8 and 9 on Hardy . I decide to open this Thread. Even if you don't find it useful , at least i hope it will be the only place where you will post the problem you encounter during the installation , so i(we) will try to resolve it , instead of having a thousand of thread around .**[/SIZE]

**I.** [SIZE=2]**_Prerequisites_**[/SIZE]
[LIST]
[*]NVIDIA Graphic Card
[*]Hardy Heron installed 8.04
[*]Internet Connection
[/LIST]
**How to know if you have a NVIDIA graphic card . Paste the command under in the terminal** ```
lspci | grep -i nvidia 
```**It should printed out a line of text with the name of your card.**

**II.** [SIZE=2]**_Driver Version_**[/SIZE]
There are three version of the restricted driver in the repositories
[LIST]
[*]Nvidia-glx-legacy
[*]Nvidia-glx
[*]Nvidia-glx-new
[/LIST]

**III.** [SIZE=2]**_Faster/Easier Way to Install_**[/SIZE]

[LIST=1]
[*]Go to **[SIZE=2]System[/SIZE]->[SIZE=2]Administration[/SIZE]->[SIZE=2]Hardware Driver[/SIZE]** and check the box to enable the driver **_*if it's provided*_** .
You can check Here Visually how to do it .
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
[*]If the driver are not provided , then **_try to install them throw Envy_**.
```
sudo apt-get install envyng-gtk
envyng-t
```then press 1, install and reboot .
And You are good to go :)
[/LIST]

**IV.** [SIZE=2]**_ Tricky Way After Clean Installation_**[/SIZE]

**_ PS _: *If the first and the second method didn't work then you can use this one. Otherwise i recommend you to try them first. Cause they are easier and you don't need to do some manual change*.**

So we understand that the method above didn't work, so You should start by..

[LIST=1]
[*]First uninstall the envy package if you installed them, otherwise just skip this step . ```
 sudo apt-get remove envyng-gtk 
```
[*]Make sure you have the build-essential installed ```
sudo apt-get install build-essential 
```
[*]Download from NVIDIA the latest driver of you card.

_**For the 8 series(8xxx) is this one :**_  [SIZE=2] _[http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)_ or this one _[http://www.nvidia.com/object](http://www.nvidia.com/object)_[/SIZE][/linux_display_ia32_173.14.12.html]("http:///linux_display_ia32_173.14.12.html")

_**For the other series(9xxx,7xxxx) : ** _Just go to this web page and download the one for you [SIZE=2]_[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)_[/SIZE].
[*] We are going to kill the gdm (gnome), so i will advice you to write down a paper the following command. 
```
sudo /etc/init.d/gdm stop
``` that will kill gnome or ctrl+alt+F1.
You should now log in + password.
[*] Go where you downloaded the NVIDIA driver. Mine was in the desktop so i had to do this 
```
 cd /home/nbayiha/Desktop 
``` But yours can be in your home directory . Just use the command ```
ls
``` to be sure that the driver are in the right directory.
[*] Then ```
sudo sh NVIDIA*
```Accept the configuration and the backing up of the xorg files.

*[SIZE=1]_PS:_ If you had in this step some problem with telinit just do ```
sudo telinit 3 
```[/SIZE]*
[*] After the installation is complete just restart gdm 
```
 sudo /etc/init.d/gdm start 
```
[*] Now we will edit your xorg.conf go to .
[SIZE=2][B]Application->System Tool->NVIDIA X Server Settings->X server Display configuration-> Save to X Configuration File(click on it,down on you right)->show preview (copy all the text inside preview).
[/B][/SIZE]
[*]Now backup your xorg.conf 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backUp 
```
[*]```
gksudo gedit /etc/X11/xorg.conf
```And delete all the file and paste what you copy in step 8 . 

Save and You are Good to go .
[/LIST]

**V.** [SIZE=2]**_ Tricky Tricky Way After Mainly attempt :KS _**[/SIZE]

[LIST=1]
[*]
First make sure everything **_comporting NVIDIA is uninstall_**, if so uninstall them from the repository(nvidia-setting nvidia-glx nvidia-glx-new....) , just remove all of them.
now follow those command step by step , better if u write it down cause we are going to kill the server.
[*]Download the NVIDIA driver from the web page [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and save them in your home directory.
[*]We are going to  disable the NVIDIA driver in the repository ,so they won't have conflicted problem with the one we download.
```
gksudo gedit /etc/default/linux-restricted-modules-common 
``` edit the DISABLED_MODULES line so it will look like this
[*]Note in a Paper the following command cause we are killing gdm .
```
sudo /etc/init.d/gdm stop 
``` or ctrl+alt+f1 Log+passwd
[*]```
sudo telinit 3 
```go to the folder where you downloaded the NVIDIA driver.
[*]```
sudo sh NVIDIA* 
```accept everything.
[*] Reboot and you are good to go .
[/LIST]

 [SIZE=2]**_ Problems_**[/SIZE]

1- For those who lost their old xorg.conf just do it to get it back 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```2- For those using Laptop(Notebook) with a Geforce Go card , if you hear the startup sound without nothing appearing on the screen , then you should check your xorg.conf and edit it that way *_(just do it after trying the three way provide above )_* 

     *Reboot and use recovery mode , log in +passwd 

     *```
sudo nano /etc/X11/xorg.cong
``` Find the line with Section "Screen"  insert a new line that say 
Option "UseDisplayDevice""DFP" 
Save the file and reboot .


[SIZE=2]If one of the method work partially or didn't work at all , report in which level you encounter the problem and we will figure out what to do :lolflag: . [/SIZE] 

Have A good Day :guitar:



Thank you so much for the detailed process. 
***Tricky way after Mainly attempt*** worked for me :D.
I was struck with low graphics for over 30 hours and been googling since then until your tutorial. 
I hope to have no further problems.

Thanks again for the tutorials!

---

