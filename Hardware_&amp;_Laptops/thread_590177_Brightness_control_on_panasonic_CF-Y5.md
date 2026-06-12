---
title: "Brightness control on panasonic CF-Y5"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by wmaelwys on 2007-10-24
I recently upgraded to Gutsy Gibbon from Feisty and my Fn hotkeys have stopped working. In feisty I was able to use Fn brightness controls to go from max/min brightness in one jump. (there was some script that fixed this but I didn't really care) I did a dist-upgrade to Gutsy and before the system restarted Fn hotkeys started working properly, going in intervals rather then min/max right away. However after restarting my Fn keys do nothing now. 

A bit of googling says I should see brightness controls in gnome-power-manager but I don't see anything of that sort there either.

I also tried changing brightness manually with "sudo echo x > /proc/acpi/video/GFX0/LCD1/brightness" but I get "permission denied". 

Any thoughts?

---

### Post by idlewild on 2007-10-24
I'm not sure 100% but my guess is that the Y-5 uses pcc-acpi for brightness like the earlier panasonic lite toughbooks. Do you have a directory called /proc/acpi/pcc/ ?

---

### Post by wmaelwys on 2007-10-24
Hm no I do not. I believe I remember having that directory under Feisty though. Is there a package I need to install to get that back?

---

### Post by LaVache on 2007-10-25
You are not alone.  I've got a Panasonic CF-74 which I recently upgraded from Feisty to Gutsy.  I have the exact same problem you're having with brightness and the Fn keys not working in Gutsy while they did work in Feisty.

I too am missing the /proc/acpi/pcc directory, leading me to believe the Panasonic acpi driver/module is missing or not loaded...?

---

### Post by LaVache on 2007-10-25
Progress!

I found the module -- it's part of Gusty but for whatever reason isn't being loaded.  To get it working, type the following into a terminal:

sudo modprobe pcc_acpi

That will load the Panasonic acpi driver.  And that's it -- your Fn keys should now be working.  

Took me a bit to figure this out, as I thought the module name was pcc-acpi rather than pcc_acpi.

I'll follow up with another post detailing how to get this to load on boot.  (There are a few ways, such as adding an entry in rc,local, though it'd be preferable to understand the problem and fix it appropriately rather than band-aid it.)

---

### Post by wmaelwys on 2007-10-25
Thanks, that worked perfectly.

---

### Post by firepulaski on 2008-01-17
I just installed Gutsy on a CF-Y7 and cannot get pcc_acpi to control the screen brightness.

I just posted to this thread:

[http://ubuntuforums.org/showthread.php?p=4154551#post4154551](http://ubuntuforums.org/showthread.php?p=4154551#post4154551)

My problem:

sudo su root -c "echo 1 > /proc/acpi/ac_brightness"   

changes the value in the file, but this has no effect on the actual screen.  HCanging the value of /proc/acpi/pcc/mute, however does mute the laptop so something is working in pcc_acpi.  I tried blacklisting the video module in case that was interfering.  No improvement.

---

### Post by jasonhaley on 2008-02-06
Thanks! I've been searching for a solution for weeks and thought I'd have to do a lot of changes..So have you figured out how to make the change permanent?

---

### Post by herme on 2008-02-15
Problem persists on Gutsy CF-Y7: the fix above does not seem to work, as 
mentioned by firepulanski. The function keys do bring up the 
small brightness window with the slider and move the slider, but I get only two 
levels: maximum and very dark. Cat'ing to /proc/acpi/ac_brightness has no 
effect.

---

### Post by bean1975 on 2008-04-12
You might find my solution to this problem at [http://ubuntuforums.org/showpost.php?p=3936173&postcount=7](http://ubuntuforums.org/showpost.php?p=3936173&postcount=7) -- it does not involve pcc_acpi which did not work out for me.

---

### Post by danosaka on 2008-07-15
:( HELP...I am having the same problem. I have installed Ubuntu 8.04 in my Japanese Panasonic CF-W4 and cannot adjust the brightness. The computer is unusable because of this. Can anyone help me? I am a beginner using Ubuntu. 

I tried the

sudo modprobe pcc_acpi

But had the reply:

FATAL: Module pcc_acpi not found

What should I do? My lap top in unusable!

---

