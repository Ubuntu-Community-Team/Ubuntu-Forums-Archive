---
title: "Update Manager not updating"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by edwardp on 2009-11-10
I have been having an issue with the Update Manager not indicating updates are available.  Xubuntu 9.10 was installed three days ago on two systems, but on the laptop, it's working perfectly.

On the desktop system, when I manually laumched the Update Manager tonight, it tells me that the information was last updated 3 days ago, which is when I installed the software.  Three days ago, it downloaded and installed the available updates released since 9.10 was released.  

Yet on the laptop, there were 26 new updates last night and another 11 this evening.  The laptop retrieved and installed all of them without any issues.

I would like to find out why the Update Manager isn't working correctly on the desktop, which is a dual-boot with Windows XP.

I noticed that out of the 37 updates it found tonight (after I manually launched the updater and selected to check for updates) two were pertaining to the Update Manager.  Could these updates have fixed whatever the problem might be??

The settings indicate that it is to check for updates daily and to prompt when they are available, but it has not been finding them for some reason, automatically.

Thank you for any assistance.

---

### Post by winotree on 2009-11-10
The one that you updating manually -- *click* Check.  This asks it it to check itself and invariably you'll get those updates.  [Had the same thing happen to me early on].  ;)

---

### Post by edwardp on 2009-11-12
I received word today that someone else is experiencing the same issue and his laptop retrieved 67 updates.

Is there something "behind the scenes" at work that perhaps forces this to check at a certain time of the day, even though that it is set to check daily for updates?

---

### Post by edwardp on 2009-11-14
I guess I'm going to have to check it manually each day, as it is obviously not checking daily per the settings.

---

### Post by edwardp on 2009-11-16
It has yet to start automatically on the desktop (specs below) and would like to know if there is something that I should look at in order to find out why it is not working automatically.

Thank you.

---

### Post by winotree on 2009-11-17
There were 23 or 24 updates at 1050am CST [US] and I was notified via my device -- the method that doesn't seem to work on yours.  QUESTION - did you get a notice and can you get those updates?  Just asking.  :)

---

### Post by edwardp on 2009-11-17
I installed this software over a week ago and have yet to see the updater run automatically on this desktop.

On my laptop, each day, the updater runs about 20 minutes after I have logged in (regardless of the time of day) and when it ran last night on the laptop, there was an icon that appeared indicating it was checking for updates, then it disappeared as no updates were available.

Again, I have yet to see this occur on the desktop.

To answer your question, no.  If the icon is this "notice" you are referring to, no.  I have yet to see it appear automatically.  If I go in and run the Update Manager manually (Applications/System/Update Manager and select Check), it will then check for updates and display which ones are available, if any.  During which, the icon will appear on-screen, but only if I run it manually.

The desktop has been on for 30 minutes now for the first time today, the updater has not run.

The forum software will not allow the /etc/cron.daily/apt file to be attached, but I can tell you that it seems like the entire first half of that file, has been pounded (#) out, lines like **APT::Periodic::Enable "1"** are pounded out.

---

### Post by klm3030 on 2009-11-17
I am having the same issue, but mine started with 9.04.  I have tried everything  but still will not automatically check and notify.  Works just fine manually.

---

### Post by edwardp on 2009-11-18
> **klm3030 said:**
> I am having the same issue, but mine started with 9.04.  I have tried everything  but still will not automatically check and notify.  Works just fine manually.

Thank you for replying.  I'm glad to know that I am not the only one having this problem.

---

### Post by edwardp on 2009-12-11
> **klm3030 said:**
> I am having the same issue, but mine started with 9.04.  I have tried everything  but still will not automatically check and notify.  Works just fine manually.

See if [http://ubuntuforums.org/showpost.php?p=8457121&postcount=3](http://ubuntuforums.org/showpost.php?p=8457121&postcount=3) will help.  

I added those lines to /etc/init/anacron.conf and rebooted one of the desktops.  Five minutes after, anacron ran as well as the updater after 30 minutes, its icon appeared next to the clock.

This resolved my issue with the system updating.  :grin:

---

