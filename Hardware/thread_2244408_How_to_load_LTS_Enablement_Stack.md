---
title: "How to load LTS Enablement Stack?"
date: 2014-09-16
forum: Hardware
---

### Post by Alex Eagle on 2014-09-16
The question is in the title. I want to get rid of Gallium 0.4 on llvmpipe and there was a post about this on askubuntu, and they suggested loading the LTSES and running some code through terminal.
And try and keep it simple as possible.

Thanks guys.

---

### Post by Bashing-om on 2014-09-16
Alex_Eagle; Hi !

In easy steps, as we must know what you are running.
Post back - Between Code Tags _ the outputs of terminal commands:
```

lsb_release -a
lspci -nnk | grep -iA3 vga
sudo lshw -C display

``` and we see where we go from there.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]where there is a will
[INDENT][INDENT][INDENT]there is a way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-09-17
```

LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:core-4.1-ia32:core-4.1-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:cxx-4.1-ia32:cxx-4.1-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:desktop-4.1-ia32:desktop-4.1-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:graphics-4.1-ia32:graphics-4.1-noarch:languages-3.2-ia32:languages-3.2-noarch:languages-4.0-ia32:languages-4.0-noarch:languages-4.1-ia32:languages-4.1-noarch:multimedia-3.2-ia32:multimedia-3.2-noarch:multimedia-4.0-ia32:multimedia-4.0-noarch:multimedia-4.1-ia32:multimedia-4.1-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:printing-4.1-ia32:printing-4.1-noarch:qt4-3.1-ia32:qt4-3.1-noarch:security-4.0-ia32:security-4.0-noarch:security-4.1-ia32:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

```

```

01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
    Subsystem: Fujitsu Technology Solutions Device [1734:1125]
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Qualcomm Atheros AR242x 802.11abg Wireless PCI Express Adapter (rev 01) [168c:3067]

```

```


  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d4000000-d401ffff ioport:9000(size=128)

```

I love the community spirit of ubuntuforums. Thanks for your help.

---

### Post by Bashing-om on 2014-09-17
Alex_Eagle; Oh Boy ;

