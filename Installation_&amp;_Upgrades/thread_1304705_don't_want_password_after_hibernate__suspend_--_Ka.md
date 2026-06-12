---
title: "don't want password after hibernate / suspend -- Karmic"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by creeble on 2009-10-29
Just installed 9.10 and hibernate and suspend finally work right on my Acer 3680!

But I'd like everything to be as simple as humanly possible -- never ask for any passwords (if possible).  Auto-login works, I *think* I've got the default keyring working for wireless networking, now all I have to do is prevent the password dialog from coming up on suspend and hibernate, and this thing will work as simply as... my daughter's Macbook :)

I tried uncommenting LOCK_SCREEN in /etc/default/acpi-support to no avail; I don't think 9.10 uses this.

I hate to say it, but I think Canonical would be doing themselves a favor if they shipped the release with these absolute minimal password settings by default.  May not work for corporate, but isn't that what they charge for?

---

### Post by albandy on 2009-10-29
gnome-power-cmd suspend

---

### Post by creeble on 2009-10-29
> **albandy said:**
> gnome-power-cmd suspend

I don't have a gnome-power-cmd -- but I have gnome-power-manager (which is running) and gnome-power-preferences, which doesn't have a setting for no lock screen after suspend.

????

---

### Post by albandy on 2009-10-29
run it from console:
gnome-power-cmd suspend

if this works, simply add link to your menu calling this command.

---

### Post by creeble on 2009-10-29
Sorry, no, there is no gnome-power-cmd on my system; can't run it  from console/terminal/anywhere.

Is it from another package?

---

### Post by albandy on 2009-10-29
sorry I didn't read you were using karmic, I'm in jaunty

---

### Post by sprince09 on 2009-10-29
Try System->Preferences->Screensaver and un-check the 'lock screen when screensaver is active'. I think that worked for me once in the past...

---

### Post by creeble on 2009-10-30
Nope, Screensaver setting doesn't do it.

I installed this thing called Authorizations (PolicyKit), and there doesn't seem to be a setting there, either.

I suspect there's a suspend and hibernate script somewhere that I could patch, but it's apparently not using acpi any more in 9.10.

I want STUbunutu, for truly stupid people.  You know, people who don't know what System->Preferences->IBus Preferences is for, as an example :)

I wonder if the Netbook edition is a little more streamlined wrt permissions?

---

### Post by creeble on 2009-10-30
[COLOR=Red]Found a workable solution![COLOR=Black]

Looks like NOT activating lock (which actually happens BEFORE suspend/hibernate) was considered a bug: [https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-power-manager/+bug/428115](https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-power-manager/+bug/428115)

But that post led me to guess at gnome-session-manager (System->Preferences->Startup Applications), and just turning off Screensaver (along with Gnome Login Sound, and Keyring Manager, both annoying!).

I guess I can live without a screensaver (pretty anachronistic these days anyway).  It comes back from suspend almost instantly now as well!

Hmm, I wonder what else I can live without... What's the Seahorse Manager?

[/COLOR][/COLOR]

---

### Post by glennric on 2009-10-31
> **creeble said:**
> [COLOR=Red]Found a workable solution![COLOR=Black]

But that post led me to guess at gnome-session-manager (System->Preferences->Startup Applications), and just turning off Screensaver (along with Gnome Login Sound, and Keyring Manager, both annoying!).

I guess I can live without a screensaver (pretty anachronistic these days anyway).  It comes back from suspend almost instantly now as well!

[/COLOR][/COLOR]

If you do this will the computer still automatically suspend after the time period set in gnome-power-preferences?  In Jaunty and before automatic suspend would only work if gnome-screensaver was active.  Gnome-screensaver is what set the computer idle, and then gnome-power-manager would suspend the computer.

---

### Post by glennric on 2009-10-31
I managed to get the password request to stop appearing after resuming from suspend in Karmic.  I had to check both apps->gnome-power-manager->lock->use_screensaver_settings and apps->gnome-power-manager->lock->suspend.  This of course is exactly the opposite behavior than what you would expect, but it works for me.

---

### Post by cmcanulty on 2009-10-31
)Install Ubuntu tweak 2)go to security )check disable lock screen

---

