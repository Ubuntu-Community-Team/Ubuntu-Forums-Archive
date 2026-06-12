---
title: "Update manager: You can install 3 updates (out of 26)"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2009-05-07
I had never seen that before, that the Update manager shows me a lot of software updates to install, but does not let me select them and offer me only a partial update.

I tried to use [Check] and got An error occured:
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 248DD1EEBC8EBFE8
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 90345E8D2FEF0CE2


Could this be the reason for the partial update? How can I fix it?

bye

Ronald

---

### Post by pastalavista on 2009-05-07
Open a terminal and enter
```
gpg --keyserver keyserver.ubuntu.com --recv xxxxxxxxxxxxxxxx
```
(replace the xxx's with the actual key number) and then
```
gpg --export --armor xxxxxxxxxxxxxxxx | sudo apt-key add -
```

and repeat the procedure for each key number

---

### Post by ELMIT on 2009-05-07
Thanks it helped to get rid of the errors, but it still cannot update:

> Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
* A previous upgrade which didn't complete
* Problems with some of the installed software
* Unofficial software packages not provided by Ubuntu
* Normal changes of a pre-release version of Ubuntu

How can I solve that?

bye

R.

---

### Post by pastalavista on 2009-05-07
Try this ```
sudo aptitude safe-upgrade
```
and if that doesn't fix it, open Synaptic Package Manager and check for broken packages.

---

### Post by ELMIT on 2009-05-07
>  sudo aptitude safe-upgrade
[sudo] password for ronald: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been automatically kept back:
  clamav-freshclam openoffice.org-base-core openoffice.org-filter-binfilter 
  openoffice.org-officebean openoffice.org-report-builder-bin uno-libs3 ure 
The following packages have been kept back:
  clamav openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-math openoffice.org-style-human 
  openoffice.org-writer python-uno 
0 packages upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

How do I check in Synaptic for broken packages?

bye

R.

---

### Post by pastalavista on 2009-05-07
> **ELMIT said:**
> How do I check in Synaptic for broken packages
R.
Go to System > Administration > Synaptic Package Manager. Click the tabs in the left pane until you find the word 'broken' and click it. If anything shows in the right pane, click the box and install or reinstall it.

But before that, though, run ```
sudo aptitude full-upgrade
``` and see what that does.

---

### Post by ELMIT on 2009-05-07
still the same:

> ronald@ronald-desktop:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  openoffice.org-l10n-de openoffice.org-l10n-en-gb openoffice.org-l10n-en-za 
  openoffice.org-l10n-ru openoffice.org-l10n-zh-cn openoffice.org-l10n-zh-tw 
The following packages will be automatically REMOVED:
  openoffice.org-writer2latex 
The following packages will be REMOVED:
  openoffice.org-writer2latex 
The following packages will be upgraded:
  openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-binfilter openoffice.org-gnome openoffice.org-gtk openoffice.org-impress 
  openoffice.org-math openoffice.org-officebean openoffice.org-report-builder-bin 
  openoffice.org-style-human openoffice.org-writer python-uno uno-libs3 ure 
20 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 80.1MB of archives. After unpacking 15.7MB will be used.
The following packages have unmet dependencies:
  openoffice.org-l10n-de: Conflicts: openoffice.org-core (>= 1:3.0.1.1) but 1:3.1.0~rc2-1ubuntu1~hardy1 is to be installed.
  openoffice.org-l10n-ru: Conflicts: openoffice.org-core (>= 1:3.0.1.1) but 1:3.1.0~rc2-1ubuntu1~hardy1 is to be installed.
  openoffice.org-l10n-zh-cn: Conflicts: openoffice.org-core (>= 1:3.0.1.1) but 1:3.1.0~rc2-1ubuntu1~hardy1 is to be installed.
  openoffice.org-l10n-zh-tw: Conflicts: openoffice.org-core (>= 1:3.0.1.1) but 1:3.1.0~rc2-1ubuntu1~hardy1 is to be installed.
  openoffice.org-l10n-en-gb: Conflicts: openoffice.org-core (>= 1:3.0.1.1) but 1:3.1.0~rc2-1ubuntu1~hardy1 is to be installed.
  openoffice.org-l10n-en-za: Conflicts: openoffice.org-core (>= 1:3.0.1.1) but 1:3.1.0~rc2-1ubuntu1~hardy1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
openoffice.org [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-base [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-base-core [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-calc [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-common [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-core [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-draw [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-evolution [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-filter-binfilter [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-gnome [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-gtk [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-impress [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-math [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-officebean [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-report-builder-bin [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-style-human [1:3.0.1-7ubuntu1~hardy1 (now)]
openoffice.org-writer [1:3.0.1-7ubuntu1~hardy1 (now)]
python-uno [1:3.0.1-7ubuntu1~hardy1 (now)]
uno-libs3 [1.4.1+OOo3.0.1-7ubuntu1~hardy1 (now)]
ure [1.4.1+OOo3.0.1-7ubuntu1~hardy1 (now)]

Downgrade the following packages:
openoffice.org-writer2latex [0.5-6ubuntu0.1 (hardy-updates, now) -> 0.5-6 (hardy)]

Score is 1121

Accept this solution? [Y/n/q/?] 
The following packages have been automatically kept back:
  openoffice.org-base-core openoffice.org-filter-binfilter openoffice.org-officebean 
  openoffice.org-report-builder-bin uno-libs3 ure 
The following packages will be DOWNGRADED:
  openoffice.org-writer2latex 
The following packages have been kept back:
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer 
  python-uno 
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 20 not upgraded.
Need to get 0B/383kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
dpkg - warning: downgrading openoffice.org-writer2latex from 0.5-6ubuntu0.1 to 0.5-6.
(Reading database ... 401099 files and directories currently installed.)
Preparing to replace openoffice.org-writer2latex 0.5-6ubuntu0.1 (using .../openoffice.org-writer2latex_0.5-6_all.deb) ...
Removing extension ... done.
Unpacking replacement openoffice.org-writer2latex ...
Setting up openoffice.org-writer2latex (0.5-6) ...
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg...An error occurred while enabling: writer2latex.jar
 done.

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
ronald@ronald-desktop:~$ 


I tried several times!

bye

R.

---

### Post by pastalavista on 2009-05-07
Still the same? Doesn't look the same at all. You got something done. What's update manager say now? Look in synaptic like I told you and search for openoffice.org as well as the broken ones. Sorry I couldn't help more.... going to bed now.. gotta be at work by 9

---

### Post by toutanc on 2009-05-07
This happened to me once or twice when one of the repos was broken (dependencies not satisfied etc), it happens sometimes with development ppas .

I usally  wait until the next day to try again, most of the time it's fixed :p

If it doesn't work then try and figure out which repo causes the problem (probably not an official one) to either change with another or remove it.

---

### Post by bixejo on 2009-05-07
I'm getting the same issue in three different machines, one with 8.04-i386, another with 8.04-amd64, and the last one with 8.10-i386. The problem seems to be related to OpenOffice repository at Launchpad. I tried two things:

[LIST]
[*]Disable OO repository and the problem vanished after reloading packages' info (well, I guess it did, there were no available package updates after I disabled this repos.)
[*]Going to synaptic and clicking on "Select all updates". When I did this (with OO repos enabled, of course), I was "suggested" to remove also a lot of packages to commit this update. I didn't dare to do so, as some of these packages were related to language support and there were no other packages that sound similar among the ones it was about to update.
[/LIST]
I don't know too much about this, but it could be possible that update-manager does not ever make updates that imply removing some other (apparently) non-related packages, so you should use some other tool like synaptic that gives you full control on what's about to happen if you make the final click.

Looks like there exists some kind of incompatibility among new OO updates and some ordinary Ubuntu stuff. It's probably a bug or some kind kind of misconfiguration of OO packages dependiences?

---