SIS graphics, display "unclaimed" ! There might be some hope yet for that graphics driver:
[http://ubuntuforums.org/showthread.php?t=2144455](http://ubuntuforums.org/showthread.php?t=2144455)
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

When all else fails, -> you could try this ppa ->
[https://launchpad.net/~canonical-x/+archive/x-staging](https://launchpad.net/~canonical-x/+archive/x-staging)

Here is the long time story:
[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

Look these over, know what your options are, and decide on what you want to do. Then we discuss this issue further.

[INDENT][INDENT]we do the best we can
[INDENT][INDENT][INDENT][INDENT]with what we have to work with
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-09-17
I've gotta ask, do you think this is what I should be doing? Have a look at another of m posts:

[http://ubuntuforums.org/showthread.php?t=2243501](http://ubuntuforums.org/showthread.php?t=2243501)

Those pics show my problem. I cottened onto the LTSES idea because of looking at another post which suggested that.

> **Bashing-om said:**
> Alex_Eagle; Oh Boy ;
SIS graphics, display "unclaimed" ! There might be some hope yet for that graphics driver:
[http://ubuntuforums.org/showthread.php?t=2144455](http://ubuntuforums.org/showthread.php?t=2144455)
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

When all else fails, -> you could try this ppa ->
[https://launchpad.net/~canonical-x/+archive/x-staging](https://launchpad.net/~canonical-x/+archive/x-staging)

Here is the long time story:
[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

Sorry dude, but pretty much everything in all of these posts went over my head. I'm gonna ask the friend who put me onto ubuntu to fix it for me. He's God of Geekiness, Inventor of Inspector Gadget, The Aristotle of Computers! So he should know what to do. :p 

If you have any answers, keep it simple, explain it well and preferably post pics to show what to do.

Thanks.

---

### Post by Bashing-om on 2014-09-17
Alex_Eagle; Yepper;

This tells the tale - from your output:
> 
 *-display UNCLAIMED
<snip>
 configuration: latency=0

You have no display (graphics ) driver loaded. Until such time as a graphics driver is loaded you will not have a good GUI experience.
As to what it will take to get a SIS driver loaded, and HOW it will perform, I do not know as I do not have direct experience with SIS graphics.
The 1st link - the best I recall - gives instruction that might get 3D acceleration working ?? I understand that the developers have got SIS graphics working for the 14.04 release.

You do your homework, and I will meet you on common ground and we see what we can do.
There are avenues we can pursue, only you can choose which you want to try 1st.

[INDENT][INDENT]the good news
[INDENT][INDENT][INDENT]there are means to make it better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-09-20
Thanks mate. Got some (seemingly) simple advice from my "ubuntu oracle" (the friend I mentioned :-P). Hope it works! :-D

---

### Post by Bashing-om on 2014-09-20
Alex_Eagle; Great !

Let us know how it goes, and what yall come up with ( for all posterity ).
Any way further we can help, ask! and we see what else we can come up with.

[INDENT][INDENT]gotta have that driver
[INDENT][INDENT][INDENT][INDENT]to make communications possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-09-20
You have Ubuntu 14.04.1. That means that you already have the latest Hardware Enablement Stack. We get it as part of the normal updating method using Update Manager. And this one came through on, or about July 24th this year.

Regards.

---

### Post by Alex Eagle on 2014-09-21
Let's put it this way; I think I'm stuffed. I have "Googled Nvidia Graphics Driver Download", or sometimes I replaced "Nvidia" with "Intel". The only vaguely useful looking thing was an installer which [I think] detects what you want and asks whether you want to install it. But I already have this program installed, and have run it, and it doesn't work. Some error about "You don't have a ... card". 

   If you could find a download that's what I want that would be great. Even better would be the terminal code to install it.

Thanks a bunch. :-D

My friend told me to look for a linux driver to download. All I found was an installer which auto finds what you need and asks if you want to install it. I already have that program, and it hasn't worked.

Can you find a driver for me? I just need a download to go on a USB. (Long story)

Thx

Sorry if I've posted this several times but my post doesn't seem to be going through. 

My friend said to find a linux driver download to put on a stick, so I could go into settings and select a drive with a driver loaded on it. Or something like that lol.

But the only thing I could find was an installer which finds what you want automatically and asks if you want to install it. But I already have that program, I've run it, and it didn't work.

Can you **please** find a driver to download for me? Or even better a terminal line to install it.

Thanks guys.

P.S: On the subject of guys, do you think there are any women on this forum? I've never been able to find one. Lol. I know pleanty of female geeks in person, but I've never found one here. :p

---

### Post by Bashing-om on 2014-09-22
Alex_Eagle; Hey;

You appear to be chasing down the wrong trail:
> 
Let's put it this way; I think I'm stuffed. I have "Googled Nvidia Graphics Driver Download", or sometimes I replaced "Nvidia" with "Intel". The only vaguely useful looking thing was an installer which [I think] detects what you want and asks whether you want to install it. But I already have this program installed, and have run it, and it doesn't work. Some error about "You don't have a ... card". 

You do not have a Nvidia OR and Intell card; Per this output of yours:
> 
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
    Subsystem: Fujitsu Technology Solutions Device [1734:1125]
&&
*-display UNCLAIMED     
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]

You are running SIS for your graphics, and that is somewhat problematic as support from the manufacturer is somewhat limited, and our developers continue to work on that driver. The support in open source is much improved in release 14.04. I refer you back once more to post #4.
Once you are aware of your options, we can continue to see what can be done to get a graphics driver loaded.

[INDENT][INDENT]there is no magic pill
[INDENT][INDENT][INDENT][INDENT]we just work with what we have
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-09-23
Tried to find a linux graphics driver download to put on a USB as my friend told me to but all I could find was an installer. But I already had it and it didn't work. :-/ 

Can you find a download for me? Or even better a terminal line to install it.

Thanks. :-D

---

### Post by Bashing-om on 2014-09-23
Alex_Eagle; Sure;

> **Alex_Eagle said:**
> Tried to find a linux graphics driver download to put on a USB as my friend told me to but all I could find was an installer. But I already had it and it didn't work. :-/ 

Can you find a download for me? Or even better a terminal line to install it.

Thanks. :-D

Give me a bit of time to get caught up on other things, and I see what I can come up with.
In my limited experience with SIS graphics, getting this chip set to work has been problematic, but doable.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-09-23
Alex_Eagle; Well,,,

You are afflicted with that "non-functioning" [SiS] 771/671 PCIE VGA Display Adapter.
Unity can not support that card, and IF you desire to run 'buntu, then (L)ubuntu release 14.04 is the one for you !
Please review thread
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)
and join that thread to discuss this further.

[INDENT][INDENT]harsh facts of life
[INDENT][INDENT][INDENT]are harsh
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-09-25
Hi. Sorry about the multiple posts. I just realized that there a second page. :-P *facepalm* I would really rather have ubuntu because I just don't like the other Linux distros. Especially Lubuntu. :-/ So I should try and find an SIS download?

Thanks for being patient. :-D

Do you think Debian could work? I really need to stay as close to ubuntu as possible because of what I need it for (mainly Python programming). So I think moving up the "distro tree" instead of across it might be the way to go.

Thanks.

---

### Post by Bashing-om on 2014-09-25
Alex_Eagle; WQell.

I have not booted 'debian' in several years, so I can not advise. Will not hurt to try.
As to using ubuntu, the reason you will not be able to run a GUI is that unity is now 3D only, and your SIS card will not support it.
Another thought, you can try ubuntu release 12.04[color=red].1[/color] as that release has the older xserver stack and does have 2d capability for unity. Release 12.04.1 does have full support 'til April 2017.
[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

not great,
[INDENT][INDENT][INDENT]maybe, good 'nuff
[/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-09-29
That's all good. Is it possible that I could get another card and replace my old one? If so how much (roughly) is a card? And how would I sort out a driver for that one.

Thanks.

---

### Post by Bashing-om on 2014-09-29
Alex_Eagle; Yes;

In my humble opinion, a new graphics card is the BEST course.
As to what to purchase, I will not go there.
But, I am running on an older ATI card that I paid $15 USD for new .
```

sysop@1404mini:~$ lspci -nnk | grep -iA3 vga
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] [1002:7146]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:2342]
        Kernel driver in use: radeon
06:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]
sysop@1404mini:~$ 

```
Running the open source driver "radeon" .. with absolutely no problem - for my use case !
I did my homework and KNEW this card was compatible with my hardware, and I sure could not fault the price. 

[INDENT][INDENT]your result could be different
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-02
OMG THANK YOU! That's exactly what I wanted to hear. Is it relitively easy to install onto the motherboard (or whatever)? You know what I mean. Sorry but does it come with driver, and if not, how would I get those?

Thanks a bunch :-)

I just watched [this]("http://is.gd/pKpKpC") on YouTube. At the beggining it says that if you bought the laptop with a factory standard card your GPU isn't replaceable. Do you know if this is true for me? I'd imagine that you can replace it but I'm not sure. I think dad bought it from the net, or possibly Curry's. 

I realize you're busy. I had a look at your profile and it's packed with other peoples tech probs. So I **really** appreciate your help. :-D

---

### Post by Bashing-om on 2014-10-02
Alex_Eagle; Hello;
My my:
> 
I realize you're busy. I had a look at your profile and it's packed with other peoples tech probs. So I really appreciate your help.

"WE" all help as best we can. it is what we do.

As to a laptop, and swapping out the GPU, depends; MOST, as you have found out, can not be replaced.
What specific laptop do you have ? -  the exact make and model. Will see what we can do in the realm of swapping that GPU out .

In the mean time, burn you a liveDVD of Lubuntu and see how it preforms on your hardware.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[INDENT][INDENT]sometimes
[INDENT][INDENT][INDENT]there just ain't no easy solutions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-03
Hee hee. I have a Fujitsu Siemens Esprimo Mobile V5535. It's crappy I know, but lets just say that my father wasn't lined up to buy the first Macintosh.

Thanks again.

Haha. I know it was a bit cheeky, but hey! Your profile's out there so people are gonna look at it :-P

I'm looking at [this]("http://is.gd/q9xPLe") on eBay. I'm signed up to a UK scheme called Shop&Scan. It's a long story but to cut it short, they pay me in coupons. I can use them on Amazon but not eBay. So I found the card on Amazon, because I may as well use the money I make, but the one on Amazon has no drivers pre-installed. So how would I get the drivers for it? And whilst I'm trying to find them, will the graphics be as bad as they are now? And how would I load the drivers?

:-)

BTW I got this message from the seller of the eBay item I linked:

[COLOR=#000][FONT=arial]Hi

We only supply the drivers available on the manufacturers website and these dont include Linux drivers.
Regards
Steve

? So what did you do? (Sorry for all the questions lol)
[/FONT][/COLOR]

---

### Post by Bashing-om on 2014-10-03
Alex_Eagle; Hey hey !

I have no familiarity with that lappie, let me have some time to see what .
How much hassle is will be to open her up
If once opened up the GPU is removable - without major surgery . 
Going back together, The cards slots must match with that of the motherboard.
Power consumption is also a consideration.

If you are basing your graphics card selection on what I chose, Don't ! .. As I am running an AMD mother board and it is a desk top machine and all my graphics needs are light. But, that ATI card suits me just fine, and I have no problems, as in none, running an open source driver.

OK,as to drivers .. linux (ubuntu) Has a totally different philosophy than what you are accustomed to. The kernel will take care of the driver. If it needs a driver it will go hunt it up and install it. If that diver is not up to your satisfaction, you can direct the system to hunt up and install a different - proprietary - driver - the system will try, see what is available from the ubuntu software repository, After "Additional Drivers" and no great driver is installed, it can get hairy. These hairy situations are not to be entered into by the inexperienced.
> 
We only supply the drivers available on the manufacturers website and these dont include Linux drivers.

Yepper, we take care of our own - However, AMD (ATI) does offer some support, IF one has a need to go that far !
Nvidia offers the better support at this time for linux in general
Intel is Solid !

> 
but the one on Amazon has no drivers pre-installed. So how would I get the drivers for it?

The kernel will take care of it ! Install the card ( if possible) and when the system boots the system will configure it's self for this new hard ware, and if needed go find the driver it wants And as well automagically install .

But you see MOST times that open source driver is absolutely fine ! .. If you are a gamer, or into accellerated graphics, Well shell out the big bucks and MAYBE there is an OEM driver for that card - one best do a lot of homework here.

> 
 but lets just say that my father wasn't lined up to buy the first Macintosh.
 
There is always bigger and better, a never ending upgrade process, I tell my kids, if what I do provide is not good enough, well, go wash dishes in the down town restaurant and buy what you want. ( but, show me the need and I will do better)

OK, let me get caught up, and I look at see about opening up your box . - Might have a long heart to heart talk with your Dad about this little endeavor 
of ours !

[INDENT][INDENT][INDENT]maybe, just maybe
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-03
Alex_Eagle; Welp; I did

I did Look, and there is no swapping out that graphics card on this a "notebook"  ->Fujitsu Siemens Esprimo Mobile V5535.

The easiest thing to do at this point is to install (L)ubuntu, and take it from there.

[INDENT]gotta have the Hardware
[/INDENT]

---

### Post by Alex Eagle on 2014-10-04
Haha, you sound just like my own dad. I understand why it's crappy, and don't blame him for it, but it's a fact I have to deal with every day, it's not what it used to be. You don't need to talk with him, I make sure he gets my current plan when I tell him.

Do you think I'd be able to find a suitable card if I looked? I don't want to trawl the net if it's to hard because I don't know what I'm looking for.

Thanks

EDIT:

Oh, ok. Does it _have_to be Lubuntu? I don't like it _at all_. I did try making a USB boot disc for Debian but the ISO wouldn't load onto the USB. ([http://is.gd/DdV1fw](http://is.gd/DdV1fw))

:-)

---

### Post by Bashing-om on 2014-10-04
Alex_Eagle; Hey !

Yeah, age does bring a change in perspectives ! as to your lappy, pretty descent box there for what it is ! Top of the line in it's class.

As to what Operating system to install .. anything that is not unity should work.
Take a look at:
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
When you have gained in knowledge and experience with linux, you might even want to do a minimal/core install and install the desk top that you prefer. But NOT unity, 
Remember unity is now 3D only and your SIS card does not have that ability.

Might even want to push the boundary a bit:
[http://ubuntugnome.org/download/](http://ubuntugnome.org/download/)

Burn an .iso to disk, and see which you like the more.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT][INDENT]there are options[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-04
Ok. I've looked at all the buntu's thanks. I'd prefer either Debian or Ubuntu. Could you explain how to install the various different DE's in the different OS's? Is it just a matter of Googling?

---

### Post by Bashing-om on 2014-10-04
Alex_Eagle; Welp;

I can not advise on anything other than 'buntu - it has been too many years since I have booted others.
As to installing multiple DEs, well, I have seen many advise it is acceptable to do so, but I have also seen many problems if/when one of them are removed. I do recommend burning a liveDVD(USB) and seeing what the system (desktop) is like from that environment.
Installing an additional DE in 'buntu is as simple as:
```

sudo apt-get install xubuntu-desktop

```
And at the login screen - username box -> ubuntu icon; select the session you want to use.

[INDENT][INDENT]options, options !
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-05
Is it possible/easy to switch between DE's? And could I replace "xubuntu" with another enviroment, like so:

```
 sudo apt-get install gnome-desktop 
```

?

EDIT:

Forget that. Just found [http://is.gd/QHXAMq](http://is.gd/QHXAMq). I refer you to post 4(?). KDE. Do you think it might be too heavy for my system. The post does say that it's requirements are similar to Unity. My other fave is GNOME Shell. Let us know what you think. :-)

---

### Post by Bashing-om on 2014-10-05
Alex_Eagle; Hang'n


The package is "ubuntu-gnome-desktop"
Install, and reboot, the new DE should be available @ the login screen from the ubuntu icon in the login box.

[INDENT][INDENT]good luck
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-05
Thanks a bunch dude. Will get back to you on whether it works.

It hasn't worked. :-( Here's a photo.
[ATTACH=CONFIG]256961[/ATTACH]

It looks like it did on Unity. How can I switch to light mode? When I installed it the terminal asked me whether I wanted to use light or normal. Can't remember the exact terms. gdb? Dunno.

Thanks

P.S: Do you skype?

---

### Post by Bashing-om on 2014-10-05
Alex_Eagle; Humm,

What command did you run to install an alternate Desktop environment ?
When you click on the ubuntu icon in the login box, what results ?

I do not have access to a gnome desktop, so I have no idea what to expect for a 'display" .

With the gnome desktop, I expect it to use "gdm" rather then "lightdm" as the DM.

[INDENT]sometimes, I just do not know
[/INDENT]

---

### Post by Alex Eagle on 2014-10-05
I used ```
 sudo apt-get install gnome-shell 
``` It was on that forum I linked. Well I thought about clicking gdm light because obviously it would demand less of my system. :-/ When I click on it it comes up with ubuntu and gnome. I switched to gnome at boot.

Correct that. I was already in LightDM. So I really don't get it now. Should I have a fiddle with stuff like hardware acceleration?

---

### Post by Bashing-om on 2014-10-05
Alex_Eagle; Welp;

Looking about I find:
This ?
> 
The switching did not work seamlessly when 14.04 was released in April 2014 and I had to add this utility to enable the desktop switch to function.

```

sudo apt-get install gnome-session

```

May be 
[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-06
Thanks for finding that for me but sadly my (as I now know), notebook, had a habit of randomly already having things people think it doesn't.

This is what terminal returned:
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

Bashing-om:

Are you still trying to help me with this? :-)

---

### Post by Bashing-om on 2014-10-11
Alex_Eagle; Yeah;

I am still hanging in here.
There is no point in me responding, however, when I have nothing to add to the thread.
I have no access to a Gnome desktop so I can not relate. Does Gnome require 3D ? I do not know. If it does, again your card will not support it.

I suggest again that you install (L)ubuntu to get a firm foundation on something that "does" work. From that foundation make the changes you desire, such as adding a desk top environment. If it breaks, one will have a better comprehension of the why.

You can not change the hardware, so you must work within the limitations of the software that interfaces between the graphics card and the kernel.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-11
Thanks. Good  to know. It's just that having heard nothing it seemed like you'd given up. Sorry about that.

I haven't actually checked, but for some reason I get the impression that GNOME is only 2D?! Don't know why I think that but will check anyway.

I appreciate that I have to work within my hardware's requirements. That's the annoying thing about it.

You've been really helpfull BTW, and tell your kids that they're lucky to have a Dad with such good reasoning power and understanding about life. That's what I like about my own Dad. My answers to things are rarely ever better than his because he's got so much more experience, which helps :-P

---

### Post by Bashing-om on 2014-10-11
Alex_Eagle; Blushingly ->

> **Alex_Eagle said:**
> Thanks. Good  to know. <snip>

<snip>
You've been really helpfull BTW, and tell your kids that they're lucky to have a Dad with such good reasoning power and understanding about life. That's what I like about my own Dad. My answers to things are rarely ever better than his because he's got so much more experience, which helps :-P
I owe that to my own Dad and Grandfather, and yes, there is no substitute for experience. It does take time to get those "hard knocks".

All we can do is try and lessen the harshness of those knocks.

To the situation at hand: Do you presently have a semi-functional Gnome desktop ? Have you tried disabling accelerated effects ?

I still say is better to get something that works, and build up, rather then something not working and try to tear down.

None the less
[INDENT][INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-11
Well I've made enough mistakes already to have a fair bit of experience, but obviously I'm still in my teens and have enough sensibility to know that I still need to ask other people and rely on them to guide me in serious stuff. I still need help.

Just checked it out on google and it turns out that GNOME **is 3D**. Do you know anything about XFCE? I like the look of that. Currently looking for the answer to whether it's 2D.

:-)

EDIT:

Just found out that it's 2D. Although, you did suggest disabling hardware acceleration in GNOME. Now to that, I can't find out how to. I you know how, let me know...

---

### Post by Bashing-om on 2014-10-11
Alex_Eagle; Hey ...

Nope no direct help in Gnome.

And Yep, I prefer xfce4 as my DE, and is what I run.
I like it because it is clean, fast and configurable . You may have a different need and attitude. All I can suggest is install it and see.
I run a "core install" (minimalistic to the extreme) and for a GUI, xfce4 best meets my wants.

IF you want to see xfce4 in all it's glory, download (x)ubuntu and test in the live environment:
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
Which I think is the easier thing for those less experienced with 'buntu to do, rather then build up from nothing.

Your system, your time, your effort
[INDENT][INDENT][INDENT]I will help in any way I can
[/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-11
Just installed. It hasn't worked?! This is firefox in a Xubuntu session.

[ATTACH=CONFIG]257130[/ATTACH]

Don't know what to do now. :-/

---

### Post by Bashing-om on 2014-10-11
Alex_Eagle; Huh ??

What has not worked ?? I have no point of reference when all you say is " It hasn't worked?" ; and yet you are using FireFox . And that is a GUI application. SO then I must infer that the GUI is functional .

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-12
I mean that things are still blown out of preportion. The tabs shouldn't take up **that** much space on the bar at the top. (Taskbar?) Also some windows still don't fit the screen all together, e.g: Software Centre.

I really don't get why the graphics are still wacko. It works, as far as being functional, but I still can't see things properly and have to Alt+F7 to drag windows. Sorry for the vagueness.

---

### Post by Bashing-om on 2014-10-12
Alex_Eagle; OK !

Now I understand .. As you running that SIS graphics card might look into the 'xrandr' command to make selective changes to the display:
see:
```

man xrandr

```

OR do we have a config file(s) we can mess about with ?
what returns from terminal commands:
```

ls -al /etc/X11/Xorg.conf
ls -al /etc/X11/xorg.conf.d
ls -al /usr/share/X11/xorg.conf.d

```

Now IF the " Xorg.conf " file exists - or we determine to make one up, then:
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
will be a big help.

[INDENT][INDENT]willing to find out
[INDENT][INDENT][INDENT]what can be done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-12
I ran the last block of code you put in your answer. Here's what it returned:
```
  ls -al /etc/X11/Xorg.conf
ls: cannot access /etc/X11/Xorg.conf: No such file or directory
rasphack@Alexs-Coding-Machine:~$ ls -al /etc/X11/xorg.conf.d
ls: cannot access /etc/X11/xorg.conf.d: No such file or directory
rasphack@Alexs-Coding-Machine:~$ ls -al /usr/share/X11/xorg.conf.d

```

The xrandr returned a menu type list of things you could go into and presumably edit, but it looked quite advanced and I didn't want to mess around with it because I'm not sure of the controls to use.

Should I create a xorg? I've read about them before but at that point I didn't know if it was the right thing to do.

Thanks

---

### Post by Bashing-om on 2014-10-12
Alex_Eagle; hummm ...

 OK, the possible config files are not an issue.
Like I have advised I have zero experience with SIS graphics. I do not have solutions. Only suggestions on what can be tried to see what might work.

I do like the idea of 'xrandr' to see what the possibilities may be.
See:
[http://ubuntuforums.org/showthread.php?t=1370258](http://ubuntuforums.org/showthread.php?t=1370258)
 for instruction on setting up an alternate resolution.
How the found resolution is made to "stick" will vary, depending on the DE.

[INDENT]there are ways, and means
[/INDENT]

---

### Post by Alex Eagle on 2014-10-12
So I have been having [this]("http://ubuntuforums.org/showthread.php?t=2244408") problem.

[This is the thread]("http://ubuntuforums.org/showthread.php?t=1370258") I want to continue.

I have an SIS card and Bashing-om has little experience with SIS. The suggested
```
 xrandr 
```
returned ```
 xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        73.0* 


```

Thanks guys.

---

### Post by Frogs Hair on 2014-10-12
The *solved* and closed thread was started four years ago and there are no supported versions of Ubuntu or flavors from that time period so a new thread is warranted.

---

### Post by mörgæs on 2014-10-12
... but it's not warranted to start two threads on the same topic. Merged.

---

### Post by westie457 on 2014-10-12
Hi, this page, [http://old-releases.ubuntu.com/releases/12.04.0/](http://old-releases.ubuntu.com/releases/12.04.0/) has a link to get 12.04.0, this version has no hardware en-ablement stack and is locked to the 3.2 series of kernels.
It also is the version my ageing (circa 2007) under-powered laptop is allowed to run.
As I am not at home right now I cannot tell you if there is a choice between 2d- or 3d-Unity at Log in. I will confirm this later when I get home.

Alex-Eagle, If you could go to System Settings > Screen Display > Resolution to check what resolutions are available for your SIS-card.
If you have already tried to change the resolution with no success there is not much more help I can offer here.

Bashing-om how do you manage to get so many easy problems to deal with.:lolflag:

---

### Post by Bashing-om on 2014-10-12
@westie457; ole buddy

I recon,

> 
Bashing-om how do you manage to get so many easy problems to deal with.&#65532;


I must not be paying the preacher ?? Or maybe - if -  it is not difficult and of a thorny nature, I make it so ? Seems Like I keep at least 3 thorny threads active at any given time and then I have to holler for help !

[INDENT]just about the time I think my learning curve is flattening out
[INDENT][INDENT][INDENT][INDENT]I have to go and do this ?[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by westie457 on 2014-10-12
@ Bashing-om, fair enough about the learning curve, mine is more like a flat surface that is slightly raised at one end.
How I managed to get this many beans on this Forum - with my level of incompetence - never ceases to amaze me.
Before this thread gets to far off topic I hope my small contribution will be of some use.

---

### Post by Bashing-om on 2014-10-12
westie457; A fount of knowledge ;

Hey with this graphics set, any offered solution is a good solution.
All depends on what course Alex wants to pursue. And what we can make work.

[INDENT]be interesting to see what
[INDENT][INDENT][INDENT][INDENT]does work out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2014-10-13
Hi there, Alex.

You say you don't like the look of Lubuntu? Have a look at my take on it:-

[ATTACH=CONFIG]257180[/ATTACH]

You have to remember, that since all Linux distros ARE so customizable, the way it looks when you first install it is just the beginning.

This has all been achieved from the existing commands available in the bog-standard install.....with the exception of the wallpaper! That's my own work, as I have a long-standing interest in graphic design. Just wanted to show you what's possible. BTW, the 'dock' at the bottom CAN be put at the left or right-hand sides of the screen, if you want to..! OR the top, even; it's simply an adaptation of a second 'panel'.

@Bashing-Om; Sorry for butting in; having read this all the way through, I simply wanted to cheer young Alex up a bit, and show him just what CAN be achieved.....with the minimum of effort!

Regards,

Mike.

---

### Post by Bashing-om on 2014-10-13
@Mike_Walsh; Hey !

Appreciate the input - We are all in this together, there is no such condition as "butting in" with useful input !
( 30 years has to account for a lot )

@Alex_Eagle; Ya see ^^; you take what you are comfortable with, and make it what "you" want.  In 'buntu, there is no best; it is what works best for you.

I happen to have a preference to xfce because -> light, fast, clean and configurable !

[INDENT][INDENT]buntu;
[INDENT][INDENT][INDENT]if you do not like it
[INDENT][INDENT][INDENT][INDENT]do something about it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2014-10-13
Hi, Bashing-Om!

Nah, that's OK, man. I'm just an inveterate tweaker; I'm never satisfied with the way things look, and I'm always looking for ways to improve them; that's what a lifelong interest in graphic design does for you, I'm afraid. And yes, I suppose 30-odd years of playing around with these things MUST count for something.....

That's NOT a clever card young Alex has got there. Certainly, he would do far better with a 2D desktop manager; that thing is NEVER going to run Unity very well. But if the initial look of Lubuntu is what's putting him off, I just thought a demonstration of what can be achieved with a small amount of patience (and 'tweaking'!), might help him to look at it from a somewhat different perspective...

I know people who have 'top-end' systems, and yet have installed Lubuntu (with its quite low requirements) because it leaves them that much more in the way of system resources to do what THEY want to do; and as we ALL know, the OS is never a means in itself, but merely the support framework upon which we build everything else. The skill, of course, comes in making sure that the OS chosen will work with the hardware available!

Stay sharp!

Regards,

Mike.

---

### Post by Alex Eagle on 2014-10-14
Guys, no offence, but can we try and keep this a little clearer? You're starting to remind me of a gaggle of women around a watercooler ('scuse the sexism here :-P).

What I mean by, "I don't like the look of it", is more, "I don't like how it functions altogether". I'm not exactly a massive fan of xubuntu now I've got it, but hey! If it works and I learn to get used to it...

None of the options in Settings>Display have any alternatives, I'm running 640X480 and that's the only setting for res. :-/

I'm getting desperate. My parents are getting annoyed about how much time I spend trying to fix this. Please help as much as possible and try and speed things up. :-) Once again (especially Bashing-om) I appreciate your help.

P.S: Spellcheck doesn't work when I'm typing my answers on this forum?! I'm using WYSIWYG.

Thanks.

---

### Post by Mike_Walsh on 2014-10-14
Hi, Alex.

Sorry about that; we ARE getting a little off-course here!

I had the same problem in my ancient Dell Inspiron, when I first installed Lubuntu to that. It has the very old Intel Extreme Graphics chip from about 12 years ago; yes, some of us DO run ancient hardware.....in my case because I like rescuing old hardware that would otherwise go on the scrapheap.

Don't take exception to this; I don't know whether you tried it, but have you tried running it in 'nomodeset'? I appreciate that you originally wanted to do away with the native kernel drivers, as you thought that was where the problem lay. However, as I understand it (and I'm perfectly willing to be corrected on this), 'nomodeset' tells the kernel to ignore trying to run the graphics chip from the range of available drivers, and 'forces' it to run instead from the default driver. That way, you wouldn't be getting the conflict between the two, which I suspect is where part of your problem lies.

I don't think folk appreciate the sheer amount of work that must have gone into the Gallium & llvmpipe drivers, because they will give you a picture on just about everything you can think of. It may not be as sharp as you would like, but it WILL be usable.

I am certain the answer for your problem lies in Bashing-Om's post #4, to whit:-

[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

It specifically deals with the workaround for SIS cards, including yours. Unfortunately, you have to remember that you, like so many other people (including myself, just a few short months ago), find out that Linux isn't quite like Windows. In fact, it isn't a bit like Windows. And this problem of yours will not be solved by downloading something, running it, and.....'Hey presto!'; everything's OK with the world again. :shock: It WILL involve a little bit of 'getting your hands dirty'; but I think you will find that once it IS 'sorted', then that's it; it will remain 'sorted'. Unlike a certain Redmond-based company's offerings, where so often the very next update to come down the pipes ends up undoing all your hard work!

Regards,

Mike.

PS: If it is at all 'do-able', and you're able to bear with us, we will try and get your problem resolved. Some questions sit around on the forums for months, without ever being truly resolved; but a lot depends on whether you, the OP, does or doesn't mind wading through some unfamiliar territory for a short while. And if all else fails, and you 'break' your system, then you turn right around and re-install again; you know where the problem lies this time.....it's the only way to truly learn. Don't despair; Linux is remarkably easy to live with, once you get your system configured. And installation itself is a piece of cake too, compared to Windows. Hang in there! :p

And bear with Bashing-Om; he may appear to have a slightly unorthodox approach to problem-solving, but he always gets there in the end. I've had reason to be grateful to him myself in the past; the guy DOES know what he's doing, trust me..! He's not a Ubuntu member for nothing.....;)

---

### Post by Alex Eagle on 2014-10-14
Good answer. That surprises me, no I haven't run that command. And yeah, I realize that it's nothing like Windows. And I'm fully prepared to wade through viscous programming soup. I love it. It makes me grumpy and tired if I do to much but I still love doing it anyway. :-P

(Got a bit of a geek on your hands)

Will post again once I've had a look at that post again and tried that command in terminal.

I'd like to quote morgaes:
> 
Addition 2014-06-22: Cards not covered by the fix. 

If the command 
 	```
 sudo lshw -C video 
```


yields **661/741/760** or **662/761** then you are probably not reading the thread. All reports seem to indicate that the cards work right away in 14.04.

However, if the card is **771/671** then some modifications are necessary. The two options are 

[LIST=1]
[*]install Lubuntu 14.04 in low resolution, add updates and create an xorg.conf, as described later in the thread, or
[*]install a 12.04-based distro with support like Bodhi Linux or LXLE, both of which are supported through 2017.
[/LIST]


```
 sudo lshw -C video 
``` does yield **771/671.** So,... what?

Terminal said it couldn't find the nomodeset command. This happens a lot with my notebook. It turns out that somebody on that other thread had a V5535 like me. :-/

But most of what was posted, as I've said to Bashing-om, went right over my head. I may be a geek but I'm still only 14. I'm still learning. And this is pretty advanced for me. Do you think I should create a xorg.conf? Also, details - **in this thread **- on how to create one would be helpful. Instead of me having to source the instructions elsewhere. 

:-) Be patient.

---

### Post by Mike_Walsh on 2014-10-14
Alex.

In the middle of cooking dinner at mo; will get back to you later. If Bashing comes on in that time, ask him about adding 'nomodeset' to /etc/default/grub; he'll know what I'm talking about. It's definitely worth a try.

Catch you in a bit!

Regards,

Mike.

---

### Post by Alex Eagle on 2014-10-14
Hope it goes well :-) Will do.

---

### Post by Elfy on 2014-10-14
If you want to add nomodeset you need to edit the grub default file and update it.

Backup the file first in a terminal

```
sudo cp /etc/default/grub /etc/default/grub.1410
```

then open for editing

```
gksudo gedit /etc/default/grub
```

If you get a fail with gksudo missing, try using pkexec

```
pkexec gedit /etc/default/grub
```

Find the line which looks like

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and add nomodeset

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

Then close and save.

Now update grub

```
sudo update-grub
```

---

### Post by Alex Eagle on 2014-10-14
@Mike_Walsh It's good to find somebody else from the UK BTW. The internet is dominated by Americans and it's nice to find somebody who's part of the British way of life. :-) No offence but it's odd virtually talking to foreigners when you don't even live in the foreign country.

Done that. But terminal came up with a fail after I saved the file. Although it seems to have retained the nomodeset part so I think it's worked?

I presume a regular restart will activate the changes.

---

### Post by Elfy on 2014-10-14
> **Alex_Eagle said:**
> ... But terminal came up with a fail after I saved the file....
I presume a regular restart will activate the changes.

What sort of fail? 

Yes.

---

### Post by Alex Eagle on 2014-10-14
Sorry, didin't explain that. Thought there might only be one type of fail possible, hence no explanation needed. I reverted the gedit file and then put the nomodeset bit back again. The error showed up twice.

```
 (gedit:2252): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


```

---

### Post by Elfy on 2014-10-14
aah - gtk warnings - you'll get used to those in a terminal :)

---

### Post by Bashing-om on 2014-10-14
Alex_Eagle; Hello;

OK, I am back on ...
Lot's of great help you have here !
The advisory is but a "warning' and can be safely ignored. Carry on.

OK did the edit to " /etc/default/grub " take  ?
```

cat /etc/default/grub

```

and if so - do you now have a usable display ?
Do you want to look and see what driver is loaded ?
```

sudo lshw -C display

```

As you decline to take the easy solution and install/ use/configure (L)ubuntu, then that entails a LOT of extra effort to find an alternate solution. How many of us run SIS graphics and that particular version .. not many and the experience is limited .. WE may be the ones to blaze a trail. And yes I can foresee that we may indeed end up learning a lot about " /etc/X11/xorg.conf " . If, in the end we determine that is what it takes, well, that is what it takes ! - A very steep learning curve here - 

We will not be able to make any determinations for a solution until it is decided on the Desktop Environment you are going to use . The files to access/edit are different one DE to another. I presently have but limited access to my (L)ubuntu install - ( rethinking my booting arrangement ) limiting the advise I may offer .

So again, get our feet planted on a firm foundation
[INDENT][INDENT][INDENT][INDENT]and push !
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2014-10-14
> **Alex_Eagle said:**
> @Mike_Walsh It's good to find somebody else from the UK BTW. The internet is dominated by Americans and it's nice to find somebody who's part of the British way of life. :-) No offence but it's odd virtually talking to foreigners when you don't even live in the foreign country.

Hi again, Alex.

Oh, you'd be surprised; there's a lot of folk on here from the UK. Elfy is for a start.....and coffee_cat (both forum staff); westie457, who posted a bit earlier, is; grahammechanical's from London.....AJ_Greeny's also from the UK. You can take advice from these guys and run with it it all the way to the bank.....they DO know what they're talking about. Many have been here since the start of the forums, 10 yrs ago..!

And don't turn yr nose up at advice from some of the 'foreigners'..! Bashing-Om might be from 'hill-billy' country in the US, but he's one of the 'good guys' for sure. :p Dennis N's another one; there's score's of others, but I just can't think of them off the top of my head..... You'll find they're a thoroughly decent bunch on here; yes, there's the usual percentage of 'nurks' on here, too, but you'll get that wherever you go.

Just remember one thing, and you'll not go far wrong. We're ALL ordinary 'users' on here, just like you; some less experienced, at least as far as Linux goes (like me).....many far more so. But we all come on here as and when we get time, and have a look to see if there's anything we can help with..... Point being, you might just have to be patient sometimes; but there's usually **somebody** on who can help in some respect or another....OK?

One last thing; if you get any major system problems, grahammechanical and/or old_fred between them will almost certainly put you on the right track. The pair of them have got unrivalled knowledge of system operation and boot/startup procedures; if they can't sort you out, I doubt anybody can!! ;)

And to answer your point from earlier, the reason we use links on here as much as we do, is because it's a pain in the rear constantly copying & pasting from one thread to another; it's the time factor again...

Regards,

Mike.

---

### Post by Alex Eagle on 2014-10-14
Lol. It's not the advice or their trusty worthiness I'm worried about, in fact, I'm not worried about anything. It's just nice to be able to talk to a Brit who's mind works like mine more so than an American. And yes I'm aware that graham is **very **experienced.

Night all!

---

### Post by Bashing-om on 2014-10-14
Alex; Hey;

I am presently awaiting your response to my pot #78.
See if the grub edit "took" and of interest is to see what driver is loaded.

patience is a virtue

---

### Post by Mike_Walsh on 2014-10-14
Hey, Bashing.

I think you'll find he's got his head down for the night. You've got to remember, he's only 14....got school in the morning! ;)

Regards,

Mike.

---

### Post by Bashing-om on 2014-10-14
Mike_Walsh; Yepper !

Homework to get done before being able to focus on this issue.
And he is 6 hours ahead of me.

However, all
[INDENT][INDENT]between us we will whoop this out
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-15
The first lot of code returned:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
  
```

Graphics still haywire. Can only get three tabs in Firefox before they start to squish. And half of the skype logon screen is missing. The seccond lot of code returned:
```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d4000000-d401ffff ioport:9000(size=128) 
```

:-/ Hmmm. No better is it?

Actually, pretty much, err, no. I'm home educated and am sometimes able to persuade mum to count it as IT lessons. Dad wouldn't let me but he's out at work! :-P But yeah I was asleep. Lolz Bashing. XD ROFL

---

### Post by Bashing-om on 2014-10-15
Alex_Eagle; Hey, hey :

My top o' the morning to you .

OK the edit to " /etc/default/grub " took and is good. After this edit did you do in terminal:
```

sudo update-grub

```
To propagate the change to the rest of the system ?

We presently have NO graphics driver loaded ! Per:
> 
*-display UNCLAIMED
<snip>
configuration: latency=0


Is there anything "blacklisted" that will prevent loading a driver ?
```

ls -al /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/blacklist-framebuffer.conf
cat /etc/modprobe.d/fbdev-blacklist.conf

```

We make this an exercise in reasoning and the power of cognitive thinking.

Tell us once more what version and DeskTop you have installed. Then we can see what we can do about this situation.

[INDENT]let the work begin
[/INDENT]

---

### Post by Alex Eagle on 2014-10-15
I have 14.04 LTS (32bit) XFCE DE.

Yes I updated grub. The second lot of code returned:
```
 total 64
drwxr-xr-x   2 root root  4096 Sep 18 09:18 .
drwxr-xr-x 144 root root 12288 Oct 15 16:56 ..
-rw-r--r--   1 root root  2507 Feb 13  2013 alsa-base.conf
-rw-r--r--   1 root root   325 Apr 10  2014 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Apr 10  2014 blacklist.conf
-rw-r--r--   1 root root   210 Apr 10  2014 blacklist-firewire.conf
-rw-r--r--   1 root root   677 Apr 10  2014 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Feb 13  2013 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 Sep  5 14:11 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Apr 10  2014 blacklist-rare-network.conf
-rw-r--r--   1 root root  1077 Apr 10  2014 blacklist-watchdog.conf
-rw-r--r--   1 root root   456 Apr 14  2014 fbdev-blacklist.conf
-rw-r--r--   1 root root   347 Apr 10  2014 iwlwifi.conf
-rw-r--r--   1 root root   104 Apr 10  2014 mlx4.conf
-rw-r--r--   1 root root    30 Apr 10  2014 vmwgfx-fbdev.conf
rasphack@Alexs-Coding-Machine:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
rasphack@Alexs-Coding-Machine:~$ cat /etc/modprobe.d/blacklist-framebuffer.conf
# Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
blacklist lxfb
blacklist matroxfb_base
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist rivafb
blacklist s1d13xxxfb
blacklist savagefb
blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
#blacklist vesafb
blacklist vfb
blacklist viafb
blacklist vt8623fb
blacklist udlfb
rasphack@Alexs-Coding-Machine:~$ cat /etc/modprobe.d/fbdev-blacklist.conf
# This file blacklists most old-style PCI framebuffer drivers.

blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

```

Don't know if I've posted a little too much. The last line was left after the ~ so I pressed enter and it spat out a load more. Hope it's ok.

Might it be my bit version? I seem to remember that windows was 64bit. :-/

---

### Post by Bashing-om on 2014-10-15
Alex_Eagle; Well;

As to 32/64 bit versions, you will get better performance with the 32 bit version as you have less than 4 Gigs of ram. ( the overhead of addressing 64 bits ).

Let me have a bit of time to test here on my box, so far all looks 'normal', but, we have:
> 
/etc/modprobe.d/blacklist-framebuffer.conf -> blacklist sisfb
/etc/modprobe.d/fbdev-blacklist.conf -> blacklist sisfb


I will be back soonest I am able, and we consider putting " sisfb " back in service.
[INDENT][INDENT]won't hurt to try
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-15
Thanks dude. This is no rush BTW. I'd like to get it working ASAP but it's not urgent. Well I installed the 32bit knowing it would probably be less demanding on my hardware but I only just realized that the might be a very small chance of incompatibility. Your solution sounds good. 

Sorry to bug you about this but what do you think to creating a xorg.conf? :-)

---

### Post by Bashing-om on 2014-10-15
Alex ; Hey

Like this:
> 
Sorry to bug you about this but what do you think to creating a xorg.conf?

I say again, it is probably what we will wind up doing. I have little experience in making one up so we will "tread lightly" when we do get to that point.
But let us explore other avenues 1st .. as it is my concern that if we employ the " xorg.conf " file, updates may break it .

[INDENT][INDENT]more than one path to an end
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-15
Alex; Hey, hey ;

I am back from testing, and ->
The use of "nomodeset" does prevent the loading of any system driver !

So, let's 
a) Remove that boot parameter "nomodeset" from " /etc/default/grub " file ( you did make a backup, yes - so we do not have to fret if there is a problem occurring now ) and once the change has been made
```

sudo update-grub

```
b) Let's UN-blacklist the sisfb drivers in the file(s) " /etc/modprobe.d/blacklist-framebuffer.conf " and " /etc/modprobe.d/fbdev-blacklist.conf  "; one at a time !
```

sudo cp /etc/modprobe.d/blacklist-framebuffer.conf /etc/modprobe.d/blacklist-framebuffer.conf-orig
gksudo gedit /etc/modprobe.d/blacklist-framebuffer.conf

```
The file is open in the text editor, arrow down to the " blacklist sisfb " entry and place a '#' character at the start of the entry. This causes the line to not be parsed such that the driver is no longer blacklisted.
Reboot at this time - nomoeset is no longer in effect and sisfb in this file is enabled - let's see the effect. 
OK, no change . ->
c) repeat the procedure for the file " /etc/modprobe.d/fbdev-blacklist.conf " .

Now what condition is the condition in ?

Do we now consider making up the " xorg.conf " file ? Any other's thoughts on this matter are welcome.
---------------------------------
off topic: I got my chain saw to start - cool this AM -. am going to work on compiling my Winter's fire wood. I will be back on here in a few hours to check on your progress.
-------------------------------

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-15
First line didn't work. It returned:
```
 cp: cannot stat ‘etc/modprobe.d/blacklist-framebuffer.conf’: No such file or directory 
```
But the second line enabled me to edit the file.

And by >  OK, no change . ->
c) repeat the procedure for the file " /etc/modprobe.d/fbdev-blacklist.conf " . 
Do you mean the "etc/modprobe.d/blacklist-framebuffer.conf" file or what. I'm unsure as to what file you mean so please try and make it as clear as possible.

Thanks.

P.S: Going to restart now...

@Bashing-om
Forget that. I replaced the second filename you suggested with the original. Stuff is still batty as I keep on describing ("all blown out of preportion" and so on...)

To xorg.conf now?

---

### Post by Bashing-om on 2014-10-15
Alex; Typo !

On my part. corrected.
should have had a leading '/' .. must have missed it when I copy/pasted .
```

sudo cp /etc/modprobe.d/blacklist-framebuffer.conf /etc/modprobe.d/blacklist-framebuffer.conf-orig
sudo cp /etc/modprobe.d/fbdev-blacklist.conf /etc/modprobe.d/fbdev-blacklist.conf-orig

```

Text editor and comment out "blacklist sisfb"  in both files, and with "nomedset" NOT set; reboot.
Graphics still no good ..
Then revert the change ( remove the '#" ) and save the file.
Then yeah let's look to building an xorg.cong file.

1st, though. let's check what resolutions the monitor supports - we do not want to overdrive the monitor !

Reboot again to the grub boot menu, 'c' key for a command line.
Post back the output of terminal command:
```

vbeinfo

``` and we see what we have to work with.
As you will not have the convenience of the GUI, can not copy and paste... hand write - carefully - and then reboot into the install to get to your browser to relay.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2014-10-15
Hiya, Bashing! 

Been out with friends most of the day, and only just got in. Anything I can help with?

Sorry about the 'nomodeset' thing; I know it used to be in morgaes' thread on bringing old hardware back to life, but it seems to have been edited out recently. I only mentioned it because it worked on my ol' brick of a Dell Inspiron that's about 12 years old. It uses the horrible old Intel 'Extreme' graphics chipset (the 82845G/GE/GL/PE/PV) that they foisted onto the market back in 2002.....dreadful thing it is!

I suggested Alex ask you about it last night because I couldn't remember off the top of my head quite where the /etc/default/grub file was located...! :oops:

(There ARE drivers available for the 'Extreme' chipset, but the installation instructions are THAT complex, I reckon they'd make even you cringe!)

As you saw, Elfy stepped into the breach and helped out with that one; but my 'suggestion' appears to have jammed a BIG ol' spanner 'in the works', does it not? Apologies for that; but from the way things are currently going, ANYthing's worth a try at the moment...! ;)

Regards,

Mike.

BTW: I'm quite happy to 'back off' if you like.....I may be 'hindering' more than 'helping'. Shan't take offence!

---

### Post by Bashing-om on 2014-10-15
@Mike, Hey;

I can use all the help and ideas anyone can come up with .. try'n "nomodeset" is a great idea and in many cases is useful .

Like I have advised I have no experience with the SIS graphics, and but limited exposure, Flying by the seat of out pants and can use all the directional aids we can come up with.

I am aware that some have had good results when the " xorg.conf " file is implemented, running the SIS graphics . Won't hurt a thing to try it and see,
Once we know what it will take to build it.

I am pretty well disconcerted that 'xrandr' only returns that one minimal resolution. Can't imagine the why ! Hopefully 'vbeinfo' will provide substantial info.

With enough people watching our backs, maybe we will not goof up too bad !


When you don't succeed 
[INDENT][INDENT][INDENT]try try again ( sky diving excepted )[/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2014-10-15
Bashing:

Just been having a browse around t'internet; came across [this]("http://www.pclinuxos.com/forum/index.php?topic=126613.0") on the PCLinuxOS forums. I have no NO idea if it'll help or not (you have a much more 'intimate' understanding of the guts of the system than I do, that's clear!), but there are mentions of 'xrandr' AND an 'xorg.conf file'.....also something to do with the vesa drivers? Have a look and see if it gives you any clues... It MAY give you some 'pointers'...[-o<

The OP is ALSO (*sigh*) using a Fujitsu Siemens setup...!! :-({|= Surprise, surprise....

Regards,

Mike.

---

### Post by Alex Eagle on 2014-10-15
Just to be extra clear: I take out nomodeset, try agin and if the doesn't work take out the #'s from both files?

P.S: Can't do anything ATM, am supposed to be asleep and am posting from my kindle :-P naughty! *hand slap*

---

### Post by westie457 on 2014-10-15
@Bashing-om, whilst pondering this issue and searching t'internet I also found the same link posted by Mike_Walsh and this  [http://askubuntu.com/questions/59621/how-to-change-the-monitors-refresh-rate](http://askubuntu.com/questions/59621/how-to-change-the-monitors-refresh-rate)
Then I remembered that some years ago I had an issue with a graphics card (might have been a SIS card) where the display was off-centre. Changing the resolution did not help however changing the 'refresh rate' from the default -50Hz to 60Hz and then 75 Hz brought everything back into line.

Changing the refresh rate is not an option in Ubuntu without the risks of using ccsm. However in Lubuntu and Xubuntu it is possible to make some changes.

BTW This issue for me was on Windows upgrading from '98 to XP.

---

### Post by Mike_Walsh on 2014-10-15
> **westie457 said:**
> @Bashing-om, whilst pondering this issue and searching t'internet I also found the same link posted by Mike_Walsh and this  [http://askubuntu.com/questions/59621/how-to-change-the-monitors-refresh-rate](http://askubuntu.com/questions/59621/how-to-change-the-monitors-refresh-rate)
Then I remembered that some years ago I had an issue with a graphics card (might have been a SIS card) where the display was off-centre. Changing the resolution did not help however changing the 'refresh rate' from the default -50Hz to 60Hz and then 75 Hz brought everything back into line.

Changing the refresh rate is not an option in Ubuntu without the risks of using ccsm. However in Lubuntu and Xubuntu it is possible to make some changes.

BTW This issue for me was on Windows upgrading from '98 to XP.

Hey there, Westie.

That is something I never even considered, I must admit. Of course, if you're using a desktop setup, like me, that's easy enough to adjust via the built-in monitor controls; but I haven't got an inkling as to how you would do that on a lappie.....much less under Linux. Is it possible to do that with CCSM? The extent of my usage of it boils down to altering the number of workspaces I have (I'm currently using six.....an avid graphic artist, y'see.....and it's SO much simpler having one app open per window!), and also the minimize to launcher tweak.

I simply haven't investigated further.....despite being an inveterate 'tweaker'!

Regards,

Mike.;)

---

### Post by westie457 on 2014-10-15
Hopefully this screenshot of Xubuntu LiveCD shows enough info. Also this Xubuntu is in a VM on a lappie so choices are limited.

Using CCSM has its own risks. Tried it around 2 yrs ago. Took me about 30 seconds to accidentally destroy the system enough to need a re-install.

---

### Post by Mike_Walsh on 2014-10-15
> **westie457 said:**
> Using CCSM has its own risks. Tried it around 2 yrs ago. Took me about 30 seconds to accidentally destroy the system enough to need a re-install.

Easily done..!

That's why I've been very careful with using it myself; including reading and watching scores of blogs and videos before I even opened it for the first time.....

Regards,

Mike.

---

### Post by Bashing-om on 2014-10-15
Guys all;

Here is my thoughts. With 14.04 we have a new xserver, and patched sis graphics drivers - except for ours " Silicon Integrated Systems [SiS] 771/671 PCIE  ".
In 14.04 we no longer have a vesa driver, have gone now to gallium/llvmpipe.; and vesa - from what I have gathered does not support higher resolutions.
Does the system recognize that the sis driver is installed ?
```

apt-cache show xserver-xorg-video-sis

```
IF so -- AND that might be a big if ->
Let's see what we can do with an xorg.conf file :
make up the file:
```

sudo touch /etc/X11/xorg.conf 

```
Copy and paste this into the touched file:
```

Section "Device"
        Identifier "Configured Video Device"
        Option "NoAccel" "true"
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
EndSection

```
Trying as simple as possible and letting the system find/set the defaults.

Reboot and let's see the effect.

[INDENT][INDENT]it just a thought
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-15
First of all, I don't think I'm using it in VM. It's fully installed onto my harddrive. Unless I misunderstand the meaning of VM.

Second, could I use windows to find what driver it uses? Win seems to work around it itself, whereas buntu doesn't seem to have been programmed to. Just a thought.

The first lot of code returned:
```
 Package: xserver-xorg-video-sis
Priority: optional
Section: x11
Installed-Size: 640
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: i386
Version: 1:0.10.7-0ubuntu6
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-sis
Provides: xorg-driver-video, xserver-xorg-video-
Depends: libc6 (>= 2.7), xorg-video-abi-15, xserver-xorg-core (>= 2:1.14.99.902)
Conflicts: xserver-xorg-driver-sis
Filename: pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.10.7-0ubuntu6_i386.deb
Size: 224774
MD5sum: 6690e9fcffa3312230f75f0527961097
SHA1: 663b9b043a9b74ee2ee83d6eed2f7f0c6fda3afb
SHA256: e6326f8006c5df30a19a97f52fb229a4b0b0d2a3a354b9e8164974e8d20406fe
Description-en: X.Org X server -- SiS display driver
 This package provides the driver for all SiS and XGI Volari cards.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xf86-video-sis driver module.
Description-md5: 42dac6b9768ebbc736ea67fc56bc1813
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-active, kubuntu-active-desktop, kubuntu-active, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-core, ubuntustudio-desktop, ubuntu-gnome-desktop

```

Don't know if it's good or bad news... :-/

---

### Post by Bashing-om on 2014-10-16
Alex; Humm...

!st things first, this:
> 
Second, could I use windows to find what driver it uses? Win seems to work around it itself, whereas buntu doesn't seem to have been programmed to. Just a thought.

Do not go think'n Windows, this is not Windows. Most of the time the kernel takes care of all drivers. It is a rarity that one must intervene as in this case. In your case we are still going to "fix" this with out having to go looking for some strange driver. And yeah, that hardware works fine in Windows, the Windows does have a driver that the manufacturer provided to run in Windows; the manufacturer did not make one to run in linux .. We must make our own .. and so the developers have ! Just that the developed driver is not compatible with your chip set ! Thus we have to give the kernel a helping hand.

We do not know yet how much help the kernel needs. 


Don't know enough yet ! Per:
> 
 Package: xserver-xorg-video-sis
<snip>
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-sis

Provides: xorg-driver-video, xserver-xorg-video-
<snip>
Conflicts: xserver-xorg-driver-sis
<snip>
Description-en: X.Org X server -- SiS display driver
 This package provides the driver for all SiS and XGI Volari cards.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xf86-video-sis driver module.


SO: Let's see where we stand, and what options we can make for ourselves .
Post back:
```

cat /etc/default/grub
cat /etc/modprobe.d/blacklist-framebuffer.conf
cat /etc/modprobe.d/fbdev-blacklist.conf
dpkg -l xserver-xorg-video-sis
dpkg -l xserver-xorg
dpkg -l xserver-xorg-driver-sis

```
and we have an idea of what to expect with building and implementing the " xorg " file.

Which IF "nomodeset" and the blacking listing were removed, and still with resolution problems .. is our next step -> " xorg.conf " .

[INDENT][INDENT]it is a process of learning
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-17
```
  cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
rasphack@Alexs-Coding-Machine:~$ cat /etc/modprobe.d/blacklist-framebuffer.conf
# Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
blacklist lxfb
blacklist matroxfb_base
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist rivafb
blacklist s1d13xxxfb
blacklist savagefb
#blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
#blacklist vesafb
blacklist vfb
blacklist viafb
blacklist vt8623fb
blacklist udlfb
rasphack@Alexs-Coding-Machine:~$ cat /etc/modprobe.d/fbdev-blacklist.conf
# This file blacklists most old-style PCI framebuffer drivers.

blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
#blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb
rasphack@Alexs-Coding-Machine:~$ dpkg -l xserver-xorg-video-sis
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  xserver-xorg-v 1:0.10.7-0ub i386         X.Org X server -- SiS display dri
rasphack@Alexs-Coding-Machine:~$ dpkg -l xserver-xorg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  xserver-xorg   1:7.7+1ubunt i386         X.Org X server
rasphack@Alexs-Coding-Machine:~$ dpkg -l xserver-xorg-driver-sis
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  xserver-xorg-d <none>       <none>       (no description available)

```

Is the conflict halfway through the list of code that you post a good thing or not? I presume not but I don't know what most of it means. I'm brilliant with windows and can fix almost anything, but I'm a complete newbie to linux.

---

### Post by Bashing-om on 2014-10-17
Alex ; Hello ...

You are wise to question, the best way to learn:
> 
Is the conflict halfway through the list of code that you post a good thing or not? I presume not but I don't know what most of it means.

IF the package were installed, then yes it would be a bad thing .. but ! it is not, per:
> 
[color=green]un[/color]  xserver-xorg-d

Further more, we know that the proper driver is installed:
> 
[color=green]ii[/color]  xserver-xorg-v 1:0.10.7-0ub i386 

We know this from the heading information: 
"Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend "
where U = unknown ( the package manager is not tracking ) ; i = installed -  in that 1st line for 1st character
where n = Not installed ; i = Installed - in that 2nd line  for the 2nd character
----------------------------------
OK, still to be done is to remove the '#' character in the 2 files that earlier we had placed.
With your text editor, and then save the files.
> 
/etc/modprobe.d/blacklist-framebuffer.conf -> #blacklist sisfb , #blacklist vesafb
/etc/modprobe.d/fbdev-blacklist.conf -> #blacklist sisfb

That puts the files back to default.

----------------------------------
I think it is then - with all back to defaults - time to try the system performance with the addition of the " xorg.conf " file.
See what results and IF/What modifications are to be done.

[INDENT][INDENT]maybe a big step forward
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-17
Oops. Posted twice :-P

Gentlemen, I direct you to[ a new thread of mine]("http://ubuntuforums.org/showthread.php?t=2248851"). It's about choosing a new laptop. I'm still trying to save the current V5535, but a new one's go to be bought at some point. 

Will come back to you on your post @Bashing.

---

### Post by Bashing-om on 2014-10-17
Alex ->

K

---

### Post by Alex Eagle on 2014-10-17
Unblacklisted the lines now. So, now what?

---

### Post by Bashing-om on 2014-10-17
Alex:
Post #104 .
Touch to create the file
copy and paste to populate the file with the contents provided.

Reboot, and let's see the effect.

[INDENT][INDENT]It could happen
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-18
Touch isn't working. It asks for my password and then does nothing when I hit enter.

**EDIT:**
I used the gksudo gedit version of the command you gave me in #104. The gksudo is mentioned in post #92. It's now saved sucsessfully. In the future please use gksudo because the other one doesn't work. :-) Going to restart now.

**POST-RESTART EDIT: **Still the same loopy graphics.

---

### Post by Bashing-om on 2014-10-18
Alex: Humm !!

Let's look at what we are working with now:
post back:
```

cat /etc/X11/xorg.conf 

```

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-18
Section "Device"
        Identifier "Configured Video Device"
        Option "NoAccel" "true"
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
EndSection

---

### Post by Bashing-om on 2014-10-18
Alex_Eagle; Sheesshh ..

The config file is in place.
Did the driver load ?
Post back:
```

sudo lshw -C display

```
and let's see

[INDENT][INDENT][INDENT]what tale gets told
[/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-18
```
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d4000000-d401ffff ioport:9000(size=128) 
```

Can we somehow "claim" the display?

---

### Post by Bashing-om on 2014-10-18
Alex_Eagle; Yeah ...

The tale is told, and we still have no graphics driver loaded .. I do not know the why !
I had expected the xorg file to do our work for us ..

Let me do some homework, and figure out why the driver is not loaded, and what we can do.

In the meantime:
[http://askubuntu.com/questions/455888/low-resolution-on-lubuntu-14-04-sis](http://askubuntu.com/questions/455888/low-resolution-on-lubuntu-14-04-sis)
try this and see, - I do not know; as I was under the impression that "vesa" was no longer an option.
Won't hurt to try it and see what results.
Remove what we have now to implement the new config file.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-test

```


[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-20
No such file or dir... :-/

---

### Post by Bashing-om on 2014-10-20
Alex; uh,

> **Alex_Eagle said:**
> No such file or dir... :-/

That tells us nothing, as there is no point of context in the statement. What file ? -> /etc/X11/xorg.conf ? ; /usr/share/X11/xorg.conf.d/use-vesa.conf ?
Where are you at, and what are you doing ?

It will be interesting to see the results of creating the " use-vesa.conf  file.

All we want to do is load a SIS driver.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-10-21
That's what Bashing's code returned. I don't know why it's done that but it has, I need you to tell me how to get round it.

P.S: Do you know of a chart showing what comment your profile shows when you get "so many" beans? E.g: right now my comment is "Just Give Me the Beans!". I wouldn't have thought there is a chart but it's worth a butchers.

I wonder if we'll reach 150 posts on this thread? And on the same point, what's the longest thread you've ever seen on ubuntuforums? And it can't have been posted by an admin member or anyone with a title on this forum.

I'd like an answer from anyone who has anything interesting to say about it. :-) Thanks.

Any updates people? :-)

Helloooooooo?

Anyone there? Are there developments ahead?

Hi guys. Have a look at [this]("http://ubuntuforums.org/showthread.php?t=2215422&p=13157566#post13157566").

Worth a go? I know it doesn't apply to my res but... Could it work?

P.S: Could just running ```
X -configure
``` work?

Please respond guys!

I tried to install FlightGear, despite my still-dodgy-graphics, and that  somehow destroyed ubuntu. I re-installed using a boot disk and during set-up everything looked ok. But after reboot the graphics were all crackers again. Obviously I don't have the XFCE DE now, so if I need it in order to fix this just tell me. I just thought this might help diagnose. :-)

---

### Post by Bashing-om on 2014-11-07
Alex: Hey,

I am still awaiting a response from my post #105.
We do need to know IF there is presently a control file in effect
Is either:
/etc/X11/xorg.conf
/usr/share/X11/xorg.conf.d/use-vesa.conf
active at this time ?

Have you tried:
[http://askubuntu.com/questions/455888/low-resolution-on-lubuntu-14-04-sis](http://askubuntu.com/questions/455888/low-resolution-on-lubuntu-14-04-sis)

[INDENT][INDENT]beyond a reasonable doubt
[INDENT][INDENT][INDENT]we will implement a control file
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-09
No I haven't got either of those files. Should I try out the thread on "ask!"?

---

### Post by Bashing-om on 2014-11-09
Alex: sure !

> 
No I haven't got either of those files. Should I try out the thread on "ask!"?

Try and see if it works, can always be reverted if it does not work OR get some additional info to aid in getting a config to work.

[INDENT][INDENT]if at 1st you do not succeed
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-11
Ok Bashing, I'll do that.

Just to inform y'all, mum was shoping on eBay (y'know, how they do), and the screen was flipping between black&white - like an old movie - and colour. Don't know what on earth was going on and I didn't get to see it. What I heard from mum is that it flipped several times and suddenly fixed itself. I'll update this post if it happens again today. Hope that might help with something. :-)

WOW BASHING!!!!!!!!! IT WORKED!!!!!!!
[ATTACH=CONFIG]257886[/ATTACH]

Just one thing, everything's a bit slow now. Would there be a way to cut some corners with the driver so that there's not so much refering to the driver by the system? Or could I set an overclock? You don't have to explain the overclocking, I should be able to find an explanation elsewhere, I don't want to overcrowd this thread!

On that subject, what's the longest thread you've ever seen? And that question goes to all who read this thread, not just Bashing. Remember this thread is now 112 posts long and 12 pages with my settings.


So, credit to Bashing-om, may he reap 1000 beans every day of his 'buntu life. :p ;)

**UPDATE:** Some graphics are still weird. It's not perfect. I have to have eBay on 90% zoom and other pages 100% but sometimes only 75%. Is there another driver I could try out? I'm extremely grateful, but I'd forever be in your debt if you could find a driver that works perfectly (if such a driver exists!). Don't put everything into it, I not really that bothered that that the no-longer-craptop is any better than it is now. But if it'd be easy to find please let me know.

Also, do you think removing Windows would speed it up a bit? I know it's taking up a fair bit of HDD space.

Thanks! :-)

---

### Post by Bashing-om on 2014-11-11
Alex' Great !

We are making progress ! And yeah, might be able to do some tweaking with the config file.
Post back the contents of the present config file, and we can consider what/where changes to make.

-------------------
Off topic: Does not matter how long of a post we make ( and I have participated in longer ); all that matters is that there is a solution arrived at.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT]time and effort, all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2014-11-11
Heya, Bashing..!

I KNEW you'd get there in the end, old son. Well done; it's all just part of that long old learning curve, ain't it?

Congratulations! (I'll bet it's added a few grey hairs, though.....hmmm??)

Regards,

Mike. =d>

---

### Post by Bashing-om on 2014-11-11
@ Mike_Walsh; Hey hey !

Nawww, mörgæs has already done the leg work, just follow his lead.

[INDENT][INDENT]now he be a stepper
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-12
Right, check back on this post later in the day and I'll have updated it to contain the config file.

I know it's not about how long it is lol! :-P (could mean something entirely different) But it's a pretty amazing thread.

Thanks a lot guys. I'm so thrilled to have it working (almost) how it should. The only times it's looked right are when it was on windows, which looks _different_ to linux/'buntu, and when I tried 'buntu first time (13.03 I think, or possibly 12.02) and I can't remember what it looked like then. Strangely, on 12.02 or 13.03 - whichever it was - I couldn't install anything because I "held broken packages"?! Really annoying. I tried to reinstall but that didn't help. Couldn't find any answers on the net, so I gave up. But 14.04 seems to work ok.

Bashing, just to clarify exactly which file is it I'm looking for? Is it the xorg.conf.d, and I presume that you want the content of the text file, not the folder?

I've got a few "config" files flying around, there's a compiz.config, a pppconfig, a pkg-config... Just wanted to be sure. Will post contents in a new post intsead of editing an old post.

P.S: Should I unmark this thread as solved?

P.P.S: I've now got a res of 1024x768. Thought you'd like to know. :-)

---

### Post by Bashing-om on 2014-11-12
Alex: yep;

You have the right of it:
> 
Bashing, just to clarify exactly which file is it I'm looking for? Is it the xorg.conf.d, and I presume that you want the content of the text file, not the folder?


The file I expect us to presently be working with:
```

cat  /usr/share/X11/xorg.conf.d/use-vesa.conf

```
And relate to us once more the problems you are experiencing, to focus our attention.

[INDENT][INDENT]won't know 'till we try
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-12
```
Section "Device"
  Identifier "Configured Video Device"
  Driver "vesa"
EndSection
```
Active windows sometimes fade to black&white, I've now witnessed it myself. It happens every time I open the software centre. I've realized it's usually when windows are not responding.

Some things are still a bit glitchy. For example, I play on a particular game, where you sign in (or up) and then play on a dedicated URL just for the game window. The whole of the sign in page can only be seen fully at 67% (I think - don't quote me!) but the game window is ok at 100%, as it should be. Gmail (the desktop app) doesn't look how it should unless maximized. 

And that's it. Of what I can remember anyway! I'll post screenshots ASAP.

Night all!

---

### Post by Bashing-om on 2014-11-13
Alex; Hey;

Think'n .. maybe we will have better results ( as good as this one is ) if we create the /etc/X11/Xorg.conf.
No big deal to move the current file out of the way and see what results with a Xorg.conf file.

What are your thoughts ?


[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT][INDENT]try try again ( sky diving excepted )
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-14
Nice little sign-off there!

I don't know do I?! Lol. I've no idea bashing, whatever you say goes... If you think it'll work I'll do it! I'm really sorry but I still am not fully comprehending all the details regarding this problem. I've have medium understanding at best, I cannot advise **you** on what to do!

P.S: Can one of you (someone understanding basics of Wine) check out [a new thread of mine]("http://ubuntuforums.org/showthread.php?t=2252750")? And also I still need help with my mic problems. Thanks.

FYI I found a thread (unsurprisingly started by morgaes) which was over 100 pages long I think. Just thought I'd let you know. :-)

---

### Post by Bashing-om on 2014-11-14
Alex; Like this:

I do not run SIS graphics, and have no direct experience with the chip set. 
It is your system, your time and your effort and depends on how much effort you are able and willing to expend . The learning curve may be steep, and perhaps a learning experience for all of us.

But, if it were me I would invest in the time to make up the Xorg.conf file and see what results. Give me some time and I will hunt up something we can start with. We know for sure that we must tell the kernel what it needs to know, it is now a matter of finding out what the kernel needs to know and how to tell the kernel.

[INDENT][INDENT]advancing on that curve of learning
[INDENT][INDENT][INDENT]sometimes, in bigger steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-15
Aah! I see. The question was more, have I got the time than do I object to doing "such-and-such" to my laptop. I have time to do whatever :-P . Whatever it is I'm doing I don't know! lol

Right. So, tell me what I need to do. I think I need to temporarily make that vesa file obsolete somehow and create an xorg.conf and put something in it. How do I do that if it is what I'm supposed to do?

:-) Thanks.

---

### Post by Mike_Walsh on 2014-11-15
Morning, Alex.

Now then; what was it you wanted advice with? 'Wine', I think you said? This isn't exactly the thread for that...

Regards,

Mike.

---

### Post by Alex Eagle on 2014-11-15
Yeah I know it's not really to do with this (maybe) but it depends. I mention Wine because I think that **might** be why my PC's running slow. But it might be something to do with the fact that I've upgraded to Utopic, the vesa driver, or something else entirely.

Thanks. :-)

---

### Post by Bashing-om on 2014-11-15
Alex; Hey hey ....

Let us try javier-ejsf's solution from:
[http://ubuntuforums.org/showthread.php?t=2167879&highlight=sis](http://ubuntuforums.org/showthread.php?t=2167879&highlight=sis)
Remember to make sure " Modelname    "LCD Panel 1280x800" " is compatible with the current display monitor and/or change it to the preferred resolution.

Move the present config file - /usr/share/X11/xorg.conf.d/use-vesa.conf - out of the way, say to the desktop, reboot and let us see what else needs to be done.

[INDENT][INDENT]sure looks like it holds promise
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-17
Sorry but,
```
rasphack@Alexs-Coding-Machine:~$ sudo cp xorg.conf /etc/X11/xorg.conf
[sudo] password for rasphack: 
cp: cannot stat ‘xorg.conf’: No such file or directory

```

There's no xorg.conf dir in /usr/etc/X11. There **is** an xorg.conf._**d**_ dir in /usr/share/X11/. What to do?

Sorry :-/ :-)

---

### Post by Bashing-om on 2014-11-17
Alex; Morning to ya;

Yeah, the file will not exist by default. You must create it, and then copy the contents of the referenced Xorg.conf file into place.
( create from either your file manager, or from terminal: command) ->
```

sudo touch /etc/X11/xorg.conf

```
Reboot and let's see what happens.
After making up the file, I can foresee that one might have to make the file "executable". We will cross that bridge when we come to it.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-17
BTW You put ```
sudo touch /etc/X11/xorg.conf/etc/X11/xorg.conf
``` when it should have just been ```

sudo touch /etc/X11/xorg.conf
```

But I figured that out when the file wouldn't save. Rebooted and got 2(? maybe one) more res options. Grabbed
some screenshots. The top option in Screen Display 2 is no use. If you look at the wallpaper on my desktop
it's all squishied. :-P
[ATTACH=CONFIG]258043[/ATTACH][ATTACH=CONFIG]258044[/ATTACH][ATTACH=CONFIG]258045[/ATTACH]

Hope that helps!

P.S: It's actually 19:08pm in the UK at the time I posted this.

---

### Post by Bashing-om on 2014-11-17
Alex; Yeah ( 5 hours ahead of me)

Looking good (?); 
What does 'xrandr' report for available screen resolutions, maybe change the resolution in the xorg.conf file ?

[INDENT][INDENT]tweak'n for effect
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-17
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1280 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1280x768       61.0  
   1024x768       85.0* 
   800x600        86.0  
   640x480        86.0 

```

Not sure if you get notified when updates on posts are made so thought I'd post this, just in case.

[Post #131]("http://ubuntuforums.org/showthread.php?t=2244408&p=13169074#post13169074") now has the appropriate attachments.

P.S: Just discovered that when you copy the space after a command in terminal, when the same line is copied - say, from a post on this forum - and pasted, terminal automatically "presses enter" for you. So if you need to put a command into terminal but need to edit it slightly before you run it - maybe changing it to apply to 32 bit not 64 or whatever - make sure of how it's been posted. Don't put it into terminal and edit it there, it might run before you don't want it to, but use gedit or something. Thought I'd let you know. I've been caught out by this more than once, so be careful! :-)

---

### Post by Bashing-om on 2014-11-17
Alex: Weellll,

What happens if you change the modline from 1024x768 to that of  1280x768  in the xorg file ?
------------
off topic: Yeah on them silly little spaces, I try to watch out for them. I too have been bit.

[INDENT][INDENT]which way to go, and what to do 
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-19
Sorry Bashing, letting the side down again! Doh! Can't figure out what to change. This is what I've got in the file: ```
Section "Device"
  Identifier "Generic Video Card"
    VendorName  "Silicon Integrated Systems [SiS]"
        BoardName   "771/671 PCIE VGA Display Adapter"
    Busid "PCI:1:0:0"
    Driver "vesa"
    Screen 0
        Option "UseFBDev" "true"
        Option "DPMS"
        Option "ShadowFB"
        Option "MaxXFBMem"
        VideoRam 262016
        Option "RenderAccel" "true"
        Option "AllowGLXWithComposite" "true"
        Option "backingstore" "true"
        Option "AddARGBGLXVisuals" "True"

EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x800"
    HorizSync 20-107
        VertRefresh 50-185
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    768
        Modes        "1280x768@60"    "1280x720@60"    "800x600@60"    "1280x800@60"    "800x600@56"
    EndSubSection
EndSection

Section "Module"
    Load "dri"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "GLcore"
    Load "i2c"
    Load "bitmap"
    Load "ddc"
    Load "int10"
    Load "vbe"
    Load "speedo"
    Load "record"
EndSection

Section "DRI"
        Mode 0666
EndSection 
```

If you could highlight in bold what I need to edit that'd be great.

Thanks. :-)

Just thought I'd suggest [this]("http://ubuntuforums.org/showthread.php?t=2167879&p=13169484#post13169484"). If we can't find a decent solution anybetter than what I've got now would this be superior to what I've got now?
:-)

---

### Post by Bashing-om on 2014-11-20
Alex; Hey, hey ...

No harm at all in seeing what results with ' xdiagnose ' .

As to the modification in the Xorg.conf:
What results in your display when changing this line:
> 
 Virtual    1280    768

to:
```

 Virtual    1280    800

```
we have 5 modlines we can try, see which gives the better display.

Not great;
[INDENT][INDENT][INDENT]but we do have things we can tweak on
[/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-21
1280x800 is too big. There isn't any bar at the top (what's the name of it again? I forget). 1280x768 does allow everything on the screen but everything is obviously "stretched". My current res works OK with most stuff. It's 1024x768. I included a screenshot of the 1280x800 res, just so you can see **how** bad it is. Any suggestions what to do know or is it back to the old research?

:-)
[ATTACH=CONFIG]258110[/ATTACH]

---

### Post by Bashing-om on 2014-11-24
alex: Hello;

Might see what results with a lower resolution, say:1280x720 ??
Might also look and see what can be done from grub:
in my '/etc/default/grub' file I have set:
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1600x900

```
where 'vbeinfo' is from the boot menu, 'c' -> grub terminal.

[INDENT][INDENT]poke at it till something else gives
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-25
Welcome screen is still dodgy. :-/ BTW, on the second line, > # note that you can use only modes which your graphic card supports via VBE, is there a list a compatible resolutions somewhere?

That's not worked either. :-/ Odd.

---

### Post by Bashing-om on 2014-11-26
Alex;

Yeah odd that there is no return from grub's command line for the command 'vbeinfo'. When I reboot this eve I will confirm my procedure.
As to:
> 
, is there a list a compatible resolutions somewhere?

Not that I am aware of. We are looking for the resolutions your system advises that are available, not to force an issue that can cause breakage.

Poke at it some more, when we know more

---

### Post by Alex Eagle on 2014-11-27
Thanks dude. BTW the bar at the top suddenly fits if I roll over it. It seems to work a bit like fullscreen on a web browser, except that half of the bar is still visible when "hidden".

:-O

---

### Post by Bashing-om on 2014-11-27
Alex; Hey, hey;

> **Alex_Eagle said:**
> Thanks dude. BTW the bar at the top suddenly fits if I roll over it. It seems to work a bit like fullscreen on a web browser, except that half of the bar is still visible when "hidden".

:-O

That ^ I would think is a setting in your preferences.

as to 'vbeinfo';
Boot to the grub boot menu ( right -shift- key when bios screen clears ), with the latest kernel highlighted press the 'c' key for a (c)ommand line.
One now has a grub prompt. At this prompt enter the grub command 'vbeinfo'.
In my case I get 2 pages of resolution options ; 
What is your result ?

At the end of the print out is "Preferred mode: 1600x900" in my case. Do you not see something similar in your case ?

Else I am at a loss as to what to do.

[INDENT][INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-11-28
I don't think it is a settings preference influenced thing. I am still on about the welcome screen. Haven't found any settings that influence that in the usual System Settings UI. 

Will boot to grub now.

P.S: Why G.R.U.B?

Here's a pic of my screen in GRUB with the results of vbeinfo.
[ATTACH=CONFIG]258254[/ATTACH]

Last line says "No info availiable", let me guess, probably because of my whacky card?

*eyeroll*

---

### Post by Bashing-om on 2014-11-29
Alex; Well.

Like this; GRUB = Grand Unified Boot loader. And that is what it is, It is to load the kernel, at the point of grub there is no operating system in existence.
I think at the "welcome screen" grub still has control and we can effect the reslolution of the screen at that point from a grub config file. In this case the file is " /etc/default/grub" .

Looking at your output from 'vbeinfo' it appears that a resolution of 1024x768 is the best we can do.
Try editing " /etc/default/grub " in the line:
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

```
change " #GRUB_GFXMODE=640x480 " to:
```

GRUB_GFXMODE=1024x768

```
note that the hash is removed from the start of the line.

For the change to propogate, we must tell the system:
```

sudo update-grub

```

Reboot and let's see what the change looks like.
-----------------------------------
There is a lot going on, and the displayed resolution depends on many factors - primarily DKMS  - Dynamic Kernel Mode Setting. Does the monitor supply, does the card read it, does the kernel pick it up ? .. Now we already know it does not happen in all respects, else we would not be making up control files ( /etc/X11/Xorg.conf , for instance ).

To give you an idea of what is happening: This is in reference to other than XFCE, but you get the gist, I hope.

The login screen is usually handled by a Display Manger that handles logging in and choosing and launching the Desktop Environment.  I think for vanila ubuntu that would be gdm, which handles graphic configuration in /etc/gdm/gdm.conf. When gdm hands off to the desktop, the configuration is handled by files in /etc/Xorg/ like xorg.conf and xorg.conf.d/*
For most systems, the details are auto-configured at startup, but if you've configured something manually like an nvidia card (SIS), the handoff appears to be failing.
We then start looking at other control files, maybe, only maybe:
1. /etc/rc.local
2. /usr/share/lightdm/lightdm.conf.d/
If you need some special behaviour when X servers and user sessions start/stop you can set commands to be run with the following configuration: 

[SeatDefaults]
display-setup-script=command
display-stopped-script=command (Not in Ubuntu 12.04 LTS)
greeter-setup-script=command
session-setup-script=command
session-cleanup-script=command
session-wrapper=command
greeter-wrapper=command (Not in Ubuntu 12.04 LTS)display-setup-script is run after the X server starts but before the user session / greeter is run. Set this if you need to configure anything special in the X server. It is run as root. If this command returns an error code the X server is stopped. 
display-stopped-script is run after an X server exits. It is run as root. 
greeter-setup-script is run before a greeter starts. It is run as root. If this command returns an error code the greeter fails to start (which will cause LightDM to stop). 
session-setup-script is run before a user session starts. If this command returns an error the session will not start (user is returned to a greeter). 
session-cleanup-script is run after a greeter or user session stops. It is run as root. 
session-wrapper is a the command to run for a session. This command is run as the user and needs to exec the command passed in the arguments to complete running the session. Use this if you need to do special setup for a user session. Note the default is 'lightdm-session' so you should chain to this if you need to override this setting. 

greeter-wrapper is a the command to run a greeter. It is the equivalent of session-wrapper for greeters.
Pick one that You like, from ones that are run with root priviledges.
See:[https://wiki.ubuntu.com/LightDM#Configuration_and_Tweaks](https://wiki.ubuntu.com/LightDM#Configuration_and_Tweaks)

Keep in mind, we are dealing with XFCE4, some differing will exist. I do not have access to your terminal or display and the trouble shooting to find an optimum solution will be slow. I have no means to test/verify anything we do, it is all on you. A lot of trial and error to find out what we can do, and what we should do.

I never said this was going to be easy. I have also advised you that I do not know what I am doing in this circumstance -> I do welcome the learning experience.

------------------
What can I say, 

[INDENT][INDENT]it is all that experience in learning
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-12-15
First of all, sorry for not replying, the last couple of weeks have been hectic and I only just remembered that you'd posted anything at all.

I will try what you've said ASAP.

P.S: I appreciate the humility. I'm surprised you know virtually nothing about my situation. I'm happy to be able to expand your knowledge. Hey, if I don't need this craptop once I get a new one I might send this one to you! So you can fiddle with it and see first-hand what the probs are.

P.P.S: Check the laptop thread... :-)

P.P.P.S: I originally had ```
GRUB_GFXMODE=1600x900
``` in place. Odd.

P.P.P.P.S: I still need a fix for the general look of everything. The desktop manager I guess. Can't remember. Anyway, everything fits, but it's a bit too tall. It looks like my screen is supposed to be half an inch less tall but it was a bit taller so it's streched it. 

P.P.P.P.P.S: I've really got far too many postscripts now.

P.P.P.P.P.P.S: lol XD

---

### Post by Bashing-om on 2014-12-15
Alex; Hello;

Maybe, just maybe it is time to consider making up particular modeline ??
see:
```

man cvt

```

[INDENT][INDENT]no easy answer
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-12-19
Ok. Done the GRUB-GFXMODE thing. The dual boot bit is better proportioned now. It used to look like a toddlers' OS. A bit like Safe Mode for Windows but worse. But when the welcome screen kicks in, the bar at the top still only half fits.

P.S: Where should I put the ```
man cvt
``` thing?

---

### Post by Bashing-om on 2014-12-19
Alex; Fine upstanding young man that you are .

Making progress ?

The terminal command " man cvt " will access the ubuntu MANual maintained on your system.
To (q)uit from the manual press the 'q' key.

See:
```

man man

```

When we go with 'cvt -> xrander' getting deep, and we will have to tread lightly . Might put this method in our back pocket and keep it as a means of last resort ?

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2014-12-19
&#55357;&#56842; Thanks! *beeming with joy, despite the regular praise I get (probably a bit too much)* &#55357;&#56836;

Ok, thanks. I'll have a look at the manual but before I do anything to it, what else is there that we could do? As you say, might be best to keep it in the back pocket for now! A bit like the bog roll I've got I my back pocket ATM. Got a massive cold! &#55357;&#56862;

&#55357;&#56836;

Bye! &#55357;&#56833;

---

### Post by Bashing-om on 2014-12-19
Alex; Hey;

Like this . You are our future. Time well invested. It best be well invested !

> 
before I do anything to it, what else is there that we could do? 

Read the manual pages, consider what you have done to get good graphics to this point, what these results have been. Maybe give us some direction on where we should focus our attention.

When your head clears from that cold, we will take off again.

For my thought process ( at this point only) what have you got set up for the startup file ?
```

cat ~/.xinitrc

```

Are there any errors reported by X ?
```

cat /var/log/Xorg.0.log
cat ~/.xsession-errors

```

[INDENT][INDENT]taking a look around
[/INDENT][/INDENT]

---

### Post by android_babbles on 2014-12-20
Hey,Perform a network install using the netboot images rather than the new <**release**>-netboot images like quantal-netboot images.Also,install the **Raring** hardware enablement packages in Precise, please run instead the following command: 

 
sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring libgl1-mesa-glx-lts-raring
Thank you!!

---

### Post by Bashing-om on 2014-12-20
@android_babbles; UUggg;

Welcome to the forum. All input is welcome and yes, tweaking on SIS graphics is trying. We do the best that we can. Optimizes what we have to work with.
> **android_babbles said:**
> Hey,Perform a network install using the netboot images rather than the new <**release**>-netboot images like quantal-netboot images.Also,install the **Raring** hardware enablement packages in Precise, please run instead the following command: 

 
sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring libgl1-mesa-glx-lts-raring
Thank you!!

Not a good thing in this case,'raring' is End-Of-Life and has no support. That is not to say that the 'trusty' HardWare Enablement stack installation would not be a viable option. // But keep in mind, we are dealing with old hardware here rather than 'new' . The purpose of HWE is to have access to new features in that new hardware.


[INDENT][INDENT]all in that process of learning
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2015-01-05
Soz guys! Lost track of time! Haven't logged in in ages. :-P 

What the heck was all that about from android_babbles? Is that what I'm supposed to do?! In which case, if it was directed at me, I've barely any idea about wha he's just said. 

Will try what you've said bashing, thanks for everything. :-) Gotta crack on with my maths ATM tho.

:-)

```
cat ~/.xinitrc
``` returns;

```
cat: /home/rasphack/.xinitrc: No such file or directory
```
By that, I'm guessin' I should have entered that whilst still within the manual? Tried that. Didn't find much else in the manual anyway. Reason 1, I don't really know what I'm looking for, Reason 2, don't know how to navigate it. I had a look at the help section but that didn't help much. :-/

I've included a photo of the manual, in case there's something in it you might wanna see. I dunno tho coz I haven't looked through it that much. :-)
[ATTACH=CONFIG]259015[/ATTACH]


```
cat /var/log/Xorg.0.log
``` returns;

```
    33.302]     RedFieldPosition: 11
[    33.302]     GreenMaskSize: 6
[    33.302]     GreenFieldPosition: 5
[    33.302]     BlueMaskSize: 5
[    33.303]     BlueFieldPosition: 0
[    33.303]     RsvdMaskSize: 0
[    33.303]     RsvdFieldPosition: 0
[    33.303]     DirectColorModeInfo: 0
[    33.303]     PhysBasePtr: 0xc0000000
[    33.303]     LinBytesPerScanLine: 1024
[    33.303]     BnkNumberOfImagePages: 20
[    33.303]     LinNumberOfImagePages: 20
[    33.303]     LinRedMaskSize: 5
[    33.303]     LinRedFieldPosition: 11
[    33.303]     LinGreenMaskSize: 6
[    33.308]     LinGreenFieldPosition: 5
[    33.308]     LinBlueMaskSize: 5
[    33.308]     LinBlueFieldPosition: 0
[    33.308]     LinRsvdMaskSize: 0
[    33.308]     LinRsvdFieldPosition: 0
[    33.308]     MaxPixelClock: 0
[    33.308] Mode: 12d (320x200)
[    33.308]     ModeAttributes: 0x9f
[    33.308]     WinAAttributes: 0x7
[    33.308]     WinBAttributes: 0x0
[    33.308]     WinGranularity: 64
[    33.308]     WinSize: 64
[    33.308]     WinASegment: 0xa000
[    33.308]     WinBSegment: 0xa000
[    33.308]     WinFuncPtr: 0xc000877b
[    33.308]     BytesPerScanline: 320
[    33.308]     XResolution: 320
[    33.308]     YResolution: 200
[    33.308]     XCharSize: 8
[    33.308]     YCharSize: 8
[    33.308]     NumberOfPlanes: 1
[    33.309]     BitsPerPixel: 8
[    33.309]     NumberOfBanks: 1
[    33.309]     MemoryModel: 4
[    33.309]     BankSize: 0
[    33.309]     NumberOfImages: 127
[    33.309]     RedMaskSize: 0
[    33.309]     RedFieldPosition: 0
[    33.309]     GreenMaskSize: 0
[    33.309]     GreenFieldPosition: 0
[    33.309]     BlueMaskSize: 0
[    33.309]     BlueFieldPosition: 0
[    33.309]     RsvdMaskSize: 0
[    33.309]     RsvdFieldPosition: 0
[    33.309]     DirectColorModeInfo: 0
[    33.309]     PhysBasePtr: 0xc0000000
[    33.309]     LinBytesPerScanLine: 320
[    33.309]     BnkNumberOfImagePages: 127
[    33.309]     LinNumberOfImagePages: 127
[    33.309]     LinRedMaskSize: 0
[    33.309]     LinRedFieldPosition: 0
[    33.309]     LinGreenMaskSize: 0
[    33.309]     LinGreenFieldPosition: 0
[    33.309]     LinBlueMaskSize: 0
[    33.309]     LinBlueFieldPosition: 0
[    33.309]     LinRsvdMaskSize: 0
[    33.309]     LinRsvdFieldPosition: 0
[    33.309]     MaxPixelClock: 0
[    33.309] Mode: 131 (640x400)
[    33.309]     ModeAttributes: 0x9b
[    33.309]     WinAAttributes: 0x7
[    33.309]     WinBAttributes: 0x0
[    33.309]     WinGranularity: 64
[    33.309]     WinSize: 64
[    33.309]     WinASegment: 0xa000
[    33.309]     WinBSegment: 0xa000
[    33.309]     WinFuncPtr: 0xc000877b
[    33.309]     BytesPerScanline: 1280
[    33.309]     XResolution: 640
[    33.309]     YResolution: 400
[    33.309]     XCharSize: 8
[    33.309]     YCharSize: 16
[    33.309]     NumberOfPlanes: 1
[    33.309]     BitsPerPixel: 16
[    33.309]     NumberOfBanks: 1
[    33.309]     MemoryModel: 6
[    33.309]     BankSize: 0
[    33.309]     NumberOfImages: 15
[    33.309]     RedMaskSize: 5
[    33.309]     RedFieldPosition: 11
[    33.309]     GreenMaskSize: 6
[    33.309]     GreenFieldPosition: 5
[    33.309]     BlueMaskSize: 5
[    33.309]     BlueFieldPosition: 0
[    33.309]     RsvdMaskSize: 0
[    33.309]     RsvdFieldPosition: 0
[    33.309]     DirectColorModeInfo: 0
[    33.309]     PhysBasePtr: 0xc0000000
[    33.309]     LinBytesPerScanLine: 1280
[    33.309]     BnkNumberOfImagePages: 15
[    33.309]     LinNumberOfImagePages: 15
[    33.309]     LinRedMaskSize: 5
[    33.309]     LinRedFieldPosition: 11
[    33.310]     LinGreenMaskSize: 6
[    33.310]     LinGreenFieldPosition: 5
[    33.310]     LinBlueMaskSize: 5
[    33.310]     LinBlueFieldPosition: 0
[    33.310]     LinRsvdMaskSize: 0
[    33.310]     LinRsvdFieldPosition: 0
[    33.310]     MaxPixelClock: 0
[    33.310] *Mode: 112 (640x480)
[    33.310]     ModeAttributes: 0x9b
[    33.310]     WinAAttributes: 0x7
[    33.310]     WinBAttributes: 0x0
[    33.310]     WinGranularity: 64
[    33.310]     WinSize: 64
[    33.310]     WinASegment: 0xa000
[    33.310]     WinBSegment: 0xa000
[    33.310]     WinFuncPtr: 0xc000877b
[    33.310]     BytesPerScanline: 2560
[    33.310]     XResolution: 640
[    33.310]     YResolution: 480
[    33.310]     XCharSize: 8
[    33.310]     YCharSize: 16
[    33.310]     NumberOfPlanes: 1
[    33.310]     BitsPerPixel: 32
[    33.310]     NumberOfBanks: 1
[    33.310]     MemoryModel: 6
[    33.310]     BankSize: 0
[    33.310]     NumberOfImages: 5
[    33.310]     RedMaskSize: 8
[    33.310]     RedFieldPosition: 16
[    33.310]     GreenMaskSize: 8
[    33.310]     GreenFieldPosition: 8
[    33.310]     BlueMaskSize: 8
[    33.310]     BlueFieldPosition: 0
[    33.310]     RsvdMaskSize: 8
[    33.310]     RsvdFieldPosition: 24
[    33.310]     DirectColorModeInfo: 0
[    33.310]     PhysBasePtr: 0xc0000000
[    33.310]     LinBytesPerScanLine: 2560
[    33.310]     BnkNumberOfImagePages: 5
[    33.310]     LinNumberOfImagePages: 5
[    33.310]     LinRedMaskSize: 8
[    33.310]     LinRedFieldPosition: 16
[    33.310]     LinGreenMaskSize: 8
[    33.310]     LinGreenFieldPosition: 8
[    33.310]     LinBlueMaskSize: 8
[    33.310]     LinBlueFieldPosition: 0
[    33.310]     LinRsvdMaskSize: 8
[    33.310]     LinRsvdFieldPosition: 24
[    33.310]     MaxPixelClock: 0
[    33.311] *Mode: 115 (800x600)
[    33.311]     ModeAttributes: 0x9b
[    33.311]     WinAAttributes: 0x7
[    33.311]     WinBAttributes: 0x0
[    33.311]     WinGranularity: 64
[    33.311]     WinSize: 64
[    33.311]     WinASegment: 0xa000
[    33.311]     WinBSegment: 0xa000
[    33.311]     WinFuncPtr: 0xc000877b
[    33.311]     BytesPerScanline: 3200
[    33.311]     XResolution: 800
[    33.311]     YResolution: 600
[    33.311]     XCharSize: 8
[    33.311]     YCharSize: 16
[    33.311]     NumberOfPlanes: 1
[    33.311]     BitsPerPixel: 32
[    33.311]     NumberOfBanks: 1
[    33.311]     MemoryModel: 6
[    33.311]     BankSize: 0
[    33.311]     NumberOfImages: 3
[    33.311]     RedMaskSize: 8
[    33.311]     RedFieldPosition: 16
[    33.311]     GreenMaskSize: 8
[    33.311]     GreenFieldPosition: 8
[    33.311]     BlueMaskSize: 8
[    33.311]     BlueFieldPosition: 0
[    33.311]     RsvdMaskSize: 8
[    33.311]     RsvdFieldPosition: 24
[    33.311]     DirectColorModeInfo: 0
[    33.311]     PhysBasePtr: 0xc0000000
[    33.311]     LinBytesPerScanLine: 3200
[    33.311]     BnkNumberOfImagePages: 3
[    33.311]     LinNumberOfImagePages: 3
[    33.311]     LinRedMaskSize: 8
[    33.311]     LinRedFieldPosition: 16
[    33.311]     LinGreenMaskSize: 8
[    33.311]     LinGreenFieldPosition: 8
[    33.311]     LinBlueMaskSize: 8
[    33.311]     LinBlueFieldPosition: 0
[    33.311]     LinRsvdMaskSize: 8
[    33.311]     LinRsvdFieldPosition: 24
[    33.311]     MaxPixelClock: 0
[    33.316] *Mode: 118 (1024x768)
[    33.316]     ModeAttributes: 0x9b
[    33.316]     WinAAttributes: 0x7
[    33.316]     WinBAttributes: 0x0
[    33.316]     WinGranularity: 64
[    33.316]     WinSize: 64
[    33.316]     WinASegment: 0xa000
[    33.316]     WinBSegment: 0xa000
[    33.316]     WinFuncPtr: 0xc000877b
[    33.316]     BytesPerScanline: 4096
[    33.316]     XResolution: 1024
[    33.316]     YResolution: 768
[    33.316]     XCharSize: 8
[    33.316]     YCharSize: 16
[    33.316]     NumberOfPlanes: 1
[    33.316]     BitsPerPixel: 32
[    33.316]     NumberOfBanks: 1
[    33.316]     MemoryModel: 6
[    33.316]     BankSize: 0
[    33.316]     NumberOfImages: 1
[    33.316]     RedMaskSize: 8
[    33.316]     RedFieldPosition: 16
[    33.316]     GreenMaskSize: 8
[    33.316]     GreenFieldPosition: 8
[    33.316]     BlueMaskSize: 8
[    33.316]     BlueFieldPosition: 0
[    33.316]     RsvdMaskSize: 8
[    33.316]     RsvdFieldPosition: 24
[    33.316]     DirectColorModeInfo: 0
[    33.316]     PhysBasePtr: 0xc0000000
[    33.316]     LinBytesPerScanLine: 4096
[    33.316]     BnkNumberOfImagePages: 1
[    33.316]     LinNumberOfImagePages: 1
[    33.316]     LinRedMaskSize: 8
[    33.316]     LinRedFieldPosition: 16
[    33.316]     LinGreenMaskSize: 8
[    33.316]     LinGreenFieldPosition: 8
[    33.316]     LinBlueMaskSize: 8
[    33.316]     LinBlueFieldPosition: 0
[    33.316]     LinRsvdMaskSize: 8
[    33.316]     LinRsvdFieldPosition: 24
[    33.316]     MaxPixelClock: 0
[    33.317] Mode: 102 (800x600)
[    33.317]     ModeAttributes: 0x1f
[    33.317]     WinAAttributes: 0x7
[    33.317]     WinBAttributes: 0x0
[    33.317]     WinGranularity: 64
[    33.317]     WinSize: 64
[    33.317]     WinASegment: 0xa000
[    33.317]     WinBSegment: 0xa000
[    33.317]     WinFuncPtr: 0xc000877b
[    33.317]     BytesPerScanline: 100
[    33.317]     XResolution: 800
[    33.317]     YResolution: 600
[    33.317]     XCharSize: 8
[    33.317]     YCharSize: 16
[    33.317]     NumberOfPlanes: 4
[    33.317]     BitsPerPixel: 4
[    33.317]     NumberOfBanks: 1
[    33.317]     MemoryModel: 3
[    33.317]     BankSize: 0
[    33.317]     NumberOfImages: 31
[    33.317]     RedMaskSize: 0
[    33.317]     RedFieldPosition: 0
[    33.317]     GreenMaskSize: 0
[    33.317]     GreenFieldPosition: 0
[    33.317]     BlueMaskSize: 0
[    33.317]     BlueFieldPosition: 0
[    33.317]     RsvdMaskSize: 0
[    33.317]     RsvdFieldPosition: 0
[    33.317]     DirectColorModeInfo: 0
[    33.317]     PhysBasePtr: 0xc0000000
[    33.317]     LinBytesPerScanLine: 100
[    33.317]     BnkNumberOfImagePages: 31
[    33.317]     LinNumberOfImagePages: 31
[    33.317]     LinRedMaskSize: 0
[    33.317]     LinRedFieldPosition: 0
[    33.317]     LinGreenMaskSize: 0
[    33.317]     LinGreenFieldPosition: 0
[    33.317]     LinBlueMaskSize: 0
[    33.317]     LinBlueFieldPosition: 0
[    33.317]     LinRsvdMaskSize: 0
[    33.317]     LinRsvdFieldPosition: 0
[    33.317]     MaxPixelClock: 0
[    33.317] 
[    33.317] (II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
[    33.317] (II) VESA(0): Configured Monitor: Using hsync range of 20.00-107.00 kHz
[    33.317] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-185.00 Hz
[    33.317] (II) VESA(0): Not using mode "1280x768@60" (no mode of this name)
[    33.317] (II) VESA(0): Not using mode "1280x720@60" (no mode of this name)
[    33.317] (II) VESA(0): Not using mode "800x600@60" (no mode of this name)
[    33.317] (II) VESA(0): Not using mode "1280x800@60" (no mode of this name)
[    33.317] (II) VESA(0): Not using mode "800x600@56" (no mode of this name)
[    33.317] (II) VESA(0): Not using built-in mode "1280x768" (no mode of this name)
[    33.317] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    33.317] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    33.317] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    33.317] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    33.318] (II) VESA(0): Configured Monitor: Using hsync range of 20.00-107.00 kHz
[    33.318] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-185.00 Hz
[    33.318] (II) VESA(0): Not using mode "1280x768@60" (no mode of this name)
[    33.318] (II) VESA(0): Not using mode "1280x720@60" (no mode of this name)
[    33.318] (II) VESA(0): Not using mode "800x600@60" (no mode of this name)
[    33.318] (II) VESA(0): Not using mode "1280x800@60" (no mode of this name)
[    33.318] (II) VESA(0): Not using mode "800x600@56" (no mode of this name)
[    33.328] (**) VESA(0): Virtual size is 1280x800 (pitch 1280)
[    33.328] (**) VESA(0):  Built-in mode "1280x768"
[    33.328] (**) VESA(0):  Built-in mode "1024x768"
[    33.328] (**) VESA(0):  Built-in mode "800x600"
[    33.328] (**) VESA(0):  Built-in mode "640x480"
[    33.328] (==) VESA(0): DPI set to (96, 96)
[    33.328] (**) VESA(0): Option "ShadowFB"
[    33.328] (II) VESA(0): Attempting to use 60Hz refresh for mode "1280x768" (11e)
[    33.328] (II) VESA(0): Attempting to use 85Hz refresh for mode "1024x768" (118)
[    33.328] (II) VESA(0): Attempting to use 85Hz refresh for mode "800x600" (115)
[    33.329] (II) VESA(0): Attempting to use 85Hz refresh for mode "640x480" (112)
[    33.329] (**) VESA(0): Using "Shadow Framebuffer"
[    33.329] (II) Loading sub module "shadow"
[    33.329] (II) LoadModule: "shadow"
[    33.329] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    33.329] (II) Module shadow: vendor="X.Org Foundation"
[    33.329]     compiled for 1.16.0, module version = 1.1.0
[    33.329]     ABI class: X.Org ANSI C Emulation, version 0.4
[    33.329] (II) Loading sub module "fb"
[    33.329] (II) LoadModule: "fb"
[    33.329] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.329] (II) Module fb: vendor="X.Org Foundation"
[    33.329]     compiled for 1.16.0, module version = 1.0.0
[    33.329]     ABI class: X.Org ANSI C Emulation, version 0.4
[    33.330] (==) Depth 24 pixmap format is 32 bpp
[    33.330] (II) Loading sub module "int10"
[    33.330] (II) LoadModule: "int10"
[    33.330] (II) Loading /usr/lib/xorg/modules/libint10.so
[    33.330] (II) Module int10: vendor="X.Org Foundation"
[    33.330]     compiled for 1.16.0, module version = 1.0.0
[    33.330]     ABI class: X.Org Video Driver, version 18.0
[    33.330] (II) VESA(0): initializing int10
[    33.339] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    33.343] (II) VESA(0): VESA BIOS detected
[    33.343] (II) VESA(0): VESA VBE Version 3.0
[    33.343] (II) VESA(0): VESA VBE Total Mem: 262144 kB
[    33.343] (II) VESA(0): VESA VBE OEM: SiS
[    33.343] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    33.343] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    33.343] (II) VESA(0): VESA VBE OEM Product: 6330
[    33.343] (II) VESA(0): VESA VBE OEM Product Rev: 3.74.10A
[    33.348] (II) VESA(0): virtual address = 0x7faca3c9b000,
    physical address = 0xc0000000, size = 268435456
