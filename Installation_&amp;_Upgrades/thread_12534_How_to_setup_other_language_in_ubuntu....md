---
title: "How to setup other language in ubuntu..."
date: 2005-01-25
forum: Installation &amp; Upgrades
---

### Post by caravana on 2005-01-25
hello..everyone

I 'm newbie for UBUNTU. I'm linux user in THAILAND.  r u know THAILAND :-)
I very like Ubuntu , I can instance read web page in THAI language  when  finish installed.
But, i can't use thai font in OpenOffice. ;-( 
Help me please..
How to setup Thai environtment  and  How to use Thai True Type Font in Ubuntu...

---

### Post by pseudonym on 2005-01-25
Hallo,

Language packs for Open Office are easy to install. You can do it in one of two ways -

1. Use Synaptic, Ubuntu's package manager. It's in Computer > System Configuration on English system. Click on 'All' in the top left-hand side - this loads all available/installed packages into the list on the right (a big list, but I find it easier this way). Just scroll down until you come to the Open Office section and you will see the Thai language pack there. Select it, right click and choose 'Mark for Installation', then go to the tool bar and click 'Apply' and this will begin the installation.

2. Use apt, the command line way of doing number 1 above -

sudo apt-get install openoffice.org-l10h-th

All this assumes that you have the language packs available, of course. I can't remember, but they should be in the standard repositories, I think.

:)

---

### Post by caravana on 2005-01-26
Hi..
Thanks ..pseudonym..


..I can apt-get the OpenOfficeTLE package from TLWG ([http://linux.thai.net](http://linux.thai.net))
and installed but not work :-(  

I will try  and thanks again..

---

### Post by caravana on 2005-01-27
hi...pseudonym
  and  Every body....

I can use synaptic get openoffice.org-l10n-th and installed.
But, I can't use THAI font in OO-Writer and all.
My thing 's system environment or X not THAI supported.

How to setup local language in ubuntu.????
help!!!  please!!!!

thanks....

---

