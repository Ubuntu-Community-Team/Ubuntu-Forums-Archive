---
title: "[SOLVED] Firefox not working"
date: 2008-10-24
forum: General Help
---

### Post by joey-elijah on 2008-10-24
Hey all. Earlier on Firefox crashed and since then it's not working. It launches but there's no homepage - or error - even tho there's one specified, no bookmarks, nothing.

I've uninstalled it and re-installed it but it makes no difference. I'm currently using Epiphany to type this - which is working fine! 

Any clues as to what may be up or how to get it to work again?

Of note, when i've uninstalled it the nreinstalled it - it seems to have picked up my profile and add-ons okay as they've been there.

---

### Post by dcstar on 2008-10-25
> **joey-elijah said:**
> Hey all. Earlier on Firefox crashed and since then it's not working. It launches but there's no homepage - or error - even tho there's one specified, no bookmarks, nothing.

I've uninstalled it and re-installed it but it makes no difference. I'm currently using Epiphany to type this - which is working fine! 

Any clues as to what may be up or how to get it to work again?

Of note, when i've uninstalled it the nreinstalled it - it seems to have picked up my profile and add-ons okay as they've been there.

Uninstalling will not remove your profile, and if your profile is corrupted then that can stop Firefox starting.

Rename the hidden .mozilla directory in your home folder, start Firefox (which will create a fresh profile), and then import/move data from the old folder that you need (like bookmarks).

---

### Post by sethvath on 2008-10-25
Another way to access profile-manager

In terminal
path/to/application -profilemanager

---

### Post by ju2wheels on 2008-10-25
Did you open firefox using sudo at any point? This should never be done and sounds like what you may have done accidentally.

If you didnt delete your firefox settings directory in your home folder yet then run this in a terminal where user is your user name:

```

sudo chown -R user:user ~/.mozilla

```

Then see if Firefox launches normally.

---

### Post by sacauntos on 2008-10-25
Hi, I'd just made the last updates to my system (running hardy) and after that, I noticed some weird behaviors in some apps, mainly firefox. My bookmarks disappeared and the forward and back buttons stopped working. 

I looked for someone with same problems here, and while I was going to do what you have suggested in this thread and backup .mozilla I realized that I didn't have any (0) space in my hard-drive. It looks like my old laptop (40 GB of HD) was completely stuffed and the latest updates filled it up completely. I freed some memory and it all started working again as usually. No need to do anything else.

I don't know if this could also be your problem (not likely if you have a semi-decent HD and not a 5 year-old laptop!). It is just my empirical experience... Good luck!

---

### Post by joey-elijah on 2008-10-25
> **ju2wheels said:**
> Did you open firefox using sudo at any point? This should never be done and sounds like what you may have done accidentally.

If you didnt delete your firefox settings directory in your home folder yet then run this in a terminal where user is your user name:

```

sudo chown -R user:user ~/.mozilla

```Then see if Firefox launches normally.

tried it and yes it did launch normally! Thank you! Not sure how i'd messed it up in the first place though, but hey ho!

---

