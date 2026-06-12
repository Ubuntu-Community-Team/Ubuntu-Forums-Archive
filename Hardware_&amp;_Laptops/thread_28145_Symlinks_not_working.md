---
title: "Symlinks not working??"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by TurboDan on 2005-04-19
Hello all,

I downloaded my first version of Ubuntu (Hedgehog) yesterday to replace FC3 on my computer.  This is also my first Debian-based Linux OS.

I am currently trying to get GTKpod to work with my iPod Mini.  In FC3, the OS mounted my iPod and displayed it as a USB device on the desktop.  Ubuntu does the same.  To allow FC3 to read the database, I created a symlink from where the OS mounted my iPod to where GTKpod looks for it:  /mnt/ipod.  Ubuntu mounts it in /media/DANIEL'S IP.

Now, it seemed like a no-brainer to simply make a similar symlink in Ubuntu.  However, for whatever reason Ubuntu does not want to create the symlink.  I did:

ln -s /media/DANIEL'S IP /mnt/ipod

(as root, of course)

...and the terminal never confirmed the symlink.  In fact, it simply jumped one line down with a 

>

mark.  That's it.  It never reset back to root@ubuntu.  Later, I pressed Ctrl+C and it went back, but the symlink doesn't seem to have been created.  Any thoughts on this would be appreciated.  This was quite simple in FC3.

On another note - I generally like Ubuntu alot, but they have alot of issues with sound.  It took me forever to get AAC files working - and then forever to discover I had to shut off system sound to get ALSA programs to work!

Thanks in advance for any help you can offer!

---

### Post by bored2k on 2005-04-19
Try
ln -s "/media/DANIEL'S IP" /mnt/ipod

Yes Ubuntu is having a hard time with sound. But I didnt see any major problems on my installs [I use eSound]. What programs are you having problems with ?

---

### Post by TurboDan on 2005-04-19
Thanks for the quick response!  

But, alas, before I read it, I discovered what a dummy I was and fixed the problem.  Turns out that the newest version of GTKpod actually allows you to identify the mount point right in the Preferences menu!  

So, I typed it in and everything loaded from my iPod!

Yup, I was a little surprised about the sound issues, especially since audio programs are a huge part of personal computing these days.  But, I found my way around that and have everything from my MP3s to my AACs working, and DVD video playing as well.  I'm already enjoying Ubuntu alot more than FC3 - it's faster too!  I was using XMMS to try to play AAC files.  I installed the libraries and everything required, but the program locked up whenever I loaded a file.  Once I disabled the system sound, it worked fine - along with a couple of my other media players.  I'm going to go over the workarounds for having esd and ALSA work at the same time tomorrow.

---

### Post by bored2k on 2005-04-19
I suggest you forget about xmms and start using beep-media-player ;). Beep supports xmms skins and has most of the plugins working ;).
[http://www.sosdg.org/~larne/w/Plugin_list](http://www.sosdg.org/~larne/w/Plugin_list)

---

