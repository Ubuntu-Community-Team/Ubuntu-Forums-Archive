---
title: "Kubuntu 8.04 -&gt; 8.10 has bad nvidia issues"
date: 2008-10-31
forum: General Help
---

### Post by reuben on 2008-10-31
I have an NVidia 8800 GT. I updated from 8.04 to 8.10 (using the craptastic adept manager).

First boot took me to the CLI, with cryptic X errors about "no screens found". I edited xorg.conf, changed the driver from nvidia to nv, tried to start X again...total lockup, and no way to get to the CLI.

I'm sick of ubuntu's crappy QA, and I'm sick of the attitude of the ubuntu reps in launchpad (everything's a wishlist; etc.)

I may well be done with ubuntu on my desktop (or, I might just go back to 8.0.4. Sigh.)

---

### Post by Astronomerguy on 2008-10-31
There are lots of helpful suggestions available for fixing this, but so far, none of them work. I'll probably downgrade to 8.04 as I know it works on my HW configuration.

---

### Post by cariboo on 2008-11-01
I just love it when people complain about free software. The way the graphics adapter drivers work in Interpid in different from the way they worked in previous version. BTW the drivers are closed source drivers provided by the manufacturers if you have any complaints direct them to Nvidia, all the maintainer does is package the **closed source drivers**. 

That being said to get your system up and running restart in recovery mode and at the menu use xfix to create a new /etc/X11/xorg.conf. this should at least get you up and running in low graphics mode. Next remove all nvivdia packages using synaptic. then use the System-->Administration-->Hardware drivers to install the latest drives for your graphics adapter.

Jim

---

### Post by reuben on 2008-11-01
I did create a blank xorg - specifically via dpkg-reconfigure. It, also, didn't work.

I will try xfix next time I'm in this circumstance; thanks for the tip.

That said, your excuses about this mean nothing. Ubuntu is not a hobbyist distro maintained by love and sweat. Mark Shuttleworth is an entrepreneur as well as an idealist; I guarantee you he's thinking revenue stream in the medium term (even if not the short term.) Look at Red Hat, too.

Ubuntu bundles the nvidia binary drivers. If they didn't, I wouldn't bitch about this. But I can't count on my two hands (maybe a slight exaggeration) the number of times Ubuntu has left me on the CLI after version upgrades or even regular in-version updates. I don't tend to sit on the betas; I generally wait until the release is shipped. 

I'm annoyed because I want Linux to succeed on the desktop among consumers; I've been using it exclusively for almost 9 years; I've gotten 2 of the engineering departments that I've worked at into Ubuntu desktops; I have my computer illiterate father on it, and he likes it fine (I tell him "don't run system updates.") It's a good system. The thing it's missing, that's holding it back (whether "it" is ubuntu or desktop linux in general) is a serious and rigorous approach to QA. When you have bug triagers refusing to pass bugs upstream unless you can reproduce the bug (it's my primary computer, buddy; I'm not going to screw it up again just to tell you that it's still an issue, and I already gave you steps to reproduce; just do me a favor and believe that it happened to me two months ago, when I filed the bug), or refusing to deal with issues (hard lockups, for example) that their software is causing due to interaction with some other component (because it's the other module's fault, of course), or the most subscribed to and longest running bug report threads continuing for years...well, that kind of defeats the purpose of running a bug reporting system, doesn't it? I didn't even file this issue in launchpad for exactly those reasons -- I don't have the log files, since I reinstalled 8.0.4; I'm not about to try it again, since I have better things to do with my time (and need my computer for work); so, the bug would go unaddressed and would likely be closed by the first triager who happens upon it. So the only thing I can do is bitch.

---

### Post by mooha on 2008-11-01
> I just love it when people complain about free software. The way the graphics adapter drivers work in Interpid in different from the way they worked in previous version. BTW the drivers are closed source drivers provided by the manufacturers if you have any complaints direct them to Nvidia, all the maintainer does is package the closed source drivers.

