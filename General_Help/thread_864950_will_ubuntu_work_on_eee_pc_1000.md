---
title: "will ubuntu work on eee pc 1000 ?"
date: 2008-07-20
forum: General Help
---

### Post by thefishki345 on 2008-07-20
Hi,
I am considering getting an ASUS eee pc 1000 for when I go traveling/extra computer/looks cool etc.

I have read the Ubuntu Documentation on the eee pc, but it is for the older eee pcs on ubuntu 7.10, and I am wondering:

Have some of the bugs been fixed? (microphone not working etc) 

does it still require quite a bit of configuration? (altering font size/resolution is fine, technical config is what im worried about)

Because, the laptop comes with XP preinstalled (only option available from what I can see besides xandros, and I don't want to use that and its not available in Australia anyway.) and a´m wondering would it be worth installing Ubuntu if there are all these things wrong.
thanks

---

### Post by palomar on 2008-07-20
You can look for specific Eee distributions like Eeebuntu, Ubuntu Eee, EeeXubuntu. See also [http://forum.eeeuser.com/](http://forum.eeeuser.com/) .

Default Ubuntu will probably work (it will on my Eee 701), but hotkeys and wifi don't work out of the box, so you have to tweak it.

[edit] Was thinking EeePC 1000 has the same specs as 700/900, but it's a bit different I see, so I don't know for sure now if the distro's I mentioned will work...

---

### Post by thefishki345 on 2008-07-20
k thanks, I will check out eeebuntu (lol)

---

### Post by thefishki345 on 2008-07-23
Palomar because of your edit, could someone who has an eee pc 1000 running ubuntu or eeebuntu or whatever tell me, and tell me if it needs any configuration or stuff that doesnt work. It would be VERY much appreciated
thanks!

---

### Post by DagMan on 2008-07-23
I read a blog post by someone who had recently bought one that neither the wired or wireless drivers were working when he installed it.  He downloaded the wired ethernet drivers, build essential, and other packages, and then went from there.  This is a pretty big thing right off to consider that getting first hand advice on it would be smart before buying.  The 900 and  (and prior) have great ubuntu specific documentation and there's even a custom kernel repo for the eepc to supply a kernel with the acpi module, the webcam driver, and the touchpad driver as it isn't synaptics compatible.

I'd really do a bit of googling to be quite sure before buying the 1000 just yet.

EDIT: S0rry, I was wrong about the 901.  It also has trouble with no wireless and ethernet after install.  More here as well [http://www.ubuntu-eee.com/index.php5?title=EeePC_901](http://www.ubuntu-eee.com/index.php5?title=EeePC_901)

---

### Post by thefishki345 on 2008-07-23
thanks for that dagman, and that is what I am trying to do, research, first hand advice, usually the people on ubuntuforums are really good for info, so again, if anyone has an eeepc 1000 or 1000 (h) running ubuntu or eebuntu please tell me, thanks!

---

### Post by Chonnawonga on 2008-08-07
I picked up an eee 1000 a couple of days ago. The Fisher-Price-style version of Xandros is cute, but it drove me up the wall. This is a fully-functional computer; why have a toy OS on it?

Installed Ubuntu from a flash drive this morning using [this guide]("http://www.ubuntu-eee.com/index.php5?title=EeePC_901"). (It says 901, but it worked for me.) So far I have wired and wireless network up and running, but I still have to work on the webcam, bluetooth, microphone, function keys, etc.

I expect the 8.04.1 version of [Ubuntu Eee]("http://www.ubuntu-eee.com/index.php5?title=Main_Page"), which should be out any day now, will simplify all this, but I couldn't put up with that joke of an OS any longer. I've paid for this machine, and I'd like to actually USE it!

---

### Post by Chonnawonga on 2008-08-08
Just a quick update:

Webcam and bluetooth are both now working very nicely: all I had to do was set them both to "Enabled" in the BIOS (hit F2 at the initial screen) and Ubuntu picked them both up, no problem.

Function keys are sort of working, thanks to the guide above.

Still no action on the microphone; I'm waiting for an easy fix for the geniuses over at [www.ubuntu-eee.com]("http://www.ubuntu-eee.com")

I tried running Compiz, but it crashed hard after a couple of minutes, besides which I was getting some really screwy behaviour from the cube rotation. I'm going to leave it off for now, as I don't want a bunch of crashes on an ext2 partition. Again, I'm waiting for Ubuntu-Eee to solve all my problems for me. If it works nearly as well as I'm hoping, I intend to make a donation.

In the mean time, I'm really enjoying Ubuntu on the Eee 1000! It's a heck of a lot better than the default Xandros-based OS.

---

### Post by MetaMorfoziS on 2008-08-08
Microphone oh yes...
I'm also have problems instead of sound from it:)

---

### Post by VMan on 2008-08-18
I have the 1000H running Ubuntu Hardy with compiz effects.  I installed from a stock Hardy CD and then installed a custom kernel and modules found on the eeeuser.com forums (sub-forum Ubuntu; adamm's custom kernel and modules).  I really like the way everything works.  I now have a perfectly customized setup that looks good and runs almost perfectly (I use AWN which has a few bugs).  If I was content to run the standard Gnome desktop, everything would be perfect, but. . . I really like AWN.

---

### Post by rats54 on 2008-08-20
Hi, is anyone running an dual (Windows XP/Ubuntu Hardy) boot on an Eee PC 1000H?

I need a new light weight-mobile laptop and I am looking at the 1000H, but I have to be able to dual boot.  When I am on the road there are just some things I have to do that require XP. Maybe some day I will be able to get rid of XP completely.

I do not know what to try; Hardy, eeebuntu or Wubi.  If someone has already done it I would like to know how and what you did.

Thanks

---

### Post by Chonnawonga on 2008-08-20
Hi rats54,

I don't have the 1000H; I have the 1000. I don't foresee any problems with a dual-boot setup, though. My suggestion would be to do a default 8.04.1 install from a USB key, and then follow the instructions [here]("http://forum.eeeuser.com/viewtopic.php?id=38030") to install the Eee-specific kernel and drivers.

---

### Post by bcn17 on 2009-01-04
I have an Eee PC 1000  and  am running 8.10 with the array.org/ubuntu kernel. It works perfect. Although I am trying to get better resolution on my  external monitor.. You can also use the ubuntu-eee.com  "Easy peasy" for a standard install with the array kernel built in.  8.04.1 or   8.10 (the latter on the  5th)

---

### Post by MN Noob on 2009-01-07
I just got a 1000 and am wanting to put Ubuntu on it. I have done some research and see most say to do the Ubuntu Eee thing. What are the main benefits in doing that, and are there any potential issues in the future(like updating).
I would prefer to just install Ubuntu and make the necessary 'tweaks' to get it working. If I were to do that, will I be causing myself more headaches than it is worth?
I looked on their(Ubuntu Eee) site, and it appears some of the tweaks I would have to do either way. As well, they are still using 8.04 and not 8.10. (I don't know if there is that big of a difference between the two releases, but I would prefer to stay most current)

---

### Post by blazemore on 2009-01-07
[Easy Peasy]("http://www.geteasypeasy.com") etc are just Ubuntu with drivers etc to make it work out the box on an eeepc. The packages will update, just don't install any additional kernels.

---

### Post by alicemoon on 2009-01-08
I have a dual boot XP windows and [eeebuntu]("http://www.eeebuntu.org/")- on my 1000h this is 8.10 and you can download either a full desktop version, netbook remix or a reduced footprint base install. I am running the netbook remix version - it updates as normal but the tweaks to make the eee work are locked so they cannot be disrupted by updates. It all works except for a couple of the toggle switches the most annoying being the wifi/blutooth but I have discovered that if I turn it on in windows it stays on in ubuntu and vice versa - apparently fixes for these are on the way with their eeeconfig scripts which are run through a gui that comes with eeebuntu. I had a look at all the options and finally went for eeebuntu and am pleased with it.

---

### Post by Phil Urich on 2009-05-17
I've been searching around for a netbook for my father, actually, and the 1000 so far seems like it might be the only good bet (big SSD, larger screen but still light, 6-cell battery), but I'm wondering now if things have changed with Jaunty?  Is anything broken now, or alternatively does nearly everything work off the bat? And if not, what still needs tweaking from a fresh Jaunty install?

---

### Post by alicemoon on 2009-05-18
I think eeebuntu 3 which is the jaunty version is now out - I have not had a look yet as I have not had the time - some of the hot keys etc still do not work from what I have read if you just install  jaunty as is -

---

### Post by Chonnawonga on 2009-05-18
Things work pretty smoothly with Jaunty out of the box, but there are a couple of tweaks that really help.

First, get [eee-control]("http://greg.geekmind.org/eee-control/"). This does a nice job of enabling fan control, extra buttons, etc.

And there may be some trouble connecting to WPA-secured networks. Jaunty uses new drivers that actually break WPA connectivity. See [this discussion]("http://ubuntuforums.org/archive/index.php/t-1110957.html").

---

### Post by Phil Urich on 2009-05-18
> **Chonnawonga said:**
> And there may be some trouble connecting to WPA-secured networks. Jaunty uses new drivers that actually break WPA connectivity. See [this discussion]("http://ubuntuforums.org/archive/index.php/t-1110957.html").

Ouch, that seems a bit serious . . . almost seems like it'd be better to stick with Intrepid then, what with this problem and the Intel graphics performance issues.  But then there's no ext4 and speedy-quick boots, alas, no perfect world.

---

### Post by Chonnawonga on 2009-05-20
I haven't had any real problems with the Intel graphics on the Eee with Jaunty.

Really, your options are to go with Intrepid and use Adamm's custem kernel, or go with Jaunty and do the WPA fix. The latter is probably a little easier (or at worst, the same) and you get more up-to-date software.

My biggest beefs with Jaunty are all non-Eee related... especially [this one]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038").

---

### Post by Phil Urich on 2009-05-23
> **Chonnawonga said:**
> I haven't had any real problems with the Intel graphics on the Eee with Jaunty.

Really, your options are to go with Intrepid and use Adamm's custem kernel, or go with Jaunty and do the WPA fix. The latter is probably a little easier (or at worst, the same) and you get more up-to-date software.

My biggest beefs with Jaunty are all non-Eee related... especially [this one]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038").

Alas, a bit of an issue with Jaunty, this release seems caught in the no-man's land between a lot of major overhauls (like the Intel drivers, and the new X.org, and etc etc)

So do you have WPA working fine on your 1000 then, though?  My father is about to purchase a 1000, but since he'll be off in airports and at conferences and such with it it's rather important to be able to connect to any and all wireless networks, *especially* the ones with heavy encryption.

---

### Post by dawnlove on 2009-05-23
blender is messed up on my eeepc 1000 with xubuntu 9.04. I hear it's a known bug in intel video. everything else works

---

### Post by Chonnawonga on 2009-05-23
Phil,

I think you're right about Jaunty. Things should be better down the road, but the transition process is a bit painful.

Your father should be fine with wifi security. Mine is working over a WPA2 connection just fine right now, and I use WEP elsewhere. I read today that the WPA issue has been fixed in regular Jaunty updates since I fixed mine, though I can't confirm that.

---

### Post by Tiler on 2009-05-29
I had a good run with Easy Peasy for almost a year but it was buggy in annoying sorts of ways.  I just reinstalled with Eeebuntu 3.0 Base and life is much, much better.  I have a couple of bugs but nothing critical.

I'm documenting the switch [here]("http://forum.eeebuntu.org/viewtopic.php?f=41&t=2875").

---

### Post by Chronon on 2009-05-29
> **Phil Urich said:**
> So do you have WPA working fine on your 1000 then, though?  My father is about to purchase a 1000, but since he'll be off in airports and at conferences and such with it it's rather important to be able to connect to any and all wireless networks, *especially* the ones with heavy encryption.

I haven't had any problems with WPA connectivity issues so far.  I use it on my home WiFi network and EeePC 1000HE without any problems.  I have stock Jaunty Netbook Remix.

---

