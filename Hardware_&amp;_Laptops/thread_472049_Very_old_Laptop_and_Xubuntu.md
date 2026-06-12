---
title: "Very old Laptop and Xubuntu"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by vorob on 2007-06-12
Hi, I&#8217;m installing your OS because, as I read, it is oriented to old PC, I&#8217;ve got that one, Laptop P3-450Mhz, 2mb video and 192mb ram. It also has got a very old Cd-Rom, speed 24x. I&#8217;ve downloaded and burned Xubuntu on CD-RW and it runs VERY slowly from it. Load time is about 20min and installation over 1-2 hours. May be you will make an option in your future versions to cache some data on Hard Drive. Or, at least load Install utility in RAM so it won&#8217;t bother CD, that&#8217;s how I imagine that: I just start Live is loads (from CD-ROM), Run Install (All 7 steps loads in RAM), select all options I need, press install and then is again start running from cd to copy files. 

P.s. maybe you have something like Alternative Ubuntu version? Where you dont need to start LIVE OS to install but in some kind of DOS, with menus :)


Sorry for my grammar, i'm rus :)

---

### Post by energiya on 2007-06-12
You could try [Zenwalk]("http://www.zenwalk.org/"). I find it faster than XUbuntu.

---

### Post by bapoumba on 2007-06-12
> **vorob said:**
> Hi, I’m installing your OS because, as I read, it is oriented to old PC, I’ve got that one, Laptop P3-450Mhz, 2mb video and 192mb ram. It also has got a very old Cd-Rom, speed 24x. I’ve downloaded and burned Xubuntu on CD-RW and it runs VERY slowly from it. Load time is about 20min and installation over 1-2 hours. May be you will make an option in your future versions to cache some data on Hard Drive. Or, at least load Install utility in RAM so it won’t bother CD, that’s how I imagine that: I just start Live is loads (from CD-ROM), Run Install (All 7 steps loads in RAM), select all options I need, press install and then is again start running from cd to copy files. 

P.s. maybe you have something like Alternative Ubuntu version? Where you dont need to start LIVE OS to install but in some kind of DOS, with menus :)


Sorry for my grammar, i'm rus :)
For the alternate version, click the box under the green "start download" button. It runs the text-mode debian installer.
[http://www.ubuntu.com/GetUbuntu/download]("http://www.ubuntu.com/GetUbuntu/download")

And its not our OS, its yours too if you wish ;)

---

### Post by vorob on 2007-06-13
Guys, very strange problem, when I ask ubuntu to shut down, it makes all necessary operations, but don&#8217;t turn off the power. Ubuntu logo still on the screen, and I&#8217;m sure that OS done everything it needs, except the last step turn off laptop. What shall I do? On the previous version there was the same thing. But on Mandriva there is nothing similar, all is ok.

Thx.

---

### Post by whayong on 2007-06-13
If you don't care for looks, try turning off the splash screen.  Mine runs faster without it.  

I would also try the alternative CD route with fluxbox, if you don't mind tinkering a bit.

Also, you may like puppy linux.  I just heard about it the other day but had some problems running it in my laptop (mostly user error), but I did get it to run on a desktop.  I installed it on a 128 MB memory stick but have yet to boot from it.  I just didn't have the time to mess around with it to much, maybe sometime today, or tomorrow, or.... (you know how it goes).  It should load the "live CD" into RAM and run the OS from there.  This might actually be a better choice for you.  I haven't used Damn Small Limux, or any other "smaller" OS's so I couldn't comment on them.

---

### Post by kerry_s on 2007-06-13
sounds like a apm or acpi problem,but you didn't give that type of info, infact you didn't tell us the make and model at all. post your /var/log/syslog

I also run a 450mhz 256ram machine and tried many distro's. I found debian to be the best and fastest on this old rig(vaio pcg-f430) boot is only 37sec's, i use a custom/minimal install and fluxbox.

---

### Post by kerry_s on 2007-06-13
whayong,
 try adding these boot options->

lapic pci=routeirq

to your boot line->

kernel		/boot/vmlinuz-2.6.21-1-686 root=/dev/hda1 ro vga=791 lapic pci=routeirq

post your /var/log/dmesg so we might see if we can spot why you can't restart.

---

### Post by vorob on 2007-06-14
If I understand your post correctly **whayong**, you are talking about Live Cd, and I&#8217;m already installed Alternative Ubuntu :) 

Here are specs of me Laptop, it&#8217;s 1999 year and here is configuration [http://vorob2.nm.ru/System.pdf](http://vorob2.nm.ru/System.pdf)

You asked me about **&#8220;/var/log/syslog&#8221;** but I&#8217;m sorry, I&#8217;m a newbie in *nix OS, so where can I check them?

My ubuntu loads 2 minutes, if you don&#8217;t believe here is it&#8217;s booting video [http://rapidshare.com/files/37113163/Ubustarts.avi](http://rapidshare.com/files/37113163/Ubustarts.avi)

