---
title: "Ubuntu 9.10 Suddenly Logs Off"
date: 2010-01-21
forum: Hardware
---

### Post by nwu on 2010-01-21
I'm encountering a very strange problem on Ubuntu 9.10, which is that my computer seems to suddenly log off for no particular reason and take me back to the login screen.

The reason I'm posting this in the Hardware forum is that it seems this started happening almost as soon as I got a new monitor for my computer.

Any ideas how I might fix this? Thanks.

EDIT: Perhaps I should also mention the following two things. The monitor is quite wide (1920 x 1080 is the recommended resolution), so I had to do a bit of fiddling with my xorg.conf file to get it to work. I also started using Compiz not long after I got the monitor, so that may be related to the problem.

---

### Post by nwu on 2010-01-23
Any ideas on this? It seems to be becoming a more serious problem now (happening suddenly several times a day).

Thanks.

---

### Post by ratcheer on 2010-01-23
Mine did that today. I have been running it for several months and this is the first time it has happened. I have no idea why and I hope it doesn't keep doing it, but I'm afraid it will.

Tim

---

### Post by mikesir87 on 2010-01-23
I've experienced this a few times... maybe two times in the last month.  I'm not quite sure what causes it either.  Once, it occurred just as I clicked on a link in Firefox.

---

### Post by nwu on 2010-01-24
OK, so I'm not the only one with this problem. It also seems to happen more often to me when I'm browsing.

I'm assuming from your profiles that you both use 9.10 as well. Has either of you installed a new monitor or started using a new program (such as Compiz) recently?

---

### Post by ratcheer on 2010-01-25
I installed a new monitpr a few weeks ago. I switched from an old 17" CRT to a 20" Magnavox LCD television set, which specifically has a PC input setting. Ubuntu and/or the nVidia driver recognized the model and automatically configured the resolution and refresh rate correctly, too.

Tim

---

### Post by YesSir on 2010-01-27
Hi all,

Just writing to confirm this. I have been working on a new monitor for a couple of days and this morning Ubuntu logged off, so I doubt whether it't because of that. Further, after installing the new monitor I also configured compiz, but that has also been some days ago.

Mine logged of using Thunderbird, it looks quite randomly...

Using 9.10.

Regards

---

### Post by mikesir87 on 2010-01-28
I do have a second monitor, but I don't connect to it very often. I also have a nVidia graphics card.  I do have Compiz installed, but I put that on right when I installed the OS.  I haven't had a log off for a few days, but I'll let you know when I do.  The last time was as I was browsing around on the internet (Firefox).

---

### Post by shusai on 2010-01-29
I could see the same problem with 9.10 right after the release which always makes me go back to 9.04 again as I don't want to work with an unreliable system.
I try to install 9.10 from time to time to see if the problem has already been fixed, but no luck yet.

I just installed 9.10 on my Panasonic-T5 notebook, so it's definitely no monitor issue for me.

Firefox was running but the log off this time came when I was typing in gedit.

The log offs are totally unpredictable and not reproducible, the only thing I can tell for sure is that it never happens with 9.04, only with 9.10.

