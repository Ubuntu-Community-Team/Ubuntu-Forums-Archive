---
title: "Howto get tv-out plus compiz working for an ati mobility 9600 on gutsy"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by gaupe on 2007-10-21
First many thanks to b:Lo[n|g]

[http://www.lunders-and.no]("http://www.lunders-and.no/wp/?p=96")



start  System / Administration / Restricted Drivers Manager 


select the ATI accelerated graphics driver 

after that your system will be rebooted.

to have compiz running you have to install xserver-xgl

do this by starting 

System / Administration /Synaptics Packagemanager 
and search for xserver-xgl.
mark and install it. 

Now for the tv-out part
In my case i had to have the s-video connected to the scart in of my tv and
then switch on my laptop. Otherwise my laptop would not see a tv connected.
it shoudl be actually working now only in my case i hade t switch it over from 
NTSC to PAL-B

this is doable with the aticonfig command but my system seemed to crash
until i found out that........

The fact is you are using Xgl, in addition to X. for the extra visual effects with the Compiz.
 Xgl however  is running on DISPLAY : 1
X on the other hand is running on DISPLAY :0. So when you use aticonfig on DISPLAY :1 it does not give you the correct information. 

To solve this do

```
 

export DISPLAY=:0
aticonfig -- whateveroption

```

So....
open up a command terminal and give the following commands

```

 export DISPLAY=:0
aticonfig -- aticonfig --tv-format=PAL-B

```

and it should work now 

check with 

```

 export DISPLAY=:0
aticonfig --query-monitor
 aticonfig --tv-info

```

what is connected and how the tv-out is set now


man aticonfig will give you all the explanation of posibilities

good luck.

---

### Post by K.Mandla on 2007-10-26
Moved to Hardware and Laptops.

---

