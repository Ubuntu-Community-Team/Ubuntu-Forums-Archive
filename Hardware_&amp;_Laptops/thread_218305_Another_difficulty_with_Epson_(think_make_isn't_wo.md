---
title: "Another difficulty with Epson (think make isn't working)"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by wandd on 2006-07-18
I am trying to get our Epson C1100N printer working.

It is on the network (and works fine from win & OS X machines).

I have CUPS installed on Ubuntu and downloaded the CUPS drivers for this model from here:
[http://www.avasys.jp/english/linux_e/dl_laser.html](http://www.avasys.jp/english/linux_e/dl_laser.html)

The instructions say to go to the directory and run ./configure; make; sudo make install, followed by restarting cupsys.

However, it doesn't work for me (I get the printer apparently installed, but it won't print a test page (or anything else) - just sits in the printer dialog without apparently bothering the printer itself.

I think the problem could be at the 'make' stage above - I get the following message:
make  all-am
make[1]: Entering directory `/home/will/Desktop/Epson-ALC1100-filter-1.0'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/will/Desktop/Epson-ALC1100-filter-1.0'

Configure appeared to have worked, but surely make needs to do something.

Does anyone have any suggestions?

Thanks
Will

---

### Post by claydoh on 2006-07-18
You might run ./configure again and look for some info there, perhaps paste the results. There is probably something missing you need to compile the driver.

I would try these steps:
(A slight modification to the steps listed in [this post]("http://www.ubuntuforums.org/showpost.php?p=592191&postcount=2"))

Install the package '[build-essential]("http://packages.ubuntu.com/dapper/devel/build-essential")' via synaptic or apt, which will install all the needed compiling bits.

Next, install the package [libcupsys2-dev]("http://packages.ubuntu.com/dapper/libdevel/libcupsys2-dev") which will install the dependecies required to compile the driver.

Then unpack the driver file you downloaded, then run 
```
$./configure
$make
$sudo make install
``` 
then, once that is done, you need to restart the cups printing system:
```
 $sudo /etc/init.d/cupsys restart
``` 
Then in the printer admin, select "AL-C1100"

Note I do not have this hardware, so I cannot test to see if it works in Dapper (the original was for Breezy, but it should work)

---

### Post by wandd on 2006-07-19
Thanks for the tips. I had a quick play yesterday evening but I think I have unchecked a repository I shouldn't - build-essentials isn't in my list of packages in synaptic.

I will have another look at it and see if I can get it working - if not I'll post the results of ./configure here. Won't be here till Friday as I'm on the (not-yet-ubuntu) laptop until then.

Thank you for taking the time to help.

Will

---

