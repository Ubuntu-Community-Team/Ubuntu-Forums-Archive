---
title: "~40 Compaq Armada PII PIII laptops recommendations"
date: 2008-09-10
forum: Hardware
---

### Post by lewdev on 2008-09-10
I've just been asked to resurrect about 40 old laptops that are Compaq Armada E700 & E500 with Pentium II and Pentium III processors and about 128MB RAM that were donated to my church.  I'm hoping to make them useful again to an average user for basic web browsing and general multimedia.

I've been doing a lot of research and testing and Xubuntu 8.04 wasn't installing.  I would let the installer run for about an hour until the screen goes black.  I've read a thread somewhere in this forum that 8.04 stopped the support for some old computers.

I've tried DSL which installed fine and works fast but they are not very easy to use.  gOS worked on the E500 but it's a little slow and it wouldn't install on the E500 because the Gnome Display manager failed.

I was wondering if I could get any recommendations on trying different Linux distributions or just try an older version of Xubuntu.  It would be appreciated.

---

### Post by snowpine on 2008-09-10
Hi Lewdev, first of all, kudos to you for taking on this project!

I think you'll find this recent thread full of good suggestions for older 128mb systems: [http://ubuntuforums.org/showthread.php?t=873112](http://ubuntuforums.org/showthread.php?t=873112)

Based on my observations of these forums, Puppy Linux gets consistently good reviews as the lightweight distro of choice for inexperienced Linux users. I think it would be a good choice for a basic web kiosk application. 

Good luck!

---

### Post by lewdev on 2008-09-10
Thanks for your quick response!  I kind of waited on posting because I didn't want to do a double post.  I guess I did, but thanks for making things a bit quicker.

I cut the suggestions down to WattOS, Puppy, and, Fluxbuntu.  I still need to look at what applications will be pre-installed and features they provide.  I'll post the results of my project for anybody that may have a similar issue.

---

### Post by snowpine on 2008-09-10
> **lewdev said:**
> Thanks for your quick response!  I kind of waited on posting because I didn't want to do a double post.  I guess I did, but thanks for making things a bit quicker.

I cut the suggestions down to WattOS, Puppy, and, Fluxbuntu.  I still need to look at what applications will be pre-installed and features they provide.  I'll post the results of my project for anybody that may have a similar issue.

You're welcome!

I have a lot of good things to say about Fluxbuntu (I used it as my main OS for a few months) but believe me when I say you don't want to administer it on 40 computers! It hasn't had any updates or bug fixes for almost a year, and there is no support or user community to speak of (apart from a few helpful people here on Ubuntuforums). I was willing to tolerate this on one computer as a learning experience, but with 40 computers, I would want as painless a process as possible.

I've not used WattOS, so I can't comment on it. 

I'm currently using a distro called Crunchbang that IMO falls somewhere between Puppy and Xubuntu 8.04 on the "light/heavy spectrum". I am not 100% sure if it will work on hardware from that vintage, but IMO it's worth checking out.

Another reason I suggested Puppy is that you have the option to run it as a Live CD. That could be a good thing if, for example, there are going to be kids using the computer unsupervised--it's impossible to trash a Live CD or download something questionable to the hard drive, like you can with a normal hard drive install! It also means that setting up a custom installation (with whatever applications, settings, wallpaper, etc.) is as easy as "remastering" a single CD and then burning 40 copies. Speed-wise, however, a regular hard drive install will generally be faster than a Live CD.

Are there any particular applications/features you need?

---

### Post by lewdev on 2008-09-10
> **snowpine said:**
> Are there any particular applications/features you need?

Ideally, I just want it to run like a normal desktop.  For example, when I stuck my USB drive in, DSL didn't automatically detect the USB and I couldn't figure out how to mount it.  I don't know if there were was a lack of driver support or just a few commands missing from my knowledge.  In the end, there was no way I was going to give out computers that require that kind of expertise.

gOS on the other hand, the drive showed up on the desktop and I was easily able to access it.  gOS includes what a full desktop needs, a web browser, Open Office, an audio player, and video player.  gOS seems to be ideal in terms of features but I don't think it was built for these weak PCs.

At the bare minimum, the computers could be just used for general web browsing but I know they have much more potential and I was hoping to find out my options.

It hasn't had any updates or bug fixes for almost a year, and there is no support or user community to speak of (apart from a few helpful people here on Ubuntuforums).

