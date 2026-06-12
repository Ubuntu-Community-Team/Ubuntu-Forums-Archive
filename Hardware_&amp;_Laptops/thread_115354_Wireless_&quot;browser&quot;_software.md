---
title: "Wireless &quot;browser&quot; software"
date: 2006-01-10
forum: Hardware &amp; Laptops
---

### Post by fritz_monroe on 2006-01-10
Let me start out by saying I am not tryign to do any war driving or anything illegal.

I am a Linux newbie.  I recently installed Ubuntu 5.10 onto my laptop and it's working great.  I set up the wireless to have 2 different locations so I can use my home network with encryption and a non-home network that does not have encryption.  The potential problem I see coming up is making sure that I connect to the correct network.  In XP, the wireless settings allow me to see the networks in range along with the SSID.  This allows me to pick the one that I'm supposed to connect to.  Is there an application that is easy to use and does basically the same thing in Ubuntu?

In case it makes a difference, I run Gnome mainly, but on occasion I use XCFE.

---

### Post by Sgood1971 on 2006-01-10
Once my wireless card had "seen" both networks. (I set the ssid for home, came to work and set it for there.) I simply changed the ssid name to "any" and it now picks up both no matter which one I am at. I have done this a few times having done numerous reinstalls and I have to manually set the ssid the first time before changing to 'any' for some reason.

---

### Post by prammy on 2006-01-10
Check the projects section in the forum and look for gtkwifi. That works great for me.

---

### Post by fritz_monroe on 2006-01-10
Sgood1971:
Thanks for the info.  What I was hoping to accomplish is being able to go to a hotel and not enter any info, just select the network off a list.  Then go to a convertion and just select the network.  No manual setup.  

[QUOTE=prammy]Check the projects section in the forum and look for gtkwifi. That works great for me.[/QUOTE]

Prammy:
  This is exactly what I was looking for.  That's the problem with being new to something, I don't know what to search on.  I'll pull this down and get configured as soon as I get home.

F_M

---

### Post by Sgood1971 on 2006-01-11
I haven't had a chance to try it yet, but [this]("http://www.kde-apps.org/content/show.php?content=33668") looks nice too.

---

### Post by fritz_monroe on 2006-01-12
That seems to be a little overkill for my needs.  I may give it a shot at some later date, but for now, GTKWifi fits the bill nicely.

F_M

---

### Post by DanceMan on 2006-01-14
This sounds like what I need also. 

Just about every touring show now sets up an open wireless network backstage for the crew. I found that Ubuntu 5.10 sometimes connected fine, but mostly would not. Occasionally it would connect, then lose it. The Win computers had no problem. Neither did I after I finally got the wireless driver for 2K installed in mine.

Ubuntu had the wireless card active and it seemed to have the signal. What it couldn't seem to do was to see the network. I noticed that the Intel software for my internal miniPCI wireless card consisted of the driver and a piece of software called ProSet. As soon as Proset was installed it popped up a dialog box with two networks showing, including the open one I knew was there. Ubuntu had shown only "Windows Network" and without the identifying network name. And I couldn't get it to connect.

If this bit of software does what Proset does, I'll be a very happy Ubuntu camper. I'm already impressed by how well it installs into recent laptops, and I've just put it into two.

---