After boot manager I see for several seconds this 
[[IMG]http://img79.imageshack.us/img79/1189/dcam0215ss1.th.jpg[/img]](http://img79.imageshack.us/img79/1189/dcam0215ss1.jpg) what is that? 

So my questions is, how to speed up boot process because windows xp loads in 10-15 sec on this machine and how to instruct him to turn off the PC :)

---

### Post by kerry_s on 2007-06-14
Okay, it's like i said it's a acpi problem. Press alt+F2 type> **gksu mousepad /boot/grub/menu.lst**

this will bring up the grub file you need to modify.

scroll down till you see a section like this(mine is a little different, i use debian)

```
title		Debian GNU/Linux, kernel 2.6.21-1-686
root		(hd0,0)
**kernel		/boot/vmlinuz-2.6.21-1-686 root=/dev/hda1 ro vga=791 lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.21-1-686
savedefault

```

the area in bold is what you want to add to->

kernel		/boot/vmlinuz-2.6.21-1-686 root=/dev/hda1 ro vga=791** acpi=force**

That should take care of your turn off problem.
syslog> press alt+F2 type>** mousepad /var/log/syslog**
With a full Xubuntu you ain't going to see no fast boot times. You can try lightning the load by uninstalling what you don't need, but since your a newby, it would be better for you to just start learning the in's and out's of linux before even thinking about performance.

---

### Post by whayong on 2007-06-14
> **kerry_s said:**
> whayong,
 try adding these boot options->

lapic pci=routeirq

to your boot line->

kernel		/boot/vmlinuz-2.6.21-1-686 root=/dev/hda1 ro vga=791 lapic pci=routeirq

post your /var/log/dmesg so we might see if we can spot why you can't restart.

Thanks for the initiative to help me out.  I don't have my lappy with me at work, but I will post what you requested as soon as I get home and start a new thread so as not to clutter this one.

---

### Post by vorob on 2007-06-18
On all *nix distributives, in all video players, and in all video files, I&#8217;ve got a strange line under videos. Here is shot. What is that and how to fix it?

[[IMG]http://img405.imageshack.us/img405/7870/dcam0520io0.th.jpg[/IMG]](http://img405.imageshack.us/img405/7870/dcam0520io0.jpg)

---

### Post by vorob on 2007-06-19
And another strange thing. Sometimes, without a reason *nix loads with horrible colors, only full rebooting helps. 

[[IMG]http://img404.imageshack.us/img404/7205/dcam0542gx9.th.jpg[/IMG]](http://img404.imageshack.us/img404/7205/dcam0542gx9.jpg)

---

### Post by kerry_s on 2007-06-19
it looks to me like your not running the right vid driver or using the right settings.
What are your specs, please provide some info on your hardware.

also you should start your own thread instead of mixing with someone elses, so it's easier to find and keep track of for people trying to help.

---

### Post by vorob on 2007-06-19
> **kerry_s said:**
> it looks to me like your not running the right vid driver or using the right settings.
What are your specs, please provide some info on your hardware.

also you should start your own thread instead of mixing with someone elses, so it's easier to find and keep track of for people trying to help.


That's my thread :)

Specs: Toshiba Satellite Pro 4220XCDT 

P3-450Mhz (Core Coppermine), 192Mb so dimm 144-PIN / 100 MHz, Trident Cyber 9525 - AGP 2x / 2Mb 
[http://www.dooyoo.co.uk/laptops/toshiba-satellite-pro-4220xcdt/details/](http://www.dooyoo.co.uk/laptops/toshiba-satellite-pro-4220xcdt/details/)

---

### Post by kerry_s on 2007-06-19
Okay you almost the same specs as my vaio. My guess is your running on 24 color when your system only supports 16.

sudo mousepad /etc/X11/xorg.conf

look for>	DefaultDepth	24
and change to->
DefaultDepth	16

looks like this in mine->

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection
```

---

### Post by vorob on 2007-06-19
Nope, all is ok, i've got **DefaultDepth 16**

---

### Post by kerry_s on 2007-06-19
let me have a look at your xorg.0.log

mousepad /var/log/Xorg.0.log

---

### Post by vorob on 2007-06-19
> **kerry_s said:**
> let me have a look at your xorg.0.log

mousepad /var/log/Xorg.0.log

Here you go man :) [http://vorob.nm.ru/Xorg.0.log](http://vorob.nm.ru/Xorg.0.log)

---

### Post by kerry_s on 2007-06-19
okay i'm going to start from the top and work my way down.

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.

this can be fixed with> sudo apt-get install xfonts-cyrillic
or 
if you want to save space

sudo mkdir /usr/share/fonts/X11/cyrillic

cd  /usr/share/fonts/X11/cyrillic

sudo mkfontdir


(==) AIGLX enabled

unless your using it, you should disable aiglx and composite, that will give you a bit of speed and save on resources.

sudo mousepad /etc/X11/xorg.conf

put this at the end of your xorg, make sure you leave a empty/blank line at the bottom.

```
Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection

```


(==) TRIDENT(0): Backing store disabled

in your xorg device section you can enable this with-> Option "BackingStore" "true"

looks like this->

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"trident"
	Option		"BackingStore"	"true"
EndSection
```


(EE) AIGLX: Screen 0 is not DRI capable

when you disable it this will go away


Okay, im not sure what to tell you on the synaptic and wacom errors, synaptic if it was me i would just uninstall it and remove the entries in xorg, cause you don't have a touchpad.
The wacom is a little weird, i know you have the eraser pointer and it use the wacom driver for eraser, which is the same for the stylus and cursor. i think your just stuck with those errors :( man i hate leaving errors.


Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

make sure you have> x-ttcidfont-conf <installed
otherwise you can just link them to /usr/share/fonts/X11

sudo ln -s /usr/share/fonts/X11/misc /usr/X11R6/lib/X11/fonts/misc
sudo ln -s /usr/share/fonts/X11/Type1 /usr/X11R6/lib/X11/fonts/Type1


other than those i don't really, see what could be causing your problem, but i'm thinking since your running a full xubuntu you might just be running low on resources for full screen vid. Sorry i know that doesn't help, but maybe you can find the manuel and read through it to see if your limited on full screen, like for mine it says for quailty video i need to use 800x600 for full screen, which is stupid, i'm not changing resolutions just to watch a video.

---

### Post by vorob on 2007-06-20
First of all thx **kerry_s**, not everybody would read my log and check for errors :)

But. I'm not using Xubuntu, I'm using full Ubuntu :)

And now, step by step to your post

I've added lines in xorg.conf

[B]Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection[/B]

Then about

**in your xorg device section you can enable this with-> Option "BackingStore" "true"**

I didn't find anything similar. Only this:

[B]Section "Device"
	Identifier	"Trident Microsystems Cyber 9525"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection[/B]

Will it be ok if add this line **Option		"BackingStore"	"true"** or i don't need it because of ubuntu not xubuntu? Or what? :)

Then, as you said, i deleted synaptic :) but didn't touched wacom cause i don't eve understand whats the problem with it?

Next 

[B]Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

make sure you have> x-ttcidfont-conf <installed[/B]

As i understand **x-ttcidfont-conf  **is **Configure TrueType and CID fonts for X**? It is fully installed.

Didn't fully understand this passage

**other than those i don't really, see what could be causing your problem, but I'm thinking since your running a full Xubuntu you might just be running low on resources for full screen vid. Sorry i know that doesn't help, but maybe you can find the manuel and read through it to see if your limited on full screen, like for mine it says for quailty video i need to use 800x600 for full screen, which is stupid, i'm not changing resolutions just to watch a video.**

Default resolution of my laptop is 1024x768 with 16bit.

P.s. what is the difference between add/remove and synaptic package manager? In last one more progs but not very friendly interface :)

