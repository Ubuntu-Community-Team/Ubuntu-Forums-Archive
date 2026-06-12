---
title: "Upgrade to Jaunty breaks Thunderbird"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by tlpintpe on 2009-04-28
I upgraded to Jaunty two days ago and have had some issues to work through.  The most troublesome is related to Thunderbird.

Thunderbird will open, but it immediately throws an error, which I have copied here:
[I]
Could not initialize the browser's security component.  The most likely cause is problems with files in your browser's profile  directory
has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the browser and fix the
problem.  If you continue to use this browser session, you might see incorrect browser behaviour when accessing security features.[/I]

When I click on one of my imap accounts the following error message pops up:

*Thunderbird cannot connect securely to xyz.com because the SSL protocol has been disabled.*

I have attempted to view the SSL certificates in Thunderbird (Edit>Preferences>Advanced>Certificates), but every time I click on View Certificates Thunderbird crashes.

Any ideas?

---

### Post by tlpintpe on 2009-04-29
bump...any help out there?

---

### Post by alphacrucis2 on 2009-04-29
> **tlpintpe said:**
> bump...any help out there?

I didn't have thunderbird installed so I just installed the package to try it out. I tested it against an imap server and it worked fine. Maybe you should try uninstalling and reinstalling the package. I don't know if that risks losing your address book and stored messages so you might want to back all that up first.

---

