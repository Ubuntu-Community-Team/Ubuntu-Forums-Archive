---
title: "Nvidia vs. Wayland"
date: 2019-04-12
forum: Hardware
---

### Post by Shibblet on 2019-04-12
I have been trying to get Ubuntu to recognize Nvidia proprietary drivers for the past week.  Doing web-search after web-search.  Finally, I find out that Wayland is the problem.

I know that proprietary drivers do not ship with Ubuntu... But why is there no automation process when a user chooses to use the proprietary drivers?  I mean, why isn't there an option for Ubuntu to disable Wayland, revert to Xorg, blacklist the Nouveau driver, and install the proprietary Nvidia drivers?  Why do we have to jump through all of those hoops?

---

### Post by #&amp;thj^% on 2019-04-12
Well if you think about that question, 2 different graphic servers. :p
Wayland is obviously a chance to change a lot of the low level stuff going on with Linux graphics. The wayland teams, Intel, AMD etc... everyone besides NVIDIA basically, decided to pursue a buffer API called GBM. NVIDIA flat refused to use GBM and pushed their own EGLStreams technology instead. Back in the Wayland camp that too was met with flat refusal.

So basically the main issue is getting everyone to agree on what they're doing, which is probably gunna end up involving something that's part way between the two technologies. Exactly why NVIDIA are refusing to budge I have no idea, **maybe they have good reason maybe not.** At a complete guess its probably so NVIDIA can keep more of the same code for all their drivers cross platform, no idea if that's true or not just a guess.

**NOTE: I will not reply to the below comment, and please don't ask.**
There are some experimental unofficial patches to get Wayland to work with NVIDIA by providing this EGLStream support, I've seen GNOME running on NVIDIA anyway. However no distro or upstream Wayland developers want to enable this fragmentation by doing anything but ignoring these patches. They want one clean standard based on GBM. There are articles from Wayland developers about why they don't like EGLStreams and won't just standardize on that, I don't really understand the technicalities though I'll just take it for granted they know their stuff.

---

### Post by Shibblet on 2019-04-12
> **1fallen said:**
> Well if you think about that question, 2 different graphic servers. :p
Wayland is obviously a chance to change a lot of the low level stuff going on with Linux graphics. The wayland teams, Intel, AMD etc... everyone besides NVIDIA basically, decided to pursue a buffer API called GBM. NVIDIA flat refused to use GBM and pushed their own EGLStreams technology instead. Back in the Wayland camp that too was met with flat refusal.

So basically the main issue is getting everyone to agree on what they're doing, which is probably gunna end up involving something that's part way between the two technologies. Exactly why NVIDIA are refusing to budge I have no idea, **maybe they have good reason maybe not.** At a complete guess its probably so NVIDIA can keep more of the same code for all their drivers cross platform, no idea if that's true or not just a guess.

I have read this somewhere before.  And I think this is why I came here to ask this question.

What I am asking is more along these lines.  Let's take Kubuntu for example.  Currently does not use Wayland.  It is still Xorg.  However, when you install the Nvidia proprietary drivers, you still have to go through and blacklist Nouveau, as well as download the driver and install them. 

Why doesn't the driver install process blacklist Nouveau automatically?  Seems perfectly reasonable that anyone installing the proprietary driver is going to use it, and not Nouveau, right?  Why make this a multi-step process?

Now, I've been an Ubuntu user since 8.04 Hardy Heron.  But new users coming to Ubuntu from Windows have an issue with this.

---

### Post by #&amp;thj^% on 2019-04-12
You probably seen it on reddit or on blackarch sites.
A graphic server (Xorg or Wayland) is only started on a new session start or boot. (That should be sufficient)
I've never had to blacklist Nouveau.
To sum it up most new users coming from windows are going to think that Linux is not very intuitive. (I can remember myself 15 years ago thinking what the heck did I just do to myself)LOL

---

### Post by QIII on 2019-04-12
Kubuntu isn't using Wayland ... yet.

The KDE developers are working with the Wayland developers.  In fact, there is a bug with Kubuntu 18.04 that KDE says they are not going to fix because it is an X Server problem and they are trying moving to make KDE compatible with Wayland.  Try using autohide on your panels using X Server and watch what happens when you have windows open in less that full screen or even close them.  The panels flicker on and off.  They say it's so screen edge stuff will work with Wayland and X Server can't be made to work, so it's a "won't fix".  To which, of course, I replied with a scatological reference and said that I already had a proof of concept script to make the panels stay hidden without the flicker.