[    33.369] (II) VESA(0): Setting up VESA Mode 0x11E (1280x768)
[    33.527] (==) VESA(0): Default visual is TrueColor
[    33.541] (**) VESA(0): Option "BackingStore" "true"
[    33.541] (**) VESA(0): Backing store enabled
[    33.542] (**) VESA(0): DPMS enabled
[    33.542] (WW) VESA(0): Option "UseFBDev" is not used
[    33.542] (WW) VESA(0): Option "MaxXFBMem" is not used
[    33.542] (WW) VESA(0): Option "RenderAccel" is not used
[    33.543] (WW) VESA(0): Option "AllowGLXWithComposite" is not used
[    33.543] (WW) VESA(0): Option "AddARGBGLXVisuals" is not used
[    33.543] (==) RandR enabled
[    33.555] (II) SELinux: Disabled on system
[    33.561] (II) AIGLX: Screen 0 is not DRI2 capable
[    33.561] (EE) AIGLX: reverting to software rendering
[    33.676] (II) AIGLX: Loaded and initialized swrast
[    33.677] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    33.735] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.739] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    33.739] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.739] (II) LoadModule: "evdev"
[    33.744] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.762] (II) Module evdev: vendor="X.Org Foundation"
[    33.762]     compiled for 1.16.0, module version = 2.9.0
[    33.762]     Module class: X.Org XInput Driver
[    33.762]     ABI class: X.Org XInput driver, version 21.0
[    33.762] (II) Using input driver 'evdev' for 'Power Button'
[    33.762] (**) Power Button: always reports core events
[    33.762] (**) evdev: Power Button: Device: "/dev/input/event3"
[    33.762] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.763] (--) evdev: Power Button: Found keys
[    33.763] (II) evdev: Power Button: Configuring as keyboard
[    33.763] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    33.763] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.763] (**) Option "xkb_rules" "evdev"
[    33.763] (**) Option "xkb_model" "pc105"
[    33.763] (**) Option "xkb_layout" "gb"
[    33.765] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    33.766] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    33.766] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    33.766] (II) Using input driver 'evdev' for 'Video Bus'
[    33.766] (**) Video Bus: always reports core events
[    33.766] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    33.767] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    33.767] (--) evdev: Video Bus: Found keys
[    33.767] (II) evdev: Video Bus: Configuring as keyboard
[    33.767] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input13/event6"
[    33.767] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    33.767] (**) Option "xkb_rules" "evdev"
[    33.767] (**) Option "xkb_model" "pc105"
[    33.767] (**) Option "xkb_layout" "gb"
[    33.767] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.767] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.767] (II) Using input driver 'evdev' for 'Power Button'
[    33.767] (**) Power Button: always reports core events
[    33.767] (**) evdev: Power Button: Device: "/dev/input/event1"
[    33.772] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.772] (--) evdev: Power Button: Found keys
[    33.772] (II) evdev: Power Button: Configuring as keyboard
[    33.772] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    33.772] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    33.772] (**) Option "xkb_rules" "evdev"
[    33.772] (**) Option "xkb_model" "pc105"
[    33.772] (**) Option "xkb_layout" "gb"
[    33.773] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    33.773] (II) No input driver specified, ignoring this device.
[    33.773] (II) This device may have been added with another device file.
[    33.773] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    33.773] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    33.773] (II) Using input driver 'evdev' for 'Sleep Button'
[    33.773] (**) Sleep Button: always reports core events
[    33.773] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    33.773] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    33.773] (--) evdev: Sleep Button: Found keys
[    33.773] (II) evdev: Sleep Button: Configuring as keyboard
[    33.773] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    33.773] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    33.773] (**) Option "xkb_rules" "evdev"
[    33.773] (**) Option "xkb_model" "pc105"
[    33.773] (**) Option "xkb_layout" "gb"
[    33.776] (II) config/udev: Adding input device HDA SIS966 Mic (/dev/input/event7)
[    33.776] (II) No input driver specified, ignoring this device.
[    33.776] (II) This device may have been added with another device file.
[    33.777] (II) config/udev: Adding input device HDA SIS966 Headphone (/dev/input/event8)
[    33.777] (II) No input driver specified, ignoring this device.
[    33.777] (II) This device may have been added with another device file.
[    33.777] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    33.777] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    33.777] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    33.777] (**) AT Translated Set 2 keyboard: always reports core events
[    33.777] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    33.777] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    33.777] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    33.777] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    33.777] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    33.777] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    33.777] (**) Option "xkb_rules" "evdev"
[    33.777] (**) Option "xkb_model" "pc105"
[    33.777] (**) Option "xkb_layout" "gb"
[    33.778] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    33.778] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    33.778] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    33.778] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    33.778] (II) LoadModule: "synaptics"
[    33.778] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    33.779] (II) Module synaptics: vendor="X.Org Foundation"
[    33.779]     compiled for 1.16.0, module version = 1.8.99
[    33.779]     Module class: X.Org XInput Driver
[    33.779]     ABI class: X.Org XInput driver, version 21.0
[    33.779] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    33.779] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    33.779] (**) Option "Device" "/dev/input/event5"
[    33.779] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 68)
[    33.779] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 93)
[    33.779] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    33.779] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    33.779] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    33.779] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    33.779] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    33.779] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    33.779] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input12/event5"
[    33.779] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    33.779] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    33.779] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    33.779] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    33.784] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    33.784] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    33.784] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    33.784] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    33.784] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    33.785] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    33.785] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    53.546] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    53.629] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    65.871] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
(EE) [mi] EQ overflowing.  Additional events will be discarded until existing events are processed.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x56) [0x7facba402e96]
(EE) 1: /usr/bin/X (mieqEnqueue+0x24b) [0x7facba3e401b]
(EE) 2: /usr/bin/X (QueuePointerEvents+0x52) [0x7facba2babf2]
(EE) 3: /usr/bin/X (xf86PostMotionEvent+0xd6) [0x7facba2f1cf6]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7fac9f584000+0x5418) [0x7fac9f589418]
(EE) 5: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7fac9f584000+0x75a2) [0x7fac9f58b5a2]
(EE) 6: /usr/bin/X (0x7facba24c000+0x95638) [0x7facba2e1638]
(EE) 7: /usr/bin/X (0x7facba24c000+0xbfcc9) [0x7facba30bcc9]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (0x7facb7f80000+0x36eb0) [0x7facb7fb6eb0]
(EE) 9: /usr/bin/X (0x7facba24c000+0x1bb4f0) [0x7facba4074f0]
(EE) 10: /lib/x86_64-linux-gnu/libc.so.6 (0x7facb7f80000+0x36eb0) [0x7facb7fb6eb0]
(EE) 11: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x7facb90ac000+0x913cf) [0x7facb913d3cf]
(EE) 12: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x7facb90ac000+0x57abb) [0x7facb9103abb]
(EE) 13: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (pixman_blt+0x52) [0x7facb90b77d2]
(EE) 14: /usr/lib/xorg/modules/libfb.so (fbCopyNtoN+0x32a) [0x7facb3cae1fa]
(EE) 15: /usr/bin/X (miCopyRegion+0x1a7) [0x7facba3e23f7]
(EE) 16: /usr/bin/X (miDoCopy+0x45e) [0x7facba3e299e]
(EE) 17: /usr/lib/xorg/modules/libfb.so (fbCopyArea+0x2d) [0x7facb3cae9dd]
(EE) 18: /usr/bin/X (0x7facba24c000+0x14018d) [0x7facba38c18d]
(EE) 19: /usr/bin/X (0x7facba24c000+0x5320a) [0x7facba29f20a]
(EE) 20: /usr/bin/X (0x7facba24c000+0x571c7) [0x7facba2a31c7]
(EE) 21: /usr/bin/X (0x7facba24c000+0x5b3d6) [0x7facba2a73d6]
(EE) 22: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7facb7fa1ec5]
(EE) 23: /usr/bin/X (0x7facba24c000+0x4576e) [0x7facba29176e]
(EE) 
(EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
(EE) [mi] mieq is *NOT* the cause.  It is a victim.
[   179.548] [mi] Increasing EQ size to 1024 to prevent dropped events.
[   179.582] [mi] EQ processing has resumed after 4 dropped events.
[   179.582] [mi] This may be caused my a misbehaving driver monopolizing the server's resources.
[  9808.276] (II) VESA(0): Setting up VESA Mode 0x11E (1280x768)
[  9808.683] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  9812.731] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  9813.477] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  9813.640] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  9813.735] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  9813.887] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm


