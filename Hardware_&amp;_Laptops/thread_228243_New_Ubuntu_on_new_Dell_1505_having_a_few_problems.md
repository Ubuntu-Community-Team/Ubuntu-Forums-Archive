---
title: "New Ubuntu on new Dell 1505 having a few problems"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by vanilla.gorilla on 2006-08-02
Hi guys and gals,

This is my first post and my first jump to ubuntu(used suse for a while or so).  Let me say my first impressions are awesome.  As for all the linux I have tried over the past year, Ubuntu completely outclasses them in my eyes.  It is very slick. 

Now, onto the questions,

It is only detecting one CPU.  For those that need to know my sys. specs are as follow
T2400 Dual Core
1 gb Ram
NvidiaGo 7300
100 gb HD

When I run cat /proc/cpuinfo it lists my cpu as 0.  Meaning one.  Now I know the command that should supposedly fix this(having googled this) and it does not run because I don't have permission/and or internet access.  When from a terminal I cannot su into root.  My password is bad it says, but I don't ever remember doing one during the install.

Last question is my wireless.  On my old suse comp I got ndiswrapper to work but am clueless where to start for this new card.  Any pointers would be helpful.

Thanks for any help guys.  I really have no idea about my SU password not being good.  How the crap do I fix that?

-Vanilla.Gorilla-

---

### Post by cromestant on 2006-08-02
you might need to isntall an smp kernel

\just a thought

they are in apt

---

### Post by vanilla.gorilla on 2006-08-02
Ok I have the wireless working now.  That was so easy.  Put one more in the Good column for ubuntu.  I still cannot log into root in a terminal, but when I use some of the administrative tools, it prompts me for a password, and the one I am trying in the terminal works(this is the password I ALWAYS use). 

And I am not experienced enough to recompile my kernel with smp support unless it goes flawlessly. I ran ::

sudo apt-get install linux-686-smp
***get prompted for password, enter the same darn one that I try when trying SU***

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-686-smp

I have no idea.  It looked so simple when I googled it. Do I need to have my install cd inserted?

Again thanks for all the help guys.

-VanillaGorilla-

---

### Post by MarkSheely on 2006-08-03
No, you won't need your install cd, and you won't need to compile anything.  Go into synaptic (System->Administration->Synaptic) 

Click on Search - enter "linux-686-smp"

When the package comes up, click on the box to mark it for installation, click on "apply" (in the toolbar next to "search"), and reboot - you'll be all set.  

That's more or less it, if I remember right.  

--Mark

---

### Post by vanilla.gorilla on 2006-08-03
Thanks for the help mark.  I went into the synaptic package manager, and it prompted for my password that doesn't work in the terminal, but strangeley works here, and it looks very clean.

The search for linux-686-smp came up nil. I hit that search button at the top adn typed it in, and it brought something up on the left hand side, but nothing is available when I click it.  When I highlight the all tab and search within that field, I do not get a linux-686-smp.

Any ideas? Or am I newbing out.

-VanillaGorilla-

---

### Post by vanilla.gorilla on 2006-08-03
Apparently my touchpad is a little touchy.  I got the list to populate on the right and am dl'ing the packages now.... fingers crossed

It said everything was installed succesfully, but my cat /proc/cpuinfo still pulls up 0  for the processor. Ima restart and see.

Hooray! I have the net and the dual procs working now!  Very awesome and quite fast on the startup.  Starting up this laptop linux beats windows by over 10 seconds.  Impressive.

One last thing.  I still cannot log in as root in the terminal.  Outside of the terminal its just fine.  Any clues?

---

### Post by MarkSheely on 2006-08-03
Nope - that problem has me stumped.  I can't think of why you would experience password problems only when using the terminal.  Maybe someone more knowledgeable than I can help?

--Mark

---

### Post by vanilla.gorilla on 2006-08-03
Thanks for the help Mark, I will repost a more concise message and see if I can get an answer.

---

### Post by UltraMathMan on 2006-08-03
If I understand you correctly you are attempting to become root using "su root". In Ubuntu you do not switch to root in the terminal, you borrow root privileges using the prefix sudo, so

```
sudo *command*
```
will prompt you for your password and run the command "as root". Hope this helps!

