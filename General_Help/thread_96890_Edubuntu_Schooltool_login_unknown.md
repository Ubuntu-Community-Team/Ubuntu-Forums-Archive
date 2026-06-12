---
title: "Edubuntu Schooltool login unknown"
date: 2005-11-29
forum: General Help
---

### Post by BobSongs on 2005-11-29
Greetings all;

I decided to give Edubuntu a try seeing that it had a few extra goodies. One of them is School Tool.

The instructions on the [Edubuntu]("http://www.edubuntu.org/tour.html") website say:
> The Schooltool Calender can be accessed from the Firefox web browser, by entering "localhost:7080" into the address bar.
Fine. Tried that and sure enough it works.

I click "Log In" on the right of the red bar and a login screen appears requesting a Username and Password. Using my own name and password don't get me in. 

I checked out the [Schooltool website]("http://www.schooltool.org/"). Even opened an account there. But that didn't do anything to let me log in to my own from localhost:7080. It's probably something very obvious I'm doing wrong. So if anyone's figured this out I could use a hand.

**Note:** Having read a previous post concerning logins, I tried ```
sudo gedit /etc/group
``` and modified **schooltool:x:116:** to **schooltool:x:116:bob** (adding my user name) and rebooted the PC. Still: no change.

Thanks,

Bob

---

### Post by adadof6 on 2005-11-29
Here are the default manager logins for [SchoolTool]("http://www.schooltool.org/") and [SchoolBell]("http://www.schooltool.org/products/schoolbell"):

For SchoolTool:
[LIST]
[*]Login: manager
 [*]Password: schooltool
[/LIST]
For SchoolBell:
[LIST]
[*]Login: manager
 [*]Password: schoolbell
[/LIST]

---

### Post by BobSongs on 2005-11-29
Thanks! It works for Schooltool.

Now to see if I can get Schoolbell installed.

I appreciate the efforts!

Bob

---

### Post by ubuntu27 on 2005-11-29
Hey BobSongs. Good luck with Edubuntu.
How long have you been using it (Edubuntu)?
Have any opinion, comments about Edubuntu?

I am asking this question because I am planning to buy a new [well, new for me, but not a new hardware] computer for my little sister. and install Edubuntu.

---

### Post by BobSongs on 2005-11-29
> Hey BobSongs. Good luck with Edubuntu.
Thanks!

> How long have you been using it (Edubuntu)?
I've installed it on PC2 about a week and a half ago. And PC1 has a dual boot with XP, with Edubuntu as primary O/S. That install is about three or so days old. It was on earlier but XP went wonky as usual. Re-installing XP meant losing GRUB. I followed some of the GRUB re-installation suggestions. But a lack of clarity had me destroying Edubuntu by mistake. :( Sooooo. I re-installed them both. Now they run well together.

> Any your opinion, comment about Edubuntu?
Well. I have to use a crowbar to get my kids off it. I figured they'd miss all the Windows games like Bugs Life and Pyjama Sam. On occasion my 3-year-old asks about it. I let him play in XP on my machine. But other than that my children enjoy it. On occasion I direct my kids to educational games which they do enjoy. But **Planet Penguin Racer** gets a lot of use. Not once have I heard a lament about the erasure of Windows.

As far as functionality it is essentially Ubuntu with a few extra goodies tossed in as a default part of the installation. Schooltool and a number of other items listed on the site are default installs. There's really nothing terribly exceptional. It uses the Gartoon icon set by default. That can be downloaded. The extra learning utilites are either available through Applications > Add Applications or Synaptic. The desktop background's cute and can be downloaded from the Edubuntu website along with quite a few more that should have been added as alternatives.

> I am asking this question because I am planning to buy a new [well, new for me, but not a new hardware] computer for my little sister. and install Edubuntu.
Again: it works like Ubuntu and not like Kubuntu. Imagine Ubuntu with added goodies for younger kids and teens. I was warned about installing Kubuntu, that there are a number of items that are broken.

I installed Edubuntu on a friend's PC as well. His kids enjoy it. They do the basics: email, IM, surfing, etc. I preinstalled it with the help of Automatix and other Firefox tweaks so the transition from Windows98 wouldn't be painful.

Bob

---

### Post by ubuntu27 on 2005-11-29
Thanks Bob!! :)

---

