---
title: "Laggy Remix?"
date: 2009-12-27
forum: Hardware
---

### Post by ZombiesNTea on 2009-12-27
Hi!

I have an Acer Aspire One with an intel Atom processor and a gig of ram.  I got it as a gift a while back loaded with Windows Vista, and have been wanting to switch to the Ubuntu Netbook Remix (I've been using Ubuntu on my desktop since last winter).  I've been too afraid that I might regret it, due to discovering any problems.

I am currently running Netbook Remix (Karmic Koala) off of my flash drive.  My biggest resisteance to switching over is, running it off of my flash drive, it is laggy... moreso than Vista.  And scrolling down webpages is really choppy.  Is this due to the fact that I am running this off of a flash drive, rather than the hard drive?

Also, as a side note, nearly every word I type in this entry is underlined in red, as if I am spelling words like "also" wrong.

Any insight into this, and is it the fact that I'm running the OS off of my flash stick?

Thanks in advance!

---

### Post by marshmallow1304 on 2009-12-27
> **ZombiesNTea said:**
> My biggest resisteance to switching over is, running it off of my flash drive, it is laggy... moreso than Vista.  And scrolling down webpages is really choppy.  Is this due to the fact that I am running this off of a flash drive, rather than the hard drive?

Probably.

> **ZombiesNTea said:**
> Also, as a side note, nearly every word I type in this entry is underlined in red, as if I am spelling words like "also" wrong.

Right-click in a text field and see if the spell checker language is set correctly.

---

### Post by ZombiesNTea on 2009-12-28
> **marshmallow1304 said:**
> Probably.



Right-click in a text field and see if the spell checker language is set correctly.
Thanks for the reply!

I did what you said, the misspelling problem is fixed :-)

So you think I should go ahead and put the remix on here?  I'm just being *really* cautious about putting it on here, I want to ensure that I don't regret it.

---

### Post by marshmallow1304 on 2009-12-28
How big is the hard drive?  You can dual-boot both Ubuntu and Windows so if it for some reason doesn't work, you can go back to Vista with no problem.

---

### Post by ZombiesNTea on 2009-12-28
> **marshmallow1304 said:**
> How big is the hard drive?  You can dual-boot both Ubuntu and Windows so if it for some reason doesn't work, you can go back to Vista with no problem.

My C drive is 222GB.  I'll try doing a dual-boot.  Thanks for all the help!

---

### Post by ZombiesNTea on 2009-12-28
I did the dual boot... here on the Ubuntu partition, it's still laggy when I scroll up and down webpages and is still moderately laggy on the home screen. 

Considering the specs (Intel atom proc, 1gb ram, I believe 50 or so gb hard drive dedicated to this partition) I don't understand why those would be problems.

---

### Post by ZombiesNTea on 2009-12-28
> **ZombiesNTea said:**
> I did the dual boot... here on the Ubuntu partition, it's still laggy when I scroll up and down webpages and is still moderately laggy on the home screen. 

Considering the specs (Intel atom proc, 1gb ram, I believe 50 or so gb hard drive dedicated to this partition) I don't understand why those would be problems.

Nix that, I believe it's actually 2gb ram.

---

### Post by ZombiesNTea on 2009-12-28
I've read that it may be that I need a patch for the kernel... could this be the case in karmic, and if so, how do I (a newbie) install it?

---

### Post by ZombiesNTea on 2009-12-28
?

---

### Post by ZombiesNTea on 2009-12-29
Also, my Intel Atom is 1.33ghz... so I really can't see my hardware being the problem.

Any help on this will be greatly appreciated!

---

### Post by jlewisfl on 2009-12-29
If you check screen resolution, you will probably find it set to 1024x768 and you can't change it.  If you have the same netbook I do (I have two AO751H-1279,  one for me, one for wife, 2GB RAM, 250GB HD), the built-in video card doesn't end up with the correct driver installed, instead it installs a VESA (generic) driver, so instead of 1366x768, we get 1024x768, and slow video, since none of the video hardware acceleration or 3D works with that driver. At least, that's what I gather from the discussions.  

