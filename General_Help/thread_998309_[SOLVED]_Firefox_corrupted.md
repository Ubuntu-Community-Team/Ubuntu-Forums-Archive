---
title: "[SOLVED] Firefox corrupted?"
date: 2008-11-30
forum: General Help
---

### Post by AlanInVancouverBC on 2008-11-30
After getting Google Earth for Linux/Ubuntu working properly with my imported Places (from XP), Firefox is behaving very strangely, and not well at all.
It opens to a blank page, not my homepage.
It doesn't show any bookmarks.
It won't open bookmarks manager.
It won't connect with Foxmarks. 

I tried uninstalling and reinstalling Firefox with no change in behaviour.

There's a screenshot for what it's worth of the Foxmarks trying to connect without success attached. The bar just keeps panning left to right, without end.

I'm afraid to dig deeper in the uninstalling process because Ubuntu is WUBI'd into a dual-boot with XP (from which I am posting this message).

Any safe suggestions would be appreciated.  :(

---

### Post by OrangeCrate on 2008-11-30
I'd suggest reinstalling Firefox, and then enable the Medibuntu repositories if you haven't already done so.

Google Earth will then be in Synaptic available for you to install. That might work better than trying to import it.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[http://ubuntu-tutorials.com/2008/01/29/medibuntu-the-only-3rd-party-repo-i-use/](http://ubuntu-tutorials.com/2008/01/29/medibuntu-the-only-3rd-party-repo-i-use/)

---

### Post by AlanInVancouverBC on 2008-12-01
I've got Google Earth installed properly.
I've uninstalled and reinstalled Firefox, but the same problem appears. It seems that in uninstalling, I'm not deleting all Firefox files, including especially my preferences, my add-ons. (BTW, I wish Firefox named their files and folders by intuitive names. There are 2 chrome folders (whatever chrome is supposed to mean). My bookmarks are in a default folder, rather than in a folder that hold all my preferences and add-ons. Etc.
So, with me entering this from my XP logon, what other files need to be deleted so that I can have a clean Firefox install in Ubuntu?
I.E. What are ALL the files that need to be deleted in Firefox for Ubuntu? I think that if I deleted that, I would be deleting the corrupt file that is causing my worries.
BTW, again, I can use Firefox in Ubuntu, but another problem I'm having, and why I need to use XP for this message is that when I entered this note, clicking on the preview post or submit reply did nothing, nothing. 

Any suggestions would be appreciated.
Alan (frustrated in Vancouver BC)

---

### Post by fooman on 2008-12-01
your firefox profile/configuration files are in a hidden directory named .mozilla

here is how to completely delete it:

first back up your bookmarks,  then go to places > home folder.

in the toolbar,  click on "view" and put a check next to "show hidden files"

find the .mozilla file,  right click on it and choose "send to trash".

a new .mozilla file will be created when you open firefox again.

---

### Post by AlanInVancouverBC on 2008-12-02
Excellent!
That's exactly what I needed to get.
Succinct, accurate, easy.
Thanks.
Again: I'd wish that programmers would label their files and directories with user-friendly names, unlike this OS and Firefox as examples.

---

