---
title: "[SOLVED] RapidSVN crashing after subversion update"
date: 2008-09-11
forum: General Help
---

### Post by belfasttim on 2008-09-11
Hi--

I've been using RapidSVN 0.9.4-3 on Ubuntu 8.04 for a few weeks with no issues-- worked great, and was very reliable.

I included a subversion update (1.5.1dfsg-1ubuntu) from Hardy backports that came through the other day, and anytime I try to connect to a remote repository the RapidSVN application crashes. No error message, just disappears. The local working copy works fine, but when I go to commit it crashes.

The same thing happened now when I installed kdesvn-- connecting to the remote repository crashed the program.

Any help much appreciated.

---

### Post by yrrej on 2008-09-11
I don't think rapidsvn supports the 1.5 version of subversion
yet...

Jerry

---

### Post by belfasttim on 2008-09-11
Got it running, had to uninstall and compile form source the subversion and rapidsvn tools, and the wxwidgets/python libs.

thanks

---

### Post by derbouka on 2008-09-16
Hi!

Can you point (url) some tutorial to do that?

Best regards,
Daniel Botelho

---

### Post by belfasttim on 2008-09-16
> **derbouka said:**
> Hi!

Can you point (url) some tutorial to do that?

Best regards,
Daniel Botelho

Hi Daniel-- there's tutorials on both the rapidsvn project page and the subversion page-- the manual for subversion also has the how-to at this link-- [http://svn.collab.net/repos/svn/trunk/INSTALL](http://svn.collab.net/repos/svn/trunk/INSTALL)

Good luck

---

