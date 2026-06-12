---
title: "Rhythmbox: Default Audio Player In Firefox"
date: 2008-07-17
forum: General Help
---

### Post by Pipistrelle on 2008-07-17
I'm trying to set Rhythmbox as the default player for various audio stream file extensions in Firefox. I have already set it up in "preferred applications" on the desktop. I am wondering what the file path is for finding it in the "choose application" box in the firefox 3.0 options Window? Every time I click a link for an audio stream, Totem comes up.

Thanks in advance :)

---

### Post by bmac on 2008-07-17
I believe it's:
Firefox/edit/preferences/applications

If you wish to use an app that isn't in the selection box - select "use other". 

I believe Rhythmbox is located in: 
"File System"/user/bin


Hope this helps.....

---

### Post by Pipistrelle on 2008-07-17
Thanks. I got it to work in root using the "gksudo" commands for Orca screen-reader and Firefox, but it blows up when I try to open the /usr/bin/rhythmbox location within my user/administrator account. I get no password prompt, either. Odd. Thanks.

---

