---
title: "aspire 4741g, nvidia geforce gt 415M driver issue"
date: 2010-10-11
forum: Hardware
---

### Post by ca1ig0la on 2010-10-11
Hi,
my laptop is a aspire 4741G.
graphic card is nvidia geforce GT 415M
I made an ubuntu 10.10 plain install. I'm running the system in low graphic mode cause I can't figure out how to get it to work.
I tried with "additional drivers" tool, but it doesn't solve any problem: the nvidia-settings opens a window with no options but a list of useless checkboxes like "show "Really Quit" dialog?" or "Enable tooltips"... nothing related to any video setting. 
I tried with the binary driver from the nvidia website. After installing it, when I restart gdm the screen get blank and the system doesn't even play the login sound. The computer gets stuck. 
I've read that before installing nvidia driver you should have default driver working acceptably. I didn't. 
Where do I start from now? I'm kind of stuck here. 

Thank You

---

### Post by ca1ig0la on 2010-10-11
in the nvidia-bug-report.sh log I can find the following error:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

---

### Post by ca1ig0la on 2010-10-12
Waiting for help I'll just keep taking tracks of my progresses ( or regresses ).

I've tried to reinstall the Nvidia driver with the additional driver tool. And again it seems that the problem is the location where the actual module are stored. I can run the system only in failsafe graphic mode.

In the logs there is always the error of some module not found. I tried both with glx and nvidia. 

It seems, tohugh, be working with vesa. but the result is the same as the low grafic mode of the filesafe session.

The questions I am trying to answer are: 
where are the module stored? (in /usr/lib/nvidia ? /usr/lib/nvidia-current? )
Where is it specified to the system where to go look for it? 

I mean, either the modules are placed or the system looks for the modules in the wrong place. 

thanks, I can feel you reading this post, don't be shy: help me! :-)

---

### Post by ca1ig0la on 2010-10-13
Has anybody a nvidia GeForce GT 415M either working or not on ubuntu 10.10?

I'm stuck with a 800x600 screen resolution, please be ubuntu toward me! :-)

---

### Post by sokke90 on 2010-10-13
The same with Geforce 8600M GT.  Log files say that my graphic adapter is not detected or not supported. 
Ubuntu 10.04 workes fine.

---

### Post by otherethe on 2010-10-13
> **ca1ig0la said:**
> Has anybody a nvidia GeForce GT 415M either working or not on ubuntu 10.10?

I'm stuck with a 800x600 screen resolution, please be ubuntu toward me! :-)
Try this right click on these links click save as and save them to your desktop

