---
title: "ATI Driver issue"
date: 2010-02-11
forum: Hardware
---

### Post by Joho22 on 2010-02-11
So Im still new to this Ubuntu OS but Im picking up things slowly but surely.

The issue I am having now is getting a driver to work with my video card.
I have installed catalyst but for some reason, it didnt install the driver for my ATI Radeon Mobility 7500. (I could have swore it was a 9700 but thats what its telling me it is)

Im running an IBM Thinkpad T40 with 1.5g ram and a 1.7ghz pentium.

Running Kowala 9.10 I believe (latest cd off the ubuntu site)

Ive tried several things but havent had any luck.

any assistance would be very much appreciated.

---

### Post by Joho22 on 2010-02-11
This has become frustrating and I had to turn to the forums and youtube videos because well... I dont want to make it worse.

Ive tried drivers and other options from the synaptic package manager (ie: EnvyNG) and that has not helped one bit.

When I rebooted I was prompted that I would have to start in low resolution mode because I jacked my display settings.

Later i tried to go through the ubuntu help section and followed a tutorial that had me editing text. Slightly scary to someone who has used Windows a long time but I braved it and put all the information I thought it told me to and alas, I still have posted on here.

Basically I have nothing in my proprietary hardware menu, I have a dummed down video setting and all in all, having a rough day...

any help would really mean the world.

---

### Post by Joho22 on 2010-02-11
here is basically what it looks like



Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 7500"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
                Virtual         1024 768
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

---

### Post by starsprout on 2010-02-11
I'm in a similar position, except I'm at least able to get out of low-graphics mode. Been there several times today, heheheh.

Are you still stuck in low graphics?

Open a terminal and type:
cd /etc/X11

Then, type:
ls 
(to show the files in the folder)

Is xorg.conf one of the files in that folder? If so you may need to edit that  to get out of low graphics mode, unless of course you never completed the drivers' install, but I'm not an expert.

If xorg.conf is in there, you can look at it's contents in the terminal simply by typing:
cat xorg.conf

I've been grappling with video drivers on 2 machines now. The variations are mind-boggling. I'm running 64-bit on this machine here so that's possibly a bit tricker.

I know it can be done though. There are very few machines that can't be configured with OSS

---

### Post by Joho22 on 2010-02-11
ok so did that command but what do I do when i change directories? you have

Then, type:
ls 
(to show the files in the folder)

---

### Post by starsprout on 2010-02-11
you shouldn't need sudo to my knowledge but if you have it use it.

do you have the fglrx drivers installed?

In your xorg.conf it's referring to an ATI driver in device section; you can change that to "fglrx" and it may fix if you have it all installed.

I hear the proprietary ATI drivers are not as good as the open source version, which i think is Xorg which I'm still learning about

---

### Post by Joho22 on 2010-02-11
says xorg isnt in the directory... this stuff is mutant to me,
i definitely dont want to go back to windows...

---

### Post by Joho22 on 2010-02-11
Ive been reading things like this...
its just baffling sometimes,
im trying to keep up but its a totally new world to me...
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Joho22 on 2010-02-11
Sorta gave up. 
Reformatting to start over.

---

### Post by hxcobd on 2010-02-11
Are you on 32-bit or 64-bit?

There's 2 steps you can generally take to get an ATI card running quick and easy:

1.) Hit System, then Administration, then Hardware Drivers. Ubuntu should find a proprietary driver for your ATI card all on its own, and you just have to click Install.

2.) Otherwise, hit System, then Administration, then Synaptic Package Manager. Search for either "radeon" or "fglrx," whichever looks more adequate to your particular card model.

I'd recommend uninstalling whatever packages you installed first, and at least get back to where you don't need low-quality mode.

If those 2 steps don't work, head over to ATI's website; they actually host official Radeon drivers for linux on it. Follow the installation instructions there.

---

### Post by Joho22 on 2010-02-11
Xcobd, thanks for the reply but since I'm newer to Linux than I'd like to admit,
I'm actually reformatting again and trolling the forums as as I type this from my phone. 

I believe it's 32 bit as I have an old laptop I'm squeezing the last bit of life from and I've tried several things to get a driver to work, a bunch are listed above. 

Speaking of uninstalling... How does one uninstall on ubuntu?
Secondly, the video card for this is a radeon 7500. And Ari no longer supports it. This is where my plight began. 

I basically would be fine with regular graphics but I just need to enable 3d acceleration for my one vice... Warcraft 3. (i'm a nerd for strategy games)

outside that ubuntu is all I need with all the free software it comes with (ie open office)
I just have been pulling my hair out cause ati shows no love to Linux users. 

But so I don't eff up your instructions. Think you can offer me and my feeliw noobie that's been posting with me how to get this done correctly? I would really appreciate it.

---

### Post by Joho22 on 2010-02-11
That was the other issue. No prop drivers showed up no matter what I did!
It was driving me nuts. 

Just finished reformatting.

---

### Post by hxcobd on 2010-02-11
> **Joho22 said:**
> 

Speaking of uninstalling... How does one uninstall on ubuntu?
Secondly, the video card for this is a radeon 7500. And Ari no longer supports it. This is where my plight began. 



Uninstalling programs on linux is sort of a misnomer, as unlike Windows, linux OSes don't have a registry like Windows does, so the OS basically "forgets" about the programs you have installed as soon as you delete all of the source files.

Uninstalling programs can be done either of the following ways:

1.) Open Synaptic Package Manager and do a Search for a particular program, package, or overall name of a file. (For instance, "openoffice") Then check out the very first column; if the box is shaded green, it means that package is already installed. Right click the package and select "Uninstall" (or remove? can't remember, it should be obvious), then hit the big Apply button to completely remove all the package's files.

2.) Find the directory the package is "installed" in (could be a number of different places... /usr/bin is a common one, as well as /home/username/.programname ) and just delete the directory and all associated files.