That being said to get your system up and running restart in recovery mode and at the menu use xfix to create a new /etc/X11/xorg.conf. this should at least get you up and running in low graphics mode. Next remove all nvivdia packages using synaptic. then use the System-->Administration-->Hardware drivers to install the latest drives for your graphics adapter.

Jim

xfix do no good, the man is saying that the driver was working on 8.04, maybe the solution will be like trying to do clean install and try out those drivers, again MAYBE I said.
Ubuntu is missing a tool like Yast. 

the man is talking good positive things, if you accept the reality you get better, because when people are trying to report problems and complain, ubuntu forum admins shouldnt take it a an attack on ubuntu, yes it's free software, bla bla bla, yes you have free volunteer developers bla bla bla, but if you listen to who complain you might have a better Idea to work smarter.
and please those people are not Terrorist do not BLOCK THEM, give them freedom of speech. the only people they shut other people's mouth are DICTATORS.
Please DO NOT BLOCK MY MESSAGE, IT'S GOOD FOR UBUNTU TO GET BETTER IF YOU LOVE FREEDOM.

Excuse my miss spelling ... Eng is not my mother language but I think you got the message.
Keep up the good work, and listen to people

---

### Post by overdrank on 2008-11-01
Please let me remind all to be polite in responses and follow the COC. Thanks :)

---

### Post by Zimmer on 2008-11-01
> **mooha said:**
> xfix do no good, the man is saying that the driver was working on 8.04, maybe the solution will be like trying to do clean install and try out those drivers, again MAYBE I said.
........

the man is talking good positive things, if you accept the reality you get better, because when people are trying to report problems and complain, ubuntu forum admins shouldnt take it a an attack on ubuntu, yes it's free software, bla bla bla, yes you have free volunteer developers bla bla bla, but if you listen to who complain you might have a better ........
Keep up the good work, and listen to people
In the not so recent past( a few releases ago) it was a lot of reading and a learning exercise to enable 3D rendering using CLOSED SOURCE (NON UBUNTU) drivers for NVIDIA and ATI owners, lots of forum posts "How do I enable 3D with my ....etc.." and many patient people kept replying pointing to the same wiki pages full of instructions and advice (including the warning that in the event of a kernel upgrade you would probably need to start all over again!!).

The people spoke/complained, UBUNTU listened, and we now have a 'simple ' method of 'installing' these (NON UBUNTU) drivers into the kernel. PROBLEM?  Yes. The brand new Ubuntu user has not read any documentation warning of the consequences of a kernel upgrade, and the handy installation GUI gives no hint of what to do next. 

Experienced users have 'seen it all before and read the wikis'. They are prepared to jump through many hoops and read many a wiki to restore their drivers and 3D rendering.

'New' users have clicked an option on an Ubuntu GUI and expect it all to be OK - which it is not! Major disappointment. It is Ubuntu's fault, obviously....

Yes, I agree, on reflection it IS Ubuntu's fault. 

If they had NOT listened to the people there would be NO option to enable the CLOSED SOURCE drivers (and the forums would still be echoing to the sounds of "How do I enable  NVIDIA/ATI 3D drivers ?").

The new user would have to go away and read and learn how to cope with this change to their Ubuntu set up.

How to resolve this?
1. Remove the option and go back to answering the "How do I install.." posts.
or
2.A little more advice on the 'Hardware drivers" option GUI might help - a few pointers in the available directions. A working option to uninstall and reinstall the drivers, maybe (might not fit well with the 'Philosophy' of Ubuntu, which more new users should read.)

 The work, to be helpful to new users with NVIDIA and ATI cards who would like 3D acceleration using CLOSED SOURCE DRIVERS, is only half done......

To undo the completed half, or to complete the other half? That is the question....


Long rant, sorry, but I have seen too many posts whining about the kernel upgrade...

---

