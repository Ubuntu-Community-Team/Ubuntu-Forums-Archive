---
title: "Wired networking broken in 8.10 latest update"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by MattParkins on 2009-01-29
Just got today's new updates and now wired networking does not work.  Thankfully I can still connect wirelessly!  The connection icon spins around and it says that it is acquiring an IP address but it never gets one.  My other computer on the network works just fine though I haven't upgraded it to the latest kernel yet.

I'm on a dell mini 9 having upgraded to Intrepid a few days ago.  Everything working great until this last update.

Does anyone else report a similar thing?  Is it just the dell mini or all computers or all netbooks or what... ?

What information would you like to help solve the issue?

---

### Post by bayouwillie on 2009-01-29
Same problem on my Acer Aspire One running Ubuntu 8.10. Everything good until the latest update (1/29). I can't connect to wired or wireless.

---

### Post by Acer Aspire Andy on 2009-01-29
The same has happened to my Acer Aspire One too. Ran updates on the 28th an the networking died.

However, it only happens if i boot into new kernel 2.6.24-11. If I select the previous version at boot it all works OK.

Does this mean that all the config files are Ok? Does the driver need updating or is an aspect of the new kernel?

Quite new to Linux so not really sure where to start!

Any help warmly welcomed!!!!!

---

### Post by MattParkins on 2009-01-29
I'd boot from earlier kernels and wait for the bug fix to come through.  Your config files will be fine I'm sure.

---

### Post by bayouwillie on 2009-01-29
I booted into the latest kernel (the one that has thrown us off) and reconfigured my wireless driver, following exactly the instructions using 'madwifi' in the Ubuntu documentation section for Aspire One:
[http://snipurl.com/aylz7](http://snipurl.com/aylz7)
wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
modprobe ath_pci

    *

      You may have to append ath_pci to /etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ath_pci

Wireless now works great again, but wired networking still out.

---

### Post by Acer Aspire Andy on 2009-01-29
How do you get use the wget function if you can't get on line?

I used this workaround when I first set up on ubuntu and it worked great but I can't see how to make it work in the faulty kernel.

Just out of curiosity, if it's all still configured correctly in previous kernels and they all use the same config files, why won't it work in the new one?

---

### Post by kitchensink on 2009-01-29
Hi, 
  I have an acer aspire one.   I have just updated with fixes from jan 29th.  The wired network now works.  Had the install mad wifi after the update.   All back to normal..

:p

---

### Post by bayouwillie on 2009-01-30
Good point. I simply went back to the madwifi folder in my Home folder. Didn't have to download. If you haven't used madwifi before, you would be out of luck.

---

### Post by bayouwillie on 2009-01-30
I also installed the updates on the 29th and it once again killed both wired and wireless connectivity. Tried to connect via ethernet cable to my AT&T DSL router (which had always worked painlessly in the past) and once again network-manager was spinning, both green lights, but could not connect. Had to go into madwifi again and reconfigure wireless to get it working (for the 2nd time). I would assume that the madwifi reconfigures are not playing with my wired connection...
Glad that someone's wired connection is working.

---

### Post by Neural oD on 2009-01-30
sometimes - as i've noticed the wired and wireless can conflict- if u don't need both at the same time - try disabling the wireless and manually enabling the wired

---

### Post by kitchensink on 2009-02-07
Hi,
   I think bayouwillie is correct the madwifi is interfing with the the wired one.  I now cannot connect to the wired after i install madwifi...

---

### Post by Vince4Amy on 2009-02-19
Nope madwifi is not interfering. I've just fresh installed and wired ethernet no longer works.

---

