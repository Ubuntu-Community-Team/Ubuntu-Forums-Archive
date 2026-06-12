---
title: "Firefox 3 Endless Constant Random Crashing"
date: 2008-08-10
forum: General Help
---

### Post by aidave on 2008-08-10
Firefox has been crashing so much lately, its ridiculous.

It will just be sitting there.
Crash.

crash
crash
crash

Anybody else getting this?
Is it noscript or firebug or something?

---

### Post by ilovelinux33467 on 2008-08-10
Try reinstalling firefox

First Uninstall it:
```
sudo apt-get remove firefox-3.0
```

Then Install it again:
```
sudo apt-get install firefox-3.0
```

---

### Post by aidave on 2008-08-10
Thanks for the suggestion.

I tried, yet it is still crashing spontaneously, even long after a simple website has been open and is just sitting there.  Google home page, or this, for example.

I also disabled all add ons.

---

### Post by aidave on 2008-08-10
Are there any crash logs for firefox, to check?

---

### Post by aidave on 2008-08-10
bump

---

### Post by aidave on 2008-08-11
bump

this endless crashing is getting ridiculous

please help

is there a way to downgrade firefox to a previous ubuntu update?

---

### Post by gordohumphrey on 2008-08-11
Not only does firefox crash randomly for me, every web browser i've tried does


:confused:

---

### Post by aidave on 2008-08-11
Fair enough, but Firefox only stays open for 10-90 seconds at a time

---

### Post by aidave on 2008-08-11
I think it may be adblock plus.

---

### Post by mkvnmtr on 2008-08-11
I'm running Firefox 3 on Hardy and it seems stable, no crashes. When I first installed 8.04 it seemed buggy but I updated and use ad block, no flash and no script and it seems ok. But I have to say just ok, not good. I could not get it to install on Mac OSX 10.3.9 on my other partition still on the old Firefox. It doesn't seem any better, just ok. I liked Camino better.

---

### Post by fragos on 2008-08-11
Eliminate extensions one at a time to see if your problem lies there. I have no problems. Myt extesion list is:

Adblock Plus
Autofill Forms
Bandwidth Meter and Diagnostics
Firebug
FireFTP
FireFTP button
Foxmarks Bookmark Synchronizer
Total Validator
Ubuntu Firefox Modifications
WikiLook

---

### Post by starcannon on 2008-08-11
Firefox 2 is available in the Synaptic Package Manager.

System->Administration->Synaptic Package Manager

I will note that: 
**Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1**
has been working flawlessly for me though.

---

### Post by dacorr on 2008-08-11
move to opera :)

---

### Post by aidave on 2008-08-14
Upon even further investigation, it looks like "MSN.com" is crashing Firefox.

"msn.com" is allowed by default with NoScript.

However after disabling it, the crashes stopped.  I think it is the MSN ads crashing Firefox.

