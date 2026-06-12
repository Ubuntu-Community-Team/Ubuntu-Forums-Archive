---
title: "Asus G75VW / Win7 / GTX 660M / Ubuntu 12.04.2 Install Issue(s)"
date: 2013-07-11
forum: Hardware
---

### Post by sieve70 on 2013-07-11
Greetings all!

My apologies for the new thread, but I have spent the last 3 nights scanning older threads without success - here and other forums - so I'm throwing this out to the audience for guidance / direction...

As the title states:

Asus G75VW w/ Win7 and GTX 660M
Installing Ubuntu 12.04.2 from DVD

I followed the guidance from the following thread regarding 12.04.1:

[http://ubuntuforums.org/showthread.php?t=2058444&p=12509635#post12509635](http://ubuntuforums.org/showthread.php?t=2058444&p=12509635#post12509635)

I can successfully obtain wifi connection through recovery menu, as well as connected wifi via upper right wifi icon / setup during install on ubuntu install desktop, so wifi is not an issue.

I successfully completed through step 12, including updating nvidia drivers via apt-get install nividia-current

After "RESUME" option in install, Step 12 in above link, I can not:

* Boot ubuntu from GRUB menu 
  - Purple screen if I go to recovery and then resume
  - Flashing underscore cursor in upper left of black display if boot directly
  - I have tried adding acpi=off through recovery - no joy (purple screen)
* Boot from ubuntu 12.04.2 live DVD - flashing underscore cursor in upper left of black display


I can still dual boot into Win7, all be it through a hoop, but that partition is still fine.

Any guidance / direction is appreciated!

Thanks!

-Dave

---

### Post by sieve70 on 2013-07-11
Any guidance / direction is appreciated!  Thanks again!

---

### Post by sieve70 on 2013-07-11
Okay - I have to respond because no one responded to me...

I had a gut feeling, and rebooted to my 12.04.2 live DVD, then I re-installed without changing anything...

Gee - it worked, and I am posting now from ubuntu on my G75... 

I'm wondering if I should still do the install of nvidia-current, as I have full 1920x1080 resolution and my dual monitor setup is working perfectly, but I will wait (at least for some time) until someone actually responses to me here on this front before I get adventurous...

---

### Post by sieve70 on 2013-07-12
Okay - I rebooted, and FUBAR...

I'm now stuck at ubuntu splash screen with all progress "dots" highlighted...

I was in after install reboot, and now it's froze on subsequent reboots... ideas?  Anyone?  

I spent 2+ hours setting things up and downloading android master repo for os mods I wish to work on... now I feel I have to restart again...

Wishing for help here... :(

---

### Post by sieve70 on 2013-07-12
Since I had to re-install again, I've done some test cases, and I've identified the fault condition -

I have a secondary monitor, HP 24", that I have connected to VGA output of the G75.

If I reboot / powerup with this display attached, then I end up in a permanently stuck ubuntu splash screen mentioned above...

That one ring any bells for anyone?

---