A large percentage of all the programs and packages you'll ever need will be found in the Synaptic Package Manager. It's quite different from using Windows, as Windows doesn't really have a comparable program.

I'd say about 85% of my programs came from Synaptic, and the other 15% are .deb or .tar files from the software maker's website.

.deb files are the linux equivalents of Windows' "installer" .exe files.

.tar files are just archives, generally containing all of the executable files you'll need to run a linux program. There's nothing to install; just unzip the .tar file and run the executable, which is generally a file with no filename extension at the end.

---

### Post by hxcobd on 2010-02-11
> **Joho22 said:**
> That was the other issue. No prop drivers showed up no matter what I did!
It was driving me nuts. 

Just finished reformatting.

If no drivers show up using the Hardware Drivers dialog, try "fglrx" from Synaptic.

If THAT doesn't work, try this:

[http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx)

Those are actually drivers for Radeon 8500, not 7500; ATI doesn't have linux drivers for the 7500 because it seems to be too old.

Follow the installation instructions on that website and let us know if you have any trouble. Should be fairly straightforward.

---

### Post by hxcobd on 2010-02-11
BEFORE you try the driver from ATI's site, open Synaptic and search for "fglrx." A bunch of things come up, but the most important are:

xorg-driver-fglrx

xorg-driver-fglrx-dev

Install those 2 and all related packages and see if they work. You'll have to restart your computer after installing.

---

### Post by Joho22 on 2010-02-11
ive learned a few things about linux via the iphone jailbreak community cydia,
so I know that if I havent updated my sources, then im searching blindly.

what sources should I have cause this is all that turned up

---

### Post by Joho22 on 2010-02-11
and those green boxes mean installed, but my proprietary drivers are still 100% empty.

---

### Post by hxcobd on 2010-02-11
Sources won't matter as far as finding out what's already installed.

You might want to go into Settings -> Repositories in Synaptic and checking all of the options that make sense. On the Other Software tab, enable all 3-4 sources that show up.

It looks like you do have the old-school Radeon xorg driver installed, so that's a start. I'd still try to find the 2 packages I mentioned, though. They should be coming up in search, if nothing else.

---

### Post by hxcobd on 2010-02-11
> **Joho22 said:**
> and those green boxes mean installed, but my proprietary drivers are still 100% empty.

Drivers found in Synaptic are not proprietary. Proprietary would only be drivers installed using Hardware Drivers or from the ATI website.

---

### Post by Joho22 on 2010-02-11
> **hxcobd said:**
> Drivers found in Synaptic are not proprietary. Proprietary would only be drivers installed using Hardware Drivers or from the ATI website.

that makes sense now, gotcha, but im still confused at the adding sources / repositories part. you said check the 4 boxes that make sense, but im new enough that I am not sure which make sense... or if the 4 options are there.

Im sorry you are holding my hand through this but I am just trying to follow your lead.

---

### Post by Joho22 on 2010-02-11
this is what I see...

(I checked the 2 boxes that show up under the other tab, they were not like that)

---

### Post by Joho22 on 2010-02-11
after those two boxes are checked, these are my options after the same search

---

### Post by Objekt on 2010-02-11
AMD/ATI dropped support for some "older" Radeon products about a year ago, and as far as I can tell, they never supplied any drivers for Radeon 9500 and earlier.

It would help to know exactly what hardware you have.  ThinkPad T40-series were sold with many different configurations, with several different video cards available.  Which model is yours?  It sounds like a T41p, because you said it has a 1.7 GHz CPU.  That would suggest a Radeon 9500 card.

Whether you have a Radeon 7500 or 9500, you can't use the Catalyst package, that much is certain.  Open source to the rescue!  This page tells how to get 3D support for your "ancient" Radeon: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Executive summary: whether you have a Radeon 7500 or 9500 or something in between, you will get anything from "good" to "full" 3D support.  I don't know what "good" means as opposed to "full," but there is definitely hope for doing 3D under Ubuntu with your creaky "old" ThinkPad.  Please let us know whether you get it to work.

---

### Post by Joho22 on 2010-02-11
I did a wikipedia search on this earlier, I dont see any that say anything about a 9500, so Im assuming its the 7500. In the bottom right corner of the lcd there is a tiny t40 written, but since I got this second hand, Im gonna bet that the info may be long gone.

---

### Post by hxcobd on 2010-02-11
Joho, in that last screenshot you just posted, the 2 packages I was talking about are listed.

I'd right-click them, check Install, hit Apply, wait for them to download and install, and then restart your computer and see how that goes.

---

### Post by lunix- on 2010-02-11
This is how I installed my HD4850:

Downloaded the 'then' newest linux-driver on ATI's page.
then:
```
./ati-driver-installer-10-1-x86.x86_64.run --extract

cd fglrx-install*/arch/x86_64/usr/lib64/

ln -s libatiuki.so.1.0 libatiuki.so.1

cd ../../../..

sudo ./ati-installer.sh 10.1 --buildandinstallpkg Ubuntu/karmic
```

This is for 64bit and on a semi-new card.. Maybe need different drivers for other cards??
But it sure worked great on HD4850.
Good luck :)

---

### Post by Joho22 on 2010-02-11
I did as you asked, well i selected it, but do i want all of this extra stuff to happen?

---

### Post by Joho22 on 2010-02-11
also these throw me for a loop as well...
what are these options and do/why do I want them?

---

### Post by james_xxx on 2010-02-11
You **cannot** use fglrx, the proprietary ATI driver, on this card. A few years ago, ATI/AMD quit supporting pre-Radeon 9500 adapters, and at a later point in time, dropped support for all but their most recent Radeon HD cards.

