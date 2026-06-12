---
title: "Problem involving deleting and SVN (unusual problem)"
date: 2008-07-17
forum: General Help
---

### Post by Pelzer on 2008-07-17
OK so...  I have a very unusual problem (or at least I think I do).  I have my P.C on a dual boot between Ubuntu Hardy and Windows XP.  I am somewhat of a gamer, and have my games installed on the XP part (although I'm trying to switch totally to WINE as much as possible).  I have HL2 Garry's Mod installed in Windows XP, as well as in WINE in Ubuntu.


So now that you know the setup....  Here is what is wrong....  There is a co-operative mod for Garry's Mod that HAS to be installed through SVN (in this case, I used Tortoise SVN).  I had installed the mod in windows and tried to install it in my WINE.  For about 5 days I only had the mod installed in windows.  At the same time, I had installed it in WINE using the built in SVN in Ubuntu.  It didn't work in wine, but worked fine in Windows...


So...  I tried an experiment (being a linux noob).  I went into my G-mod folder on the Windows Partition, copied the Tortoise SVN'd folder INTO MY G-MOD FOLDER IN UBUNTU.  When I did this I was simply seeing if somehow this would kick it into action in wine (stupidly I thought this, but at the same time it was "what the hell, what can it hurt?  I can just delete it).  Naturally, the mod still didn't run...  


So, after copying it over in wine and finding it didn't run, I DELETED IT IN UBUNTU.  As soon as I had deleted it in ubuntu, the mod stopped working properly in Windows.  So, I am thinking (probably wrong) that somehow Totroise SVN is calling out to both folders (the original and the Ubuntu deleted copy) because I deleted it in ubuntu, it probably deleted the way windows does, which is simply ignore it (Or does Ubuntu totally wipe it out?).  So I'm thinking windows still sees it????  Maybe?  IDK exactly how SVN works, so Please take it easy on a noob (I'm trying to understand what has happened).  What I want to do is to recover the deleted copy in ubuntu, send it back to the NTFS partition and delete it through windows.  I'm logically deducting that this might fix the problem...  


What I need to know is what tools could I use to recover it, and what the hell is happening?  Thanks for any help or input, these forums are great!

---

### Post by Pelzer on 2008-07-17
EDIT:  Also to add a little info...  I HAVE TRIED RE-INSTALLING TORTOISE SVN AND HAVE RE-INSTALLED THE MOD IN WINDOWS, AND IT STILL HAS VERY SCREWED UP WEIRD PROBLEMS.  IF IT RUNS AT ALL, IT MIXES THE CO-OP GAMETYPE WITH OTHER GAMETYPES, VERY UNUSUAL.

---

