---
title: "Toshiba l355-s7915"
date: 2009-09-26
forum: Hardware
---

### Post by sa-mejia on 2009-09-26
I am writing this to let people know that this computer, Toshiba L355-S7915 has a few problems with Ubuntu, and to also see if there is anybody out there that has any ideas of how to solve them.

The most annoying problem: by some weird reason, the wireless works very badly.  It is highly unreliable and very slow.  When I use it in windows, it is significantly faster.

Second annoying problem: desktop screen resolution varies everytime one reboots.  Sometimes it shows a good sized resolution, others a low quality one.  I've posted this problem here: [http://ubuntuforums.org/showthread.php?t=1246588&highlight=toshiba+l355](http://ubuntuforums.org/showthread.php?t=1246588&highlight=toshiba+l355), but so far nobody has been of help.

Third problem: Once the fan turns on, it will never turn off.

Santiago.

---

### Post by IcarusR on 2009-09-28
As far as wireless is concerned what card is it, what chipset.

```
lspci
```

What version of Ubuntu are you running.
Try searching for the name of the card on google ie 'card name Ubuntu'

---

### Post by WhoFlungChow on 2009-10-28
> **sa-mejia said:**
> I am writing this to let people know that this computer, Toshiba L355-S7915 has a few problems with Ubuntu, and to also see if there is anybody out there that has any ideas of how to solve them.

The most annoying problem: by some weird reason, the wireless works very badly.  It is highly unreliable and very slow.  When I use it in windows, it is significantly faster.

Second annoying problem: desktop screen resolution varies everytime one reboots.  Sometimes it shows a good sized resolution, others a low quality one.  I've posted this problem here: [http://ubuntuforums.org/showthread.php?t=1246588&highlight=toshiba+l355](http://ubuntuforums.org/showthread.php?t=1246588&highlight=toshiba+l355), but so far nobody has been of help.

Third problem: Once the fan turns on, it will never turn off.

Santiago.


I have the exact same problems as you.  This laptop is horrible.

I don't even use the wireless anymore, because it's too much of a pain in the butt.  I use the ethernet at work, and don't even care to bother using wifi anywhere else because I have to go through some big procedure to get it to work each time I use a new wireless network (using temporary fix I found doing search for "rt8187b".)

---

### Post by BitJunkie on 2009-10-29
I have a Satellite L505. I haven't noticed any problems with the wireless, but I did have problems with the display and fans.

