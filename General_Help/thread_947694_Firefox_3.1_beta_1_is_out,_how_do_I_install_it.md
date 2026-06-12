---
title: "Firefox 3.1 beta 1 is out, how do I install it?"
date: 2008-10-14
forum: General Help
---

### Post by stormtrooprdave on 2008-10-14
Firefox 3.1 beta is available for download from here:

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.1b1/]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.1b1/")

How do I install it to try it out?

---

### Post by mthei on 2008-10-14
Once you download, all you have to do is extract the tar.gz file (either by "tar xjf firefox-3.1" or by double-clicking on the on the file and then clicking and dragging the Firefox file inside), and then just run the Firefox binary inside.
If you want to remove the Firefox from Ubuntu's package manager and use the beta is up to you, but Ubuntu usually stays up to date with Firefox releases once they're made official.

---

### Post by dburnett77 on 2008-10-14
> **stormtrooprdave said:**
> Firefox 3.1 beta is available for download from here:

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.1b1/]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.1b1/")

How do I install it to try it out?

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

describe it.  Just unarchive it, and make sure like they say to have the required libraries.  Should be able to make a desktop icon for the unpacked file and put it on your desktop, or wherever you wish.

---

### Post by hyper_ch on 2008-10-14
is there any compelling reason why you need that?

---

### Post by stormtrooprdave on 2008-10-14
> **mthei said:**
> Once you download, all you have to do is extract the tar.gz file (either by "tar xjf firefox-3.1" or by double-clicking on the on the file and then clicking and dragging the Firefox file inside), and then just run the Firefox binary inside.
If you want to remove the Firefox from Ubuntu's package manager and use the beta is up to you, but Ubuntu usually stays up to date with Firefox releases once they're made official.

Nothing happens when I double click the binary file

---

### Post by scruff on 2008-10-14
> **hyper_ch said:**
> is there any compelling reason why you need that?

To check out the supposed 2x faster javascript engine? I used windows for 1 whole week just to check out Chrome and it was unREAL! I hadn't used windows for a week in something like 7 years if that tells you anything... The face that Firefox is headed in the same direction this quickly is exciting.

---

### Post by mikewhatever on 2008-10-14
> **hyper_ch said:**
> is there any compelling reason why you need that?

+1. I also think that if one is savvy enough to test beta software, he should, at least, be able to figure out how to install it. Otherwise, perhaps one is not as savvy as one might think.

---

### Post by scruff on 2008-10-14
> **mikewhatever said:**
> +1. I also think that if one is savvy enough to test beta software, he should, at least, be able to figure out how to install it. Otherwise, perhaps one is not as savvy as one might think.

[edit]Point taken. Although that should be where us more experienced users come in to assist with making new users more savvy :) [/edit]

I also just grabbed adobe's libflashplayer and dropped it into firefox/plugins. I went to copy my existing flashplayer and noticed it was flashplugin-alternative (never thought to check before, or test the two). Only been running it for 5 minutes so haven't had time to really tell the difference. But FF is def more responsive with javascript heavy pages.

---

### Post by hyper_ch on 2008-10-15
well, the problem is that most new users on linux are just versions freaks and need to obtain the latest version of anything, regardless whether it gives them some benefit. Due to the repository installation new users should first learn to stick with that and once they are confortable start compiling/install random stuff ;)

---