---

### Post by kerry_s on 2007-06-20
yeah just add to that

Section "Device"
Identifier "Trident Microsystems Cyber 9525"
Driver "trident"
BusID "PCI:1:0:0"
Option "BackingStore" "true"
EndSection


synaptic is better, i always uninstall the add/remove program on any of my full installs.

---

### Post by ubuntu27 on 2007-06-20
> **vorob said:**
> Hi, I’m installing your OS because, as I read, it is oriented to old PC, I’ve got that one, Laptop P3-450Mhz, 2mb video and 192mb ram. It also has got a very old Cd-Rom, speed 24x. I’ve downloaded and burned Xubuntu on CD-RW and it runs VERY slowly from it. Load time is about 20min and installation over 1-2 hours. May be you will make an option in your future versions to cache some data on Hard Drive. Or, at least load Install utility in RAM so it won’t bother CD, that’s how I imagine that: I just start Live is loads (from CD-ROM), Run Install (All 7 steps loads in RAM), select all options I need, press install and then is again start running from cd to copy files. 

P.s. maybe you have something like Alternative Ubuntu version? Where you dont need to start LIVE OS to install but in some kind of DOS, with menus :)


Sorry for my grammar, i'm rus :)

There is Xubuntu ALternate CD, which is not a LiveCD, but rather just a specialized INSTALL CD. This will be much faster as it does not need to load the desktop for testing purposes. 

You can get it here:

Direct Iso download:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

Bittorrend DOwnload:
[http://torrent.ubuntu.com/xubuntu/releases/feisty/release/alternate/](http://torrent.ubuntu.com/xubuntu/releases/feisty/release/alternate/)


Make sure to download the ALTERNATE CD, and the version that you want (64bit or 32bit? I bet you want 32bit, so **try i386**)

---

### Post by vorob on 2007-06-27
Hello once again :) I've got a new portion of questions. First of all, in SYSTEM > PREFERENCES > FILE MANAGMENT I've found how to turn on preview for files smaller then 500kb, and it is working, but my video films, it weight much more then 500kb but also have preview. That's strange. 

Also i didn't find any program to mount and unmount my drives. Thanks to ubuntu default setup which already mounted all my hard rives of windows OS, but for some strange reason i can't edit my hard where XP is installed. I would like to change this. 

And the last thing, in Open Office word, how to choose on which language I'm writing? Example: i wrote something on Russian (I've got rus open office) and it is ok, he checked my grammar and other things, and then in the same document I write something in English, but open office is still thinking that I'm writing on Russian and stress everything i wrote...

---

