---
title: "Cannon LBP 2900  installaton Problem"
date: 2011-11-12
forum: Hardware
---

### Post by Vishnu V on 2011-11-12
hi
When i tried to install Canon LBP2900 on Ubuntu 11.10, (As instruction from [https://help.ubuntu.com/community/CanonCaptDrv190]("https://help.ubuntu.com/community/CanonCaptDrv190")). I got an error for the following command
```

sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 -E

```
and the error is
```

lpadmin: Bad device-uri scheme "ccp"

```


Please Help 

Thanks 
Vishnu V

---

### Post by krishnan t s k on 2011-12-23
I think you must be using 64-bit ubuntu as i am and have same problem i had...the good news is, you can get your current problem solved through the link i'm posting below but the bad news is beyond that, if you are using a 64-bit ubuntu, your printer will probably not work and you will have to depend on windows to print your documents and files
 [http://kgrz.posterous.com/canon-lbp2900-on-ubuntu-1110-64-bit-installat](http://kgrz.posterous.com/canon-lbp2900-on-ubuntu-1110-64-bit-installat)
wish you all the best :) :)

---

### Post by giruzz on 2012-01-18
> **krishnan t s k said:**
> I think you must be using 64-bit ubuntu as i am and have same problem i had...the good news is, you can get your current problem solved through the link i'm posting below but the bad news is beyond that, if you are using a 64-bit ubuntu, your printer will probably not work and you will have to depend on windows to print your documents and files
 [http://kgrz.posterous.com/canon-lbp2900-on-ubuntu-1110-64-bit-installat](http://kgrz.posterous.com/canon-lbp2900-on-ubuntu-1110-64-bit-installat)
wish you all the best :) :)

Not sure if it helps but Canon published V2.40 of their drivers.

You can find it here
[http://www.canon.co.uk/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP2900B.aspx?DLtcmuri=tcm:14-846492&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP2900B.aspx?DLtcmuri=tcm:14-846492&page=1&type=download)

g.

---

### Post by Vishnu V on 2012-02-03
I do many tries for installing the printer 
update my system.
Trying to change ccpd etc
I found the bad sevice uri error is removed by creating some soft links
(got from [http://forums.opensuse.org/hardware/406919-canon-lbp-2900-a.html]("http://forums.opensuse.org/hardware/406919-canon-lbp-2900-a.html"))
```

/usr/lib64/cups/backend/ccp -> /usr/lib/cups/backend/ccp
/usr/lib64/cups/filter/pstocapt -> /usr/lib/cups/filter/pstocapt
/usr/lib64/cups/filter/pstocapt2 -> /usr/lib/cups/filter/pstocapt2
/usr/lib64/cups/filter/pstocapt3 -> /usr/lib/cups/filter/pstocapt3 

```
Even though this not solved my problem.
After some days 

Then i tried to reinstall my printer  and now my printer is working 
(I think updates solved my problem)

Thank You Very much :D

---