```

And ```
cat ~/.xsession-errors
``` returns;

```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
```

---

### Post by Bashing-om on 2015-01-05
Alex Eaglel Hi !

Welcome back .. tough to keep up with all these long delays in-between-times .
From the log, Xorg sure is not in a happy state. Will take me some time to reflect on what the root cause might be.

I will do some homework, see what I can come up with.

[INDENT][INDENT]Hoo Boy, that learning process
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2015-01-05
Thanks Bashing. Really grateful for your help. Although I will be replacing this machine with some beaut of a Win10 angel, the ol' V5535 won't go to waste! I'll either turn it into a server or something or use it for CP and computer technical research.
:-) Take your time. That's what I always say. Easy going like an Ent. (Read LOTR TTT - just google it)

Hey dudes and dudettes! Just to inform y'all, I'm not completely leaving the ubuntu community! Actually, far from it! I have just aquired a lovely new desktop from some old friends, (I say new, more, pretty much unused, it's relatively old. A HP of some sort I think, or at least, the monitor is) and they didn't ask a penny! (I know, lucky git, right?) Anyways, it had Windows Vista (*_ACK_*) Home Premium (Hmeh, not that bad :roll: :-?), and it was quite slow but since I installed Ubuntu 14.04 Trusty Tahr over everything it works perfectly! It shuts down it less than 3 seconds! Epic XD

I think it runs quite fast because of the processor. It's got very  little RAM and the HDD isn't that big either... I have loads of flash  drives though so storage isn't a problem. I could enter for a world  reccord because of the amount of flash drives I have.

I had to get a WiFi adapter off of Amazon to get it to connect to the net (no inbuilt chip) but it was only £3.62 or something (about $5). It works dead well, no lag on the connection, it runs at 802.11n and I have it set up about 15m away from the modem.

It came with a never-used-before keyboard and a slightly tired mouse, but I've got a great mouse already (also from Amazon - £5) so I just use my own.

   So, what use is it to me? What am I going to do with it? Both valid questions that, in this case, you're probably *not* wondering \\:D/. lol
I've already installed Geany (legendary program) via the terminal, so I'll use it for python programming and maybe a few other of the supported languages by Geany, I'll escape from The White Witch of South Marsh (you need better knowledge of Grimbarian geography to know what that means) - my nana... lol
That means that every Friday I'll play on Miniclip and other assorted game sites with my beautiful 1280x1024 display and really revel in the marvels of technology (even the old stuff!). :-) Hmmm, makes me happy just thinking about those prospects. XD proper nerd. I love playing Super Mario All Stars on my 1986 SNES, but that's linked to the TV... Usually the best stuff on the TV on Friday nights are The Chase, Mastermind and A Question of Sport. So I guess I'll have to stick to emulators. :-/ :-D

I may even use it for school, the laptop's slower than I'd like now.

Thanks everybody! :-)

---

### Post by Bashing-om on 2015-01-13
Alex; ->

can not beat better hardware .

[INDENT][INDENT]move'n on up
[/INDENT][/INDENT]

---

### Post by Sally_Joshua on 2015-01-15
Very useful link here [http://askubuntu.com/questions/436374/how-to-get-rid-of-the-gallium-0-4-on-llvmpipe-llvm-0x300-driver-intel-needed](http://askubuntu.com/questions/436374/how-to-get-rid-of-the-gallium-0-4-on-llvmpipe-llvm-0x300-driver-intel-needed)

---

### Post by Alex Eagle on 2015-01-15
> **Sally_Joshua said:**
> Very useful link here [http://askubuntu.com/questions/436374/how-to-get-rid-of-the-gallium-0-4-on-llvmpipe-llvm-0x300-driver-intel-needed](http://askubuntu.com/questions/436374/how-to-get-rid-of-the-gallium-0-4-on-llvmpipe-llvm-0x300-driver-intel-needed)

What do you think to that Ask Ubuntu thread, Bashing? How about this:

> **[ACCEPTED ANSWER. PROBLEM SOLVED]**  Getting "Intel Haswell" instead of the "Gallium 0.4 llvmpipe" video  driver: I very much appreciate the support I got from an export user of  Ask Ubuntu. The problem was indeed solved by loading the "LTS Enablement  Stack" drivers. I Just followed the link offered by **Lekensteyn** and copied the commands in the terminal. Amazing how simple things can turn out to be in Ubuntu: I love it! JGMS                 –                      [JGMS]("http://askubuntu.com/users/259263/jgms")?

Do you think the intel haswell driver would be relevant for me? I can't remeber what hardware I've got! XD

---

### Post by Bashing-om on 2015-01-15
Alex; No relation;

Welp:
> 
Do you think the intel haswell driver would be relevant for me? I can't remeber what hardware I've got! XD


[http://askubuntu.com/questions/436374/how-to-get-rid-of-the-gallium-0-4-on-llvmpipe-llvm-0x300-driver-intel-needed](http://askubuntu.com/questions/436374/how-to-get-rid-of-the-gallium-0-4-on-llvmpipe-llvm-0x300-driver-intel-needed)
> 
What do you think to that Ask Ubuntu thread, Bashing? How about this:


As the focus there is Intel, and what you are working with is 'SIS' .
We are stuck at making up a custom Xorg.conf file. - Is what I think - 
To that end, you need to understand 'cvt' and 'xrandr' .
Even then I doubt there is a perfect solution, just something that is workable.

[INDENT][INDENT]when all else fails
[INDENT][INDENT][INDENT][INDENT]read the instructions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alex Eagle on 2015-01-25
Just to clarify, am I waiting for you to figure out what to do next?

I just don't want to be sitting around doin' nowt if it's you wiatin' for me!

:-)

---

### Post by Bashing-om on 2015-01-25
Alex: Yuk ...

Looking at the Xorg.log file, the system and the graphics card just is not happy . I think we need to provide a reasonable modeline in the video configuration file.

Let's get an updated status:
```