I've brought this up to the KDE developers and have been greeted the same snarky "we know what you need" attitude of the Wayland developers.  Sharp words were exchanged.

A shame.  I may have to move away from Kubuntu.

So, anyway, don't count on Kubuntu not using Wayland in the future.

---

### Post by monkeybrain20122 on 2019-04-12
> **Shibblet said:**
> 
What I am asking is more along these lines.  Let's take Kubuntu for example.  Currently does not use Wayland.  It is still Xorg.  However, when you install the Nvidia proprietary drivers, you still have to go through and blacklist Nouveau, as well as download the driver and install them. 

Why doesn't the driver install process blacklist Nouveau automatically?  Seems perfectly reasonable that anyone installing the proprietary driver is going to use it, and not Nouveau, right?  Why make this a multi-step process?

Now, I've been an Ubuntu user since 8.04 Hardy Heron.  But new users coming to Ubuntu from Windows have an issue with this.

I have no idea about Kubuntu, but I never have to "blacklist nouveau" on Ubuntu if I install the driver as a .deb (I have used Nvidia driver with Ubuntu on and off since Ubuntu 10.10, I stayed away from Nvidia for a few years because of Optimus, and lack of $$ :) ) I have just recently installed Ubuntu 16.04 and 18.04 on a few machines with Nvidia card. Never once did I "blacklist nouveau".  That step is necessary only if you install the nvidia driver as a .run file.

---

### Post by rbmorse on 2019-04-13
> **Shibblet said:**
> I have been trying to get Ubuntu to recognize Nvidia proprietary drivers for the past week.  Doing web-search after web-search.  Finally, I find out that Wayland is the problem.

I know that proprietary drivers do not ship with Ubuntu... But why is there no automation process when a user chooses to use the proprietary drivers?  I mean, why isn't there an option for Ubuntu to disable Wayland, revert to Xorg, blacklist the Nouveau driver, and install the proprietary Nvidia drivers?  Why do we have to jump through all of those hoops?

Wayland still has a lot of problems.  I personally think it's not quite ready for primetime, yet. 

To use Ubuntu on xorg, click on the little gear icon next to the dialog box where you enter your password during log-in. One of the options will be "Ubuntu on Xorg".  This is a "sticky" option, Ubuntu will continue to use xorg on subsequent boots until changed. 

As far as installing the proprietary Nvidia driver into Ubuntu, Have you tried the "software and updates" utility?  Click on the "additional drivers" tab.

---

### Post by Shibblet on 2019-04-15
> **rbmorse said:**
> Wayland still has a lot of problems.  I personally think it's not quite ready for primetime, yet. 

To use Ubuntu on xorg, click on the little gear icon next to the dialog box where you enter your password during log-in. One of the options will be "Ubuntu on Xorg".  This is a "sticky" option, Ubuntu will continue to use xorg on subsequent boots until changed. 

As far as installing the proprietary Nvidia driver into Ubuntu, Have you tried the "software and updates" utility?  Click on the "additional drivers" tab.

I always have a partition set aside on my HD for "test running" other distributions.  And since Kubuntu is my main distro, I decided to install Ubuntu in my open partition to see how it functions. 

First thing I did was open up /etc/gdm3/custom.conf and took the "#" (REMARK) out from in front of WaylandEnable=false.  This essentially disables Wayland.  After this, I installed my Nvidia drivers (390).  Ubuntu is creamy buttery smooth, and my game performance is on par with Windows.  Tomb Raider came in around 90fps (GTX780ti and i7-3770)

---

### Post by rbmorse on 2019-04-15
I noticed an article on Phoronix today reporting that Nvidia has made support for EGL_streams available for kwin, the compositor used by KDE.  Perhaps support for other desktops is coming. 

