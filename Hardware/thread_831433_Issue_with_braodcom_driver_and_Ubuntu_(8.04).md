---
title: "Issue with braodcom driver and Ubuntu (8.04)"
date: 2008-06-16
forum: Hardware
---

### Post by x_hxc on 2008-06-16
I recently just installed Ubuntu and now have a dual os, vista basic (downgrading soon) and Ubuntu 8.04. My Broadcom driver which is 4312 is not wanting to work or isn't even recognized with Ubuntu os, but when i switch to vista it connects directly with no problem and the lil blue light is on whilst in Ubuntu it's still red...
I have no way of accessing the internet while on Ubuntu not through WiFi nor through my Wireless Verizon USB. 
I'm quite new to ubuntu, or at least setting everything up.

The file b43-fwcutter i uninstalled and then reinstalled, only to find that each timethere is an error when i try to redownload, such as -

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) Could not resolve 'archive.ubuntu.com'

Is there some trick to this? I've tried 

sudo apt-get update or sudo apt-get install build-essential 
and with the update, i get the same 'W:Failed to fetch...'

WHy is my hardware not being recognized and how do i get it to work ?!

---

### Post by sergiom99 on 2008-06-16
maybe this tuto can help you configure your Wlan driver.
[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)
It helped with my broadcom 4328 and the writer used it for a 4311 chip.

---

### Post by x_hxc on 2008-06-19
:\ Didn't seem to work at all. I did a fresh install of Ubuntu again and it detects my card now. 
So i bring up the hardware drivers option. I press enable for the broadcom43 wireless driver,i put in the livecd and it starts installing package 'b43 fw-cutter'. Then it says----> Extract and install firmware? I check yes and continue and unfotunately it gives me an error :

...'subprocess post-installation script returned error exit status 1'

I just need to have an internet connection in able to download the firmware(b43-fwcutter)?

---

