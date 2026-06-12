---
title: "Weird issue with automounting USB drive on Xbuntu. Only automounts on reboot."
date: 2014-05-21
forum: Hardware
---

### Post by dmanww on 2014-05-21
I upgraded xbuntu yesterday and it seems to have scrambled the settings a bit.
  
I have an external USB drive that needs to be automounted when the computer powers on.

  
Here is what it's doing. If I start the machine from scratch it will  not automount. But if restart, it will automount  perfectly. Even if I don't mount it after the initial boot. 

  
org.gnome.desktop.media-handling.automount is set to TRUE 

  
org.gnome.desktop.media-handling.automount-open is set to FALSE.

  
I'm running an SSD main drive and someone has suggested that it's  booting too quickly. I disabled fast boot and it took an extra 10 sec or  so to boot, but still has the same behavior.

  
The weird thing is I have auto open disabled but when it automounts  on reboot it still auto opens. Maybe something is making it ignore the  settings.

  
Any ideas what could be causing this?

  [URL="https://www.dropbox.com/s/1p02dt4fhaxmk5l/USB%20issues%20fstab.txt"]
Extract from fstab[/URL]

---

### Post by dannyboy79 on 2014-05-21
if you want it to be mounted upon bootup and always in the same folder you need to add it to your fstab file.

---

