---
title: "ATI Switchable Graphics Thread"
date: 2011-04-25
forum: Hardware
---

### Post by ultimatebuster on 2011-04-25
I'm currently using a Lenovo Y460 laptop with ATI 5650 as well as an embedded graphics card inside my CPU, i5 M430.

It appears that Ubuntu/Linux doesn't doesn't like the switchable graphics in my laptop.

As far as I know, switchable graphics works this way: When switchable graphics mode is on, both the dedicated and the integrated chip is turned on. This allows the OS to turn off 1 of the chip in order to gain maximum performance (in the case of the dedicated graphics) or maximum battery (in the case of the integrated graphics). 

However, installing the fglrx driver will break X when the switchable graphics is on, therefore forcing the user into commandline. While commandline is great, you can't do much work under that. 

Using the open source driver will leave both card on, draining a LOT of power and overheating the laptop to 75~85C. 

This means that Ubuntu is completely unusable with this laptop.

If you googled search "ubuntu switchable graphics", there many threads about this issue, none of which gives this a definitive solution.

I realize that this is probably an AMD issue, but I'm wondering if anyone else have made any progress in fixing this problem.

---

### Post by Yellow Pasque on 2011-04-25
If you can still return your Y560, do it now.

---

### Post by ultimatebuster on 2011-04-25
Can't, and it's a great laptop.

All new i5 and i7 has integrated graphics. Any laptop with an additional dedicated card should be able to switch between the 2 either via ATI Switchable or NVIDIA Optimus

---

### Post by Yellow Pasque on 2011-04-26
> **ultimatebuster said:**
>  Any laptop with an additional dedicated card should be able to switch between the 2 either via ATI Switchable or NVIDIA Optimus

It can.. in Windows, but it's a no go on Linux. :(

---

### Post by ilembitov on 2011-04-26
Same here. I own HP Envy 13 with Ati HD4330 and Intel GMA4500MHD. I think you should wait for Ubuntu 11.04, which comes with Catalyst 11.4 [that should support some sort of GPU switching]("http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ"). But I'm not sure how well it works, didn't test it myself. Otherwise, you might want to check vga_switcheroo approach. However, it only works with open source ATI drivers.

Sorry folks, but my HP Envy 13 is a great machine, and if I have to stay on Windows, I'll do just that. It's well buit, fast (although the specs are dated), lasts long on a battery charge (8-9 hours on full screen brightness and active wi-fi). And it's dirt cheap right now - about $750. Even though I've used Linux for the past 7+ years, Envy 13 packs a killer-combo for me.

---

### Post by belltown on 2011-04-26
Here are a few articles on Phoronix that discuss the issue:

