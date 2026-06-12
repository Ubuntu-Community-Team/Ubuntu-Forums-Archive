---
title: "Just installed Ubuntu and the internal keyboard doesn't work"
date: 2014-08-21
forum: Hardware
---

### Post by sang-gyegmx.de on 2014-08-21
Hello,

I installed ubuntu on an ASUS Eee PC and now the internal keyboard doesn't work at all. I chose to install only Ubuntu over a previous Windows 7 installation. Opted for the automatic partitioning option, did not chose encrypt home directory.  I choose US keyboard, although this machine is from Canada, but if it was just a layout issue, some keys should work. Am I missing a driver? 

Any suggestions? While I am waiting for replies, I will reinstall .... 

I am adding additional observations that I made while trying to find a solution, which I haven't (Thursday August 21, 5:09 Atlantic)

The keyboard & touchpad work fine during the installation.
The keyboard & touchpad work fine when just 'trying Ubuntu' from the USB drive
The keyboard does not work in the desktop once Ubuntu is installed.
The failure of the keyboard to respond is independent from the installation parameters (with/without LVM, 3rd party sw, automatic updates)
A wireless keyboard connected after the installation doesn't work, either, but the mouse does (as does the touchpad).
NOTE: The keycombination that brings me into the terminal DOES work!!!! [that doesn't seem to make any sense to me]

During startup a few error/debug messages appear:
[13.136949] gma500 0000:00:02.0: GPU: Power management timed out.
[13.640528] gma500 0000:00:02.0: trying to get vblank count for disabled pipe
[13.642461] gma500 0000:00:02.0: trying to get vblank count for disabled pipe

but it seems that #1 has to do with the graphics card and the others don't seem to connected to a particular problem

---

### Post by Bashing-om on 2014-08-21
sang-gyegmx.de; Hello ;

We often see this as a result of what bios hands off to the ubuntu kernel. Maybe look in your bios for settings similar to "usb-legacy" and/or "plug and play". Alter the settings in bios and see if that works. This is "assuming" that the keyboard is functional up and until the ubuntu operating system is loaded ( no workie then bios/kernel are not communicating properly).

Else, if you can lay your hands on an old ps/2 keyboard, might help in the troubleshooting process.

[INDENT][INDENT]a failure to communicate ?
[/INDENT][/INDENT]

---

### Post by sang-gyegmx.de on 2014-08-21
woh - Thanks Bashing-OM,

that was quick. I'm reinstalling now without automatic update and 3rd party software ....

I tried a wireless mouse/keyboard combination before and the mouse works (as does the touchpad) but not the keyboard. During the installation (enter name, password, test keyboard screen) the keyboard works great ... afterwards it didn't . I'll check what happens the second time around and will go into the bios if the error still occurs. In any case, I will be back with you in a jiffy. Thanks again ...

---

### Post by Bashing-om on 2014-08-21
sang-gyegmx.de; Yepper;

That is a good thought too - not to install the 3rd party stuff and the updates at install time - as that keyboard is under the control of Xorg and it is possible that the 3rd party installed drivers are raising havoc with the keyboard. In this instance the proprietary drivers will not be installed.
These matters can of course be taken care of after the install.

[INDENT][INDENT]more than one path
[INDENT][INDENT][INDENT]to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sang-gyegmx.de on 2014-08-21
Ok. Bashing-OM,

here I am again. No change through changing the installation parameters. Still no keyboard.

I looked into the bios and I couldn't find any legacy-usb or plug-play settings .... I will look for them again, while I wait for your reply. 

But what I noticed is that when I start Ubuntu the following error message appears before Ubuntu starts:
[13.136949] gma500 0000:00:02.0: GPU: Power management timed out.
[13.640528] gma500 0000:00:02.0: trying to get vblank count for disabled pipe
[13.642461] gma500 0000:00:02.0: trying to get vblank count for disabled pipe

Does that help.

 I don't have a ps/2 keyboard, just my wireless and I tried that already. 

Any thoughts?

Thank you.

---

### Post by Bashing-om on 2014-08-21
sang-gyegmx.de; Oh Boy;

this:
> 
[13.136949] gma500 0000:00:02.0: GPU: Power management timed out.

says we need to look at ACPI, and now we are getting into waters that I am not familiar with, nor comfortable.
How to set boot options to overcome this:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

These links will assist you in deciding/setting the boot parameters.


[INDENT][INDENT][INDENT]study
[INDENT][INDENT][INDENT]to show thyself approved
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sang-gyegmx.de on 2014-08-21
thank you - I feel a little scared .... this is a friend's machine who wants to take it to the States next Wednesday (I already lost his house key when he was away the last time, no more f***-ups!)

just a an observation: 
I was able to use ALT CTR F2 to get into the terminal.  

I don't know what to do there, and how to get out, but ... it seems relevant. Is there anything I can do in the terminal to change the keyboard settings? It's strange I can't find other threats on this subject. 

I will look at the links you've sent. 


Thank you
Sang-gye

---

### Post by sang-gyegmx.de on 2014-08-21
and it seems I can't leave the terminal - it asks for a password but the password I've set is not accepted.

---

### Post by sang-gyegmx.de on 2014-08-21
Cold start ... arg .... 

Another observation: I plugged the installation USB in again and chose Try Ubuntu (instead of Install) and the keyboard works.  However, I don't think my friend will like this workaround.

Which kernel are you thinking of adding? The links you sent refer to older installations ( I have 14.04.1 LTS)

---

### Post by Bashing-om on 2014-08-21
sang-gyegmx.de;

Understand this, what you are experiencing is not the norm !
Are you certain you are booting to a text terminal and not to a "grub >" prompt ?

Not a bad idea either to try and boot to a terminal and maybe do some exploration to get some idea of what is happening .

Let's try and boot to terminal the correct way ->
Boot the install and as soon as the bios screen clears depress and hold the right shift key -> grub boot menu;
With the top most entry highlighted press the 'e' key for edit mode -> boot options screen;
Arrow down and across to the terms "quiet splash" and replace them with the term "text" - with out the quotes -.
Key combo ctl+x to continue the boot process to a text terminal (TTY1).
Login here with the username and password - there is no response to the screen when the password is entered, enter blindly and hit the enter key.

Are you logged into the system ?

IF so, next
[INDENT][INDENT][INDENT]we can look around
[/INDENT][/INDENT][/INDENT]

---

### Post by sang-gyegmx.de on 2014-08-21
Thanks so much. Yes, I am in (and this looks like the area where I have been before, so I think, I did get into the text terminal from the desktop). Anyways, this time I was able to log in!!!! Waiting for instructions.

---

### Post by sang-gyegmx.de on 2014-08-21
while I am hanging out:

Welcome to Ubunty 14.04.1 LTS (GNU/Linux 3.13.0-32-generic i686)
*Documentatin: [https://help.ubuntu.com/](https://help.ubuntu.com/)

65 packages can be updated
36 updates are security updates.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the individual files in /usr/shar/doc/*copyright.

Ubuntu comes with ABSOLUTLELY NO WARRANTY, to the extent permitted by
applicable law 


robert@Robert:~$

---

### Post by Bashing-om on 2014-08-21
sang-gyegmx.de; Outstanding !

Maybe all this is but a graphics driver issue !
Let's see what the system relates about the card and driver .
Post back the outputs - Between Code Tags - of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We see where we go from here - but an active terminal is a promising good thing .

maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by sang-gyegmx.de on 2014-08-21
Thank you for the 'flowers' - blush .... I am amazed myself. 



```
robert@Robert:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:Obe1
] (rev 09)
          Subsystem:SSUTek Computer Inc. Device [1043:84a9]
          Kernel driver in use:  gma500
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
```


```
robert@Robert:~$ sudo lshw -C display
[sudo] password for robert:
   *-display
          description: VGA compatible controller
          product: Atom Processor D2xxx/N2xxx Integrated Graphics Controller
          vendor: Intel Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: 09
          width: 32 bits
          clock: 33 MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=gma500 latency=0
          resources: irq:45 memory dfc00000-dfcfffff ioport:f0e0(size=8)
robert@Robert:~$
```

---

### Post by Bashing-om on 2014-08-21
sang-gyegmx.del OH NO !

> 
Kernel driver in use:  gma500


we are sucking hind tit here !
[https://wiki.archlinux.org/index.php/Poulsbo](https://wiki.archlinux.org/index.php/Poulsbo)
[http://ubuntuforums.org/showthread.php?t=1984236](http://ubuntuforums.org/showthread.php?t=1984236) <- support thread for the GMA500 ( bodhi.zazen )
[http://ubuntuforums.org/showthread.php?t=2107593](http://ubuntuforums.org/showthread.php?t=2107593)

There just is not good support for that driver.
All I can suggest is to read and heed, see what you can work out. I have never encountered that critter directly, so I can not be much help directly.
I will do what I can.

A developer is presently active in  bodhi.zazen's thread, you and he may get good results when you join that thread.

[INDENT][INDENT]sometimes,
[INDENT][INDENT][INDENT]there just ain't no good help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sang-gyegmx.de on 2014-08-21
Hi Bashing-OM:

I found something that seems to be related in this thread:  [http://ubuntuforums.org/showthread.php?t=2143769](http://ubuntuforums.org/showthread.php?t=2143769)

QUOTE:

**"PowerVR based chips on Linux [[edit]("http://ubuntuforums.org/w/index.php?title=Intel_GMA&action=edit&section=25")]**

GMA  500, GMA 600, GMA 3600, GMA 3650 are PowerVR based chips incompatible  with Intel Graphics Media Accelerator main architecture. There are no  Intel supported [FOSS]("http://ubuntuforums.org/wiki/FOSS") drivers. The current available FOSS drivers (included in Linux 3.3 onwards) only support 2D acceleration (not 3D acceleration).[SUP][[SIZE=2][25][/SIZE]]("http://ubuntuforums.org/#cite_note-Poulsbo_-_ArchWiki-25")[/SUP]
Ubuntu supports GMA500 (Poulsbo) through the ubuntu-mobile and gma500 repositories on [Launchpad]("http://ubuntuforums.org/wiki/Launchpad_%28website%29").  Support is present in an experimental way for 11.10 and 12.04, but the  installation procedure is not as simple as other drivers and can lead to  many bugs. Ubuntu 12.10 has 2D support included.[SUP][[SIZE=2][52][/SIZE]]("http://ubuntuforums.org/#cite_note-52")[/SUP]
[Joli OS]("http://ubuntuforums.org/wiki/Joli_OS"), a Linux based OS optimized for netbooks, has a driver for the GMA500 built in.
PixieLive, a GNU/Linux live distribution optimized for GMA500 netbooks, it can boot from USB Pendrive, SD Card or HardDisk.
Intel releases official Linux drivers through the IEGD (Intel Embedded  Graphic Driver) supporting some Linux distributions dedicated to the  embedded market.[SUP][[SIZE=2][53][/SIZE]]("http://ubuntuforums.org/#cite_note-53")[/SUP]
In November 2009, the [Linux Foundation]("http://ubuntuforums.org/wiki/Linux_Foundation") released the details of a new, rewritten Linux driver that would support this chipset and Intel's other upcoming chipsets. The [Direct Rendering Manager]("http://ubuntuforums.org/wiki/Direct_Rendering_Manager") and [X.org]("http://ubuntuforums.org/wiki/X.Org_Server") parts would be free software, but the 3D component (using [Gallium3D]("http://ubuntuforums.org/wiki/Gallium3D")) will still be proprietary"

---

### Post by sang-gyegmx.de on 2014-08-21
Must have posted at the same time as you ....


I checked out bodhi.zazen's thread and it dates from 2012. Is it still a good idea to join?

---

### Post by Bashing-om on 2014-08-21
sang-gyegmx.de; Well;

The situation is not without hope.
The  bodhi.zazen thread started back then, as of 3 weeks ago there is activity - and has the interest of a developer.

All I can suggest is to study the options that you can make available, and choose the better one for your abilities ( and as much as we can help ).

I do admit ->

[INDENT][INDENT]the pressure is on you
[/INDENT][/INDENT]

---

### Post by sang-gyegmx.de on 2014-08-21
ok ... I will enter in that discussion .... not sure if that is appropriate.

---

### Post by sang-gyegmx.de on 2014-08-21
I am sorry, I am not clearly seeing any solutions.

Is there an option to change/update the driver?
Then there is discussion about changing the 'kernel' .... I have only a very vague idea what that means. Is that difficult?
Do you think another Linux distribution could solve the problem? (Fedora doesn't seem to be the one ;)  )
And who is the developer? How do we know someone is still interested? 

This seems to have something to do with keyboard: [https://github.com/EMGD-Community/xserver-xorg/blame/master/debian/local/64-xorg-xkb.rules](https://github.com/EMGD-Community/xserver-xorg/blame/master/debian/local/64-xorg-xkb.rules)

Maybe I should try and reinstall windows?

---

### Post by |{urse on 2014-08-21
If you put your windows disc in and it lets you use the keyboard during install, then your problem is linux, if it doesnt work then its a dead keyboard or improperly seated connection to the zif cable connector.

So you don't go reinstalling unnecessarily.

---

### Post by Bashing-om on 2014-08-21
sang-gyegmx.de; Humm, like this

All linux distributions are based on the same same kernel, it is highly unlikely that any other distro will function any different.

Changing the kernel: Nope, not a good solution for someone unfamiliar with linux, as that leads to no sponsored support.

Building the driver: Well, can be done with good guidance - that ain't me as I have yet to have that experience ( lucky !).

> 
And who is the developer? How do we know someone is still interested? 

Join the thread, ask an intelligent question,  and await the response.

And yes the possibility does exist that the incorrect driver has been loaded. There is " gma500" and also "gma500_gfx "; gma500_gfx is for the Poulsbo card and gma500 is for the cedarview one. The kernel can make mistakes, though rare.
We might explore that possibility and find out which card you have.

> 
I am sorry, I am not clearly seeing any solutions

If there were easy solutions we would not be at this point.

Tentatively I say, If you are not willing or able to put forth the effort that it may take to make this work, then yes put Windows back on the system .... better yet, both ! .. Dual boot and at your leisure seek the solution that fits your use-case for the gma500 problem.

Now that said, I am but one of about 1600 persons. Give it some time and see what others here can and do advise.

I do not mean to be either curt nor rude nor unsympathetic, with the gma500 card I just do not have a solution. I will support you in what ever course you decide is in your best interest. I have not been there and I just do not know.

[INDENT][INDENT]this is one of those rare times
[INDENT][INDENT][INDENT][INDENT]I just do not know[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bodhi.zazen on 2014-08-21
The gma500 driver is now in the default kernels of most ditros and for the most part works out of the box, although performance is a bit laggy (the gma500 is not a power house on windows either IMHO).

Take care with that old gma500 thread as one of the developers was at one point in time giving advice that I could never reproduce. Some of the advic ewas resulting in broken systems. The most up to date information is located at [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

You will see not much has changed as the driver , over time, moved out of the experimental phase and into stable. The Ubuntu (and most other distros) updated the default kernel to load the driver as a module.

Unfortunately the gma500 and similar cards are a bit long I the tooth and kernel development as stopped. Thus there is nothing new with the driver.

At any rate , the gma500 driver has to do with the graphics card and not the keyboard.

Assuming the keyboard is working, try running from a live usb drive and select an alternate keyboard layout or simply go with the defaults.

The keyboard is set in the initramfs using console-data and keyboard-configuration

See - also - [http://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu](http://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu) and [http://askubuntu.com/questions/360378/how-to-access-the-keyboard-layout-options-in-13-10](http://askubuntu.com/questions/360378/how-to-access-the-keyboard-layout-options-in-13-10)

---

### Post by Bashing-om on 2014-08-21
@bodhi.zazen; heaps thanks !
Takes a load off me.

For My education: Is not the keyboard as well as the graphics controlled by Xorg, such that the keyboard interface is also a component of the graphics driver ? Relating from the old /etc/X11/xorg.conf file.

[INDENT]respectfully
[INDENT][INDENT][INDENT]always open to learning better
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sang-gyegmx.de on 2014-08-21
@bodhi.zazen; Thank you so very much for checking in on me. That means a lot. And yes, everything was really slow under Windows, which is why my friend wanted to switch. He was hoping it'll be faster under Ubuntu. Not sure that he'll find that that's the case. Maybe there is a way to tweak the installation a bit. 
@Bashing-om; Thank you for your very kind and patient support so far. 
@[**[COLOR=#000000]|{urse[/COLOR]**]("http://ubuntuforums.org/member.php?u=223883"); thanks for the tip ....


And now @all: ... I have no idea how and why, because apart from browsing different forums and google the same question in 100 ways, I didn't do anything else but stare at the screen, restart, retry, switch into terminal, try to get out (which I didn't), staring some more .... now the keyboard works. I am able to log into the desktop. When the keyboard first responded in desktop mode, I received an error after login. Something along the lines 'Sorry there is a system error. Restart and try again. Do you want to send report?" Which is what I did. And now .... Holy moly, I am able to start Firefox and do a search. 

Again ... I have no idea what happened, I can only attribute it to divine intervention and I am enough of a theist that I will. :)

Sang-gye

---

### Post by Bashing-om on 2014-08-21
sang-gyegmx.de; Outstandingly great news !

OK, how is the action , is ubuntu fast enough on that box ? - rule of thumb if Windows was slow - the top-of-the-line ubuntu will be also, it takes the horse power to run ubuntu.
If so, a better alternative will be Lubuntu or Xubunu. Different desktops and much less resource hungry than ubuntu.
( I have a personal preference for xfce (xubuntu) because it is light weight, FAST, and highly configurable )

None the less
[INDENT][INDENT][INDENT]we can now say
[INDENT][INDENT][INDENT][INDENT]welcome to our world
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sang-gyegmx.de on 2014-08-22
Hi Bashing-om,

thanks for the welcome. :)  Got my share of beans within the last 2 days, that's for sure ...

I think it's still slow, but my friend was really, really happy with the outcome. He says it's fast and he will try it out with skype. It was the fact that skype froze on him on a regular basis with his windows installation that he wanted to switch. (How can they sell a netbook that doesn't play youtube videos and can't handle a video chat ?????)  So, skype working or not working will make or break it. If that doesn't work, I will try xubuntu. I also talked to my bro, who supports networks in Germany. He recommended open SUSE, but admitted that he hasn't worked with Linux in a while. 

Thanks again, Bashing-om .... delight meeting you.  :)

Sang-gye

---

### Post by Bashing-om on 2014-08-22
sang-gyegmx.de; Hey hey ;

Well, just glad to assist, and pleased things are working out.
Download and burn to disk both xubuntu and Lubuntu see which you/your friend like.

Then when you are comfortable with 'buntu ->
For something really FAST, lightweight and customized, you will do a core-install and install exactly what/how you like.

As this matter is concluded, please mark this thread solved.
Top of post -> thread tools

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]you 'can' have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

