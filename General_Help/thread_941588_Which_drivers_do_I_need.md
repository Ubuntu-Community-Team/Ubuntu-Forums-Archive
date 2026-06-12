---
title: "Which drivers do I need?"
date: 2008-10-08
forum: General Help
---

### Post by AilesGrises on 2008-10-08
How do I find out which drivers I need, and when I figure that out, where can I get them?

I'm running Ubuntu on a Dell Inspiron E1405 laptop.

(Sorry if this isn't where the question belongs, I didn't know where to put it)

---

### Post by tuxxy on 2008-10-08
What drivers are you reffering to? video drivers should be enabled at system > admin > hardware drivers

If nothing is listed, download envy and use this application to isntall your video driver

```
sudo apt-get install envyng-gtk
```

---

### Post by Ms_Angel_D on 2008-10-08
You should be a bit more specific, Drivers for what?

---

### Post by caleb12 on 2008-10-08
I think I'm understanding what you're asking... First off, drivers in Linux are synonymous with modules. Modules are compiled or loaded by the kernel. Sometimes you may need a specific module or driver that is not in your current kernel, such as a video driver - especially an ATI or Nvidia. In this case, you would install the source for such a driver and compile it. Ubuntu has great tools for working with these things, so it all sounds alot more complicated that it is. In my experience installing an ATI driver was as easy as opening Synaptic and selecting the module... 

To figure out what modules are loaded, type (in a terminal):

sudo lsmod 

this will spit out all loaded modules, not always that helpful but combined with:

sudo lspci -v 

which will spit out the specific devices on your system along with the modules that they loaded. This is useful when you are troubleshooting hardware issue.

But, MetalHellsAngel is right... what drivers are you looking for?

---

### Post by AilesGrises on 2008-10-09
Umm, drivers for stuff >.>

I remember on Windows you had sound drivers and video drivers and wireless drivers and everything had a driver... I don't know how these things work, and I assume that Ubuntu doesn't come pre-installed with these, and that I would have to find some elsewhere.

So I guess Sound, Wireless, and Video, since those are the ones I know about.
How do I even find out which ones I need?
And I don't have System > Admin > Hardware Drivers. And what is Envy?
I'm running 7.1 Gutsy.

---

### Post by caleb12 on 2008-10-09
Hit alt+F2 and type in gnome-terminal, or if you are on KDE type: konsole 

Welcome to the command line... type sudo lspci -v > ~/Desktop/device.txt 

Post that file here... 

Most drivers are modules, most of these modules you probably already have. There are really only a few proprietary type modules that you may need; such as ATI or NVidia - in which case you would use Envy it makes installing 3rd party modules very easy. Chances are you have everything you need already... Linux drivers (modules) are not the same as drivers in Windoze - you don't have to go to six different vendor sites to find obscure drivers... it's all contained in the kernel. Ubuntu is also very good about building restricted modules, restricted in the sense that they are not covered by the GPL. 

What is the reason you are asking for drivers anyways? I mean, is something not working right? are you having problems with hardware? or just planning on installing ubuntu?

---

### Post by Yellow Pasque on 2008-10-09
> What is the reason you are asking for drivers anyways? I mean, is something not working right? are you having problems with hardware? or just planning on installing ubuntu?

I believe it's just another Microsoft user about to break off his/her shackles and wanting to make sure he's not leaving slavery for the poorhouse :P

---

### Post by doas777 on 2008-10-09
> **AilesGrises said:**
> Umm, drivers for stuff >.>

I remember on Windows you had sound drivers and video drivers and wireless drivers and everything had a driver... I don't know how these things work, and I assume that Ubuntu doesn't come pre-installed with these, and that I would have to find some elsewhere.

So I guess Sound, Wireless, and Video, since those are the ones I know about.
How do I even find out which ones I need?
And I don't have System > Admin > Hardware Drivers. And what is Envy?
I'm running 7.1 Gutsy.

yeah I had to deal with that paradigm shift myself. Linux does not really need drivers for your stuff. most of they are already built in. there are a few notable exceptions to this rule, but the only things i;ve had to install drivers for at my video cards and wireless network cards. everything else is already in there.

if you do need extra drivers, you can download source and compile it (not nearly so hard as it sounds) and install the modules.

if you have questions about a specific device, first google, and if nothing comes up after adjusting your query a few times, post back here.
be specific about the device you wish to install

Envy is an application to help you download and install the proprietary Nvidia and ATI devices. it used to be just nvidia (envy => nv => nvidia). 

sound should not be an issue (I've never seen a sound card that didn't work out of box), but video and wireless can be a pain. a lot of the time they install easily, but if you do have a problem it can be a big endeavour to get working right. feast or famine....

try to use the restricted drivers in system -> admin -> hardware drivers  (check the box to enable and reboot). if that doesn't work out, you may have to fall back to envy or ndiswrapper. the are literally hundreds of tutorials and discussions about those.

you can get information about your specific devices with the lshw command (list hardware), by running:
```

sudo lshw

``` 


have fun and good luck,
Franklin

---

### Post by caleb12 on 2008-10-09
> **AilesGrises said:**
> Umm, drivers for stuff >.>

I'd have to agree...

---

### Post by AilesGrises on 2008-10-12
[QUOTE=caleb12;5937737]Hit alt+F2 and type in gnome-terminal, or if you are on KDE type: konsole 

Welcome to the command line... type sudo lspci -v > ~/Desktop/device.txt 

Post that file here... 
/QUOTE]

When I type that in, it gives me instructions on the uses of lspci, and I don't see anything on the list that would give me hardware statistics.

I'm looking for drivers because I want to make sure that I'm up to date on everything. The standard Windows troubleshooting goes something like:
1. Is your computer plugged in?
2. Is your monitor turned on?
3. Are your drivers up to date?

Ubuntu is very confusing, and some things aren't quite working, and I want to make sure I'm completely updated on drivers so that when something isn't working, I know it isn't a driver issue.

I've been running Ubuntu for probably about 4 months.

---

### Post by caleb12 on 2008-10-12
I understand... Ubuntu is really not that confusing, it's just a new way of doing things. I understand the windows perspective and as far as Linux is concerned - ubuntu has done a hell of a job at making that experience user friendly. Bear with it, the reward at the end of the day is worth it. 

lspci is a command line tool to display alot of information regarding hardware. I learned linux at the command line, and it's where I'm most comfortable. I know ubuntu has developed alot of GUIs to display the same information although I am not that familiar with those tools - so if someone else wants to chime in here... that would be great. 

But, all this is secondary - your purpose is to find drivers, right? So, the first thing you need to understand is that all the drivers for linux hardware is contained in the kernel... It's already there, it's built in - you don't have to download anything or install anything. There are only a couple situations, and a couple pieces of hardware that would require special drivers - those are video cards or wireless cards (and only specific varieties). So, let's start there - what kind of video card and wireless (if any) do you have? 

Windows tends to over complicate things... linux is actually very simple and it's strength is in it's simplicity. And Ubuntu has done an amazing job at simplifying even further and making it all much more palatable for people used to other OS's...

---

