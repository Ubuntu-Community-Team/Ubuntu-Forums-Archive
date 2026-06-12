---
title: "Epson WP-4540 Ubuntu 16.04 Won't Print Cups &quot;filter failed&quot;"
date: 2016-04-04
forum: Hardware
---

### Post by linuxthunder on 2016-04-04
Downloaded the correct drivers from the Epson site and installed just like in 14.04 successfully and scanning is working fine but it won't print.

Printer is recognized and installed with proper ip address but printing test page says the state is Stopped "Filter Failed".  I read some threads with issue for earlier version of Ubuntu but it wasn't any different than what I have tried.

Any help would be appreciated.  thanks

---

### Post by thorstenfrank1978 on 2016-04-12
I had a similar problem for my Dell C2665 laser printer, and was able to solve it after much perusing of the internet. The "filter" that's referred to in the error message is an executable file which was, in my case, compiled as a 32 bit exexcutabl while my system was 64 bit. To make this work, you'll have to install the needed libraries like so:
sudo apt-get update
sudo apt-get install gcc-multilib libcups2:i386

---

### Post by linuxthunder on 2016-04-15
Thank you so much thorsten!  This worked perfectly after many hours of trying to get it to work.

Much appreciated!

---

### Post by mendieta on 2016-07-28
> **thorstenfrank1978 said:**
> I had a similar problem for my Dell C2665 laser printer, and was able to solve it after much perusing of the internet. The "filter" that's referred to in the error message is an executable file which was, in my case, compiled as a 32 bit exexcutabl while my system was 64 bit. To make this work, you'll have to install the needed libraries like so:
sudo apt-get update
sudo apt-get install gcc-multilib libcups2:i386

OMG. In my case, gcc-multilib was missing, and installing it fixed my issue (same error message as the OP). 

Thanks so much. Should this be reported as a bug? Mmm

---

