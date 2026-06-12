---
title: "Unable to upgrade from 9.04 to 9.10 beta"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by Contraste on 2009-10-18
I've tried to upgrade from Ubuntu 9.04 to 9.10 beta using the Update Manager (ALT + F2 >> update-manager -d). It works right until all the new packages have been downloaded. Then, when it is going to install them, the Update Manager shows an error dialog and doesn't install.
When I open it again (System > Administration > Update Manager), lots of packages are available to install and a dialog telling me to do a "partial upgrade" appears.

I don't know why this happens. Is there anything I must do before upgrading to a beta version (I was able to upgrade to Alpha 5 by the same method), or is this a bug?

Thank you.

---

### Post by bulldog on 2009-10-18
If you have any third party repositories in your sources.list,just disable them.
Then do the partial upgrade as stated and it should be fine.

I installed the beta a while ago,and I had to do a partial upgrade after a few days as well,so no worry about that one.

---

### Post by peakshysteria on 2009-10-18
> **Contraste said:**
> I've tried to upgrade from Ubuntu 9.04 to 9.10 beta using the Update Manager (ALT + F2 >> update-manager -d). It works right until all the new packages have been downloaded. Then, when it is going to install them, the Update Manager shows an error dialog and doesn't install.
When I open it again (System > Administration > Update Manager), lots of packages are available to install and a dialog telling me to do a "partial upgrade" appears.

I don't know why this happens. Is there anything I must do before upgrading to a beta version (I was able to upgrade to Alpha 5 by the same method), or is this a bug?

Thank you.

It was the same for me. I just went to System --> Administration --> Software Sources and changed Download from to another country than the default (Norway in my case) to United States. Then once again I ran ALT + F2 --> update-manager -d

Everything then went smooth.

---

### Post by dkknight593 on 2009-10-18
I think it's a bug.

I had same problem.  Attempting partial upgrade messed up gnome.

I tried to upgrade some packages I thought were important manually through Synaptic.
Then I restarted and started recovery mode.  chose repair packages and for the most part my system is up and running again.

Well sort off.  Hal_lpadmin keeps crashing.  And coming out of screen saver does not show log in screen.

-venk

---

### Post by Contraste on 2009-10-18
I changed "Download from" to United States in the Software Sources Menu and started the Update Manager. It finally did! Thank you all guys!

---

### Post by peakshysteria on 2009-10-18
Good things man. Nice to hear it. Please mark the thread as **Solved** so other people might solve their problems as well.

Happy days.

---