I checked the logfiles (don't really know what to look for though;)) and the only thing which seems strange is this error(?)-message: kernel: [   11.787377] [drm] TV-12: set mode NTSC 480i 0
This occurs every few seconds.

I don't know if this could cause the log off, after doing some research on google it looks as if it is a problem with Intel GMA graphic. Disabling all visual effects helped some people. I also read that with newer kernel-versions (2.6.31.33?) the error was gone, but in that case we have to wait until a new kernel will be released.

Before going back to 9.04 again I will try for a few days if the log offs still occur with all visual effects turned off.

---

### Post by gcvisel on 2010-01-29
Seeing the same with an eMachines E520 laptop.  9.4 was stable, but 9.10 logs off every few days, mostly in Firefox, (but I have FF running all the time.)
 
   Maybe I'll downgrade back to 9.4.  :-(

---

### Post by shusai on 2010-01-29
After a few hours I thought everything was OK, but suddenly another log off.

So disabling all visual effects does not help, I'm going back to 9.04 again... :(

---

### Post by YesSir on 2010-01-30
I was trying to remember what I changed the day this started.. I added the system monitor to my task bar. It´s a long shot, but could it have anything to do with the sudden log offs?

---

### Post by shusai on 2010-02-01
I think [**this bug report**]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/511095") on launchpad is "our bug".

It would be helpful if we posted our issues there.

---

### Post by RJARRRPCGP on 2010-02-01
I don't have this problem.

---

### Post by ratcheer on 2010-02-02
> **RJARRRPCGP said:**
> I don't have this problem.

Lucky you.

Tim

---

### Post by spartan298 on 2010-02-03
As I was setting up the screensaver on a fresh install of 9.10 I found that running the SS preview or just allowing it to start, say after 1 minute, consistently causes the system to log off.

---

### Post by shusai on 2010-02-04
Interesting.

I completely disabled the screensaver yesterday and had no log off since...

---

### Post by Amrobadr on 2010-02-06
Same Problem here
I'm disabling all visual effects & using v9.10

but the problem is still appearing

I've disabled the screensaver, and I'll see if this will work :confused:

---

### Post by Amrobadr on 2010-02-06
Same problem again :((
it's really annoying :(

---

### Post by shusai on 2010-02-06
Same problem again! :(

No issues for two days so I thought disabling the screensaver did help, but it just happened again...
This time it was right after I copied some text with Ctrl-c.

I'm not really sure, but I think this was not the first time it occurred after copying, has anybody else noticed something similar?

---

### Post by teh603 on 2010-02-06
I had this problem on my AAO when I briefly "upgraded" it to Karmic. Turned out it would log me out whenever I'd enter my admin password to run the update manager. Got really frustrating, too.

---

### Post by nwu on 2010-02-06
For me, it seems to happen mostly when Firefox is loading something.

---

### Post by Whisp3r on 2010-02-09
I've tried several things.

Disabled visual effects, disabled screen saver, turned them on, etc. I have found no pattern. It's happened while browsing in Firefox, using terminal, writing in OpenOffice, or even when the computer was 'idle' and I wasn't doing anything.

Almost seems like it's time to drop back to 9.04. Makes this version unreliable.

---

### Post by itsjustarumour on 2010-02-10
Oops, post deleted, my mistake!

---

### Post by pudge on 2010-02-12
I am having the same problem with 9.10 as well.  Adding hardware was not a factor.  I believe adjusting resolutions for a high end monitor does have an affect on this issue.  I watch the logon wink, blink, try to drive to the higer res and then logoff.  Same with firefox as the display engine renders a page. Granted firefox does not change screen resolution but it does drive the video driver to re-render text and pictures to statisfy user display options.

---

### Post by shusai on 2010-02-13
I'm not sure if it did really help, but for 2, 3 days I'm not having any problems anymore.

I added the PPA from [here]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"), a few updates were installed afterwards and no more log off since...

---

### Post by pudge on 2010-02-14
> **shusai said:**
> I'm not sure if it did really help, but for 2, 3 days I'm not having any problems anymore.
 
I added the PPA from [here]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"), a few updates were installed afterwards and no more log off since...
 
shusai - thank you!!:D
 
So far this works for me as well.
 
This reminds me of a similiar problem encountered in ubuntu 8.x where the nVidia driver blew up xfce/gnome upon logging in, returning the user to the logon screen.  Back then the solution was to reset some vesa parameters in xorg files - thankfully alcohol usage has blotted out most of that painful memory. The PPA you provided has updated drivers and xorg files that seem to solve the problem for me.
 
Again, many thanks.

---

### Post by Whisp3r on 2010-02-23
I tried that solution. Worked fine for a couple days as well, but were back at it.

---

### Post by Whisp3r on 2010-02-24
Where would I find a log to see why my xsession is logging off?

---

### Post by itsjustarumour on 2010-02-26
> **Whisp3r said:**
> Where would I find a log to see why my xsession is logging off?
I think Xorg.0.log and Xorg.0.log.old are the ones to look at, which can be found in /var/log

---

### Post by jmberros on 2010-04-11
This has been happening to me the past few days and I have JUST seen it 10 mins ago. 

Firefox was opened, but let's be honest, Firefox is always opened. It happens often when I leave the computer logged at night, downloading torrents with Transmission. I have a desktop-pc (no laptop/netbook), Karmic 9.10, and I haven't made any hardware changes recently (no new monitor).

---

### Post by flanagan on 2010-05-01
This happens to me every time there is a major Ubuntu upgrade (like yesterday's official release of 10.0.4 Lucid Lynx), it is always 100% reproducible and fixable. There is apparently some gross incompatibility among Firefox, Flash, and Compiz Fusion.

**To reproduce (for me)**: Visit a site that uses flash (any site) in Firefox. Then enter some text in the search box (any text). Sometime between the 5th and 10th character I enter, Firefox crashes, taking Ubuntu right out with it. It actually just logs you out of Ubuntu. After that, Firefox will always crash using the search box in just the same manner until you do at least a Restart.

**The fix (for me)**: This is brought about by the fact that a major upgrade to Ubuntu always seems to insist on installing Compiz Fusion plugins, despite the fact that they were not installed in the previous version. I can live without Compiz Fusion plugins, but not Firefox/Flash. I just use Synaptic Package Manager to remove compiz-fusion-plugins-main and Restart. 

I suppose if you cannot live without these plugins, you might try a different browser, until these three/four pieces of software get their collective act together.

---

### Post by completely new on 2010-05-06
The same thing happens to me. Since I got Ubuntu, it's all problems and nothing's being fixed. :(

---

### Post by RJARRRPCGP on 2010-05-07
Getting logged off, sounds like the problem I had, IIRC, with Midori, when using the current TinyMe base. (it may have also occurred under Ubuntu)

The current Midori version seems to have fixed that bug. 
When I was at weather.com and trying to get weather information, poof, all of a sudden I have the login screen in front of me!
Apparently, just the browser crashing, can crash the GUI system, X.Org, or the desktop environment.

Cannot recall getting logged off when using Firefox.

---

### Post by AkifTariq on 2010-05-13
Yesterday I clean installed Ubuntu 10.04 LTS and I started facing this problem. I usually prefer swap file over swap partition and did so in this installation. Is it possible that swap file is causing the problem in Ubuntu 10.04. I never faced such problem in Karmic even with swap file. One very important thing I noticed is that it logs me out when I am typing in google search extension in firefox (on top right).

---

### Post by bubblessg on 2010-05-26
I have this problem too... and nothing helps...I change my monitor , and for now its okay
I pritty sure its nvidia driver

---

### Post by heremy on 2010-05-27
new user here...stumbled across this forum due to having this logging off issue...hope there is a fix in the works. very aggrevating.

---

### Post by malfindin on 2010-05-28
I have the log out issue as well and very interestingly I have:


A. An Intel Graphics Card
B. A second Monitor Attached
C. Use Thunderbird for EMAIL.

Why on earth would these 3 things combine to create and issue? I noticed in the thread that two other people had the same combo.

---

### Post by itsjustarumour on 2010-06-08
I'm had this same problem on 3 different machines with NVidia, ATI and Intel graphics, so I don't think its tied to a particular driver - my gut feeeling is its an Xorg problem.

---

### Post by Man_Beach on 2010-06-08
This has been happening to me too, since my clean install of 10.04 - never happened with 8.10.

I thought it might be due to my fairly old ATI Radeon graphics card - I had to disable all of the visual effects in preferences to get 10.04 to work properly in the first place. So, with no use for visual effects, I've tried flanagan's solution of removing compiz-fusion-plugins-main. It removed Compiz as well, but so far all seems to be working well.

---

### Post by malfindin on 2010-06-08
I have resolution. If I don't leave Thunderbird open after use, so that it's not active when the screen-saver kicks in. I no longer have the issue. I have no answer as to why this works or what causes the issue in the first place, but for me it is "fixed".

~malfindin

---

### Post by Man_Beach on 2010-06-09
> **Man_Beach said:**
> This has been happening to me too, since my clean install of 10.04 - never happened with 8.10.

I thought it might be due to my fairly old ATI Radeon graphics card - I had to disable all of the visual effects in preferences to get 10.04 to work properly in the first place. So, with no use for visual effects, I've tried flanagan's solution of removing compiz-fusion-plugins-main. It removed Compiz as well, but so far all seems to be working well.

Nope - didn't work. Think I'll try Opera instead.

---

### Post by qonos68 on 2010-06-10
Same problem here. There has not been any problem until an upgrade to  Virtualbox 3.2.4. It happened yesterday and since that moment I had this  issue three times: the first time trying to connect through vnc, the  second using firefox and the third doing nothing special being connected  through vnc again.
Hope this help.

---

### Post by sosaited on 2010-08-03
I've had this problem 3 times now, and have lost some pretty important data when it happened.

I can't remember what I was doing the first time, but the second time I typed "n" and "Enter" in Firefox, and it got to the log in screen. And just now I was typing something in gedit (Firefox was running), I pressed Enter, and got the log in screen.

I have Intel 915G Chipset Asus P5GL-MX board and 32bit Karmic.

---

### Post by malfindin on 2010-08-03
For me the problem went away after distro upgrade to 10.04. Back up and upgrade.

---

### Post by buildup on 2010-10-29
Flanagan - thnx for your post.  In 9.x, 10.04 my Dell 1764 Core I5 would freeze.  10.10 the instant logoff.  Your post seems to have worked.  This would ALWAYS happen with VMWare Workstation or Player within 10 mins.  So far it has been running 15mins!

---

### Post by penta666 on 2011-02-07
Hello all

I have same problem, Ubuntu 10.10 suddenly Logs Off.

I have try to solve problem by doing several steps, but it's not helped. :( 

1. I try to change VGA Card (from nVidia to ati)
2. I try to read logs , but there nothing interest , no warnings, no error
3. I try to install Debian, Ubuntu 10.10 Server, Ubuntu 10.10 x64

Help me please , I don't know how to fix this prblem :( 

P.S. I don's use Firefox and my "uname -r " == 2.6.35-26-generic-pae 

Regards.

---

### Post by malfindin on 2011-02-07
I'm sorry It's been a long time since I had this problem. Updates fixed it for me. I do remember it was a specific program that caused the issue. Are you using stock Ubuntu with nothing added?

---

### Post by penta666 on 2011-02-07
No , I'm using Ubuntu with many programs and configurations that I do for myself :(

---

### Post by penta666 on 2011-02-07
No , I'm using Ubuntu with many programs and configurations that I do for myself

---

### Post by penta666 on 2011-02-07
One thing.... It's happened randomly , I can't understand when and why :(

---

### Post by malfindin on 2011-02-07
We'll here's what I suggest as a fix. The issue is almost certainly related to how Gnome interacts with your extra software. Install the Kubuntu or Xubuntu desktop and use that for awhile until you see a kernel update fly by, then you can try Gnome again.

I use KDE, GNOME, and EXFICE interchangeably on my laptop without issue.

Some gnome settings spill over into Xubuntu. KDE is almost it's own universe.

That's the beauty of Linux, if one thing isn't working you have so many choices, none of which cost you money.

~Malfindin

---

### Post by penta666 on 2011-02-08
Thank's I try installing KDE on Ubuntu 10.10 (08.02.2011). 
Let's see... is it help or not.

---

### Post by penta666 on 2011-02-14
Log out today again :( :( :(

---

### Post by hobbestec on 2011-02-18
This xserver logout happens to me in Ubuntu 10.10 with a Core i5 with integrated video.  Firefox will crash on some pages but not others.  But I can always duplicate it by going to specific pages, and they are very plain webpages, no flash or java.   I just switched to Google Chrome for now that does not crash on those pages, but I would like to use Firefox more often.

---

### Post by penta666 on 2011-02-22
Thanks [hobbestec]("http://www.uluga.ubuntuforums.org/member.php?u=18243") for answer, but I'm not using firefox, I'm using chrome, but it apears again and again :(. Now I'm upgrade to 11.04 alpha1, using since today, hopefull that bug fixed :( :)

---

### Post by penta666 on 2011-03-02
Today my Ubuntu 11.04 log off again :( :( :(. BUG DIDN'T FIXED. :( Ubuntu devs please fix it. Say if anything I can do , or what you need to know.

---

### Post by alfonso78 on 2011-03-13
Hi,

I have the same issue with 10.10

can you check your /var/log/syslog after the bug happens and see if you have the same error described in this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709642](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709642)
acpid: client XXX[0:0] has disconnected

the best way to check (if you have two PCs) is to ssh into your box from an other PC and keep an eye on syslog (sudo tail -f /var/log/syslog) and go check the ssh window after the bug happens.

I think registering to the bug  on launchpad to show it affects many people might help.

---

