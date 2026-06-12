---
title: "USB-stick behaving strange"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by PereUbu on 2006-06-26
Hi

My USB-stick automounts just fine. The USB-folder pops up, and I copy a few files over to it, and then disconnect the stick. When I connect it again later on, it automounts but there are no files on the stick. Where did the files go? [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

I have tried everything I could think of, including reformatting the stick (fat32).

Is this a Dapper-bug, or is it something I can do to solve the problem?

By the way the stick is a Verbatim 512mb, and works just fine on my girlfriends windows-pc. 

Best regards
PereUbu

---

### Post by glinsvad on 2006-06-26
> 
The USB-folder pops up, and I copy a few files over to it, and then disconnect the stick.

Do you unmount the USB-drive before unplugging the stick? Otherwise I'm pretty sure no changes are written to the USB-drive. It's simply a matter of delayed writing...

---

### Post by PereUbu on 2006-06-26
Yes, you're right Glinsvad. It works when I unmount the stick first. Thank you for sharing your info!

Ubuntu-devs:
I really think that the Ubuntu-system should write the files to the USB-stick at once and not when unmounting. Desktop-users are used to just unplug the device and carry their files with them and will do the same mistake as I did, which is a unpleasant surprice when you just need those files you thought were on the stick. So please dear Ubuntu-devs, change this!

Another thing is that when I right-click the USB-stick icon on the desktop it for some reason says *eject* the device and not *unmount* the device.

All the best from
PereUbu

---

