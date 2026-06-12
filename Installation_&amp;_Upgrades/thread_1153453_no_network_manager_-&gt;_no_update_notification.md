---
title: "no network manager -&gt; no update notification?"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by Hackie2 on 2009-05-08
Hi

It seems that uninstalling the network manager (it corrupted my network in a time i was testing with xen) also disabled the update notification in gnome. Update manager itself still works, but i have to open it manually and click update to see if there is something new. this is very annoying.

I think network manager started the package update automatically after establishing a connection, but i did not find any script responsible for.

When i call apt-get update, i also get a new package list, but is does not hit the notification

any idea? i dont want to install network manager again, and i cannot find a reason for such a hard-coded connection between this two tools..

thx
Daniel

PS: using ubuntu 9.04

---

### Post by HyRax on 2009-05-08
Notifications have changed in 9.04. Unless there is a critical security update, the Update Manager will auto-appear only once a week now.

If you don't like this new behaviour (I certainly don't), you can change it back to the old behaviour of notification for any update by bringing up the gconf-editor.

[list=1]
[*]Press ALT + F2. A "Run application" window appears.
[*]Type in "gconf-editor" and hit Enter. The editor will appear.
[*]In the left pane, expand out "apps".
[*]Now scroll down until you see "update-notifier". Click on it.
[*]In the right pane is a checkbox for "auto_launch". It has a tick in it. UNTICK this.
[*]Close the editor.
[/list]

If you run a *sudo apt-get update* again and there are new updates, the normal update manager icon and general notification will appear in the system tray just like it used to before.

---

### Post by TheOldFellow on 2009-05-28
Wierd! Are you saying that to get back the old Automatic Upgrade Check Every Day behaviour, you UNCHECK auto-launch?  This seems the wrong way about.  Crazy programmers!

I'm looking for a way to set it up so that:

1) Every day Update Manager runs in the background.
2) If there are any updates available a little icon appears in the toolbar - it would be nice if they were colour-coded for critical etc.
3) If I click on it, then the update manager runs and does the updates.

This was the behaviour I got in Warty-Intrepid, and the main reason I recommended Ubuntu to people who hate Microsoft's SP-hell.  Taking it away without a clear way of putting it back is a major ****-ache.

---

### Post by Hackie2 on 2009-05-30
> **TheOldFellow said:**
> Wierd! Are you saying that to get back the old Automatic Upgrade Check Every Day behaviour, you UNCHECK auto-launch?  This seems the wrong way about.  Crazy programmers!

I also thing that is the wrong way. At the moment i am waiting for new security updates to check that approach..

What i want is exactly the same: daily check (database update), and notification icon if there is a reason for it

---

### Post by Liph on 2009-07-19
The steps above are correct. You are disabling the auto launch of update manager, ie. telling it not to open automatically. This means it will now display a notification instead.



If you would still like the manager to open automatically but do it more than once a week you can edit the regular_auto_launch_interval setting. This is the number of days between opening. The default is 7 but if you change it to 0 it will open as soon as they are available. (Security updates always cause the manager to open immediately)

---

### Post by Hackie2 on 2009-07-20
> **Liph said:**
> The steps above are correct. You are disabling the auto launch of update manager, ie. telling it not to open automatically. This means it will now display a notification instead.

At the time i wrote the first message, nothing popped up after doing a apt-get update. this just happened ~2 weeks ago. maybe a change in one of the updates?

seems to be ok now. Thx

---

