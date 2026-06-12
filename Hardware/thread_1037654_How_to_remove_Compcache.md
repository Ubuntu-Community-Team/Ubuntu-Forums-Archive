---
title: "How to remove Compcache"
date: 2009-01-12
forum: Hardware
---

### Post by ZeroTruths on 2009-01-12
For those of you who don't know what CompCache is, here's what it is: [http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

Essentially, it allows systems with weaker specs to run Ubuntu without any major hickups (lag). This is good for a Live CD. However, since I've installed Ubuntu, I wish to remove it.

Any ideas as to how to remove it?

---

### Post by kozimodo on 2009-03-05
I'd like to know too.

---

### Post by SuperCurro on 2009-03-06
> **ZeroTruths said:**
> For those of you who don't know what CompCache is, here's what it is: [http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

Essentially, it allows systems with weaker specs to run Ubuntu without any major hickups (lag). This is good for a Live CD. However, since I've installed Ubuntu, I wish to remove it.

Any ideas as to how to remove it?

I have the same problem, but I need disable it

My problem is this:

My ubuntu 8.10 was stable, but now in few days the ram and swap memory full suddenly beacuse this problem



```
Mar  6 17:20:05 server wviewd[6996]: <1236356405384> : storing record for 2009-03-06 17:20
Mar  6 17:20:05 server htmlgend[7042]: <1236356405425> : Adding 10 minute sample for 2009-03-06 17:20...


Mar  6 17:20:05 server wvhttpd[7047]: <1236356405425> : WUNDERGROUND-send: http://weatherstation.wunderground.com/weatherstation/updateweatherstation.php?ID=ICOMUNID24&PASSWORD=fblanquer&dateutc=2009-03-06+160x1.6772fbf927d18p+648200x0.00000b7e6c844p-102205&winddir=346&windspeedmph=005&windgustmph=014&hu


Mar  6 17:20:05 server wvhttpd[7047]: <1236356405425> : WUNDERGROUND-send: midity=48&tempf=055.1&rainin=0.00&baromin=29.96&dewptf=35.700&weather=&clouds=&softwaretype=wview-4.0.1&action=updateraw


Mar  6 17:20:06 server wvhttpd[7047]: <1236356406067> : WEATHERFORYOU-send: http://www.hamweather.net/weatherstations/pwsupdate.php?ID=A20423A20&PASSWORD=fblanquer&dateutc=2009-03-06+16-0x1.5a140bf927d18p-128200x1.59e08b7e6c844p-88606&winddir=346&windspeedmph=5.0&windgustmph=14.0&tempf=55.1&rainin=0.00&ba


Mar  6 17:20:06 server wvhttpd[7047]: <1236356406067> : WEATHERFORYOU-send: romin=29.96&dewptf=35.7&humidity=48&weather=&softwaretype=wview-4.0.1&action=updateraw
Mar  6 17:20:11 server htmlgend[7042]: <1236356411285> : Generated: 1035 ms: 25 images, 15 template files


Mar  6 17:21:10 server htmlgend[7042]: <1236356470937> : Generated: 687 ms: 17 images, 15 template files
Mar  6 17:22:11 server htmlgend[7042]: <1236356531018> : Generated: 768 ms: 17 images, 15 template files


Mar  6 17:23:11 server htmlgend[7042]: <1236356591226> : Generated: 758 ms: 17 images, 15 template files
Mar  6 17:24:10 server htmlgend[7042]: <1236356650984> : Generated: 734 ms: 17 images, 15 template files


Mar  6 17:25:11 server htmlgend[7042]: <1236356711130> : Generated: 879 ms: 17 images, 15 template files
Mar  6 17:26:11 server htmlgend[7042]: <1236356771231> : Generated: 877 ms: 17 images, 15 template files


Mar  6 17:27:11 server htmlgend[7042]: <1236356831056> : Generated: 805 ms: 17 images, 15 template files
Mar  6 17:27:29 server kernel: [14438.135835] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


Mar  6 17:27:29 server kernel: [14438.135859] compcache: Error allocating memory for compressed page: 60594, size=4096 
Mar  6 17:27:29 server kernel: [14438.135871] Write-error on swap-device (254:0:484752)
Mar  6 17:27:29 server kernel: [14438.136813] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


Mar  6 17:27:29 server kernel: [14438.136824] compcache: Error allocating memory for compressed page: 60595, size=2093 
Mar  6 17:27:29 server kernel: [14438.136835] Write-error on swap-device (254:0:484760)
Mar  6 17:27:29 server kernel: [14438.137088] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


Mar  6 17:27:29 server kernel: [14438.137098] compcache: Error allocating memory for compressed page: 60596, size=4079 
Mar  6 17:27:29 server kernel: [14438.137108] Write-error on swap-device (254:0:484768)
Mar  6 17:27:29 server kernel: [14438.137342] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


Mar  6 17:27:29 server kernel: [14438.137351] compcache: Error allocating memory for compressed page: 60597, size=4073 
Mar  6 17:27:29 server kernel: [14438.137360] Write-error on swap-device (254:0:484776)
Mar  6 17:27:29 server kernel: [14438.137593] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


Mar  6 17:27:29 server kernel: [14438.137602] compcache: Error allocating memory for compressed page: 60598, size=4082 
Mar  6 17:27:29 server kernel: [14438.137611] Write-error on swap-device (254:0:484784)
Mar  6 17:27:29 server kernel: [14438.137840] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


Mar  6 17:27:29 server kernel: [14438.137849] compcache: Error allocating memory for compressed page: 60599, size=4079 
Mar  6 17:27:29 server kernel: [14438.137858] Write-error on swap-device (254:0:484792)
Mar  6 17:27:29 server kernel: [14438.138090] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


Mar  6 17:27:29 server kernel: [14438.138098] compcache: Error allocating memory for compressed page: 60600, size=4096 
Mar  6 17:27:29 server kernel: [14438.138108] Write-error on swap-device (254:0:484800)
Mar  6 17:27:29 server kernel: [14438.138342] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


Mar  6 17:27:29 server kernel: [14438.138350] compcache: Error allocating memory for compressed page: 60601, size=4061 
Mar  6 17:27:29 server kernel: [14438.138359] Write-error on swap-device (254:0:484808)
Mar  6 17:27:29 server kernel: [14438.138615] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


Mar  6 17:27:29 server kernel: [14438.138626] compcache: Error allocating memory for compressed page: 60602, size=4074 
Mar  6 17:27:29 server kernel: [14438.138641] Write-error on swap-device (254:0:484816)
Mar  6 17:27:29 server kernel: [14438.138941] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


Mar  6 17:27:29 server kernel: [14438.138949] compcache: Error allocating memory for compressed page: 60603, size=4096 
Mar  6 17:27:29 server kernel: [14438.138960] Write-error on swap-device (254:0:484824)
Mar  6 17:27:29 server kernel: [14438.139208] compcache: Error allocating memory for compressed page: 60604, size=4096 


Mar  6 17:27:29 server kernel: [14438.139217] Write-error on swap-device (254:0:484832)
Mar  6 17:27:29 server kernel: [14438.139461] compcache: Error allocating memory for compressed page: 60605, size=4044 
Mar  6 17:27:29 server kernel: [14438.139471] Write-error on swap-device (254:0:484840)


Mar  6 17:27:29 server kernel: [14438.139715] compcache: Error allocating memory for compressed page: 60606, size=4052 
Mar  6 17:27:29 server kernel: [14438.139725] Write-error on swap-device (254:0:484848)
Mar  6 17:27:29 server kernel: [14438.139964] compcache: Error allocating memory for compressed page: 60607, size=4063 


Mar  6 17:27:29 server kernel: [14438.139973] Write-error on swap-device (254:0:484856)
Mar  6 17:27:29 server kernel: [14438.140338] compcache: Error allocating memory for compressed page: 60396, size=2122 
Mar  6 17:27:29 server kernel: [14438.140352] Write-error on swap-device (254:0:483168)


Mar  6 17:27:29 server kernel: [14438.140528] compcache: Error allocating memory for compressed page: 60609, size=2036 
Mar  6 17:27:29 server kernel: [14438.140539] Write-error on swap-device (254:0:484872)
Mar  6 17:27:29 server kernel: [14438.140818] compcache: Error allocating memory for compressed page: 60610, size=4096 


Mar  6 17:27:29 server kernel: [14438.140831] Write-error on swap-device (254:0:484880)
Mar  6 17:27:29 server kernel: [14438.141096] compcache: Error allocating memory for compressed page: 60611, size=4096 
Mar  6 17:27:29 server kernel: [14438.141106] Write-error on swap-device (254:0:484888)


Mar  6 17:27:29 server kernel: [14438.141335] compcache: Error allocating memory for compressed page: 60613, size=4096 
Mar  6 17:27:29 server kernel: [14438.141344] Write-error on swap-device (254:0:484904)
Mar  6 17:27:29 server kernel: [14438.141673] compcache: Error allocating memory for compressed page: 60614, size=4096 


Mar  6 17:27:29 server kernel: [14438.141683] Write-error on swap-device (254:0:484912)
Mar  6 17:27:29 server kernel: [14438.141895] compcache: Error allocating memory for compressed page: 60615, size=40te-error on swap-device (254:0:508392)


Mar  6 17:27:29 server kernel: [14438.577151] compcache: Error allocating memory for compressed page: 63550, size=28 
Mar  6 17:27:29 server kernel: [14438.577156] Write-error on swap-device (254:0:508400)
Mar  6 17:27:29 server kernel: [14438.577246] compcache: Error allocating memory for compressed page: 63551, size=1430 


Mar  6 17:27:29 server kernel: [14438.577252] Write-error on swap-device (254:0:508408)
Mar  6 17:27:29 server kernel: [14438.577850] compcache: Error allocating memory for compressed page: 63292, size=2209 
Mar  6 17:27:29 server kernel: [14438.577861] Write-error on swap-device (254:0:506336)


Mar  6 17:27:29 server kernel: [14438.577928] compcache: Error allocating memory for compressed page: 63293, size=28 
Mar  6 17:27:29 server kernel: [14438.577941] Write-error on swap-device (254:0:506344)
Mar  6 17:27:29 server kernel: [14438.578035] compcache: Error allocating memory for compressed page: 63553, size=28 


Mar  6 17:27:29 server kernel: [14438.578043] Write-error on swap-device (254:0:508424)
Mar  6 17:27:29 server kernel: [14438.578207] compcache: Error allocating memory for compressed page: 63294, size=3969 
Mar  6 17:27:29 server kernel: [14438.578217] Write-error on swap-device (254:0:506352)


Mar  6 17:27:29 server kernel: [14438.578272] compcache: Error allocating memory for compressed page: 63344, size=314 
Mar  6 17:27:29 server kernel: [14438.578282] Write-error on swap-device (254:0:506752)
Mar  6 17:27:29 server kernel: [14438.578337] compcache: Error allocating memory for compressed page: 63383, size=300 


Mar  6 17:27:30 server kernel: [14438.578347] Write-error on swap-device (254:0:507064)
Mar  6 17:27:30 server kernel: [14438.578477] compcache: Error allocating memory for compressed page: 63384, size=2705 
Mar  6 17:27:30 server kernel: [14438.578494] Write-error on swap-device (254:0:507072)


Mar  6 17:27:30 server kernel: [14438.578668] compcache: Error allocating memory for compressed page: 63385, size=4096 
Mar  6 17:27:30 server kernel: [14438.578678] Write-error on swap-device (254:0:507080)
Mar  6 17:27:30 server kernel: [14438.578788] compcache: Error allocating memory for compressed page: 63386, size=2532 


Mar  6 17:27:30 server kernel: [14438.578800] Write-error on swap-device (254:0:507088)
Mar  6 17:27:30 server kernel: [14438.578864] compcache: Error allocating memory for compressed page: 63387, size=607 
Mar  6 17:27:30 server kernel: [14438.578876] Write-error on swap-device (254:0:507096)


Mar  6 17:27:30 server kernel: [14438.578996] compcache: Error allocating memory for compressed page: 63388, size=2047 
Mar  6 17:27:30 server kernel: <mpcache: Error allocating memory for compressed page: 63468, size=1160 


Mar  6 17:27:30 server kernel: [14438.588511] Write-error on swap-device (254:0:507744)
Mar  6 17:27:30 server kernel: [14438.588630] compcache: Error allocating memory for compressed page: 63635, size=1105 
Mar  6 17:27:30 server kernel: [14438.588639] Write-error on swap-device (254:0:509080)


Mar  6 17:27:30 server kernel: [14438.588761] compcache: Error allocating memory for compressed page: 63636, size=1960 
Mar  6 17:27:30 server kernel: [14438.588769] Write-error on swap-device (254:0:509088)
Mar  6 17:27:30 server kernel: [14438.588943] compcache: Error allocating memory for compressed page: 63637, size=1728 


Mar  6 17:27:30 server kernel: [14438.588955] Write-error on swap-device (254:0:509096)
Mar  6 17:27:30 server kernel: [14438.589121] compcache: Error allocating memory for compressed page: 63638, size=2217 
Mar  6 17:27:30 server kernel: [14438.589131] Write-error on swap-device (254:0:509104)


Mar  6 17:27:30 server kernel: [14438.589250] compcache: Error allocating memory for compressed page: 63639, size=1217 
Mar  6 17:27:30 server kernel: [14438.589260] Write-error on swap-device (254:0:509112)
Mar  6 17:27:30 server kernel: [14438.589459] compcache: Error allocating memory for compressed page: 63640, size=1988 


Mar  6 17:27:30 server kernel: [14438.589471] Write-error on swap-device (254:0:509120)
Mar  6 17:27:30 server kernel: [14438.589599] compcache: Error allocating memory for compressed page: 63469, size=2087 
Mar  6 17:27:30 server kernel: [14438.589609] Write-error on swap-device (254:0:507752)


Mar  6 17:27:30 server kernel: [14438.589798] compcache: Error allocating memory for compressed page: 63470, size=4096 
Mar  6 17:27:30 server kernel: [14438.589807] Write-error on swap-device (254:0:507760)
Mar  6 17:27:30 server kernel: [14438.589998] compcache: Error allocating memory for compressed page: 63471, size=4082 


Mar  6 17:27:30 server kernel: [14438.590008] Write-error on swap-device (254:0:507768)
Mar  6 17:27:30 server kernel: [14438.590190] compcache: Error allocating memory for compressed page: 63472, size=4096 
Mar  6 17:27:30 server kernel: [14438.590200] Write-error on swap-device (254:0:507776)


Mar  6 17:27:30 server kernel: [14438.590374] compcache: Error allocating memory for compressed page: 63473, size=4096 
Mar  6 17:27:30 server kernel: [14438.590385] Write-error on swap-device (254:0:507784)
Mar  6 17:27:30 server kernel: [14438.590495] compcache: Error allocating memory for compressed page: 63474, size=2146 


Mar  6 17:27:30 server kernel: [14438.590504] Write-error on swap-device (254:0:507792)
Mar  6 17:27:30 server kernel: [14438.590626] compcache: Error allocating memory for compressed page: 63494, size=2410 
Mar  6 17:27:30 server kernel: [14438.590636] Write-error on swap-device (254:0:507952)


Mar  6 17:27:31 server kernel: [14438.590751] compcache: Error allocating memory for compressed page: 63495, size=2305 
Mar  6 17:27:31 server kernel: [14438.590762] Write-error on swap-device (254:0:507960)
Mar  6 17:27:31 server kernel: [14438.590884] compcache: Error allocating memory for compressed page: 63496, size=1108 


Mar  6 17:27:31 server kernel: [14438.590896] Write-error on swap-device (254:0:50796] compcache: Error allocating memory for compressed page: 63709, size=3699 
Mar  6 17:27:31 server kernel: [14438.597939] Write-error on swap-device (254:0:509672)


Mar  6 17:27:31 server kernel: [14438.598087] compcache: Error allocating memory for compressed page: 63710, size=3670 
Mar  6 17:27:31 server kernel: [14438.598092] Write-error on swap-device (254:0:509680)
Mar  6 17:27:31 server kernel: [14438.598241] compcache: Error allocating memory for compressed page: 63711, size=3694 


Mar  6 17:27:31 server kernel: [14438.598246] Write-error on swap-device (254:0:509688)
Mar  6 17:27:31 server kernel: [14438.598393] compcache: Error allocating memory for compressed page: 63712, size=3656 
Mar  6 17:27:31 server kernel: [14438.598399] Write-error on swap-device (254:0:509696)


Mar  6 17:27:31 server kernel: [14438.598542] compcache: Error allocating memory for compressed page: 63713, size=3647 
Mar  6 17:27:31 server kernel: [14438.598547] Write-error on swap-device (254:0:509704)
Mar  6 17:27:31 server kernel: [14438.598692] compcache: Error allocating memory for compressed page: 63714, size=3681 


Mar  6 17:27:31 server kernel: [14438.598697] Write-error on swap-device (254:0:509712)
Mar  6 17:27:31 server kernel: [14438.598845] compcache: Error allocating memory for compressed page: 63715, size=3614 
Mar  6 17:27:31 server kernel: [14438.598850] Write-error on swap-device (254:0:509720)


Mar  6 17:27:31 server kernel: [14438.598998] compcache: Error allocating memory for compressed page: 63716, size=3724 
Mar  6 17:27:31 server kernel: [14438.599003] Write-error on swap-device (254:0:509728)
Mar  6 17:27:31 server kernel: [14438.599146] compcache: Error allocating memory for compressed page: 63717, size=3642 


Mar  6 17:27:31 server kernel: [14438.599152] Write-error on swap-device (254:0:509736)
Mar  6 17:27:31 server kernel: [14438.599296] compcache: Error allocating memory for compressed page: 63718, size=3621 
Mar  6 17:27:31 server kernel: [14438.599302] Write-error on swap-device (254:0:509744)


Mar  6 17:27:31 server kernel: [14438.599448] compcache: Error allocating memory for compressed page: 63719, size=3594 
Mar  6 17:27:31 server kernel: [14438.599454] Write-error on swap-device (254:0:509752)
Mar  6 17:27:31 server kernel: [14438.599600] compcache: Error allocating memory for compressed page: 63720, size=3568 


Mar  6 17:27:31 server kernel: [14438.599605] Write-error on swap-device (254:0:509760)
Mar  6 17:27:31 server kernel: [14438.599747] compcache: Error allocating memory for compressed page: 63721, size=3558 
Mar  6 17:27:31 server kernel: [14438.599753] Write-error on swap-device (254:0:509768)


Mar  6 17:27:31 server kernel: [14438.599913] compcache: Error allocating memory for compressed page: 63722, size=3572 
Mar  6 17:27:31 server kernel: [14438.599919] Write-error on swap-device (254:0:509776)
Mar  6 17:27:31 server kernel: [14438.600095] compcache: Error allocating memory for compressed page: 63723, size=3523 


Mar  6 17:27:31 server kernel: [14438.600102] Write-error on swap-device (254:0:509784)
Mar  6 17:27:31 server kernel: [14438.600266] compcache: Error allocating memory for compressed page: 63724, size=3486 
Mar  6 17:27:31 server kernel: [14438.600272] Write-error on swap-device (254:0:509792)


Mar  6 17:27:31 server kernel: [14438.600431] compcache: Error allocating memory for compressed page: 63725, size=3509 
Mar  6 17:27:31 server kernel: [14438.600436] Write-error on swap-device (254:0:509800)
Mar  6 17:27:31 server kernel: [14438.600584] compcache: Error allocating memory for compressed page: 63726, size=3380 


Mar  6 17:27:31 server kernel: [14438.600590] Write-error on swap-device (254:0:509808)
Mar  6 17:27:31 server kernel: [14438.600736] compcache: Error allocating memory for compressed page: 63727, size=3398 
Mar  6 17:27:31 server kernel: [14438.600742] Write-error on swap-device (254:0:509816)


Mar  6 17:27:31 server kernel: [14438.600952] compcache: Error allocating memory for compressed page: 63500, size=3448 
Mar  6 17:27:31 server kernel: [14438.600963] Write-error on swap-device (254:0:508000)
Mar  6 17:27:31 server kernel: [14438.601102] compcache: Error allocating memory for compressed page: 63501, size=2553 


Mar  6 17:27:31 server kernel: [14438.601113] Write-error on swap-device (254:0:508008)
Mar  6 17:27:31 server kernel: [14438.601203] compcache: Error allocating memory for compressed page: 63502, size=1845 
Mar  6 17:27:31 server kernel: [14438.601215] Write-error on swap-device (254:0:508016)


Mar  6 17:27:31 server kernel: [14438.601264] compcache: Error allocating memory for compressed page: 63503, size=28 
Mar  6 17:27:31 server kernel: [14438.601273] Write-error on swap-device (254:0:508024)
Mar  6 17:27:31 server kernel: [14438.601379] compcache: Error allocating memory for compressed page: 63504, size=1884 


Mar  6 17:27:31 server kernel: [14438.601390] Write-error on swap-device (254:0:508032)
Mar  6 17:27:31 server kernel: [14438.601510] compcache: Error allocating memory for compressed page: 63506, size=2334 
Mar  6 17:27:31 server kernel: [14438.601520] Write-error on swap-device (254:0:508048)


Mar  6 17:27:31 server kernel: [14438.601626] compcache: Error allocating memory for compressed page: 63507, size=1850 
Mar  6 17:27:31 server kernel: [14438.601636] Write-error on swap-device (254:0:508056)
```


I found this solution, but at the moment Im not sure it resolve the problem

```

https://lists.ubuntu.com/archives/ubuntu-users/2009-February/174065.html

The following little script may be helpfull:

---8<--- swapreset ---8y---
#!/bin/bash
#
#     Filename : swapreset
#      Version : 0.1
#         Date : 07-feb-09
#       Author : email.listen at gmail.com
# Last changed :  07-feb-09
#
#      Options : none-yet
#        Usage : swapreset
#                

## test for compcache
## if yes reset swap and remove compcache and it's child kernel modules
if [ "$(lsmod|grep compcache)"  ] ; then
	## restarting swap, 
	## compcache will _not_ restart
	echo -e "currently aktive swap partitions:"\n
	echo -e "--------------------------------"\n
	sudo swapon -s
	echo -e "will now reset swap partitions"\n
	sudo swapoff -a
	sudo swapon -a
	echo -e "--------------------------------"\n
	echo -e "finally aktive swap partitions:"\n
	sudo swapon -s
	sudo rmmod compcache
	sudo rmmod lzo_decompress
	sudo rmmod lzo_compress
else
	echo -e "no compcache loaded! \nnothing to do so far."
fi

---8<--- swapreset ---8y---

Save this file to a users $HOME/bin/ directory who has sudo privileges.


Make it executable with:

    sudo chmod 700 swapreset

Start it and compcache is disabled.


```

---

### Post by macvr on 2009-05-13
seems that there is a bug .
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/")

to check if this the problem ,run...
```
 sudo swapon -s
```ramzswap is also list along with the regular swap.

on further reading that mailing list>[https://lists.ubuntu.com/archives/ubuntu-users/2009-February/174405.html]("https://lists.ubuntu.com/archives/ubuntu-users/2009-February/174405.html")
> Problem is solved after deleting /usr/share/initramfs-tools/conf.d/compcache 
and a: 

  sudo update-initramfs -u 



rather than reseting the swap, deleting the above compcache file solves the problem...
the compcache seems to be activated at every boot!

after deleting the file ,to check , after reboot
```
 sudo swapon -s
``` this time the swap does not list ramzswap...

---

### Post by solitaire on 2009-05-21
Many thanks for that!!

My laptop has frozen 6 times since 9:04's been released!

Lucky I was in tty1 when it started to freezr and i seen the "compcache" errors flying up the screen!
That's when i notices my cache was 254Mb bigger than i had set.

Quick google and i found this.
Hopefully once the ram swap has been removed my system will be happy! :D

---

### Post by Skip Da Shu on 2009-05-28
> **macvr said:**
> seems that there is a bug .
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/")

to check if this the problem ,run...
```
 sudo swapon -s
```ramzswap is also list along with the regular swap.

on further reading that mailing list>[https://lists.ubuntu.com/archives/ubuntu-users/2009-February/174405.html]("https://lists.ubuntu.com/archives/ubuntu-users/2009-February/174405.html")

rather than reseting the swap, deleting the above compcache file solves the problem...
the compcache seems to be activated at every boot!

after deleting the file ,to check , after reboot
```
 sudo swapon -s
``` this time the swap does not list ramzswap...

Could you tell from "free -m" before and after if it actually freed the RAM?  I assume if you're getting it out of vmlinuz and init.rd that it would.

---

### Post by macvr on 2009-05-29
> **Skip Da Shu said:**
> Could you tell from "free -m" before and after if it actually freed the RAM?  I assume if you're getting it out of vmlinuz and init.rd that it would.

this is my output now... but didnt check before
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1555        456          0        162        636
-/+ buffers/cache:        757       1254
Swap:         3467        320       3146
```

but i'm pretty sure that my swap was not used untill i removed the compcache[ since i used to monitor the swap/memory activity with conky]
even though my swappiness was set to 100 ! it kept trying to write to the ramzswap and since it wasnt able to, my memory was getting bloated...

but after the compcache file was removed, swap is used ... sparing my memory...

---

### Post by Skip Da Shu on 2009-05-29
Thanx much.

---

### Post by EdwardBrown on 2010-03-14
In case you are using non-default kernel or have generic and architecture-specific kernel, e.g. 
```
2.6.30-1-generic and 2.6.30-1-386
```you should run update-initramfs like this:
```
sudo update-initramfs -u -k `uname -r`
``` which updates initramfs image for the kernel you currently running.


If you update image other than current the ramswap is still present in ```
sudo swapon -s
``` output after reboot.

---