_[[SIZE=2]AMD's Catalyst Misses The Support Train, Again[/SIZE]]("http://www.phoronix.com/scan.php?page=news_item&px=OTI2OQ")_

_[[SIZE=2]Here's The Special AMD Present For Ubuntu Users[/SIZE]]("http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ")_

_[[SIZE=2][COLOR=black]PowerXpress Support Notebooks Under Linux[/COLOR][/SIZE]]("http://www.phoronix.com/scan.php?page=news_item&px=OTI3Mg")_

For now, however, you can use vgaswitcheroo to switch graphics cards between the ATI 5650 and intel integrated graphics to power down the unused card, as described in the _[Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics")_ wiki.

---

### Post by ultimatebuster on 2011-04-26
Also I'm forced to use WUBI because It's not possible to install it along side Windows without reformatting my drive (an extended partition at the end of the partition table).

I need linux for a lot of development based task, if this doesn't work I might just stick Ubuntu in a virtual machine on top of windows.

---

### Post by ultimatebuster on 2011-04-26
I just installed the 11.04 beta and installed fglrx, it no longer kicks me into terminal, which is good.

However, unity no longer starts after installing fglrx. Attempting to start the catalyst control panel gave me:

> There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

Temperature no longer shows ATI card, and temperature of the CPU is still at about 70C

---

### Post by Yellow Pasque on 2011-04-26
> **ultimatebuster said:**
> I just installed the 11.04 beta and installed fglrx, it no longer kicks me into terminal, which is good.

You seem to be confused (or one of those individuals that refuses to believe s/he's pretty much SOL with switchable graphics on Linux). You're using the Intel IGP, NOT the Radeon. All the Radeon is doing is sucking battery and generating heat. Installing ATI drivers won't help unless you have a BIOS switch to turn off the Intel GPU. See this to remove fglrx/Catalyst and get 3D working again: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by ultimatebuster on 2011-04-26
I know that part. I'm aware that the ATI card is not doign anything.

This really should be simpler, has been a problem ever since 10.04

---

### Post by Yellow Pasque on 2011-04-26
Good luck with that..

---

### Post by ZeroXtreme on 2011-05-01
I'm running a dual boot configuration on my Y460 with Windows 7 Ultimate x64 and Ubuntu Natty 11.04 x64.

Under Windows, everything runs fine since all drivers are provided, under Linux almost all soft keys do not work, but thats about the extent of my problems and it is acceptable at this point for me.

BTW, I configured the BIOS to run under "Discrete Graphics" rather than "Switchable Graphics" to get the full functionality of the ATI Graphics Card since switchable graphics is still not supported in Linux, and I actually almost never switch to the Intel Graphics Card even under windows.

Just my two bits on the matter.

---

### Post by antskip on 2011-05-01
> **ZeroXtreme said:**
> I'm running a dual boot configuration on my Y460 with Windows 7 Ultimate x64 and Ubuntu Natty 11.04 x64....I configured the BIOS to run under "Discrete Graphics" rather than "Switchable Graphics" to get the full functionality of the ATI Graphics Card since switchable graphics is still not supported in Linux, and I actually almost never switch to the Intel Graphics Card even under windows
doing the same -  using a wubi 64bit install within a win7 32bit (use 32bit in win7 because of mediocre lenovo 64bit driver). used switchable graphics in windows for almost two years without ever wishing to switch to the intel gpu, so now use external ati gpu in dedicated mode. runs like the wind in ubuntu, as does system in general -  even in wubi install.

I have had a couple of system freezes which are a worry, and hope to find out the reason or fix. until then not keen to do a linux file system install...

---

### Post by aeronutt on 2011-05-01
> **Temüjin said:**
> If you can still return your Y560, do it now.

> **Temüjin said:**
> Good luck with that..

These types of comments are not helpful.

---

### Post by aeronutt on 2011-05-01
I'm having similar problems with Dell Vostro 3550, Intel i3 processor, and AMD Radeon HD6000 series discrete graphics.  Here's what I can't do yet:

- can't use the proprietary fglrx
- can't use vga_switcheroo (Also, vga_swicheroo needs to write to a file that in 11.04 is now owned by root. I haven't figured out the secure way to fix that.)

Here's what I can do:
- using radeon.modeset=1 or 0 and i915.modeset=1 or 0 during boot in grub, I can at least boot, and Unity recognizes my hardware as good enough for unity 3d. A graphics benchmark showed that with radeon.modeset=1, I was getting better performance than with i915.modeset=1. However, performance is not as good as the h/w should allow (compared in windows, for example.)

Here's a thread I started on the same topic.  
[http://ubuntuforums.org/showthread.php?t=1743108](http://ubuntuforums.org/showthread.php?t=1743108)
But happy to stay here and help with a solution. But I'm a rookie to all this.

---

### Post by Yellow Pasque on 2011-05-01
> **aeronutt said:**
> These types of comments are not helpful.
That depends on your definition of helpful. Some people have returned systems after they found out that they couldn't use the GPU they thought they were getting.

It's a shame you don't find my suggestions useful, but I'm not bothered by it. You can lead a horse to water, but you can't make it drink..

---

### Post by aeronutt on 2011-05-01
> **Temüjin said:**
> That depends on your definition of helpful. Some people have returned systems after they found out that they couldn't use the GPU they thought they were getting.

It's a shame you don't find my suggestions useful, but I'm not bothered by it. You can lead a horse to water, but you can't make it drink..

Interesting opinion, as there's nothing fundamentally wrong with my graphics. I know this because they work great in Windows, so I must assume there IS a way to get them to work well in Linux. Rather than succumbing to buying old hardware, I'd prefer to work with the community for a solution. Now, if there is a fundamental reason these graphics resources can't work in Linux, I'm all ears.

---

### Post by nosushi4you on 2011-05-04
> **aeronutt said:**
> I'm having similar problems with Dell Vostro 3550, Intel i3 processor, and AMD Radeon HD6000 series discrete graphics.  Here's what I can't do yet:

- can't use the proprietary fglrx
- can't use vga_switcheroo (Also, vga_swicheroo needs to write to a file that in 11.04 is now owned by root. I haven't figured out the secure way to fix that.)

Here's what I can do:
- using radeon.modeset=1 or 0 and i915.modeset=1 or 0 during boot in grub, I can at least boot, and Unity recognizes my hardware as good enough for unity 3d. A graphics benchmark showed that with radeon.modeset=1, I was getting better performance than with i915.modeset=1. However, performance is not as good as the h/w should allow (compared in windows, for example.)

Here's a thread I started on the same topic.  
[http://ubuntuforums.org/showthread.php?t=1743108](http://ubuntuforums.org/showthread.php?t=1743108)
But happy to stay here and help with a solution. But I'm a rookie to all this.

I'm having a very similar problem. The proprietary drivers disable Unity, but Unity seems to run very well when without the drivers. Could you please explain what you did to get your system to boot in a little more detail? I've been looking all over for a possible fix and have found nothing.

---

### Post by aeronutt on 2011-05-04
> **nosushi4you said:**
> I'm having a very similar problem. The proprietary drivers disable Unity, but Unity seems to run very well when without the drivers. Could you please explain what you did to get your system to boot in a little more detail? I've been looking all over for a possible fix and have found nothing.

I had to do a lot of surfing to find the answer also. But in the end pretty simple. To be clear, I have an Intel integrated graphics chip, plus AMD Radeon discrete graphics. This is apparently what Ubuntu (and all other Linux) can't handle, 2 graphics chips. So what I'm showing you simply disables the discrete AMD graphics.  There's a hook in the kernel that allows you to set some boot parameters for the graphics options. 

Edit /etc/default/grub, and change the following line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

To

GRUB_CMDLINE_LINUX_DEFAULT=radeon.modeset=0

then run update-grub.

That's it. Your intel integrated grahics should be working.

If you want to experiment with the boot options for the graphics cards, you can edit the kernel options at boot at the grub selection menu.  The two switches are i915.modeset=?  and radeon.modeset=?.  At grub menu, just hit 'e', then use your cursor to add/edit the above 2 options in the line that starts with 'linux /boot/vmlinuz....'.  Add the options to the end of the line, then hit control-x, and those options with be used for only that boot session.

I'm also going to load 11.04 onto a play  partition, and play with vga_switcheroo and the latest AMD proprietary driver. vga_switcheroo is another kernel option that is supposed to let you switch between 2 graphics card, but it only uses the open drivers. The latest AMD driver is also supposed to let you switch between an AMD graphics card using the AMD driver, and an integrated graphics. What I'm not sure of if the AMD driver supplied with 11.04 is the same one being offered by AMD on their web site. Here's some info. But over the next week, I'm hoping to find time to play with it all.

[http://www.phoronix.com/scan.php?page=news_item&px=OTM4Ng](http://www.phoronix.com/scan.php?page=news_item&px=OTM4Ng)

---

### Post by aeronutt on 2011-05-04
This looks promising:
[http://www.phoronix.com/scan.php?page=news_item&px=OTM4Ng](http://www.phoronix.com/scan.php?page=news_item&px=OTM4Ng)

Specifically:
"The Catalyst 11.4 Linux driver also offers the first bits of **AMD PowerXpress support under Linux**, but it's clunky in that the X.Org Server needs to be restarted when switching graphics adapters. This implementation is meant for switching between Intel and ATI Radeon graphics. "

Any have experience with the latest AMD PowerXpress in 11.04 ?
I assume that PowerXpress is NOT the same as simply loading the fglrx driver under 11.04 software sources?

---

### Post by nosushi4you on 2011-05-04
Thank you! Editing the GRUB like you said, I am now able to get my system to boot correctly every time. Plus, Unity works like a charm! I get decent performance from my Intel card, even 720P video plays smoothly.

---

### Post by ultimatebuster on 2011-05-07
I finally got Ubuntu 11.04 installed. I installed ATI Catalyst 11.04. The switchable graphics now seems to be working, kinda. (I guess you get 1 switch)

At first it kept telling me I can't switch. A couple restart later, I successfully was able to switch to integrated (Intel). It told me to restart, so I did so.

Unity tells me I cannot boot into it, so I'm in GNOME2 again. Attempting to fire up the catalyst control panel will give me. Same with aticonfig, fglrxinfo.

error while loading shared libraries: /usr/lib/libGL.so.1: file too short

I'm positive that I'm using the integrated graphics as my laptop temperature is holding steady at 44C, though I lost access to unity and the ATI Catalyst 11.4.

Under integrated graphics my second monitor has weird issues that makes everything "vibrate". Under discrete only that problem doesn't exist (if i enable discrete only in BIOS)

---

### Post by ultimatebuster on 2011-05-07
The above problem is fixed by downloading the ATI Driver from their website, do 
```

./ati-driv* --extract ~/ati

```

Go to nautilus and navigate to ~/ati
Search for libGL.so.1.2 and copy that somewhere, in mycase i just copied it to ~/ati
then

```

sudo cp ~/ati/libGL.so.1.2 /usr/lib/libGL.so.1.2

```

Switching now works, mostly. Requires you to log out and log back in. Might need to reset unity, if you switched from intel back to ATI.

Though Intel still fails if you want unity. Maybe there's a driver somewhere.

---

### Post by aeronutt on 2011-05-11
> **nosushi4you said:**
> I'm having a very similar problem. The proprietary drivers disable Unity, but Unity seems to run very well when without the drivers. Could you please explain what you did to get your system to boot in a little more detail? I've been looking all over for a possible fix and have found nothing.

Nosushi, I've found a better way. The previous way I described didn't power down the AMD chip. The better way is to leave the grub options alone, and edit rc.local and blacklist the radeon driver. When I did this way, I have; -reliable boot, increased battery life from 2 hours to 4 hours, uses integrated intel graphics. (I still cannot switch graphics by any method, eg vgaswitcheroo or AMD fglrx driver.)

See here:
[http://ubuntuforums.org/showthread.php?t=1744188](http://ubuntuforums.org/showthread.php?t=1744188)

---

### Post by marcelhekking on 2011-05-11
Hi aeronutt,

After days and days searching the internet I think your solution will work for me. Thanx! I am going to try this afternoon. Btw, could you please keep me informed on how your doing with the new drivers? 

Cheers,
Marcel

---

### Post by nosushi4you on 2011-05-11
> **aeronutt said:**
> Nosushi, I've found a better way. The previous way I described didn't power down the AMD chip. The better way is to leave the grub options alone, and edit rc.local and blacklist the radeon driver. When I did this way, I have; -reliable boot, increased battery life from 2 hours to 4 hours, uses integrated intel graphics. (I still cannot switch graphics by any method, eg vgaswitcheroo or AMD fglrx driver.)

See here:
[http://ubuntuforums.org/showthread.php?t=1744188](http://ubuntuforums.org/showthread.php?t=1744188)

Thank you for all your help. It's much appreciated. I finally got my switchable graphics working. Like ultimatebuster said, you have to install the new driver from AMD/ATI. Here is the guide I followed. EVerything works perfectly now. :D

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

I'm switching to GNOME3 now, though. It's more stable than people give it credit for.

---

### Post by aeronutt on 2011-05-11
So far, I've not been able to get the proprietary driver to work.
But I noticed a few things in that guide that I hadn't tried...thanks.

---

### Post by nosushi4you on 2011-05-11
It works with Unity for me. The switching doesn't work so well, even though the option is there in the Catalyst Control Center. But at least the ATI card now works with Unity. The bad news is that the new driver does not work with GNOME 3. So, I'm going to try your blacklisting method. It's not like I play games on linux or anything, anyways, and I could sure use the lower temperatures and increased battery life.

---

### Post by aeronutt on 2011-05-11
Yea, that guide isn't working for me. The commands:
sudo aticonfig --initial -f
and
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

both return "aticonfig: No supported adapters detected"

and fglrxinfo returns a segmentation fault.

And now....ubuntu won't boot w/o going into safe graphix mode.

Might have something to do with my graphics card, HD6630, fairly new I think.

I guess I have $100 worth of useless h/w when using Ubuntu. This is just such a shame, something as fundamental as graphics support, and Windows7 is so much better.

I'm going back to the blacklist method, and will maybe try all this agian in a few months. Lots of stuff wrong with this version of Ubuntu on my laptop...simple things like touchpad, booting, cam, screen brightness, graphics, responsivness of Unity, etc.

---

### Post by nosushi4you on 2011-05-11
I'm sorry the guide I posted did not work for you. It's a shame that newer graphics hardware does not have proper support for linux systems yet. I love switchable graphics when they work properly. I ended up using your blacklisting method, as the proprietary drivers break GNOME 3. It works like a charm. Thanks!

---

### Post by ultimatebuster on 2011-05-11
How did you guys get integrated card working? Unity doesn't work on mine.

---

### Post by jedikaine on 2011-05-13
> **nosushi4you said:**
> Thank you for all your help. It's much appreciated. I finally got my switchable graphics working. Like ultimatebuster said, you have to install the new driver from AMD/ATI. Here is the guide I followed. EVerything works perfectly now. :D

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

I'm switching to GNOME3 now, though. It's more stable than people give it credit for.

I also followed the guide and it finally worked!(Tried it on 10.10) I'm not sure if it's due to the new driver or because I used the X2/Dual GPU Cards configuration instead of the generic one.

My laptop has an option of either Intel HD graphics or ATI 5470 HD thru the Catalyst Control Center.

Thanks for posting the guide, nosushi4you! :cool:

---

### Post by ultimatebuster on 2011-05-14
Can you guys post the output of your fgrlxinfo while in integrated graphics?

I have:
> display: :1.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile GEM 20100330 DEVELOPMENT 
OpenGL version string: 1.4 (2.1 Mesa 7.10.2)

This results in me only being able to use the ubuntu classic (no effect). All other will result in failure.

---

### Post by aeronutt on 2011-05-14
Just FYI, I'm not using fglrx (AMD's proprietary driver). I haven't been able to get it to work.

---

### Post by depeha on 2011-05-14
Nice to find out someone's looking into this problem. I'd like to share my experiense with ATi/Intel grapihcs.

Few days ago, I installed Kubuntu 11.04, and tried new AMD's 11.5 driver. For the first time, I got working ATI 5650 on my HP (+ i5 450M graphics).
After installation, it took me to tty, I ran "aticonfig" with some argumets, don't remember all, but I think there was something with "-v", "-f" and few others. After next reboot I got working KDE. That was nice. First thing I noticed, desktop effects were just little bit faster than on Intel's i5 graphics. But there were also problems... It was impossible to get to tty (ctrl+alt+Fx combo). X just crashed. Same happend when I tried suspend to RAM. 

Graphics switching worked. Laptop consumed much less power (13 - 20 W, instead of ~40W). Most time restarting X worked, but some times it stucked at tty.

After all, I thing opensource drivers + switcheroo are now better choise than AMD's drivers.

---

### Post by belltown on 2011-05-16
I'm running Ubuntu 11.04 on an ENVY 14 laptop with an integrated Intel HD graphics card and a discrete (switchable) ATI HD5650 graphics card. I've been able to get the ATI Catalyst 11.5 driver somewhat working using the instructions in [http://ubuntuforums.org/showthread.php?p=10805756](http://ubuntuforums.org/showthread.php?p=10805756) (see attachments).

The switchable graphics seems to work although it requires a system reboot when changing graphics cards. The temperatures seem to be very low, however, on either graphics card, so it looks like the unused card is being de-powered as would be the case using vgaswitcheroo. No blacklisting was necessary here.

There are a few problems. For example, suspend hangs up when on the ATI driver, and I had to disable hardware acceleration in Flash to get Flash videos to play on the ATI card. I'm not using Unity, just the Ubuntu Classic desktop, so I don't know how well that works.

---

### Post by depeha on 2011-05-17
@ belltown: Is ATi visibly faster than Intel on ubuntu? And can you access ttys?

---

### Post by belltown on 2011-05-17
> **depeha said:**
> @ belltown: Is ATi visibly faster than Intel on ubuntu? And can you access ttys?

I haven't noticed any visible performance increase when using the ATI driver, although I haven't been using anything that requires 3D graphics. I'm just trying to keep things simple right now as I'm fairly new to Linux and just want to get a basic system I can start working with. I'm running the Gnome Classic desktop without any desktop effects and haven't started playing with any 3D games yet.

No, the TTYs don't work on the ATI driver. When I press CTRL+ALT+Fn I sometimes get a screen with some Linux console messages that appears for a few seconds then bounces me back to the login screen. Sometimes the computer locks up completely and I have to do a hard reset. The TTYs work fine on the Intel integrated driver.

Also, suspend does not work on the ATI driver. The system hangs.

At least I was able to install the driver without any problems and I have noticed that my temps are much cooler than when I was running on the integrated driver without having powered down the ATI card with vgaswitcheroo when I had the Radeon driver installed.

I'm generally running on the Intel driver now, which suits my needs at the moment. It looks like it will take a bit more work for ATI to work out the bugs in their driver. At least I had no trouble installing the driver and my system boots up properly without any of the black screen problems I had with the radeon driver, and I don't have to blacklist anything or use any special boot commands to get the system to work.

---

### Post by dzolo on 2011-05-17
Hi,

Has anyone figured out, how to switch to external monitor with Catalyst 11.5?

On HP ENVY 14 part of application for managing display is missing. :-(

---

### Post by depeha on 2011-05-18
@dzolo: Look [_HERE_](http://wiki.cchtml.com/index.php?title=Ubuntu_Natty_Installation_Guide&oldid=6541). Maybe you'll have more luck than I had.
BTW with open source drivers dualbox (HDMI+VGA) works like a charm.

---

### Post by dzolo on 2011-05-18
> **depeha said:**
> @dzolo: Look [_HERE_](http://wiki.cchtml.com/index.php?title=Ubuntu_Natty_Installation_Guide&oldid=6541). Maybe you'll have more luck than I had.
BTW with open source drivers dualbox (HDMI+VGA) works like a charm.

I am currently running on open source drivers, external monitor works fine, but there is many issues during boot and suspend, which Catalyst solve. I tried install drivers step by step using wiki, but still cannot get external monitor working. So I am stuck on open source drivers for now.

---

### Post by depeha on 2011-05-19
What issues?

Sometimes when my laptop is booting it just stuck at black screen, and I have to press ctrl+alt+delete to restart, but that happens maybe once a week. That's only problem I have during boot.
Suspend to RAM works great for me. (I use suspend a lot - like 10-20x a day...)

---

### Post by ultimatebuster on 2011-06-11
I get booting issues as well, if I plug in the external monitor while booting. I have to hardreset it.

---

### Post by depeha on 2011-06-11
**ultimatebuster**:
try this:

```
sudo echo blacklist \radeon > /etc/modprobe.d/radeon.conf
```

I have installed Arch Linux (2.6.38) few days ago, and I must say, it's great. Kwin performance on intel graphic is much better than on kubuntu, no problems during boot (no hangs).

BTW, if you blacklist radeon, you have to do
```
sudo modprobe radeon
```
before
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
to turn off ATi chip.

(remember, switcheroo works only with open source drivers, and believe me, they can do the job.)

---

### Post by ultimatebuster on 2011-06-11
I'm using the ATI graphics card driver, and using their switching

---

### Post by depeha on 2011-06-11
I still recommend opensource drivers... No problems anymore, battery life is great, hdmi works well... In my opinion, AMD's drivers bring problems (as I described [_here_](http://ubuntuforums.org/showpost.php?p=10813845&postcount=35)), without visible performance increase.

---

### Post by ultimatebuster on 2011-06-18
Will try when I install ubuntu onto my other HDD tonight. Anyway to uninstall unity?

---

### Post by ultimatebuster on 2011-06-18
depeha:

Your commands don't work

Though this thread is extra helpful: [http://ubuntuforums.org/showthread.php?t=1744188](http://ubuntuforums.org/showthread.php?t=1744188)

---

### Post by ultimatebuster on 2011-06-18
Alright so it's kind of working right now.

This is what I did:

```
First. I had to put this into /etc/rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe radeon
chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
exit 0
```

That turns off the ATI card at startup.

Then. In the file /etc/modprobe.d/blacklist.conf
add the line **blacklist radeon** at the end. This blacklists the ATI card, which will prevent a startup kernel crash.

Lastly, in terminal, run:

```
sudo gedit /etc/init.d/DisOn
```

Then paste:

```
#!/bin/sh 
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
exit 0
```

into the document and save it.
Back in console, enter these commands:

```
sudo chmod +x /etc/init.d/DisOn 
sudo ln -s /etc/init.d/DisOn /etc/rc0.d/K10DisOn
sudo ln -s /etc/init.d/DisOn /etc/rc6.d/K10DisOn
```

This is to solve a shutdown/reboot issue.

However. This is not a perfect solution. Dual display still doesn't work. The secondary display still jitters, flickering, tearing, whatever you want to call it, making it very blurry (video capture makes it look fine, but in real life it looks jittery and blurry). Under ATI card it works fine, though the ATI card is filled with problems.

---

### Post by riyasmp on 2011-06-27
Hi guys

Thanks a lot for these posts. I have been using ubuntu 10.10 so far with intel+ATI combination. my problem is the computer heats up so quikly that i have to switch back to windows which is a shame.

I have got 11.04 one my 2nd drive and it has got more problems than any releases. some times it hangs while booting and i have to switch off and switch on the computer again which is disappointing.

I know that developments are goin on in this field. can any one help me so that i can customise my laptop the following way

1) any fix to stop the fan going at high speed while using latop?
2)I am happy to use the open source driver. how can i make the switching possible. the codes given here [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics) never switches my graphics card.

I am happy to give any more info if u like

regards

---

### Post by ultimatebuster on 2011-06-27
Don't use unity, and use my method above your post. That should make it usable. 

I have problems, though, most of them can be listed here:

[http://thekks.net/1293](http://thekks.net/1293) (scroll to ubuntu)

---

### Post by ultimatebuster on 2011-06-29
Good news! I'm able to get the ATI drivers working, but only with Kernel 2.6.39-2+. 

Get that, and use the following command for **64bit systems and ubuntu 11.04**. you can change the commands below for different configurations

These are to patch the kernel. For more detail, visit this page: [http://askubuntu.com/questions/50687/fglrx-catalyst-11-6-is-it-compatible-with-kernel-2-6-39](http://askubuntu.com/questions/50687/fglrx-catalyst-11-6-is-it-compatible-with-kernel-2-6-39)

The only issue right now is secondary display flickering and tearing.

```
sudo apt-get install -y build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install -y ia32-libs
cd ~; mkdir catalyst11.6; cd catalyst11.6
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-6-x86.x86_64.run
wget http://www.mindwerks.net/wp-content/uploads/2011/03/2.6.39_bkl.patch
wget http://www.mindwerks.net/wp-content/uploads/2011/03/no_bkl.patch
chmod +x ati-driver-installer-11-6-x86.x86_64.run
sh ./ati-driver-installer-11-6-x86.x86_64.run --extract ati
cd ati; for i in ../*.patch; do patch -p1 < $i; done
./ati-installer.sh 8.861 --buildpkg Ubuntu/natty
cd ..
rm -rf ati
sudo dpkg -i fglrx*.deb
sudo reboot
```

---

### Post by aeronutt on 2011-06-29
> **ultimatebuster said:**
> Good news! I'm able to get the ATI drivers working, but only with Kernel 2.6.39-3

Get that, and use the following command for 64bit systems.

These are to patch the kernel. For more detail, visit this page: [http://askubuntu.com/questions/50687/fglrx-catalyst-11-6-is-it-compatible-with-kernel-2-6-39](http://askubuntu.com/questions/50687/fglrx-catalyst-11-6-is-it-compatible-with-kernel-2-6-39)

The only issue right now is secondary display flickering and tearing.

```
sudo apt-get install -y build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install -y ia32-libs
cd ~; mkdir catalyst11.6; cd catalyst11.6
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-6-x86.x86_64.run
wget http://www.mindwerks.net/wp-content/uploads/2011/03/2.6.39_bkl.patch
wget http://www.mindwerks.net/wp-content/uploads/2011/03/no_bkl.patch
chmod +x ati-driver-installer-11-6-x86.x86_64.run
sh ./ati-driver-installer-11-6-x86.x86_64.run --extract ati
cd ati; for i in ../*.patch; do patch -p1 < $i; done
./ati-installer.sh 8.861 --buildpkg Ubuntu/natty
cd ..
rm -rf ati
sudo dpkg -i fglrx*.deb
sudo reboot
```

What CPU and graphics hardware do you have?

---

### Post by ultimatebuster on 2011-06-29
I have ATI HD5650 and Intel i5 m430. Lenovo Y460.

---

### Post by ultimatebuster on 2011-07-15
Is there anyone experiencing memory leak like issues after patching the kernel?

Symptom: [http://askubuntu.com/questions/51785/swap-shoots-to-100-after-a-couple-of-hours-of-usage](http://askubuntu.com/questions/51785/swap-shoots-to-100-after-a-couple-of-hours-of-usage)

---

### Post by Paulo Carvalho on 2011-08-30
Just to let you know, my laptop , HP same graphics card and inter card, same processor.
i have my ati driver working beautifully.
Will post how to if you need.

---

### Post by LinoLinux on 2011-08-31
Hey Paulo,

I have an hp laptop with switchable graphics (intel hd3000 and ati 6470m) with natty 64bit and I tried, with no luck, to use latest catalyst. I can install them but as I reboot I only get a distort image of logon screen. I can access tty but couldn't get things to work. Did you have similar issues? How did you solve them?
Thanks for your help

---

### Post by bcschmerker on 2011-09-14
I ran into an issue during an attempted video upgrade:  On my hybrid Everex® running Ubuntu® 10.04.3-LTS-bis (LinUX Kernel 2.6.35), I found that the current Gigabyte® MA78GM-S2HP mobo (Advance Micro Devices® Athlon 64 x2 5600+, 780G/SB210 chipset, Radeon® HD 3200 planar graphics/RV) *cannot* run an Asus® EAH6850DC/2DIS/1GD5 (Advance Micro Devices® RV970 Barts Pro GPU) properly in power-on self test, even with the planar GPU disabled.  The last stable BIOS available for my mobo from Gigabyte Technology predated the official release of the entire AMD® Radeon® HD 6000 series.  It therefore looks as though I will need an ATi® R600- or R700-based video display adapter.

The revised list of VDA candidates now includes the ATi® All-in-Wonder® HD (RV635 GPU), Radeon HD 3850 (RV670 GPU), and Radeon HD 4850 (RV770 Pro GPU); Gigabyte® did offer one HD 4850 variant (Gigabyte® GV-R485-512H-B) that will fit my rig with the Creative Laboratories® SB0350 audio adapter in the end slot, with one legacy PCI slot betwixt them (to allow for inlet of cooling air).

Of the three ATi® video card classes shown above, which one runs best with the X.org drivers (packages: xserver-xorg-ati, xserver-xorg-radeon, xserver-xorg-radeonhd)? the Advance Micro Devices® Catalyst™ Control Center (package: fglrx-amdcccle)?  Can any be paralleled with my planar Radeon HD 3200?

---

### Post by riyasmp on 2011-10-09
hi could you please let us know the steps to make the switchable graphics work under linux.

i have ati/intel comination on hp paviolion laptop

regards

---

### Post by riyasmp on 2011-10-09
> **Paulo Carvalho said:**
> Just to let you know, my laptop , HP same graphics card and inter card, same processor.
i have my ati driver working beautifully.
Will post how to if you need.

hi

could you just post the steps to make switch able graphics work under ubuntu. i have got intel /ATI combination on my hp pavilion laptop.

with regards

---

### Post by Alexislavie on 2012-02-23
Check this post : [ http://ubuntuforums.org/showthread.php?p=11712748]("http://ubuntuforums.org/showthread.php?p=11712748")

---

