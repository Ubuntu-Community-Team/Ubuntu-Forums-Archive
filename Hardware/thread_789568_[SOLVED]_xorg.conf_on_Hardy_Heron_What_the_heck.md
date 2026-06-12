---
title: "[SOLVED] xorg.conf on Hardy Heron: What the heck?"
date: 2008-05-10
forum: Hardware
---

### Post by Arthur Archnix on 2008-05-10
Can someone please tell me why there are no settings in my xorg.conf for my video card? In gutsy a pretty darn good xorg.conf file would be generated for you automagically at install time. Now, there's nothing there but "configured video device".

Instead, we have a hidden utility for changing video settings: 
```
gksudo gtk-displayconfig
```But I don't want to use the gui. My changes are not persisting. I think. It's hard to tell, the gui thingy isn't that great. What file do I edit, how is ubuntu determining what driver I need to use, for what card, and where can I edit advanced options like disabling dri?

And most importantly, where is this documented?

---

### Post by roma2 on 2008-05-10
Everything you need to configure is in your /etc/X11/xorg.conf file, including driver version, dri settings, video modes, etc.

to get the file section parameters, open a terminal and type ```
man xorg.conf
``` and for more information use ```
man xorg
```

To get a list of your pci devices (e.g., your video chipset) use ```
lspci
``` You'll need to restart the X server after your changes by either logging out or using <ctrl>+<alt>+<backspace>. I would include a copy of my file, but it is currently a mess as I am trying to configure twinview for my external monitor on my laptop docking station.

Hope this helps :)

---

### Post by Arthur Archnix on 2008-05-11
I appreciate the response Roma, but it doesn't really address my question. At least, not directly. My point was that xorg.conf contains zero information about my video card. Under Gutsy there was a section called device that listed my video card (properly), the current driver in use, the name of it (for system use), and any options. Now, there is only a name "configured video card". [B]Configured by whom, where, how? 
[/B] 
I ran dpkg-reconfigure -xserver-xorg, and it didn't even have a try at my video card. All it did was reconfigure my keyboard.

So again, if there's no information about my video card in xorg.conf, how is Ubuntu determining the display information? Do I edit xorg.conf and hope Hardy doesn't decide to over-ride my settings, or am I permitted to understand what's going on, given the option to use it or lose it. So to speak.

PS. Have you taken a look at the man page for xorg.conf? Clearly, I'm not the only one frustrated with the lack of documentation. :)

---

### Post by GnuSense on 2008-05-11
Art, if you backed up your Hardy xorg.conf you may well be able to splice bits back in to your new, ultra-minimalist xorg.conf like I [did]("http://ubuntuforums.org/showthread.php?t=789724").

Actually, since I couldn't get Hardy to configure dual monitors using the GUI tools (and, AFAIK, there are NOT any other tools in Hardy and the GUI tools are pretty rough at this point), I just used my old xorg.conf and edited in enough "Configured" stuff to get my rodent to work in Hardy.  It worked well enough even though I understand the old "xinerama" dual monitor stuff is deprecated.

If you didn't back up your old xorg.conf maybe you can use your older Ubuntu live discs to generate another one.

---

### Post by Arthur Archnix on 2008-05-11
Gnu, I've read your 'report'. It's exactly why I'm trying to get some answers. Luckily, I'm not having any problems. Whatever black magic is operating in the background is working. But the reason I switched to Linux was because it wasn't black magic. Everything was open to the user. Ubuntu seems to be moving away from that. Why else does no one seem to know what files need to be edited, and how? Why is there no documentation about the changes from Gutsy to hardy in terms of manually configuring the devices?

Fedora 9 is being released in a few days, then there's debian, arch... I know there are other options. But what's happening to Ubuntu? Why are the only tools gui tools? Why does dpkg-reconfigure xserver-xorg not do what it used to? Where is this change documented?

---

