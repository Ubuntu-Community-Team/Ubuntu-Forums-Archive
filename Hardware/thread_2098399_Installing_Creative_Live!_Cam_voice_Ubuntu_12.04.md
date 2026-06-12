---
title: "Installing Creative Live! Cam voice Ubuntu 12.04"
date: 2012-12-26
forum: Hardware
---

### Post by ljmartz on 2012-12-26
I am a noob and installed Ubuntu after my frustrations with Vista reached peak.  I am currently running Ubuntu 12.04 dual boot with Vista on a Dell Inspiron 1501 laptop.  I have a Creative Live! Cam voice webcam that I want to use for Skype calls.  It works on audio, but does not work on video.  

I have tried to download Cheese to test for video, but the first attempt in installing Cheese ended with a broken software center.  The second attempt at installing Cheese, was successful with the Cheese install (installed via Terminal), but any attempt to open Cheese ends in an error message that states that the application encountered an error and was shut down.  I don't necessarily care if I get Cheese up and running, as my sole objective is to make Skype video calls.  However, if the best way to troubleshoot video issues is to fix Cheese, then I'm willing to go down that road. 

```
lsusb
```
mimi@mimi-Inspiron-1501:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 041e:404b Creative Technology, Ltd 
Bus 001 Device 003: ID 041e:4048 Creative Technology, Ltd 
Bus 001 Device 004: ID 041e:4045 Creative Technology, Ltd Live! Cam Voice

Any assistance is greatly appreciated.

---

### Post by ljmartz on 2012-12-27
There are few things more disheartening than to get an unsolvable (with your own resources) error in an open source program,  to post a question on a forum to try to get help with said error, only to get the resounding sound of virtual crickets echoing back from the forum.  In the immortal words of Ferris Buellers' economics teacher "anyone, anyone?"

---

### Post by ljmartz on 2012-12-27
Google and I are making some progress.  After running Cheese in terminal I googled the error message I received which was: 

Xlib:  extension "GLX" missing on display ":0.0".  

Google brought me to:
[http://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/#comment-158](http://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/#comment-158)

After running that fix I can now at least get Cheese to load, but with the following error: 

(cheese:2401): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

After googling this error, it appears that this is a known bug with Cheese.  As I stated earlier, I don't care if Cheese runs or not, my sole objective is to get my webcam running.  If fixing Cheese fixes my webcam, then so be it.  Still hoping for assistance.

---

### Post by ljmartz on 2012-12-27
Output from error when Cheese loads in Terminal:

```
mimi@mimi-Inspiron-1501:~$ cheese

(cheese:16655): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:16655): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:16655): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:16655): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:16655): Gtk-WARNING **: Attempting to add a widget with type GtkGrid to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:16655): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

** (cheese:16655): WARNING **: cheese-window.vala:1624: Error: No device found
```

---

### Post by ljmartz on 2012-12-27
My father, a genius who held multiple degrees in Aero-dynamical Engineering from MIT, had a plaque mounted over his desk which read: 

"Our objective is to thoroughly analyze all situations, anticipate all problems prior to their
occurrence, have answers for these problems, and move swiftly to solve these problems when called upon.

However, When you are up to your *** in alligators it is difficult to remind yourself your initial objective was to drain the swamp."

After a full day of googling, trying in vain to find an answer to my posted problem, I can fully identify with alligator killing.  At this point the alligators have won and I find no solution to enable me to drain the swamp. 

What I find to be most disheartening is that there are a large number of posts to this forum from individuals experiencing the same problem that I have and like me, their posts have gone unanswered too.

In this particular instance, I am forced back to Vista whenever I want to Skype.
****

---

### Post by Rasoul on 2013-01-31
It seems that Ubuntu recognizes the webcam and initiates its sound hardware correctly. The following commands might solve the problem with video hardware initialization.

1. Open a terminal (Ctrl+Alt+T)

2. Enter the following command to stop linux webcam driver,
$ sudo rmmod uvcvideo

3. Enter the following command to restart the driver,
$ sudo modprobe uvcvideo

4. Now test your webcam with the Skype in Ubuntu. If it works fine, please let me know.

Good luck!

---