See this page: [http://health.msn.com/health-topics/articlepage.aspx?cp-documentid=100205363](http://health.msn.com/health-topics/articlepage.aspx?cp-documentid=100205363)
Just scroll down and it will crash.

---

### Post by psylonius on 2008-08-14
I have been having the exact same problem as the original post and it is driving me crazy. I have to completely reboot my computer again before I can start using firefox without it crashing every few seconds. It seems like the longer I leave my computer on the more unstable firefox is. (And no, it's not a heat related issue). The most frustrating thing is that it is totally random. Sometimes I can go for a really long time with no problems at all and then other times firefox will just keep crashing every 10 to 20 seconds. And like the original poster said, I could just open the browser to the start page (google) and not touch anything and it will crash or if it's open to a webpage and just sitting there for a while with no activity (i.e. not scrolling the page or moving my mouse over any links) because I'm reading what's on the page, it will just crash for no reason. I thought I was the only one having this problem and am relieved to know that others are having the same issues. Now we just need to figure out how to solve it.

---

### Post by CrusaderAD on 2008-08-14
I had this EXACT same problem. I had updated to Firefox 3.0 and had install a bunch of video software (codecs, players, etc). Then Firefox started to crash randomly. I uninstalled a the extra video codecs and removed/installed firefox again. Now it works fine. I'm not sure, but I think certain codecs play with flash websites and cause firefox to act up. Strange.

---

### Post by psylonius on 2008-08-14
I just came across this [http://ubuntuforums.org/showthread.php?t=764950&highlight=firefox+keeps+crashing]("http://ubuntuforums.org/showthread.php?t=764950&highlight=firefox+keeps+crashing") at the bottom of the page. Has anyone else tried this to see if it works for them as well?

---

### Post by aidave on 2008-08-14
I did try the SCIM removal, but it didnt solve the crashing.

I have currently:
AdBlock
NoScript
DuplicateTab
TabClickingOptions
UbuntuFirefoxModifications

I disabled msn.com in Noscript and now it isnt crashing.
That is totally wierd and makes no sense though.
Because google.ca would crash before, and it doesnt refer to msn.com.

---

### Post by aidave on 2008-08-14
> **psylonius said:**
> I have been having the exact same problem as the original post and it is driving me crazy. I have to completely reboot my computer again before I can start using firefox without it crashing every few seconds. It seems like the longer I leave my computer on the more unstable firefox is. (And no, it's not a heat related issue). The most frustrating thing is that it is totally random. Sometimes I can go for a really long time with no problems at all and then other times firefox will just keep crashing every 10 to 20 seconds. And like the original poster said, I could just open the browser to the start page (google) and not touch anything and it will crash or if it's open to a webpage and just sitting there for a while with no activity (i.e. not scrolling the page or moving my mouse over any links) because I'm reading what's on the page, it will just crash for no reason. I thought I was the only one having this problem and am relieved to know that others are having the same issues. Now we just need to figure out how to solve it.

Yes this is what I was/am experiencing, for whatever reason, the Noscript msn.com block has fixed it.  At least it hasnt crashed since I set that.

---

### Post by fragos on 2008-08-14
Don't forget what company has MSN. I just tried msn.com and no crash. It wouldn't allow me to see Olympic video because of my Linux OS.

---

### Post by psylonius on 2008-08-14
> **fragos said:**
> Don't forget what company has MSN. I just tried msn.com and no crash. It wouldn't allow me to see Olympic video because of my Linux OS.

I don't crash on msn.com either so the msn test link provided above worked for me with no problem also.

However the SCIM removal 'seems' to be working for me, but it has only been a short time so can't really say for sure until a couple days go by at least.

I too suspected it might be adblock plus or noscript but since others I believe have disabled those plugins and were still crashing I guess it is something else.

If I get anymore crashes since I've done the SCIM removal then I think I may uninstall miro tv which I use to aggregate my video podcasts and see if that might help. (Not sure if firefox started crashing more often after I started using miro or not or if it was one of the latest automatic system updates)

---

### Post by RheaHS on 2008-08-14
Was a flash stabiliser plugin in the repositories that caused mine to crash. It's stopped now I removed it. I can't for the life of me remember what it's called though.

---

### Post by psylonius on 2008-08-14
OK. I'm now starting to think that this is actually a Firefox 3 problem in general as I am now seeing the same type of problems on a completely different machine running a completely different operating system. My computer that is running Windows 2000 Professional and has never ever given me any problems with firefox is doing the same thing. This is the error msg that comes up when it crashes and also immediately when I try and restart firefox:

-----
Firefox had a problem and crashed. We'll try to restore your tabs and windows when it restarts.

Unfortunately the crash reporter is unable to submit a crash report.

Details: The application did not leave a crash dump file.
-----

So being that it's happening on a completely separate machine and Operating system that is the staple of stability of all my computers (and one that's been powered off for the past few days incidentally) only leads me to believe that it's the latest Firefox release that's the problem.

Although like I've said before, doing the SCIM removal on my ubuntu box so far seems to be working. But less than half a day's testing isn't really conclusive.

I'm really at a loss now.:confused:

---

### Post by CrusaderAD on 2008-08-15
This may sound dumb. But perhaps your network is infected with some sort of virus or spyware? I've removed bugs that can cause these issues. I would suggest running a few programs on your windows box like spybot, adware, avg. Then again, your linux box should be fine since it's not as likely to catch a cold.

---

### Post by psylonius on 2008-08-15
> **raptormanad said:**
> This may sound dumb. But perhaps your network is infected with some sort of virus or spyware? I've removed bugs that can cause these issues. I would suggest running a few programs on your windows box like spybot, adware, avg. Then again, your linux box should be fine since it's not as likely to catch a cold.

No. It's not a virus or spyware. I'm very careful & check for that sort of stuff religiously every day including using the programs you've mention and more. Also, the computers are on different networks with different routers & different ISP's and like I said the windows box was powered off for the past few days anyway and it's the only one on that router (non-WiFi). I'm in the IT business so I'm well aware of the problems malware or viruses can cause and the only difference I can recall with my windows box is the last update of firefox or it's plugins. I'll have to go with a stripped down very basic/generic firefox to be able to tell for sure. The original poster said things cleared up for him when he put msn.com into his noscript plugin so it may very well be an issue with that particular plugin.

---

### Post by psylonius on 2008-08-15
I just remembered and forgot to mention that Miro is a program that is installed on both my ubuntu box & windows box and I recall them mentioning a an incompatibility issue with a java plugin for firefox in ubuntu. But supposedly it only sometimes crashes miro and not firefox. Though I've never had that problem on my machine and still shouldn't be an issue on the windows machine. But I'll have to uninstall it and see what happens. And no one else having firefox problems has mentioned that they use miro so I don't know. I hate backtracking to try & find the root cause of a problem.

---

### Post by heykev on 2008-08-15
Just a "me too" post.  Firefox 3.0.1 on Ubuntu 8.04 is crashing frequently for me regardless of the add-on config or currently-displayed content.  I can often perform an action without problem and then perform that same action again and it crashes.

There's a lot of chatter about this everywhere -- not just in this forum -- so I'm hopeful that it's a priority issue for Mozilla.

Got a chuckle just now when Firefox crashed while I was viewing mozilla.com's list of known issues for Firefox 3.0.1.

---

### Post by psylonius on 2008-08-15
Well, I think I'm finally zeroing in on my problem. As I mentioned before, when I did the SCIM Revomal, firefox seemed to function properly again on my ubuntu box. However, I just started up miro to get my latest video podcasts and noticed that no new podcasts downloaded and I couldn't click on any of my channels or my library or anything for that matter in the left hand column. Though browsing in the miro web interface and going through the menus and minimizing, moving the window, etc. all worked but I couldn't even close the program. Had to kill all associated processes for it. Since removing the SCIM stuff is the only thing that I changed, I decided to reinstall it to see if miro would work again and low and behold it did. But that also immediately started firefox crashing ridiculously again. To the point of complete unusability. (within 20 sec of startups)

So once again back to synaptic package manager to remove SCIM and also Miro this time and so far all is well again with firefox. If the next few days continue to be crash free then I'll just have to find a different way to aggregate my podcasts and since I have no need for Chinese or special foreign characters, hope that no other programs need to hook into SCIM. Keeping my fingers crossed....

---

### Post by aidave on 2008-08-17
Whats miro and SCIM?  I havent used either of them.

Is your firefox still crashing?
Mine seems fine now.

---

### Post by wfp on 2008-08-17
Firefox has been crashing for me also, and it's random. It seems to crash more on flash sites or on certain sites that i am streaming video. It's just random thou so it's hard to pin down the problem.  I have the new flash 10 installed now for 2 days and it has not crashed, but i also have flash block installed. And have not been streaming much video either.

---

### Post by munshi on 2008-08-17
well i have tried removing SCIM from the synaptics package manager but this hasnt prevented my firefox from crashing

---

### Post by Ric_NYC on 2008-08-22
It seems like nobody cares about those crashes...

My question is: Is there another good browser that doesn't crash all the time?

Maybe if we start using another browser the developers of FF start to care about that bug.

---

### Post by fragos on 2008-08-22
Try epiphany it's faster and stable. It will find plugins like flash that you already installed for firefox. There are some extensions like ADblock but nothing like the number firefox has.

---

### Post by munshi on 2008-09-28
just came back from the IRC channel and there bobertdos recommended removing all flash packages and installing the nonfree again and it seems to do mircales.try it

---

### Post by Amarsingh0793 on 2008-09-28
You know... if you are having problems with Firefox 3, you can always get Firefox 2 from the repos (as a temporary measure)

---

### Post by gjoellee on 2008-09-28
firefox doesn't crash in Intrepid like it does in Hardy:D

---

### Post by KA3VVB on 2008-11-01
I'm a newbie having the same problems as most of the other people posting in this thread. I'm lucky if I get 2 mouse clicks into a Firefox session before it crashes. I tried simply exiting from SCIM, (not uninstalling), and then restarting Firefox, and (fingers crossed) Firefox hasn't crashed since. However, this is NOT a reasonable solution or viable workaround. I do 80 percent of my work in Japanese, and can't work without SCIM, or some other IME. You can't search if you can't input the search terms. Does anyone know if this problem is being worked on by the folks at Firefox or SCIM?
*[COLOR="DarkSlateGray"]Using Ubuntu 7.10 on a new Dell M1330, with Firefox 2.0.0.17[/COLOR]*

---

### Post by michaelzap on 2008-11-01
+1

Driving me nuts! Firefox was a bit unstable in Hardy, but since I upgraded to Intrepid last night it's been downright useless. I've uninstalled SCIM, Miro, and Flash (then reinstalled the adobe Flash 10 via Synaptic) and tried launching without add-ons but it's not much (if any) better.

This is the one app that I absolutely need to work, so I'm a little bit stressed...

---

### Post by michaelzap on 2008-11-02
OK this is really a critical issue for me. Firefox crashes on me **constantly** - so often that I can't possibly do anything with it. It seems to be mostly triggered by sites with Flash in them, but I'm not positive that's the cause (right now it's working on the ubuntuforums.org site at least).

Things I've tried:
[LIST]
[*]uninstalling SCIM and Miro
[*]uninstalling Flash Player (including deleting the one in my .mozilla folder) and reinstalling it via Synaptic (tried the nonfree and adobe versions)
[*]uninstalling Flash and not reinstalling it
[*]launching Firefox in Safe Mode with no add-ons
[*]renaming my .mozilla folder and launching Firefox fresh
[*]renaming my .fonts folder so those are eliminated as a variable
[*]turning off all visual effects
[*]messing with my PulseAudio settings a bit
[*]adding export XLIB_SKIP_ARGB_VISUALS=1 to the usr/bin/firefox script that I heard solved the issue for some folks
[/LIST]

None of this has helped in the least. It still crashes constantly and I can't get any work done. And it's actually not Firefox that's the problem, since **Opera also crashes just as frequently!**

At this rate the only way I'm going to be able to do anything is to run Internet Explorer in a virtual machine (how ridiculous is that?).

Anyone have any suggestions as to what I can do to resolve this?!?

---

### Post by fragos on 2008-11-02
I switched to epiphany which integrates completely with Gnome. It's available with Gecko rendering like Firefox or Webkit like Safari. It has fewer extensions but is noticably faster Firefox. I recommend you try it. Also running any application from a terminal window will provide more information about problems than when initiated with the GUI. It still comes up in the GUI environment but leaves the terminal window open for detailed error messages.

---

### Post by caro on 2008-11-02
I had a similar problem with FF3 after upgrading to Hardy.  FF would randomly crash on sites with flash, video, etc.  After I uninstalled libflashsupport, the problem completely went away.  No problem with Intrepid either.

---

### Post by Flywaver on 2008-11-02
I use Kubuntu 8.10 with Firefox 3.0.1, Flash is not even installed and FF keeps on crashing, even on this site lol! 

Anyone tried 3.1 Beta? 
I remember on Ubuntu 8.10 RC the latest version of FF was running fine, never crashing! :(

Cheers!

---

### Post by michaelzap on 2008-11-03
OK so I may be a bit closer to figuring this out...

For most of the day Firefox was working pretty well (it only crashed once). Then tonight I launched Amarok and it couldn't find any output engines so I couldn't play any music. I had set all of the output sources to Autodetect in the Sound Control Panel yesterday, and I hadn't tried to play any sounds until now.

So I set them back to PulseAudio and restarted. Now Amarok works fine, but Firefox is crashing like mad again. So it seems as if this problem is audio-related, and now I just have to figure out how to fix it...

---

### Post by Flywaver on 2008-11-03
Ok for some odd reason, I completely removed Firefox 3.0.3, rebooted, reinstalled the Dev edition and it works like a charm! :)

Cheers!

---

### Post by BetterSense on 2008-11-03
another 'me too'

[http://ubuntuforums.org/showthread.php?t=969952](http://ubuntuforums.org/showthread.php?t=969952)

---

### Post by michaelzap on 2008-11-04
> **michaelzap said:**
> OK so I may be a bit closer to figuring this out...


I still haven't been able to resolve this, and my system is useless without being able to keep a browser running reliably. WTF can I do to frigging fix this?!? I'm really, really frustrated right now...

---

### Post by fragos on 2008-11-04
FF 3 is working fine for me but when I tired FF 2 crashes I changed to Epiphany and waited for FF 3 to come out. FF has more add-ons but Epiphany integrated much better with the Gnome environment than FF and is much faster. I recently decided to back to Epiphany even though FF 3 was a major improvement over 2. With Ubuntu 8.10, Epiphany defaults to the same Gecko engine as FF but can be installed with webkit which is used by Safari and now Google Chrome.

---

### Post by michaelzap on 2008-11-05
Still crashing constantly. I upgraded to Firefox 3.0.4 from Mediabuntu and that made no difference. And Epiphany crashes just as often as Firefox and Opera, so it's not a specific browser issue per se anyway.

---

### Post by FlappySocks on 2008-11-05
My Firefox would randomly crash, although most frequently on my home page.
Now it crashes all the time.
I tried Epiphany (Gecko) wich is the same.
Epiphany (Webkit) doesn't crash, but it's hoplessly slow at times
Opera crashes in the same way.
It doesn't seem to be rated to any plugin.  Maybe a font issue? :confused:

---

### Post by michaelzap on 2008-11-05
> **FlappySocks said:**
> 
It doesn't seem to be rated to any plugin.  Maybe a font issue? :confused:

I've renamed my .fonts folder trying to eliminate that variable, and my browsers still crash just as frequently (constantly).

---

### Post by martinbriscoe on 2008-11-07
For me I think it was the upgrade to 8.10 that brought this to my attention. But now ff is effectively useless. will try the flash ideas, have completely reinstalled ff from the repos but no difference. This is a major problem for Ubuntu. A browser has to be the most important program for many people - this need to be addressed urgently. I wonder if other distros are reporting the same.

Epiphany works fine and fast for me. I'll stick with that until a solution is found.

Edit>
Following the responses earlier in this thread I have disabled shockwave flash 9.0 r124 (goto>Tools>Add-ons)

and for the last 10 mins I havent been able to get a crash and have revisted all the sites including gmail that were giving me problems before - fingers crossed. 

Thanks for all the advice

M

---

### Post by michaelzap on 2008-11-07
> **martinbriscoe said:**
> 
Following the responses earlier in this thread I have disabled shockwave flash 9.0 r124 (goto>Tools>Add-ons)


That's odd. I thought that Ibex automatically updated Flash to 10.0.r12. That's what I have (installed via Synaptic).

I still get crashes constantly (at least 500 today!). It's unbelievably frustrating, and so far I can't figure it out. I may just reformat and reinstall from scratch, but I didn't want to spend all that time and I'm not positive that it will actually help (downloading the live CD now to see if it crashes as much from that).

---

### Post by FlappySocks on 2008-11-07
Dont get too excited.  I tried the Flash thing a few days ago, and it made no difference.

Yesterday, for some reason, I didn't have a single crash for 3 hours, and just when I declared it fixed, it started crashing again.](*,)

---

### Post by michaelzap on 2008-11-07
> **FlappySocks said:**
> Yesterday, for some reason, I didn't have a single crash for 3 hours, and just when I declared it fixed, it started crashing again.](*,)

I don't know if I've gone three hours, but every time I think it's fixed it bites me on the *** like this also!

I'm not sure it has anything to do with Flash. Today I had six tabs open, all of which I was working on for a website and none of them had any Flash in them. Firefox would crash, and then when I would restore the session (so as not to have to start everything over), it would crash again. On the fifth or tenth time I restored the session it would just work as if nothing were wrong and stay that way for an indeterminate period of time.

It seems to me to be page loads (or content loads from different URLs on the same page) that crash it, not specifically Flash. Dunno why that would be, but I remember when the Firefox 3 beta was being tested the phishing filter could crash the browser. Except that this bug happens in every browser for me...

---

### Post by FlappySocks on 2008-11-07
I think it's Java myself, or maybe something to do with image rendering.
All browsers on my system crash or run very slow. Gecko/Webkit/Opera.

---

### Post by teaker1s on 2008-11-07
May be of interest my htpc intrepid ibex ibex with choice of Gnome/kde/xfce4 at login.

If I run a kde session then firefox plays flash flawlessly-flashplugin non free.
Maybe for those desperate for youtube and have the space consider installing an alternate desktop for flash viewing until there is a fix for flash in gnome.

Looking for ages at bug reports I've yet to nail the cause and swfdec suffers crashes with gnome too.


:confused:

---

### Post by martinbriscoe on 2008-11-08
My Shockwave plugin has something to do with this. With this plug in disabled ff has been perfect for 24 hrs. as soon as plugin enabled again It crashes within 30 secs. The crash was experienced by visiting a site called prime location. with shockwave disabled this site runs fine.

But thinking thru this I have shockwave 9 something. whereas my eeepc which I am using to type this has v10.0.0 so Id better upgrade first and see what happens. 

>>
OK -uploaded v10.0 by doing: <sudo apt-get install flashplugin-nonfree> as mentioned at: [http://queleimporta.com/installing-flash-10-on-intrepid-ubuntu-810-64-bits/en/](http://queleimporta.com/installing-flash-10-on-intrepid-ubuntu-810-64-bits/en/)

everything seems fine initially bbc and utube video/audio is good, no early crashes - I must have a 64 bit pc this makes me wonder if there are just a number of problems with ff on ibex but they all produce similar results. 

>>
Every cloud has a sliver lining - the epiphany browser looks interesting -significantly faster than ff -plays audio/video out the box. I might run with this for a while.

Martin

---

### Post by michaelzap on 2008-11-08
> **martinbriscoe said:**
> My Shockwave plugin has something to do with this. With this plug in disabled ff has been perfect for 24 hrs. as soon as plugin enabled again It crashes within 30 secs. The crash was experienced by visiting a site called prime location. with shockwave disabled this site runs fine.

I've tried disabling that plugin in Firefox, and it didn't work for me. In my case all browsers (FF, Opera, and Epiphany) crash equally, so it's not a Firefox-specific issue at all. I wonder what hardware those of us who have this problem have in common (I have an Intel Core 2 Duo with an nVidia 6200 video card, and I'm running 32-bit Ibex).

---

### Post by martinbriscoe on 2008-11-08
I have:

Ubuntu 8.10 (2.6.27-7-generic)
AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
GeForce 8300 GS
FF 3.0.3



Martin

---

### Post by michaelzap on 2008-11-08
> **martinbriscoe said:**
> I have:

Ubuntu 8.10 (2.6.27-7-generic)
AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
GeForce 8300 GS
FF 3.0.3


Alright so that's two GeForce cards. What version of the nVidia driver are you using? I have 177.80.

---

### Post by fragos on 2008-11-08
I don't have a problem, Sempron 2800+, FX5200, Ibex and one thing different from the last couple of posters. My Nvidia driver is 173.14.12

---

### Post by michaelzap on 2008-11-08
> **fragos said:**
> I don't have a problem, Sempron 2800+, FX5200, Ibex and one thing different from the last couple of posters. My Nvidia driver is 173.14.12

Rats. I had hope that the 173 driver might solve it for me, but no luck. Firefox crashes just as much with it as it does with version 177.

---

### Post by martinbriscoe on 2008-11-09
> **michaelzap said:**
> Rats. I had hope that the 173 driver might solve it for me, but no luck. Firefox crashes just as much with it as it does with version 177.

I have 177.8 & no more crashes for now. M

---

### Post by [Neurotic] on 2008-11-09
I've also had bad stability issues with Firefox in Ibex - ever since late Alphas, and all through the Beta period as well, and they never got resolved.

There was no crash logs, just an (Core Dumped) message in the debug console.

Its about the only thing in Ibex I've seen that is quite bad.

---

### Post by michaelzap on 2008-11-10
> **martinbriscoe said:**
> I have 177.8 & no more crashes for now. M

I had the 177.80 nVidia driver to begin with, so that didn't help. I also tried installing KDE to see if browsers are as unstable in it as in Gnome (they are, although I did get to see how purty KDE 4 is). The one way that I found that Firefox didn't crash on me constantly was running Ubuntu from the Live CD.

So I'm now in the process of reformatting and reinstalling Ibex from scratch. So far it seems to be working as it should. In the end this may be yet another cautionary tale of why upgrading is bad and fresh installs are good (it shouldn't be that way, but at this point I just want a working browser so I'll accept it).

---

### Post by michaelzap on 2008-11-10
> **michaelzap said:**
> So I'm now in the process of reformatting and reinstalling Ibex from scratch. So far it seems to be working as it should. In the end this may be yet another cautionary tale of why upgrading is bad and fresh installs are good (it shouldn't be that way, but at this point I just want a working browser so I'll accept it).

Indeed a fresh Ibex install seems to have fixed the problem. I now have pretty much all my programs installed and configs and files moved over, and so far Firefox is still behaving. Did everyone who experienced this problem upgrade from Hardy, or did some of you have this issue after a fresh install of Ibex?

---

### Post by michaelzap on 2008-11-11
> **michaelzap said:**
> Indeed a fresh Ibex install seems to have fixed the problem. I now have pretty much all my programs installed and configs and files moved over, and so far Firefox is still behaving. Did everyone who experienced this problem upgrade from Hardy, or did some of you have this issue after a fresh install of Ibex?

24 hours later, Firefox has yet to crash even once. The other thing is that it loads pages MUCH faster than it did previously. Starting with Hardy (which I installed clean), I noticed that page loads often stalled out on domain name lookups and took much longer than they should have, so this is a major improvement!

---

### Post by cjlindem on 2008-11-12
The instructions in this bug report seem to have fixed it for me.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/286119]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/286119")

Basically, uninstall winbind package if you have it installed.

---

### Post by psyke83 on 2008-11-12
The problem that users are experiencing is most likely caused by Flash and the libflashsupport library. There is a very nasty bug in libflashsupport that causes instability in Firefox (see bug [192888]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888") for details).

The solution:

Intrepid users shouldn't need to do anything, as it's fixed officially. However, if you have manually installed "libflashsupport", then remove this package.

Hardy users: you need to upgrade Flash, some ALSA libraries, reconfigure PulseAudio, and 64bit users need extra 32-bit libraries and nspluginwrapper 1.1.2. There is no official fix (and the changes are too intrusive for a LTS release). [This]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") guide provides the unofficial fix (and won't interfere with future upgrades).

---

### Post by Mamono on 2008-11-14
I am experiencing the same problems on two fresh Intrepid installs.  I have been running Kubuntu on my desktop at home since Gutsy and have not had a single problem.  I am currently on Hardy with KDE 3 and still have no problems.

However, on my work computer I just installed a fresh clean Intrepid (originally had XP on it) and that was when I first started experiencing these crashes.  I then recently installed Kubuntu Intrepid on my wife's laptop and her Friefox also crashes constantly.  

I know my work computer has an ATI X1300 and I have the restricted drivers installed.  Both systems are Intel Dual Cores.  I don't think this is a video driver issue.

The one thing that they both have in common is that I've installed the 64-bit version.  My home desktop is still running 32-bit.  I'm wondering if this has something to do with the 64-bit version of K/Ubunutu.  Is anyone experiencing this problem running 32-bit?

---

### Post by michaelzap on 2008-11-14
> **psyke83 said:**
> The problem that users are experiencing is most likely caused by Flash and the libflashsupport library.

I'm not convinced this was my issue. I completely removed all Flash from my machine (32-bit Intrepid upgraded from Hardy) and still had constant crashes. Although I have an Intel Core 2 Duo (not an AMD CPU), I suspect that winbind may have been the cause of my problems, since I had installed it before upgrading.

> **Mamono said:**
> Is anyone experiencing this problem running 32-bit?

I practically couldn't use any browser at all after upgrading to 32-bit Intrepid from Hardy, and I also have a Core 2 Duo CPU. A fresh installation worked fine, however (read my previous posts for everything else I tried first). If you have winbind installed, you might try removing that and seeing if it fixes the crashing (I didn't try that before I started over from scratch).

---

### Post by Mamono on 2008-11-14
> **michaelzap said:**
> If you have winbind installed, you might try removing that and seeing if it fixes the crashing (I didn't try that before I started over from scratch).

I just checked and, as this is a fresh install, I do not have winbind installed.  Also, as some of the previous posters mentioned trying to remove SCIM I checked and that is not installed, either.  I would love to remove a package to try and resolve this but it is just about as clean as you can get.  Here is what I've installed:

Codeweavers Crossover Pro
kubuntu-restricted-extras
Quanta+
ATI restricted drivers

Other than the routine updates, I haven't installed anything else.

---

### Post by Mamono on 2008-11-14
Oh yeah, I also installed ncpfs.  I also suppose it is worth mentioning that I have the following Firefox add-ins installed:

Extensions:

Adblock Plus
Adblock Filterset.G Updater
Ubuntu Firefox Modifications
Web Developer

Plugins:

Default plugin
Demo Print Plugin for unix/linux
IcedTea Web Browser Plugin
Shockwave Flash (10.0 r12)

---

### Post by Mamono on 2008-11-14
Ok, just another update.  I deleted my ~/.mozilla directory and I crashed within 15 minutes.  So it does not appear to be the fault of any of the add-ons.  I just enabled the backports in my apt repos so let's see if getting an updated version of something might help.

---

### Post by LcKayaker on 2008-11-15
> **cjlindem said:**
> The instructions in this bug report seem to have fixed it for me.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/286119]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/286119")

Basically, uninstall winbind package if you have it installed.

Thank you, thank you.  After chasing through Java incompatibilities, Flash suggestions, and complete reload of Firefox after deleting .Mozilla, the solution for me was removing Samba/winbind.

---

### Post by davidsampson on 2008-11-16
I am having the same problem.

Strangely, there is one page I can never get to load.  Most pages do not work once, and then for awhile after that, but eventually they start working again.  When I try to go to the wikipedia page for 311, it *always* crashes.  Not only that, but epiphany and galeon also crash on that page, otherwise they are stable.  I was able to load it with seamonkey.  Can anyone reproduce this problem?

---

### Post by OverlordManny on 2008-11-20
Well, removing winbind was a great solution to my firefox problem. Unfortunately getting my network drive (on a windows server) to work requires winbind. I'm not sure if I want to have to pick between the two.

---

### Post by michaelzap on 2008-11-20
> **OverlordManny said:**
> Well, removing winbind was a great solution to my firefox problem. Unfortunately getting my network drive (on a windows server) to work requires winbind. I'm not sure if I want to have to pick between the two.

Give your network drive a static ip (using your router or the drive's configuration utility) and then mount it using the ip address. That's what I do for my network drives. I prefer doing it that way anyway, since Samba seems to give me grief if I don't.

---

### Post by ugkbunb on 2008-12-12
I have been struggling to get any browser stable in xfce/ubuntu 8.10 32-bit setup... it is really the only thing holding me back from wiping my winblows partion clean. It would happen 99% on youtube/video/flash websites but somtimes just randomly. I tried gNash/swf-dec(sp?)/flash9/10 with/without nspluginwrapper and/or libflashsupport... nothing seemed to help. I tried Firefox/Midori/Epiphany/Dillo all were affected... This is what I did to fix it...

booted up into gnome... went to Sound pref set everything back to ALSA defaults (was using pulseaudio)... set my default sound card back to my MOBO's instead of pulseaudio. 

Low and behold I can browse youtube just fine now with just flash 10 removed both nspluginwrapper or libflashsupport. If I enable pulseaudio daemon firefox begins crashing immediately.

EDIT:Upon more digging I decided to reformat... a fresh in stall of 64-bit Xubuntu fixed everything. I am now able to use pulseaudio + 64bit alpha Flash10. I installed ubuntu-restricted-extras and noticed it installed nspluginwrapper and Flash 9. I unistalled them both but now I have a bunch of packages I no longer need (I assume because nspluginwrapper is no longer available).. I removed them with autoremove but was wondering will removing those libs effect my ability to play various types of media?

---

### Post by wimpelmeesje on 2009-03-07
I can confirm that (in my case at least) the problem is the winbind package. The crashes started when I first installed the package and disappeared when I removed it. A couple of days ago I updated my firefox to the latest version and I installed winbind again. The random crashes were back as before so now it's uninstalled once more and my firefox is crash free.

The crashes always occur when a page was loading, maybe that would help someone trying to find a fix other than removing winbind.

---

