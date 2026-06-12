---
title: "An Ubuntu Newbie tells his story"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by Jeffa on 2007-03-21
[SIZE=3]My first Ubuntu System Project[/SIZE]

So I think my tale is a common enough one. I consider myself rather computer literate. I've built my own machines, and customized them extensively. However, like most, I've been raised on Windows. I've become rather frustrate with Windows lately, and was interested in giving Linux a try. So, I installed Ubuntu on an older machine, and I liked what I saw! When the time came to build a new system, I decided to abandon windows all together, and go Ubuntu all the way! 

So, that's my story. The system i wanted to build would serve as a file server and media box. Additionally, I was hoping to keep it pretty efficient, cool and quite. (at least as quite as you can make a RAID array). I knew it would be next to impossible to get the system totally quite, but I did my best to keep the noise down. Lastly, I wanted the system to be expandible. 

Additionally, I decided to phase the project. Phase I would be the basic system. After that was up, running, and stable, I would move on to Phase II, the storage array. 

With that in mind I started my research on components. I've recently purchased and received everything needed to complete phase I of the project. I thought I would use this thread to document my progress so that others may benefit from my experience. So here goes.....


[SIZE=3]First, the specifications for Phase I:[/SIZE]

**Case**
Lian Li PC-210B
A beautiful case, as one would expect from Lian Li. Solidly built, great design, LOTS of room. This case positions the PSU on the bottom and inverts the MOBO, so everything seems a little backwards, but no big deal. So far, I haven't run into any problems with things not fitting. 

Other case examined: Antec P180. For obvious reasons. It's notoriously quite, which i liked. However, I wanted maximum expandability for the storage array, so I went with the 8 port RAID controller, plus boot drives, so I needed more 3.5" bays than the P180 had to offer. 

**MOBO**
Asus P5W DH
A fascinating looking mobo with lots of cool features. I like the passively cooled north and south bridge, the included media remote control, passive mp3 player mode, and it had enough expansion slots for what I wanted to do. 

Potential drawback: 
Although the Instruction Manual states you can use the second PCI-E slot for devices other than Graphics cards, I have read in more than one place that the official Asus position is that their PCI-E slots were design specifically for Graphics Cards, and use of other controllers in the PCI-E slots is not officially supported by Asus. I have a hard time believing a company like Asus would have trouble following the PCI-E standard, and will be very disappointed if i can't use the second PCI-E slot for a RAID controller. only time will tell.....

**Processor**
Intell Core 2 Duo
probably nothing you haven't heard before. I didn't read a single negative thing about this processor in my research. 

**Memory**
2 GB of Kingston HyperX DDR2 800 Dual Channel
Fast, came with heat spreaders, it's Kingston.....

**Power Supply**
Corsair HX620W 
After a good review on [SPCR]("http://www.silentpcreview.com/article692-page1.html"), I was sold. It had what I was looking for. Powerful, quiet, modular. It was a little pricey, but like they say, you get what you pay for. 

**Graphics Card**
Asus EN7600GT Silent
Obviously, I went with Nvidia. The passive cooling system of this card intrigued me. We'll see how it performs....

