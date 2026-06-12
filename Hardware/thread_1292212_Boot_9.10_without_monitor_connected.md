---
title: "Boot 9.10 without monitor connected"
date: 2009-10-15
forum: Hardware
---

### Post by marleaux on 2009-10-15
Hi all,

I have a self made media pc with an onboard intel graphics card. Because I was not able to mirror the screen (1280x1024) to a TV with automatic rescaling, I bought a small device that can do this for me. Unfortunately the VGA connector of it is not fully wired. This means that the system thinks, that no monitor is connected.
If I plug that thing in after gnome has booted completely, everything works fine. But - of course - I want it to be connected all the time.

So I do need to be able to start the xserver and gnome without automatically search for a monitor.

I tried some tips I found here but I had no success.
What I tried:
create a xorg.conf that works with X in Ubuntu 9.10
Remove all but the one resolution I need.
Add Option "ConnectedMonitor" "CRT"

Linux will not boot and is not accessable by vnc. Even ping does not response.

Do you have an idea how I can tell the xserver to do what i want without caring about connected devices?

[edit:]
After booting the computer I can see GRUB on both screens. The system freezes with with a blanc screen (no VGA signal) after GRUB loads linux.


Best regards,
marleaux

---

### Post by Giblet5 on 2009-10-15
> **marleaux said:**
> Hi all,

I have a self made media pc with an onboard intel graphics card. Because I was not able to mirror the screen (1280x1024) to a TV with automatic rescaling, I bought a small device that can do this for me. Unfortunately the VGA connector of it is not fully wired. This means that the system thinks, that no monitor is connected.
If I plug that thing in after gnome has booted completely, everything works fine. But - of course - I want it to be connected all the time.

So I do need to be able to start the xserver and gnome without automatically search for a monitor.

I tried some tips I found here but I had no success.
What I tried:
create a xorg.conf that works with X in Ubuntu 9.10
Remove all but the one resolution I need.
Add Option "ConnectedMonitor" "CRT"

Linux will not boot and is not accessable by vnc. Even ping does not response.

Do you have an idea how I can tell the xserver to do what i want without caring about connected devices?

Best regards,
marleaux

It sounds like the PC is stopping during POST (self-test). Not ubuntu related...

Try hooking up a monitor and entering BIOS setup.

There should be an option like "Halt on Error" and some optional error types. It's probably set to "ALL". Set it to "None". Save the changes. Power off. Switch the monitor cables around. Try again.

---

### Post by marleaux on 2009-10-15
Hi Giblet5,

thanks for your quick answer - good idea. But the computer itself does not care about the monitor. I hibernated the system, plugged off the power plug for 20 seconds and switched it on again. That works fine. I'm back on my gnome desktop after 25 seconds with 1280x1024 on the monitor and a scaled copy on the TV.

I'm still sure that ubuntu stops because it can not find a monitor.

Any other ideas?

marleaux

p.s.: I changed "halt on" to "no errors" anyway.

---

### Post by Giblet5 on 2009-10-15
> **marleaux said:**
> Hi Giblet5,

thanks for your quick answer - good idea. But the computer itself does not care about the monitor. I hibernated the system, plugged off the power plug for 20 seconds and switched it on again. That works fine. I'm back on my gnome desktop after 25 seconds with 1280x1024 on the monitor and a scaled copy on the TV.

I'm still sure that ubuntu stops because it can not find a monitor.

Any other ideas?

marleaux

p.s.: I changed "halt on" to "no errors" anyway.

Nope. Sorry.

I had an HTPC but replaced it with a PS3 that has a 1TB drive hanging off its SATA interface. I have mediatomb installed on my Samba server and all of the 50+G of music is available right off the PS3's attractive menu.

ie, I cheated.

---

### Post by Jliax on 2009-11-01
Any luck one this one? Got the same problem here. Xorg.conf is set to VESA.

---

### Post by MrTAToad on 2009-11-01
I'm having the same trouble with 9.10 (after upgrading from 9.04).

For some reason, without a monitor, 9.10 wont even boot to the boot loader (although with 9.04 it was all fine) - POST check, is, as far as I know, all okay (there is no options to stop on an error).

---

