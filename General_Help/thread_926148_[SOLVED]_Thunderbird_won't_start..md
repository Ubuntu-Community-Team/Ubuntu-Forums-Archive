---
title: "[SOLVED] Thunderbird won't start."
date: 2008-09-21
forum: General Help
---

### Post by jmcgovern on 2008-09-21
I'm having trouble with Thunderbird at the moment.  It was installed for a while before I used it.  When i started it up, it asked me to create a profile, as usual.  I attempted to do so, but it gave me an error having to do with permissions.  I chowned my .mozilla-thunderbird folder to my username (t was owned by root), and attempted to restart thunderbird.  It's now telling me that Thunderbird is already running but not responding.  This is an error id expect to see in Windows, not Linux. It still happens even after a complete uninstall and reinstall of Thunderbird.  I've run top several times, and I can't see Thunderbird listed as any of the processes.

---

### Post by fooman on 2008-09-21
have you tried restarting the computer? ...or this:

```
sudo killall thunderbird-bin
```

---

### Post by jmcgovern on 2008-09-21
I've restarted several times, including between the complete removal of Thunderbird and reinstallation.  Running the suggested command returns 'no process killed'.

---

### Post by projectgonewrong on 2008-09-21
Try going into System>Administration>System Monitor   then finding the Thunderbird process then kill/end it.  I sometimes get this with Firefox, and normally just doing that or logging off then back in works for me.

---

### Post by jmcgovern on 2008-09-21
Thunderbird doesn't appear in System monitor anywhere.  I get the error even after a completely fresh boot. without starting anything up manually.

---

### Post by pieoncar on 2008-09-21
I'm pretty sure Thunderbird uses "lock" files.  Can you try removing ~/.mozilla-thunderbird (or renaming it to something else for a moment) and run Thunderbird again?  Would it be very bad if you had to make your new profile again?

---

### Post by jmcgovern on 2008-09-21
That solved it.  for some reason, the profile wasn't deleted when I removed Thunderbird the first time, even though I had selected 'complete removal'.

---

### Post by Tips on 2008-09-30
Thanks, I've been trying to figure this out for hours.  Even a complete uninstall didn't work, but deleting the ~/.mozilla-thunderbird directory worked.

---

### Post by Tips on 2008-09-30
Here's a more detailed explanation on how I fixed it on my computer:

[LIST=1]
[*]backup your existing ~/.mozilla-thunderbird directory.  Put that aside and start editing your active copy:
[*][find the .parentlock file]("http://kb.mozillazine.org/Profile_in_use") inside your profile directory and delete it
[*]go to ~/.mozilla-thunderbird and check that profiles.ini isn't blank.  If it's blank, then rename it to profiles.ini.BAK and starr thundebird.  Thunderbird wii create a new one and a new xxxxxx.default profile.  Close Thunderbird and edit the new profiles.ini file so that it contains the name of your original xxxxx.default profile and not the new xxxx.default one.
[*]restart Thunderbird and everything should be restored...
[/LIST]

---

