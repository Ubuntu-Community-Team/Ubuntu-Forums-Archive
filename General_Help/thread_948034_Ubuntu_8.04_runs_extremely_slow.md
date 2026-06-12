---
title: "Ubuntu 8.04 runs extremely slow"
date: 2008-10-14
forum: General Help
---

### Post by kshaff03 on 2008-10-14
I was given a compaq presario from a friend. I threw a 160 GB hard drive in it and installed ubuntu with the intent of using it as a backup file server and SVN server.

Its only a PIII, but performance has been acceptable.  I installed SVN a couple nights ago and had it set up. I noticed that I had about 6 new updates and I clicked to install them.  I let them install over night.  The machine has been nearly unresonsive ever since. Its extremely slow.  It takes 30 seconds to popup a console window.

I've rebooted several times and even logged into failsafe console mode.  Commands appear slow even in that mode.

One thing I've noticed is that when logging in, I get a message saying "There was an error starting GNOME Settings Daemon....Possible reasons include : the remote application did not send a reply, etc. etc."  I think this error message is more of a symptom of the slowness than the cause of the slowness.

If I run top, cpu usage is low.  So is disk and memory usage.  I've noticed some issues posted about compiz, but I don't appear to have that installed.  Many applicatoins won't even start.  Firefox will come up, but most websites time out before downloading a page.

The only thing I can attribute this to is that one of the updates messed things up, but I can't run synaptic to get any installations history.

As far as I recall, the only programs I've installed were samba and svn.  SVN isn't even running. I'm stuck.

Any ideas?

Thanks

---

### Post by oilchangeguy on 2008-10-14
first, about your 160gb hard drive. i doubt your pIII bios sees the full 160gb. have you checked?

---

### Post by BobJoe on 2008-10-14
might want to post some tech specs

---

### Post by exploder on 2008-10-14
Take a look at your services and sessions and disable anything that you do not need running. The gnome settings error is common and easily fixed. To get rid of the error, open Sessions, select "Add", for name type, "Gnome Settings Daemon", for command type, "gnome-settings-daemon", for comment type, "Bug Fix" and click ok.

Make sure you don't use the quotes in the above mentioned fix and the error should be gone. Turning off Tracker will speed things up considerably, so I suggest turning it off in both Sessions and Services and you should see improvement.

---

### Post by kshaff03 on 2008-10-14
It looks like it recognizes 140 GB of the 160.

I tried adding the Gnome Settings Daemon to the sessions dialog, but no luck getting rid of the error.

I disabled everything in the Sessions dialog.  Rebooted.  Still slow.  

As far as specs are concerned, its a PIII Coppermine CPU. I'm not sure of the specifics.  I'm going to need some help getting a more complete specs.  Is there a command I can run to provide more detail? Oh, of course: 384 MB /RAM

---

### Post by kshaff03 on 2008-10-16
This is still an issue.  Any more ideas?

---

### Post by spawn. on 2008-11-04
I'm having similar issues on occasion. I usually ignore them but sometimes I'm like, wtf!@ My specs are 2.6GHz Core2Duo, 2GB Ram, 256MB OpenGL 570M, on a ThinkPad T61p. 

The freezing seems to occur at random. However, I encounter it more frequently when dealing with Audio files such as mp3, wav, wma, etc. When I go to add music to a media player, the application greys out, then loads up the songs. I do realize that adding a folder full of music to a playlist will slow the application down, but sometimes it will hault it to a complete stop.

---