> **snowpine said:**
> It hasn't had any updates or bug fixes for almost a year, and there is no support or user community to speak of (apart from a few helpful people here on Ubuntuforums).


Another requirement was also support and I'm glad you pointed that out because I think that's important.

I am looking for a distro that I can hand to someone and have him/her easily pick it up with little to no instruction.  I have found that in using Xubuntu on my own computer.  It's just that Xubuntu wasn't working.

Is it possible that the Xubuntu installation froze up because of the memory load LiveCD requires?  I can't check at the moment, but is there an option to install Xubuntu without loading LiveCD GUI?

---

### Post by snowpine on 2008-09-10
> **lewdev said:**
> 
Is it possible that the Xubuntu installation froze up because of the memory load LiveCD requires?  I can't check at the moment, but is there an option to install Xubuntu without loading LiveCD GUI?

From Xubuntu.org:

> Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

Note that the 64mb install is not currently possible due to a bug in the installer; 128mb is the minimum to install with the Alternate CD (which uses a text-based installer).

Now, some people suggest using an older version of Xubuntu with lighter system requirements. I personally am new to Linux, so I have no experience with anything before 7.10.

---

### Post by nc_jed on 2008-09-10
It may also be worthwhile to fool the installer into installing onto the hard disk by using a 2.5" -> 3.5" IDE adapter.  Idea being, physically install the laptop drive in a desktop computer, run the alternate text-based installer, get everything all finalized on the install.  Remove the drive from the desktop, install to the laptop, let it boot up and go through the necessary updates (when it finds the difference in hardware).

Also worthwhile is considering a server install, and add on the window manager afterwards through apt-get.  Xubuntu 8.04 has far too much Gnome and KDE services installed by default.  It has (in my opinion) gotten away from the XFCE centric distro that it once was and is getting gunked up by all the Gnome/KDE cruft that comes along.  I think 7.04 was the last Xubuntu release that was pure XFCE.

