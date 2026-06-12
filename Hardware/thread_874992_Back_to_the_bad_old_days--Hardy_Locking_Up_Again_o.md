---
title: "Back to the bad old days--Hardy Locking Up Again on My Laptop"
date: 2008-07-30
forum: Hardware
---

### Post by bobnutfield on 2008-07-30
Hello Everyone,

I am not actually expecting anyone to solve this issue.  I just thought I would offer it as information and see if anyone else is experiencing it, or, just maybe someone actually knows whats going on.

I installed Hardy on my Toshiba A210 laptop back in February when it was still in beta.  Of course, I had all the issues you would expect to have with a beta install, namely frequent lock-ups and crashes.  But, I persevered, followed through with all the updates, all the way to the official release on April 24.  Eventually, things settled down and I had a reasonable stable system I could actually use.  Things were still buggy, even after the realease, so I set up a dual boot with Slackware 12.1, because Slackware has always been stable for me.  I figured I would use Slackware for a lot of my work while Hardy continued to be updated and became more stable, as Ubuntu always has for me since 2006.  And, because Ubuntu is so feature rich right out of the box, where Slackware is not, I thought I could eventually resume my use of Hardy as my main system.  The lock-ups and freezes had all but disappeared until one week ago when they came back in all of their fury.

I was out of town for a week, and when I returned, there were 68 updates to Hardy waiting.  Now, I am not one who just blindly clicks "OK" when updating my system; I look at whats being updated and consider the possible consequences.  Included in these updates were updates to Firefox3 and Xulrunner.  These concerned me a little because Firefox has been a beast since the release of 3, but they appeared to be only security updates. So, I updated.

Ever since then, I am again getting hard lock-ups (requiring a power button restart), normally when I am using Firefox, but also at other times as well with no particular app running.  There has been no changes or new software whatsoever.  Only this update.

This concerns me because this is a new laptop and hard lock-ups will eventually damage the hard drive.  Ubuntu is my distro for my productive work, but, for the time being at least, I am having to return to Slackware for that.  Now, I am not complaining.  My relationship with Ubuntu is been great and it has serviced me will since Dapper.  But I don't want to see my expensive laptop damaged, either, as I am also getting temperture spikes and in general it is now running hotter.  Please don't suggest a hardware issue as these things do not happen with Slackware.

If anyone else has experienced any thing similar, I would love to hear from you.

---

### Post by evets25 on 2008-07-30
Because of the way linux seperates out processes running in userland from those running in the kernel space, from what I understand, it should not be possible for firefox to completely lock up your system in such a way. The usual culprit for something like this is a driver, usually graphics, or something hardware-related. Not necessarily defective hardware, but at least kernel/driver level stuff. So firefox probably has nothing to do with this particular problem. If you have done a kernel update (which is likely from the sound of it) try booting into a different kernel and seeing if you still get the same problems. If not, then you can simply uninstall the newer kernel, and pin your kernel version so that it won't update it, or even notify you when a new version is available. look in synaptic for packages that are installed with names like "kernel-generic" or with names containing words like "image," "kernel," and "linux," as well as the "restricted-drivers" package and pin them.

---

### Post by bobnutfield on 2008-07-30
Thanks for your response...your comments make sense and yes, there was a kernel update, though not a major one as it did not even change the version number. It seemed to be just an update to the existing kernel (2.6.24-19-generic).  I have gone back to using the -18 kernel to see what happens.

**UPDATE:** I had not bothered to look at anything else, but as it turns out I was booting into the -18 kernel anyway because the -19 won't boot and it was removed from the menu.lst file.  Never seen anything like that before.

---

### Post by mariner09 on 2008-08-14
I had used Hardy through the beta cycle and never had any issues.  Once I did a fresh install of the final release, the lock-ups started.  I can't find any helpful log info or anything meaningful.  Only the mouse will move, but there's no response to any clicks or key presses.  It's very annoying.

I've disabled proposed repos thinking I was too bleeding edge and did a fresh install to no avail.  It usually happens to me when the laptop is sitting with no work activity and that's when it happened.

I don't want to have to go back to FC9,  but I may have no choice if I can't hunt this down...

---

### Post by bobnutfield on 2008-08-14
> **mariner09 said:**
> I had used Hardy through the beta cycle and never had any issues.  Once I did a fresh install of the final release, the lock-ups started.  I can't find any helpful log info or anything meaningful.  Only the mouse will move, but there's no response to any clicks or key presses.  It's very annoying.

I've disabled proposed repos thinking I was too bleeding edge and did a fresh install to no avail.  It usually happens to me when the laptop is sitting with no work activity and that's when it happened.

I don't want to have to go back to FC9,  but I may have no choice if I can't hunt this down...

I am really not sure if there is a solution at this point.  The logs reveal nothing (for me at least).  However, I am convinced that it is related to either firefox or the terminal program on the desktop.  It happens intermittently when using firefox, but it is frequent when the terminal is running.  It starts by refusing to get focus in the terminal from the mouse (can't get the mouse cursor to show up in the terminal).  I know when it starts this that it going to freeze at any moment.  It does not do this until the laptop has been running for some time, usually about an hour, or if I am doing something cpu intensive (like flash in firefox).  I would think that it was temperature related, but the cpu cores never get over 50 degrees.  Oddly, if I click on a taskbar icon when the cursor will not show up in the terminal, that seems to fix it temporarily.

It is definitely not hardware related as I also have Slackware on this laptop and it runs smooth as silk.  I love using Hardy, but I can only do serious work in Slackware because of this issue.

---

