---
title: "Repository 404s in Synaptic"
date: 2008-10-28
forum: General Help
---

### Post by seanos on 2008-10-28
Mysteriously today my ISP's repository stopped working in Synaptic - I just get failure messages when downloading and reloading produces a lot of "404 Not Found" messages.

I thought I'd test this and manually downloaded [http://ftp.netspace.net.au/pub/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/hardy/main/binary-i386/Packages.gz) using Firefox.  It worked fine, so now I'm not sure what's going on here.

I've been away and hadn't booted Ubuntu for a while, so yesterday I did about 250MB of updates, all of which seemed to go smoothly.  Has something changed after the update?  What is Synaptic doing differently to Firefox?

[Edit] Ditto for "sudo apt-get update"

---

### Post by cariboo on 2008-10-28
I would try a different server just to see if you get the same errors.

JIm

---

### Post by seanos on 2008-10-28
> **cariboo907 said:**
> I would try a different server just to see if you get the same errors.

JIm

Nope...fails with 4 Australian mirrors and the main server.  Time for a reboot perhaps.

---

### Post by seanos on 2008-10-28
No joy.

---

### Post by dcstar on 2008-10-28
> **seanos said:**
> Mysteriously today my ISP's repository stopped working in Synaptic - I just get failure messages when downloading and reloading produces a lot of "404 Not Found" messages.

I thought I'd test this and manually downloaded [http://ftp.netspace.net.au/pub/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/hardy/main/binary-i386/Packages.gz) using Firefox.  It worked fine, so now I'm not sure what's going on here.

I've been away and hadn't booted Ubuntu for a while, so yesterday I did about 250MB of updates, all of which seemed to go smoothly.
.........


If you did "about 250MB of updates" then chances are you have a 8.10 system which has not been officially released as yet.

Pre-release systems are constantly updated and mirror sites take time to receive the massive quantities of data from the main repositories and therefore can be in a state of only have received part of the updates (like the main index file which refers to files that are still on the way).

Wait a day or so to allow all the update packages to make it to the mirror repositories.

---

### Post by seanos on 2008-10-28
> **dcstar said:**
> If you did "about 250MB of updates" then chances are you have a 8.10 system which has not been officially released as yet.

Nope, not an upgrade.  Why would Update Manager offer you an upgrade that's not released?

The 250MB is just based on my unmetered traffic.

Thanks for taking the time to reply, but if you were paying attention you'd see I was having trouble accessing the **hardy** repository.

---

### Post by wabre on 2008-10-28
i'm having troubles as well with mirrors all over the world. while everything was working until about 2 days ago, now the mirrors are not accessible or during the update process some links are ignored.

might this be caused by the upgrade of the mirrors to the new release of 8.10 in 2 days??

maybe maintenance to repositories and mirror updates?

it's not possible to chose other mirros when they download with 15kb/s...


i could not find any official information which would state anything. and this happens to any of my computers.

---

### Post by Kevbert on 2008-10-28
Please post your sources.list. Do you get a http 404 error if you put one of the failing links in your browser ?

---

### Post by wabre on 2008-10-28
> **Kevbert said:**
> Please post your sources.list. Do you get a http 404 error if you put one of the failing links in your browser ?

i'm in russia right now, used yandex.ru mirror without any problems, including all sources you see in the attached file. but now either it's incredibly slow and it ignores some sources or it ends in time outs. same with other mirrors, unless i chose one in switzerland or somewhere else, but then it takes nearly hours to update.

i will check the http 404 errors in the browser

edit: checked the links: e.g. cairo-dock works, the others, be it archive ubuntu or launchpad end in a google search link if i copy paste into address

fab@fab-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy Release.gpg                         
Hit [http://mirror.yandex.ru](http://mirror.yandex.ru) intrepid Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy/cairo-dock Translation-en_US        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://mirror.yandex.ru](http://mirror.yandex.ru) intrepid/main Translation-en_US                    
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy Release                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg    
....

---

### Post by seanos on 2008-10-28
> **Kevbert said:**
> Please post your sources.list. Do you get a http 404 error if you put one of the failing links in your browser ?

First thing I tested - works fine in the browser.

---

### Post by wabre on 2008-10-28
this is what i also get in the terminal:

Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
  503 Service Unavailable
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
  503 Service Unavailable
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources                        
  503 Service Unavailable
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources                    
  503 Service Unavailable

they worked before, about 2 days ago

---

### Post by Kevbert on 2008-10-28
Software sources.list seems fine. Just tried medibuntu and that seems fine also. Not sure what to suggest, must be something to do with the server or your connection to the server.

---

### Post by seanos on 2008-10-28
Does anyone have any more suggestions?  I've attached a list of what's been installed in the last couple of days - can anyone see a culprit?

Once again, this doesn't seem to be a *simple* network problem as I can manually download files from the repository using Firefox.

---

### Post by Kevbert on 2008-10-29
It may be easier to download the files from [[COLOR="Red"]here.[/COLOR]]("http://packages.ubuntu.com/hardy/gnome/gnome-do") I know it's no ideal but at least you can get the files.

---

### Post by seanos on 2008-10-29
After quite a few attempts I managed to connect to another Australian repository.  I'm now waiting for a response from Netspace to see if there is a  problem at their end.

---

### Post by seanos on 2008-10-31
> We are currently doing some maintenance to our FTP servers, therefor
some directories and file may have been changed.

There is currently an open news desk in regards to this on our website:
[https://my.netspace.net.au/myNetspace/newsdesk.do](https://my.netspace.net.au/myNetspace/newsdesk.do)

Also, it appears the link you may have been after has changed:

[http://ftp.netspace.net.au/pub/ubuntu/dists/hardy/restricted/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/dists/hardy/restricted/source/Sources.gz)
to:
[http://ftp.netspace.net.au/pub/ubuntu/archive/dists/hardy/restricted/source/Sources.gz](http://ftp.netspace.net.au/pub/ubuntu/archive/dists/hardy/restricted/source/Sources.gz)Interesting, but a little unhelpful.  Their maintenance seems to have started *after* I had problems.

Is that directory change (/ubuntu/dists/hardy/ -> /ubuntu/archive/dists/hardy/) part of the move to Intrepid?  If so, should Synaptic pick that up automatically?  It doesn't at the moment (it's still looking for the 1st one), but maybe that's all part of Netspace's maintenance.

---

