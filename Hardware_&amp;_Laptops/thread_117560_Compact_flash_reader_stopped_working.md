---
title: "Compact flash reader stopped working"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by linux-noobie on 2006-01-15
In installed Ubuntu a while ago then added the kububtu desktop ... 
This was working great and when I add a CF to my built in USB connected card reader I got a little icon ..

Then I had some updates to make in adept and after changing everthing went weird.  

Now I can't see it at all although my 3 USB 2.0 disks do all work although they keep changing name ... to things like usb0 then media2 then sdc1 etc.  

Still at least these still work but I can't read my CF at all.  

If I look in the KDE info USB thing it shows the 6 in 1 reader but no Cf card.  

Please help I don't want to have to keep rebotting into Windows to get my photo's transferred.

---

### Post by linux-noobie on 2006-01-15
Well I guess noone is going to answer this.  So I tried googling and saw soime stuff about udev.  
So anyway I looked in the package manager thing and found the udev entry.  
It was updated to a new version ..(-15)

After this I added devfs=mount to the grub options and rebooted and it worked.  

I guess I will just not do updates from now on since it seems they break the system ..

---

### Post by coaxx on 2006-01-22
wouldt be nice if somebody couldt tell us if things work again in the repository.

---