32bit system: [ftp://download.nvidia.com/XFree86/Linux-x86/260.19.06/NVIDIA-Linux-x86-260.19.06.run](ftp://download.nvidia.com/XFree86/Linux-x86/260.19.06/NVIDIA-Linux-x86-260.19.06.run)
64bit system: [ftp://download.nvidia.com/XFree86/Linux-x86_64/260.19.06/NVIDIA-Linux-x86_64-260.19.06.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/260.19.06/NVIDIA-Linux-x86_64-260.19.06.run)

Once you get it saved to your desktop open a terminal Type this command in
this is step by step:

Frist command will shut down your gui so you may wanna write this down if you cant rem it

sudo stop gdm       (((this kills your gui)))
cd Desktop            ((( are cd /home/your folder name/Desktop
if you dont rember are didnt write it down type in dir so you can view the files on your desktop
sudo sh NVIDIA-Linux-x86_64-260.19.06.run          ((( are NVIDIA-Linux-x86-260.19.06.run Depending on your os type))
go tho the installer it'll ask at the end do you wish for the installer to Config x for you select yes if it does not after install type this in
sudo nvidia-xconfig
Now type in sudo start gdm
plz do Let me know if this has helped you

I know you've said you've install the others befor but im guessing you done it with software center, and are apt-get I 2 had a problem some what like this when i force installed 195 drivers due to the fact the 260 are no were near as good at least not for my self It would just boot up to a shell prompt and are just lock up on the normal loading screen so just like i said give this a try im sure it'll work for you

---

### Post by ca1ig0la on 2010-10-13
Hi,
thanks friend for your help, sadly I've already tried that way. Actually my graphic card driver is the NVIDIA*.256.53. 
I've also tried to balcklist the modules following several and different guides. I am wondering if I am the only one with this graphic card experiencing those issues. 
It would help to know if anybody with my same nvidia got it to work ( also people who couldn't get it to work are welcome to complain altogether :-) and eventually find a solution ).

thanks again.

---

### Post by cascade9 on 2010-10-13
> **ca1ig0la said:**
> Hi,
thanks friend for your help, sadly I've already tried that way. Actually my graphic card driver is the NVIDIA*.256.53. 

I dont think that the 256.xx drivers will work on that card. Doing a search (including 'beta and archived drivers') the only drivers I get for the 415M is the new 260.1912 drivers, which only came out in the last day or so (260.1912- 												October 13, 2010). 

[http://www.nvidia.com/object/linux-display-amd64-260.19.12-driver.html](http://www.nvidia.com/object/linux-display-amd64-260.19.12-driver.html)

---

### Post by ca1ig0la on 2010-10-14
Oh, I am sorry!
I'll try it immediately and'll let you know!

Thanks a lot.

---

### Post by ca1ig0la on 2010-10-14
Ok, 
it didn't work: I guess the problem is not within the driver itself. I think there may be a system wide problem. I'll go for a new plain installation of the system. We'll see! :-)

---

### Post by DRDarkRaven on 2010-10-14
The newest driver doesn't work for my GT 420M graphic card either.

But the vesa driver does,so I don't think this is a system-wide problem, just a driver problem per se.

---

### Post by ca1ig0la on 2010-10-14
What do you mean with "the vesa driver does"?
What resolution are you using? I am running vesa right now and I can't make it go further than 800x600!!! And my screen is a 16:9 :-(
Cold you paste here your xorg.conf pleeze?

thanks

---

### Post by ca1ig0la on 2010-10-15
Guys, let try to answer these question to address the problem:

1) Did you upgrade from 10.04 or plain installed 10.10?
2) Are you having troubles only with the nvidia driver or can't get any driver to work?

Me:

1) I made a plain 10.10 install
2) I can't get any driver to work ( vesa seem to work but only at a resolution of 800x600, that is not acceptable of course )

---

### Post by ca1ig0la on 2010-10-15
As far as I've found out until now, some of the people who have updated the 10.10 from the 10.04 are able to work around this problem (so if you are of this category don't worry too much).
Sadly for me, I haven't heard about anybody who did an Ubuntu 10.10 plain installation and has been able to fix the problem. :'(
The good thing is that now, after working the whole day at 800x600, my mobile phone screen seems awesome!

---

### Post by ca1ig0la on 2010-10-29
nvidia 260.19.12: one more driver that can't fix my problem!

---

### Post by funicorn on 2010-10-29
It's for sure the problem of the video driver, but not merely the NVIDIA thing.

4741G is built on the platform of Inter i3/5+Nvidia Gforce series, which support
Optimus technology. Optimus means you have both intel video card integrated 
inside the Intel cpu and NVIDIA card plugged in PCIE. 

As far as video output is concerned, It works in different ways:

1. Independence output mode, which uses only one card of each time, either Intel or Nvidia.

2. 2D rendering with Intel and 3D acceleration with NVIDIA. 

Unfortunately, 4741G only works in the second mode, which means  both cards are working
whenever video output is needed. In linux system, there is no proper driver for this Optimus 
working mode. The best thing you can do is to try installing NVIDIA driver and prey. 

As far as I know, there are two possible ways to make it work,

1 Install the NVIDIA driver of version 256.44. You have to startx with ABI check off, which 
can be done by inserting Option "IgnoreABI" "true" into the ServerFlags section in xorg.conf, 
or with cmd startx --ignoreabi.

2 Install the newest linux kernel of version 2.6.36-60, and the newest NVIDIA driver of version
260.12, then make certain configuration to /etc/X11/xorg.conf relevant to your screen settings.
And the funny thing is you need do some really dirty tricks to make the cards work, like you have
to install different versions of NVIDIA drivers since they include some files needed.

The first way is much simpler, but I found 256.44 does not work very well on Ubuntu 10.10, which causes high cpu usage by Xorg, and 256.44 has other bugs like the gnome-terminal is slow.

The second way is difficult, and I don't have that energy to make it work. But it's possible 290.12
works better since it's built on newer version of Xserver package.

Similar issues are all over bug ppa website. You can search above info with key words
"ubuntu nvidia driver no screen found ". Good luck.

---

### Post by ca1ig0la on 2010-11-01
thank you Saint Funicorn! I'll try right now.

---

### Post by albert blas on 2011-01-03
Hi, I have a i5 CPU and a GT 415m GPU, and i have the same problem, does anybody can fix the problem, because I need to install the Nvidia drivers to use the Cuda Api.

---

### Post by zaheridor on 2011-04-16
try using virtualgl. have a look at [http://ubuntuforums.org/showpost.php?p=10683406&postcount=10](http://ubuntuforums.org/showpost.php?p=10683406&postcount=10)

---

### Post by kkng on 2011-05-20
I have download the latest driver at nvidia website (nvidia.com)
driver: NVIDIA-Linux-x86-270.41.06.run
Did a sh run.
It hang after reboot.

system Aspire 4741G
Nvidia 415M

---

### Post by kkng on 2011-05-20
> **kkng said:**
> I have download the latest driver at nvidia website (nvidia.com)
driver: NVIDIA-Linux-x86-270.41.06.run
Did a sh run.
It hang after reboot.

system Aspire 4741G
Nvidia 415M
Using Synaptic Package Manager, I select:
nvidia-current: 270.29-Oubuntu1-xup2
Enable it using Hardware Driver.

After reboot, the system hang at the purple startup screen.

---

