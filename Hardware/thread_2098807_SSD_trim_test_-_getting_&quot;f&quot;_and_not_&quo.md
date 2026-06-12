---
title: "SSD trim test - getting &quot;f&quot; and not &quot;0&quot;"
date: 2012-12-27
forum: Hardware
---

### Post by Ventiti on 2012-12-27
Good evening everybody.

I have a SSD and I followed this test ([http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2/](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2/)) to discover if trim is enabled. But I did not get "0" at the end but "f". Could someone, please, enlighten me? 


Here:

reading sector 119807832: succeeded
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff


Thank you for your help.

---

### Post by dabl on 2012-12-27
Not sure about that test, but if you can find #5 down this long page, I have used that test and confirmed the expected result on 3 SSD's:

[http://siduction.org/index.php?module=news&func=display&sid=78&lang=en](http://siduction.org/index.php?module=news&func=display&sid=78&lang=en)

---

### Post by linrunner on 2012-12-27
Hi,

does it really matter if there are 0's or f's? The sector's previous contents has been purged and therefore it is TRIMmed now.

Could you show us:
```
sudo hdparm -I /dev/sda | grep TRIM
```

---

### Post by Ventiti on 2012-12-27
Thank you all for your answers.

Concerning your first question: I don't really know :)


I get this output:

*    Data Set Management TRIM supported (limit 16 blocks)

---