For the display issue, I changed my xorg.conf file as I described in this thread: [http://ubuntuforums.org/showthread.php?t=1256607](http://ubuntuforums.org/showthread.php?t=1256607)

For the fan issue, I had to add the following boot parameter to /boot/grub/menu.lst: acpi_osi="Linux"
Find the default boot entry and add it to the end. So the line will look similar to: kernel ...<some stuff blah blah>..... splash vga=791 acpi_osi="Linux"

Of course, back up xorg.conf and menu.lst first if you decide to change them.

---

### Post by zoonose on 2009-11-01
> This laptop is horrible.
> the wireless works very badly

I don't think it's the laptop-my wireless is fine, acpi_osi="Linux" (in lilo.conf for me) fixed the
fn-f7/f8 keys(I never noticed a problem w/the fan)- the only problem I had was getting suspend to work.
The display is weird (1.3/1 instead of 1.6) once in a while; restarting X fixes it when it happens.

Maybe this will help:

```
$:/sbin/lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Toshiba America Info Systems Device ff67
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Toshiba America Info Systems Device ff67
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: HDA Intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: i801_smbus
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff66
	Kernel driver in use: r8169
```

Some modules aren't shown 'cause I have them compiled in.

{EDIT}I should mention that I am using Slackware on this laptop, if it matters, although I don't
see any reason Ubuntu shouldn't work just as well.

---

### Post by sa-mejia on 2009-11-23
Thanks a lot BitKunkie. So far, it seems that your tip did the trick with the fan.

> **BitJunkie said:**
> For the fan issue, I had to add the following boot parameter to /boot/grub/menu.lst: acpi_osi="Linux"
Find the default boot entry and add it to the end. So the line will look similar to: kernel ...<some stuff blah blah>..... splash vga=791 acpi_osi="Linux"

Of course, back up menu.lst first if you decide to change it.

I just wanted to give others a little bit more of direction, in case they are a bit puzzled with their menu.lst.  When I opened my menu.lst, I did not find any line which had 

kernel ...<some stuff blah blah>..... splash vga=791 

I did found, however, several lines which had:

kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=32327973-938f-4ac5-ac01-ca05f6cbc367 ro quiet splash 

I was at first confused about why I had several lines with almost the same information.  After a while, I noticed that each line obeys to each linux kernel.  What solved the fan issue for me was to go to the first line of

kernel ...<some stuff blah blah>..... splash 

(which corresponds to my latest kernel, Ubuntu 9.04, kernel 2.6.28-16-generic) And added what appears in blue

kernel ...<some stuff blah blah>..... splash  [COLOR="Blue"]vga=791 acpi_osi="Linux"[/COLOR]

---

### Post by oldefoxx on 2009-12-05
I have the same notebook. bought recently.  Vista went sick-o on me, and apparently no way to correct the problem.  Moving on the Ubuntu 9.04 was a no-brainer.  Now have Windows 2000 Pro and XP Pro as clients under VirtualBox.  Much better, I assure you.

Interesting problem with display changing resolution.  That's what brought me here.  When it gets it wrong, I sometimes get a green box in the upper left corner with the word Unknown inside.  Then I have only two or three resolution choices.  I will have to try the cure above and see if it takes.

As to wireless, the L355-s7915 only sports an integrated 802.11g, and being a notebook, you cannot upgrade it directly.  But you have an ExpressCard34/54 slot on the left side, and I've found ExpressCard34's that support 802.11n.  That means higher speed and greater distance.  The cards vary in price, from about $70 up, but some recertified ones for about half that.  Just shop around online.

If you want to cut down the brilliance of the screen, you might be surprised to learn that this is not managed through System/Preferences' Display and Appearance settings, but through the Power Management settings.  Makes sense, after a fashion, but not what you would expect.  Also note that the Dim if Idle setting may result in what looks like screen flicker if you pause to think while typing.  Might want to turn that setting off, or make the Idle detection delay a bit long so as to avoid the flicker effect.

The mousepad may also require some adjustment.  There is something new out, which is a buttonless touchpad.  You effect a mouse press by pausing the movement of your finger on the pad.  Wait long enough, and it is as if you double click the left button.  The L355-s7915 defaults in software settings to a mix of the two modes.  You can change this in Systems/Preferences/Mouse.  Pay particular attention to the Touchpad tab, where you can turn this new mode off completely.

---

### Post by jeff913 on 2009-12-07
I have the same laptop.  With Ubuntu 9.04 loaded the wireless worked poorly if at all, but I have since installed 9.10 and the wireless works just fine.

---

### Post by oldefoxx on 2009-12-18
I'm currently running another thread on Wireless Networking with a L355-S7915, and will stay at it until I feel the issue has been fully addressed.  In my present view, Ubuntu is not adequately dealing with the whole issue of going Wireless, but maybe we can dredge something out.

The Wireless Network Controller in the L355-S7915 is a RLT8187B from Realtek.  They also made the wired chipset in the same machine.  Reports are that you could add support to versions of Ubuntu before 9.04. but 9.04 and beyond support the wireless controller natively.  I guess the 9.04 version was still experimental to some extent, at least in the Beta release.

The thing is, the Network Manager employed in Ubuntu is somewhat lacking in some features, and may prove a bit inadequate for certain tasks.  But that does not preclude a command line approach, which is the area I am beginning to explore now.  For instance, some useful commands that a Terminal user can employ are lspci, lsusb, lshw, iwconfig, ifconfig, dhclient, and others.  There are also discussions that can be found on what table entries can be made or modified to add more impact to the wireless experiance.

I think the idea with Ubuntu is just to help you get your notebook to connect to your home network, and some reports are that it is not doing too badly at this.  But that might leave the question of how to also connect at work, to another's private network (with their permission), or to a public access point where available, like at your friendly coffee shop.

---

### Post by oldefoxx on 2009-12-19
About that changing resolution on reboots problem.  I found something interesting that seems to trigger it.  For some reason, the notebook seems to think an external monitor is plugged in, and wants to go to the dual monitor mode.  This might produce a small green box in the upper leftx corner, maybe with a yellow sidebox.  The software has not been told about a second monitor, and for some reason assumes that the highest resolution supported is only 1024x768, or 800x600, or perhaps only only 640x480.  This is the setting that the notebook's built-in screen then displays at, and you cannot set it higher.  It has to do with the other settings in display which somehow got impacted.  If you can find and fix it there, then you do not have to reboot or stop and restart the X-session.  The green and possible yellow boxes seem to represent monitors added to the panel.  I agree, something seems offbase here and out of whack, but this seems to point more to where the problem is and how to deal with it on a limited basis.

---

### Post by oldefoxx on 2009-12-19
I stand corrected, in part anyway. The notebook does think that there are two monitors attached, and the screen size reduction is caused by the fact that the box for selecting mirror screens is set, but the unknown (and unattached) monitor then determines the resolution for both, since it is being deemed to have a lower range of resolutions.  Uncheck that and you can straighten it out, but then it wants to make a configuration change, and follows that with a suggestion that you log out then back in for the change to take effect. The question of why or how these boxes are getting checked during bootup remains unanswered.

As to the green box or green and yellow boxes being displayed, that is because the box for showing displays in panel has also gotten checked.  The green box represents the built-in display, and the yellow (which is shown as being much smaller) represents the supposed external monitor.

Rather odd behavior, and somehow hardware specific I guess.

The matter of Wireless options and performance is subject to further research.  There are many drivers out there, as development has gone through a number of generations of development and debugging now.  Some approaches seem most promising, and only a limited range are being picked up for inclusion in the Linux kernel.  So with wireless, you now have several unknowns to deal with to even begin to address this matter.

(1)  What manner of Wireless Hardware in involved?  Here it seems to be the RTL8187B from Realtek, which employs a USB to LAN methology, and that is not always a best performer due to the way that USB works.  It is however rated as being more or less 802.11g compliant, which isn't bad, but still subject to how well it actually works and what all it can do.

(2)  Does it require a firmware upgrade?  This is eluding to the fact that some hardware devices have their code stored in reprogrammable medium, called firmware, and as efforts to get the best and max out of the hardware progresses, it sometimes requires that the stored program in the firmware be replaced with something newer.  Firmware is very specific to hardware, and also is a big factor in what drivers will then work with both.

(3)  Is there a driver for a given operating system that will work properly and well with the specific hardware and firmware that is involved? Where Windows is concerned, the answer is probably yes, because this is the primary market for such devices.  With Linux, it is far less certain, as many equipment manufacturers don't see the Linux community as worth going after.  But the Linux community itself is getting stronger, and bringing forth many of its own solutions, but these are more limited in terms of what is covered than what is available to the Windows world.

So what it comes down to is this:  Right hardware, right firmware, right driver, for use with a given operating system.  Or, the other way around:  Right operating system for use with given hardware, still requiring right firmware if need be.

What tends to make the first choice harder is that it can be very hard to find out what type of hardware is part of some device, and without knowing that, how do you determine if there is a driver for it, and if there appears to be a driver that should work, is there anything special required as well?  You know, firmware upgrade maybe, or an updated Linux kernel that adds new capabilities as well.  Even then, until you try, you may not have an answer to your question as to whether it will work for you.  And though there might be new firmware, how would that impact your use of the device if you decide to revert to Windows?  After all, maybe its driver works just fine with the existing firmware in the device.

It's sometimes having to deal with matters like this that make many people feel and say that Linux is not ready for the big market yet.  But that misses a critical point.  You buy a new PC that comes with Windows installed, all such problems have already been solved for you.

If manufacturers sold PCs with Linux already on them, they would be just as easy to get along with as Windows is.  You get to a stage where you want more out of Windows than came with it, you begin to see that these problems are common to all operating systems to some degree.  That is when you find out how much real community support there is for what interests you now/

And Linux has a big world-wide community, although much if it is divided up into different camps focused on different Linux distributions.  But hey, look how many flavors of Windows is out there now.  And tracking the Windows community online, you find many people with questions but very few answers posted in response.  That is partly because people that have some of the answers are invited to cluster at some watering hole so that the site owner can get others to subscribe to his pool of willing experts in order to try and get answers.

I'm just explaining that I've now learned that it might take some doing to get the best out of Wireless, and if that seems like too much trouble, I'm sorry.  But don't blame the Linux world for this, it just takes a lot before everything goes exactly right.  Besides, learning can be fun if you look at it right.  Now you will be able to do something most others can't or won't get involved with.  That ought to be worth something, even if it is only a bit of personal pride.

---

### Post by zoonose on 2009-12-22
Something that may be worth trying: lately I've been using kernel modesetting instead of specifying the vga framebuffer resolution; since then, I've not had the 1152x864 resolution come up.

---

### Post by oldefoxx on 2009-12-23
Even easier, I just opened System/Preferences/Display and unchecked to Mirror Screens and the other box, and did not bother with a resolution change.  It then corrected itself without even a log out and log in step.

My guess is that it still thinks an external monitor is attached, at the lower resolution setting, but now leaves my desktop monitor state alone and everything is working fine, even after many shutdowns and restarts.

---

### Post by oldefoxx on 2009-12-26
I got my Toshiba notebook refurbished, which means no real paperwork, such as manuals, included.  But there was a Quick Start guide, and I was taking another look at it today.  I finally noted that under the leftmost front green light there is a little slide switch, and that moving it to the left turns the yellow light off, and to the right turns it back on.  The Quick Start guide identified this as the off/on switch for the wireless adapter's antenna.  The yellow light indicates when it is set to On.  Something to note.

Not too many details about the notebook otherwise.  However, documentation, including specifications and a manual, can be had for download online.  Just use a search engine to find it.

I'm still not to the point of getting my internal wireless-g adapter working.  Seems a mixed bag - works with no problem for some, but not for others.  Is it possible that a different adapter was used in some notebooks and not all work or were adequately tested?  Hard to say.  When it comes to finding problems, the most important thing I learned over my long career was something we use to call Easter-egging.  Now that might not sound like much, and some might say that to find the unknown, it helps to search where you haven't searched before, and that is partly true.

But the real secret, or let's just say method, is to determine from what evidence is evident, what seems to relate to the problem at hand.  It could be something that is just now showing up.  Or it could be something that should be there but isn't, for some unexplained reason.

Once you have something to go by, the next step is to try and make some change, and see what effect it has on whatever it is that you see, or should see and don't.  Often, this should not be a small change, but a rather large one.  If your indicator is effected, then the problem must be somewhere in or related to whatever you changed.  If it stays the same, then that indication must be tied to what you haven't changed yet.  So now you should have some idea of where to shift your focus to. 

Programmers sometimes use similar techniques when sorting or searching through data.  Because they have the choice of dividing each sequence of choices by two, these methods go by the names of binary sort and binary search.  They are effective and fast, but depend on the information being in some sequence already for greatest effectiveness.

So, in my case, I have a working notebook but I cannot connect to anything with the built-in wireless, but I have no wireless network to test against.
My purchase of a wireless router resolves that issue.  Found a nice reconditioned wireless-N one at [www.geeks.com](www.geeks.com) for just $19.95.  A few others were cheaper.  But if that doesn't solve the problem, then I am trapped if it still doesn't work.  How do I circumvent a possible problem with the internal adapter or driver?  That is the reason I also shopped for and bought an ExpressCard/34 wireless-N card there, also at the low price of $19.95.  I could have bought Wireless-G for less, and there were other choices at the same price, but going by customer reviews found elsewhere on the internet, I think I made a couple of wise choices.  By going wireless-N, I get higher speeds and more distance, so I will likely be more pleased with the final results.

I did have one other option to consider.  Instead of a ExpressCard, I could have opt for a USB to Wireless-N device, at close to the same price.  That would have allowed one other option:  Plug that device into a Desktop by one of its USB ports, and you can tested everything short of the notebook separately.  But I decided not to do that, because USB ports just stick out, and to hang some device off one, especially a notebook, means a problem just keeping it in place and out of the way.  I decided that a USB extended device just was not part of my long range plans, so I dropped that idea.

Give me the week for these items to ship, and a chance to try them out, and I may have more to report later.

---

### Post by ross76 on 2010-06-22
no problems for me with wireless or display. as for the fan, restarting my PC just once does the trick.

---

