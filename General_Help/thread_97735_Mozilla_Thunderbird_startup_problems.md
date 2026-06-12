---
title: "Mozilla Thunderbird startup problems"
date: 2005-12-01
forum: General Help
---

### Post by WebDrake on 2005-12-01
Hello all,

I've been having some problems with Thunderbird 1.0.7 on my newly-installled Ubuntu system.

Here's what I've done: I was running TB 1.5 release candidate 1 on Windows XP Pro.  I copied across the profile to a folder on a shared FAT32 drive and, using Thunderbird Profile Manager, set up the profile in Ubuntu to use that directory.

On initial startup I can click on the Thunderbird icon; the program loads, all email is there, it connects---all is good.  However, double-clicking on emails to open them results in---nothing.  (The preview pane, on the other hand, works fine.)

However, if I close Thunderbird, then try to reopen it, nothing happens.  If I go via the Profile Manager and try to start the profile from there, I get an error message that the profile is already in use.... but a "top" command reveals no sign of a still-running Thunderbird process.

Any ideas?

Many thanks,

        -- Joe

---

### Post by aysiu on 2005-12-01
I don't know how to fix it, but in the future I'd advise against sharing Thunderbird preferences between Windows and Linux (I know it can be done--I'm just advising against it) and between 1.5 and 1.0.7.

If you find yourself constantly using both Windows and Ubuntu, I'd invest in a bit more disk space and use IMAP instead of POP for checking email.

If you're already using IMAP, there should be no reason to share profiles between the two OSes.

---

### Post by WebDrake on 2005-12-01
OK.  Well, the most important thing is that I have a load of old email that I would like to keep track of, and that I want to have the same message folders (inbox, sent items, etc. etc.) from both OS's.  Any way of effectively doing this?

Many thanks,

        -- Joe

---

### Post by BlueNoteMKVI on 2005-12-02
Yup - use imap.  Unless you configure it differently the imap protocol will store your messages on your mail server, so wherever you happen to be you're reading the same mail.  I read mail from:

-My desktop computer, in Linux, running Thunderbird
-The same computer, occasionally booted to Windows, running Thunderbird
-My laptop, running Thunderbird
-My Treo, running SnapperMail
-Occasionally a computer at a friend's house or at school, using WebMail

Since all of those locations use the imap protocol my messages always show up the same (include read/unread status, replied, etc) wherever I am.

---

### Post by WebDrake on 2005-12-02
I have managed to solve this problem without IMAP as follows: rather than copying across the whole profile folder, I set up a new profile under Ubuntu and replicated the account settings from my previous profile.  Then, I copied across, not the complete profile, but just the mail storage files---i.e. Inbox, Inbox.msf, etc.

This works fine under Ubuntu.  I rebooted into Windows and pointed a new profile at this directory; it also recognised it without problems.  This new profile seems to work fine under both XP and Ubuntu without problems, though just to make sure I am now running TB 1.0.7 on both platforms.

Out of curiosity, what's the schedule for Ubuntu to update its servers to include FF 1.5? :-P

Best wishes,

          -- Joe

---