### Post by glennric on 2009-10-31
> **glennric said:**
> I managed to get the password request to stop appearing after resuming from suspend in Karmic.  I had to check both apps->gnome-power-manager->lock->use_screensaver_settings and apps->gnome-power-manager->lock->suspend.  This of course is exactly the opposite behavior than what you would expect, but it works for me.

Ok, this didn't work after all.  It worked at first, but after rebooting it didn't work.  I might have done something else that made it stop asking for the password.  Anyway, I tried installing Ubuntu Tweak and doing what cmcanulty suggested, and that worked.

---

### Post by vanvoorenfamily on 2009-11-01
> **cmcanulty said:**
> )Install Ubuntu tweak 2)go to security )check disable lock screen

Hi Newbie here.

Where or how do Install Ubuntu tweak?
Where is security?

Thanks.

---

### Post by cmcanulty on 2009-11-01
here is the link make sure you install correct version, key etc as  page explains
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by espee838 on 2009-11-02
i don't like having to enter my password after suspend hibernate either, i'm going to give this a try:

1. Run gconf-editor  (ALT+F2 > gconf-editor)
2. apps> gnome-power-manager> lock
3. Uncheck Suspend and Hibernate

I dunno if it'll work, and i probably won't find out until tomorrow

---

### Post by apanloco on 2009-11-06
I've tried it all, and I can confirm that what cmcanulty is proposing is the only solution that really works to remove the lock screen on resume in Karmic, to date.
/Apan

---

### Post by TheKorn2 on 2009-11-08
> **apanloco said:**
> I've tried it all, and I can confirm that what cmcanulty is proposing is the only solution that really works to remove the lock screen on resume in Karmic, to date.
/Apan

Where in ubuntu tweak do you see any options that refer to this?  I have tweak installed under Karmic, and the only relevant options are under system-> power management, then I have "enable lock screen when blank screen activates" turned off, but I *still* get a password prompt upon suspend resumption.

Not to mention all the *other* options in the menu *don't actually work*.  (I have hibernate ticked off, but there it is on the menu, thumbing its nose at ubuntu tweak.)

---

### Post by cmcanulty on 2009-11-09
Sounds like a bug or maybe you hyave something else set that overrides the tweak

---

### Post by TheKorn2 on 2009-11-09
> **cmcanulty said:**
> Sounds like a bug or maybe you hyave something else set that overrides the tweak

You're missing the point.  That option doesn't even sound like it *should* do what you're saying it does.  I don't have blank screen selected as my screensaver.  I shut screensavers off completely.  (Unless I'm missing something here.)

---

### Post by cmcanulty on 2009-11-10
some of the settings are under preferences-power also

---

### Post by TheKorn2 on 2009-11-10
> **cmcanulty said:**
> some of the settings are under preferences-power also

It's almost like we're not using the same program.  I don't know what version of tweak you're using (I'm using 0.4.9.2, which is apparently the latest) but I have absolutely nothing even *close* to this.

When I start tweak, I get five options...  computer, applications, startup, desktop, personal, system.  The *only* one that has anything about power management is under system.

The "preferences" button just has options about how tweak displays itself...  colors, window height/width, and so-forth.

[IMG]http://www.thekorn.net/temp/tweak.png[/IMG]

---

### Post by cmcanulty on 2009-11-10
No I said look under preferences in top panel not tweak and some power settings are there

---

### Post by brk3 on 2009-11-10
Confirming the ubuntu tweak method works.  BS that had to go to this much trouble though :/

See attached for where to enable the option.

---

### Post by cmcanulty on 2009-11-10
maybe you didn't realize you should click unlock first in bottom right

---

### Post by slugicide on 2009-11-10
So is there no solution to this? Other than install some tweaking program? It's really fµcked up on a netbook, where you want it to suspend often to save battery life.

---

### Post by bilderbuchi on 2009-11-12
can one find out what the tweak program does? i figure it just adjusts some file, any way to find out which command is executed?

---

### Post by Jesus_Valdez on 2009-11-12
gconf-editor -- apps -- gnome-power-manager -- lock

---

### Post by bilderbuchi on 2009-11-13
those are all off, screensaver lock option is also off, but still it locks when waking from hibernate.

---

### Post by almalaci on 2009-11-13
i can confirm the same. Everything unchecked under apps>gnome-power-manager>lock, also in the tweak program. Still asks for password.

---

### Post by almalaci on 2009-11-13
But after a restart, it doesn't! :D

---