You may also want to consider IceWM since it is light on resources and can be configured to look a lot like Windows ([http://themes.freshmeat.net/projects/icewmsilverxp/](http://themes.freshmeat.net/projects/icewmsilverxp/)).  I believe your audience will be first time Linux converts.  

- Jed

P.S.  Congrats on the project, I hope it gets off the ground.

---

### Post by mikjp on 2008-09-11
Don't try an old version of any distribution, you want an uptodate distro as they are more secure. See my recommendatios in my [blog posting about top 10 lightweight distributions](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html).

Greetings,

Mikko

---

### Post by darrelljon on 2008-09-11
Newer versions are more targeted for vulnerabilities. Have a look at [operating systems for old computers]("http://ubuntuforums.org/showthread.php?t=575456").

---

### Post by lewdev on 2008-09-11
Thanks for the link, Mikjp!  I saw it in the previously mentioned thread.  I'll check those out!

> **darrelljon said:**
> Newer versions are more targeted for vulnerabilities. Have a look at [operating systems for old computers]("http://ubuntuforums.org/showthread.php?t=575456").

Thank you for your extensive list! It's sincerely appreciated!  It's exactly what I was looking for!  Some distributions were just too low-featured, some were too big.  It's good to be able to look at the list to determine which distribution would suit the computer(s) at hand.

---

### Post by lewdev on 2008-09-12
Puppy Linux was great because it had a lot of features and it was fairly quick.  I was pretty convinced that Puppy Linux was everything I was looking for but it required the CD to boot.  I don't want to have to burn a copy for each and every laptop.  Installing was a bit of a hassle because of pupfs, which seems to be a profile stored in a file single file with a limit of 1.25GB per profile, thus I assume does not allow more space to be used beyond that.  I don't see why it couldn't be more straight forward.

I kind of like the idea of using the 2.5" -> 3.5" IDE adapter, but I think there are about 60-70 laptops now that I took another look at the pile and to remove the HD for each and every one of them will be very time consuming.  I'll be going back to school in about two weeks and I'm also hoping to let some church members take over the installation process.

Problems I ran into:  I was supposed to use MBR to store Grub so the computer just completely stop trying to boot from the CD drive and kept trying to boot the formatted and empty hard drive.  So I had to find an floppy (luckily had one) and an app to allow a boot from the CD drive.  Didn't work so I'm hoping to find another solution soon.

I booted up Slax and it looked very impressive.  It felt very friendly and stable.  I couldn't get to installing it to HD yet though.

Another mistake, I just assumed Puppy was the solution.  I should have tried a few distros before committing to one.

---

### Post by snowpine on 2008-09-12
> **lewdev said:**
> Puppy Linux was great because it had a lot of features and it was fairly quick.  I was pretty convinced that Puppy Linux was everything I was looking for but it required the CD to boot.  I don't want to have to burn a copy for each and every laptop.  Installing was a bit of a hassle because of pupfs, which seems to be a profile stored in a file single file with a limit of 1.25GB per profile, thus I assume does not allow more space to be used beyond that.  I don't see why it couldn't be more straight forward.

I kind of like the idea of using the 2.5" -> 3.5" IDE adapter, but I think there are about 60-70 laptops now that I took another look at the pile and to remove the HD for each and every one of them will be very time consuming.  I'll be going back to school in about two weeks and I'm also hoping to let some church members take over the installation process.

Problems I ran into:  I was supposed to use MBR to store Grub so the computer just completely stop trying to boot from the CD drive and kept trying to boot the formatted and empty hard drive.  So I had to find an floppy (luckily had one) and an app to allow a boot from the CD drive.  Didn't work so I'm hoping to find another solution soon.

I booted up Slax and it looked very impressive.  It felt very friendly and stable.  I couldn't get to installing it to HD yet though.

Another mistake, I just assumed Puppy was the solution.  I should have tried a few distros before committing to one.

Sorry if I led you astray with my recommendation. :( 
I was under the impression that Puppy could be installed to hard disk just like any other distro. I did not realize it only booted from the CD.

---

### Post by lewdev on 2008-09-12
> **snowpine said:**
> Sorry if I led you astray with my recommendation. :( 
I was under the impression that Puppy could be installed to hard disk just like any other distro. I did not realize it only booted from the CD.

Don't worry, I made that assumption too.  It does an install to the hard disk, it just needs to have the CD in there to boot up.  The CD can be removed once booted, or else, it goes to a black screen.  Maybe I was doing it wrong.  The other alternative is to boot from floppy disks using Wakepup, but I don't think I'll be able to find a bunch of floppies laying around somewhere.  It'll also force another step in the installation process.

I'd also like to mention that using Puppy was good because it ran well under LiveCD and I was able to use the Gparted GUI, which was very easy to use.

Anyway, Puppy installed fine on 4 laptops before I decided to try a different distribution.

---

### Post by darrelljon on 2008-09-13
Puppy does two types of install.
Full which installs to the hard disk and doesn't require the CD on subsequent reboots.
Frugal which does require the CD on subsequent reboots.

---

### Post by lewdev on 2008-09-13
Yes, I'm pretty sure I selected the FULL option and after setting up a pupfs, I did a restart without the CD and it goes to a black screen.  Only when I let it boot from the CD, it boots normally.  Maybe it didn't install properly... I don't know.

What I do know is that the installation wasn't very straight forward or simple as it should be.  Which makes another reason to look for another OS.

---

### Post by lewdev on 2008-09-22
I started with [Puppy Linux]("http://www.puppylinux.org/") and came back to it after trying out many other distros:

[Slax]("http://www.slax.org/")
I don't think there was an installer for this one.  I looked in the forums and it apparently stopped supporting hard disk installs.  Tried it out and it looked great.  It was smooth and sleek, but no install.  I liked how it had the look and feel of Windows which is what most people would find familiar.

[Fluxbuntu]("http://fluxbuntu.org/")
I really liked this because it came with a lot of great software and it has a system just like Ubuntu, just with a lighter window manager (Fluxbox).  I only preferred Puppy Linux over it because there was not only a start menu but the icons on the desktop were laid out.  Plus points for automatic partitioning (install was easy as a breeze).

[Zenwalk]("http://www.zenwalk.org/")
Crashed on install... next.

[TinyMe]("http://tinyme.mypclinuxos.com/")
This one almost looked as smooth as WinXP.  The LiveCD gave a great demo of a great look and feel, it just crashed on install.

[Vector Linux]("http://www.vectorlinux.com/")
Couldn't even get to a LiveCD menu.

[DSL-N]("http://www.damnsmalllinux.org/dsl-n/")
Works fine.  But the file manager was confusing.  I think any typical user would just avoid it or just not want the computer for mere difficulty of comprehending how to use it.

Puppy Linux, though unfortunately, requires manual partitioning, but was the best in usability.  The icons to the general applications were all laid out on the desktop by default.  Accessing a USB storage device wasn't automatic but the icon to have it mount was right on the desktop.

A noticeable fault is the fact that the installer does not install Grub properly, thus, I came across this article:

[http://ubuntuforums.org/showthread.php?t=880547](http://ubuntuforums.org/showthread.php?t=880547)

to have the issue resolve.  It requires just a few commands but I still need to do it to every computer.

So far, I have about a dozen laptops with Puppy Linux installed, I just haven't had anybody take them to use yet so I have not yet received a reaction.  Some people took other laptops to just install whatever they choose.

If anything, I think those laptops would be great for trying new things on the computer like installing server software or something.

Personally, I liked Fluxbuntu because it was easy to install and being an Ubuntu user, I felt comfortable with things like apt-get and sudo.

---

### Post by 00b00nt00 on 2008-10-14
I'm using a Compaq Armada E500 with 512MB RAM pinched from other computers, and Ubuntu 8.04. Why don't you cannibalise some of these old laptops, giving them extra RAM? If you have 40 with 128MB RAM,then you may be able to get 20 with 256MB RAM. More than enough to run Xubuntu (and even Ubuntu via the alternate CD).

---

### Post by lewdev on 2008-10-16
I wouldn't want to waste the laptops.  I think they will run decently with PuppyLinux and be useful for their general purposes, which is web-browsing, media-playing, and word processing.

btw, I tried using Fluxbuntu and configured it to a working condition.  Please do NOT use it.  It lacks so many features, it's not worth installing.  I had to put so much work into things it should have to begin with.

---

### Post by snowpine on 2008-10-16
Smart choice! :) As I said back in post #4, I can't even imagine trying to administer Fluxbuntu on 40 computers! I am curious if you can clarify one thing, though. You said Fluxbuntu "lacks so many features... it should have to begin with," but you said your main needs are web browsing (fluxbuntu has kazehakase), media playing (vlc), and word processing (openoffice word). Believe me I am not trying to talk you into giving Fluxbuntu a second chance; I just don't understand your statement.

---

### Post by lewdev on 2008-10-16
I was trying to install a lighter operating system for a friend and I wanted to give it to him so that he could pick it up and easily figure things out.  He's not very tech savvy, so I had to make sure he knew how to figure things out in the easiest way possible.

I wanted things like:
[LIST]
[*]Plug'n Play for USB thumb drives (remedy for this is 'sudo apt-get install ivman' and [a little bug fix]("http://releases.fluxbuntu.org/7.10/rc/HEADER.txt"))
[*]I click-open an mp3 file, OS doesn't know what program to use.
[*]I wanted to place icons on the desktop.  This was a huge pain because I still don't remember how I did it.
[*]Flux programs menu has no icons and I can see how it would be difficult to find out what each does.  I mean seriously, he wouldn't have any idea what Samba is.
[*]I was going back to college in a few days so it wasn't very fun having to look up on how to do everything.
[/LIST]

I loved the light-weight browser and VLC player; it just didn't have anything else that you might find important.  I don't recall what other things I had to find and install but all I do remember is that I didn't have a good experience.  In searching for missing applications, I found a review that pointed out all of its missing features but I can't seem to find it again.  I don't thing that I should have to find so many things to get it working.

---

### Post by snowpine on 2008-10-16
Thanks for sharing your experiences here for future readers of this thread. :) Here's what I know about the questions you raised (again, more directed at a hypothetical potential Fluxbuntu user browsing this thread than directly at you):

> Plug'n Play for USB thumb drives 

A known Fluxbuntu bug. Ivman is already installed, so 'mkdir ~/.ivman' is all you need to do.

> I click-open an mp3 file, OS doesn't know what program to use.

This is Fluxbuntu's default behavior for all file types. It lets you decide which application to use for each file type. Right click on the file and choose Set Run Action, then type the application you want to use as the default. I agree this is annoying but I see the logic. :)

> I wanted to place icons on the desktop.  This was a huge pain because I still don't remember how I did it.

Simply drag the document, folder, or application from Rox filer onto the desktop.

> Flux programs menu has no icons and I can see how it would be difficult to find out what each does.  

No idea on this one. I think you'd have to edit the menu file and manually add each icon. Maybe not, maybe there's an easy way to turn on the icons.

Good luck with Puppy!

---

