---
title: "Screen &quot;Tearing&quot; Dell Latitude C800"
date: 2009-01-10
forum: Hardware
---

### Post by Tech-Geek on 2009-01-10
Hello All,
I'm volunteering with a school district to try to setup some laptops for families with low income to get laptops for their children.  The school district has donated 3 Dell Latitude C800 laptops for testing.  I'd much rather load linux onto them instead of windows to save money and prevent virus issues.  

The problem I'm having is with screen tearing.  I found on some earlier fourms that this is a video sync problem and I should update the /etc/X11/xorg.conf file.  but when I open it there is very little information there compared to what I see listed on other screen shots.  

The result is I'm still having a problem and loosing hair.  If anyone could at least give me a pointer it'd be great.

Thanks

---

### Post by jb70115 on 2010-01-24
I have the solution. Same situation with donated laptop for a student. The problem is a simple fix once you know it.

Newest Ubuntu distros do not use a xorg.conf so you will have to create one, simple task.

First we need to create the file xorg.conf. Fortunately there is automatic way of doing this with generating xorg.conf with the detected devices from the X.
 
In order to generate xorg.conf you need to switch to one virtual console using the key combination CTRL + ALT + F1. 
Now execute the following commands:

user@ubuntu ~# sudo service gdm stop

This command will stop the X.
Now we need to generate the xorg.conf file:

user@ubuntu ~# sudo Xorg -configure

This has generated the file in ~/xorg.conf.new.
We need to make the X using it so we have to put this file inside /etc/X11/

user@ubuntu ~# sudo mv ~/xorg.conf.new /etc/X11/xorg.conf

Now we need to edit the file so it actually works.

user@ubuntu ~# sudo nano -w /etc/X11/xorg.conf

Add the following lines under the Section "Monitor":

HorizSync 31-82
VertRefresh 40-110

Save and exit the file.
Now restart x window

user@ubuntu ~# sudo service gdm start

And now we having a working computer, ain't it beautiful?

Sorry never completed a write up before, refer to the following sources.

[http://www.baltimoremick.com/blog/2008/08/25/dell-latitude-c800-display-problems-with-ubuntu/](http://www.baltimoremick.com/blog/2008/08/25/dell-latitude-c800-display-problems-with-ubuntu/)

[http://ubuntuforums.org/showpost.php?p=977236&postcount=5](http://ubuntuforums.org/showpost.php?p=977236&postcount=5)

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

PS- If your screw the pooch and need to reset the xorg.conf you can delete the file and start again, no harm no foul.

sudo rm /etc/X11/xorg.conf

Best of luck!

---

### Post by Iowan on 2011-02-12
> **jb70115 said:**
> I have the solution. Fixed mine...
Now I need to fix bad/intermittent connection that causes screen to flicker until I push on the back (of screen).
THANKS!

---