### Post by Ralph Hoflich on 2009-11-03
Yes, I'm having this problem too. With 9.04 it was no problem, after an online upgrade, after the reboot, it doesn't work. I have 2 graphics cards - a built-in motherboard one, and a PCI one. If I connect a monitor to the motherboard connector, it starts up fine! So strange. I wonder if it's a grub issue, or a lower-level kernel issue?

---

### Post by BooDaddy on 2009-11-03
Im having the same issue.  I have an older GX260 that will not boot without the monitor plugged in.  I cant ping my machine after I boot without a monitor.  If I plug a monitor in, and boot, I have no problems.

Now, heres whats odd.  If I boot without monitor, if I hook up a monitor after it has powered on... nothing displays. 

There is nothing in my bios set to halt on video.. only keyboard which has been disabled.

Anybody come up with a solution?

---

### Post by Ralph Hoflich on 2009-11-11
I'm still at a loss with this one - I can't seem to find any logging in /var/log when the system doesn't boot - my feelings are that maybe it's GRUB or something low level? The funny thing is, when I boot without a monitor, then it stays there and doesn't continue, if I connect the monitor then, I still can't see anything on the screen! So trouble-shooting this is very difficult. Anybody have any ideas how I can trouble-shoot this?

Would be very keen to reboot the machine without having to bring my monitor down to the PC...

---

### Post by marleaux on 2009-11-17
Hi.

