---
title: "HP with Ubuntu"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by nocturn on 2005-05-18
I read that HP is offering Ubuntu as an option on some of its notebooks.
I couldn't find them on their site though (I live in Europe, where they are supposed to be available).

Does anyone know where to find them?

---

### Post by Bartholomaeus on 2005-05-18
Hi the only thing, that I have read about this. Is that HP will sell some types of notebooks, which have a pre-install of Dos and an copy of Ubuntu. So that the user had do install it himself. 
But I think that you didn't find these notebooks in the stores now. As I read.

here a link, but it's in german: [http://www.heise.de/newsticker/meldung/58740](http://www.heise.de/newsticker/meldung/58740)

Maybe it helps, I hope so. Finally I'm very happy about HP's decision to do this. 

greetings Bart

---

### Post by phen on 2005-05-19
there's another thread in this forum, where Thomas Schneller, an HP employee is answering questions about the release. He also provides you with an prerelease version of the hp-ubuntu (im atm using it, works fine :-) 

search for "hp" "ubuntu" "nc6120" youll find it!

cheers,
kai

---

### Post by Thomas Schneller on 2005-05-20
It's not on the market yet. Hopefully in some weeks. But you will not find it on the HP website. Will be sold over resellers. I will post a note when available

Best regards

Thomas

---

### Post by nocturn on 2005-06-06
A silly question, but if I buy such a model right now, will everything work with Ubuntu (Hoary)?

---

### Post by Thomas Schneller on 2005-06-06
[QUOTE=nocturn]A silly question, but if I buy such a model right now, will everything work with Ubuntu (Hoary)?[/QUOTE]

Except the sd-card reader. No Linux driver for that device so far. And there is an option either to have a broadcom wlan or Intel wlan card. Regommanded is the Intel one as their are Linux drivers available. The broadcom device needs to be used with ndiswrapper and the win driver. Meaning, this will not work out of the box but needs to be enabled manually.

Best Regards

Thomas

---

### Post by Abakaba on 2005-06-07
So is this HP Ubuntu anywhere near release soon? And where can I get it? I have an nc6000 and would love to get it working properly.

---

### Post by Thomas Schneller on 2005-06-07
Grab a copy here:

