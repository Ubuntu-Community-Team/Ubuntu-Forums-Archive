---
title: "T60p GPU running too hot!"
date: 2008-05-04
forum: Hardware
---

### Post by ajith.ranabahu on 2008-05-04
Hi all,
I upgraded my T60p laptop to Hardy about a week ago (it was on Gutsy and Feisty before then). Since this one acts as one my home servers it runs 24-7. However to my dismay it got stuck after 24 hours of upgrade and the cause seemed to be the heat ! I was thinking the apmd/acpi screwed up somehow but they are working fine. After getting the sensor applet it is showing me the GPU is running constantly around 80 to 85 oC which I suppose is a pretty high temp for the device ? (the fan runs nonstop). So far it got stuck twice (which never happened with Gutsy or Feisty)

I've been running fglrx driver all along and I don't think that could be the problem. My configuration (important specs) is as follows

cpu  - dual core T2600
ram 2 GB
graphics ATI MOBILITY FireGL V5200

Any hints are appreciated 

Thanks

---

### Post by andersq on 2008-05-06
I'm still running Gutsy but this might work for you to. I'm not sure if I had to install something, but I don't think so. For further info check:

[http://www.thinkwiki.org/wiki/Category:T60p](http://www.thinkwiki.org/wiki/Category:T60p)

It seems the GPU has three different powerstates that can be checked by typing

aticonfig --list-powerstates

in a terminal.By default it runs at the highest state. Setting the powerstate to minimum doesn't seem to make any difference to performance for me. Command to set lowest powerstate is like this:

aticonfig --set-powerstate=1 --effective=now

which I added to my Sessions manager under System/Preferences.

Now my output looks like this:
me@x:~$ aticonfig --list-powerstates
    core/mem      [flags]
-----------------
* 1: 128/135 MHz  [low voltage]
  2: 324/135 MHz
  3: 398/324 MHz  [default state]

This decreased my temp reading by at least 10 degrees (now 67). Any tips to reduce it further are welcome.

Good luck.

/Anders

---

### Post by ajith.ranabahu on 2008-05-06
Hi andersq,
Thanks for the reply. I tried that and its failing with the following message

[I]Setting the requested power state failed or is not supported yet.
Possible reasons for failure:
  - thermal control is in effect
  - trying to set the current power state again
Modes unsupported due to bandwidth limitations:
  - dual head/big desktop/clone modes[/I]

The lap is connected to a 22' monitor and running at 1650x1050. Could that be the reason ?(the high resolution)

---

### Post by JacobSingh on 2008-10-05
I have exactly the same configuration (monitor and res) and exactly the same problem.

I am using the advanced dock though, and my GPU is even higher!

It always runs above 100deg!! and the CPU sits around 64

I tried setting the freq, and got the same error as well.  

If I even try to open a simple 3d app like neverball, the system hits the trip point in 5-10 seconds and shuts down.  Even without the monitor, this system runs really hot (but not as hot)... wish I could fix this.

---

