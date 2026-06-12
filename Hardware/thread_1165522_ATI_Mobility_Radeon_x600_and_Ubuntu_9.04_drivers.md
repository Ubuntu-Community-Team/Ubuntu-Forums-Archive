---
title: "ATI Mobility Radeon x600 and Ubuntu 9.04 drivers"
date: 2009-05-20
forum: Hardware
---

### Post by hatorade on 2009-05-20
After reading up a bunch on Google and these forums, I see that there is some seemingly non-trivial complexity to getting my ATI Mobility Radeon x600 driver to function properly on Ubuntu. 

My question is: Is all I can do about getting my graphics card to work the best just use the default ubuntu drivers? Should I install some other sort of driver to get the most out of my video card? I would like to be able to use Compiz and other things (I think Boxee doesn't work because of my graphics card too). 

Thanks

---

### Post by Viligam on 2009-05-21
Not sure if this helps, but here is a news response to the question ...

[http://www.linux-magazine.com/online/news/proprietary_driver_for_ubuntu_9_04_fglrx_for_x_server_1_6](http://www.linux-magazine.com/online/news/proprietary_driver_for_ubuntu_9_04_fglrx_for_x_server_1_6)

**"Proprietary Driver for Ubuntu 9.04: Fglrx for X Server 1.6 **

         Dimon                  Apr 27, 2009 7:52pm  GMT  	
         				After upgrading to Ubuntu 9.04 I've found that there is no Fglrx driver for ATI X600 card.
The open source driver is only good to play a tux racer, very sluggish performance.
I've tried to install the latest ati-driver-installer-9-3-x86.x86_64.run from ATI web site but it gives an error: "Error: ./default_policy.sh does not support version default:v2:i686:lib::none:2.6.28-11-generic;"
I've installed then  Fglrx through package manager but it made computer freeze.
I found funny that recovery mode has option to fix video related problems which was useless in my case.
I've tied to reconfigure xserver: dpkg-reconfigure -phigh xserver-xorg without success.
Eventually I had to remove Fglrx driver.
[U][B]
My opinion is: dont't upgrade to Ubuntu 9.04 if you have ATI video card[/B][/U]"

---

### Post by hatorade on 2009-05-22
I guess the question I'm getting at is the following:

I installed Ubuntu 9.04. I have a Radeon Mobility x600 graphics card. Did the Ubuntu 9.04 installation install the best drivers for my graphics card for me, or do I need to install a better one? As of now, I can't use the 'normal' or 'extra' graphics settings.

---

### Post by del_diablo on 2009-05-24
ATI do not longer make drivers for a few of their cards(older than the Radeon 2000 series), which is quite alot. I find it stupid that they did not make legacy for it, its a pain for people with those cards.
Anything newer than Radeon 2000, they got drivers for that supports 1.6...

---

### Post by ScottSawyer on 2009-09-10
same issue on my "older" Aspire 5000.  Had some other issues with sisfb in /etc/modules.

maybe someone will put up a driver and a link? Please?

---

### Post by markbuntu on 2009-09-11
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by ScottSawyer on 2009-09-11
Wow, a gentleman and a scholar.

I am about half way through the instructions, post back later.

Thanks again.

---