I solved it. The problem - in my case - is that I do have an intel graphic card (onboard). The Intel dirver has a bug. The man pages speak about "DDC", in the driver source you can see, that the entry is called "NoDDC". But playing around with NoDDC had no effect. :-(

I needed to add** i915.modest=0** to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub.

And I added xrandr settings to [B]/etc/X11/Xsession.d/45custom_xrandr-settings

[/B]Now I can boot with and without monitor and I allways have the right resolution via VNC or on the small 5" display. :-) Why the hell is this so complicated? :mad:

best regards

---

### Post by wawacito on 2009-12-23
I am having same problem.  I cannot boot without a monitor.  The PC completely freezes because when i hit caps lock or number lock no lights turn on and when i plug the monitor up after that i get nothing but a black screen.  I have to shut it down hard (hold down the power button) and then power back up. 

I think its after the grub selection.  When I shut it down hard - the next time it boots it goes into this menu "kernel ... something or other" is the first choice.  "kernel ... something + safe mode" is the second choice.  The third and fourth choices are memory tests.  (i can see this because i reattached the monitor).

So then i do another hard shutdown.  Pull the monitor cable.  Then I power back up.  I see the hard drive flashing flashing ... and then stop.  I'm (blindly) guessing that its at the Grub selection menu again.  So I hit enter.  Sure enough the hard drive light goes flashing flashing ... then stops.  At that point I'm frozen again (no caps lock or number lock and black screen when i reconnect the monitor).


I tried the xorg.conf thing.  Didn't work.

I'm trying to do this last suggestion by marleaux.  Someone please help me.

I go "cd /etc/default/grub" it says "no such directory"
So I go "cd /etc/default/"  apparently "grub" is a file.
I go "sudo pico grub" and i see a file open up.
i find the line that says "GRUB_CMDLINE_LINUX_DEFAULT".
The full line reads:
   GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash"
I put a # in front of that line.
Then i enter
   GRUB_CMDLINE_LINUX_DEFAULT = "i915.modest=0"

tried reboot with no monitor - same thing.  Frozen.

my computer is a IBM thinkcentre S50 8183-GNU and it has intel integrated video.  I went to Lenovo website and obtained latest BIOS update.  There is no option in the BIOS for "halt on" anything.  I am running 9.10 Karmic.  

Somebody please help?
And when providing a solution please be more specific.  When marleaux wrote "And I added xrandr settings to /etc/X11/Xsession.d/45custom_xrandr-settings" i thought ... "i dont have a 45custom_xrandr-settings" file in that directory and even if i did i don't know how to "add xrandr settings".

---

### Post by wawacito on 2009-12-24
more details. The same problem happens to me with Ubuntu 9.04.  I just reloaded the system with ubuntu 9.04 - same thing.  What could be wrong?

---

### Post by jeffas on 2010-01-30
I don't know if this is relevant to your problem, but I had this when trying to boot with just an HDMI TV connected. It needed either a VGA or DVI monitor connected.
[http://art.ubuntuforums.org/showthread.php?p=8693251](http://art.ubuntuforums.org/showthread.php?p=8693251)
The solution that worked for me was removing the 'splash' option from the GRUB_CMDLINE_LINUX_DEFAULT line; but it seems you did that anyway.
You did run update-grub didn't you? (As described at the top of /etc/default/grub.)

---

### Post by kc9fgq on 2010-02-07
I found that it works if you open /etc/default/grub and edit the line that says:

GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash"

to say:

GRUB_CMDLINE_LINUX_DEFAULT = "quiet"

I am running 9.10 on an Intel Atom as a file and web server, so I want to be able to tuck this computer away in a closet with only power and network running to it, now it starts perfectly without a monitor attached.

---

### Post by jasa66 on 2010-04-10
Any news here? 

I have same problem with 9.10 - won't boot up without display.  Yesterday I upgraded to 9.10 and once again this headless boot-up problem occurred. I got workaround for 9.04 with VESA driver trick, but now I have used all tricks I have read here.

I have MSI mainboard with integrated graphics card and most likely I have Intel chipset, but earlier mentioned trick did not work for me. 

GRUB 2 upgraded and tricks done also there - no cure.

With display no problems to boot up, but without - always stuck and cannot connect to VNC, putty or other way. Long press of power button is only way to get out.

these are already used:
GRUB_CMDLINE_LINUX_DEFAULT = "quiet"
915.modest=0 to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub

Next tip - please?

--JaSa

---

### Post by g.p.1985 on 2010-04-17
**Re: Boot 9.10 without monitor connected** 			
 			 			 		   		 		 		I found that it  works if you open /etc/default/grub and edit the line that says:

GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash"

to say:

GRUB_CMDLINE_LINUX_DEFAULT = "quiet"

I am running 9.10 on an Intel Atom as a file and web server, so I want  to be able to tuck this computer away in a closet with only power and  network running to it, now it starts perfectly without a monitor  attached.


I have a PC with Intel Atom I  followed your instructions but when I do sudo update-grub gives me this  error

/ Etc / default / grub: 9:  GRUB_CMDLINE_LINUX_DEFAULT: not found

What can be wrong?


someone help me thanks

---

### Post by Tass on 2010-04-18
I've got the same problem in 10.04 Beta 2.  It wasn't an issue in 9.04. I know the PC boots up & Ubuntu starts loading because I can ping it after about 20 second - I can't VNC or Remote Desktop.

I will try the various suggestions here and post my progress.

---

### Post by webaake on 2010-05-05
There's a typo above with kernel line! It should be i915.**modeset**=0.

---

### Post by Gh0styuk on 2010-05-08
I have tryed all of the tips in this topic, The only thing i got stuck on is the 45 custom thing not sure how to do that.

Regards
Gh0sty

---

### Post by webaake on 2010-05-08
I've now tried the modeset hack to the kernel line and the xrandr in xession.d but to no avail. Seems that there's no way to boot a really headless server into X without a monitor connected, with linux and intel 945g/gma950 graphics. Earlier hacks in xorg.conf "option NoDDC" and the like aren't working either. Whata bummer!

---

### Post by smurfix on 2010-06-19
> **g.p.1985 said:**
> 
GRUB_CMDLINE_LINUX_DEFAULT = "quiet"


Lose the spaces.

---

### Post by quicky2g on 2012-10-05
I'm using Debian Squeeze (6.0.6). I have a basic install with a few applications and wanted to boot without a monitor. I've tried all kinds of tutorials mentioning modification to /etc/inittab and executing "startx" in either /home/<user>/.profile or some other file...nothing worked until now. My default /etc/default/grub file had this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="**quiet**"
```I changed it to:
```
GRUB_CMDLINE_LINUX_DEFAULT="**i915.modeset=0**"
```Then I ran this command as the root user:
```
update-grub
```If you're an Ubuntu user you should run:
```
sudo update-grub
```I installed Teamviewer and set it to auto run. Now I can boot the PC without a monitor, keyboard, or mouse and connect to it through Teamviewer! AWESOME!!!

---

### Post by quicky2g on 2012-10-18
I found out i915 only works for Intel cards. I have a computer with an old radeon card. I had to use this line instead:

```
GRUB_CMDLINE_LINUX_DEFAULT="**radeon.modeset=0**"
```I'm guessing this should work for Nvidia cards but not sure:

```
GRUB_CMDLINE_LINUX_DEFAULT="**nouveau.modeset=0**"
```

---

