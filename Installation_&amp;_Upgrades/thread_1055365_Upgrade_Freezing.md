---
title: "Upgrade Freezing"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by jlund77 on 2009-01-30
Here is my last ditch effort to get Ubuntu to update on my computer.
I'm a newbie, so please dumb down any reply please.

Was given a old laptop from a friend.  Compaq Evo N800c.  I have no clue what he has added or removed from this machine.  
I've been trying to upgrade Ubuntu 6.10 to 8.10 from a burned .iso.  As far as i can tell the disc burned clean.

When i go to run from the disc, it starts, asks for language, gives me the Ubuntu logo with bars moving, and than freezes shortly after.

Can't find a post that solves the problem.
I realize that this may not be enough info, but any help will be great.

---

### Post by avtolle on 2009-01-30
A quick Google search on that model indicates that it came with 256mb RAM. If no RAM upgrade was had, there's not enough RAM in the box to install from the Live CD. You might try either the alternate install iso burned to CD, which uses a text-based installer and can install from 256mb, or take a look at Xubuntu, which uses XFCE, a lighter desktop; from the Xubuntu site, it appears that a Live CD of Xubuntu 8.10 can be installed on a box with 256mb RAM.

---

### Post by jlund77 on 2009-01-30
Thanks for the quick response.

Figured that it was an issue with not enough RAM from other posts I read.

Is there in upside or downside to either of the alternative install methods use mentioned.

Really not trying to use the computer for much.  Trying to use it at work for nothing more than internet research.

---

### Post by slakkie on 2009-01-30
Upgrading directly to 8.10 is not possible from 6.10.

I just wrote an howto on how to upgrade from 6.10 to 8.04.2: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

