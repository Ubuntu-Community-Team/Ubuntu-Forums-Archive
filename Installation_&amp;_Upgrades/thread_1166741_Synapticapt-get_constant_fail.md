---
title: "Synaptic/apt-get constant fail"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by mingtien on 2009-05-22
This is a follow-up to a previous post, which I don't think I worded correctly, so here's another try.  I would be grateful for any advice on this, as it is frustrating not to be able to run system updates.

Over the last few weeks, I have been unable to get a system update to complete, either using apt-get or using Synaptic.  In both cases -- most of the time, running an update will produce a number of errors, and at one point it will just hang.  I've attached captured text from apt-get and a screenshot from Synaptic below.

Most of the error messages (or FAILs) seem to do with a file called Translation-en_GB, if anyone can advise as to what that does. The signature verification error is new (that is, I've seen it in the past, but not recently).

Oddly enough, when I connect to a fast (wired or wifi) broadband network, updates work.  When I connect via wireless broadband (EVDO/CDMA2000 -- my ONLY connection 99% of the time), updates almost never work (I seem to recall them working under Intrepid for a time).  Mail (IMAP and POP), RSS, DropBox, FTP, wget, and web browsing all work fine, and I have no problems downloading large files (I've downloaded a handful of CD and DVD iso's recently -- via web, ftp, and torrent).

I have looked through the last year's history of similar problems, and the only similar ones were not resolved (or possibly, were resolved but the person never wrote a follow-up entry).

Here is apt-sources -- I've commented out most of them for testing purposes.  The problem is the same whether I use the main site, the main UK archive, or various sites here in Asia.

```


# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://th.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://th.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

# Remastersys
# deb http://www.geekconnection.org/remastersys/repository ubuntu/

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
# deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
# deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
# deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main universe multiverse
# deb http://www.geekconnection.org/remastersys/repository ubuntu/

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
# deb http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu jaunty main


```


And when I try to run apt-get update (I'm running this in a root terminal in this example, but the same problem occurs when running via sudo).  The last bit (41 packages) is where it hangs.  


```


root@buriram:~# apt-get update
Get: 1 http://gb.archive.ubuntu.com jaunty-updates Release.gpg [189B]          
Hit http://archive.canonical.com jaunty Release.gpg                     
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg [189B]             
Ign http://archive.canonical.com jaunty/partner Translation-en_GB              
Ign http://packages.medibuntu.org jaunty/free Translation-en_GB                
Hit http://archive.canonical.com jaunty Release                                
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_GB            
Ign http://archive.canonical.com jaunty/partner Packages                       
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB
Hit http://packages.medibuntu.org jaunty Release                               
Hit http://archive.canonical.com jaunty/partner Packages                       
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB     
Hit http://packages.medibuntu.org jaunty/free Packages                         
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB   
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Get: 2 http://gb.archive.ubuntu.com jaunty-security Release.gpg [189B]         
Ign http://gb.archive.ubuntu.com jaunty-security/main Translation-en_GB        
Ign http://gb.archive.ubuntu.com jaunty-security/restricted Translation-en_GB  
Ign http://gb.archive.ubuntu.com jaunty-security/universe Translation-en_GB    
Ign http://gb.archive.ubuntu.com jaunty-security/multiverse Translation-en_GB  
Get: 3 http://gb.archive.ubuntu.com jaunty Release.gpg [189B]                  
Get: 4 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 5 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 6 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]     
Get: 7 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]     
Get: 8 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]     
Get: 9 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]     
Get: 10 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 11 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 12 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 13 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 14 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 15 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 16 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 17 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 18 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 19 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 20 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]    
Get: 21 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 22 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 23 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 24 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 25 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 26 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 27 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 28 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 29 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 30 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 31 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 32 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 33 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 34 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 35 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
99% [35 Translation-en_GB bzip2 0] [Connecting to gb.archive.ubuntu.com (194.16
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign http://gb.archive.ubuntu.com jaunty/main Translation-en_GB                 
Get: 36 http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB [35.2kB]
Hit http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB           
Hit http://gb.archive.ubuntu.com jaunty-updates Release                        
Get: 37 http://gb.archive.ubuntu.com jaunty-security Release [49.6kB]          
Err http://gb.archive.ubuntu.com jaunty-security Release                       
  
Get: 38 http://gb.archive.ubuntu.com jaunty Release [74.6kB]                   
Ign http://gb.archive.ubuntu.com jaunty Release                                
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages                  
Get: 39 http://gb.archive.ubuntu.com jaunty-updates/restricted Packages [14B]  
Get: 40 http://gb.archive.ubuntu.com jaunty-updates/restricted Packages [14B]  
Get: 41 http://gb.archive.ubuntu.com jaunty-updates/restricted Packages [14B]  
Get: 42 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB] 
Get: 43 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB] 
Get: 44 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB] 
Get: 45 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB] 
Get: 46 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB] 
Get: 47 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB] 
Get: 48 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB] 
Get: 49 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB]
Get: 50 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB]
Get: 51 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB]
Get: 52 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB]
Get: 53 http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages [675B] 
Get: 54 http://gb.archive.ubuntu.com jaunty/main Packages [1253kB]             
Get: 55 http://gb.archive.ubuntu.com jaunty/universe Packages [4757kB]         
Get: 56 http://gb.archive.ubuntu.com jaunty/restricted Packages [8848B]        
Get: 57 http://gb.archive.ubuntu.com jaunty/multiverse Packages [197kB]        
99% [41 Packages bzip2 0]


```


And (below) is a snapshot of the same problem in Synaptic -- again it will get to a certain point and just hang.


Can anyone point me in the right direction as to how to solve this?  Is there something very obvious that I am missing?

Thanks!!

---

### Post by mingtien on 2009-05-26
Bumping this, in hopes to find someone who has had a similar experience, and found some resolution...

---

### Post by mingtien on 2009-05-30
Toujours à l'espoir que quelqu'un reconnaitra la problème et en aurait un résolution...

---

### Post by mingtien on 2009-06-09
Bump -- would still love to fix this problem

---

### Post by dE_logics on 2009-06-09
See if you don't have any broken dependencies.

IF not, it's a problem with you ISP...why not try downloading something else (an archive will be prefect) and see if its not corrupt? (extract the archive to see that).

---

### Post by mingtien on 2009-06-10
Thank you for your reply, De-Logics!  

I ran sudo apt-get check and there do not appear to be any broken dependencies (also, all packages are working that I can tell...).

Also I have no problems (corruption or otherwise) downloading any other files.  For the packages I've had to add without Synaptic/apt-get working, I've just downloaded either .deb files and added them manually, or grabbed the source tarballs and built them.  I've also downloaded various other large files ranging from CD iso's to DVD iso's, with no problems.

I think that the clue lies in the Translation-en_GB failure on every attempt to update -- can anyone tell me what that does, or point me in the right direction?

---

### Post by mingtien on 2009-06-18
Bump.

salty-wet ghost-man

---

### Post by mingtien on 2009-07-04
Bump -- still have not resolved this problem

---

### Post by mingtien on 2009-07-10
Bump (bumpety bump, mouldy stump, camel's hump, rhino's rump, English frump, ace's trump)


Still not resolved :)

---

### Post by Crunchy the Headcrab on 2009-07-12
I'm having a similar issue.  I can apt-get via ethernet all day long and not have a single error.  However, the minute I start apt-getting or synaptic over wifi I get a truck load of errors!  My wifi connection seems perfectly fine.  I am surfing the net and downloading things through firefox in perfect time.  Even downloading things through apt-get is quick, but then I get errors during unpacking/installation.

What I have to do, which is very annoying, is setup/install my system with ethernet plugged in and only use wifi for surfing.  If I want to install via apt-get or synaptic OR update, I have to take my computer down to my desktop, rip the ethernet out of my desktop pc and plug it in to my lappy (wireless gateway only has 1 ethernet port).

Also note that sometimes apt-get over wifi works.  So just when I think my woes are over they start again.  The common denominator for failed updates for me is wifi though.  I _never_ have errors over a wired connection.

---

### Post by mingtien on 2009-09-02
Sorry to take long to reply - I've been on a 6 week business trip to the land down under (actually even with some fairly arduous days at work, it still felt like a holiday, and my mates at work were fantastic hosts!!).

I'm pretty sure it's a network speed issue.  I had no problem with ethernet connections, and the fast wifi in my serviced flat worked fine.  With the wireless broadband dongle that I hired for travelling around the country, updates never worked (nor did some slow wifi links), but with a colleague's wireless broadband (different provider and a LOT faster) updates worked fine.

I was also able to reproduce the problem on several fresh installs of Ubuntu 9.04, both 32-bit and 64-bit versions (I was given 2 new laptops from work).

So the moral of the story is: even if your connection is fast enough to download a handful of iso's, it might not be fast enough for Synaptic to update -- you've just got to wait until you get to a place that is faster!

---

### Post by stlsaint on 2009-09-02
please mark thread as solved or at least resolved.

---

