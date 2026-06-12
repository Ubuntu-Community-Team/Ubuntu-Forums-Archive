---
title: "ubuntu/linux netbooks"
date: 2011-11-13
forum: Hardware
---

### Post by motoperpetuo on 2011-11-13
i logged on to [www.zareason.com](www.zareason.com) today, ready to enter my credit card number and buy a netbook and...zareason apparently doesn't offer netbooks anymore. they did, like a week ago, but now there aren't any listed. 

i know that system76 stopped offering netbooks several months ago. i guess netbooks are dying out in favor of tablets, but i'd still like to have a bigger netbook (around 11.6" width) designed specifically for linux. anyone know if such a thing exists anymore?

barring that, if anyone out there has a netbook that's around 11'6" in width and 3.5 pounds (about 1kg) or so in weight that worked out of the box with ubuntu or mint, the make and model number would be useful information too.

---

### Post by ShopCoop on 2011-11-14
Hi, I dont not have the perfect solution, but I do have a solution that is working for me since I had the same struggle looking for a netbook 11.6" that would run ubuntu.

I have a HP DM1- 4010us running dual boot with 11.10(64) and Windows 7.  

Did work out of the box once I did a little tweaking and am very happy with the results considering that i have only had this laptop/netbook for a week or so.

Dual boot will require dumping a primary partition.  If you are not interested in dual boot, then turfing the windows and hp partitions will make life easier.  All the features, wifi, touchpad, etc all worked out of the box once I figured out the partition stuff.   

Only thing to be aware of is this runs a AMD E-450 Fusion with the integrated ATI graphics.  This does cause some issues since current flgx drivers have issues with this VERY new graphics system.  After a little research here on the forums, I was able to avoid/uninstall ubuntu's system drivers (additional drivers icon) and install catalyst 11.9 and remove the AMD unsupported hardware Watermark.

Everything seems to be running nicely now.  I am avoiding unity 3d however, seems to randomly freeze.  2d is SOLID! :)

Food for thought, hope it helps a bit.  

Cheers

---

### Post by motoperpetuo on 2011-11-18
thanks for your reply. that would also be a possible solution. for what it's worth, i contacted zareason, and they say they're planning on releasing a new, improved 11.6" netbook in time for the holidays.

---

### Post by ts3 on 2011-11-25
> **ShopCoop said:**
> Did work out of the box once I did a little tweaking and am very happy with the results considering that i have only had this laptop/netbook for a week or so.

Quick question on the dm1 4010us laptop: would you mind posting a bit more about the tweaking you did or point me to the forum posts/guides you used?  I just bought the same laptop & am having trouble with the wireless and the graphics.

---

