---
title: "My gripe about package managers"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by pixeltecs on 2009-06-23
This may be my lack of knowledge but I have used Ubuntu since 8.04 and have never really gotten along with the package manager.  I've used other linux variants prior, as well and never get along with any of the package managers.  Here's an example of a problem I have with it.  I use Pidgin for IM.  Pidgin/Yahoo recently broke because Yahoo is upgrading servers and their protocol has changed.  I found that the fix is to upgrade to Pidgin 2.5.7.  Actually, I found a work around in my current version but let's pretend like I didn't since my workaround will eventually break anyway.

So, what do I do?  I like that the package manager works with the update manager and I get patches to things and sometimes new versions of software.  I don't want to lose this capability by circumventing the package manager and installing Pidgin.  Then again, I want my problem solved and it seems that I have no choice but to do this.  So, from now on, I will have to remember to periodically check that there aren't patches and updates to the new version of Pidgin.

It's not just Pidgin, this happens to me all the time.  Depending on my urgency, I will go around the package manager.  I have seen that you can change software sources.  It's not clear if that's what I want.  It seems like I want to select a different software source for just this one package.  ...but I don't think you can do that.

Anyway, if anyone knows of a solution to this problem for Ubuntu, I'd love to hear it.  Otherwise, if anyone knows of a project that wants to solve this problem, I'd love to get involved.

I think if I were to sketch it out, it would work something like this: The package manager points to organized collections of software projects.  The community or a core team could vote/select stable versions and rate software and patches to give clients a good sense of stability and security.  However, an end user could override the community setting and grab the latest version through the package manager and still receive updates as that version moves into community accepted stability.  BTW, if anyone has ever used freebsd's ports system, it seems to have a little flavor of what I want.

The End

---

### Post by pixeltecs on 2009-06-24
So, interestingly enough, my Pidgin workaround broke almost immediately.  So, I caved and just decided to install the latest version which revealed something to me.  Apparently, there is at least a mechanism for altering your package manager like I want because that's what the Pidgin folks do.  To make an install, they provide the sources but also give the script to link your package manager (apt) to a PPA that they provide.  This allows you to receive future updates of Pidgin from them through the package manager.  So, even though I'd like an easier front end for managing your packages, this seems to give me the functionality I wanted.  I have essentially added an override of the jaunty repository list for this one package, Pidgin.  If you are interested in more details, look into PPAs.

---

### Post by tenach on 2009-06-24
I believe it's more of an addition than an override.  I just recently had to do that with my installation, and that of two other computers.  I'm glad that the Pidgin people at least put easy instructions up... otherwise I would have just uninstalled Pidgin, downloaded the newest, and compiled from source.

---

