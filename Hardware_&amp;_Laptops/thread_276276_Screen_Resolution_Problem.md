---
title: "Screen Resolution Problem"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by Woodbadge on 2006-10-12
I have installed Ubuntu 6.06 desktop and I am using a Compaq 1701 LCD monitor.  The screen resolution has been set during the install as 640 x 480.

I have tried to change the resolution through System>Preferences>Screen Resolution but only that single resolution is offered.  Refresh rate is fixed at 60

I have tried to reconfigure the X server config file but managed to screw the configuration up despite accepting the default detected settings.  Fortunately I had backed up the old config file and I am back to square one with a very inappropriate screen resolution for a 17" monitor.

I am a complete novice with Linux so would appreciate any help I can get in as much detail as possible.

Thanks.

---

### Post by Kateikyoushi on 2006-10-12
Read [this thread]("http://www.ubuntuforums.org/showthread.php?t=179160&highlight=low+screen+resolution") seems some people found a solution.

---

### Post by Woodbadge on 2006-10-15
I have tried a number of options after reading more posts on this site, without success.  The last one was to manually enter HorizSync and VertRefresh information in the xorg.conf file as there were none previously set.

On reboot (the boot sequence went through OK) I have now ended up with the monitor telling me "Input Signal Out of Range" and accepts no keyboard input.

Is there any way I can access my system from this to change the xorg.conf file back to previous settings or have I got to reinstall?

---

### Post by Breepee on 2006-10-15
Are yoou sure your monitor supports higher refreshrates at that resolution? Most TFT's don't, as it is not necessary on a TFT to have high refreshrates (since it doesn't, unlike CRT's).

---

### Post by Woodbadge on 2006-10-15
Well, I suspect it doesn't as it has had the effect described in my last post.  But having tried a number of other options which didn't work I tried changing these settings.  

So, the question remains, can I get myself back to Ubuntu without reinstalling?

---

### Post by Kateikyoushi on 2006-10-15
You can do it by booting the live cd and mount the partition if necessary.
Then edit the xorg.conf file or just restore the backup if you created one.

---

### Post by Woodbadge on 2006-10-15
Thanks.

I ended up reinstalling and, strangely, the resolution was fine on the reinstall!!

Thanks for your help and ideas though.

---