There are some patches for the Kernel, and some other stuff necessary, which I have not yet done (had some issues with both audio and networking, partly because I also installed KDE) so I am still having slow video.  There is at least one thing you can do immediately.  Turn off the video effects, like fading when going from an app to the main menu (I dislike the remix gnome desktop/menu combo).  Turning off those effects speeds things up a lot, especially since with the VESA driver video speed is handicapped to start with.  

KDE seems to me to run much faster than the remix version of Gnome, because it doesn't do those video fading effects, and it doesn't load a whole new screen, with fade effects,  like Gnome does when you ask for the main menu, and just seems much more responsive as a result.  But expect problems in installing KDE AND Gnome both.  I am on my fourth re-install. Apparently if you don't install things in the right order, or you are a teensy bit inattentive (or tired and bleary-eyed at 2 a.m.) and allow Synaptic to install something for KDE that requires removing something, or several somethings, from Gnome, it can break networking, or something else, requiring another fresh re-install from the USB stick...

Even with the video problems, it still seems faster than Vista, though.  I have all my desktop machines dual-booted and they spend almost all the time running on the linux side.  Laptops and Netbooks are apparently  a real challenge to write drivers for, because they are all somewhat unique and a driver for the same device on two different laptops may require two different drivers.  And every week there are new laptop models on the market, requiring different drivers.

I also have not figured out exactly where to find (and fix) basic X system configuration files, or an Xorg "emergency fix-it" app that works from the command line to let you modify an X configuration that refuses to load, and I know Mandrake/Conectiva/Mandriva had that capability, which was a lifesaver when you changed a driver setting, restarted, and found out it broke X.  IF SOMEBODY READS THIS AND CAN POINT ME TO THOSE THINGS, IN UBUNTU,    P L E A S E   POST THAT INFO - THANKS!!

---

### Post by ZombiesNTea on 2009-12-29
> **jlewisfl said:**
> If you check screen resolution, you will probably find it set to 1024x768 and you can't change it.  If you have the same netbook I do (I have two AO751H-1279,  one for me, one for wife, 2GB RAM, 250GB HD), the built-in video card doesn't end up with the correct driver installed, instead it installs a VESA (generic) driver, so instead of 1366x768, we get 1024x768, and slow video, since none of the video hardware acceleration or 3D works with that driver. At least, that's what I gather from the discussions.  

There are some patches for the Kernel, and some other stuff necessary, which I have not yet done (had some issues with both audio and networking, partly because I also installed KDE) so I am still having slow video.  There is at least one thing you can do immediately.  Turn off the video effects, like fading when going from an app to the main menu (I dislike the remix gnome desktop/menu combo).  Turning off those effects speeds things up a lot, especially since with the VESA driver video speed is handicapped to start with.  

KDE seems to me to run much faster than the remix version of Gnome, because it doesn't do those video fading effects, and it doesn't load a whole new screen, with fade effects,  like Gnome does when you ask for the main menu, and just seems much more responsive as a result.  But expect problems in installing KDE AND Gnome both.  I am on my fourth re-install. Apparently if you don't install things in the right order, or you are a teensy bit inattentive (or tired and bleary-eyed at 2 a.m.) and allow Synaptic to install something for KDE that requires removing something, or several somethings, from Gnome, it can break networking, or something else, requiring another fresh re-install from the USB stick...

Even with the video problems, it still seems faster than Vista, though.  I have all my desktop machines dual-booted and they spend almost all the time running on the linux side.  Laptops and Netbooks are apparently  a real challenge to write drivers for, because they are all somewhat unique and a driver for the same device on two different laptops may require two different drivers.  And every week there are new laptop models on the market, requiring different drivers.

I also have not figured out exactly where to find (and fix) basic X system configuration files, or an Xorg "emergency fix-it" app that works from the command line to let you modify an X configuration that refuses to load, and I know Mandrake/Conectiva/Mandriva had that capability, which was a lifesaver when you changed a driver setting, restarted, and found out it broke X.  IF SOMEBODY READS THIS AND CAN POINT ME TO THOSE THINGS, IN UBUNTU,    P L E A S E   POST THAT INFO - THANKS!!

