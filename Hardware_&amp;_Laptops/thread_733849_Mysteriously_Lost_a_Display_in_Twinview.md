---
title: "Mysteriously Lost a Display in Twinview"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by rchille on 2008-03-24
Hello all!

I've been running my Dell D620 under Gutsy with an nvidia card for almost a year now with Twinview feeding the two monitors on my desk.

However, Friday I booted up and one of the monitors ( **right hand monitor**) remained dark. :(

I plug into my docking station, thumb the power and see grub displaying on the **right hand monitor** followed by the Ubuntu splash screen (also on the  **right hand monitor** ).  

Then **right hand monitor** goes blank and the login appears on the **left hand monitor**, and for the duration of the session I can't get anything to display on the **right hand monitor**.

I tried nvidia-settings (how I config'ed Twinview in the first place.) but it only lists the Laptop monitor and **left hand monitor** where it use to show all three. 

I looked at my /etc/X11/xorg.conf and the timestamp had not changed in a few months and the entry for both monitor was still in there.

I tried to reconfigure x with ```
dpkg-reconfigure xserver-xorg
``` and then running nvidia-settings but still no  **right hand monitor**.

The only thing I can think of that I did was try to use the "Fn+F8" key combo in a meeting to switch to an external display (It didn't seem to work),  But I've rebooted several times since then (and even tried to toggle it again a few time to see if maybe the setting is getting preserved and confusing things.)

Anyone out there have an idea to what might be wrong (and just as important how to fix!)

Thanks,
Rob

---

### Post by rchille on 2008-03-25
Interestingly enough, I discovered that if I Cltrl+Alt+F* when the new session pops up it is on the right hand display. :confused:

Anyone with an idea?

---

### Post by rchille on 2008-03-31
Still playing with this off and on.

I've found that if I swap the cables the behaviour with the two monitors reverses and now nvidia-setting can only see the right hand screen only.

Any ideas?

Thanks

---

