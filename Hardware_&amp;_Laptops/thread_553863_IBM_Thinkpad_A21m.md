---
title: "IBM Thinkpad A21m"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by roxy99 on 2007-09-18
Hi I've recently successfully installed Xubuntu on this 700mhz, 128mb thinkpad and it seems to work fine.  My issue is that I am dissappointed by the somewhat slow respnosiveness.  I had always been under the impression that Linux and especially a lighter-weight distro like Xubuntu, is less bloated and snappier than Windows 2000.

Previosuly Windows 2000 was on this same laptop.  I admit that it was not that responsive with Win2K to begin with.  However that's after 3 years of use so naturally Win2K gets slower and slower with use (the way MS Windows tends to be with clogged up registry entries over time).

I imagine a fresh install of Win2K compared to a fresh XUbuntu install that Win2k wins in the resonsive interface category.  

For example, loading up firefox there is about a 2-3 sec delay before my google home page is displayed.  I'm not taking about internet bandwith (high speed connection)this is simply the application load time.  Open Office takes about 3-5 sec to load.  Its adequate performance but somehow I was expecting a little more snap.


How can I tweak XUbuntu to make it faster?  Are there background processes I can do without and if so how to disable them?

---

### Post by roxy99 on 2007-09-18
:)  As a follow up to my question, how important is the amount of RAM versus CPU mhz for XUbuntu performance?  I think RAM seems to be a big bottleneck so I was wondering with cheap ram prices it may be worth upgrading the ram to 256mb.  Will I notice a significant performance boost?

If I upgrade the RAM, do I have to tell Linux somehow how to optimize the RAM or does Linux do its own housekeeping automatically and use the RAM it's given.

Thanks in advance.  Great forum BTW  :)

---

### Post by roxy99 on 2007-09-19
bump

---

### Post by trippinnik on 2007-09-19
Well I'd have to say that the RAM is the most important factor.  However the two programs that you mentioned do tend to have slow start up times.  OO in particular.  You may want to try running some different programs as those are both very large.  For office appsin Xubuntu you can use Gnome office apps like Abi word since they are also built on Gtk.  The startup time will be much faster and more reposnisive once running.  You could also try Galeon instead of firefox, it's built using Gtk as well and uses the Gecko engine, so it's rendering of webpages is the same as firefoxes it's just runs lighter and doesn't have the extensions. 
You may also want to try an even lighter Window manager like fluxbox or Enlightenment.  I'm running on an old laptop too (an IBM X22) 733mhz but i upgraded to 640MB or ram and run KDE or GNOME quite well.

---

### Post by roxy99 on 2007-09-20
Thanks for the response.  Those lightweight apps sound interesting and  I'll definately look into them for my own education.  The thing is my wife is using this laptop and I don't want to water down the system too much.  It needs to offer Windows like user freindliness and features or she'll force me to put back win2k  OO os as close to MS Office as possible.  I'm on a crusade to convert her to the virtues of linux so I want her to be pleased with the experience.

I've heard about fluxbox but I've always been under the impression that these lightweight DE tend to be highly stipped down and may lack functionality.  For her sake the DE can't be too 'Geeky'

Your respnse confirmed my suspicion though: these apps are memory hogs and that linux craves memory but manages it well- the more memory you throw at it, the better it performs.

So I went ahead and updraded to 384mb (from 128 mb).  Now its running more like a PC from this millenium.  Apps load up reasonably well.  There is a HUGE performance boost when I upped from 128 to 384.   I'm tempted to go for 512mb (this laptops max)  - or is there no marginal performance boost from 384mb?

I'm tempted to install the full blown Gnome based Ubuntu given that I have  384mb and its running well now.  I guess I could be pushing my luck a bit.  Although you're running a circa 700mhz PIII like me so I guess it can handle Gnome quiet decently. Is it fair to say that Xubuntu on 384mb will run like Ubuntu on 512mb ?

Maybe I'll buy a faster IDE drive and put straight Ubuntu w/Gnome on that.  I'll keep the 10gb 4200rpm drive intact with XUbuntu and throw it in a drawer.

---

### Post by trippinnik on 2007-09-20
Should be fine.  I put Ubuntu on my wife's laptop and didn't bother to make it run lightweight stuff and she's got 700mhz p3 with only 256MB of ram.  I've been using kde recently (it seems a bit snappier on this machine and I was running a lot of KDE apps anyway.  You could try using kdecore instead of full Kubuntu as well here: [http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core).  You could also replace Metacity and make sure to stop all the services you don't need from starting up in the backgroun at boot.

---