**Other**
Random stuff. Floppy drive. (I was hoping to go without, and may remove it after everything is set up. We'll see) 

LG optical drive. Dual layer, DVD +/- R, RW; CD +/- R, RW

That just about does it for Phase I. The hardware installed without a hitch. The system powered up flawlessly. Popped the install disc into the optical drive, and I'm currently running the memory test. As soon as that finishes, I'll be installing and configuring. Once that is finished, it's on to Phase II! 

[SIZE=3]The specifications for Phase II:[/SIZE]

I haven't bought these yet. As previously stated, I'm going to get the system up and running before going on to this phase. But I'll list the specs for good measure. 

**RAID Controller**
Areca 1220
True Hardware RAID, supports many different RAID (including RAID 6). This is the 8 port version. Read many good things about the speed, quality, and usability of this card. 

The only potential drawback is its Linux compatibility. I've read some people using it on Linux, and I think I even read the latest drivers are in the latest kernel, but I can't seem to remember where i read that. 

**Drives**
Seagate 500 GB
Maxing out the 8 ports will eventually give me 3.5 TB of storage, and that makes me happy. 

I'll update this thread with my progress. I hope other can benefit from this experience as much as I have. 

Cheers!

[SIZE=5]Update #1[/SIZE]

Finished the install, and as expected it went off without a hitch. Now on to the configuring.....

[SIZE=5]Update #2[/SIZE]

after installation, there were quite a few updates (161!). So, I installed all the updates. 

After updating, I enabled all the repositories, installed flash, easytag, and gstreamer codecs. 

not too excting. I'm just going through and configuring basic things. Should get more interesting when i start building the array!


[SIZE=5]Update #3[/SIZE]

A few minor hardware conflicts arose. First, the power cord on the front chasis fan is too short to reach the fan connector on the motherboard. A minor annoyance. Extention cables run about $2, but c'mon Lian Li, this was an expensive case.

The second minor confilct arose from the side chasis fan and the passively cooled graphics card. The heat pipe on the graphics card sticks out farther then tyiical cards, so I couldn't reinstall the fan bracket assembly as it was originally installed. To fix this, I removed the inner fan guard and outer fan louvre and installed the fan bracket assembly closer to the outside edge of the case. Losing the fan guard probably won't be a major issue, and losing the louvre may impact the effectiveness of the fan a bit, but I doubt it will have a major impact. Besides, installing the fan assembly without the louvre is better than not insalling the fan assembly at all.

[SIZE=5]Update #4[/SIZE]

Installing Nvidia drivers. I decided to go with the [Envy Script]("http://albertomilone.com/nvidia_scripts1.html"), and it went perfectly. The Drivers installed without an incident, and thankfully, now i can adjust my screen resolution.


[SIZE=5]Update #5[/SIZE]

Sound. Ok, this was pretty straight forward. I installed the drivers that came with the mobo. When I tried it out, only two of the speakers were working (out of a 5.1 surround sound system). after a little poking around, i figured out that by default, most of the channels are muted. So i ran alsamixer from terminal, and unmuted the appropiate channels. Now the sound is working perfectly! 

[SIZE=5]Update #6[/SIZE]

Getting the DH Remote working. 

OK, on to the tough stuff. (for me anyways). I'm trying to get the DH Remote that came with the P5W DH Mobo working. searched the Asus website and posted on their forums, but no luck. Thanks to RapMan for informing me that installing LIRC from source will do the trick. (at least i hope!) thing is, being a newbie, i haven't done this before, so here goes nothin'. 

I installed *dialog* as per the LIRC documentation, downloaded and unpacked the tarball, and tried running the configure script. There's a long list of hardware supported, but I didn't see the Asus DH remote listed specifically. So I used the *Asus Digimatrix IT87xx CIR port* option. After finishing the installation, I had to add the following line to *etc/modules*

alias char-major-61 lirc_it87

as per the [LIRC instructions]("http://www.lirc.org/html/install.html")


[SIZE=5]Update #7[/SIZE]

Well, it has been a while since I updated this thread. I've spent quite some time getting to know Ubuntu a little better, and still trying to get the DH Remote working. But back to that in a minute. 

I've decided to move on to phase two of the server (adding the RAID array). I have the Areca 1220 and 3 Seagate 500GB HDD's. Before attempting this, I decided to upgrade to Feisty. While updating, I was getting some nVidia errors. So I tried uninstalling Automatix, but that didn't help. I tried uninstalling Envy, but that broke X. Spent most of last night and today just trying to get X working again, but couldn't. I decided to just reformat for the upgrade. So now I'm running Feisty. I opted to enable the nVidia drivers in System -> Administration -> Restricted Drivers Manager as opposed to any third party scripts. All seems to be working now. I hope to spend the next day or two building the array. Wish me luck!


[SIZE=5]Update #8[/SIZE]

That was too easy. Everything went rather well. I installed the controller and drives, booted up, and entered the Areca McBIOS. Using the Quick Volume/RAID Setup, I configured the array and volume set and rebooted. After rebooting, it looked like X was broken again. But I swapped the RAID controller with the Graphics card, and all worked as it was supposed to. This is of particular importance to anyone wanting to use this RAID controller and MOBO combo. The manual says to use the primary (orange) PCIe slot for graphics cards, and the secondary (black) PCIe slot for other controllers, but I had to swap them in order for everything to work. Lastly, I went into gparted and formated the array. Now it all seems to work!

[SIZE=5]Update #9[/SIZE]

Just a quickie update. I plugged my speakers into the on board sound, and at first I was only getting sound out of the front channel. To remedy this, all I had to do was open the alsa mixer (double click on the speaker) then go to Edit->preferences and put checks next to the appropriate channels (IE "surround", "front", and "center") and BAM! I've got surround sound! No manual editing of any config files. sweeeet.

[SIZE=5]Update #10[/SIZE]

Another quickie update. The RAID volume wasn't automatically  mounting, so i used [this]("http://www.tuxfiles.org/linuxhelp/fstab.html") guide to edit my /etc/fstab file. It was pretty darn easy and straight forward, only requiring me to add a single line to the end of the file with the configuration information.

---

### Post by nphx on 2007-03-22
Nice story. You should include some picture illustration in it.

---

### Post by Jeffa on 2007-03-23
> **nphx said:**
> Nice story. You should include some picture illustration in it.

good point. I should have thought of that!

---

