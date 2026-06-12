---
title: "FirefoxFirefox... update -&gt; total crash... first problem I could not solve"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by jkcowboy on 2009-06-14
Hi all,

System: Ubuntu 9.04 Jaunty, FireFox version 3, and I believe build2 with flash addon.  Computer: Dell Inspiron 1150

Problem: Yesterday, my Update Manager found a few upgrades.  I didn't look closely and authorized the updates.  Today, Firefox failed to open, displaying an XML error and the line of code that it failed on.  I can't get this particular error again and so don't have the exact error message. I've used all the following apt-get commands trying to reload Firefox.  sudo apt-get "remove, install, purge, build-dep, check".  I've done the same using synaptic package manager.  All fail in the same mode, showing that I have missing dependencies.  But even the build-dep fails to fix them.  I can't even remove the packages.  When I delineate the package I always use the general word "firefox" without the version numbers.

Example:  The following shows a few of the commands used and the outputs from terminal...

jking@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  firefox-3.0
Suggested packages:
  firefox-3.0-gnome-support latex-xft-fonts
The following packages will be upgraded:
  firefox-3.0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
108 not fully installed or removed.
Need to get 0B/887kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 124771 files and directories currently installed.)
Preparing to replace firefox-3.0 3.0.10+nobinonly-0ubuntu0.9.04.1 (using .../firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb) ...
Unpacking replacement firefox-3.0 ...
dpkg: error processing /var/cache/apt/archives/firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb (--unpack):
 trying to overwrite `/etc/firefox-3.0/pref', which is also in package ubufox
Please restart all running instances of firefox-3.0, or you will experience problems.
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Note: above no instance of firefox was running in "top" and the computer had been freshly restarted


jking@ubuntu:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox-3.0-branding: Depends: firefox-3.0 (= 3.0.11+build2+nobinonly-0ubuntu0.9.04.1) but 3.0.10+nobinonly-0ubuntu0.9.04.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

jking@ubuntu:~$ sudo apt dist-upgrade -f firefox
sudo: apt: command not found
jking@ubuntu:~$ sudo apt-get dist-upgrade -f firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be upgraded:
  firefox-3.0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
108 not fully installed or removed.
Need to get 0B/887kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 
124771 files and directories currently installed.)
Preparing to replace firefox-3.0 3.0.10+nobinonly-0ubuntu0.9.04.1 (using .../firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb) ...
Unpacking replacement firefox-3.0 ...
dpkg: error processing /var/cache/apt/archives/firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb (--unpack):
 trying to overwrite `/etc/firefox-3.0/pref', which is also in package ubufox
Please restart all running instances of firefox-3.0, or you will experience problems.
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Looking at Synaptics Manager the following broken packages are shown ->
Firefox-3.0-branding... When I try to fix the broken package from synaptice the following message is given ->

E: /var/cache/apt/archives/firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb: trying to overwrite `/etc/firefox-3.0/pref', which is also in package ubufox

Now in short, I can't load, unload or fix Firefox.  Thankyou to anyone who takes the time to look at this problem and a lifetime of Christmas cards to the fellow that knows to do :)

Thanks, John

---

### Post by jimv on 2009-06-14
Try moving the folder that it's choking on:

sudo mv /etc/firefox-3.0/pref /etc/firefox-3.0/pref.old

---

### Post by jkcowboy on 2009-06-14
Thanks JimV,

I tried what you said and here are the results:

jking@ubuntu:/etc/firefox-3.0$ sudo mv pref pref.old
[sudo] password for jking: 
jking@ubuntu:/etc/firefox-3.0$ ls
pref.old  profile
jking@ubuntu:/etc/firefox-3.0$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox-3.0-branding: Depends: firefox-3.0 (= 3.0.11+build2+nobinonly-0ubuntu0.9.04.1) but 3.0.10+nobinonly-0ubuntu0.9.04.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


This is the unmet dependencies I was talking about.  I have not been able to fix them.  I don't understand why Linux has problems attempting to write a file with root power.  Back to the question at hand.  Is there a sure fire way to unload/reload Firefox and not mess anything else up?  Anything basically wrong with what I have been trying to do?

---

### Post by jkcowboy on 2009-06-14
For all, I renamed the one pref file to pref.old.  For now I will leave it unless told to restore it.  John

---

### Post by jkcowboy on 2009-06-14
Think I made some progress...   I decided to run apt-get -f install one more time after renaming the pref file and got the following with no errors.  Then I reinstalled Firefox, also with no errors.  I ran all this SSH, so I will check out firefox when I get home.

I'll post again if the problem persist.

Open question for all?  Why would Linux jam on writing to a file with root access?  Why doesn't it just write the file over the old one?  I don't think I would have tried to change the name of a pref file on my own.  Insight on this?   -John

---

### Post by jkcowboy on 2009-06-14
Well I think I made some progress. I have no visible errors.  When I try and start Firefox now, it appears to try and start (icon in bottom tray) but then closes (never actually displays a window or load a webpage).

What does it mean when program fails to start?  -John

---

### Post by jimv on 2009-06-14
ok, lets do this:

sudo apt-get purge firefox ubufox

sudo rm -r /etc/firefox-3.0

sudo apt-get install firefox ubufox

---

### Post by jimv on 2009-06-14
double post, sry

---

### Post by jkcowboy on 2009-06-14
All and especially JimV  thanks.

After successfully updating the packages I had a problem with the program starting.  All works now!  But, I don't know why I had to do the following:

1.  Fully removed Firefox...again.
2.  Disabled start scripts in /usr/bin for firefox and firefox-3.0.... wasn't necessary
3.  deleted .mozilla files in two locations (administrator, and one of the users)
4.  Reinstalled Firefox from Synaptic... no errors.... but still would not run
5.  Enabled start scripts in /usr/bin for firefox and firefox-3.0... should have never done this... still no run
6.  Looked at permissions for the two startup scripts..
     a.  /usr/bin/firefox -> owner:root:read/write, group:root:read/write, others:read:write
     b. /usr/bin/firefox-3.0 -> owner:root:read/write,group:root:readonly, others: read only
     I relaxed permission on (a) to be the same as (b)... and everything worked!!!!!!

Program starts normally now and I DONT KNOW WHY!  The permission were set by Synaptics and installed without errors.  Why would group and others have to be set to read/write.  Read only should work for running a script shouldn't it?  

If you know the answer, please tell so I handle this better next time a program doesn't start.

-John

---

### Post by frank_costanza on 2009-06-15
After the update to 3.0.11, Firefox was crashing for me too.

I ended up trying some of the above advice. But in the end, I just disabled all of my add-ons. To do this, I ran Firefox in safe mode by running ```
firefox -safe-mode
``` from the terminal. Then, I selected the option to disable add-ons.

Now, I just need to add them back one-by-one to see if I can identify a problem with any of them.

---