With your Radeon 7000/7500, the driver you have by default when you install Ubuntu is the driver you need. You will likely not be able to enable any compositing managers (like Compiz).

It may well be that you will not be able to get optimal performance out of this card without creating the /etc/X11/xorg.conf file and adding configurations to it. You will need to do a search in this forum for your specific card, and likely try to copy an xorg.conf configuration that is reportedly working for others.

This is all sort of rough going for newcomers. The state of video/video drivers in Linux in general has always seemed to be a huge mess to me. My opinion is that this mess has been at its worst in Ubuntu. (I have had much better fortune with Fedora 12 or Debian Lenny with older Radeon cards.)

Good luck!

---

### Post by Joho22 on 2010-02-11
> **james_xxx said:**
> You **cannot** use fglrx, the proprietary ATI driver, on this card. A few years ago, ATI/AMD quit supporting pre-Radeon 9500 adapters, and at a later point in time, dropped support for all but their most recent Radeon HD cards.

With your Radeon 7000/7500, the driver you have by default when you install Ubuntu is the driver you need. You will likely not be able to enable any compositing managers (like Compiz).

It may well be that you will not be able to get optimal performance out of this card without creating the /etc/X11/xorg.conf file and adding configurations to it. You will need to do a search in this forum for your specific card, and likely try to copy an xorg.conf configuration that is reportedly working for others.

This is all sort of rough going for newcomers. The state of video/video drivers in Linux in general has always seemed to be a huge mess to me. My opinion is that this mess has been at its worst in Ubuntu. (I have had much better fortune with Fedora 12 or Debian Lenny with older Radeon cards.)

Good luck!

then in that case, would you suggest i download and install fedora?

---

### Post by Joho22 on 2010-02-11
> **Objekt said:**
> AMD/ATI dropped support for some "older" Radeon products about a year ago, and as far as I can tell, they never supplied any drivers for Radeon 9500 and earlier.

It would help to know exactly what hardware you have.  ThinkPad T40-series were sold with many different configurations, with several different video cards available.  Which model is yours?  It sounds like a T41p, because you said it has a 1.7 GHz CPU.  That would suggest a Radeon 9500 card.

Whether you have a Radeon 7500 or 9500, you can't use the Catalyst package, that much is certain.  Open source to the rescue!  This page tells how to get 3D support for your "ancient" Radeon: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Executive summary: whether you have a Radeon 7500 or 9500 or something in between, you will get anything from "good" to "full" 3D support.  I don't know what "good" means as opposed to "full," but there is definitely hope for doing 3D under Ubuntu with your creaky "old" ThinkPad.  Please let us know whether you get it to work.

I totally missed this post. If anyone hasfigured this out for a different build, please let me know. 
And yes if I do get it working I'll definitely post it up here.

---

### Post by james_xxx on 2010-02-11
There is no way I could absolutely guarantee that it work better for you, but if you were interested, you could always try an F12 Live CD. Mileage is going to vary depending on exactly which card you are trying to use.

Another approach, might be to try using Ubuntu Jaunty (the previous release). Jaunty is still supported, and IIRC, some of these older Radeon cards performed better in Jaunty than in Karmic. There is nothing wrong with running Jaunty, and there are still many people using it. I use it myself on one older laptop that has a Radeon Mobility video adapter.

On a *possibly*  brighter note, there are likely going to be some changes in the next version of Ubuntu that will bring some improvement to the native Free/Open Source ATI drivers.

---

### Post by Objekt on 2010-02-11
Fedora 12, or any other distro, is not going to magically cure your display problems.  You are going to have the same problems with video support, regardless of the distro, simply because you have an older Radeon.  This is not an Ubuntu-specific problem in any way.

---

### Post by Joho22 on 2010-02-11
> **Objekt said:**
> Fedora 12, or any other distro, is not going to magically cure your display problems.  You are going to have the same problems with video support, regardless of the distro, simply because you have an older Radeon.  This is not an Ubuntu-specific problem in any way.

Makes sense. And oddly sounds like the apple "I'm a mac" commercial knocking vista/7. 

Well I'd like to try to code this but being a beginner... I'm obviously not as good as the next person. 
Should I take this to the next level and hope for the same kindness in an irc chat?

I know I messed up last time I tried this so I guess I'm looking for a start point.

---

### Post by Objekt on 2010-02-11
> **Joho22 said:**
> also these throw me for a loop as well...
what are these options and do/why do I want them?

Unfortunately, none of those are useful in your situation.  Software Center doesn't take into account your hardware, so it doesn't try to keep you from installing stuff you can't use.  

Going item-by item:

The "jockey-gtk" application makes it easy to install any proprietary drivers that might be available for your hardware.  For example, the Catalyst or Nvidia proprietary drivers.  As discussed, there is no Catalyst package which will support your graphics card.

The "ATI binary X.org" option would install the fglrx driver, which, as stated above, also won't work.

"jockey-kde" does the same thing as "jockey-gtk" except it uses K Desktop Environment.  Functionally, no different from "jockey-gtk."

"Envy-NG" does pretty much the same thing as the two "jockey" apps.

The last option would install the ATI Catalyst package, again not an option for you.

Software Center often offers multiple ways to do the same thing.  It can be a bit confusing if you have no idea what you need.

---

### Post by Joho22 on 2010-02-11
as im goiing through the link objekt gave me, im going to try and post this as much as possible so i do not make a mistake, but this should settle what my card is

```
joho@joho-laptop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
joho@joho-laptop:~$
```

---

### Post by james_xxx on 2010-02-11
There is no doubt plenty of blame to go around. AMD dropping support for so many of their older cards (some not even all *that* old) is a huge contributor to this.

