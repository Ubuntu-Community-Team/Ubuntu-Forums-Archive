---
title: "Finally - an answer to the 1440x900 res problem on 82865g integrated graphics cards!"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by ThingsThatGoFlirInTheShla on 2008-02-27
I'm going to re-write this article step by step so that any newbies, who are considering whether to pull that last strand of hair out or sweep it across and hope no-one notices, actually know what they're supposed to be doing. 

The original thread is here::
[http://ubuntuforums.org/showpost.php?p=4416287&postcount=67]("http://ubuntuforums.org/showpost.php?p=4416287&postcount=67")

**1.First of all go to Applications> Accessories> Terminal**

**2.Copy the following text and paste it into the terminal.** *(You'll have to right click> paste. keyboard shortcuts don't work)*

```
sudo 915resolution 3a 1440 900 8 1904 934
```

**3. Press enter and when prompted type in your password and hit enter again**

**4.Go to System> Administration> Screens and Graphics**

**5.Under the "Screen" tab click the text next to the word "Monitor"**

[B]6.Under "Manufacturer" Select "Generic".
   Under "Model" Select "LCD Panel 1440x900".
   Tick the "Widescreen Monitor" box in the bottom left and hit "OK".[/B]

**7.Click on the text next to the word "Resolution" and select "1440x900"**

**8.Hit the OK button and you'll be prompted to log out.**

**Logout, Log back in again....All done =]**

---

### Post by unbutu on 2008-02-27
I was very happy to find both this post and the thread it refers to.  The above procedure worked for me, with the following changes:

1) In addition to 

```
sudo 915resolution 3a 1440 900 8 1904 934
```

I also needed 

```
sudo 915resolution 4b 1440 900 16 1904 934
sudo 915resolution 5a 1440 900 32 1904 934
```

(as instructed in the [other thread]("http://ubuntuforums.org/showpost.php?p=1465348&postcount=10")) in order to get a crisp picture.

2) So that I don't have to enter those three commands every time I reboot my machine, I added them to the file /etc/init.d/rcS (just before the only active line in the file: "exec /etc/init.d/rc S", as mentioned in the [other thread]("http://ubuntuforums.org/showpost.php?p=1775271&postcount=19")).  My /etc/init.d/rcS now looks like this:

```
#! /bin/sh
#
# rcS
#
# Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
#

915resolution 3a 1440 900 8 1904 934
915resolution 4b 1440 900 16 1904 934
915resolution 5a 1440 900 32 1904 934

exec /etc/init.d/rc S
```

Now, every time I restart, they're done automatically.

3) After having done this, my display was off-center by a tiny bit (a problem also mentioned in the [other thread]("http://ubuntuforums.org/showpost.php?p=1555035&postcount=16")).  I pressed the auto-image-adjustment button on my monitor (LG L192WS), and it centered it perfectly.  I haven't had to press it again.

ETA: I'm using Ubuntu 7.10 on an x86-64/amd64 architecture with an Intel GM965/GL960 Graphics Controller.

---

### Post by ThingsThatGoFlirInTheShla on 2008-02-28
Thanks for the additional points.
I've only just turned my machine back on since writing this thread and... horror! it had all reset!!

How do you open "/etc/init.d/rcS" using the terminal though? Im guessing it needs a sudo command because it won't let me write to it if i use nautilus.

I really am new to this and haven't really grasped command line basics.

---

### Post by unbutu on 2008-02-28
The easiest way to edit /etc/init.d/rcS from the command line is probably:

```
sudo gedit /etc/init.d/rcS
```

I don't use gedit personally, but it's pretty user friendly (with a drop-down menu for saving and exiting).

As an aside, I do have one question/concern about the need for the 915resolution commands.  From the [package description]("http://packages.ubuntu.com/gutsy/x11/915resolution"):

> The 915resolution package becomes obsolete with the newer xorg, especially if you have the xserver-xorg-video-intel package installed. Newer xorg brings modesetting support by default.

I have xserver-xorg-video-intel installed, but I still needed to execute the 915resolution commands to get the proper resolution.  Does anyone know if there are different commands I could be using?

---

