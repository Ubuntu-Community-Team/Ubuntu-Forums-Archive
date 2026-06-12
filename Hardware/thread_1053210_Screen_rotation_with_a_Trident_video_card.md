---
title: "Screen rotation with a Trident video card"
date: 2009-01-28
forum: Hardware
---

### Post by gorcq on 2009-01-28
I have a Toshiba tablet PC running both Ubuntu 7.10 and Windows, and I would like to rotate the screen when I fold it down to use the stylus. But xrandr doesn't work.
```

$ xrandr -o 1
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```
My best guess is that this means that "1" is an unsupported orientation. But I don't know why this should be. When I boot with Windows I am able to rotate the screen any way I want, so I know that my Trident Cyberblade video card is capable of doing this, as is the monitor; therefore, it can't be a hardware issue. In Ubuntu, I use a Linux video card driver released by Trident; I have tried several other video card drivers, and they all cause XOrg to fail. In any case, it should be compatible with the video card.

I am left with the conclusion that there is something wrong with either RandR or some setting in Ubuntu, or both; but this is all I can tell. Any help would be appreciated.

---

### Post by gorcq on 2009-01-29
Anyone?

---

### Post by Favux on 2009-01-29
Hi gorcq,

The problem is that even if the videocard supports rotation, the video driver may not.  For instance with the ATI video chipsets the proprietary "fglrx" driver doesn't support rotation (that may have changed with the new version released the last couple days) while the Xorg driver "radeon" supports rotation.

Then if the chipset and driver supports rotation you still may have to modify the xorg.conf to get it.  For instance nVidia (and maybe Intel) require the line:
```
	Option		"RandRRotation"  "on"
```
to get rotation.  It's placed in the:
```
Section "Device"
	Identifier	"Configured Video Device"
```
xorg.conf section.  I think other cards may require a different but similar RandR option.

So what you're asking turns out to require some in depth knowledge.  Which Toshiba tablet pc do you have?  Maybe knowing that could give us a handle to figure things out.

---

### Post by gorcq on 2009-01-30
Sorry, it's a Toshiba Portege 3500. The video card is a Trident CyberBlade XPAi1.

Hmm... I don't seem to have the xorg.conf section you mention. In the section for my video card, it said Option "RandRRotation" "true", so I changed it to what you said with no effect. I've attached a copy of my xorg.conf in case it proves elucidating.

---

### Post by Favux on 2009-01-30
Hi gorcq,

You had it in the right section, and as far as I can tell "true" and "on" are equivalent, so leave it "true".

The video part of your xorg.conf, based on what little I know, looks OK.  You do have a "cursor" section, which is only for external graphics tablets so I commented it out, also in "ServerLayout".  In addition I commented out the "DeviceName" Options, because I don't think you need them (not quite sure about that in Gutsy), besides which the one in the "eraser" section says "cursor".  The changes are in the attached xorg.conf.

Now I think we know rotation is possible because didn't Lycoris preinstall their version of linux in the Toshiba Protege 3500 back when it first came out?  Surely rotation would have been a feature?  But did they do it with some sort of proprietary patch?  There is at least one other 3500 user, littlematt, trying to get rotation.  I don't know if he has succeeded or not.

I doubt any of the xorg.conf changes I made will give rotation.  It looks like a little more research is needed.  Is your current video driver the Xorg version?  Is there another?  I don't think Trident is still releasing video cards or drivers.  Are they still in business?  Did Lycoris ever release how they were getting rotation with their Lycoris Desktop/LX Tablet edition?

I hope this is of some use.

Oh right.  You have Compiz turned on, correct?  Try turning it off and then seeing if you get rotation.

---

### Post by Favux on 2009-01-31
Hi gorcq,

