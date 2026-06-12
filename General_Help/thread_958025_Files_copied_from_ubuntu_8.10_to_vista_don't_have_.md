---
title: "Files copied from ubuntu 8.10 to vista don't have &quot;read and write&quot; permissions"
date: 2008-10-24
forum: General Help
---

### Post by indieB on 2008-10-24
First of all I am a newbie as far as linux is concerned.

Ok. So here's the thing.

Yesterday, I Upgraded from 8.04 to 8.10 Beta and then today it downloaded updates for the 8.10 RC .

Here's the problem:  Any file or folder I copy from ubuntu to vista(windows in general) doesn't seem to have any read write permissions.

I basically cannot open the copied files when using windows.

I did not have this problem when I was using 8.04 so, I don't know what to do.

When I access the file(which is in the ntfs file system) from ubuntu, I can use it but in properties->permissions, all the menu bars are greyed out and at the bottom it says " YOU ARE NOT THE OWNER SO YOU CANNOT CHANGE THESE PERMISSIONS"

---

### Post by doas777 on 2008-10-24
if you are an administrator on the windows box, you can take ownership of the files, under file properties -> security -> advanced -> owner .

once you have ownership, set the permissions to your liking.

good luck, 
Franklin

---

### Post by indieB on 2008-10-24
Actually, ubuntu just updated while I was typing this issue and now after the update, i tried copying a file and then I accessed it from windows and it works just fine.

I guess, someone else found it ahead of time.....


Thanks a lot for the suggestion but before this, windows won't even let me touch the file let alone set the permissions.

---

