---
title: "nmapplet in Avant-Window-Navigator (AWN)?"
date: 2008-08-27
forum: General Help
---

### Post by archeryguru2000 on 2008-08-27
Does anybody know of a way to integrate the nmapplet (or comparable) into the avant window navigator?  I've done a little searching, but to no avail.  Any help would be greatly appreciated.

thanks,
~~archery~~

---

### Post by archeryguru2000 on 2008-08-27
Bump... anybody?

---

### Post by archeryguru2000 on 2008-08-27
I've found this web-site that is (was) working on a network manager for AWN.

**_[Avant Window Navigator Forum]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=940")_**

Please let me know if anybody can assist in this.  I plan on trying to make this work on my own... but I'm not quite a programmer.  Any assistance would be greatly appreciated.

~~archery~~

---

### Post by forest.r on 2008-11-05
bump. please help everyone.

---

### Post by archeryguru2000 on 2008-12-27
Thanks for the bump forest.r
I feel this could be a great project for some folks.

---

### Post by archeryguru2000 on 2009-01-26
For all those interested (which is apparently only me), attached is the python code so far on the nmApplet for AWN.  I've received this code from [http://awn.planetblur.org/]("http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=940&page=1&isLive=true").  I hope somebody out there would be willing to assist in making this a reality.

~~archery~~

---

### Post by archeryguru2000 on 2009-03-04
Ok, using the attached applet I am able to display "some" information... some of the time. :-k  If anybody would be willing to assist in making this a reality, I would greatly appreciate it.

~~archery~~

---

### Post by kaivalagi on 2009-03-04
You probably ought to detail more about what you are trying to achieve in a AWN applet

I had a quick look at nm-applet and it doesn't even run on my 8.10 install

There is the gnome network monitor which is written in python, you may want to look at that instead to get some ideas: [http://gnetworkmonitor.sourceforge.net/](http://gnetworkmonitor.sourceforge.net/)

I checked out source via svn and there is a netstat module which could come in handy

Provide more info and I'll try to assist, when I have the spare time ;)

---

### Post by archeryguru2000 on 2009-03-05
> **kaivalagi said:**
> You probably ought to detail more about what you are trying to achieve in a AWN applet

I had a quick look at nm-applet and it doesn't even run on my 8.10 install

There is the gnome network monitor which is written in python, you may want to look at that instead to get some ideas: [http://gnetworkmonitor.sourceforge.net/](http://gnetworkmonitor.sourceforge.net/)

I checked out source via svn and there is a netstat module which could come in handy

Provide more info and I'll try to assist, when I have the spare time ;)

Thank you very much for the reply kaivalagi.  It was getting a bit lonely in here.  ;)  I appreciate the link to the network manager website.  However, that's not quite what I had in mind.  I'm trying to "duplicate" part of the **_[COLOR="Blue"][nm-applet]("http://projects.gnome.org/NetworkManager/")[/COLOR]_** (that is displayed on the desktop panel) into the AWN dock bar.  On my work laptop (Dell Latitude), I've been able to succeed in making it work (sort of).  However, on my personal laptop (HP Pavillion)... not so much.  I'll try to remember to take a screenshot of my work comp to show you how it looks on there.  Below is a screen shot of how it looks (or doesn't) on my home comp.  The nm-applet only shows up as a vertical bar.  I would prefer it to appear as it does below in the second image.  Not sure if you're able to help, but I thank you for your response.

~~archery~~

---

### Post by kaivalagi on 2009-03-05
If I were you I would start by creating a normal gtk window based app, and get it to output correctly what you want to see...

Once you have that working then look at integrating the code into the awn applet framework.

That way you'll know whether issues like you're having relate to AWN based coding issues or the functionality you seek...it will also help with testing :)

If you can get a gtk window based test rig together like this I can download and run it locally without having to go through unnecessary steps to debug. I can then see what I can do to help...

I don't have wireless, does that matter...I assume the app is for any network connection?

---

### Post by archeryguru2000 on 2009-03-06
You would not (ideally) need wireless for this, just some type of connection to the outside world.  I'll see what I can do about the gtk window.  Thanks for the assistance, I greatly appreciate it.  I'll keep you posted on my progress.

~~archery~~

---

### Post by archeryguru2000 on 2009-06-05
I feel like an idiot!  I/we already have a working network manager for AWN.  It's called 'Notification Area' just like in the gnome panel.  Attached is a screenshot of my network monitor.  I would still like to continue working on a separate applet just for monitoring the network, but for now I will have to put it on the back burner.

~~archery~~

---

### Post by kaivalagi on 2009-06-05
> **archeryguru2000 said:**
> I feel like an idiot!  I/we already have a working network manager for AWN.  It's called 'Notification Area' just like in the gnome panel.  Attached is a screenshot of my network monitor.  I would still like to continue working on a separate applet just for monitoring the network, but for now I will have to put it on the back burner.

~~archery~~

Extra features would be nice ;)

Just post back when/if you have any questions on writing a new applet, I'll see if I can help (I haven't written a awn applet before)

---