[http://cdimage.ubuntu.com/custom/20050516/hoary-install-i386.iso](http://cdimage.ubuntu.com/custom/20050516/hoary-install-i386.iso)

---

### Post by nocturn on 2005-06-07
[QUOTE=Thomas Schneller]Except the sd-card reader. No Linux driver for that device so far. And there is an option either to have a broadcom wlan or Intel wlan card. Regommanded is the Intel one as their are Linux drivers available. The broadcom device needs to be used with ndiswrapper and the win driver. Meaning, this will not work out of the box but needs to be enabled manually.

Best Regards

Thomas[/QUOTE]

Hello Thomas

I mailed HP Belgium about this and they have no knowledge of this project...

---

### Post by Thomas Schneller on 2005-06-07
They should. Anyway, please mail me, who you contacted and I will follow up.....

---

### Post by phen on 2005-06-07
are there any differences between the prerelease and the most up to date version?

could i install them without reinstalling ubuntu completely? maybe by updating with dpkg

Thank you!

Kai

---

### Post by Thomas Schneller on 2005-06-07
Kai,

the above link is pointing to the final release. And no, currently it is not possible to update an existing installation. But will be in the future. It's planned to pack all changes into a package which can then be apt-get installed....

Best regards

Thomas

---

### Post by gregor on 2005-06-07
hi thomas,

i plan to buy a notebook to run debian linux and hp + ubuntu seems the best choice at the moment. according to the press release nx6110, nc6120, nc6220, nc6230 and nc6000 models will be supported. how about the other similar models?

my choice is reduced to SXGA nc6230 (hp supported, but not released in germany yet)
and WSXGA nc8230 (not supported by hp?, ATI Mobility Radeon X600 a problem?).

i would prefer the nc8230 because of the wide screen. 3d acceleration is not essential.

should i wait for the nc6230 or will the customized ubuntu run equally on the nc8230?

best regards,
gregor

---

### Post by nocturn on 2005-06-08
Hi Thomas

A different question, do you know which other models work well with Linux ?
I'm rather interested in a Pavilion too, which I can find much easier and cheaper then the models you mentioned.

Thanks

---

### Post by Thomas Schneller on 2005-06-09
*should i wait for the nc6230 or will the customized ubuntu run equally on the nc8230?*

I will do a test and let you know.

*A different question, do you know which other models work well with Linux ?*

No. Cause of the short livecycle of consumer notebooks we do not support them. But regarding price, just search for nc6110. Starting price should be around 700 Euro.

Best regards

Thomas

---

### Post by nocturn on 2005-06-09
[QUOTE=Thomas Schneller]
No. Cause of the short livecycle of consumer notebooks we do not support them. But regarding price, just search for nc6110. Starting price should be around 700 Euro.
[/QUOTE]

Thanks Thomas, but I didn't mean it officially.  Just if you knew personally which others would work without support from HP.  I'm still not sure what I will end up buying...

---

### Post by somez on 2005-06-09
[QUOTE=nocturn]Thanks Thomas, but I didn't mean it officially.  Just if you knew personally which others would work without support from HP.  I'm still not sure what I will end up buying...[/QUOTE]

What about the HPQ nx7000 series?

---

### Post by Thomas Schneller on 2005-06-09
* Just if you knew personally which others would work without support from HP. I'm still not sure what I will end up buying...*

I am currently preparing an unoffical program with my team colleges to participate to Ubuntus Laptop program:

[http://www.ubuntulinux.org/wiki/LaptopTestingTeam](http://www.ubuntulinux.org/wiki/LaptopTestingTeam)

we will test current HP consumer models and feedback the result. But might take some time until available. May be we start with nx7000.... (:

---

### Post by nocturn on 2005-06-10
[QUOTE=Thomas Schneller]* Just if you knew personally which others would work without support from HP. I'm still not sure what I will end up buying...*

I am currently preparing an unoffical program with my team colleges to participate to Ubuntus Laptop program:

[http://www.ubuntulinux.org/wiki/LaptopTestingTeam](http://www.ubuntulinux.org/wiki/LaptopTestingTeam)

we will test current HP consumer models and feedback the result. But might take some time until available. May be we start with nx7000.... (:[/QUOTE]

Thomas, thank you for what you are doing for the GNU/Linux community!  This kind of things are very important to the success of Free Software.

---

### Post by somez on 2005-06-10
[QUOTE=Thomas Schneller]* Just if you knew personally which others would work without support from HP. I'm still not sure what I will end up buying...*

I am currently preparing an unoffical program with my team colleges to participate to Ubuntus Laptop program:

[http://www.ubuntulinux.org/wiki/LaptopTestingTeam](http://www.ubuntulinux.org/wiki/LaptopTestingTeam)

we will test current HP consumer models and feedback the result. But might take some time until available. May be we start with nx7000.... (:[/QUOTE]
 Thomas I really appreciate your work, good job ;-)

---

### Post by Benjamin_Lebsanft on 2005-06-11
HP Germany doesn't know about this either...

---

### Post by sweetthdevil on 2005-06-14
To answer your question about a pavilion, i'm runnig ubuntu on a hp pavilion zd7377ea p4 3.2 ht and absoluty not a problem except form the sd card reader mention earlier that doesn't have a driver for linux so far...

---

### Post by Gandalf on 2005-06-14
Ubuntu is working great with my HP Pavilion dv1071ea laptop, everything is great except of course the TI 6-1 card Reader :(

---

### Post by nocturn on 2005-06-16
Thomas, if you are still here.

Do you know if the Pavilion zv5000 (ZV5474EA) is somewhat compatible with Linux?

Thanks

---

### Post by nocturn on 2005-06-16
[QUOTE=Gandalf]Siemens-mobiles.org Visit it you won't regret it[/QUOTE]

I worked there and I regret it ;-)

---

### Post by somez on 2005-06-16
[QUOTE=nocturn]Thomas, if you are still here.

Do you know if the Pavilion zv5000 (ZV5474EA) is somewhat compatible with Linux?

Thanks[/QUOTE]
 As far as I know, the HPn Pavilon ZTxxxxx series are good for linux, this is equals to the Compaq X1000 and the HPQ nx7000 series

---

### Post by JLB on 2005-06-17
based on posts in these forums and mainly Thomas Schneller, i pulled the trigger on a nc6120 laptop today. I purchased the pr126ua model. I look forward to receiving it and running a fully supported laptop. Unfortunately, the HP folks here in the USA had no clue about Linux and the NC series laptops, What they were doing in Europe or even How I could get it with FreeDOS. We don't offer that although it is prominently displayed in the laptop description pages. Alas, I had to get XP and live without a pricebreak. :P

@ Thomas Schneller, I would be happy to provide feedback on the HP tweaked Ubuntu if needed. Feel free to contact me.

Regards!

JL

---

### Post by IcemanV9 on 2005-06-18
FYI - I have two HP laptops (N5430 and ze5185) at home. Ubuntu Hoary 5.04 are running fine on both. Just a few annoying problems that I have encountered:

_ze5185_
o blanking CD-RW disc doesn't work
o hibernate doesn't work
o limited special shortcut keys
o ati/radeon driver is outdated (couldn't get more than 500s FPS!) (i have done ati howto in other thread already - still doesn't work)

_N5430_
o hibernate doesn't work
o limited special shortcut keys
o when the battery ran out of juice, it just crashed instead of shutdown nicely. (it caused corrupted boot area)

---

### Post by grenier on 2005-06-18
[QUOTE=][/QUOTE]
 I've got a zv5000(zc5330ea) serie notebook. I installed under standard Hoary, and everything important works, but :
- after installing the 3D hardware drivers (nvidia), I had to manually tweak graphics settings to have 1200x800 - something to do with the display not correctly identifying itself.
- no SD card reader (but you knew that already). I hope it won't take long to be solved.
- no hotkeys, but I think I saw them appear in a log somewhere when I tried to use them. I'm guessing this is only a matter of associating an action to them (the wifi on/off button works, though).
- I use an USB external mouse. If I unplug and replug it, no luck. It has to be there from boot-up time.
- As I have no device to test them, I can't say anything about firewire and bluetooth, but they appear to be configured.
- I can't input sound (from a mike). But that last one may be untrue, since I have problem with the headset port (only one side working). But I'll have to reinstall windows to test it, which I'm not looking forward too.
- Hibernate works, but no suspend to RAM; that isn't specific to any laptop as I understand.

Of course, I only listed the issues, not everything else that worked.

---

### Post by phen on 2005-06-18
@JLB

look on the hardware laptop hewlett-packard pages for help with the nc6120. i just updated it yesterday. i ve got the same laptop, and it is working 100%

cheers,
kai

---

### Post by somez on 2005-06-18
Guys what about the HP ZT, or Compaq X1000 or HPQ 7000 series notebooks? They are great machines because of the wsxga screen, and as far as I know they are well supported by Ubuntu.

---

### Post by JLB on 2005-06-18
Thanks Phen! Will do.

---

### Post by funkenstein on 2005-06-19
quick note- my nx9005 works fine with Out-Of-The-Box-Hoary. I went through the standard upgrades and installs, as well as the [Automated Script](http://ubuntuforums.org/showthread.php?t=22646) ... I still have trouble with specific things like MultiMon and exernal soundcards and playing flac, but that's a S/W problem :p....

either way, downloading the HP-specific hoary now, then wait till I finish uni next week  ](*,)  and install and play and frolic!

---

### Post by jochen on 2005-06-23
Got recently an HP6220 and easily installed the HP-specific hoary. Mostly working fine. Not working is the external monitor output and the SD card reader.
Somewhat working is Suspend-to-ram, it doesn't work with from the logoff menu or using sleep. But closing the lid works. Not quite sure what closing lid actually is doing, but some kind of suspend it does.

Anyone have ideas what to try with the external monitor ?

---

### Post by jochen on 2005-06-24
[QUOTE=jochen]
Anyone have ideas what to try with the external monitor ?[/QUOTE]

Answering my own question.

What you need is
[http://sourceforge.net/projects/i855crt](http://sourceforge.net/projects/i855crt)
and also apply the i915 support patch to the source.

make and as root or sudo
i855crt swcursor on 1024x768@70
gets a better working external monitor. The picture could be clearer, not sure if this is due to the monitor or the given signal. Can't get a different resolution, but then this is the resolution of the laptop, although @75 there and not @70.

To get a working cursor you also need to change xorg.conf, add the Option 
"SWCursor" "1" like this:
Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        Option "SWCursor" "1"
        BusID           "PCI:0:2:0"
EndSection

---

### Post by somez on 2005-06-24
I think we should create a WIKI page for these kind of info, what do you think about this guys?
Maybe we only need to place links of the specifyc forum topics, it can be useful.

---

### Post by Gandalf on 2005-06-24
[QUOTE=somez]I think we should create a WIKI page for these kind of info, what do you think about this guys?
Maybe we only need to place links of the specifyc forum topics, it can be useful.[/QUOTE]
 Well i think a good page, maybe a blog with all HP-Ubuntu related tweaking would be cool, i vote for it and i can host it if anyone interrested

---

### Post by somez on 2005-06-24
[QUOTE=Gandalf]Well i think a good page, maybe a blog with all HP-Ubuntu related tweaking would be cool, i vote for it and i can host it if anyone interrested[/QUOTE]

I'm really interested in it. You think the ubuntu wiki is not suitable for this?

---

### Post by nictuku on 2005-06-24
For the record, I succeded installing ubuntu hoary in a HP "Compaq nx9005" laptop.

I had three issues, though:

1) Modem support. Fixed by using the hsf driver from [http://www.linuxant.com](http://www.linuxant.com). It's a proprietary and commercial driver, though. The FREE licence will only provide a 33.6kbps speed.

2) The keyboard needed customization to work. Using ABNT2 with no further setup had issues with some keys. The solution is to use some custom keymaps:

[http://www.cetico.org/wiki/doku.php?id=hp-nx9005-abnt2](http://www.cetico.org/wiki/doku.php?id=hp-nx9005-abnt2)

3) Very odd keyboard/mouse behaviour. Once in a while, only when I'm typing, the mouse pointer starts to click wherever it's standing. No, I'm not touching the mouse pad accidentaly. That is very frustrating while typing texts, like this one. I have to leave the mouse pointer somewhere it's harmless to click.

---

### Post by Gandalf on 2005-06-24
[QUOTE=somez]I'm really interested in it. You think the ubuntu wiki is not suitable for this?[/QUOTE]
 Yes maybe but if you need file hosting i mean for maybe drivers or something PM then i offer it

---

### Post by JLB on 2005-06-24
[QUOTE=nictuku]For the record, I succeded installing ubuntu hoary in a HP "Compaq nx9005" laptop.

I had three issues, though:

snip-----

3) Very odd keyboard/mouse behaviour. Once in a while, only when I'm typing, the mouse pointer starts to click wherever it's standing. No, I'm not touching the mouse pad accidentaly. That is very frustrating while typing texts, like this one. I have to leave the mouse pointer somewhere it's harmless to click.[/QUOTE]

I am having this same issue on a NC6120 Laptop. I have changed the driver to ImPS/2 for some testing. I have not yet pinpointed what the true cause is. But so far... no jumping/random clicking behavior has been noticed.

---

### Post by somez on 2005-06-25
[QUOTE=Gandalf]Yes maybe but if you need file hosting i mean for maybe drivers or something PM then i offer it[/QUOTE]

That's great! Who else wants to help us? :-)

---

### Post by fabe3k on 2005-07-16
Are there any plans for support for the nx6125?

---

### Post by senectus on 2005-07-16
By sheer chance and coincidence My company just bought me a nc6120 (with windows).
I'm downloading this: [http://cdimage.ubuntu.com/custom/20050516/hoary-install-i386.iso](http://cdimage.ubuntu.com/custom/20050516/hoary-install-i386.iso) 
Right now so I can throw it on :-D
The laptop isn't too bad.. with the exception of the LCD it's utter crap.. (1024x768) After having use my personal Think pad A31p with 1600x1200 res It's REALLY painful to use this one.
Another thing is that the colours seem really washed out.. Like there is too much white or something.. any idea's on how to fix that?


Also is there a newer image I can get from somewhere? it looks like that one was created on the 16th of May...

---

### Post by senectus on 2005-07-17
I just noticed that the laptop is a NX6120 not a NC6120, but I installed it anyway and it's worked an absolute treat :-D

Even the volume buttons work perfectly, when the "bog standard" install doesn't make them work.

---

### Post by senectus on 2005-07-18
Sorry for the reply to a reply of a reply.. but quick question..
Does this install of Ubuntu have "specially compiled" kernel?
If I download and install via synaptic the 686 kernel will it break some of the nice intergration that you HP guys have done?

---

### Post by Thomas Schneller on 2005-07-18
[QUOTE=senectus]Sorry for the reply to a reply of a reply.. but quick question..
Does this install of Ubuntu have "specially compiled" kernel?
If I download and install via synaptic the 686 kernel will it break some of the nice intergration that you HP guys have done?[/QUOTE]
 Yes, it has some kernel modifications. But as they are not HP specific but ACPI specific, they should be implemented in new kernel releases as well. So it should not break anything. But no promissis. I didn't trey it myselfe.

Best regards

Thomas

---

### Post by DW5 on 2005-07-18
[QUOTE=JLB]I am having this same issue on a NC6120 Laptop. I have changed the driver to ImPS/2 for some testing. I have not yet pinpointed what the true cause is. But so far... no jumping/random clicking behavior has been noticed.[/QUOTE]

I'm running a nx9010 and have this problem.  I've always chalked up to the base of my thumbs slightly brushing the mouse (so slightly I don't feel it, and it happened when I was on XP, too).  Does the driver change you made still seem to work?

---

### Post by senectus on 2005-07-19
[QUOTE=Thomas Schneller]Yes, it has some kernel modifications. But as they are not HP specific but ACPI specific, they should be implemented in new kernel releases as well. So it should not break anything. But no promissis. I didn't trey it myselfe.

Best regards

Thomas[/QUOTE]
Thanks for the reply.
I've done the update and it seems ok so far.. I haven't played with the power management stuff yet so no idea if it broke that.

What I _really_ want to work on is the LCD screen settings.. 
With your test case does the font's on yours look really ugly and "fuzzy/messy" ??

And is it possible to set the LCD to 32 bit colour.. the xorg.conf is only set to 24 bit..

---

### Post by iimre on 2005-07-28
Hi,

I'm using Thomas Schnellers' "custom image" (2005.06.27) on an nc6000. It's fine! Many thanks for Thomas and all who fine tuned it for hp notebooks. Now the question: Anybody used this with a bluetooth mouse? I'm planning to buy one, but only if it is working for sure. Any experience?

Thx

Imre

---

### Post by somez on 2005-07-28
[QUOTE=iimre]Hi,

I'm using Thomas Schnellers' "custom image" (2005.06.27) on an nc6000. It's fine! Many thanks for Thomas and all who fine tuned it for hp notebooks. Now the question: Anybody used this with a bluetooth mouse? I'm planning to buy one, but only if it is working for sure. Any experience?

Thx

Imre[/QUOTE]

I think the best way is to borrow on and try it, before you buying :-)

---

### Post by zsdian on 2005-07-28
[QUOTE=Thomas Schneller]Grab a copy here:

[http://cdimage.ubuntu.com/custom/20050516/hoary-install-i386.iso](http://cdimage.ubuntu.com/custom/20050516/hoary-install-i386.iso)[/QUOTE]

I was shopping for a new laptop and chose an HP nx6110 after I heard about this special version of Ubuntu for HP. (Mine came with a Win XP licence, that I can dual boot if I try hard). The HP Ubuntu works very nicely. I have yet to try the modem, wireless and remote monitor ports but the rest seems to work nicely.

There are some issues, hot keys are not directly supported and if I close the lid it gets pretty warm and the screen backlight appears to burn. I am sure most of this is easily fixed, I just have not had the time to play with it.

But I have some questions and comments:

- Please tell the sales people back at HP that they can cross one sale off the Windows count and add it on the Ubuntu Linux one.

- I note that there is as yet no advertised upgrade path. I installed the version dated 16 May 2005. I see there have been a couple of others released since. I have been cautious about upgrading packages with apt-get least I break some of the hardware specific functionality. Can we get a list of what packages are not safe to upgrade? Hopefully the list will get shorter, over time.

- How about an apt-get repository that has patched versions of the hardware specific packages? We could then add it onto the end of sources.list Choose version numbers so they just ahead of the corresponding official packages. When the patches are back ported, the patched versions can be dropped from the special repository.

- It would be nice to have a mailing list or forum dedicated to the "Thomas Schneller version" of Ubuntu. This thread is getting very long. We need a bit of space to discuss features and report bugs etc, a single thread is a bit limiting. A dedicated web page would not be a bad idea too. At least we could post the URL around when people start asking about suggestions for laptops. Can Ubuntu host something equivalent to a Sourceforge project?

I have no doubt that if there is a well supported version of a well supported Linux distribution, specific to a range of well priced, quality, readily available laptops, then the combination would become the first choice of many, who like myself, gave up on Windows years ago. But it must be kept as close a possible to the native upstream version, and it be upgraded when the upstream gets upgraded. 

Thanks for your efforts. You have planted a good seed. Let the community help keep it watered and it will grow into a tree that even HP can't help noticing.


Ian

---

### Post by netsyd on 2005-07-28
Has anyone given this a go with the NC4000? I'm interested in trying it out, but if it's not worth it (streamlined), I'll stick with my functional setup.

Thanks!

---

### Post by nixon on 2005-07-29
Hi,

I'm currently running breezy on an nc8230, there are lots of features in breezy that I wish to retain (but will go back to hoary if it has better support) when are we likely to see an apt-gettable HP package? Currently the only things that aren't working that well for me is wireless and hibernation.. both of which i can live without for now.. the wireless detects the networks fine but has trouble joining them (no idea why)..

if there is a package due to come out soonish I'd love to be able to stay on breezy..

Thanks in advance

Nixon

---

### Post by npaladin2000 on 2005-08-05
[QUOTE=nixon]Hi,

I'm currently running breezy on an nc8230, there are lots of features in breezy that I wish to retain (but will go back to hoary if it has better support) when are we likely to see an apt-gettable HP package? Currently the only things that aren't working that well for me is wireless and hibernation.. both of which i can live without for now.. the wireless detects the networks fine but has trouble joining them (no idea why)..

if there is a package due to come out soonish I'd love to be able to stay on breezy..

Thanks in advance

Nixon[/QUOTE]


Oh I wish you'd try the standard Hoary...I'm considering buying the very same laptop.  I've got a Thinkpad T42, but I miss having a widescreen, and an "eraserhead" is an absolute necessity for me.  Are you using the Intel or Broadcom wireless?

---

### Post by kristian on 2005-08-05
[QUOTE=Thomas Schneller]Grab a copy here:

[http://cdimage.ubuntu.com/custom/20050516/hoary-install-i386.iso](http://cdimage.ubuntu.com/custom/20050516/hoary-install-i386.iso)[/QUOTE]
 I've already got Breezy installed on my HP nx9105 and everything is working (even the sd-card reader) exept the time estimations when using the gnome-panel applet for battery status. Is this something that's fixed in the hp-ubuntu distribution?

---

### Post by JLB on 2005-08-06
[QUOTE=DW5]I'm running a nx9010 and have this problem.  I've always chalked up to the base of my thumbs slightly brushing the mouse (so slightly I don't feel it, and it happened when I was on XP, too).  Does the driver change you made still seem to work?[/QUOTE]
a little bit better now, but some other issues remained. i went back to the bog standard configuration and learned to live with it. I use an external mouse now. it is in my opinion a driver issue still. I taped a piece of plexiglass over the mouse touchpad so *I definitely could not* touch it accidently. during a lengthy paper authoring session i had the mouse jump/click on me.

Maybe something in breezy will make it all better  :D.

---

### Post by DW5 on 2005-08-08
I hope so.  It is a really annoying trait, and when writing on a roll a true pain in the rump.

DW

---

### Post by DW5 on 2005-08-10
I have an nx9010 and did a presentation last night on a projector.  I booted with the projector plugged in and the computer automatically rerouted the video feed to the projector, leaving its own lcd blank.  I couldn't get an FN key combos to switch from projector to screen or to merely display the content on both.  

I would like to be able to face my class and manipulate the computer projecting the image behind me. 

What do I need to do to toggle both the video out and the monitor on.

Thanks for any help.

DW

---

### Post by phen on 2005-08-10
try to boot without external display plugged in. plug the projecter in afterwards, and try to press the  fn+displayswitch key. i am using an nc6120, and this helps changing the behaviour (allthough i dont have the same problem as you!)

or try to use the fn+displayswitch during bios/grub/console bootup. it has a different behaviour then, too.

kai

---

### Post by DW5 on 2005-08-10
I can see both screens by booting first and then hooking up the projector.  That will work.

However the fn+switchkey doesn't do anything.

Thanks.

DW

---

### Post by locutus42 on 2005-08-11
[QUOTE=kristian]I've already got Breezy installed on my HP nx9105 and everything is working (even the sd-card reader) exept the time estimations when using the gnome-panel applet for battery status. Is this something that's fixed in the hp-ubuntu distribution?[/QUOTE]

Kristian,  do you have any info on what/how you got the SD-card reader working? I have a Compaq R4000 with the SD-Card reader and would like to enable that. Thanks.

---

### Post by locutus42 on 2005-08-15
Does anybody have the 6:1 memory card reader working on HP/Compaq laptops? If so, could you explain how or point to information on this. Thanks.

Thanks

---

### Post by phen on 2005-08-15
unfortunately, there are no linux drivers available for the texas instruments card reader of hp's buisiness laptops.

you won't get it to work atm, afaik.

cheers,

kai

---

### Post by locutus42 on 2005-08-15
[QUOTE=jochen]Anyone have ideas what to try with the external monitor ?[/QUOTE]

Maybe this will help( NOTE: 2 monitor sections and the "DesktopSetup" option(s) ):

parts of my xorg.conf file:

# **********************************************************************
# Monitor section
# **********************************************************************
Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5 - 60.0
    VertRefresh 60 - 85
    Option "DPMS"
EndSection

Section "Monitor"
    Identifier  "Monitor1"
    HorizSync   31.5 - 60.0
    VertRefresh 60 - 85
    Option "DPMS"
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************
# === ATI device section ===
Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
#    Option "DesktopSetup"               "0x00000200"  #horizontal LCD=primary
#    Option "DesktopSetup"               "0x00000201"  #horizontal LCD=secondary
#    Option "DesktopSetup"               "0x00000300"  #virtical LCD=primary
#    Option "DesktopSetup"               "0x00000301"  #virtical LCD=secondary
#    Option "DesktopSetup"               "0x00000100"  #clone
#    Option "DesktopSetup"               "0x00000000"  #single
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "31.5 - 60.0" 
    Option "VRefresh2"                  "60 - 85" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "no"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
#    BusID "PCI:1:0:0"    # no device found at config time
    BusID "PCI:1:5:0"    # no device found at config time
    Screen 0
EndSection

---

### Post by Rob2687 on 2005-08-15
How is this different from the regular Hoary? I wonder if it will work with my compaq n600c....

---

### Post by phen on 2005-08-16
rob, please read the beginnings of this thread. there are links posted where it is explained which notebooks are supported!

afaik mainly the buisiness notebooks, because they have slower release cycles...

cheers,

kai

---

### Post by srijith on 2005-08-16
Has anyone successfully upgraded the kernel of an HP customised install from the basic 2.6.10-5-386? In particular I am concerned if the acpi, LED stuffs will still work with the new kernel.

---

### Post by infinito on 2005-08-16
Has anyone tried the HP Custom Ubuntu CD on a nx8220 or nc8230 or simliar one?
I saw the CD seems to be for nc6xx0 series, so i'm not sure if it will break something in these laptops...

---

### Post by sigma2805 on 2005-08-16
has anyone tried this on a compaq? i have a m2010us

---

### Post by tobiase on 2005-08-16
I have installed the hp-version of ubuntu on my nx8220, In general, it works great. Although i haven't got the accellerated fglrx drivers to work yet.
I haven't really tried out the ACPI suspend modes yet either..

Some users of this laptop has experienced a annoying high pith noice when running on battery power, a (quite dirty) fix for this is described at
[http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=907758](http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=907758) 


Cheers,
Tobias

---

### Post by infinito on 2005-08-17
Here are the diffrences between the original Hoary cd and the HP Custom cd.
Just some new packages and a few fixes.
```

--- ubuntu-5.04-install-i386.list	2005-08-17 13:00:36.981004800 +0200
+++ hoary-hp-install-i386.list	2005-08-17 13:00:03.670068832 +0200
@@ -1,5 +1,6 @@
-/README.diskdefines
 /isolinux/boot.cat
+/isolinux/isolinux.bin
+/README.diskdefines
 /isolinux/f1.txt
 /isolinux/f10.txt
 /isolinux/f2.txt
@@ -10,7 +11,6 @@
 /isolinux/f7.txt
 /isolinux/f8.txt
 /isolinux/f9.txt
-/isolinux/isolinux.bin
 /isolinux/isolinux.cfg
 /isolinux/isolinux.txt
 /isolinux/splash.rle
@@ -276,7 +276,6 @@
/pool/restricted/l/linux-restricted-modules-2.6.10/nic-restricted-modules-2.6.10-5-386-di_2.6.10.5-1_i386.udeb
 /pool/main/a/aalib/aalib1_1.4p5-22_i386.deb
 /pool/main/a/acl/libacl1_2.2.26-1_i386.deb
-/pool/main/a/acpi-support/acpi-support_0.21_i386.deb
 /pool/main/a/acpi/acpi_0.07-3_i386.deb
 /pool/main/a/acpid/acpid_1.0.4-1ubuntu4_i386.deb
 /pool/main/a/adduser/adduser_3.59_all.deb
@@ -320,6 +319,9 @@
 /pool/main/b/binutils/binutils_2.15-5ubuntu2_i386.deb
 /pool/main/b/bittorrent/bittorrent_3.4.2-3ubuntu4_all.deb
 /pool/main/b/blt/blt_2.4z-3ubuntu1_i386.deb
+/pool/main/b/bluez-libs/libbluetooth1_2.11-1_i386.deb
+/pool/main/b/bluez-pin/bluez-pin_0.24-1_i386.deb
+/pool/main/b/bluez-utils/bluez-utils_2.10-5ubuntu3_i386.deb
 /pool/main/b/bogofilter/bogofilter_0.93.3.snapshot20050105a-1_i386.deb
 /pool/main/b/bpalogin/bpalogin_2.0.2-3ubuntu1_i386.deb
 /pool/main/b/bsd-finger/finger_0.17-7_i386.deb
@@ -517,6 +519,7 @@
 /pool/main/g/gimp/libgimp2.0_2.2.2-1ubuntu5_i386.deb
 /pool/main/g/gksu/gksu_1.2.4-1ubuntu8_i386.deb
 /pool/main/g/gle/libgle3_3.1.0-5_i386.deb
+/pool/main/g/glib1.2/libglib1.2_1.2.10-9_i386.deb
 /pool/main/g/glib2.0/libglib2.0-0_2.6.3-1_i386.deb
 /pool/main/g/glib2.0/libglib2.0-data_2.6.3-1_all.deb
 /pool/main/g/glibc/libc6-dev_2.3.2.ds1-20ubuntu13_i386.deb
@@ -1212,6 +1215,7 @@
 /pool/main/s/scrollkeeper/libscrollkeeper0_0.3.14-9.1_i386.deb
 /pool/main/s/scrollkeeper/scrollkeeper_0.3.14-9.1_i386.deb
 /pool/main/s/sed/sed_4.1.2-8_i386.deb
+/pool/main/s/setserial/setserial_2.17-39_i386.deb
 /pool/main/s/sgml-base/sgml-base_1.26_all.deb
 /pool/main/s/sgml-data/sgml-data_2.0.2-0ubuntu2_all.deb
 /pool/main/s/shadow/login_4.0.3-30.7ubuntu16_i386.deb
@@ -1376,6 +1380,16 @@
 /pool/main/z/zenity/zenity_2.10.0-0ubuntu1_i386.deb
 /pool/main/z/zip/zip_2.30-8_i386.deb
 /pool/main/z/zlib/zlib1g_1.2.2-4ubuntu1_i386.deb
+/pool/local/a/acpi-support/acpi-support_0.21.2_i386.deb
+/pool/local/g/gnome-bluetooth/gnome-bluetooth_0.5.1-1ubuntu7_i386.deb
+/pool/local/g/gnome-bluetooth/libgnomebt0_0.5.1-1ubuntu7_i386.deb
+/pool/local/h/hp6xx0/hp6xx0_0.2-2_i386.deb
+/pool/local/i/i810switch/i810switch_0.6.2-2ubuntu1_i386.deb
+/pool/local/i/irda-utils/irda-utils_0.9.16-8_i386.deb
+/pool/local/libb/libbtctl/libbtctl1_0.4.1-1ubuntu3_i386.deb
+/pool/local/libb/libbtctl/python2.4-libbtctl_0.4.1-1ubuntu3_i386.deb
+/pool/local/libo/libopenobex1.0/libopenobex-1.0-0_1.0.0-rel-3_i386.deb
+/pool/local/s/sl-modem/sl-modem-daemon_2.9.9a-1ubuntu4.1_i386.deb
 /pool/restricted/d/drdsl/drdsl_1.0.3-2ubuntu1_i386.deb
 /pool/restricted/l/linux-meta/avm-fritz-firmware_2.6.10-7_i386.deb
 /pool/restricted/l/linux-meta/linux-386_2.6.10-7_i386.deb

```

---

### Post by sigma2805 on 2005-08-19
ok,
i installed it on my compaq m2010us. So far everything looks to be good...the FN key works for the brightness of the screen and stuff(not sure if this is hardware related). When i tried to go into hibernation, the computer went to sleep but i couldn't pull it out of hibernation. I tried pushing the power button but that didn't bring it back. Any suggestions?

---

### Post by Ptero-4 on 2005-08-19
[QUOTE=sigma2805]ok,
i installed it on my compaq m2010us. So far everything looks to be good...the FN key works for the brightness of the screen and stuff(not sure if this is hardware related). When i tried to go into hibernation, the computer went to sleep but i couldn't pull it out of hibernation. I tried pushing the power button but that didn't bring it back. Any suggestions?[/QUOTE]
 Hi. Tomas if you're still there. Does the Pavilion 734n support Ubuntu? My sister got a Pavilion 734n and I tried to put Ubuntu on it right away but faced some BIG PROBLEMS. the first time I tried to install ubuntu I resized the WinXP partition and created another one (formatted with ntfs), rebooted , formatted the partition, added some files and rebooted again twice and the partition was still there. Confident enough I backed the stuff up and installed ubuntu (deleted the ntfs partition and put ubuntu on it) but when the install was done and the installer instructed me to reboot the PC. When I rebooted I saw some odd messages stating something like "Microsoft Rights Management system" and then some more like "non-Windows partition or hard drive device detected. Device have been converted to windows format" among the BIOS messages (In the initial screen where you see the messages stating the amount of RAM the PC have installed) and then it booted into WinXP WITHOUT GOING INTO GRUB. I rebooted with the Ubuntu LiveCD and ran fdisk (yes I know my way around those tools) and got shocked at what I saw. The Ubuntu partitions weren't there. It was like if I never did the partitioning. I rebooted twice without the LiveCD and the odd messages didn't appeared anymore. I tried to install Ubuntu again. This time I took photographies of each step I did when I got to the partitioner so that If the partitions vanished again I could review the process and see if I did something wrong (like forgetting about writitng the new partition table to disk b4 leaving the partitioner). I reviewed the photos b4 rebooting the PC and according to them I had done every step right. I rebooted and you guess it. Those odd BIOS messages appeared again and the partitions were gone again. I went mad and wiped the HD clean (destroying the HP restore partition with it) and reinstalled. This time the partitions stayed there but the BIOS messages appeared and there were a new one like "Device format conversion failed. Resorting to automatic hardware lockdown mode"
and then something like "Modem disabled", "Networking disabled", "Floppy device disabled", "Disaplay parameters spoofed" and some more like those. It booted into grub this time and finished the installation but when it went to show the desktop it blinked several times and the I had to go to tty1 and stop gdm. I went to the xorg.conf file and realized that the display refresh rates (both vertical and horizontal) were very high. I copied the xorg.conf to xorg.conf.custom and appended some lower settings also changed the driver (set to i810 which is incorrect since the Pavilion have a Nvidia not an intel chipset) to vesa and gave it lower bitdepth. restarted gdm and finally it started the GUI. But I found that the floppy, nic and modem were not working (there was no entry for the floppy in /etc/fstab, obviously odd, I added it and rebooted but the floppy just wasn't working (Hey it's got a single drive in the standard place in the IDE ribbon how can it not mount when you put a fsckin' floppy in it and it have the settings that has worked for all the PCs that have a single floppy drive in the same place in the IDE cable), It just would not mount even if you had a floppy in it). Right now that $PC is sitting in the closet since if it won't allow me to use WHAT I WANT and not WHAT A BASTARD RICH AND CORRUPT GEEK WITH NAPOLEONIC DELUSSIONS WANTS ME TO USE. I won't turn it on never again.

P.d: If installing Linux on that POS Pavilion PC involves wiping the HD and otherwise tampering with the machine guts just to keep it from deleting the Linux partitions and reformatting them with FAT/NTFS as soon as it's rebooted after the partitions are created, and making the graphics and floppy drive (things that are extremelly idiot proof under modern distros) requires gutting half of the Linux structure and moving config files around so that the Pavilion is unable to re-screw up the files. Then I don't want to even imagine the work involved in making work the more complex components of this PC AND KEEPING THEM WORKING. And IANAL but those BIOS messages basically say that the PC itself was programmed to scan it's HD on boot and kill Linux partitions on sight and in case it can't do it (like what happened when I deleted the hp restore partition) to spoof, deactivate and otherwise mess up it's own hardware so that using Linux becomes a painfull option b/c of the intentional incompatibilities the PC creates itself. Sorry Tom. you may be trying to get your company computers compatible with Ubuntu but your boss screwed up the Pavilion line and lost some customers (I'm not the only one that got this POS PC, my college got a bunch of them to put Ubuntu on them and put them in the computer lab but seing this issues they took those PC back for a refund and got the other two local colleges and the gov to do the same with their recently purchased Pavilion 734n units). As for me I'm waiting to see how this ends up to see if there's some hope that the Pavilion can come out of the closet and in the desk again.

---

### Post by sigma2805 on 2005-08-20
Hmmm...windows rights management? thats odd. perhaps you should call HP and find out if they have some sort of BIOS chip that prevents changes to the BIOS or hardware. Also, go into the BIOS and see if you can disable that. hmm...actually...HP probably won't provide support if you tell them you are trying to install Ubuntu. I searched for Microsoft Rights Management System on google and mostly it refers to files that you create in say office. you can control who views those files.


[QUOTE=Ptero-4]Hi. Tomas if you're still there. Does the Pavilion 734n support Ubuntu? My sister got a Pavilion 734n and I tried to put Ubuntu on it right away but faced some BIG PROBLEMS. the first time I tried to install ubuntu I resized the WinXP partition and created another one (formatted with ntfs), rebooted , formatted the partition, added some files and rebooted again twice and the partition was still there. Confident enough I backed the stuff up and installed ubuntu (deleted the ntfs partition and put ubuntu on it) but when the install was done and the installer instructed me to reboot the PC. When I rebooted I saw some odd messages stating something like "Microsoft Rights Management system" and then some more like "non-Windows partition or hard drive device detected. Device have been converted to windows format" among the BIOS messages (In the initial screen where you see the messages stating the amount of RAM the PC have installed) and then it booted into WinXP WITHOUT GOING INTO GRUB. I rebooted with the Ubuntu LiveCD and ran fdisk (yes I know my way around those tools) and got shocked at what I saw. The Ubuntu partitions weren't there. It was like if I never did the partitioning. I rebooted twice without the LiveCD and the odd messages didn't appeared anymore. I tried to install Ubuntu again. This time I took photographies of each step I did when I got to the partitioner so that If the partitions vanished again I could review the process and see if I did something wrong (like forgetting about writitng the new partition table to disk b4 leaving the partitioner). I reviewed the photos b4 rebooting the PC and according to them I had done every step right. I rebooted and you guess it. Those odd BIOS messages appeared again and the partitions were gone again. I went mad and wiped the HD clean (destroying the HP restore partition with it) and reinstalled. This time the partitions stayed there but the BIOS messages appeared and there were a new one like "Device format conversion failed. Resorting to automatic hardware lockdown mode"
and then something like "Modem disabled", "Networking disabled", "Floppy device disabled", "Disaplay parameters spoofed" and some more like those. It booted into grub this time and finished the installation but when it went to show the desktop it blinked several times and the I had to go to tty1 and stop gdm. I went to the xorg.conf file and realized that the display refresh rates (both vertical and horizontal) were very high. I copied the xorg.conf to xorg.conf.custom and appended some lower settings also changed the driver (set to i810 which is incorrect since the Pavilion have a Nvidia not an intel chipset) to vesa and gave it lower bitdepth. restarted gdm and finally it started the GUI. But I found that the floppy, nic and modem were not working (there was no entry for the floppy in /etc/fstab, obviously odd, I added it and rebooted but the floppy just wasn't working (Hey it's got a single drive in the standard place in the IDE ribbon how can it not mount when you put a fsckin' floppy in it and it have the settings that has worked for all the PCs that have a single floppy drive in the same place in the IDE cable), It just would not mount even if you had a floppy in it). Right now that $PC is sitting in the closet since if it won't allow me to use WHAT I WANT and not WHAT A BASTARD RICH AND CORRUPT GEEK WITH NAPOLEONIC DELUSSIONS WANTS ME TO USE. I won't turn it on never again.

P.d: If installing Linux on that POS Pavilion PC involves wiping the HD and otherwise tampering with the machine guts just to keep it from deleting the Linux partitions and reformatting them with FAT/NTFS as soon as it's rebooted after the partitions are created, and making the graphics and floppy drive (things that are extremelly idiot proof under modern distros) requires gutting half of the Linux structure and moving config files around so that the Pavilion is unable to re-screw up the files. Then I don't want to even imagine the work involved in making work the more complex components of this PC AND KEEPING THEM WORKING. And IANAL but those BIOS messages basically say that the PC itself was programmed to scan it's HD on boot and kill Linux partitions on sight and in case it can't do it (like what happened when I deleted the hp restore partition) to spoof, deactivate and otherwise mess up it's own hardware so that using Linux becomes a painfull option b/c of the intentional incompatibilities the PC creates itself. Sorry Tom. you may be trying to get your company computers compatible with Ubuntu but your boss screwed up the Pavilion line and lost some customers (I'm not the only one that got this POS PC, my college got a bunch of them to put Ubuntu on them and put them in the computer lab but seing this issues they took those PC back for a refund and got the other two local colleges and the gov to do the same with their recently purchased Pavilion 734n units). As for me I'm waiting to see how this ends up to see if there's some hope that the Pavilion can come out of the closet and in the desk again.[/QUOTE]

---

### Post by srijith on 2005-08-20
[QUOTE=infinito]Here are the diffrences between the original Hoary cd and the HP Custom cd.
Just some new packages and a few fixes.
```

--- ubuntu-5.04-install-i386.list	2005-08-17 13:00:36.981004800 +0200
+++ hoary-hp-install-i386.list	2005-08-17 13:00:03.670068832 +0200
@@ -1,5 +1,6 @@
-/README.diskdefines
 /isolinux/boot.cat
+/isolinux/isolinux.bin
+/README.diskdefines
 /isolinux/f1.txt
 /isolinux/f10.txt
 /isolinux/f2.txt
@@ -10,7 +11,6 @@
 /isolinux/f7.txt
 /isolinux/f8.txt
 /isolinux/f9.txt
-/isolinux/isolinux.bin
 /isolinux/isolinux.cfg
 /isolinux/isolinux.txt
 /isolinux/splash.rle
@@ -276,7 +276,6 @@
/pool/restricted/l/linux-restricted-modules-2.6.10/nic-restricted-modules-2.6.10-5-386-di_2.6.10.5-1_i386.udeb
 /pool/main/a/aalib/aalib1_1.4p5-22_i386.deb
 /pool/main/a/acl/libacl1_2.2.26-1_i386.deb
-/pool/main/a/acpi-support/acpi-support_0.21_i386.deb
 /pool/main/a/acpi/acpi_0.07-3_i386.deb
 /pool/main/a/acpid/acpid_1.0.4-1ubuntu4_i386.deb
 /pool/main/a/adduser/adduser_3.59_all.deb
@@ -320,6 +319,9 @@
 /pool/main/b/binutils/binutils_2.15-5ubuntu2_i386.deb
 /pool/main/b/bittorrent/bittorrent_3.4.2-3ubuntu4_all.deb
 /pool/main/b/blt/blt_2.4z-3ubuntu1_i386.deb
+/pool/main/b/bluez-libs/libbluetooth1_2.11-1_i386.deb
+/pool/main/b/bluez-pin/bluez-pin_0.24-1_i386.deb
+/pool/main/b/bluez-utils/bluez-utils_2.10-5ubuntu3_i386.deb
 /pool/main/b/bogofilter/bogofilter_0.93.3.snapshot20050105a-1_i386.deb
 /pool/main/b/bpalogin/bpalogin_2.0.2-3ubuntu1_i386.deb
 /pool/main/b/bsd-finger/finger_0.17-7_i386.deb
@@ -517,6 +519,7 @@
 /pool/main/g/gimp/libgimp2.0_2.2.2-1ubuntu5_i386.deb
 /pool/main/g/gksu/gksu_1.2.4-1ubuntu8_i386.deb
 /pool/main/g/gle/libgle3_3.1.0-5_i386.deb
+/pool/main/g/glib1.2/libglib1.2_1.2.10-9_i386.deb
 /pool/main/g/glib2.0/libglib2.0-0_2.6.3-1_i386.deb
 /pool/main/g/glib2.0/libglib2.0-data_2.6.3-1_all.deb
 /pool/main/g/glibc/libc6-dev_2.3.2.ds1-20ubuntu13_i386.deb
@@ -1212,6 +1215,7 @@
 /pool/main/s/scrollkeeper/libscrollkeeper0_0.3.14-9.1_i386.deb
 /pool/main/s/scrollkeeper/scrollkeeper_0.3.14-9.1_i386.deb
 /pool/main/s/sed/sed_4.1.2-8_i386.deb
+/pool/main/s/setserial/setserial_2.17-39_i386.deb
 /pool/main/s/sgml-base/sgml-base_1.26_all.deb
 /pool/main/s/sgml-data/sgml-data_2.0.2-0ubuntu2_all.deb
 /pool/main/s/shadow/login_4.0.3-30.7ubuntu16_i386.deb
@@ -1376,6 +1380,16 @@
 /pool/main/z/zenity/zenity_2.10.0-0ubuntu1_i386.deb
 /pool/main/z/zip/zip_2.30-8_i386.deb
 /pool/main/z/zlib/zlib1g_1.2.2-4ubuntu1_i386.deb
+/pool/local/a/acpi-support/acpi-support_0.21.2_i386.deb
+/pool/local/g/gnome-bluetooth/gnome-bluetooth_0.5.1-1ubuntu7_i386.deb
+/pool/local/g/gnome-bluetooth/libgnomebt0_0.5.1-1ubuntu7_i386.deb
+/pool/local/h/hp6xx0/hp6xx0_0.2-2_i386.deb
+/pool/local/i/i810switch/i810switch_0.6.2-2ubuntu1_i386.deb
+/pool/local/i/irda-utils/irda-utils_0.9.16-8_i386.deb
+/pool/local/libb/libbtctl/libbtctl1_0.4.1-1ubuntu3_i386.deb
+/pool/local/libb/libbtctl/python2.4-libbtctl_0.4.1-1ubuntu3_i386.deb
+/pool/local/libo/libopenobex1.0/libopenobex-1.0-0_1.0.0-rel-3_i386.deb
+/pool/local/s/sl-modem/sl-modem-daemon_2.9.9a-1ubuntu4.1_i386.deb
 /pool/restricted/d/drdsl/drdsl_1.0.3-2ubuntu1_i386.deb
 /pool/restricted/l/linux-meta/avm-fritz-firmware_2.6.10-7_i386.deb
 /pool/restricted/l/linux-meta/linux-386_2.6.10-7_i386.deb

```[/QUOTE]
 So that would mean, I guess that upgrading the kernel packages, as needed by the latest upgrades, would not stop anything from working! Great.

---

### Post by locutus42 on 2005-08-20
[QUOTE=sigma2805]Hmmm...windows rights management? thats odd. perhaps you should call HP and find out if they have some sort of BIOS chip that prevents changes to the BIOS or hardware. Also, go into the BIOS and see if you can disable that. hmm...actually...HP probably won't provide support if you tell them you are trying to install Ubuntu. I searched for Microsoft Rights Management System on google and mostly it refers to files that you create in say office. you can control who views those files.[/QUOTE]

There should be NO reason for HP to not support their hardware and software( OS and APPS shipped ). But, it sounds pretty fishy that a new NTFS partition had no effect while an ext2/3 partition was rejected. This could be a new trick to limit GNU/Linux expansion...  Hopefully, there's something in the BIOS where this "feature" can be turned OFF. Otherwise, the orginal poster should call HP and ask why he/she can't put another operating system or filesystem on the computer. Tell them you need a secure and trustworthy operating system and filesystem for one of their work related projects...

---

### Post by Ptero-4 on 2005-08-21
[QUOTE=locutus42]There should be NO reason for HP to not support their hardware and software( OS and APPS shipped ). But, it sounds pretty fishy that a new NTFS partition had no effect while an ext2/3 partition was rejected. This could be a new trick to limit GNU/Linux expansion...  Hopefully, there's something in the BIOS where this "feature" can be turned OFF. Otherwise, the orginal poster should call HP and ask why he/she can't put another operating system or filesystem on the computer. Tell them you need a secure and trustworthy operating system and filesystem for one of their work related projects...[/QUOTE]
 I'm the original poster of that post. I DID call HP and they told me that they won't support Linux. I told them that I needed a more secure OS and all I got was a lecture about how Windoze was a better solution. I think that the problem here is that the HP management people is too tied to the M$ politics, like Compaq was when they were a separate company. The same happens in DELL and I know b/c I used to be tech support in Dells call center and each time a customer called complaining that his/her PC wasn't compatible with Linux I had to answer them that I couldn't do shit b/c the Dell management's always in bed with BillG. And beleive me I always felt bad about not being able to solve their issues (If the issue was a hw problem I always covered the cost b/c dells and HP politic is that if you have a non-M$ OS in your hd your warranty is "void" even if you never openend the PC or did broke it intentionally). Basically I do see a reason for HP to put such a thing in their machines and like you said it is indeed a new M$ trick to limit GNU/Linux usability and I think that there's no place in the BIOS to turn it OFF (what's the point for M$ in putting bobby traps if they will put controls to disable them and put them in the most obvious place). Also sigma2805 MS drm is one of the common names for this TCPA/Palladium thing. AFAIK there's a preliminar version of that shipping in the M$ friendly branded PC's like HP/Dell the reason why google didn't got it is b/c M$ put a robots.txt in the part of their servers that holds the documentation for their TCPA plans.

---

### Post by locutus42 on 2005-08-21
[QUOTE=Ptero-4]I'm the original poster of that post. I DID call HP and they told me that they won't support Linux. I told them that I needed a more secure OS and all I got was a lecture about how Windoze was a better solution. I think that the problem here is that the HP management people is too tied to the M$ politics, like Compaq was when they were a separate company. The same happens in DELL and I know b/c I used to be tech support in Dells call center and each time a customer called complaining that his/her PC wasn't compatible with Linux I had to answer them that I couldn't do shit b/c the Dell management's always in bed with BillG. And beleive me I always felt bad about not being able to solve their issues (If the issue was a hw problem I always covered the cost b/c dells and HP politic is that if you have a non-M$ OS in your hd your warranty is "void" even if you never openend the PC or did broke it intentionally). Basically I do see a reason for HP to put such a thing in their machines and like you said it is indeed a new M$ trick to limit GNU/Linux usability and I think that there's no place in the BIOS to turn it OFF (what's the point for M$ in putting bobby traps if they will put controls to disable them and put them in the most obvious place). Also sigma2805 MS drm is one of the common names for this TCPA/Palladium thing. AFAIK there's a preliminar version of that shipping in the M$ friendly branded PC's like HP/Dell the reason why google didn't got it is b/c M$ put a robots.txt in the part of their servers that holds the documentation for their TCPA plans.[/QUOTE]

Please post your story to [www.linuxtoday.com](www.linuxtoday.com), This way, the word gets out about this new trick to keep Linux off OEM hardware at the BIOS layer.

---

### Post by nocturn on 2005-08-22
Hi Ptero

Maybe you can try to reach Thomas by private message, this is pretty big...
I bought a HP Pavilion that is working very well, just because HP was beginning to support Linux.

---

### Post by cossidhon on 2005-08-22
Thomas,

You told us in this tread there is no special HP stuff in this build, just kernel settings specific to ACPI. Could you please specify these here, so I can build my own kernel based on these settings on Kubuntu?

What I miss most is not being able to resume succesfully from acpi S3 (suspend to RAM) and i've read in this thread you guys fixed this. how?

Thanx!!

---

### Post by TimelessRogue on 2005-08-27
Just this afternoon downloaded and installed Hoary on an older HP Pavilion n5000 with excellent success ... particularly as compared to a number of other "vendors" (RedHat, Gentoo, Debian as well as others over the years including Fedora 4 most recently).  Booted right in and all is working well although I'm working on network, modem and wireless configurations.  Full screen resolution also, but VERY satisfied at this point.

I'm sure, after having a look around these forums, that all I need to know concerning any setups or problems will be answered here ... and thanks in advance to all.

Still have Win 2000 Pro on a small NFTS partition but will probably lose that as soon as everything else is up and running.  Or not ... don't really need the room.

I'll let you know how it all comes together ...

By the way, this a Pavilion n5000 Model GE with AMD Athlon XP 1100 on an Omnibook N32N-736 board with a Phoenix GE.M1.03 bios, 512 megs of memory, Trident Video Accelerator CyberBlade-XP display, ESS ES56CVM-PI Data Fax Voice Modem , Accton EN2242 Series MiniPCI Fast Ethernet Adapter with a Memorex USB wireless mouse.

Update:  For a few months now have been using Dapper Drake (doing daily updates 'til the final release came out) with no problems other than the continuing screen setup/resolution situation with the Trident Cyberblade XP (which I am having absolutely NO luck with ... just not getting full screen and there's just no help for this at either HP or Trident!).  So I guess I can report that all is relatively well and I am pretty much totally satisfied with Ubuntu!

---

### Post by locutus42 on 2005-08-27
[QUOTE=cossidhon]Thomas,

You told us in this tread there is no special HP stuff in this build, just kernel settings specific to ACPI. Could you please specify these here, so I can build my own kernel based on these settings on Kubuntu?

What I miss most is not being able to resume succesfully from acpi S3 (suspend to RAM) and i've read in this thread you guys fixed this. how?

Thanx!![/QUOTE]


I'm also interested in these HP ACPI tweaks. I'd like to try them on the R4000.

---

### Post by JLB on 2005-09-07
Has anyone seen or heard from Thomas Schneller as of late? I would love to see an update from him regarding what is being done with Breezy/HP and if the "HP-ized Hoary packages were ever made available.

Regards!
JL

p.s.  And before you ask... Yes, I did email Thomas directly a few times, but to no avail. :(

---

### Post by taj on 2005-09-08
[QUOTE=srijith]So that would mean, I guess that upgrading the kernel packages, as needed by the latest upgrades, would not stop anything from working! Great.[/QUOTE]

I had some hd problems after the [kernel update of 19 Aug](http://ubuntuforums.org/showthread.php?p=338475). I opened a new thread for this (end result: I had to reinstall ubuntu and certainly NOT update the kernel)

---

### Post by spud7 on 2005-09-13
hello,
i am planning to buy an nc8220 and would like to know if anyone has any experience with ubuntu and this model.
i don´t think that it is much different from i.e. the nc6220 but i am curious  O:) 

michael

---

### Post by infinito on 2005-09-13
[QUOTE=spud7]hello,
i am planning to buy an nc8220 and would like to know if anyone has any experience with ubuntu and this model.
i don´t think that it is much different from i.e. the nc6220 but i am curious  O:) 

michael[/QUOTE]
 Take a look here: [https://wiki.ubuntu.com/LaptopTestingTeam/](https://wiki.ubuntu.com/LaptopTestingTeam/)
Maybe you can find something interesting.

---

### Post by JLB on 2005-09-14
If it is anything like my NC6120 (apparently it is in the same family,) you will love it. Using Breezy makes it even better than the HP-ied Hoary too. most everything out of the box is supported. The rest is done with some very minor editing. If you like, see my wiki page [https://wiki.ubuntu.com/LaptopTestingTeam/HPNC6120](https://wiki.ubuntu.com/LaptopTestingTeam/HPNC6120) reagrding my NC6120. I have some decent notes in there about it.

About the only thing I have left to complain about is resume from hibernate when on AC power. The laptop locks up. It works great on battery though :)

---

### Post by Ptero-4 on 2005-09-14
I gave the story to a friend in my college and he posted it in his blog. He says that he will post it in Linuxtoday and then delete it from his blog.

P.d: I was about to post my story to linuxtoday but my ISP was taken down recently due to some legal issues they were having.  And the only way to get on the internet is using a friends iBook G3 500MHz to connect through the college wireless network. I didn't want to post from the college b/c the college has only one wireless access point and it happens to be located in the corridor that leads to the college's Microsoft certification training room and I don't want any M$ employee that happens to come through that corridor to look at the laptop screen and see what I'm posting on the internet (you'll surelly know why I don't want that to happen)

---

### Post by phen on 2005-09-16
JLB: resuming from hibernate is no problem for me! please see the wiki: 

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard)

section nc6120!

you'll find a page where i explain how to fix the hibernation!

cheers

---

### Post by JLB on 2005-09-16
* To get Hibernation (Suspend to disk) to work, I had to change the last line of /etc/default/acpi-support to: STOP_SERVICES="mysql irda-utils"

Done that. No joy on Breezy :) At least not while on AC power. Its OK on battery.

Got any other tips? I'd be happy to see them. Thanks Phen!

---

### Post by JLB on 2005-09-16
[QUOTE=JLB]* To get Hibernation (Suspend to disk) to work, I had to change the last line of /etc/default/acpi-support to: STOP_SERVICES="mysql irda-utils"

Done that. No joy on Breezy :) At least not while on AC power. Its OK on battery.

Got any other tips? I'd be happy to see them. Thanks Phen![/QUOTE]

Update. Hibernate DOES work now with todays update (16 Sept 2005) with the AC power adapter plugged in. It will now resume but only if my USB mouse is not plugged in. If the usb mouse is plugged in, it will hang. This points to the ehci_hcd module i think. But rmmod/modprobe of various usb modules didn't help.

Yay! one step closer now.... may just have to add something to /etc/default/acpi-support now to have the proper module unloaded/reloaded when the hibernate script is run.

FIXED!  added the usb modules and 1394 to /etc/default/acpi-support to have them unloaded/reloaded and the laptop is now at 100% :D
(well... except for the card readaer since no drivers are availabel for it.

---

### Post by putz3000 on 2005-09-16
I have a ze2117us model pavilion and would like to know if any one has attempted an install on this model yet?  if so what issues arose?  Also, i read on one of the other posts about a bios/boot protection issue to protect windows?  is there some place I can go on the web to learn more about this (starting to wonder if i should have bought an hp....I hate their new CEO so it was a hard step for me in the first place!)

p.s. I have tried to boot up with the live cd and had it freeze while loading the GUI.  During initial boot, there was a point where I saw breifly a couple of errors or undetects but was unable to catch what areas i had problems at.   If I am unable to run the live cd is that a pretty good indication that I will be fighting a normal install as well?

---

### Post by JLB on 2005-09-17
Just a note of intrest here regarding HP laptops and Linux. I read a press release yesterday that stated HP is now delivering the NC6120 and NX(?)6110 with Mandriva Linux in Europe. For now it is being sold in France only. Sales in other countries is forthcoming. Go HP!

---

### Post by phen on 2005-09-18
JLB, i'm glad to see that you were able to fix the problem. do you want to add your work around to the wiki? either to the laptop compatibility page or to the laptop testing team homepage. i really dont know what fits best, but i think it would be nice to keep this info public (in a few weeks, a lot of users will ask probably :-)

have you got a link to that news? i like what i hear!


EDIT: is anybody using a nc6120 with its docking station? it would be nice to hear your stories with it :-) or even better: to read about them here:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard)

my special question is: does the external display work when the laptop's lid is closed? does it work in a different resolution than the internal screen? is the external display fully usable and configurable while not messing around with the internal?

thanks!

---

### Post by JLB on 2005-09-18
Phen,
I already have a wiki for it. Chekc out the laptop testing team page. It's there along with my notes.

---

### Post by JLB on 2005-09-18
[http://www.mandriva.com/company/press/pr?n=/pr/products/2562](http://www.mandriva.com/company/press/pr?n=/pr/products/2562)

link to the HP/Mandriva announcement.

---

### Post by phen on 2005-09-19
jlb: cool, i didn't knew it was your page!

---

### Post by Elius Maximus on 2005-09-19
I have problem with my Hp Pavillion zd 8239 AE notebook. The ubuntu won`t find the chipset drivers and won`t enable and find the broadcom wireless networkcard. Any that has a solution or know about drivers that I can find on the net?

---

### Post by skela on 2005-09-19
I have Ubuntu running on my HP dv1170ea without any problems. Had to manually install new wlan driver and firmware though, the wireless was a bit buggy. After that everything was perfect . :D

---

### Post by JLB on 2005-09-19
[QUOTE=phen]jlb: cool, i didn't knew it was your page![/QUOTE]

we ought to get together and compare notes. to make sure our lappys are the best running ones :P

Maybe combine our notes for the wiki as well. what do you think?

---

### Post by JLB on 2005-09-19
[QUOTE=Elius Maximus]I have problem with my Hp Pavillion zd 8239 AE notebook. The ubuntu won`t find the chipset drivers and won`t enable and find the broadcom wireless networkcard. Any that has a solution or know about drivers that I can find on the net?[/QUOTE]
afaik, you need ndis wrapper for the broadcom chipset wifi. plenty of posts in the forums about ndis wrapper. try that route and get back to us.

---

### Post by phen on 2005-09-20
JLB:

What do you want to compare? just send me an email: phen at gmx dot de.
actually, my notes are hoary-only. As soon as Breezy is out, we should compare our notes, and write the wiki page together :) I am gonna buy a docking station, too. there isn't anyhing written about docking at all, is it? I contacted some guy from the mailing-lists, but he has never added his information...

cheers!

---

### Post by JLB on 2005-09-21
sounds like a plan. we can get the wiki page as up to date and accurate as possible when Breezy releases. 

We can go over each and every standard entry, then under the notes/addt'l info add any tweaks/tips as needed. Maybe even cover hoary-->breezy upgrade notes as well as clean installs.

Look forward to working with you.

JL

---

### Post by JLB on 2005-09-25
just a note. colony 5 breezy has hibernate working out of the box now.! now if TI / HP would release the stuff on the card readers, the nc6120 would be 100% supported. I'll ssettle for 99% without the card reader :)

---

### Post by velvet.monkeywrench on 2005-09-27
Another article: [http://www.infoworld.com/article/05/05/23/21OPopenent_1.html]("http://www.infoworld.com/article/05/05/23/21OPopenent_1.html") :cool:

---

### Post by phen on 2005-09-27
jlb: 
perfect plan! i think my courses don't start before breezy's release, so i am able to upgrade    just after release :) and my docking will come in october, too...

did you test out 686 kernel under breezy? i ran into problems when i tried to use them with the prerelease version of HPuntu. havent tried it again since. we can cover that, too. 

my baby just returned from hp-support (third time in 3 weeks... well it is a quality laptop). now it looks as if everything works as it should. i am ready to go :-)

---

### Post by JLB on 2005-09-27
sorry to hear about the laptop. hope it arrives back to you 100%.
i686 kernel is not a problem. works great.  let me know when you are ready on the other stuff. hopefully we can provide the rest of the HP laptop users some solid info.

---

### Post by olaf-g on 2005-09-28
Hi.

I have installed the HP hoary image (downloaded on 22-09-05) on my nc6120 which was working very nice but I was 'hungry' for the cool stuff of breezy ;) So I dist-upgraded on 26-09-05 and everything worked quite nice exept that with the new breezy kernel (2.6.12) hibernation isn't working. Guess I tried it while on AC but I'll try again when running of the battery. So I went back to the hoary kernel (2.6.10).

I used to be a debian user for many years now, but I'm new to ubuntu... As I wanted to run audio software and jackd I wanted to install the kernel module 'realtime'. I followed instructiond from the net but obtaining the module by using module-assistant didn't work. Is this because it wants to install it for kernel 2.6.12 but I'm using 2.6.10??? Is it better to use the new kernel? When breezy final will be released? Where will be that wiki page for HP notebooks on breezy (I'm willing to contribute ;))?

Thanks so far.

---

### Post by LeLaulau on 2005-09-29
hi,

I was trying to upgrade from Hoary to Breezy on my HP Pavilion zd8000... and everything seemed to have worked fine only one problem:.... the X-server! :)

I installed the ATI Driver with the executable (not the rpm) and now I wished to uninstall it...

The problem apt-get tell me is:
```
Reading package lists... Done
Building dependency tree... Done
0 mis à jour, 0 nouvellement installés, 0 à enlever et 436 non mis à jour.
1 partiellement installés ou enlevés.
Il est nécessaire de prendre 0o dans les archives.
Après dépaquetage, 0o d'espace disque supplémentaires seront utilisés.
Paramétrage de xfree86-common (6.8.2-10.1) ...
xfree86-common postinst warning: /usr/bin/X11 symbolic link points to wrong
   location ../bin
Analyzing /usr/bin/X11:
drwxr-xr-x  13 root root 4096 2005-09-29 00:12 /usr
drwxr-xr-x  2 root root 32768 2005-09-29 00:53 /usr/bin
lrwxrwxrwx  1 root root 6 2005-09-28 23:29 /usr/bin/X11 -> ../bin
Analyzing ../bin:
drwxr-xr-x  21 root root 4096 2005-09-29 00:44 /..
drwxr-xr-x  2 root root 4096 2005-09-29 00:12 /../bin
Searching for overlapping packages...
The following packages appear to have file overlaps with the XFree86 packages;
these packages are either very old, or in violation of Debian Policy.  Try
upgrading each of these packages to the latest available version if possible:
for example, with the command "apt-get install".  If no newer version of a
package is available, you will have to remove it; for example, with the command
"apt-get remove".  If even the latest available version of the package has
this file overlap, please file a bug against that package with the Debian Bug
Tracking System.  You may want to refer the package maintainer to section 12.8
of the Debian Policy manual.
The overlapping packages are:
x-common
xfree86-common postinst error: bad symbolic links on system
dpkg : erreur de traitement de xfree86-common (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 74
Des erreurs ont été rencontrées pendant l'exécution :
 xfree86-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can someone help me?

---

### Post by phen on 2005-09-29
olaf: i think the wikipage should be accessible from
wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard

lelaulau: is it possible that you replaced some files from these packages with files from the ati executable? i did the same with other packages (my wlan-adapter), and i don't know how to fix this either. i think the problem is that apt-get doesn't want to overwrite files not in its list.
there has to be and option like "apt-get install --force" or something. But i haven't tried it yet. i'm interested in a solution for this, too! :-)

---

### Post by LeLaulau on 2005-09-30
Ok my problem was resolved. I uninstalled xfree86.
no I have other problems with my keyboard and xkb. Perhaps it's related:

[http://www.ubuntuforums.org/showthread.php?t=70388](http://www.ubuntuforums.org/showthread.php?t=70388)
[http://forum.ubuntu-fr.org/viewtopic.php?pid=93648#p93648](http://forum.ubuntu-fr.org/viewtopic.php?pid=93648#p93648)

---

### Post by Gandalf on 2005-10-11
Guys take a look to this
[http://www.everestinc.com/fml.htm](http://www.everestinc.com/fml.htm)

---

### Post by locutus42 on 2005-10-11
[QUOTE=Gandalf]Guys take a look to this
[http://www.everestinc.com/fml.htm](http://www.everestinc.com/fml.htm)[/QUOTE]

Nice.  We can only hope that HP or Everest Inc releases the driver and/or code so we can use this. It looks promising that HP wants to get Linux support for this 6:1 media device and paid for it to be done. :-)

---

### Post by iimre on 2005-10-13
Hi,

Breezy final release is out now :)
Has anybody tried to upgrade the custom HP'ised version to Breezy? Or I'd better wait for a Breezy based custom version? Or maybe it is not neccesary because it has the neccessary HP support out of the box? 

Any experience welcomed. 

Regards

Imre

---

### Post by phen on 2005-10-15
hello!

i updated my system yesterday.
In hoary, i did the following changes to the system:
I changed the kernel module ipw2200 manually, i changed the ipw2200 firmware

after my dist-upgrade via cd, everything works nicely. dmesg shows a ipw2200 firmware error, but it works still. 

to upgrade, follow these directions:
[https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29](https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29)

I have some very minor thing to sort out now: the firmware error, the splash screen is not on by default, and my usb disk is not automounted

cheers,

kai

---

### Post by phen on 2005-10-18
EDIT: everything's working now! i gonna add my infos to the wiki soon...

---

### Post by phen on 2005-10-18
today i was not able to hibernate/shutdown my nc6120. during boot, i saw something conspicious: my system was still booting the hp laptop package. also, the splash screen does not work. i did a dist-upgrade from hoary to breezy.

is somebody reading who has updated, too and has some experiences to share?

thank y'all!

cheers

---

### Post by bgalan on 2005-10-18
Hey,
i've played with ubuntu for a few months now and i love it. i'm using a pavilion ze4145, dual boot with XP (which i almost don't use anymore), and i recently updated to breezy... 
Almost everything works in the laptop, except "hibernation." i'm finally able to suspend to ram, though when i power on the laptop everything seems to work fine except the keyboard. what i did is i connected a usb keyboard and usb mouse and things started working again; though i did have to logout gnome so the keyboard and touchpad of the laptop would work again. any ideas how to fix this? i love ubuntu! thanks!!! :)

---

### Post by simohell on 2005-10-18
I've got the same problem with nx9005. Hibernation works if I use USB keyboard but if I dont the laptop wakes up allright apart from the keyboard not reacting at all. And then it starts with the screen saver as usual.

---

### Post by nixon on 2005-10-24
I'm running breezy on an nc8230, i had originally installed the hp version of hoary.. a dist-upgrade did the trick for me.. tho I have found that I can't use the default ati driver and had to install and configure the fglrx xorg driver.. (X wouldn't start without it)..

now everything appears to be working pretty well, except for hibernation.. If I hibernate and try to start up again.. the screen comes up all garbled.. the startup time is basically the same as shutting down so thats what I've been doing.. kinda a pain..

usplash didn't work after my initial upgrade so i did a dpkg-reconfigure linux-image-2.6.12-9-386 and a dpkg-reconfigure usplash.. a reboot and i was away.. hopefully I can figure out what the problem is with hibernation.. other than I'm a happy chappy..

---

### Post by greenwom on 2005-10-30
[QUOTE=Thomas Schneller]Except the sd-card reader. No Linux driver for that device so far. 

Thomas[/QUOTE]

What kind of card reader?  I have a smart disk sony card reader that works out the box.  I'm using a HP 503n w/ breezy.

---

### Post by sarimak on 2005-11-15
[QUOTE=simohell]I've got the same problem with nx9005. Hibernation works if I use USB keyboard but if I dont the laptop wakes up allright apart from the keyboard not reacting at all. And then it starts with the screen saver as usual.[/QUOTE]

Try to hibernate via script which contains usual echo to /sys/power and then rmmod uhci_hcd & modprobe uhci_hcd. I know it's only a workaround but it works for my USB mouse on Compaq Deskpro EN running Breezy.

BUT: I also run Breezy on nc6000 and I don't need to do such mess to keep USB mouse working...

Hope it helps...

---

### Post by Snapper187 on 2005-11-18
Hi everyone,

I've bought an HP nc6120 like three weeks ago with my decision based on jlb's LaptopTesting entry. I do not regret it so far, thanks.

I'm having trouble getting hibernation to work properly, however, using Breezy. The machine seems to save machine state and shutdown properly, but if I try to resume my session, I get something like "ACPI handler is NULL" and "need to copy 60521 pages" after which the laptop just stops proceeding (sorry I cannot copy and paste the entire error message).

Do you guys have the same issue, or do you get any further while resuming? jlb (or was it phen?), could you please give me your exact line of usb/1394 modules you're excluding in /etc/default/acpi-support?

Has any nc6120 user actually managed to get hibernation to work with final Breezy?

Thanks in advance!

---

### Post by olaf-g on 2005-11-19
Snapper187: I have exactly the same with my nc6120. I had installed the HPdized hoary image, upgraded to breezy... When waking up from hibernation it freezes after 'copying xxx pages'. With the hoary kernel 2.6.10 hibernation works fine. I don't really want to go back to that kernel and do the [hoary wifi fix]("http://www.ubuntuforums.org/showpost.php?p=167782&postcount=46"), but if I can't fix the hibernation in breezy...

So Phen and others, please post your acpi setup.

---

### Post by simohell on 2005-11-24
[QUOTE=sarimak]Try to hibernate via script which contains usual echo to /sys/power and then rmmod uhci_hcd & modprobe uhci_hcd. I know it's only a workaround but it works for my USB mouse on Compaq Deskpro EN running Breezy.

BUT: I also run Breezy on nc6000 and I don't need to do such mess to keep USB mouse working...

Hope it helps...[/QUOTE]

Well, it seems you missed the point completely.

USB-mouse and USB-keyboard are the ones that do work. The laptops internal keyboard and toutchpad don't. Thanks for taking interest anyway...

---

### Post by phen on 2005-12-08
hi!

i haven't changed the setup. under hoary, i had to add a irda-utils entry to the last line of the acpi-support file. thats explained on the wiki!



cheers

---

### Post by phen on 2005-12-24
Does the suspend hotkey work under kubuntu for anyone? i added kubuntu-desktop to my ubuntu installation, maybe i can install something additionally to make it work...

thanks for your help

---

### Post by Snapper187 on 2006-01-11
Unfortunately, I still couldn't manage to make my HP hibernate.

Using "echo -n disk > /sys/power/state" [1], however, where you can see the messages while Ubuntu saves all data in swap space, I can see that it fails copying at about 60% moaning about something with "ipw".

I wasn't able to read it all because it scrolled down really quickly and the machine rebooted afterwards, but I figured it had to do with the IPW2200 driver. Next reboot, I removed the ipw2200 module before hibernating, and indeed it completed copying to swap 100% !

Too bad it didn't help at all. While trying to recover from hibernation, Ubuntu still freezes with "use resume= to [...]". :(

I also added a "resume=" parameter to grub but as I had predicted it didn't ease the problem: the swap partition is hard-coded into /etc/mkinitramfs/initramfs.conf and will be applied at boot-time as far as I can see.

Some guy on the Ubuntu forum claims that removing the "splash" option from grub made his laptop return from hibernation. His is not an nc6120, however, and doing so had no effect on my machine either.

I thought I better tell you guys so maybe one of yours might come up with a proper solution...


[1]actually, I had to use *sh -c "echo -n disk > /sys/power/state"* or otherwise the shell would quit with a "no permission" error.

---

### Post by olaf-g on 2006-03-04
[SIZE="4"]Finally I made hibernation working again!!![/SIZE]

Well, that was a struggle. After spending one free saturday afternoon I made it. And it was so simple... I tried to unload all possible modules etc. But the solution was the bootsplash. I found it because I couldn't unload the vga16fb module and I asked myself why it is needed... harhar.

So just edit your /boot/grub/menu.lst and remove the **splash** keyword from the kernel parameters. Save and reboot. Now you should be able to hibernate and resume successfully. It worked fine on my HP nc6120 hoary hp image dist-upgraded to breezy.

Just one more thing: When running ```
sudo update-grub
``` or installing new kernels the splash is magically coming back. So in order to get rid of the bootsplash forever, edit /boot/grub/menu.lst and remove the **splash** keyword from the line starting with ```
# nonaltoptions=
```

Have fun

Olaf

---

### Post by Josh Kurtz on 2006-05-28
Does anyone know where I can get the HP Ubuntu image?  It's not on Ubuntu's website anymore.

---

### Post by phen on 2006-05-29
just try the actual breezy standard installation CD. All changes made by HP are incorporated in breezy. You'd need HP Ubuntu if you would like to install hoary.. but i cant help you with this one..

---

### Post by ubuntu27 on 2006-05-29
[QUOTE=Josh Kurtz]Does anyone know where I can get the HP Ubuntu image?  It's not on Ubuntu's website anymore.[/QUOTE]

[QUOTE=phen]just try the actual breezy standard installation CD. All changes made by HP are incorporated in breezy. You'd need HP Ubuntu if you would like to install hoary.. but i cant help you with this one..[/QUOTE]

Why install Hoary or Breezy now? Just move to Dapper!! :D

[http://www.ubuntu.com/testing/dapperrc](http://www.ubuntu.com/testing/dapperrc)

---

### Post by Josh Kurtz on 2006-05-29
> just try the actual breezy standard installation CD. All changes made by HP are incorporated in breezy. 
Thanks.  I guessed as much last night so I downloaded breezy, installed it, installed kubuntu-desktop and I was good.  I had to fiddle a little with madwifi since there was an older version installed with breezy that I had to remove but that didn't take too long.  

The best thing of all of this is my nc6000 suspends to ram and wakes up properly!  I was messing with my Debian etch install for 5 days writing scripts and editing files but I just couldn't get it to come back from sleep.  Ubuntu really impressed me with its laptop support which is stellar.  

Big thanks to HP for spending time with Ubuntu optimizing it for their laptops.8)

> Why install Hoary or Breezy now? Just move to Dapper!! 
I'll update apt and dist-upgrade to it once it goes final.

---

### Post by ZERO_SHIFT on 2006-10-11
Here is a link that might intrest you:

[http://www.ubuntuforums.org/showthread.php?t=275249&page=2](http://www.ubuntuforums.org/showthread.php?t=275249&page=2)

---

### Post by AussieLakerFan on 2006-10-11
I am using 6.06 Dapper on my HP nx8220.

Everything works very well.  I was using SuSE Linux Enterprise Desktop 10 and while that was pretty good, this is GREAT!!

Haven't tested the sd card reader (nor even tried to get it going)

Screen is good at proper resolutions, has ATI Raedon Mobility X600 video card.

Hooked it up to a projector once, didn't know how to configure the monitor output though, didn't really look either, it was for a presentation and it sent it out at the right res anyway...

I certainly would be interested to hear more info regarding an official HP release for this laptop, but will also settle for any tips and tricks specific for this laptop...

---

### Post by olaf-g on 2006-10-13
Jeeez... I forgot to post here that I solved my card reader problem on my HP nc6120. Finally all of its hardware is working. Strike!!!

[http://ubuntuforums.org/showthread.php?p=1614392#post1614392]("http://ubuntuforums.org/showthread.php?p=1614392#post1614392")

Cheers

Olaf

---

### Post by djbrody on 2007-11-12
I have taken the time to workout some of the issues of using a HP NX9420 laptop.
ATI RADEOM X1600 I could not get the ubuntu restricted driver to produce the resolution that i wanted.

ATI supplies a driver for linux that works great 1680 X 1050 Plug N Play with super resolutions and refresh rate. I have attached the link to the ati available driver [ATI LINUX]("http://ati.amd.com/support/drivers/linux/linux-radeon.html"). They supply a simple instruction page.

---

