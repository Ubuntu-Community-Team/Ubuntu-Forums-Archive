---
title: "PSP read only? can't trasfer files?"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by Weav on 2005-09-05
I connect my PSP to Ubuntu and it recognizes it as 992M Removable media. I click on properties and it says i can read write execute it.

I try to drag and drop files into the PSP but it says permission denied can not write.
I then tried to mv the file throught the command line where it says that its read only.

How can i change is so i can copy files? I try to change options but it says i'm not the owner of the disk? But up above it says steve is the owner of the disk. WHat is going on?

---

### Post by Vidar on 2005-09-10
[QUOTE=Weav]I connect my PSP to Ubuntu and it recognizes it as 992M Removable media. I click on properties and it says i can read write execute it.

I try to drag and drop files into the PSP but it says permission denied can not write.
I then tried to mv the file throught the command line where it says that its read only.

How can i change is so i can copy files? I try to change options but it says i'm not the owner of the disk? But up above it says steve is the owner of the disk. WHat is going on?[/QUOTE]
 I had no problems copying files TO my psp, but I have no way of deleting them properly (permissions) and even if I delete them they seem to still occupy as much space on my memorysticks as they did before, kind of odd... had an empty 512mb Memory stick duo that told me it had 92,6mb avaliable storage. I formatted it and it showed 512mb again...

Also, if you do not unmount the psp before disconnecting the unit, the files transferred will not be copied it seems. 

By the way, anyone know what video converting program would work best for converting my anime episodes into h.264-encoded video at psp-resolution?

---

### Post by Vidar on 2005-09-12
[QUOTE=Vidar]I had no problems copying files TO my psp, but I have no way of deleting them properly (permissions) and even if I delete them they seem to still occupy as much space on my memorysticks as they did before, kind of odd... had an empty 512mb Memory stick duo that told me it had 92,6mb avaliable storage. I formatted it and it showed 512mb again...

Also, if you do not unmount the psp before disconnecting the unit, the files transferred will not be copied it seems. 

By the way, anyone know what video converting program would work best for converting my anime episodes into h.264-encoded video at psp-resolution?[/QUOTE]


Nevermind that, now I cant even copy files to it... :(

---

### Post by senectus on 2005-09-18
[QUOTE=Vidar]I had no problems copying files TO my psp, but I have no way of deleting them properly (permissions) and even if I delete them they seem to still occupy as much space on my memorysticks as they did before, kind of odd... [/QUOTE]

This is because a .Trash-username file was created and the files moved into that folder.
Show hidden then delete the .Trash-username, that will clear the files properly :-)

---

### Post by Vidar on 2005-09-24
[QUOTE=senectus]This is because a .Trash-username file was created and the files moved into that folder.
Show hidden then delete the .Trash-username, that will clear the files properly :-)[/QUOTE]

Thanks, actually figured it out myself after some trial and error but nevertheless your answer will make a good resource for newcomers. :)

Now Im just looking for a good way of converting my anime on my stationary ubuntu machine, something like [http://www.pspvideo9.com/](http://www.pspvideo9.com/) would rock my socks. :)

---

