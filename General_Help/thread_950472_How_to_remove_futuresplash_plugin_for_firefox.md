---
title: "How to remove futuresplash plugin for firefox?"
date: 2008-10-17
forum: General Help
---

### Post by bonk_ on 2008-10-17
I want this removed since it is probably the cause of conflict and crashing firefox upon entering flash sites.


In Firefox about:plugins under Shockwave Flash title it shows up as

application/futuresplash | FutureSplash Player

This plugin is not in the SPM, nor found when entering sudo apt-get remove futuresplash, nor found in Firefox's Tools>Add-ons>Plugins

in term I type 'locate libflash' and get:

/usr/lib/libflashsupport.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
/usr/lib/opera/plugins/libflashplayer.so

could it be the first one? if so how do I remove it?

---

### Post by spawn. on 2008-10-17
It may be easier to remove Firefox 3.0 and ALL of its associated files via synaptic. Keep Adobe Flash 10 and re-install Firefox 2. It will solve your crash problem until they fix the bugs.

---

### Post by ajgreeny on 2008-10-17
In FF3, go to Tools->Add-ons and in the Plugins tab disable the Futuresplash plugin.  It may work, or it may not, but I find FF3 much better and quicker than FF2, so would try to avoid going back to v2, if I were you.

---

### Post by bonk_ on 2008-11-08
Bump!

Is it impossible to heave this software out?? To wait for an update to fix this is getting ridiculous... there must be a way to surgically remove it somehow?

bonnk

---

### Post by spawn. on 2008-11-08
All you have to do is add a repository that includes the older version of Firefox with Adobe Flash version 9, then uninstall the newer version and Flash 10. 

BUT, I have noticed that there are no more crashes with Firefox version 3.0 and Flash version 10. I think they may have released enough updates to fix this problem. I haven't experienced a crash since _I've been regularly installing the updates._

Here is a screenshot of the repositories that I have. One of these babies has the Firefox version 2 with Adobe Flash version 9. Sorry about the size...

[IMG]http://i279.photobucket.com/albums/kk154/70rr/Screenshot.png[/IMG]

---

### Post by spawn. on 2008-11-08
As an alternative to reinstalling Firefox version 2, you can simply uninstall the Flash version 10 and install the Flash version 9 into Firefox 3. 

Reverting to Flash verion 9 also solves the problem where Flash version 10 fails to play YouTube videos. I noticed there are times when the Flash  version 10 just fails to load properly and there is a huge delay before anything happens, if at all.

---