---

### Post by kufford on 2006-08-04
MathMan is correct. Basically, you enter your user password in order to use root privileges as you are entered as a sudoer. You can log into root by setting a super user password.

```

# sudo passwd

```

It should ask you for your user password and then give you the option of setting a unix (root) password. Then, you can operate as root by simply typing:

```

# su

```

Be careful with it though... sudo is a much safer method of dealing with permissions...

Good luck.

---

### Post by 5-HT on 2006-08-04
> **kufford said:**
> You can log into root by setting a super user password...

Alternatively, you could always get a root shell without having to unlock the root account by either: ```
 sudo -s
``` or ```
sudo -i  #to simulate a root login shell
``` or ```
 sudo su 
```

---

### Post by mattyj on 2006-09-16
Hello,

Are your having any problems with overheating or is everything pretty much working well?

I would like to get an E 1505 but was concerned by this:

[http://ubuntuforums.org/showthread.php?t=186003](http://ubuntuforums.org/showthread.php?t=186003)

Thanks,

MJ

---

### Post by UltraMathMan on 2006-09-16
My E1505 idles at ~30-40°C, and hit a max of 65°C for a few seconds once or twice. I haven't had any problems heat-wise with mine :)

---

### Post by mattyj on 2006-09-16
Thank You very much,

How do you monitor the temp?  Was that a BIOS problem?  Any ideas what to look out for?

---

### Post by UltraMathMan on 2006-09-16
I use a gnome applet that sit on one of my panels, [http://computertemp.berlios.de/](http://computertemp.berlios.de/) 

I don't really know what is causing the problems, but I haven't seen anything extraordinary yet

---

### Post by NTolerance on 2006-09-18
How do you make lm-sensors work with the E1505?  It doesn't detect any sensors for me.  #-o

---

### Post by UltraMathMan on 2006-09-18
I'm not sure what you mean, are you trying to run the applet I posted above?

---

### Post by NTolerance on 2006-09-18
I was trying the applets that are included with GNOME.  I'll try yours if my E1505 sound issues are ever fixed.

---

### Post by UltraMathMan on 2006-09-18
Sound issues -> [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Helped me work through a couple problems

---

### Post by mattyj on 2006-09-18
Ultramathman,

Are you using the stock BIOS to control the fans, or did you go with the i8k solution?

---

### Post by UltraMathMan on 2006-09-19
I didn't make any changes to the fan control, so stock BIOS

---

### Post by ysr on 2006-09-24
> **NTolerance said:**
> How do you make lm-sensors work with the E1505?  It doesn't detect any sensors for me.  #-o

Looking at this thread [http://www.ubuntuforums.org/showthread.php?t=2780]("http://www.ubuntuforums.org/showthread.php?t=2780")  seems like few have had any luck with lm-sensors on dell laptops. In fact, laptops in general seem to be problematic, presumably because of their custom chipsets. For a quick, one off look at the temperature, do ```
acpi -V
``` For an applet that sits in your panel that you can keep an eye on, do ```
 sudo apt-get install sensors-applet
``` Then right click on your panel-->add to panel-->System and Hardware-->Hardware Sensors Monitor. If you have the i8k kernel module for dll laptops loaded, you should also be able to monitor fan speeds. (Right click on the applet --> properties, and check out the i8k section). Some people seem to prefer the gkrellm-i8k to achieve the same (which also needs the i8k kernel module loaded, by the way).

---

### Post by dogriley on 2006-09-27
Which wireless card did the 1505 come with, and did you use ndiswrapper ?  I could not get the Dell 1500 Mini Card, Draft N card with ndiswapper.  I could get it to an installed state, and even get the card to scan local access points, but could not get it connected.  

TO stop the bleeding in lost time, for $35 from amazon I ordered a Intel 3495 ABG Mini PCI and it is supported  with the stock 6.06 distribution.

> **vanilla.gorilla said:**
> Ok I have the wireless working now.  That was so easy.  Put one more in the Good column for ubuntu.  I still cannot log into root in a terminal, but when I use some of the administrative tools, it prompts me for a password, and the one I am trying in the terminal works(this is the password I ALWAYS use). 

And I am not experienced enough to recompile my kernel with smp support unless it goes flawlessly. I ran ::

sudo apt-get install linux-686-smp
***get prompted for password, enter the same darn one that I try when trying SU***

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-686-smp

I have no idea.  It looked so simple when I googled it. Do I need to have my install cd inserted?

Again thanks for all the help guys.

-VanillaGorilla-

---

### Post by UltraMathMan on 2006-09-27
I got the Intel 3945 card with my E1505, figuring it would be more mainstream than a dell card and therefore easier to get working (I didn't buy the laptop with the intention to install linux though - I guess I just got lucky).

---

### Post by joekepley on 2006-09-30
I just bought an Inspiron 6400 which I'm told is exactly the same as the E1505, except for the badge on the case. 

Here's my setup: 

[LIST]
[*]T7200 Core 2 Duo 2Ghz Processor
[*]Nvidia Geforce Go 7300 GPU
[*]Intel Wireless
[*]DVD-RW
[*]Bluetooth
[*]1680x1050 Display
[*]2GB RAM
[/LIST]

Install was fairly normal. Wireless, sound, CD burner, volume controls, hibernate, suspend and  most everything else worked right out of the box. The standby/hibernate Fn keys don't seem to work. Media controls (play, ffw, rew, etc) weren't auto-configured, but could be assigned through the GNOME preferences, so I'll count those as 'works'.

[SIZE="4"]Dual-core[/SIZE]
Only detected one proc after the install, so I used apt to install the smp kernel. Enabled virtualization support in BIOS so that VMWare Workstation could use the processor's virtualization to run XP as a guest. For some reason it took a REALLY long time to go through POST after doing this the first time, but everything's normal since then and VMWare runs very quickly. Speedstep functions as it should.

[SIZE="4"]Graphics[/SIZE]
The nv driver worked fine for 2D, but I had a couple problems after installing the proprietary Nvidia driver from apt. 

Once the nvidia driver loaded, I couldn't Ctrl-Alt-F1 to the desktop any more, I'd just get a black screen. Disabling the splash screen solved this (edit /boot/grub/menu.lst, remove 'quiet splash' from the kernel parameters, reboot). 

Second problem: XGL and compiz would work fine on the display, but not if the display was running in TwinView mode with an attached external monitor. Upgrading to nvidia driver version 8774 solved this. Running compiz and XGL  , I get an occasional 'why-did-I-spontaneously-wind-up-back-at-login', but I chalk that up to running compiz and XGL. Edgy allows you to run AIGLX with the Nvidia propietary driver, so I'm looking forward to running that come November when edgy stablizes. 

Third Problem: The CRT/LCD Fn key seems to do nothing. My work-around hack for this is to have two xorg.conf files saved. I inserted a script right before X loads in the init process that uses iwconfig to sniff the wifi environment, and loads the twinview xorg.conf if I'm at work (where my second monitor is), or a single-display xorg.conf otherwise. Kinda goofy, but it works pretty well.

[SIZE="4"]Bluetooth[/SIZE]
Bluetooth worked out of the box, but the generally crummy support for it in gnome makes it a bigger hassle than it needs to be. apt-got bluez-*, btsco, and gnome-bluetooth. Lots of futzing around eventually allowed me to upload contacts to my phone, connect for dial-up networking, and use a bluetooth headset for ekiga. 

[SIZE="4"]Fan/Temp[/SIZE]
Modprobe won't load the i8k module unless you force it to, but when you do, it works. I'm not sure at this point if I should do this or let BIOS handle the fan speed. I'm going to watch the ACPI thermal monitor for a while and decide if I want to hand fan control over to the OS instead of the BIOS. Anyone else have any experience with this?


[SIZE="4"]Card Reader[/SIZE]
The one thing I don't yet have working is the card reader. It works for a 32MB SD card I have, but not for xD or a 256MB MMC. I understand that this is supported in newer kernels, so I'm trying to read up on the 'Ubuntu' way to compile and install your own kernel without messing up package management (I'm mostly a Gentoo guy). Any advice there would be appreciated.

---

### Post by arthur_kalm on 2006-11-18
Yeah, don't bother making a password for root. If you want to always work as root, just type
```
sudo su
```
And you will become the super user. Enter your regular password there.

---

