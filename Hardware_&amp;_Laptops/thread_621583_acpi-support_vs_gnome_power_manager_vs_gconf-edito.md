---
title: "acpi-support vs gnome power manager vs gconf-editor"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by Bigbird999 on 2007-11-23
Trying to get my laptop to suspend and resume properly.  Lots of issues, but here is where I am now.  I have it set to suspend when I press the suspend button or when I close the lid or when I select the logout button and then suspend in the GUI menu.  All suspend the machine as expected.  But when I try to resume (by pressing the suspend button on the keyboard) it only resumes properly if I have suspended by using the logout>suspend icons.  If I suspend it by closing the lid or pressing the keyboard button it appears to resume, (i get a flashing cursor and then a black screen while the  system continues to start up)  The wireless  card lights up and I am pretty sure that it is stuck at the password screen, but since I have a black screen I can't see it.  

To this newb, it appears that the hardware suspend (lid and keyboard buttons) suspend in a different manner than the software (logout>suspend) buttons.

In trying to solve this I have followed a lot of threads and discovered that there are suspend settings in acpi-support, gconf-editor>gnome power manager and the gnome power manager.  I am pretty sure that I have some conflicts going on but I can't seem to sort this out. I also know, judging by the numerous threads, that I am not alone in having an issue with suspend/hibernating and resuming on a laptop.  BTW this function works flawlessly in Win2K (I'm double booting) so it is an issue with Ubuntu configuration and/or hardware support and not a hardware issue.. 

I guess what I need to know is which of these settings in which file is the key?  Or at least how do I get the hardware buttons to behave like the software button?

BB

---

