---
title: "desktop effects Latitude c610"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by kazbear on 2007-12-22
I started with a clean install of Ubuntu 6.1.  I made no modifications through this process.  I ran the update for 6.1.  Then ran the update for 7.04.  I was happy to see desktop effects working great.  I then did the upgrade for for 7.10.  Now, desktop effects cannot be enabled. 

Last thing I did was install Envy, but no change.  Before I go any further, any suggestions to get desktop effects working on this laptop?

Thanks

-kaz

---

### Post by kazbear on 2007-12-27
Still looking for a solution, but until then, I have reverted to 7.04.  The graphics card is old and only 16 megs ram (I think) so I am not expecting much.  It seems to work just fine as it is though...

---

### Post by Yellow Pasque on 2007-12-27
What video card do you have?
Does your /etc/X11/xorg.conf file look any different between Feisty and Gutsy?

---

### Post by tjasko12 on 2008-03-22
I know I just bumped a very old thread, but, I have a reason for this,

I also have the Dell C610. And I happened to install 7.10 over my previous installation. I too lost compiz. It says that the desktop effects could not be enabled. Something changed from  7.04 to 7.10. I would really like to use compiz in order to get Avant Windows Manager to work... If anyone can find a fix, that would be great for all of the C610 users out there...

I can say that this is a problem. And if anyone have fixed it, it should go into the final release that is coming out in April sometime (Ubuntu 8.04 if I can recall...).

---

### Post by Yellow Pasque on 2008-03-23
tjasko12, type *compiz* in the terminal. What does it say?

Also, this might help:
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

---

### Post by tjasko12 on 2008-03-23
My video card could be blacklisted. I'll do what the link says, and see what happens.

[QUOTE="*compiz*"]
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c59 (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution ( 1024x768 ) to maximum 3D texture size (512): Failed.
aborting and using fallback: /usr/bin/metacity 
[/QUOTE]

---

### Post by tjasko12 on 2008-03-23
I think I see my very first problem. (Make sure the first block after the initial comments has /usr/ paths and not /usr/local paths. Areas you may need to change are bolded.)

Here is the output of gksudo gedit /usr/bin/compiz (before modifications....attached).

I'm not very good at this stuff. I'm great with Linux, and the terminal, but not compiz. So please see if any of you can help me out... I'll follow what was said here... [http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

Here is my new output after the modifications... (both *compiz* look the same to me....)
[QUOTE="*compiz*"]
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c59 (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution ( 1024x768 ) to maximum 3D texture size (512): Failed.
aborting and using fallback: /usr/bin/metacity[/QUOTE]

Edit:
Something just popped up in the terminal. It took a while... It was at the very end. After aborting and using fallback...
Window manager warning: last_focus_time (3688568596) is greater than comparison timestamp (3688568480).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around

I saw that it tried to turn it on, but still, it failed...

---

### Post by tjasko12 on 2008-03-25
Does anyone have any idea on how this could be fixed?

---

