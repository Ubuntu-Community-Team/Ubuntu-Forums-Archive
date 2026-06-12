---
title: "select other application to open Firefox media"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by hgraham on 2009-10-08
I am trying to change the default Firefox media player for streaming audio.  In Firefox Preferences Applications I want to change the associated programs for various file types.  An option for "use other" is provided and it displays the home folder tree.  How do I select the desired program from this home folder tree?  A list of available programs is not offered.

---

### Post by aysiu on 2009-10-08
Try /usr/bin

---

### Post by hgraham on 2009-10-08
/usr/bin/vlc solved associating the audio files with a new player (in this case vlc) in Firefox. What I really wanted to do is to play the .pls files from Shoutcast and live365 in the vlc player.  I solved this by entering 'about:config' into firefox's address bar, and then located key 'browser.download.hide_plugins_without_extensions' and toggle it's value to 'false' and then close the tab. Then I went to firefox preferences applications and searched for .pls and changed the file association to vlc by choosing 'use other' and selecting /usr/bin/vlc as the application. Both live365 and shoutcast now open in vlc.  Be sure to change the option in both shoutcast and live365 to play the streaming audio in other .mp3 player than the default.

---

