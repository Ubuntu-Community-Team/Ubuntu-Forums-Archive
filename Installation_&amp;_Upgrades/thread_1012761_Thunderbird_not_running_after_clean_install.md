---
title: "Thunderbird not running after clean install"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2008-12-16
Does anyone have experience of this problem? I have posted a similar message in the Thunderbird support conference of mozilla, but so far no one has replied. As it is urgent I have also posted here.

TB is running but is not responding

In order to do a clean install, I zapped the root directory and reinstalled Ubuntu intrepid. As I have a seperate directory for the home, I continued to use it but created  a new user (rob) on installing Intrepid. Previously the user had been robin. Upon advice from this  conference,  I have copied the hidden files in the home of robin  to the new home of rob. With other programs this has worked, including FF.

I would prefer not to have to make a new profile in TB because I have spent a lot of time building it up.

I did have a .parentlock in the profile directory but I have removed it.

I notice the profile ends in Rob where as the new login name is rob. It is in the home/rob directory so I assume  x8thazak.Rob will make no difference.

Profile.ini contains:

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob
```

The profile directory contains the following:


```
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/XUL.mfl
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/XUL.mfasl
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/xpti.dat
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/XPC.mfasl
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/virtualIdentity.rdf
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/virtualFolders.dat
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/user.js
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/urlclassifier2.sqlite
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/translation.rdf
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/training.dat
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/storage.sdb
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/secmod.db
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/prefs.txt
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/prefs.js~
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/prefs.js
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/persdict.dat
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/panacea.dat
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/mimeTypes.rdf
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/mailViews.dat
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/localstore.rdf
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/localstore-safe.rdf
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/key3.db
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/install.log
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/history.mab
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/fromfccdata.txt
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/extensions.rdf
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/extensions.ini
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/extensions.cache
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/downloads.rdf
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/defaults.ini
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/cookies.txt
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/compreg.dat
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/components.ini
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/compatibility.ini
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/cert8.db
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/blocklist.xml
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/abook.mab
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/abo
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/a
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/17130852.s
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/WebmailData
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/US
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/prefs.js backup
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/Mail
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/extensions
/media/mydocs/Thunderbird profiles/Profiles/x8thazak.Rob/chrome

```

---

