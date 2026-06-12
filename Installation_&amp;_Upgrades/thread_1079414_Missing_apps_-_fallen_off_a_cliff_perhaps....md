---
title: "Missing apps - fallen off a cliff perhaps..."
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by larryfroot on 2009-02-24
Hi,

Firstly I have no idea why I have ubuntu gutsy displayed to the left. I am using intrepid.

Just the way my day is going I suppose. Anyways....

Either synaptic or gnome are throwing a wobbly here, but when I add a new application via synaptic or cli, a corresponding menu launcher isn't made. I know that the two apps I have downloaded do get included as menu items. And the menu editor has no sign of them either. Nor does using the full name (case sensitivity noted) of the app in a terminal launch either of them. When I try to install it again via apt/cli I am told the the app is already installed. Its just that I have no way of launching it!

Ironically I have come across this problem whilst making a training video for my friends who are interest in abandoning windows. This is a real show-stopper and I would really appreciate any help anyone can give me.

Just to emphasise - case sensitivity and full app name given in terminal.

Apt tells me that app is installed, but won't launch it. 

There is zilch in either my menu or in the menu editor - and I know that they have entries in the menus as I have had them before. 

Please help! Thank you!

---

### Post by larryfroot on 2009-02-24
OK...this is interesting. I had a thought...I have installed kubuntu 4.2 before I installed deluge and epiphany in gnome. Guess what? The working menu entries are there in KDE, but absent in Gnome. Heck, even the cli in gnome don't wanna know. Anyway to rectify this? If I just uninstall kubuntu will the issue right itself? Prob not, but if anyone has light to shed on this that would be great!

---

### Post by jtrindle on 2009-02-24
check out /etc/xdg/menus and see if you have:

applications.menu

That file went missing on my home system and I lost all menu options in gnome except the custom ones I had created myself.

In my case copy the dist version to applications.menu did the trick (more or less).

---

### Post by larryfroot on 2009-02-24
Thank you! Really appreciate your input!

Checked but applications menu was all present and correct. However trying out some of the locations given in the xml of the various menu files on offer I came across one possible discrepancy in /etc/xdg/menus/settings.menu referred to... 

<!-- Ensure we read from the old capplets .desktop location -->
  <LegacyDir>/usr/share/control-center-2.0/capplets</LegacyDir>

I checked out /usr/share/control-center-2.0/capplets and all I saw was a solitary .png 

Mind you, I wouldn't know what a capplet is if it gave me a hundred pounds in the street. 

It isn't so much the files but what it is that writes to those files. Its been hijacked by kubuntu! If anyone knows where to look and what to look out for, that would be a Good Thing. A Very Good Thing! But thanks for your help and your time and perhaps this might be a learning experience for both of us.

---

### Post by larryfroot on 2009-02-24
...ah well, I can't really afford the time it might take to answer this one. Sadly, as I would have loved to learn what it is that writes the xml menu entries and how it operates. But at least I have learned that having parallel installations of ubuntu / kubuntu may lead to various conflicts like the one I have had. Hope this bit of info is useful to someone, and thanks again for replying. LF

---