You were correct on the screen resolution... only option I have.  I'm not sure what model of the Aspire One I actually have... how would I find that out?

What do you mean by KDE?  Are you referring to Xubuntu?  I'm still pretty uneducated on Linux.  If that has a netbook remix much like Ubuntu, I'd be willing to replace Ubuntu on this partition with a Xubuntu (or Kubuntu) netbook remix.

My biggest issue (video is choppy and slow, but I don't use this laptop much for video) is the fact that the home screen is so slow.  I'm getting to a point where soon I'm just going to say "screw it," and remove this partition, and just use Vista (as much as I loathe Vista).  I think the netbook remix is pretty awesome, and would love to use it if I could get it to work reasonably.  I was thinking of trying just regular Ubuntu on here, but I really just don't know if I want to deal with *that* having some kind of problems as well.

---

### Post by jlewisfl on 2009-12-29
First, some background. As I understand it, there are a number of  "window managers" or "display managers" .  The two main ones are KDE and Gnome.  The remix uses Gnome.  Each has a complete (and different!)  set of code libraries, and applications that use those library sets.   And unfortunately, some applications require a different version, or edition, of particular libraries, and sometimes in order to install one application, the system may require you to remove other (sometimes MANY other) mutually incompatible applications, usually because of conflicts between different libraries or different library versions, in which case you may need to hit Cancel and NOT install that application. Worst case, if you tell it to go ahead and install it, you can break things to the point where you have to do a complete reinstall and start again from scratch.

Since the video driver (at the moment) that SHOULD be installed isn't, that means that when you change from a running application to the main (full desktop) menu, that requires a complete "repaint" of the entire screen, or, if you are scrolling down through that main menu, MANY repaints of the entire screen, which, as you watch it, is slow and painful.   

I know a lot of people must have thought long and hard when it came to deciding what to include in the Remix, keeping in mind that the netbooks you and I have, with 250GB of hard disk and 2GB of RAM and a 11.6" screen, at 1366x768 are way on the high end of "Netbooks", AND that a, or the, primary target for this Remix is the linux newbie, people for whom "computer" = "Windows", and the Remix, I expect, has "evangelism" for linux as a primary purpose.  Those of us who have been using linux for years really shouldn't expect the Remix to be fully satisfactory.  Ubuntu probably put "bulletproof" (i.e., userproof) near the top of the list of characteristics for the Remix.  And they came close.  The laptop/netbook market is a huge challenge to write code for since there are so incredibly many hardware permutations, and each model is a unique combination of specialzed hardware. The driver for the exact same device, on two different laptop/netbook models, may not work on both of them.  While it is aggravating to not have everything working, I have nothing but admiration and respect for all those folks trying to get everything right in a very difficult job.

Now, Good news; :)  After several tries I have finally gotten the right video driver working, I have networking working right, and I have sound working right, all at the same time, and with both KDE and Gnome desktops and their library sets and applications installed and working.  But it took an inordinate amount of time and probably six re-installs from the USB stick.  And in some cases I'm not even sure what change fixed what problem.  But keep trying, keep reading these forums, and use the Search function to seek out the answers.  This is a great Community.

I am particularly happy with how KDE works on my AO751H.  Compared to the Gnome-based Remix, it seems (especially with the correct video driver installed and working)  tremendously faster.  Since I have both KDE and Gnome installed, I can, even running the KDE-based display manager, run Gnome-based applications. 

Since you are relatively new to linux,  I think I would suggest small steps, probably just see if you can get the correct video, audio and network drivers working (simultaneously) with your current Gnome-based Remix.   Just be careful, pay attention to all the details, and have fun.  Persevere.

Using an aftermarket 9-cell Li-Ion battery, I'm getting  > 7  hours of use per battery charge.  This is a NICE little box.

Here are some places to check for help:
[http://ubuntuforums.org/showthread.php?p=7680966](http://ubuntuforums.org/showthread.php?p=7680966)
[https://help.ubuntu.com/community/AA1](https://help.ubuntu.com/community/AA1)

Sorry this was so long :(

---