I do, however, lay some of the blame for these issues on Ubuntu. Rather than delaying the adoption of newer Xorg version until certain issues could be resolved, Ubuntu plugged ahead. At one point this left many users of certain Intel adapters in the cold. It is my impression that *some* of the issues people are having right now with certain ATI cards are for similar reasons.

Some of what I am saying is admittedly based on my subjective experiences. I have a few machines using these older cards that have faired better using Fedora 12 and Debian Lenny than with Ubuntu Karmic. This is, however, **not** to say that in the next iteration of these Operating Systems the tables might in some way be turned around differently. My intent is definitely not to just bash Ubuntu, although I do believe some of these above mentioned issues could have been avoided to some extent with more care.

---

### Post by Joho22 on 2010-02-11
> **Objekt said:**
> Unfortunately, none of those are useful in your situation.  Software Center doesn't take into account your hardware, so it doesn't try to keep you from installing stuff you can't use.  

Going item-by item:

The "jockey-gtk" application makes it easy to install any proprietary drivers that might be available for your hardware.  For example, the Catalyst or Nvidia proprietary drivers.  As discussed, there is no Catalyst package which will support your graphics card.

The "ATI binary X.org" option would install the fglrx driver, which, as stated above, also won't work.

"jockey-kde" does the same thing as "jockey-gtk" except it uses K Desktop Environment.  Functionally, no different from "jockey-gtk."

"Envy-NG" does pretty much the same thing as the two "jockey" apps.

The last option would install the ATI Catalyst package, again not an option for you.

Software Center often offers multiple ways to do the same thing.  It can be a bit confusing if you have no idea what you need.

confusing is the word for sure! heh, at least someone empathizes with the poor little noob. though now that I know what kind of card I have, that walkthrough you linked a few posts ago, is that my best option?

---

### Post by Objekt on 2010-02-11
Yep, a 7500.  No difference from the 9500, as far as getting 3D support.

The oldest Radeon I've had to deal with in Linux was an x1650, so I haven't actually done the procedure I linked to.  If you can make it work, you are entitled to feelings of superiority. :D

---

### Post by james_xxx on 2010-02-11
Neither Software Center, nor any of these other options are going to be of any help with this video adapter.

The driver you have when you install Ubuntu is the **only** option you have.

Like I said, your best bet is to scan the forums for 'Radeon Mobility 7500' and see what other people have done with xorg.conf to get it running as well as possible.

---

### Post by Joho22 on 2010-02-11
> **Objekt said:**
> Yep, a 7500.  No difference from the 9500, as far as getting 3D support.

The oldest Radeon I've had to deal with in Linux was an x1650, so I haven't actually done the procedure I linked to.  If you can make it work, you are entitled to feelings of superiority. :D

Where is the cringe smiley when you need one...
well since you are the expert ... at least compared to me,
want to read some of that and clue me in on what I might need to do to my system to prepare for this while I take time to say goodbye to my family before i head into battle with code?

---

### Post by Joho22 on 2010-02-11
> **james_xxx said:**
> Neither Software Center, nor any of these other options are going to be of any help with this video adapter.

The driver you have when you install Ubuntu is the **only** option you have.

Like I said, your best bet is to scan the forums for 'Radeon Mobility 7500' and see what other people have done with xorg.conf to get it running as well as possible.

glad i read the rest of page 4 before i dove in.
how would one scavenge the forums for that stuff?

---

### Post by james_xxx on 2010-02-11
I wish I could take the time to look for a possible working xorg.conf for you, but I have to leave in the next few minutes.

Just be mindful that there could be a fair bit of difference between how one would configure a Radeon 7000, or a Radeon Mobility 7500, or a Radeon 9000, etc. The difference, for example, between a Radeon 7000 and a Radeon 9000 is pronounced. You may be able to use desktop effects with the 9000. With a 7000, that would be very doubtful.

If I get the chance later this evening, I may try to do some looking, if you have not been able to find anything.

---

### Post by Joho22 on 2010-02-11
> **james_xxx said:**
> I wish I could take the time to look for a possible working xorg.conf for you, but I have to leave in the next few minutes.

Just be mindful that there could be a fair bit of difference between how one would configure a Radeon 7000, or a Radeon Mobility 7500, or a Radeon 9000, etc. The difference, for example, between a Radeon 7000 and a Radeon 9000 is pronounced. You may be able to use desktop effects with the 9000. With a 7000, that would be very doubtful.

If I get the chance later this evening, I may try to do some looking, if you have not been able to find anything.

Ill be searching, if I find something, youll know here.
Thanks a ton James and Objekt too, i know its a bitch to deal with noobs, I used to do IT for a Non-Profit company... believe me I know how hard it is to deal with idiots.

---

### Post by hxcobd on 2010-02-11
James looks to be considerably more well-versed than myself as far as video drivers go, so I don't doubt that his words are true.

I had similar video issues myself running a few distros of linux 2-3 years ago. I believe I had a Radeon 7000 at the time.

I spent literally weeks editing xorg.conf by hand to get proper screen resolutions, refresh rates, and so on.

I never could get adequate performance out of the thing. I think that's why, when I installed 9.10 on this laptop I'm using, and it popped up with, "We found a proprietary driver without you even doing anything!", I literally almost passed out from sheer joy.

Trying another distro may honestly be your best bet, if you're really concerned about video performance.

One distro that always performed really well for my video cards in the past is called Elive.

PCLinuxOS and SAM were two other distros I always really liked.

I should forewarn you though: Ubuntu has the BEST hardware drivers, especially for things other than video, all-around.

Especially for a new person switching from Windows, I definitely would stay with Ubuntu, personally. It's by far the most-developed, most well-known, and most stable distro out there. (A generalization, of course.)

---

### Post by Joho22 on 2010-02-11
A list of the ones I have found that might pertain...