[https://www.phoronix.com/forums/forum/phoronix/latest-phoronix-articles/1092841-nvidia-eglstreams-support-merged-into-kwin-for-kde-plasma-5-16](https://www.phoronix.com/forums/forum/phoronix/latest-phoronix-articles/1092841-nvidia-eglstreams-support-merged-into-kwin-for-kde-plasma-5-16)

---

### Post by mastablasta on 2019-04-17
> **QIII said:**
> 
I've brought this up to the KDE developers and have been greeted the same snarky "we know what you need" attitude of the Wayland developers.  Sharp words were exchanged.


that's because users don't know what is right and good for them. :P

if you offer an app or OS to enthusiast, first users... only few might complain. when you offer it to the public things are quite different. as Microsoft is finding out these days after they decided to use what was basically a beta version on home users. 

a few testers told them there was a problem with the update. but they ignored it. after all it was only a few of such reports, they don't matter right? wrong, when users got their hands the news spread, it created bad brand image for the OS, it created doubt in users who used to use windows for a long time... even after they fixed the issue people are no longer sure if they should update or not. after all that October update erased files for plenty of users and it didn't even roll out to that many. 

overall i think they should often look more into the context of the bug rather than think, ah it's only a few users complaining others seems fine with this.

how after 3 years this is the only solution still blows my mind:
> 
**14.04 LTS to 16.04 LTS upgrade**

[COLOR=#333333][FONT=&amp]**WARNING**: LTS to LTS upgrade to Xerus is currently problematic and should not be attempted. Please install a fresh copy of 16.04 instead. To prevent messages about upgrading, change Prompt=lts to Prompt=normal or Prompt=never in the /etc/update-manager/release-upgrades file.[/FONT][/COLOR]


Currently?

---

### Post by Shibblet on 2019-04-17
> **mastablasta said:**
> that's because users don't know what is right and good for them. :P

if you offer an app or OS to enthusiast, first users... only few might complain. when you offer it to the public things are quite different. as Microsoft is finding out these days after they decided to use what was basically a beta version on home users.

You forgot the age old adage "That's not how we used to do it." :P

> **mastablasta said:**
> a few testers told them there was a problem with the update. but they ignored it. after all it was only a few of such reports, they don't matter right? wrong, when users got their hands the news spread, it created bad brand image for the OS, it created doubt in users who used to use windows for a long time... even after they fixed the issue people are no longer sure if they should update or not. after all that October update erased files for plenty of users and it didn't even roll out to that many. 

overall i think they should often look more into the context of the bug rather than think, ah it's only a few users complaining others seems fine with this.

how after 3 years this is the only solution still blows my mind:


Currently?

One of the most difficult things for them to do, is to figure out how many things can be fixed before the deadline.  It turns into a process of triage.  Can we fix this?  Is it necessary?  Do we have time to fix this?  Is it necessary?

Ubuntu has a roll out of every 6 months, and the deadline has been met every month, almost without fail, as far back as I can remember (8.04 Hardy)

I have wondered why Ubuntu doesn't become a rolling release, or at least start a rolling release distribution of Ubuntu.

---

### Post by kryten35 on 2019-04-24
The ubuntu disks 19.04  now have the option to install the propriety  nvidia graphics driver during the install.
The blacklisting of the open source drivers and switching to xorg etc is done automatically.

Theres also an option to install ubuntu -safe graphics if the ubuntu disk boots to a black screen and you dont want or know how to mess about with nomodeset.

The open source nvidia drivers currently dont work with xorg.only work with wayland.Noticed that with debian buster as well.

---

### Post by Shibblet on 2019-04-25
> **kryten35 said:**
> The ubuntu disks 19.04  now have the option to install the propriety  nvidia graphics driver during the install.
The blacklisting of the open source drivers and switching to xorg etc is done automatically.

It's a beautiful thing, isn't it?

Although, in order to get my personal settings to load by default, I have to manually create my xorg.conf file.

What I do, is make all of my settings in the nvidia-settings program, then instead of saving the file right from nvidia-settings, (because it won't let you, even as super-user) I copy the settings into a text file, and then save it as /etc/X11/xorg.conf

Next time I reboot, they are enabled by default.

> **kryten35 said:**
> Theres also an option to install ubuntu -safe graphics if the ubuntu disk boots to a black screen and you dont want or know how to mess about with nomodeset.

The open source nvidia drivers currently dont work with xorg.only work with wayland.Noticed that with debian buster as well.

Yes!  You know, the nouveau driver is pretty darn good.  If I didn't play games, and had an Nvidia card in my PC, I'd just stick with Nouveau.  I mean, community added wayland support, before Nvidia did?  That's pretty awesome.

I am tired of hearing people say how "bad" the nouveau driver is.  I wish people would look at this driver for what it is, instead of what they think it should be.  This driver was built from the ground up by the Nvidia/Linux community, and has worked amazingly for many years.  The only thing it is lacking, is game support.  And that's because Nvidia is a bit stingy with their technology when it comes to driver optimization.  

Pssst... (Consipriacy Theory) I heard that Nvidia's drivers are written by an A.I., that's why they can't share them.

---

