---
title: "Upgraded from 8.10 to 9.04 but can't go to 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Thrasonic on 2009-10-31
Hello all.  I've upgraded from Kubuntu 8.10 to 9.04 and that went fine.  But I'm running into problems upgrading from 9.04 to 9.10.  First I tried with just the upgrade option in the bottom right corner by the clock.  It runs through some things and starts downloading the files necessary (takes forever) and then begins the upgrade process after I tell it to go ahead and it doesn't get anywhere - it doesn't install any files.  Instead I get an error message which I don't have right now.

The reason I don't have that error message is because I came to the boards and found the upgrade info if I want to use a CD instead.  I tried that and I got the following after it went through Preparing, Setting channels, getting packages, and then Installing:

Could not install upgrades:  The upgrade is now aborted.  Your system could be in an unusable state.  A recovery will run now (dpkg --configure -a).  There's a report bug button and when I click on it I get the following in terminal (I used terminal to launch the upgrade from the CD):

jon@kubuntu:~$ kdesudo sh /cdrom/cdromupgrade

adept_manager: no process killed
adept_updater: no process killed
gpgv: Signature made Tue 27 Oct 2009 01:28:21 PM EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
 * Starting automatic crash report generation: apport
   ...done.
konqueror(5139) FixHostUriFilter::filterUri: FixHostUriFilter::filterUri:  KUrl("https://launchpad.net/ubuntu/+source/update-manager/+filebug")
konqueror(5139) KonqViewManager::setCurrentProfile: "webbrowsing" localPath= "/root/.kde/share/apps/konqueror/profiles/webbrowsing"
konqueror(5139) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kio_http_cache_cleaner
kded(5156) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "NetworkManager 0.7"
kded(5156) KDEDModule::setModuleName: registerObject() successful for  "networkstatus"
kded(5156) KDEDModule::setModuleName: registerObject() successful for  "kcookiejar"
kded(5156) KDEDModule::setModuleName: registerObject() successful for  "favicons"
kdeinit4: preparing to launch
kdeinit4: preparing to launch
konqueror(5139): The kwalletd service has been disabled
konqueror(5139): The kwalletd service has been disabled
konqueror(5139): The kwalletd service has been disabled
konqueror(5139): The kwalletd service has been disabled
konqueror(5139): The kwalletd service has been disabled
konqueror(5139): The kwalletd service has been disabled
konqueror(5139): The kwalletd service has been disabled
QObject::connect: Cannot connect (null)::walletOpened(bool) to KHTMLWalletQueue::walletOpened(bool)
konqueror(5139): The kwalletd service has been disabled
kdeinit4: preparing to launch

Any ideas what's keeping me from upgrading?  I really don't want to do a clean install because I'm a newbie and it takes me days, if not weeks to get everything configured all over again.

---

### Post by frt975 on 2009-10-31
start synptac and click on mark all updates. then go to file/generate download script. place it in the folder you want the updates to be downloaded to. once it's done, open file/import downloaded files. this only helps if apt refuses to download updates.
-------------------------------
sorry about the spelling and capitalization i'm on my psp

---

### Post by Thrasonic on 2009-11-01
Unfortunately that doesn't work.  In Kubuntu I don't have synaptic installed and when I try to install it I get an error message.  In Kubuntu I'm using Package Manager and here's the error message I get:

Download failed.
The list of errors is attached. The recovery for this case is currently not implemented. If you see 404 errors, it might be useful to try fetching package lists (see the Sources tab) and retrying the operation.

The error was: 
APT Error. Context:
    Package download failed, 
    Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages., 
    Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages., 
    Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages., 
    Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages., 
    Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages., 
    Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages., 
    Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages., 
    : , 
    : , 
    : , 
    : , 
    : , 
    : , 
    : , 
    : , 
    : , 

If I click the Changes button on the left side of the Packages Manager window there are a ton of things that are listed as things that need to be upgraded or installed, but when I try to apply the changes, with or without adding Synaptic, it doesn't work.  I tried using terminal and sudo apt-get update followed by upgrade and it ripped through a ton of stuff and removed a ton of stuff as well.  It looks like the upgrades to some software went through fine, but the upgrade to 9.10 didn't work.

---

### Post by Thrasonic on 2009-11-01
Okay, using the terminal to do apt-get updates and upgrades apparently upgraded the system to 9.10, but instead of giving me the gui I get a command prompt asking for my username followed by another for my password.  Before that the grub menu shows 9.04 as the choice but the screen asking for my password and login shows 9.10 kubuntu tty, so I'm assuming it upgraded me to 9.10.  Like I said there was a ton of stuff in the package manager to be installed and/or upgraded so perhaps everything it had downloaded from previous upgrade attempts was able to be installed?  I don't know, but now I don't know how to get my gui back.  Help?

---

### Post by Thrasonic on 2009-11-01
bump

---

### Post by Thrasonic on 2009-11-01
Bump

---

### Post by Thrasonic on 2009-11-01
bump

---

### Post by Thrasonic on 2009-11-02
bump

---

