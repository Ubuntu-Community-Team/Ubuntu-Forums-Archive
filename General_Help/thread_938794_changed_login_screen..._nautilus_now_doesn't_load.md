---
title: "changed login screen... nautilus now doesn't load"
date: 2008-10-05
forum: General Help
---

### Post by ft23002 on 2008-10-05
Hello,

On fresh install of ubuntu 8.04, went to change the login screen to one downloaded from gnomelook called "camping"  , heres the link:
[http://www.gnome-look.org/content/show.php/Camping?content=29255]("http://www.gnome-look.org/content/show.php/Camping?content=29255")

I DO NOT RECOMMEND DOWNLOADING/USING THIS!

Its only to show those what it was that caused this problem.

Followed the instructions from a post on here to simply download new login, once downloaded, dragged it over the login gui and it asked to install and use this, clicked yes. It was shown as the new login screen to use. Other changes made in login window was welcome text, and backround color, thats it.

After closing login and other open windows, logged off, and noticed the same default login screen. So restarted and again same default login screen. Entered user name / pw and when booting to desktop, received 2 errors about nautilus being unable to start, All that was seen is desktop backround, No taskbars, icons, time, nothing.

Restarted to session options and tried:
starting as gnome... was told nautilus was not default script, would I like to make it default, clicked yes. Now when rebooting to desktop, no error messages, the backround displays for a couple of seconds then all that displays is an orange/brown screen.

Tried session terminal and running nautilus from there and all that happens is it opens a "places" window, no taskbars.

Any help would be greatly appreciated.

---

### Post by ft23002 on 2008-10-05
Its not like I'm not trying to help myself...

Heres what I tried since last post:

session terminal:
gnome-panel

taskbar opened and...
went to login window options, uninstalled/deleted "camping" and changed everything back to default.
Restarted
No Help...Same brownish grey screen- no desktop, taskbars, nothing

at log-in screen pressed ctrl+alt+F2

...logged in

tried:
sudo apt-get remove gnome-panel
sudo apt-get install gnome-panel
sudo apt-get install ubuntu-desktop

restart
Same...No Help

at log-in screen pressed ctrl+alt+F2

...logged in

sudo apt-get remove nautilus
sudo apt-get install nautilus
sudo apt-get install natilus-cd-burner
...etc, reinstalled all that "remove nautilus" removed.


Same... No help.

This is getting real old, fast. Can't even make simple changes on a new install without it crashing the OS. Making changes by using a GUI and downloading from gnomelook which I would think is safe, yes it was an older theme, but nothing on the site states what version things will or will not work on and having this happen is unexceptable. This is the third install in 1 week. The last was because of a failed attempt at move home directory. After reading much on the subject and finding different sources stating the same commands it did not work. Nor did the restore. Nor did all the other suggestions. So after reinstalling and setting it up where the home dir has its own partition to mount too, I get this problem today. Figured keep it simple and make simple gui changes, only to find that doing so is no better or safer than using other non gui methods. Whats a new user to think???

---

### Post by ft23002 on 2008-10-05
Welp, its hardly the proper fix, but after a  reinstall while keeping my home dir everything seems to be good.

Have to chalk it up to learning experience. Its good to know that with the home dir root on it its own partition, during the OS reinstall the option was presented to use the users home dir & the settings contained within. So after the install, ran the update manager, installed the restricted graphics driver and a couple of other things, and I'm up-and-running with all prior settings in place. Its a big help for sure. Now knowing this, I'm comfortable customizing settings knowing that if a reinstall is needed, I'll at least not have to redo them all. ;)

I would mark this as solved, but its hardly the right solution. If one does not have there home dir mounted to its own partition or backed-up, they are pretty much having to start from scratch by reinstalling.

Also, not sure about attempting to change the log-in screen.
Was it an issue with the downloaded "camping" package or something within ubuntu???
Maybe someone can take a look at this and figure out why it didn't work.

Thanks to those who did give this thread a look. I'm not giving up on linux or ubuntu, but at this point can only see it as being something to toy around with and accept reinstalling the OS as part of the procedure. IMHO its not ready for primary home use, not that anybody said it should be, but when I see computer manufactures sell there pc's with only ubuntu or other linux distros. on them... thought it was further along and more stable than it appears to be. I'm sure once I get it setup with the programs & customizations I like, it will be fun rather than repetitive. Sure, one is learning along the way, but I know how to install the OS and would rather be spending more time really learning about linux than only fixing it. Think nearly everyone would agree that changing the log-in screen should not cause problems as its far from doing anything "advanced". Ohhh well..

Rock'n & Roll'n On...

:guitar: \\:D/

---

### Post by mssever on 2008-10-06
Your login problems were probably coincidental to your GDM theme. I went to the page you linked to, and noticed that the theme was last modified in 2005, and that its rating was 80% positive. That's a good indication that the theme isn't broken. I installed the theme and had no problems. So I'm pretty sure that the GDM theme had nothing to do with your problems.

---

### Post by ft23002 on 2008-10-06
Not sure why it didn't work here. Thats very strange if it wasn't caused by the gdm theme as it was immediately after its install. It has only happened this one time although only been running ubuntu for a few weeks now.

Do you know if since I kept my user profile (/home dir) during the reinstall if there would be a log of the nautilus error and/or any other info that may help solve this? Also, prior to dragging the theme over the login gui, should it have been unpacked? I dragged the downloaded package just as it was received and didn't unpack it. It was pictured and selected in the login window list of installed login choices, so thinking it was done right...dunno.

As much as I would like to use a downloaded log-in screen, would prefer to know what went wrong and should it happen again have a possible fixes on hand.

If you think theres a log that may help find out what went wrong, please let me know. Thanks for the help.

---

### Post by mssever on 2008-10-06
> **ft23002 said:**
> Not sure why it didn't work here. Thats very strange if it wasn't caused by the gdm theme as it was immediately after its install. It has only happened this one time although only been running ubuntu for a few weeks now.That's hard to say without error messages.

> Do you know if since I kept my user profile (/home dir) during the reinstall if there would be a log of the nautilus error and/or any other info that may help solve this?You can check ~/.xsession-errors, but it's probably been overwritten by now. Log messages go in /var/log normally.
> Also, prior to dragging the theme over the login gui, should it have been unpacked? I dragged the downloaded package just as it was received and didn't unpack it. It was pictured and selected in the login window list of installed login choices, so thinking it was done right...dunno.You did it right. Unless there's strong evidence to the contrary, it's best to regard this as a coincidence. Of course, you can try installing that theme again. If you have more problems, then you can get some data to work from.

---

### Post by ft23002 on 2008-10-06
Checked the .xession-errors, theres a few items that need a further look. 

```
Initializing nautilus-share extension

** (nautilus:6039): WARNING **: Unable to add monitor: Not supported
** (gnome-app-install:11043): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1255: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)

** (gnome-app-install:17913): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1255: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
```
The file "AppInstall.py doesn't exist, not sure whats up with that.

Did you test it by restarting right after or as I did by logging off the user session into the login screen first?
Don't know if that matters, but ya never know.

Thanks for the help and your willingness to test the package.

---

### Post by mssever on 2008-10-07
> **ft23002 said:**
> ```
** (nautilus:6039): WARNING **: Unable to add monitor: Not supported
** (gnome-app-install:11043): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1255: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)

** (gnome-app-install:17913): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1255: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
```Notice that the message is from the program gnome-app-install. When I run it from the command line, I see that it's the Add/Remove app. I get the same warnings. It's usually safe to ignore warnings if you aren't the programmer, and a lot of Gnome programs emit such warnings. I don't think that it's anything to worry about.
> Did you test it by restarting right after or as I did by logging off the user session into the login screen first?
Don't know if that matters, but ya never know.
I tested it by using the user switcher applet to bring up the login screen and log into a test account. I didn't log off as I have stuff open I don't want to close, and my testing method should be sufficient.

GDM themes get installed in /usr/share/gdm/themes. gdmsetup (which you use to manage your themes)runs as root, and gdm runs as root. By contrast, Nautilus runs as your user (unless you explicitly run it as root, which you shouldn't normally do). So the change that GDM themes could mess up Nautilus is extremely remote. Furthermore, I've installed broken GDM themes before. What happens is that GDM falls back to its default theme, Gnome Circles (I think that's the default). Additionally, as I mentioned earlier, its inconceivable that if the theme was really broken that no one would have complained since 2005.

I just though of one possibility, though. Perhaps your download got corrupted, resulting in corrupted files being installed. It's conceivable that a GDM theme could break GDM, which could impact your ability to log in using GDM. However, there's no way to test that theory now that you've reinstalled. If that indeed happened, it shouldn't be too hard to recover from it if you know what you're doing.

---

### Post by ft23002 on 2008-10-07
> **mssever said:**
> Notice that the message is from the program gnome-app-install. When I run it from the command line, I see that it's the Add/Remove app. I get the same warnings. It's usually safe to ignore warnings if you aren't the programmer, and a lot of Gnome programs emit such warnings. I don't think that it's anything to worry about.

Good to know, as I wasn't sure about there relevance.

> **mssever said:**
> 
I tested it by using the user switcher applet to bring up the login screen and log into a test account. I didn't log off as I have stuff open I don't want to close, and my testing method should be sufficient.

Would think that would produce the same result. Wasn't sure since it was the log-in screen if a restart had to be done first. Will a change in a program or newly added program that requires a restart always state a restart is needed before it will work? I have seen this after some updates, but was wondering if it will always alert a user that a restart is needed.

> **mssever said:**
> 
GDM themes get installed in /usr/share/gdm/themes. gdmsetup (which you use to manage your themes)runs as root, and gdm runs as root. By contrast, Nautilus runs as your user (unless you explicitly run it as root, which you shouldn't normally do). So the change that GDM themes could mess up Nautilus is extremely remote. Furthermore, I've installed broken GDM themes before. What happens is that GDM falls back to its default theme, Gnome Circles (I think that's the default). Additionally, as I mentioned earlier, its inconceivable that if the theme was really broken that no one would have complained since 2005.

This is why I'm perplexed with this problem. No other system changes were made prior to restarting and then having nautilus not load. It would appear as though the GDM theme was broke, as it did not become the log-in screen. Its thumbnail was shown in the (customizing) login window gui and was selected, yet the login screen was the default (mine was Human). While in the middle of this post, I changed the login to a different one that comes with ubuntu and it worked fine.

> **mssever said:**
> 
I just though of one possibility, though. Perhaps your download got corrupted, resulting in corrupted files being installed. It's conceivable that a GDM theme could break GDM, which could impact your ability to log in using GDM. However, there's no way to test that theory now that you've reinstalled. If that indeed happened, it shouldn't be too hard to recover from it if you know what you're doing.

This is what I'm starting to think as well. It's a good reason for me to learn how to verify downloads. Don't know if every download has this ability, but its something that would be good to know. However like you said, if it was a bad download it shouldn't have affected nautilus. I was still able to use the log on screen as it defaulted back, but why did nautilus fail to load afterwards.

I still have the original downloaded package...
you going to be on here most of the day. lol

I/WE could give it another shot if your up to it. Not to say it will happen again, like you said its unlikely to have caused nautilus to fail, but if does.

If your up to it, I will try it again.

---

### Post by mssever on 2008-10-07
> **ft23002 said:**
> Would think that would produce the same result. Wasn't sure since it was the log-in screen if a restart had to be done first. Will a change in a program or newly added program that requires a restart always state a restart is needed before it will work? I have seen this after some updates, but was wondering if it will always alert a user that a restart is needed.Technically, only kernel changes require a reboot to take effect, though some other changes require logging out and back in,and Firefox says that you have to restart it to avoid problems (I didn't heed that advice once and wondered why all the buttons and menus were blank...).  Generally, you can just restart the affected component(s) and whatever depends on them. Usually, the package manager will do that for you.  Sometimes, though, it's quicker to reboot than to figure out what to restart--especially for newbies. And it's getting more difficult to know exactly what to restart nowadays as the Linux desktop matures. So, while I used to never reboot--and I still don't reboot my server--I'm much more likely to reboot my laptop to save me from taking the time to figure out exactly what needs to be restarted.

> I still have the original downloaded package...
you going to be on here most of the day. lol

I/WE could give it another shot if your up to it. Not to say it will happen again, like you said its unlikely to have caused nautilus to fail, but if does.

If your up to it, I will try it again.
Sure, if you want to try again, I'll do whatever I can to help. You've probably noticed that I've been away from my computer for most of the day, and I'll be away off and on tonight and tomorrow, but I'll do my best.

---

### Post by Sami655 on 2008-10-07
does anybody know how to download limewire

---

### Post by Soupcan on 2008-10-07
> **Sami655 said:**
> does anybody know how to download limewire

You should make your own thread for this; don't threadjack someone else's.

---

### Post by Sami655 on 2008-10-07
how do i start a thread im new at this

---

### Post by Soupcan on 2008-10-07
> **Sami655 said:**
> how do i start a thread im new at this
Click the new thread button in the forum you want to make your topic in.

---

### Post by ft23002 on 2008-10-07
> **mssever said:**
> Technically, only kernel changes require a reboot to take effect, though some other changes require logging out and back in,and Firefox says that you have to restart it to avoid problems (I didn't heed that advice once and wondered why all the buttons and menus were blank...).  Generally, you can just restart the affected component(s) and whatever depends on them. Usually, the package manager will do that for you.  Sometimes, though, it's quicker to reboot than to figure out what to restart--especially for newbies. And it's getting more difficult to know exactly what to restart nowadays as the Linux desktop matures. So, while I used to never reboot--and I still don't reboot my server--I'm much more likely to reboot my laptop to save me from taking the time to figure out exactly what needs to be restarted.


Sure, if you want to try again, I'll do whatever I can to help. You've probably noticed that I've been away from my computer for most of the day, and I'll be away off and on tonight and tomorrow, but I'll do my best.

Thank you msserver for all the info and help.

I've added you as a contact and will use the contacts window.
FYI: I have a bad habit of forgetting to log-off.

I'm almost hoping for a repeat with using the camping GDM theme now, it would be great to know what went wrong.

---

