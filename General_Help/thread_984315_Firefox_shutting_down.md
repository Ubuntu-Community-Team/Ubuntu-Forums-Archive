---
title: "Firefox shutting down"
date: 2008-11-16
forum: General Help
---

### Post by thonaker on 2008-11-16
Firefox 3.0.3 has started to shut itself down.  I get no warning, it just shuts off like a light bulb.  No error messages.  No particular web site triggers it, that I can tell.

I had to start using other browsers, because it's just not usable this way.

I just re-installed Firefox, it didn't help.

Troy

---

### Post by thonaker on 2008-11-17
Oddly enough I just realized I've had Firefox up and running for a while now.  I just updated my desktop to a cube view with CompizConfig, which I find quite neat.  Could something I did with this have fixed Firefox?  I would expect it to break things not fix things.

Troy

---

### Post by roshanjose on 2008-11-17
That is not the thing. The actual problem lies where you have put in several addons. You might have put in several video players etc.. and many other unnecessary ones....Remove all these and decrease the load on your firefox, I bet this would get you running it well without crashing

---

### Post by roshanjose on 2008-11-17
You can see you addons at Tools---> Addons

---

### Post by thonaker on 2008-11-17
Well, I do have maybe 20 plug-ins.  I think I may have multiple plug-ins trying to do the same things.  

Maybe this is the problem.

I guess I could disable some of them.

Troy

---

### Post by thonaker on 2008-11-19
Well, it was running fine, then started to shut down again today.

I disabled a few plug-ins, do I need to disable more of them?

Troy

---

### Post by easoukenka on 2008-11-19
Run firefox by typing in terminal firefox -safe-mode this will temporarily disable all plugins.  If it crashes now then we have a problem with firefox.

---

### Post by thonaker on 2008-11-19
Does this help?  This is what the terminal showed me, after it went down.  I reset some things.  I haven't tried disabling the plug-ins yet.

troy@troy-desktop:~$ firefox -safe-mode
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
troy@troy-desktop:~$ 

Troy

---

### Post by thonaker on 2008-11-19
Similar message with the add-ons disabled.

troy@troy-desktop:~$ firefox -safe-mode
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6353): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
troy@troy-desktop:~$ 

Troy

---

### Post by easoukenka on 2008-11-19
Let's try the following.
Close Firefox
Let's try backing moving your files somewhere else with mv ~/.mozilla ~/.mozilla_backup 

sudo apt-get purge firefox
sudo apt-get install firefox


If that doesn't work then goto firefox website download the newest one and install it yourself hopefully this works for you.

---

### Post by thonaker on 2008-11-19
Ok, so I did that.  I tried to move the backup files back to .mozilla, using the mv command, just reversing things.  That didn't seem to restore my bookmarks.

How can I get my bookmarks back?  Not that this is major or anything.

Troy

---

### Post by thonaker on 2008-11-19
Thanks for your help.

Everything seems fine right now.  I just don't have my bookmarks, which isn't really a major deal.  Would be nice to restore those though.

Troy

---

### Post by easoukenka on 2008-11-20
I am sorry about bookmarks I thought that would save them.  Digg through that directoy a little in mine I do see a bookmarks.html.  

I typed locate bookmarks.html and I do see some files inside the actual firefox directory so maybe you are out of luck  but you may as well look  

Glad your problem is fixed See ya

---

### Post by thonaker on 2008-11-20
I have a bookmarksbackup file in .mozilla.  Can this be used some way?

Troy

---

### Post by MasterNetra on 2008-11-20
idk but firefox tends to act up for me sometimes too in the same manner and i do have the latest version and the only plugins i have are the ones that allow you to actually view videos on the web and i shouldn't have to get rid of those. Any suggestions for a light weight browser that can utitlize flash and what not?

---

### Post by thonaker on 2008-11-20
Galeon seems to work pretty well for me.

I like my Firefox, but when that fails, I go to Galeon.

Troy

---

### Post by jocose on 2008-11-20
> **thonaker said:**
> Firefox 3.0.3 has started to shut itself down.  I get no warning, it just shuts off like a light bulb.  No error messages.  No particular web site triggers it, that I can tell.

I had to start using other browsers, because it's just not usable this way.

I just re-installed Firefox, it didn't help.

Troy

When did the problem start? In my case, as I detailed in a separate thread, [**"Latest Firefox Update Leads to Frequent Flash Related Crashes"](http://ubuntuforums.org/showthread.php?t=988558)**, Firefox started this behavior after I updated. Prior to updating, none of these problems were happening. Now, I've noticed this same behavior with the error messages as mentioned in this thread. Firefox was working for me with Flash 10 until I updated, then the problems began, it happened to me every time back when I had Flash 9, too.

[color=red]I recommend manually downloading and installing Seamonkey from Mozilla's site.[/color] When I manually download and install Seamonkey, the crashes experienced in Firefox don't happen in the manually downloaded/installed Seamonkey. [color=blue]*I haven't tried purging the Firefox I installed from the repos and installing Firefox manually from Mozilla's site as I did with Seamonkey, but I guess this would be worth a shot.*[/color]

Any reports on this problem being resolved by manually downloading and installing Firefox from Mozilla's site? Could this crash issue be limited to installing and/or updating from the repos somehow? Seamonkey from the repos exhibited similar behavior in my experience, but a manual install shows no problems.

---

### Post by thonaker on 2008-11-21
Seems like the purge and re-install has fixed things.  I haven't crashed yet.

I don't remember exactly when this started to happen, but it wasn't that long ago.

Troy

---

