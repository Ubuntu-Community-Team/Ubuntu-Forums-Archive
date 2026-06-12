---
title: "Firefox addons won't install"
date: 2008-07-24
forum: General Help
---

### Post by midnightToker on 2008-07-24
Just installed Hardy on a Lenovo Thinkpad T61.  Everything works great, haven't had any issues, except for a weird bug in firefox.  I can't install addons.  I've installed plugins and themes, so those are not affected.  But regardless of where I try to get the addon (mozilla.org or the individual project page) nothing happens when I click the link to "install now".  It just hangs.  I cannot right-click and save the link either - same problem.  The addons interface just says "connecting..." indefinitely.  

I found a workaround, which is to find the addon I want, right click the "install now" button, and copy the link location.  Then I switch to terminal and wget that link.  I switch to firefox and choose File -> Open File and then the addon installs no problem.  Obviously that's not a long-term solution though.

To date, I've tried uninstalling and re-installing firefox (apt-get remove firefox-3.0, apt-get install firefox-3.0).  Then I tried install firefox-2.  Then I removed firefox-2 and tried deleting my profile (~/.mozilla/firefox/xxxxxxx.default).  Then I deleted the entire ~/.mozilla folder.  None of those worked.

Any ideas?

---

### Post by kerry_s on 2008-07-24
are you sure there ff3 compatiable?
have you tried the internal add on installer? (tools> add-ons> get add-ons)

---

### Post by midnightToker on 2008-07-24
I'm sure.  The main one I use is foxmarks.  I also use nuke anything enhanced.  I've been using foxmarks and FF3 for months now on several different computers and OS's.  Also, when I used wget to download foxmarks and then installed it manually, I had no problems.

I did try the internal installer, that's what just says "connecting..." at the bottom.  It's almost like firefox is refusing to download anything with .xpi file extension!

---

### Post by amoran on 2008-08-02
I am seeing the same behavior on my Lenovo IdeaPad Y510 with ff3.01 on hardy.  The add-on's manager just sits there saying "connecting...".

The work-around of downloading the add-on to the filesystem and installing from there works.

---