I looked into it a little more.  Please see the following bug reports:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/162312]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/162312")
[https://bugzilla.redhat.com/show_bug.cgi?id=379221]("https://bugzilla.redhat.com/show_bug.cgi?id=379221")

It's unclear to me if this is a result of the change in Xserver conflicting with the driver or the driver not being updated.  Or an update to the driver that broke rotation.  It may be that you're just running into the limitations of the video chipset, which was panned at introduction.  Please see the following review:
> But game players beware: The machine is hobbled by a Trident CyberBlade XP video chipset that is literally barely able to redraw the screen when rotated in tablet mode, much less play anything that requires 3D rendering. Also, Direct-X only functions correctly in laptop mode. Any screen rotation will slow game play so badly as to be unusable. This laptop would be vastly improved by a more capable display processor.
[http://www.gadgetspage.com/laptops/toshiba-portege-3500-3505-tablet-pc-review.html]("http://www.gadgetspage.com/laptops/toshiba-portege-3500-3505-tablet-pc-review.html")

I'm not saying it's impossible.  But I feel sure you want to decrease any possible video overhead, like turning off Compiz, etc.  As I recall littlematt had a second monitor set up in his xorg.conf.  I don't think many video cards can support rotation and a second monitor.  So that may have been a problem.

Maybe even considering going to Xubuntu???

---

### Post by gorcq on 2009-01-31
Favux,

I put in your edited xorg.conf and restarted Xorg to no effect.

As for Compiz, I've never heard of it before and as far as I can tell, it is not running. It does not show up in the System Monitor's processes list, and when I type "compiz --version" at a terminal, I get the message "No whitelisted driver found," followed by information about Metacity.

I'm aware that my video card isn't top of the line, but as I only use it for my school-work, this has never bothered me too much. As far as I know, the most video-intensive thing I have running is Xorg, and I have turned off visual effects in the appearance preferences dialog and generally done my best to lower the strain on the card. I think Windows is somewhat more graphics-intensive, because there are certain things that I can't turn off under that operating system -- one of the reasons I'm starting to like Ubuntu better.

My trident driver is called "xserver-xorg-video-trident" in the repository, so I assume that it is designed for xorg, and it is the most recent version. The man file attributes the authorship to "Alan Hourihane, EXA for Blade chips by Jesse Barnes," which may mean that it is not, in fact, connected with Trident, contrary to what I had thought. A quick google search reveals a large number of trident drivers, or probably different versions of the same one, connected with these two names; and no others. It seems like a waste of time, not to mention potentially dangerous, to switch out my existing driver for what is likely an older version, so I didn't test any of them.

As for switching to Xubuntu: First, why might that be better? And second, only as a last resort. I almost destryed all my files installing Ubuntu; of course, I'm quite sure I won't make the same idiotic mistake if I add another operating system, but at the moment, it seems like rather a big job.

---

### Post by Favux on 2009-01-31
Hi gorcq,

Good, the edited xorg.conf worked.  So some unnecessary entries have been removed.  So if you want you can now delete the commented out "cursor" stuff and the "devicename" entries.

Compiz is the video add-on that allows special 3-d visual effects and eye candy.  The base compositing window manager for gnome/Ubuntu is Metacity.  Compiz is kind of a super Metacity.  The quick way to tell is if you go to System>Preferences>Appearance>the Visual Effects tab you'll see three choices.  If not one of the three are checked then you're on Compiz, if one is checked, then it's Metacity.  What I was saying, in a round-a-bout way, is you want to have "normal" or even better "none" checked.  That way you're using Metacity, and with "none" checked, you're using the least video resources you can in Ubuntu.

In the xorg.conf you have "glx".  See:
[http://en.wikipedia.org/wiki/GLX]("http://en.wikipedia.org/wiki/GLX")

Xubuntu uses XFCE desktop, it's for lowspec. computers.  The windowing system is less resource heavy, it's a lower video resource requiring X windowing system.  See:
[http://www.xubuntu.org/]("http://www.xubuntu.org/")

I'm just tossing out ideas.  All I'm saying is that it would be good to reduce video demands until you get rotation.  It removes other destracting complications.  Once you have rotation you can start adding back eye candy.  I'm not saying you have to switch to Xubuntu, I'm just trying to point out that with linux you have choices.

Knowing that your current driver is "xserver-xorg-video-trident" is a great start.  Especially if you know the version number.  Why?  Because we know rotation was supported at some point.  If the problem is that an updated X server broke rotation for your driver then you won't get rotation in Ubuntu.  But you might in Xubuntu since it isn't as heavy on X.  Or maybe there is a driver that was updated to work with the new X server.  Follow?

My speculation is your problem with rotation is a video resources/video driver problem.  So each time you reduce the demand on video resources try rotating.  After all the poster towards the bottom on the first bug report said he got something to happen.  I'm just not sure he meant rotation.

---

### Post by gorcq on 2009-02-01
Hmm. I see why Xubuntu might be better for my purposes. Suppose I installed it as a third operating system and found that I liked it. Is there a simple way, at that point, to un-install Ubuntu without destroying my files? I ask, because my hard drive isn't so big that I'd want to permanently partition it into three pieces.

---

### Post by Favux on 2009-02-01
Hi gorcq,

Let's summarize.

Your stylus, eraser, and two stylus buttons work fine.  We've found and cleaned up some unnecessary entries in your xorg.conf.  Using Metacity with Visual Effects checked to "none" entering in a terminal:
```
xrandr -o left
```
or
```
xrandr -o right
```
does not give you rotation.  Even with:
```
	Option		"RandRRotation" "true"
```
in your xorg.conf.  Why don't you try commenting "RandRRotation" out "#" in your xorg.conf and try rotating again.  Just for completeness sake.

We have a bug report from 11/07 reporting rotation broken.  The original poster seems to feel it's Xorg's version of X that is responsible.  This seems possible, ie an update of Xserver broke the driver.  Or to put it another way, the driver wasn't updated to work with the new version of X.

Reading it several times Timo Aaltonen who was assigned the bug is telling us it is the driver.  It was not updated.  He says it is not a Xorg bug.

I speculated that a lower resource demanding windows manager might allow the driver to function on the current version of X.  This may be possible, but perhaps unlikely.

It seems the best way to proceed is to find out if Xorg has updated, or plans to update the driver for your video chipset.  You could make an entry into the bug report.  You could contact the Xorg driver folks directly, or through their message board/forum.

This way you may save a lot of research.  The Xorg developer responsible for the Trident drives may not know rotation is broken.  Of course there's always the possibility that someone has "patched" the driver and has rotation working.

And in the meanwhile, let's hope someone who knows the answer posts on your thread.

PS:  There's a great backup thread in the Tutorials & Tips forum.  Lot's of people prefer /home on a separate partition so that they can have multiple different linux OS's installed.  There are HOW TO's on that too, plus on how to migrate your /home to a separate partition.  Of course there are many opinions on what's the best way to do each one of these!
PPS:  If you do get rotation working, some rotation scripts are available at:
[http://ubuntuforums.org/showthread.php?p=6274392#post6274392]("http://ubuntuforums.org/showthread.php?p=6274392#post6274392")

---

### Post by msright1981 on 2009-02-01
Hi,

Is Compiz still the best 3D effect source in Ubuntu or is there any better option at the moment, as Compiz seems to cause a lot of problems & crashes on my TP.

---

### Post by Favux on 2009-02-01
Hi msright1981,

Right now it's Compiz.  Gnome is suppose to be making progress.  Kwin in Kubuntu.

Compiz has had it's problems culminating with the main developer walking out.  But the remaining developers just had a meeting, I think they elected a new head developer, and they decided Compiz C++ was the way to go.  So hopefully things will improve noticeably and quickly.

---

### Post by gorcq on 2009-02-02
Yeah, it looks like this is a known bug on launchpad.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/162312](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/162312)

---

### Post by littlematt on 2009-02-09
> **Favux said:**
>  There is at least one other 3500 user, littlematt, trying to get rotation.  I don't know if he has succeeded or not.


Hi again Favux and hi msright1981

Short answer, no, I haven't got it working.

I have the same hardware, a Portege 3500, and get the same error for xrandr, having tried messing aroung with the line about randr in xorg.conf. Interestingly, I think I;m using a different driver,as it says "driver:   trident" in xorg.conf. It still seems likely to be a mis-match between driver, OS and hardware, and a new driver seems the most likely solution, though how to find the right one is beyond me.

Are we still thinking it may be a resource problem? This seems odd, as I always thought of XP as more resource intensive than ubuntu. (I too have "none" for visual effects, I don;t think it will go any higher!)

To Favux in particular, I don't have a second monitor, and getting rid of the extra entries in xorg.conf may well free up resources, though when I tried to comment out some stuff the screen would only display with huge black bars round the outside.


I don't think I've been much help, I'm afraid.

---

### Post by littlematt on 2009-02-10
Hi, thought you might want this (my xorg.conf is attached)

---

### Post by Favux on 2009-02-10
Hi gorcq and littlematt,

littlematt, I think we are taking for granted that with your video chipset the less resources the better.  I have run into a couple of folks who couldn't get rotation with a second monitor added, but were able to rotate once the second monitor was removed, so keep that in mind.

I think you both have the same driver.  Driver   "trident" .  But not 100% sure.

We know the Trident driver use to support rotation on older versions of Ubuntu (Feisty?).  From the bug report I think what you are dealing with is that at some point, a newer version of Xorg's Xserver broke rotation for your driver.  And your driver wasn't updated to work with the newer version of Xserver.  What's the version and date of the last Xorg "trident"?

You should figure out exactly which version of X broke the driver.  You could then go back to the version of Ubuntu that had the X before the one that broke rotation.  You may then be able to backport newer things you want to use.  Lot's of work, admittedly.

If you want to I'd suggest PMing each other and setting up a plan.  You together know an awful lot about the situation.  Divide up the work:
-find the version of X
-what was the last version of X rotate worked for (and the associated Ubuntu)
-start a new thread with all the information (and xorg.conf) consolidated.  (Maybe post on Red Hat, Suse, etc.)
-littlematt, you should post on the bug report.
-look for other bug reports.
-contact the bug maintainer-see what he knows.
-contact Xorg driver dev.s (maybe they would be willing to fix the driver for rotation.  Or if they can't explain why it isn't possible)
-search the web, maybe someone has already fixed this.

Between the two of you it shouldn't require that much time.  You both have Wacom working.  It would be a shame not to get full tablet functionality (rotation).  That's my two cents.

---

### Post by littlematt on 2009-02-11
OK, I'm going away for half term I'm afrad. I get back on Mon 23rd, I'll try and sort this out then. Hopefully if we work together we can find a solution!

---

### Post by Favux on 2009-02-16
Hi gorcq and littlematt,

To figure out which version of "trident" and Xserver you have you could try:
```
dpkg -l | grep [Tt]rident
```
and
```
dpkg -l | grep xserver-
```

---

### Post by littlematt on 2009-02-25
> **Favux said:**
> Hi gorcq and littlematt,

To figure out which version of "trident" and Xserver you have you could try:
```
dpkg -l | grep [Tt]rident
```
and
```
dpkg -l | grep xserver-
```

Hi

```
dpkg -l | grep [Tt]rident
```
gives
```
ii  xserver-xorg-video-trident                 1:1.2.4-1                         X.Org X server -- Trident display driver

```
and
```
dpkg -l | grep xserver-
```
gives what is attached (it was a bit long to post)


I have no idea what any of this means. Do you get the same outputs gorcq?

---

### Post by gorcq on 2009-03-04
I got a different version number when searching for trident. I don't know what it means, either.

---

### Post by Favux on 2009-03-21
Hi everybody,

I found the debian git repository of David Nusinow.  It looks like he is the debian maintainer of the X.org Trident Driver.  The most recent driver version he lists is:
```
xserver-xorg-video-trident-1_1.3.0-2
```
dated 6 months ago.  The one you list littlematt, 1.2.4-1, is dated 13 months ago.  While yours gorcq is 1.2.3-1 dated at least two years ago (the site only lists 1.2.3-2).  The link is:

[http://git.debian.org/?p=pkg-xorg/driver/xserver-xorg-video-trident.git;a=summary]("http://git.debian.org/?p=pkg-xorg/driver/xserver-xorg-video-trident.git;a=summary")

I am intrigued by the entry:
> 2008-06-06  Julien Cristau  Revert to building against xserver 1.4
Why revert to 1.4?  And notice the date.  We are using X server 1.5 in Intrepid and are going to 1.6 in Jaunty.  I also noticed that neither David Nusinow or Julien Cristau seem to be on the bug report.

My guess is David Nusinow is the Debian package mainainer.  But he may also be with Xorg, and Julien Cristau seems likely to be one of/the Xorg driver dev.  At least you now have a couple names to try and contact.  Maybe try David Nusinow first?

I hope this is helpful.

---

### Post by littlematt on 2009-03-21
> **Favux said:**
> Hi everybody,

I found the debian git repository of David Nusinow.  It looks like he is the debian maintainer of the X.org Trident Driver.  The most recent driver version he lists is:
```
xserver-xorg-video-trident-1_1.3.0-2
```
dated 6 months ago.  The one you list littlematt, 1.2.4-1, is dated 13 months ago.  While yours gorcq is 1.2.3-1 dated at least two years ago (the site only lists 1.2.3-2).  The link is:

[http://git.debian.org/?p=pkg-xorg/driver/xserver-xorg-video-trident.git;a=summary]("http://git.debian.org/?p=pkg-xorg/driver/xserver-xorg-video-trident.git;a=summary")

I am intrigued by the entry:

Why revert to 1.4?  And notice the date.  We are using X server 1.5 in Intrepid and are going to 1.6 in Jaunty.  I also noticed that neither David Nusinow or Julien Cristau seem to be on the bug report.

My guess is David Nusinow is the Debian package mainainer.  But he may also be with Xorg, and Julien Cristau seems likely to be one of/the Xorg driver dev.  At least you now have a couple names to try and contact.  Maybe try David Nusinow first?

I hope this is helpful.


Hi Favux

Wow - this is great. Thank you for finding this, I was thinking we wouldn't get anywhere.

I'm afraid I've been bombarded by infomaton, almost all of which has gone over my head - I still feel new to Ubuntu! For example, you say David Nusinow is probaably the Debian package mangaer, what is that?!?

All this about reverting to 1.4 - is that the version of Xorg they're using to run the driver? Am I right that this site is a record of these people building and addapting the trident driver over time? I guess this means they couldn't get it to work in more modern versions of Xorg? I assume reverting to 1.4 for us would mean changing to an earlier version of Ubuntu?

Since you suggest contacting him, a quick google turned up the following page with a email address for him (dnusinow@debian.org) which seems to confirm he works for/has involvemnet with debian. Take a look at the site: [http://packages.debian.org/changelogs/pool/main/x/xutils-dev/xutils-dev_7.4+4/changelog](http://packages.debian.org/changelogs/pool/main/x/xutils-dev/xutils-dev_7.4+4/changelog) perhaps you can tell me what this site is and what this means? I guess it's unrelated to what we're trying to do, but I guess I should send him an email? not quite sure what to say, since, like I say, I don't really understand who he is or what debian is.

Sorry, I guess I'm hoping you'll clarify what all the infomation from your last post actually means for us.

Matt

---

### Post by Favux on 2009-03-21
Hi littlematt,

I think when they say reverting to X server 1.4, he is talking about that is the version of X server he is compiling the driver against.  I know there are problems with 1.5 (what we have in Intrepid).  Maybe that's where rotation was lost?  If it was, from the bug site, the problem that caused him to revert had been going on for a while.

The site you linked to looks to be another Xorg package they are maintaining.  Debian is another linux distribution.  It is an old, established version that Ubuntu is based on.  It is a more "purist" OSS organization.  They won't put any proprietary stuff in their distribution.

Hopefully somewhere on the Debian site(s) is a deb of the newer driver I referenced.  You could try that and see if it supports rotation.  That's one of things to ask for in the e-mail.  You just want to mention rotation is broken and is there anything you can do?  You might want to link to the bug site also.  You could ask him for the e-mail of the driver maintainer so you could contact the maintainer directly.  Just ask (beg?) for help.

Two more 3500 users popped up today.  Hopefully they will join you.  And, especially if they join you on the bug report, you can add their names to the e-mail.

---

### Post by Favux on 2009-03-22
Hi everybody,

Ah ha!  Even more progress.  littlematt Julien Cristau is who you want to e-mail, I think.  He seems to be with Debian too.  Check this link out:

[http://lists.debian.org/debian-x/2008/09/msg00359.html]("http://lists.debian.org/debian-x/2008/09/msg00359.html")

It has his e-mail address!  Submitting xserver-xorg-video-trident-1_1.3.0-2 to experimental means they're checking it out.  Notice the changes from xserver-xorg-video-trident-1_1.3.0-1.

Even better I found the deb site for xserver-xorg-video-trident-1_1.3.0-1 (remember 1_1.3.0-2 is in experimental, so the deb isn't posted yet).  It is located here:

[http://packages.debian.org/unstable/x11/xserver-xorg-video-trident]("http://packages.debian.org/unstable/x11/xserver-xorg-video-trident")

You should be able to download the deb onto your desktop and double click on it to install it without borking your system.  I'm not totally sure, because if it is built against X server 1.4 it may break on the 1.5 in Intrepid.  I think the Debian Package Installer would halt saying it can't install on 1.5 if there was a problem.  What are you on gorcq?

So if you're going to try it I'll give you a link on how to use xfix:

[http://kshoster.net/index.php?c=tuts/xfix]("http://kshoster.net/index.php?c=tuts/xfix")

---

### Post by Favux on 2009-03-28
Hi everyone and littlematt,

A new 3500 user just tested out the xserver-xorg-video-trident-1_1.3.0-1.  And littlematt he started off with a video section like yours and went to gorcq's simpler one.

[http://ubuntuforums.org/showthread.php?t=1102194]("http://ubuntuforums.org/showthread.php?t=1102194")

The xorg.conf he used is on post #13.  In addition to matthewVS, Cdmjfd rode along and fixed his identical video problem.

So I think that makes about 10 of you 3500 users, at least, I've seen in the past couple of months.  And given that only a fraction of folks post there seems to be a fair number of you out there.

If someone uses the xserver-xorg-video-trident-1_1.3.0-1 deb I would love for them to try rotation.

---

### Post by gorcq on 2009-03-30
Hey,

I downloaded the Trident deb, but I can't install it. It just says, "Dependency not satifiable: libc6."

According to the page I downloaded it from, this version requires libc6 ">= 2.5-5". Currently installed on my system is libc6 version 2.6.1-1. Either I don't understand version numbers as well as I think I do, or that dependency is already satisfied.

Oh, and since you asked (I think), I'm pretty sure I have xorg version 1.3.

---

### Post by Favux on 2009-03-30
Hi everyone,

Either they just posted it or I missed it.  Here's xserver-xorg-video-trident 1:1.3.0-2 and it is built against Xserver 1.5!

[http://packages.debian.org/experimental/xserver-xorg-video-trident]("http://packages.debian.org/experimental/xserver-xorg-video-trident")

Since 1.5 is in Intrepid, those of you on Intrepid could try it.  It may be the best chance for rotation.

Hi gorcq,

I'm glad you made a try.  I agree that doesn't make much sense.  Some of the libs are on the deb site, but I don't know if you want to install them.  Maybe that's the Debian Package Manager telling you it will break on your Xserver?  Are you on Feisty, Gutsy, or Hardy?  I forgot.  Since you have 1.2.4-1 I don't think any of the other deb.s apply to you.  But take a look:

[http://packages.debian.org/search?keywords=xserver-xorg-video-trident&searchon=names&suite=all&section=all]("http://packages.debian.org/search?keywords=xserver-xorg-video-trident&searchon=names&suite=all&section=all")

---

### Post by gorcq on 2009-04-03
Gutsy.

---

### Post by littlematt on 2009-04-03
Hi again Favux

I don't quite understand the page you linked too. There is a list of packages to download. I tried goign down the list, and most gave a "wrong archetecture" error. Then the i386 package gave a different error, "Dependency is not satisfiable: xserver-xorg-core".
I found a package called xserver-xorg-core-dbg in synaptic, but this had no effect.
Next I searched for xserver-xorg-core on the site you linked to (packages.debian.org) and downloaded it, but it gave dependency error libdrm2.
So I found and installed this from the same site. This allowed me to install xserver-xorg-core, but it did give an error "Failed to satisfy all dependencies (broken cashe)". A pop up told me to run "sudo apt-get install -f" in teriminal, so I did, and then reinstalled xserver-xorg-core and it seemed to work, but the xserver-xorg-video-trident package still gives "Error: Dependency is not satisfiable: xserver-xorg-core"

I don't understand how the dependency can be not stisfied when I just installed it: perhaps it's a problem with the versions? I don't really understand.

In summary, I downloaded and installed:

libdrm2_2.4.5-2_i386.deb    - Which worked
xserver-xorg-core_1.4.2-11_i386.deb   - Which I think worked
xserver-xorg-video-trident_1.3.0-2_i386  - Which gave dependency error.

Any suggestion for what to do now?? I was hoping that installing this package might be the holy grail, but I can't even get as far as installing it!


littlematt

---

### Post by Favux on 2009-04-03
Hi littlematt,

Sorry that's my fault for not being clearer.  I just wanted you to try the Deb.s and see if they'd install.  They have a lot of the dependencies packaged in them but if they won't run on a different kernel or Xserver then they won't run.

The Xorg Xserver is the basic framework for giving you a graphical environment (gui).  If I run:
```
dpkg -l | grep xserver-
```
among other things I get
```
xserver-xorg-core                          2:1.5.2-2ubuntu3.1                      Xorg X server - core server
```
So Intrepid has xserver-xorg-core 1.5.2-1. Since the xserver-xorg-video-trident-1_1.3.0-1 was built against X server 1.4 for whatever reason I was hoping it might run on Hardy or earlier.  From when you ran that command a while ago was Hardy's xserver-xorg-core a v. 1.4 something?  Did you change it?  Check with the command.  Also see if Synaptic Package Manager gives you the option of going back to your previous version, in other words are both now present?

Bottom line I'm not sure why the dependency wasn't satisfied.  But I didn't want to get into compiling a video driver, hence using the deb.s.  We'd need really good instructions to do that and I can't do that without having your hardware.

I'm back to you folks trying to contact one of the folks involved in maintaining the package or better still involved upstream with Xorg and driver development.  As they don't seem to be listed on the bug report they may not even be aware that rotation was broken, apparently after Feisty?  Disappointingly I don't see anyone posting on the bug report after you and gorcq.

---

### Post by littlematt on 2009-04-04
Hi Favux

I get
```
 ii  xserver-xorg-core                          2:1.4.2-11                       Xorg X server - core server 
```

I have no idea on the significance of this...

I don't know what is was before. I guess a was a little bold to start installing these new packages without knowing the first thing about what I was doing.

Synaptic package manager lists:
[installed]xserver-xorg-core  installed version: 2:1.4.2-11   Latest version: 2:1.5.99.902-1
[not installed] xserver-xorg-core-dbg  latest version: 2:1.5.00.902-1
[installed] xserver-xorg-dev  Installed version: 2:1.4.1   latest version: 2:1.5.99.902-1

EDIT:
going into properties of xserver-xorg-core in Synaptic under versions tab lists 2:1.4.2-11 (now) and 2:1.4.2~git20080131-1ubuntu9 (hardy)

Which I think means I could force it to roll back to there, but don't know if that would help.

---

### Post by Favux on 2009-04-04
Hi littlematt,

OK
```
ii  xserver-xorg-core                          2:1.4.2-11
```
Should mean v. 1.4.2-11 I guess.  And from your output in "dgkg -l.txt" you had:
```
ii  xserver-xorg-core                          2:1.4.1~git20080131-1ubuntu9.2    Xorg X server - core server
```
which would be v. 1.4.1?  So you did update it, it looks like.  And Xserver is still bringing up your gui (desktop).  So no harm no foul?  It just isn't, for whatever reason, letting you run the new Trident driver from the deb.

Your running Hardy correct?  Any particular reason?

---

### Post by littlematt on 2009-04-05
Yeah, I'm in Hardy.

When I first installed, I tried the newest (Intrepid, I think) but I couldn't get the resolution to work, and saw somewhere that Hardy had more tools & functionality in that respect.
You thinking a different version might work with this package?

---

### Post by Favux on 2009-04-05
Hi littlematt,

On Hardy MatthewVS got 1.3.0-1 to work.  But that was built to Xserver 1.4 which is the version in Hardy.  Since 1.3.0-2 is built to 1.5 which is the version in Intrepid I would think you would need to be in Intrepid for it to work.  But since we don't know if it supports rotation I am uncomfortable encouraging you to move from Hardy LTS to Intrepid just to try.

But you could see if 1.3.0-1 works for you and allows you to simplify your xorg.conf like Matthew's.  And you could double check rotation.

---

### Post by xzero1 on 2009-04-10
> I am uncomfortable encouraging you to move from Hardy LTS to Intrepid just to try.
Ah, but he may not have to  -- if he has the space. See this thread [http://ubuntuforums.org/showthread.php?t=1121058](http://ubuntuforums.org/showthread.php?t=1121058). Still, I haven't yet tried this, but ***windows** will be forever banished *from my tablet if it works!

 I plan on installing Jaunty netbook remix by this method (it already has cellwriter support). It seems Jaunty has targeted portables and hopefully, thats what some of this trident work is about. I am running Intrepid and will be happy to try some new debs or take a shot at a new compile after I see how Jaunty works out.  Keep up the good work.! :p

---

### Post by Favux on 2009-04-10
Hi xzero1,

Slick, I saw your thread earlier before you found the solution.  I didn't realize you had a Toshiba Portege 3500.

---

### Post by xzero1 on 2009-04-10
> Hi xzero1,

Slick, I saw your thread earlier before you found the solution.  I didn't realize you had a Toshiba Portege 3500.     Indeed, I do.  BTW, working rotation must have been pre-Feisty I had that installed and it did not work. Since someone has gotten rotation to work on Hardy I think it would be of great help if he can post on the bug report that was previously mentioned.

---

### Post by gorcq on 2009-04-10
> **xzero1 said:**
> Still, I haven't yet tried this, but ***windows** will be forever banished *from my tablet if it works!

Booting to an iso file on the hard drive does look cool, if it works; I wasn't aware that one could simply edit the grub menu like that.

As for Unetbootin, that's how I originally put Gutsy on my laptop. I tried using it again last month in the hope of testing Xubuntu to see if rotation worked in that, but ended up spending four hours trying to get the damn thing to connect to the internet and download the operating system before giving up. I tried using both ethernet and wifi connections without success. 

It's funny, because when I installed Gutsy, I recall the process being surprisingly simple. Of course, I installed Unetbootin from Windows that time, using a Windows msi file, instead of from Linux. I wonder if that had anything to do with it...

---

### Post by littlematt on 2009-04-17
Hi Favux, and everyone else

Sorry to be a cop-out, but I've decided to got back to XP, at least for now.

I've found the hard drive just isn't big enough for two OSs, and I find I keep runnig out of room for music etc.
I'd prefer to get rid of XP and stick with Linux of some form, but there are several resons I can't. Mainly, I need MS Word for school work (OpenOffice is great, but not 100% compatible with .doc yet). The lack of rotation aslo gets on my nerves, but it seems we're very close to a solution.

I'll probably be back, maybe this summer once I've finished school, on one linux distro or another. For now, though, goodbye and thank you so much for all your help.

See you again soon, I hope
littlematt

---

### Post by Favux on 2009-04-17
Hi littlematt,

Sorry to hear that.  But your reasons sound valid.

Have you thought about getting a larger hardrive and increasing your RAM?  Not too expensive nowadays.

---

### Post by gorcq on 2009-10-27
Wow. It's been awhile since anyone posted on this thread.

I spent this weekend upgrading my laptop to Jaunty, and I thought I'd report for the record that this has not made it spontaneously capable of rotating the screen.

---