### Post by edmicman on 2008-10-15
I dunno....I've been using the prebeta Minefield versions on Windows at work for the past week or so and it did seem improved.  When 3.1b1 dropped yesterday I grabbed it for Windows, and it seems to respond faster on JS heavy pages, and looks to have fixed some stability problems that had started creeping up in the Minefield versions I'd been using.  I would love to upgrade my Hardy laptop at home with 3.1 and the newly released Flash 10 final (I've been using the beta on that, too, and the Flash performance was *much* better)

Since converting to Ubuntu full time when 8.04 came out, that's been one of those love/hate things I have with it.  On Windows, I tend to always be trying out the latest updates of my favorite programs that I use all the time.  Usually there are much-appreciated updates and fixes that I look forward to.  I appreciate that there is a central Ubuntu repository that will handle updates for me so I don't have to.  But I find myself frustrated a lot that the versions in the repos are so much behind on the packages I use a lot.  And in my experience working with software outside of the repos (Firefox is a good example) can be a PITA.  That there is two detailed walkthroughs on how to install Firefox outside of Synaptic and that it relies heavily on the command line is a testament IMO that something can be improved.  But that's just my $.02.

In either case, maybe I should investigate more on how to manually maintain the software I use.  Firefox, Filezilla, and Pidgin are the main programs that come to mind that are woefully out of date with the released versions.  And unless I misread something on the packages webpages, FF 3.1 isn't even slated to be included with 8.10, either.

---

### Post by sethvath on 2008-10-16
32bit firefox 3.1 works out of the box after extracting the tar file. For 64bit, you need to "getlibs libdbus-glib-1.so.2" to resolve one of the missing dependencies. 

Other than that minor issue in 64bit, everything seems to work great. 3.1 is slightly snappier than 3.03 and on any javascript heavy sites (read ajax-heavy) you'll appreciate the speed.

---

### Post by vikrant82 on 2008-10-17
Why not try : ```
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main
```

More on it : [http://www.tgdaily.com/content/view/39752/140/](http://www.tgdaily.com/content/view/39752/140/)
:)

---

### Post by vikrant82 on 2008-10-17
Well I just did some [ACID 3 ]("http://acid3.acidtests.org/")tests...

Opera 9.6 : 85
Firefox 2 : 53
Firefox 3.0.3 : 71

Firefox 3.1b : 89 <-- That's what we are talking about.

---

### Post by Rocktman2 on 2008-10-17
FF 3.1 Beta 1 is sooo much faster than 3.0-3.03 (on Window$ anyway). Since I've had good luck with most FF betas, I'm also trying it out (I was also a beta tester for a while).

I've been using FF since it was Phoenix 0.4 & the FF 3.x versions, so far, have been crappy & slow, IMHO. I haven't seen a version this bad since 0.9 (I think it was).

That said, I'll wait for FF 3.1 to either show up in the repository or be an auto D/L.

---

### Post by vikrant82 on 2008-10-17
> - JS speed gains: Mozilla claims JS speed gains of up to 40x thanks to an optimized engine called TraceMonkey. 

But this is disabled by default and can be enabled by setting  "javascript.options.jit.content" to "true" in about:config.

---

### Post by manuelg on 2008-10-17
> **vikrant82 said:**
> But this is disabled by default and can be enabled by setting  "javascript.options.jit.content" to "true" in about:config.

And one can also enable "javascript.options.jit.chrome" which will speed up your addons.

---

### Post by edmicman on 2008-10-17
Ok, so if I'm on 8.04 and want to run 3.1b1, what is the best way to do it?  It sounds like using the FirefoxNewVersion instructions are best, but the Ubuntzilla package sounds cleaner and easier - unfortunately there's nothing I see about 3.1 being part of that.  If I download and unarchive the files from mozilla, and put them in the /opt folder and run the firefox exe, is that going to hose up my existing installation?  It seems like I had problems before in trying to run firefox outside of the "standard" installation.

---

### Post by Rocktman2 on 2008-10-18
> **edmicman said:**
> Ok, so if I'm on 8.04 and want to run 3.1b1, what is the best way to do it?  It sounds like using the FirefoxNewVersion instructions are best, but the Ubuntzilla package sounds cleaner and easier - unfortunately there's nothing I see about 3.1 being part of that.  If I download and unarchive the files from mozilla, and put them in the /opt folder and run the firefox exe, is that going to hose up my existing installation?  It seems like I had problems before in trying to run firefox outside of the "standard" installation.

In order to run different versions of FF, they must be installed in separate directories & have separate profiles (you can migrate things like passwords & bookmarks, not extensions or themes). Then you have to use the -profilemanager parameter with both versions of FF so you can choose the correct profile that goes with each FF version.

---

### Post by dougfractal on 2008-10-19
```
sudo echo "activate sudo"
```

```
echo "deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install firefox-3.1
```

If you don't want to move you icons around and use firefox-3.1b1 as your main browser 

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /usr/bin/firefox-3.1 /usr/bin/firefox
```



If you whant to undo that change
```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

(edit: added rm, thanks to sethvath)

On your first run firefox-3.1 creates a new profile from your old 3.0.x profile, so it takes a bit of time, but it is so much better.

Install flash 10 from the intrepid repo as well. (works in hardy)

```
sudo apt-get remove libflashsupport
wget http://fr.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.12.36ubuntu1_i386.deb
sudo gdebi flashplugin-nonfree_10.0.12.36ubuntu1_i386.deb
```

---

### Post by gjoellee on 2008-10-19
I used this tutorial: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by jackinthefox on 2008-10-20
so its up and running but i cant watch flash videos... amd64 any ideas???

---

### Post by sethvath on 2008-10-20
> **dougfractal said:**
> ```
sudo echo "activate sudo"
```

```
echo "deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install firefox-3.1
```

If you don't want to move you icons around and use firefox-3.1b1 as your main browser 

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /usr/bin/firefox-3.1 /usr/bin/firefox
```



If you whant to undo that change

[COLOR="Blue"]Missing one step here
sudo rm /usr/bin/firefox[/COLOR]
```
sudo dpkg-divert --rename --remove /usr/bin/firefox
```
[COLOR="Blue"]Only after you remove the file can you do a dpkg-divert remove[/COLOR]
On your first run firefox-3.1 creates a new profile from your old 3.0.x profile, so it takes a bit of time, but it is so much better.

Install flash 10 from the intrepid repo as well. (works in hardy)

```
sudo apt-get remove libflashsupport
wget http://fr.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.12.36ubuntu1_i386.deb
sudo gdebi flashplugin-nonfree_10.0.12.36ubuntu1_i386.deb
```

Edited above in blue

---

### Post by duott on 2008-10-20
{edited} Fixed it. 

Everything is up and running now :)

---

### Post by kwalker1969 on 2008-10-25
> **mikewhatever said:**
> +1. I also think that if one is savvy enough to test beta software, he should, at least, be able to figure out how to install it. Otherwise, perhaps one is not as savvy as one might think.

Mike, I too was a MS Windows user b4 Migrating (due to MS Vista release - YUCK!). So I take offense to your remark! There is NO reason we (previous Windows users) can NOT be a BENEFICIAL Addition to Linux and BETA test NEW LINUX software... After all, I beta-tested Firefox (and other programs) on the Windows environment, thus PERHAPS I (and others) could suggest some improvements to LINUX software I/we have seen! Besides weren't we all, EVEN YOU, ONCE New to Linux and in the Same situation as far as installing and cofiguring etc????

That said, I wish there was a SIMPLE Universal installer for progarms not in .deb for but in .tar.gz2 or .rpm, that a Newbie, or whoever, could run in Konsole (terminal) like 'install' application, ie, 'install firefox3.1.b1.tar.gz2' that would invoke an unarchiver like ARK and install the excutable after it is unarchived. OR if each program creator released one in the archive for it's specific programs that too would help (like window programs do)!

I followed the above steps EXACTLY in Konsole (terminal) but the program started showed the version number being still '3.0.3' in "Help"-> "About" NOT '3.1 beta ?' (? being 1 or 2 or # of beta).

---

### Post by edmicman on 2008-10-26
IMO, it's not necessarily the packaging that makes trying out programs not in the repos confusing for beginner users.  I'm totally OK with expanding an archive to some folder, creating a shortcut to the binary from there, and running it from there.  Heck, in Windows I could create my own program files structure or subfolder off of c:\ if I needed to.  But what I run into with Ubuntu is not knowing where or how I should put whatever files I have downloaded for a program?  Do I put them in /opt/?  In /usr/bin?  In ~/bin/?  Where are the config files that personalize the program for me?  Are they in my home directory?  Are they in the same directory as the executable files?  Are they stored in a completely different path of settings?

And then you have cases where there's a global shortcut for some programs (i.e., dumping the Firefox beta somewhere, but when you run it it still runs the Synaptic installed version).  I think Pidgin works the same way with this.  

I'm sure it's just a matter of getting used to things and practice.  But I, too, have found some things difficult in my own transition.  I appreciate the repos maintaining my software updates and installations for me.  But when I was on Windows, there were a handful of programs that I used regularly that I always wanted to have the latest version of, and even try out betas for.  Luckily most of these programs would have updaters built into them, but I could always grab the installer from their websites and do it myself.  Now it seems I either need to hope they publish a .deb installer, or make it myself from source.  Or wait 6 months and hope some updated version will show up in the next release!

---

### Post by dmber on 2008-10-31
thanks guys!  working great so far.

i'm on an Eee PC 900 with 1 gig of RAM.  I had some pretty bad "greying out" issues with Ff 3.  Haven't had it yet with 3.1b2.  Thanks.

---

### Post by dmber on 2008-11-01
aaaand not so much anymore.  after adding those repos, i've gotten multiple "updates" from the regular update manager in the tray.  and now firefox ("Shiretoko") won't start.  At all.  I click it in AWN and it just spins for a while then stop spinning.

Is there a way I can find a LOG file or something to tell me what's up?

thanks.

---

### Post by vikrant82 on 2008-11-02
Yea, actually the repo versions (fta2,fta3) was broken for a while. It was because this file, /etc/gre.d/1.9.1b2pre.system.conf was not getting created properly..

There should have been new updates yesterday, with versions *.ft4 which fixes the issues.

So why not just try the following... 

```
sudo apt-get update
sudo dpkg --force-depends --purge xulrunner-1.9.1
sudo apt-get install -f
sudo apt-get install xulrunner-1.9.1
```

---

### Post by KhaaL on 2008-11-11
> **vikrant82 said:**
> Yea, actually the repo versions (fta2,fta3) was broken for a while. It was because this file, /etc/gre.d/1.9.1b2pre.system.conf was not getting created properly..

There should have been new updates yesterday, with versions *.ft4 which fixes the issues.

So why not just try the following... 

```
sudo apt-get update
sudo dpkg --force-depends --purge xulrunner-1.9.1
sudo apt-get install -f
sudo apt-get install xulrunner-1.9.1
```



This isnt working for me:

```

khaal@Xeraphim:~$ sudo apt-get update
Hit http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Get:1 http://archive.ubuntu.com intrepid Release.gpg [189B]                    
Ign http://archive.ubuntu.com intrepid/main Translation-en_US                  
Hit http://archive.canonical.com intrepid Release                              
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US            
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US              
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US            
Hit http://archive.ubuntu.com intrepid-updates Release.gpg                     
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US          
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US    
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US      
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US    
Hit http://archive.ubuntu.com intrepid-backports Release.gpg                   
Ign http://archive.ubuntu.com intrepid-backports/main Translation-en_US        
Ign http://archive.ubuntu.com intrepid-backports/restricted Translation-en_US  
Ign http://archive.ubuntu.com intrepid-backports/universe Translation-en_US    
Ign http://archive.ubuntu.com intrepid-backports/multiverse Translation-en_US  
Hit http://archive.ubuntu.com intrepid-security Release.gpg                    
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US         
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US   
Hit http://wine.budgetdedicated.com intrepid Release.gpg
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US
Get:2 http://archive.ubuntu.com intrepid-proposed Release.gpg [189B]
Ign http://archive.ubuntu.com intrepid-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-proposed/main Translation-en_US
Hit http://wine.budgetdedicated.com intrepid Release                           
Ign http://archive.ubuntu.com intrepid-proposed/multiverse Translation-en_US   
Hit http://archive.canonical.com intrepid/partner Packages                     
Ign http://archive.ubuntu.com intrepid-proposed/universe Translation-en_US
Get:3 http://archive.ubuntu.com intrepid Release [65.9kB]
Get:4 http://ppa.launchpad.net intrepid Release [27.6kB]               
Get:5 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Ign http://wine.budgetdedicated.com intrepid/main Packages                     
Get:6 http://ppa.launchpad.net intrepid Release [27.6kB]                  
Get:7 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://wine.budgetdedicated.com intrepid/main Packages                  
Ign http://ppa.launchpad.net intrepid/main Packages                         
Hit http://archive.ubuntu.com intrepid-updates Release
Hit http://archive.ubuntu.com intrepid-backports Release
Hit http://archive.ubuntu.com intrepid-security Release
Get:8 http://archive.ubuntu.com intrepid-proposed Release [48.9kB]
Ign http://ppa.launchpad.net intrepid/main Packages                          
Ign http://ppa.launchpad.net intrepid/main Packages                          
Ign http://ppa.launchpad.net hardy/main Packages                             
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages                 
Hit http://ppa.launchpad.net intrepid/main Packages                 
Get:9 http://archive.ubuntu.com intrepid/main Packages [1256kB]     
Hit http://ppa.launchpad.net intrepid/main Packages                        
Hit http://ppa.launchpad.net hardy/main Packages                           
Hit http://ppa.launchpad.net hardy/main Sources                             
Get:10 http://archive.ubuntu.com intrepid/restricted Packages [8408B]       
Get:11 http://archive.ubuntu.com intrepid/main Sources [505kB]
Get:12 http://archive.ubuntu.com intrepid/restricted Sources [3113B]
Get:13 http://archive.ubuntu.com intrepid/universe Packages [4542kB]
Get:14 http://archive.ubuntu.com intrepid/universe Sources [1981kB]
Get:15 http://archive.ubuntu.com intrepid/multiverse Packages [199kB]
Get:16 http://archive.ubuntu.com intrepid/multiverse Sources [95.8kB]
Hit http://archive.ubuntu.com intrepid-updates/main Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://archive.ubuntu.com intrepid-updates/main Sources
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://archive.ubuntu.com intrepid-updates/universe Packages
Hit http://archive.ubuntu.com intrepid-updates/universe Sources
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://archive.ubuntu.com intrepid-backports/main Packages
Hit http://archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://archive.ubuntu.com intrepid-backports/universe Packages
Hit http://archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://archive.ubuntu.com intrepid-security/main Packages
Hit http://archive.ubuntu.com intrepid-security/restricted Packages
Hit http://archive.ubuntu.com intrepid-security/main Sources
Hit http://archive.ubuntu.com intrepid-security/restricted Sources
Hit http://archive.ubuntu.com intrepid-security/universe Packages
Hit http://archive.ubuntu.com intrepid-security/universe Sources
Hit http://archive.ubuntu.com intrepid-security/multiverse Packages
Hit http://archive.ubuntu.com intrepid-security/multiverse Sources
Get:17 http://archive.ubuntu.com intrepid-proposed/restricted Packages [4996B]
Get:18 http://archive.ubuntu.com intrepid-proposed/main Packages [33.0kB]
Get:19 http://archive.ubuntu.com intrepid-proposed/multiverse Packages [14B]
Get:20 http://archive.ubuntu.com intrepid-proposed/universe Packages [11.7kB]
Fetched 8755kB in 6s (1336kB/s)                                                
Reading package lists... Done
khaal@Xeraphim:~$ sudo dpkg --force-depends --purge xulrunner-1.9.1
dpkg - warning: ignoring request to remove xulrunner-1.9.1 which isn't installed.
khaal@Xeraphim:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ggzcore-bin libggzmod4 guile-1.8-libs libggz2 libggzcore9
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
khaal@Xeraphim:~$ sudo apt-get install xulrunner-1.9.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xulrunner-1.9.1: Depends: libhunspell-1.1-0 (>= 1.1.6-1) but it is not installable
E: Broken packages
khaal@Xeraphim:~$ 

```

And I have these repos in my sources:

deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main


Running 8.10 if its of any help...

---

### Post by rykel on 2008-11-13
Thanks for this thread! Been using FF 3.1b1pre2 for a while now with almost total satisfaction! Very fast and responsive on ajax-heavy websites!!

I now look forward to using FF 3.1 Beta 2... any idea when it will be out, and if the PPA repository will automatically update Beta 1 currently on my system?

---

### Post by binbash on 2008-11-13
Thanks for the javascript tricks and installation instructions!

---

### Post by takakia on 2008-11-20
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xulrunner-1.9.1: Depends: libhunspell-1.1-0 (>= 1.1.6-1) but it is not installable
E: Broken packages
khaal@Xeraphim:~$ 
[/CODE]

And I have these repos in my sources:

deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main


Running 8.10 if its of any help...[/QUOTE]

I have the same problem of dependency. Is there any fix for this.

---

### Post by timchesonis on 2008-11-26
> **rykel said:**
> Thanks for this thread! Been using FF 3.1b1pre2 for a while now with almost total satisfaction! Very fast and responsive on ajax-heavy websites!!

I now look forward to using FF 3.1 Beta 2... any idea when it will be out, and if the PPA repository will automatically update Beta 1 currently on my system?

FF 3.1 Beta 3 is out now, so how do we upgrade to it from 3.1 beta 2?  I too, have the repositories, but it doesn't seem to want to update beta 2 to beta 3.

---

### Post by JRod37 on 2009-02-26
> **mikewhatever said:**
> +1. I also think that if one is savvy enough to test beta software, he should, at least, be able to figure out how to install it. Otherwise, perhaps one is not as savvy as one might think.

Wow, dude, you're kind of a jerk. Everyone has to start somewhere. Nobody is born with the knowledge of an experienced beta tester. Your attitude goes against everything that Ubuntu is about. If your "superior intellect" can't tolerate the newbies then I suggest you go back to complaining about Vista to your dog and stop making others feel small.

---

### Post by yoda2031 on 2009-03-06
> **JRod37 said:**
> 
[QUOTE=mikewhatever;5966839]+1. I also think that if one is savvy enough to test beta software, he should, at least, be able to figure out how to install it. Otherwise, perhaps one is not as savvy as one might think.

Wow, dude, you're kind of a jerk. Everyone has to start somewhere. Nobody is born with the knowledge of an experienced beta tester. Your attitude goes against everything that Ubuntu is about. If your "superior intellect" can't tolerate the newbies then I suggest you go back to complaining about Vista to your dog and stop making others feel small.[/QUOTE]

Whilst I agree that everyone has to start somewhere, I disagree that Mike's attitude was as bad as you make out.  There are far worse examples of acidic posts than that one.

I also think Mike's point was valid - if one does not know how to install software, then it follows that one's ability to provide technical information to the package maintainer is fairly limited.  Thus making beta testing rather moot in this case.

However, I don't think this justifies an attitude whereby advice is not given to potential beta testers.  As has been pointed out, some are technically able just not familiar with the Linux way of doing things.  Some others don't want to beta test, they just want the latest and greatest software - and, if they are prepared to put up with the bugs and headaches that come with that, why should they not be entitled to exactly that?

The "install" command mentioned previously is totally possible, and I would implement it myself if I weren't incredibly selfish and busy :P
Pointers in the right direction for those who DO wish to implement the script:
I recommend bash as the language of choice,
One way of easily distinguishing between a request to install a package (which does an apt-get install, I would've thought) and a request to install an archive (which would do a tar -xvzf to /usr/local by default, I suppose) might be to have a command line argument which you grep for a ".tgz", ".tar.gz",".tar",".tar.bz2" extension and deal accordingly,
Another option might be to use "wget" calls if no extension is found, basing the URL you pass to "wget" on some database of bleeding-edge applications - but you'd have to find/create said database first :P

Good luck, have fun and peace out!

---

### Post by vibe666 on 2009-03-11
when i was 19, i bought my first computer (win95 back then) and proceeded to try new things and quite often broke stuff and had to figure out how to fix things.

it turned out i had quite a knack for fixing computers and after a lot of self taught break/fix (where i was both sides of the equation) experience i got a job selling computers and from there worked my way up on the tech side of things.

i'm now doing 3rd level support globally for one of the largest IT companies on the planet.

i'm still very new to linux and tbh i still really don't have much of a clue with it, but i',m learning and that's the only way i'm going to find out, trying new things and possibly breaking them and then learning how to fix them, but then that's how every single person here from the top to the bottom got where they are today, be it treading their first steps in ubuntu land or developing for the community.

everyone started at the bottom, so just try and give us new guys a break and help out where you can and let us make our own mistakes and then help us to figure out how to fix them and this whole community will keep growing and next time someone does something stupid, someone you helped out of a hole might be the one to help the next guy and the whole community 'thing' keeps on moving along the way it's supposed to.

it's 2009 people, not 1999 and linux is supposed to be for everyone, please try and remember that before you don your 1337 h@x0r caps.

---

