---
title: "Kubuntu 9.10 Firefox Installer works?"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by another_sam on 2009-11-07
Today I installed Kubuntu 9.10 on a machine, and the Firefox Installer did not work properly: at the end of the process it said something like "Firefox is already installed", and accessing Applications > Internet menu for the second time showed again the Firefox Installer instead of Firefox.

Is it just my case? Did any of you test this?

Thank you.

---

### Post by Marlonsm on 2009-11-07
It worked for me. After installing I had both the FF installed and FF in the menu, so I removed the installer.
You can try getting Firefox with kPackagekit.

---

### Post by pwrcul on 2009-11-07
I had the same problem with the Kubuntu netbook 9.10 which I installed today.

I used KPackagekit to remove kubuntu-firefox-installer then reinstalled it and ran it.  It worked then and installed FF.

It's icon hung around along with the Firefox Browser icon.  Maybe if I had rebooted, the icon would have disappeared.  But I used KPackagekit to remove it, rebooted and it was gone.

---

### Post by pwrcul on 2009-11-09
I had to do a fresh install so I had a 2nd try at this.  

This time the Firefox installer worked right away.

I restarted Kubuntu and found the kubuntu-firefox-installer was still in the internet folder so I still had to use KPackagekit to delete it.

---

### Post by another_sam on 2009-11-11
I think the behavior should be to automatically remove kubuntu-firefox-installer and its icon from the menu, immediately after executing kubuntu-firefox-installer . Don't you think so? I think I will report this as a bug.

( I searched and it does not seem to be already reported: [https://bugs.launchpad.net/~kubuntu-bugs?field.searchtext=kubuntu-firefox-installer&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/~kubuntu-bugs?field.searchtext=kubuntu-firefox-installer&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=) )

---

### Post by pwrcul on 2009-11-11
I agree, another_sam.  I would appreciate your entering a bug report.

---

### Post by another_sam on 2009-11-14
oh, my bad. It was already reported. Just searched on the wrong place. I am not used enough to Launchpad.

You can search here:
[https://launchpad.net/ubuntu/+bugs?field.searchtext=kubuntu-firefox-installer&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/ubuntu/+bugs?field.searchtext=kubuntu-firefox-installer&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)
And find the bug:
[https://bugs.launchpad.net/ubuntu/+source/kubuntu-firefox-installer/+bug/439431](https://bugs.launchpad.net/ubuntu/+source/kubuntu-firefox-installer/+bug/439431)

So, fix comitted. It will be for 10.04. 

Thanks anyway guys!

edit: and if I used Google better, I would found it through "Show more results from launchpad.net" at [http://www.google.com/search?q=kubuntu+firefox+installer+bug&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=kubuntu+firefox+installer+bug&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by pwrcul on 2009-11-15
Thanks for the update and the links, another_sam.

I am glad a fix is committed in the next release.

You are ahead of me in terms of Launchpad.  I will sign up either today or the near future.

Your search links will help me see if other issues I have experienced have already been addressed by showing how you went about your search.

Guiseppe Pennisi in his bug report at
[https://bugs.launchpad.net/ubuntu/+source/kubuntu-firefox-installer/+bug/439431](https://bugs.launchpad.net/ubuntu/+source/kubuntu-firefox-installer/+bug/439431)
has a long context section/signature for the developers.  I will have to work one up.

---