### Post by jocko on 2008-05-11
> **Arthur Archnix said:**
> 
Fedora 9 is being released in a few days, then there's debian, arch... I know there are other options. But what's happening to Ubuntu? Why are the only tools gui tools? Why does dpkg-reconfigure xserver-xorg not do what it used to? Where is this change documented?

Actually, what causes this is the fact that the version of xorg in hardy automatically detects card and driver and is no longer dependent on xorg.conf for configuration.
This means if nothing is specified in xorg.conf, xorg configures itself.
I'm sure this will happen in other distros as well when they start using xorg 7.3 or higher.
I guess if you want to find documentation on this, you should check [x.org]("http://www.x.org/wiki/Releases/7.3").
I think this is good (when it works), but I don't understand why they had to remove the driver and display options from dpkg-reconfigure...

---

### Post by mc4man on 2008-05-11
unfortunately i think what hardware you have, what drivers your using, ect. will determine how and what path to take to get things right. What seems consistent is if the 'autodection' isn't doing this you need what I'd call a working xorg.conf. that you can edit if need be and have it take effect. i did a fresh install last night of hardy on my main box (nvidia 7800 gs) and thru a bit of bs managed to get a good xorg.conf, edited in a few lines and it's now working perfectly ala gutsy. My method may not work for you so not worth posting. What I would suggest you _may_ try is enable screens and graphics and enter the proper info there - that should give you a xorg you can work with. (can be found edit menus-> other
If the new xorg isn't persistent let me know i have a couple of of the wall ideas in that regard. 
May work best with nvidia card and restricted drivers

---

### Post by roma2 on 2008-05-12
> **Arthur Archnix said:**
> Gnu, I've read your 'report'. It's exactly why I'm trying to get some answers. Luckily, I'm not having any problems. Whatever black magic is operating in the background is working. But the reason I switched to Linux was because it wasn't black magic. Everything was open to the user. Ubuntu seems to be moving away from that. Why else does no one seem to know what files need to be edited, and how? Why is there no documentation about the changes from Gutsy to hardy in terms of manually configuring the devices?

Fedora 9 is being released in a few days, then there's debian, arch... I know there are other options. But what's happening to Ubuntu? Why are the only tools gui tools? Why does dpkg-reconfigure xserver-xorg not do what it used to? Where is this change documented?

Yeah, I misunderstood your original post. Sorry about that.

---

### Post by Yellow Pasque on 2008-05-12
> But the reason I switched to Linux was because it wasn't black magic. Everything was open to the user. Ubuntu seems to be moving away from that.
Ubuntu is a user-friendly Linux distribution in the Debian/GNU tradition. It's got a huge repo, is well-documented, and is very configurable.

If you want an elegant, minimalistic build, check out Arch Linux.

---

### Post by Arthur Archnix on 2008-05-12
I think Jocko's on the right track. xorg 7.3 is the main culprit here, though why the automagic reconfiguration of xserver has been crippled is unclear. The site, unfortunately, has nothing to speak of. They just refer you to the man pages. The man pages, are pretty much the same as they were under gutsy, though I'll keep looking there for something new.

I'd gone through them before, however, and noted that I'm not the only one frustrated with the poor documentation. Read the man page for xorg.conf yourself if you want to understand why I say that. Hint: It's in the video adapter section.

Temüjin: You don't need to sell me on Ubuntu. I'm sold. I'm just frustrated. I wish I understood what's changed from Gutsy in X. I'm trying to find out, reading man pages, searching forums, asking on IRC, searching the net... I can't find out. I can't get answers. I agree that about tries to be user-friendly, but is this ongoing mystery really in the Debian tradition? I see less and less in Ubuntu that's in line with the Debian tradition with every release. 

Just to repeat... I'm not having problems. My video works fine. But I don't understand how it works fine, or why, and I used to. And this bothers me. Because if it breaks I can't fix it. And I can't help others fix theirs. 

