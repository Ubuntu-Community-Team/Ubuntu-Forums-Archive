---
title: "Update Manager not running daily - Jaunty"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by TheOldFellow on 2009-05-23
Since updating to Jaunty, neither of my systems automatically runs Update daily, although that is the setting in the preferences for Update.
I know that updates are coming through, as they arrive fine if I run update manually.
Is this a bug, or something to do with my set up?

---

### Post by Brandon Williams on 2009-05-23
This issue is discussed in [the release notes](http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates), and several times in the forums. You'll always get faster responses to a search than a post :-)

---

### Post by TheOldFellow on 2009-05-28
I read that, but the command given does not return the system to the same behaviour as, say Intrepid.  This command just stops the update manager running at all.  The release notes are extremely misleading - I'd say wrong.

And I did search, but found nothing helpful.  This probably says more about my search abilities than what is available though.  My intense dislike of Forums probably doesn't help - Usenet rules OK (but not for Ubuntu).

---

### Post by Brandon Williams on 2009-05-28
The command given returns my system to precisely the same behavior as I had in previous releases. Updates are checked daily and the icon appears if updates are available.

Double check the Updates tab in the Software Sources capplet to make sure that you have both jaunty-security and jaunty-updates checked, that you have a check next to 'Check for updates' with Daily selected, and that you have selected the 'Only notify about available updates' radio button. If you have any different settings than this, then you might be experiencing a bug that I wouldn't see due to configuration differences.

---

### Post by TheOldFellow on 2009-05-30
Well, as they say, your mileage may vary'.  This command does not work for me.  Not on either of my machines.

---

