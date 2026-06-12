---
title: "Mounted hard drive not showing up in &quot;computer&quot;"
date: 2009-10-20
forum: Hardware
---

### Post by disophisis on 2009-10-20
I'm using virtualbox and I'm actually using kubuntu 9.04, but it's probably not much different from Ubuntu in this regard. 

I have created a 10 gig virtual disk and formatted it as ext4 and mounted it to /media/store

I can get to that directory and it seems the hard drive is there (it shows the proper capacity) but after sudo mount -a and rebooting the virtual machine, It's not showing up in "Computer", with the rest of the media.

any idea what I should do?

if you need my fstab contents or something let me know :)

thanks!

---

### Post by skatinjj on 2009-10-20
When you go to computer in your virtual machine, you can not see a device labeled "file system"?

---

### Post by disophisis on 2009-10-20
When I hit the K menu in the bottom left, go to Computer, and look under "Places" I get the following:

Home

Network

Root

Trash

I read an article and I've double checked to make sure I didn't miss anything, and the article said after adding the entry for the device into /etc/fstab, then reloading fstab, the volume should show in places.  The volume is called 'store', so no, it probably won't say file system... to my knowledge.

edit - however, if I open File Manager, and look on the left, there is a "places" heading, and under that, I see "volume"... which is the device I'm looking for.  Odd.

---

### Post by skatinjj on 2009-10-20
Misread your post / replyed to wrong post...sorry.

Try adding the virtual drive in the settings menu.

Settings > Hard drive > add hard drive

---

### Post by disophisis on 2009-10-20
This may be where KDE differs from Gnome...there's not a settings menu with hard drive in it.  Hmm...

---

### Post by disophisis on 2009-10-20
WAIT! 

I think I found it... thanks so much, I think you gave me the idea.

I went to System > file manager

on the left, under places, i right clicked the volume that I mounted earlier and selected "add entry"

added an entry called Store and set the location as /media/store

works like a charm :)

also had to do sudo chmod 2777 /media/store  

to get permissions and everything.

---

