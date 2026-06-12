---
title: "really weird problem"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by gatsu85 on 2009-03-31
this is my fist post in this forum, so hello to everyone ):P

I'm actually having a weird problem that prevents me from using ubuntu

after a reinstallation of ubuntu intrepid I tried to copy my old home folder over the new one, to get all my settings back

after that i did ctrl+alt+F1 and wrote this commands:

sudo /etc/init.d/gdm stop
cd ..
sudo chmod -R 755 /home/gatsu
sudo chmod -R 644 /home/gatsu/.dmrc

as i always did to restore the files owning without having problems

now... after restart all of my settings were back (wich is good), but every window i open is completely blank (or black, depending on the window) and it goes back to normal only if resized. 
for instance if i open menu.lst it appear completely white, if i resize the window it goes back to normal, but any modification i make to the file isn't displayed until i resize the window again... 

this is appening even for the desktop, wich obviously can't be resized

after more than a year using ubuntu i was starting to think i became good at solving problems, but in this situation i really don't know were to put my hands...

please, if you have some ideas, help me

thanks

---

### Post by 123456789123456789123456 on 2009-03-31
I wonder if some of the files from your old installation were corrupt in some way.  if that were the case, then the changes you made, could have corrupted some other files in ubuntu.  Other than a complete reinstall, and setting things back manually, without copying, I don't know of a way to fix this problme.  It could also be related to somehting else, so hold on for other replies.

---