cat /var/log/Xorg.0.log
cat /etc/X11/xorg.conf
ls -al /usr/share/X11/xorg.conf.d/use-vesa.conf
ls -al /etc/X11/xorg.conf.d
ls -al /usr/share/X11/xorg.conf.d

```

And I do some homework and see what it is going to take to make up a modeline that the graphics card accepts.

[INDENT][INDENT]Oh what fun !
[/INDENT][/INDENT]

---

### Post by Alex Eagle on 2015-02-23
Hello all! Bashing has informed me that he can't really provide much more help on this subject. I think it *has* kind of reached the end of the road now anyway. I'm not really that bothered about whether GRUB looks *just perfect* and the rest of the UI is OK. It's only when it comes to playing certain games that the game window can get a bit iffy. But I've got a good desktop for games now! I've even got Steam on it. :-O XD Yay!

I hereby declare this thread as solved. If any better solutions can be found, you know how to contact me. Thanks everybody. :-) Keep computerin'!

---

### Post by rienesl on 2015-03-28
Hi there
about 3 days ago, I rescued a V5535 from being disposed. I ran exactly into the same problems and funnyhow, currently I'm getting exactly the same outputs in my logs, like posted here. Currently I'm running on 1024x768x24@85, switching to 1280x768x24@61 destroys the geometry of the picture (it is stretched) and 1280x800x24x? is not available. The last post had a very sad conclusion. Maybe I might offer some help here? I'm using *buntu on about 8 Notebooks for 5 years now (one of them is the legendary AC100 and I'm using *ubuntu on it since the very experimental stage of this porting). I'm not experienced in coding, but I'm familiar with shell commands.
Greetings,
Martin

PS: I realized "Join Date: Apr 2009" - wow, how time flies by... So to correct myself: I'm using *buntu for 6 years now :)

---