I'm gonna read up on x 7.3 and post back here if I find anything. Assuming some brilliant ubunterite doesn't fill in the details before I manage to do that.

---

### Post by Arthur Archnix on 2008-05-13
Here's the deal: Autodetection is just where its at and where things are going. If you want to override it, just setup your xorg.conf.

If you want to specify a driver for the xserver to use, you have to do that in xorg.conf. If you change it via the gui, there's nothing saying the next time you reboot it won't just autodetect it again and load whatever driver it wants. At least, that's my understanding.

---

### Post by Zorael on 2008-05-13
> **Arthur Archnix said:**
> If you change it via the gui, there's nothing saying the next time you reboot it won't just autodetect it again and load whatever driver it wants. At least, that's my understanding.
Hmm, one would think that changing it via Gnome's gui would save said changes to xorg.conf. It does in KDE. :>

*jab*

---

### Post by Yellow Pasque on 2008-05-13
> **Zorael said:**
> Hmm, one would think that changing it via Gnome's gui would save said changes to xorg.conf. It does in KDE. :>

*jab*
I wonder if the GUI asks for a password or is being started with root permissions from the terminal (i.e. gksudo)..

---

### Post by Zorael on 2008-05-13
> **Temüjin said:**
> I wonder if the GUI asks for a password or is being started with root permissions from the terminal (i.e. gksudo)..
Very valid question. It does in KDE. :>

*jab^2*

---

### Post by Arthur Archnix on 2008-05-15
I'm going to mark this as solved, because I found release notes for Fedora 9 here: [http://docs.fedoraproject.org/release-notes/f9/en_US/sn-Xorg.html](http://docs.fedoraproject.org/release-notes/f9/en_US/sn-Xorg.html)  They kind of make sense for Ubuntu too. But if anyone knows of any Ubuntu release notes with comparable information please link them. I'm back on Gutsy for now after too many problems with Hardy.

EDIT: I've found some release notes for Hardy:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

[http://www.ubuntu.com/getubuntu/releasenotes/804overview](http://www.ubuntu.com/getubuntu/releasenotes/804overview)

---

### Post by TimTang on 2009-03-14
Arthur Archnix - I agree with you totally!! On Gutsy I had my system set up perfectly. Now with a new fangled computer everything better and faster and a fresh installation of Intrepid, after two weeks of pissing around with different settings and reading multiple help guides, I'm sitting in front of a blank screen with a wireless key board that won't work between post and the login screen. When I do get the log in screen (which I've since lost) the text is about 10 times to large for the user and password.

I tried to implement the same settings that I had in Gutsy into the xorg.config file but now it has no effect. I used to have it set for 1360x765 for my 1366x768 flat screen and it was perfect, even with the lost pixels. Now (at least when it was working; now i have a blank screen as a result of trying to fix the huge fonts) no matter what resolution I choose I end up with a black frame of un-used space.

This autodetect stuff is crap. Most manufacturers are putting erroneous spec's in their EDID. I read the output from mine and according to the spec's my screen is smaller than an A4 sheet of paper. So how does the xserver deal with crap spec's? How do we over ride it or at least manually set our own xorg.conf like we used to be able to?

Why were users not informed of this major change in xserver? I didn't know anything until I edited the xorg.config file.

There's a message to the effect "Some of the settings you could previously set in this file will no longer work", and they're right; they don't. Wouldn't that be the ideal place to notify the user with something to the effect "If you would like to manually customise your settings please refer to such-and-such document, or visit such-and-such web site". Instead there is nothing and I don't know how to fix it! Even with the ATI fglrx there are no resolutions available that match my screen which is 1366x768, the same as 90 percent of all the large flat screen on the market. Do the people designing the graphic cards NOT GET OUT MUCH. How can they not know the screen resolution of the billions of flat screen TV's that are sitting in living rooms all over the world!

This really sucks!!!!!

---

