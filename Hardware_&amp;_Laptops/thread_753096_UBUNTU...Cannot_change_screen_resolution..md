---
title: "UBUNTU...Cannot change screen resolution."
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by overdrank on 2008-04-12
> **damd70 said:**
> Changed from a CRT monitor to an Sony LCD with a Ubuntu dual boot pc.  I had to change screen resolution.  It went well.  Then I put in a KVM switch.  Left XP machine had to be readjusted  Went Well.  Right XP machine had to be ajusted and it went well.

The UBUNTU OS resolution cannot be changed from 640/480@50hz. No other options.  Following some very explicit instructs from Ubuntu forums specifically on this subject, I run into a problem fixing it, because Ubuntu lists the old CRT as the default monitor, not the Sony LCD which it is on.  I am afraid to change any text in this screen as it may never be right after that.  

I guess it is like making a change in the registry.  I know if I change The entry ¨ENVISION" to
"SONY",  it will work, but I am afraid to make things worse.  Ubuntu does see my video card correctly.  It is an amazing OS, but I am lost.  I am deep inside the OS ready to make a res change, then I noticed that the monitor was not correct.  Thank God.  I will leave this on all nite, because I will never find my way back to where I am at.  Hopefully I will wake to the right answer here.

Can some one tell me how to change the resolution under my  above crazy circumstances?

Thank you

Hi and if you install a new monitor I think a simple reconfigure of the xorg will do it. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```  in the terminal.

---

