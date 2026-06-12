---
title: "Need some help with Ubuntu/Kubuntu Dependencies."
date: 2013-03-17
forum: Hardware
---

### Post by EscapedNight on 2013-03-17
[COLOR=#000000][FONT=verdana]I reinstalled ubuntu today. There was no problem...until i installed krita from kubuntu backports ppa. Since then krita is not starting. It was in my computer even yesterday in old installation, working fine.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Anyways, so i asked in KDE/krita forums - they asked me to run [/FONT][/COLOR]kbuildsycoca4 installing kdelibs-bin

And then ran krita. it started but had no icons in it. I installed then the oxygen gtk2, gtk3 engine and oxygen icons themes. and the icons were back. 

But the problem is whenever I start it, i keep getting an error window that says "***Could not start process Cannot talk to klauncher: The name org.kde.klauncher was not provided by any .service files***"

The Guy who was guiding me in kde/krita forum said, it seems to him that many dependencies are not installed and the main installation is broken. waiting for an update wont help. And said this is not problem of krita also specifically. It must be some problem with ubuntu :P

Now I'm clueless! Any idea?

If I run krita from the terminal, i get these -


```
krita
Legacy integer arithmetics implementation 
krita(3540)/koffice (lib pigment) KoColorConversionSystem::insertColorSpace: Cannot add node for  "YCBCR (8-bit integer/channel)" , since there are no profiles available 
krita(3540)/koffice (lib pigment) KoColorConversionSystem::insertColorSpace: Cannot add node for  "YCBCR (16-bit integer/channel)" , since there are no profiles available 
krita(3540)/koffice (lib pigment) KoColorConversionSystem::insertColorSpace: Cannot add node for  "YCBCR (32-bit float/channel)" , since there are no profiles available 
krita(3540)/koffice (lib kopageapp) KoOdfLoadingContext::KoOdfLoadingContext: could not parse manifest document 
krita(3540)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "ThumbCreator"  not found 
krita(3540)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "ThumbCreator"  not found 
krita(3540): couldn't create slave: "Cannot talk to klauncher: The name org.kde.klauncher was not provided by any .service files" 
krita(3540)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "ThumbCreator"  not found 
krita(3540)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "ThumbCreator"  not found 
krita(3540): couldn't create slave: "Cannot talk to klauncher: The name org.kde.klauncher was not provided by any .service files" 
krita(3540)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "ThumbCreator"  not found 
krita(3540)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "ThumbCreator"  not found 
krita(3540): Couldn't start knotify from knotify4.desktop:  "KLauncher could not be reached via D-Bus. Error when calling start_service_by_desktop_path:
The name org.kde.klauncher was not provided by any .service files
" 


krita(3540)/kdeui (KNotification) KNotification::slotReceivedIdError: Error while contacting notify daemon "Failed to execute program /usr/bin/knotify4: Success" 

```


Tried to revert back to old krita version by removing the ppa and everything related about kde. but that led me many misisng dependancies. So added the backport ppa again and ran these commands...

```
sudo apt-get install -f &&
sudo apt-get clean &&
sudo apt-get autoclean &&
sudo apt-get autoremove &&
sudo apt-get update
sudo apt-get install aptitude
sudo aptitude install krita
```

But it didnt solved the problem.


**Ps. Sorry for posting in wrong section. Moderators please move it to proper section.**

---

### Post by SeijiSensei on 2013-03-17
First off, why not start with Kubuntu?  If you must use Ubuntu as the base, try installing "kubuntu-desktop" before installing krita.

---

### Post by EscapedNight on 2013-03-17
> **SeijiSensei said:**
> First off, why not start with Kubuntu?  If you must use Ubuntu as the base, try installing "kubuntu-desktop" before installing krita.

But why I will need whole kde desktop for an app only?

---

### Post by SeijiSensei on 2013-03-17
You'll get most of the major dependencies.  It's not all that large either by modern standards, perhaps a few hundred megabytes.

Your problem could be the PPA.  Apparently the packager did a poor job of specifying the required dependencies if they weren't brought in automatically.

---

