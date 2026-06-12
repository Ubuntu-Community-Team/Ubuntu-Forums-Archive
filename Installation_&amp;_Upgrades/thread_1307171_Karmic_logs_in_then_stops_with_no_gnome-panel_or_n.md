---
title: "Karmic logs in then stops with no gnome-panel or nautilus"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by tmckellar on 2009-10-30
Should have known it was too good to be true. I remember how in the old days it sucked beyond belief trying to upgrade from 5.04 to 5.10 or 5.10 to 6.06. I thought those days were gone after seeing how easily everything for Karmic downloaded and installed. Then I rebooted.

So here is what is happening. My problem seems to be in between what most other people are reporting. Grub works like a charm. I can login no problem. Then it just stops. I can see my background but there isn't a gnome-panel in sight and can't see the files on my desktop. Being a Gnome-do user I am able to get a terminal open and poke around, start Firefox, and even start up gnome-panel and nautilus. However when I fire up the latter two there are no icons and items in my main menu are missing. Played with gnome-appearance-properties and it tells me none of the icon theme packs are installed.

I can log into Kde and get the bar there but still no actual desktop. Failsafe Gnome has been the only thing to yield a different result so far. Everything works 100% in Failsafe Gnome. Not even logging in as root in recovery mode could do anything better. 

I am assuming there is a log file somewhere or some info in something that may be pertinent to my problem. If anyone can give me a clue as to where to look or what may be going on it is greatly appreciated. Thanks in advance.

---

### Post by Exüberance on 2009-10-30
I'm getting a very similiar issue. I just installed Ubuntu 9.1. After I updated the graphics drivers, it was working fine. I restarted a few times. No problem. Then I booted Vista (I duel-booted Vista and Linux, but I didn't do the partition with Vista so Vista refuses to believe that it exists), and then rebooted in Ubuntu, and it fails. All I can do is get the Ctrl+Ald+Delete/power-button menu.

I believe the problem is that Vista doesn't regocnize that another partition exists, so whenm I booted it, it somehow screwed up some files there so they no longer start, but since I can't remove the partition since Ubuntu uses it and Vista refuses to believe that it exists, I can't just delete it and try again. :(

I can access the terminal and trying a few commands such as SSH, GCC, CD, LS, etc. it seems to work fine, but I can't get anything graphical other than the background and the one window that appears when pressing the start button.

It's a 64-bit system, if that is at all relevant.

---

### Post by tmckellar on 2009-10-30
That does sound very similar to my issue. I dual boot with XP but haven't touched it in weeks. I have seen others that have restarted several times and then were able to get in but I have had no such luck.

Is it in anyway possible this could be a dbus issue? My first reboot I got a message about language files not being installed possibly related to ibus.

---

### Post by WhiteSphinx on 2009-10-31
After upgrade to Ubuntu 9.10, Gnome is frozen. I can only get it to work if I boot up in "Failsafe Gnome" mode. This is not as aesthetically pleasing because the desktop visual effects do not work.

---

### Post by tmckellar on 2009-11-01
I did in a manner of speaking find a solution. Backup all my stuff and start fresh. Unfortunately most people won't have two hard drives in their computer like I do or other computers on the network to back it all up to. So I am hoping someone can figure out what is going on with this and help others out there having this problem. Doing a fresh install was my initial idea several months ago but went ahead and tried the upgrade anyway. You live and learn I guess.

---

