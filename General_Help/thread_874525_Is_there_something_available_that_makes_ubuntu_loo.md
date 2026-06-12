---
title: "Is there something available that makes ubuntu look like Windows?"
date: 2008-07-30
forum: General Help
---

### Post by rmjohnson144 on 2008-07-30
Sorry if this has been asked a thousand times, but I can't seem to find exactly what I'm looking for.  

The reason I need this is that I maintain my family and friend's computers and they are just fed up with the constant virus and paying big bucks for virus protection that just doesn't work at all.

anyway, they are finally interested in Linux if they can use most of their windows programs and remain virus free.  unfortunately they are mostly computer illiterate and would be totally lost in ubuntu.  I was hoping that there was a nice Windows theme I could install to help in the converting process.

Thanks for any tips
-=Mark=-

---

### Post by david_lynch on 2008-07-30
> **rmjohnson144 said:**
> Sorry if this has been asked a thousand times, but I can't seem to find exactly what I'm looking for.  

The reason I need this is that I maintain my family and friend's computers and they are just fed up with the constant virus and paying big bucks for virus protection that just doesn't work at all.

anyway, they are finally interested in Linux if they can use most of their windows programs and remain virus free.  unfortunately they are mostly computer illiterate and would be totally lost in ubuntu.  I was hoping that there was a nice Windows theme I could install to help in the converting process.

Thanks for any tips
-=Mark=-

IMHO if they really want windows, you should let them have windows. Just make sure they have a good firewall, keep their virus software, their popup blockers, spyware blockers etc all up to date, don't open emails from strangers, don't go to untrusted websites etc...

If they do get to the point where they want a change, linux is pretty easy to use, as long as the hardware is supported. I just can't see trying to make linux look like windows. bleh, what a thought.
:lolflag:

As for running their windows programs, that really depends on what they are. Some windows programs are well behaved under wine, some aren't. Some windows programs have native linux equivalents. If you can list what programs they want to run, we could get a better idea of the feasibility.

---

### Post by zxscooby on 2008-07-30
[http://ubuntuforums.org/showthread.php?t=871614](http://ubuntuforums.org/showthread.php?t=871614)

check it out

---

### Post by eppo on 2008-07-30
i would probably try using KDE. that acts/looks more like windows. but then as far as programs, that depends. IMO if they want to play games, they shouldnt bother. or they need to let you know exactly what they do with it, and install all the programs they need so they dont need to configure it at all. make sure you have sshd running, because you are going to have to log in and help them fix stuff.

---

### Post by DJI274 on 2008-07-30
How about getting them on to the most popular Open Source Applications first, Firefox,Thunderbird, OpenOffice etc. That will probably cover the majority of their needs and once they are happy with them they'll hardly notice the switch to Ubuntu.

---

### Post by billgoldberg on 2008-07-30
Install them a nice copy of linux mint.

And place some icons on the desktop.

They will love it.

---

### Post by rmjohnson144 on 2008-07-30
Thanks for all the replies.

I like that link with the Royale themes.  I liked the Vista themes in there as well, but I have been warding off Vista to everyone, but a few are thinking of getting it lately now that most of the major issues have been ironed out.  

As for the programs they run, they mostly use email and browsing with some works/office use.

mostly Word.  I was thinking about openoffice lately as that is ported to windows.

I have Firefox on all systems, but they switch back to IE most of the time as they are familiar with it.  I'll have to check firefox and see if there is a IE theme.

Most use Outlook for email and evolution is close.  I have Thunderbird installed but they all switch back to Outlook.  Some I've talked some into webmail to avoid putting messages on their machine, so that should convert well.

some are starting to use Windows messenger.  Is there a good look-a-like for that?

as for games most are simple D stuff and DX9 so most should run under Wine.  Some are starting to use these online gaming sites.  My cousin is on Pogo.com and it seems to use a lot of Java so that should be OK.  You know of any sites that would be compatible with unubtu?

Most don't even touch the file system stuff so that should be OK. It just needs to be point and click and the more it resembles windows the more comfortable they'll feel.  They just don't want a huge learning curve more than anything.

---

### Post by tuxxy on 2008-07-30
Install windows in Virtualbox and load it up from in Ubuntu

---

### Post by chavanak on 2008-07-30
I second tuxxy. But you need a decent system to run a virtual box or vmware

---

### Post by Mark Phelps on 2008-07-30
To try to address your original comments ...

1) Reusing most of their windows apps.  Running a virtual Windows session inside Linux will give you the best chance of being able to reuse your windows apps.  Other options are installing Wine or Crossover.  I've used both of these last two, and apart from some "older" (2003) versions of MS Office apps, the results have been total failures of one kind or another.  However, I gave up on this over six months ago, and the more recent versions of Wine or Crossover might be better.  You should google for these two, go to their respective websites, and look through their lists of compatible Windows apps to get a feel for how well they will work with the apps you want to reuse.

2) Windows Desktop.  The KDE desktop bears a lot more similarity to the Windows (XP) desktop than does Gnome.  You can install Ubuntu using Gnome by default and add the KDE desktop later.  Also, if you want a GNU/Linux distro that looks and behaves even more like Windows, look into PC LinuxOS (known as PCLOS).  They now have two current distros, one with KDE by default, and one with Gnome by default.

3) Windows look-alike.  There is tweaking you can do that will modify the look-and-feel of Linux to be a lot more like XP or Vista. Examples for Vista include Aero-LINsta (for the general theme) and LiNsta-Black-Plastic-Alu (for the windows borders).  Look at Gnome-look.org for the GTK themes and you will find these.

4) Doing "windows-stuff" in Linux.  Open Office is improving it's ability to import MS-document stuff with every version. Version 2.4 does a superb job of importing MS Word and Excel files. Haven't tried the Works files, so I can't tell you about those.

5) Outlook replacement.  While Thunderbird is a great alternative for email to Outlook, the MS app has grown over the years to be much more than email.  Don't expect T-Bird to do everything that Outlook currently does; in fact, I don't believe that there is a single Linux app that does everything Outlook 2007 does.  But ... since I use webmail by default, I could be wrong about this.

Good Luck

---

