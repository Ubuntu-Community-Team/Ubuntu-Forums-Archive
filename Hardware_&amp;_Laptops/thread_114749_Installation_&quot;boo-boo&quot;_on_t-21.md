---
title: "Installation &quot;boo-boo&quot; on t-21"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by catalina on 2006-01-09
Hi, newby from Canada.  I recently installed ubuntu on 4 of 5 laptops and works great.  I made a mistake on the 5th.  I was setting up the usernames differently (not writing them down) and on the 5th one I forgot the username that I had used.  I thought the easiest thing for me to do was to re-install ubuntu, but now I think I have created a mess.  I cannot format the hard-drive (or I am not familiar with how to re-install/fix the previous installation) and I cannot use the laptop.  The re-installation only goes so far then I get error messages.

I am using 5.10 breezy.  When I start the install from CD I can see the partitions on the hard-drive but I cannot erase them, or I don't know how to proceed from there.

I am extremely happy with ubuntu but totally frustrated with the installer! (me!).

Can someone spare some patience and help please.

Thank you.
Dean.

---

### Post by Greg2 on 2006-01-09
[QUOTE=catalina]
I am using 5.10 breezy.  When I start the install from CD I can see the partitions on the hard-drive but I cannot erase them[/QUOTE]
If you have already decided to do a complete reinstall, then the easiest way (imho) would be to d/l the System Rescue CD iso image and burn a System Rescue CD and use that to fix, change and reformat your drive. Then your can install the new Ubuntu system without any problems like permissions and usernames that you can’t remember.

The iso image is here:
[http://www.sysresccd.org/download.en.php](http://www.sysresccd.org/download.en.php)

You simply boot from the CD and hit ‘enter’ at the message Boot, Then when you get a command prompt enter:```
run_qtparted
```

If you have never used QtParted you should read the manual first.

---

### Post by catalina on 2006-01-09
Hi Greg,

Thank you for your help.  I read through and tried doing what you had suggested except I had to amend it a little.  I don't have a burner for these units (they are just for customers checking in at our lodging establishment) so I used a windows ghost cd I had in my cd os graveyard pile, ghosted 2000 pro onto the hd and re-installed ubuntu with success.  I really need to get a burner for these units!!

Thank you for your help.  I really appreciate you taking your time out to help us "nit wits."

Dean.

---

