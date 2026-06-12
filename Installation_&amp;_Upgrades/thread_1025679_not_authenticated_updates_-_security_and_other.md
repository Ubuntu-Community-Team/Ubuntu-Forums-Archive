---
title: "not authenticated updates - security and other"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by arjay27529 on 2008-12-30
update manager is notifying that i have an "urgent" security update.  when i enable the update manager i receive a message that the updates are not authenticated.  i have attempted the same process with the command

sudo aptitude dist-upgrade   with these results

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libamrnb3 libamrwb3 
The following NEW packages will be installed:
  libamrnb3 libamrwb3 
The following packages will be upgraded:
  libavcodec1d libavformat1d libavutil1d libperl5.8 libpostproc1d mplayer 
  openoffice.org-help-en-gb openoffice.org-help-en-us 
  openoffice.org-l10n-common openoffice.org-l10n-en-gb 
  openoffice.org-l10n-en-za perl perl-base perl-modules 
14 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.9MB/31.1MB of archives. After unpacking 938kB will be used.
Do you want to continue? [Y/n/?] 

upgrade manager lists those files plus libamrwb3  libamrnb3  to be downloaded and installed.

1.  how do i verify that these are legitimate - even if not authenticated - update files?  

2.  how/why are these appearing in update manager if not authenticated?

total newbie here.

---

### Post by Partyboi2 on 2009-01-01
>  2.  how/why are these appearing in update manager if not authenticated?

Normally you get "cannot authenticate" from using 3rd party repositories. To my knowledge there has been no updates for these packages from the ubuntu repos lately. So maybe these are updates from 3rd party repositories that you have added.

---

### Post by arjay27529 on 2009-01-03
> Normally you get "cannot authenticate" from using 3rd party repositories. To my knowledge there has been no updates for these packages from the ubuntu repos lately. So maybe these are updates from 3rd party repositories that you have added.

thank you partyboi

is there a way to verify which 3rd party repositories ive added?

and a way to verify the "authenticity" of updates from them?

---

### Post by Pumalite on 2009-01-03
Medibuntu and Avant-Windows-Navigator are common ones.

---

### Post by Elfy on 2009-01-03
> is there a way to verify which 3rd party repositories ive added?

Open software sources in the system admin menu - you'll find a 3rd party tab - have a look there.

---

### Post by arjay27529 on 2009-01-04
thank you - forestpixie & permalite

have found listing and researched sources of "unauthenticated" updates.  will proceed and install them.

thanks again.

---