[http://ubuntuforums.org/showpost.php?p=8780129&postcount=6](http://ubuntuforums.org/showpost.php?p=8780129&postcount=6)

[http://ubuntuforums.org/showthread.php?t=1345912&highlight=Radeon+Mobility+7500%2C+xorg.conf](http://ubuntuforums.org/showthread.php?t=1345912&highlight=Radeon+Mobility+7500%2C+xorg.conf)

[http://ubuntuforums.org/showpost.php?p=7746065&postcount=1](http://ubuntuforums.org/showpost.php?p=7746065&postcount=1)

thus far

---

### Post by Joho22 on 2010-02-11
> **hxcobd said:**
> James looks to be considerably more well-versed than myself as far as video drivers go, so I don't doubt that his words are true.

I had similar video issues myself running a few distros of linux 2-3 years ago. I believe I had a Radeon 7000 at the time.

I spent literally weeks editing xorg.conf by hand to get proper screen resolutions, refresh rates, and so on.

I never could get adequate performance out of the thing. I think that's why, when I installed 9.10 on this laptop I'm using, and it popped up with, "We found a proprietary driver without you even doing anything!", I literally almost passed out from sheer joy.

Trying another distro may honestly be your best bet, if you're really concerned about video performance.

One distro that always performed really well for my video cards in the past is called Elive.

PCLinuxOS and SAM were two other distros I always really liked.

I should forewarn you though: Ubuntu has the BEST hardware drivers, especially for things other than video, all-around.

Especially for a new person switching from Windows, I definitely would stay with Ubuntu, personally. It's by far the most-developed, most well-known, and most stable distro out there. (A generalization, of course.)


hxcobd you too were a huge help, and I am still researching up a storm.

---

### Post by james_xxx on 2010-02-11
Joho22,

I looked through the links you included in your last post. The second one looks very promising:

[http://ubuntuforums.org/showthread.php?t=1345912&highlight=Radeon+Mobility+7500%2C+xorg.conf](http://ubuntuforums.org/showthread.php?t=1345912&highlight=Radeon+Mobility+7500%2C+xorg.conf)

You may already know how to do this, but one way to go about it would be to open a terminal, and enter:

```
sudo nano /etc/X11/xorg.conf
```

Then enter your password.

After this, copy all of the text from the xorg.conf in your link into the terminal.

After this, press CTL-X, enter yes, then... reboot!!

Hopefully at this point, you will be experiencing better performance. 

Let us know how it goes!

---

### Post by starsprout on 2010-02-11
Hey guys any chance you can help me get my "VGA compatible controller: ATI Technologies Inc Device 9712" to run Compiz and OpenGL?

I'm in 64-bit 9.10 on a brand new Compaq Presario CQ61 laptop (don't laugh, it was a good price).

I'm able to get it clear with good resolution with fglrx and can even get the ATI (AMD?) "official" driver to work for resolution and create a xorg.conf file and all, but I can't get the Distro-specific ATI (AMD) driver to build it's package in order to run 2D or 3D.

Any tips would be swell - I'm fairly agile with a terminal and can send you test and query results easily and quickly...

James_xxx? Hxcobd? Anyone?


Here's the output from Bash when I go through the steps to install the Ubuntu/karmic package:


root@TZELTAL:/home/iguanamin/Software# sh ./ati-driver-installer-10-1-x86.x86_64.run --buildpkg Ubuntu/karmic
Created directory fglrx-install.fV9GdD
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.69................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/karmic
Package build failed!
Package build utility output:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.690-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
test -x debian/rules
mkdir -p "."
#Create important strings

I'm skipping a lot of output here - it was all good....
**here's** where the errors show:

 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlopen used by debian/xorg-driver-fglrx/usr/lib/libXvBAW.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlsym used by debian/xorg-driver-fglrx/usr/lib/libXvBAW.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlerror used by debian/xorg-driver-fglrx/usr/lib/libXvBAW.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XGetGeometry used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReadPad used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFree used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XSetErrorHandler used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlsym used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XGetErrorDatabaseText used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlclose used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XMaxRequestSize used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XCreateGC used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFreeFontInfo used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: 21 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: couldn't find library libatiuki.so.1 needed by debian/xorg-driver-fglrx/usr/lib/xorg/modules/linux/libfglrxdrm.so (ELF format: 'elf64-x86-64'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.fV9GdD



How do I set LD_LIBRARY_PATH and to WHAT?

---

### Post by james_xxx on 2010-02-11
starsprout,

I won't have a lot of time this evening, but could you answer a few questions?

What output do you get from 'lspci | grep VGA'?

Did you first try using Ubuntu's hardware drivers utility before using the install script from AMD?

---

### Post by starsprout on 2010-02-11
> **james_xxx said:**
> starsprout,

I won't have a lot of time this evening, but could you answer a few questions?

What output do you get from 'lspci | grep VGA'?

Did you first try using Ubuntu's hardware drivers utility before using the install script from AMD?

I did try the Ubuntu hardware driver (that's fglrx? xorg-fglrx-driver). I removed it but can reinstall. I honestly think I did go right to AMD and didn't even try to run OpenGL in the Ubuntu driver.

Here's my lspci | grep VGA output:

root@TZELTAL:/home/iguanamin/Software# lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712
root@TZELTAL:/home/iguanamin/Software#

---

### Post by james_xxx on 2010-02-11
The recommended utility for installing some proprietary hardware drivers is called either jockey-gtk or jockey-kde, depending on your Desktop Environment.

If you are using Gnome, you should be able to find it in the menu. I believe it is under 'Administration', and listed simply as something like 'hardware drivers'.

This utility is not flawless, but it would be worth trying that before you go a different route.

BTW, I am not sure which adapter 'Device 9712' stands for. Do you know? I was just trying to determine whether or not fglrx will work with your card. I am assuming it will, since you said this was a new laptop.

---

### Post by starsprout on 2010-02-11
I reinstalled the ATI Proprietary drivers using the System Hardware tool (jockey?)

When I restarted I had several new errors and had to come into low graphics mode. Now I also reverted to a backed up version of xorg.conf and will reboot to see if that does any better. Either way, I'll eventually get the sharp resolution back, but I want OpenGL features.

Yes it is a brand new laptop - I was confused about that "ATI Technologies Inc Device 9712" descriptor also. Earlier today when I had fglrx configured pretty well I was able to type fglrxinfo and it showed a different model ATI "Mobility Radeon" card and number. Hmmm.

Thanks for whatever help.
Stay tuned....

---

### Post by starsprout on 2010-02-11
I'm back up and running with Xorg and fglrx and I can even view the ATI Catalyst Control Panel Administrator where it says my card is:
ATI Mobility Radeon HD 4200

Still no OpenGL though. Good resolution, but no effects (Compiz, Cairo-Dock, etc)

Nonetheless, I still believe in Linux.

---

### Post by Objekt on 2010-02-12
> **Joho22 said:**
> Ill be searching, if I find something, youll know here.
Thanks a ton James and Objekt too, i know its a bitch to deal with noobs, I used to do IT for a Non-Profit company... believe me I know how hard it is to deal with idiots.

No problem at all.  We were all "noobs" once.  I still feel like a "noob" compared to the real hardcore Linux guys, people who use stuff like Gentoo and (shudder) Arch Linux.  I'm glad I've learned enough to contribute to this forum.

I would be interested to know what kind of 3D stuff you can do on your laptop.  An easy way to test it is the game Neverball, which is available through the Ubuntu Software Center.  If that game runs smoothly, you probably have all the 3D support possible.

I second the earlier point about turning off desktop effects.  They are pretty, but are an unnecessary drag on older hardware.

---

### Post by starsprout on 2010-02-12
my card is supposed to be brand new - I just bought this Compaq 

After re-installing the drivers from ATI (AMD) website, which apparently installed xorg and fglrx, I'm back running this xorg.conf with good resolution but no accelerated graphics, which I should have I think.

Right now I can't even load the ATI Catalyst Manager


Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by hxcobd on 2010-02-12
Starsprout, you have roughly the same video card that I currently have in my laptop. I'm using a Radeon Mobility 2600 HD.

Based on what works in my setup, the Hardware Drivers (or Jockey, as someone else mentioned) is probably going to be your best, most stable bet.

If you open Hardware Drivers and something actually comes up, I'd definitely make all efforts to get that working before trying the ATI driver.

I'm a bit hesitant to open my mouth on how to fix this, as you said you're on 64-bit linux, and I have almost zero experience with it. 64-bit linux looked like an even bigger pain in the *** than 64-bit Windows, and for that, I've avoided it like the plague...

---

### Post by hxcobd on 2010-02-12
Also, probably obvious, but star, did you make sure to install the x86_64 drivers from ATI, and not the x86 ones?

---

### Post by starsprout on 2010-02-12
yeah I looked closely at the driver version - the filename has _86 in it no matter which version you download from ATI so I guess it's all the same package (I have explored the package and it has nearly 100 distribution-specific directories in it).

What's more confusing on that note is that the ATI website says 64-bit users have to have the 32-bit pack installed first for the 64-bit to work.

I doubt it's a 64-bit issue. 

HX - you say you're running a similar card with the Jockey-installed "ATI" driver? Do you get 2d or 3d effects? (Compiz, Cairo-dock, wobbly windows, etc.?)

My other HP laptop, 4 years old, functions fine with the off-the-shelf ubuntu drivers. There's gotta be a way to get this one to perform.

Incidently I'm going through the exact same issue on my desktop, where I have an added ATI Radeon 2600XT (with 4 outputs) that I can't get to run 3D either. I did learn a lot in the last day or two about it all, so may try that again.

Otherwise, I can't even figure out if I have all the prerequisites in place to run the driver from ATI.

What's the difference between the "ATI Drivers" from the AMD.com website and the Jockey version?

---

### Post by Objekt on 2010-02-12
In my experience, the Jockey-provided proprietary drivers are always a version or two behind the most recent release.  

Certainly that's the case with Nvidia.  Jockey wants to install version 185.something of the Nvidia drivers, but I opted to download and install the 190.53 .run package from Nvidia's website instead.  

I don't know whether Jockey also suggests an older Catalyst package, because I don't have ATI hardware in any of my computers any more.

To further answer your question: using Jockey to install the drivers is easier.  It does all the work automagically, so all you have to do is reboot.  If you download the drivers from AMD, you will have to manually shut down Xserver, run the install package, and then reboot.

---

### Post by Joho22 on 2010-02-12
So I have another day off Sunday and I'll give those codes a shot then. Today I'm stuck in my cube at work.

---

### Post by hxcobd on 2010-02-12
> **starsprout said:**
> 

HX - you say you're running a similar card with the Jockey-installed "ATI" driver? Do you get 2d or 3d effects? (Compiz, Cairo-dock, wobbly windows, etc.?)

What's the difference between the "ATI Drivers" from the AMD.com website and the Jockey version?

Yup, I have full 2D and 3D acceleration. Compiz worked fine, and every game I've tried has run like a beauty.

As someone else posted, the only difference between the Jockey version and the ATI download is driver version. I'm sure the Jockey versions are tweaked a bit for the purpose of streamlining into Ubuntu and Jockey.

It would be nice if Hardware Drivers gave a bit more information on the actual driver it installed. I didn't even see a release version, just glancing at it.

---

### Post by waynefoutz on 2010-02-12
> **james_xxx said:**
> There is no way I could absolutely guarantee that it work better for you, but if you were interested, you could always try an F12 Live CD. Mileage is going to vary depending on exactly which card you are trying to use.

Another approach, might be to try using Ubuntu Jaunty (the previous release). Jaunty is still supported, and IIRC, some of these older Radeon cards performed better in Jaunty than in Karmic. There is nothing wrong with running Jaunty, and there are still many people using it. I use it myself on one older laptop that has a Radeon Mobility video adapter.

On a *possibly*  brighter note, there are likely going to be some changes in the next version of Ubuntu that will bring some improvement to the native Free/Open Source ATI drivers.

I have a a Radeon X1270, The only way I can get full 3d support is by sticking with intrepid. 

My suggestion is to stay away from ATI video hardware if you want to run anything other than windows. ATI dropped support for my laptop's video with the release of Catalyst 9.4. I'm stuck with 9.3 which will not run on Jaunty or later.

---

### Post by Joho22 on 2010-02-13
> **james_xxx said:**
> Joho22,

I looked through the links you included in your last post. The second one looks very promising:

[http://ubuntuforums.org/showthread.php?t=1345912&highlight=Radeon+Mobility+7500%2C+xorg.conf](http://ubuntuforums.org/showthread.php?t=1345912&highlight=Radeon+Mobility+7500%2C+xorg.conf)

You may already know how to do this, but one way to go about it would be to open a terminal, and enter:

```
sudo nano /etc/X11/xorg.conf
```Then enter your password.

After this, copy all of the text from the xorg.conf in your link into the terminal.

After this, press CTL-X, enter yes, then... reboot!!

Hopefully at this point, you will be experiencing better performance. 

Let us know how it goes!

AHHHH!!!!
Omg! My girlfriend just laughed at me cause I got so excited i shook my hands in the air like a little school girl. (I swear I like girls...)

Im 99% sure it worked because the resolution was strange when i rebooted and then went to system > pref > display and was able to go to 1024 x 768.

Ill test it out with Warcraft tomorrow after work because I have to get it to download and re install playonlinux / wine etc.

you guys, if im ever in your town, i owe you a round of beers!

Ill keep you all posted, thanks a lot!

---

### Post by james_xxx on 2010-02-13
Joho22,

I am glad to hear that significant progress has likely been made. Congrats!

One note of caution, though...

Your video card is an older card. You should be able to get some 3D acceleration going and so on, but performance with WoW and other games that might be 3D intensive may still require a bit more than this card will be able to handle.

That being said, I wish you well!

---

### Post by Joho22 on 2010-02-13
> **james_xxx said:**
> Joho22,

I am glad to hear that significant progress has likely been made. Congrats!

One note of caution, though...

Your video card is an older card. You should be able to get some 3D acceleration going and so on, but performance with WoW and other games that might be 3D intensive may still require a bit more than this card will be able to handle.

That being said, I wish you well!


Quick update 
tried using OpenGL and wine on wc3 and it did kick back an error. 
I'm not doing wow, it's the strategy game before wow came out. It's not as graphic intensive. 

I'm back at work now so I'll check it out in a couple hours.

---

### Post by Joho22 on 2010-02-13
Btw , this laptop ran all of the apps I'm installing before when it was a windows rig.

---

### Post by Joho22 on 2010-02-13
so this is the error that it kicked back when I tried to run the program in opengl, which i thought woulda solved my problems.

when I ran the program without opengl it showed me the start menu screen, without the menu. and without any animation. sound played but thats about it.

Kinda confused here...

---

### Post by waynefoutz on 2010-02-13
I still say the only way you are going to get opengl in ubuntu out of that card is by running an old build of ubuntu, probably 8.10 or earlier, and installing an old version of catalyst.

You can get the driver here:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.35&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.35&lang=English")

9.3 is the last version that supports your hardware. This driver is the only way you are going to get openGL out of that card. Unfortunatly, it will not run on Jaunty or later. Intrepid's support ends in April, Hardy Heron, 8.04, you are good until  April 2011. 

Also there are other distro's out there, go to Distrowatch, here is Ubuntu's page, 
[http://distrowatch.com/table.php?distribution=ubuntu]("http://distrowatch.com/table.php?distribution=ubuntu")

Look around for other distros if you like. Scroll down and see which version of xorg-server the distro is running. It's the last entry. You want something that is running version 1.5.2 or lower. Catalyst 9.3 will not run with Jaunty's 1.6.0 xorg-xserver

I have similar hardware in my laptop, I'm running Intrepid, (8.10) with the 9.3 Catalyst. It runs opengl as good as it did in windows. Not sure What I'm going to do in April when intrepid is no longer supported. I may keep running it anyway, I might just install 10.04 and dual boot Windows XP for my gaming, or I may go to another distro, I'm leaning toward CentOS, which is an open source clone of Red Hat. 

I banged my head against the wall for months trying to get my ATI card to run my windows games, for me, it is Team Fortress 2, Going to an older build of Ubuntu is only solution I could come up with. The latest closed source drivers don't support our older cards, and the open source drivers work, but you get no openGL. The old driver is the only option.

---

### Post by Joho22 on 2010-02-14
> **waynefoutz said:**
> I still say the only way you are going to get opengl in ubuntu out of that card is by running an old build of ubuntu, probably 8.10 or earlier, and installing an old version of catalyst.

You can get the driver here:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.35&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.35&lang=English")

9.3 is the last version that supports your hardware. This driver is the only way you are going to get openGL out of that card. Unfortunatly, it will not run on Jaunty or later. Intrepid's support ends in April, Hardy Heron, 8.04, you are good until  April 2011. 

Also there are other distro's out there, go to Distrowatch, here is Ubuntu's page, 
[http://distrowatch.com/table.php?distribution=ubuntu]("http://distrowatch.com/table.php?distribution=ubuntu")

Look around for other distros if you like. Scroll down and see which version of xorg-server the distro is running. It's the last entry. You want something that is running version 1.5.2 or lower. Catalyst 9.3 will not run with Jaunty's 1.6.0 xorg-xserver

I have similar hardware in my laptop, I'm running Intrepid, (8.10) with the 9.3 Catalyst. It runs opengl as good as it did in windows. Not sure What I'm going to do in April when intrepid is no longer supported. I may keep running it anyway, I might just install 10.04 and dual boot Windows XP for my gaming, or I may go to another distro, I'm leaning toward CentOS, which is an open source clone of Red Hat. 

I banged my head against the wall for months trying to get my ATI card to run my windows games, for me, it is Team Fortress 2, Going to an older build of Ubuntu is only solution I could come up with. The latest closed source drivers don't support our older cards, and the open source drivers work, but you get no openGL. The old driver is the only option.

I'll give it a shot on my next day off. 
You say 8.10 for a temp fix. 

I'll give this a shot. Tonight cause the iso is downloading at 1.1megs
girlfriends with fios rule!

---

### Post by Joho22 on 2010-02-14
So that driver will work for a Radeon mobility 7500?
I dont see it on that list...

I reformmated again and was about to install that when I realized it wasnt the 7500 mobility driver...

Just double checking.
Crap its 4am

---

### Post by waynefoutz on 2010-02-14
> **Joho22 said:**
> So that driver will work for a Radeon mobility 7500?
I dont see it on that list...

I reformmated again and was about to install that when I realized it wasnt the 7500 mobility driver...

Just double checking.
Crap its 4am
 
I apologize!

I thought you had the 9500 mobility....
You may have to go with an older version of catalyst....

I just found this, your card was working three years ago:
[http://ubuntuforums.org/showthread.php?t=361136]("http://ubuntuforums.org/showthread.php?t=361136")

I'm sorry I gave you the wrong info, but I still think I'm barking up the right tree. I bought my laptop exactly one month before ATI  dropped all linux support and declared my graphics chipset obsolete. As the link above demonstrates, you card worked in older versions of Ubuntu. The problem is Ubuntu is a distro that rapidly evolves. It's over-hauled every six months. 

The latest linux kernel 2.6.32, which is not included with Karmic but will be in Lucid when it come out next April, was heralded as the answer to us guys with older ATI cards, this kernel would give us 3d support with open source drivers. Here is a guide on installing it on Karmic:
[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/#]("http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/#")
I did this on mine, I couldn't tell any difference. It didn't break anything, you might want to give it a try. 

Other than that, with an old card like that, the only answer I've found is moving to an older distro. One that isn't updated as often as Ubuntu. I'm probably going to try Lucid in April, If that doesn't do it for me, I'm probably going to migrate to CentOS or Debian. Either way, I'll never buy a laptop with ATI in it again. My daughter has a Dell laptop two years older than my Dell laptop, with an Intel integrated graphics chip in it, and it runs Karmic beautifully with full 3d.

Give 8.10 a try, and follow the guide above when it was working back then....actually 8.04 might be better, since it's supported until April 2011. It's kind of a bear to set up wireless on though, since it has an older version of network-manager.

---

### Post by Joho22 on 2010-02-14
Crap, you posted that retraction too late. 
I tried installing and thought all went well but...
I now have a scrambled screen. Thank god for the iPhone or I'd be effed. 

I'll try your new link but first...
How do I fix my screen?

---

### Post by Joho22 on 2010-02-14
So my laptop now looks like those old 8-bit video games when not fully inserted into the nintendo. 
So needless to say I'm beside myself with frustration and this close to buying a MacBook pro.

---

### Post by waynefoutz on 2010-02-14
> **Joho22 said:**
> So my laptop now looks like those old 8-bit video games when not fully inserted into the nintendo. 
So needless to say I'm beside myself with frustration and this close to buying a MacBook pro.

boot up in the recovery mode, so you get a command line, type 

sudo dpkg-reconfigure xserver-xorg

this should launch an app so you can autodetect and put things back the way they were

Macbook Pro might not be a bad idea;)

---

### Post by DeusEx on 2010-02-15
You might want to switch to the open source drivers. I have a radeon 9500 non pro (very similar to 9700) which, FINALLY, works very well with the open source drivers.

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

Granted, since you've probably been messing with all kinds of drivers the best thing to do is to get a fresh install of your ubuntu.
Alternatively you can clean up every trace of the proprietary fglrx drivers.

Open source drivers should work out of the box with a fresh install, the only thing you may need to do is enable acceleration by adding 'ati' to your xorg.conf.

---

### Post by starsprout on 2010-02-15
Strange - I got it all working in Kubuntu - KDE

I'm with you on the reinstall. That's what I'm going to do, except I'm going with Kubuntu - I like it

By the way, FYI - I got tons of faster help than forums using IRC. Just sudo apt-get install xchat - the best irc server I found for ATI and Radeon help was FreeNode - they have a ton of useful channels with ppl in them round-the-clock

---

### Post by waynefoutz on 2010-02-15
I'm glad you all got it working...I had no luck with open source with  my Radeon Xpress 1270 (which is much newer than the 9700) with Karmic and the 2.6.32 kernel. It runs some stuff, but Google earth and 3d games don't display properly. I read that article about the ATI drivers "coming of age" a few months ago...I've been stuck on Intrepid since it's release. Jaunty broke my 3d. I had hopes for Karmic, especially in light of that article. After I installed Karmic, I upgraded the kernel to .32, reinstalled the open source drivers...I couldn't tell the difference. I even tried Fedora 12 which comes with the .32 kernel, and the screen was garbled on the live cd.  I ended up reinstalling Intrepid. Hopefully they get the open source drivers working for me when Lucid come out.

---

