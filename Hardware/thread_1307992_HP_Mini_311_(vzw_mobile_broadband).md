---
title: "HP Mini 311 (vzw mobile broadband)"
date: 2009-10-31
forum: Hardware
---

### Post by unsungboxer on 2009-10-31
I am trying to get my built in Gobi chip to work (vzw cdma + GSM) with the fresh install of ubuntu 9.10.   
This netbook has only been available for about a week with broadband built in, so I am unable to find much support.

It contains:  
HP un2400 mobile broadband module. (and is already activated/working under the windows 7 partition)

I have done:  
network manager > edit connections > mobile broadband > Add > Verizon

```
Connect automatically: check
Number: #777
username: [email]my_10_digit_mtn@vzw3g.com[/email]
password: vzw
```

Result:  
Nothing happens

Open up terminal, and:
 ```
route -n
```

No route is detected.

Read through this thread with no luck.: 
[http://art.ubuntuforums.org/showthread.php?p=8185674]("http://art.ubuntuforums.org/showthread.php?p=8185674")

Any help is greatly appreciated. Thank you.
-unsung

---

### Post by heyshadylady on 2009-11-04
I would like to bump this, having the same issue with HP Mini 1151nr - verizon 3g broadband card included.

---

### Post by unsungboxer on 2009-11-07
I had luck here: [http://ubuntuforums.org/showthread.php?t=1008200&page=10](http://ubuntuforums.org/showthread.php?t=1008200&page=10)
Post #93

---