The update from 8.04.2 to 8.10 is really easy afterwards:
[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

---

### Post by avtolle on 2009-01-30
I always install from the alternate, and have not had any problems (from 7.04 through 8.10). I've installed Xubuntu on a spare machine twice, and like it OK, but I've been in Gnome too long to easily transition. Again, no problems. 

Full disclosure: all my boxes have >512 mb RAM, so I have a lot of options as to which Ubuntu or variant to install and use.

---

### Post by jlund77 on 2009-01-30
I'm running you install, and I'm hung up after the sudo do-release-upgrade command.

Where do I need to install the patch at?

I see that a place listed, but I can't find that exact location on my computer.

Thanks for the help.

---

### Post by slakkie on 2009-01-30
Run find /tmp -name feisty

You will see something like:

/tmp/tmp<some random string>/feisty

cd into /tmp/tmp<some random string>

And continue the howto.

---

### Post by jlund77 on 2009-01-30
typed  find /temp -name feisty  and got the response:
No such file or directory.

---

### Post by slakkie on 2009-01-30
> **jlund77 said:**
> typed  find /temp -name feisty  and got the response:
No such file or directory.

not /temp but /tmp

---

### Post by jlund77 on 2009-01-30
my dumb was typing temp not tmp got the file

---

### Post by jlund77 on 2009-01-30
I found the patch, but I guess i'm not following where to copy and paste it.

Should I see a file that says /tmp/temp <something>/DistUpgradeControler.py.patch that it needs to patched to, or am I just patching the DisUpgradeControler.py file that I am looking at now?

---

### Post by slakkie on 2009-01-30
> **jlund77 said:**
> I found the patch, but I guess i'm not following where to copy and paste it.

Should I see a file that says /tmp/temp <something>/DistUpgradeControler.py.patch that it needs to patched to, or am I just patching the DisUpgradeControler.py file that I am looking at now?

You will patch the DistUpgradeControler.py with the patch file (DistUpgradeControler.py.patch). 


If you run 'patch < DistUpgradeControler.py.patch' you will make the changes as described in the file, all the lines starting with - will be removed and all the lines with the + will be added. Once you applied the patch you can run 'patch -R < DistUpgradeControler.py.patch' and you will undo the changes (just as info, you do must not do that for the upgrade process).

A patch file is created by running diff -u <file 1> <file 2>

---

### Post by jlund77 on 2009-01-30
I think we need to dumb the lingo back down.  This is pretty much the first time on Ubuntu, so we need to approach this as Linux 101.
Thank you so much for your help.

Also, I had to restart the computer a few minutes ago.  Is that goint to cause problems?  Did I lose the temp files that are needed?

---

### Post by slakkie on 2009-01-30
> **jlund77 said:**
> I think we need to dumb the lingo back down.  This is pretty much the first time on Ubuntu, so we need to approach this as Linux 101.
Thank you so much for your help.

Also, I had to restart the computer a few minutes ago.  Is that goint to cause problems?  Did I lose the temp files that are needed?

Haha, OK :) I was just trying to clarify the patch story (guess it didn't help ;)).

Files in /tmp will be removed after a reboot because it is actually a RAM disk (so you are edditing files stored in memory). So a reboot will have removed the files. But that doesn't matter if you have upgraded successfully.

---

### Post by jlund77 on 2009-01-30
Still not upgraded yet.  ran lsb_release and it came up as 6.10.
We will get there.  Hang in there with me.

---

### Post by jlund77 on 2009-01-30
This is where I'm at, and I can't seem to make anymore progress.  Where have I gone wrong?


jefflundgern@jefflundgern:~$ sudo perl -p -i.ORIG -e 's/(?:(?:\w+.)?archive|security).(ubuntu.com)/old-releases.$1/' /etc/apt/sources.list
Password:
jefflundgern@jefflundgern:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy Release.gpg [191B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/main Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/restricted Translation-en_US
Get:2 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:3 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
jefflundgern@jefflundgern:~$ sudo aptitude install update-manager-core update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
jefflundgern@jefflundgern:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jefflundgern@jefflundgern:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting '/tmp/tmp5xSOEh/feisty.tar.gz'
authenticate '/tmp/tmp5xSOEh/feisty.tar.gz' against '/tmp/tmp5xSOEh/feisty.tar.gz.gpg' 

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/restricted Sources
Done downloading            

Updating repository information
WARNING: Failed to read mirror file

No valid mirror found
While scanning your repository information no mirror entry for the upgrade was found.This can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update all 'edgy' to 'feisty' entries.
If you select 'no' the update will cancel.
Continue [yN] n

Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
jefflundgern@jefflundgern:~$ diff -u <DistUpgradeControler.py> <DistUpgradeControler.py.patch>
bash: syntax error near unexpected token `<'
jefflundgern@jefflundgern:~$ diff -u DistUpgradeDControler.py DistUpgradeControler.py.patch
diff: DistUpgradeDControler.py: No such file or directory
diff: DistUpgradeControler.py.patch: No such file or directory
jefflundgern@jefflundgern:~$ cd /tmp/tmp5xSOEh
jefflundgern@jefflundgern:/tmp/tmp5xSOEh$ sudo patch < DistUpgradeCOntroler.py.patch
bash: DistUpgradeCOntroler.py.patch: No such file or directory
jefflundgern@jefflundgern:/tmp/tmp5xSOEh$ sudo patch < DistUpgradeControler.py.patch
bash: DistUpgradeControler.py.patch: No such file or directory
jefflundgern@jefflundgern:/tmp/tmp5xSOEh$ sudo patch < DistUpgradeControler.py
Password:
patch: **** Only garbage was found in the patch input.
jefflundgern@jefflundgern:/tmp/tmp5xSOEh$ sudo aptitude install patch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
jefflundgern@jefflundgern:/tmp/tmp5xSOEh$ sudo ./feisty --frontend DistUpgradeViewText --mode=server

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-updates/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) edgy-security/restricted Sources
Done downloading            

Updating repository information
WARNING: Failed to read mirror file

No valid mirror found
While scanning your repository information no mirror entry for the upgrade was found.This can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update all 'edgy' to 'feisty' entries.
If you select 'no' the update will cancel.
Continue [yN] y
 WARNING: Failed to read mirror file

Generate default sources?
After scanning your 'sources.list' no valid entry for 'edgy' was found.

Should default entries for 'feisty' be added? If you select 'No' the update will cancel.
Continue [yN] y
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Done downloading            
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Done downloading            
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Sources
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Sources
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Done downloading            

Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]


Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
jefflundgern@jefflundgern:/tmp/tmp5xSOEh$ 
jefflundgern@jefflundgern:/tmp/tmp5xSOEh$

---

### Post by slakkie on 2009-01-30
No you are doing the patching all wrong, just follow the instructions in the howto, they are made in such a way that you can copy/paste all of it. Just make sure you you patch it by doing:

patch < DistUpgradeControler.py.patch 

And the content of the patch file is:

```

--- DistUpgradeControler.py.ORIG        2009-01-29 18:51:43.000000000 +0100
+++ DistUpgradeControler.py     2009-01-29 18:52:44.000000000 +0100
@@ -352,11 +352,11 @@
             # them back to archive.ubuntu.com - now this is a problem
             # of course for people upgrading from EOL release to a
             # EOL release
-            if (not entry.disabled and
-                entry.uri.startswith("http://old-releases.ubuntu.com/ubuntu")):
-                entry.uri = "http://archive.ubuntu.com/ubuntu"
-                logging.debug("transitioning old-releases.ubuntu.com to '%s' " % entry)
-                continue
+            #if (not entry.disabled and
+            #    entry.uri.startswith("http://old-releases.ubuntu.com/ubuntu")):
+            #    entry.uri = "http://archive.ubuntu.com/ubuntu"
+            #    logging.debug("transitioning old-releases.ubuntu.com to '%s' " % entry)
+            #    continue

             logging.debug("examining: '%s'" % entry)
             # check if it's a mirror (or offical site)
```

---

