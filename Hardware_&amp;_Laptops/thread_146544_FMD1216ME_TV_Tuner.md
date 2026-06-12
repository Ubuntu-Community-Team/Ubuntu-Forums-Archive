---
title: "FMD1216ME TV Tuner"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by peppermint on 2006-03-18
Hi, I'm trying to get my tv tuner card working in 5.10. It says “FMD1216ME” on the card. Googling this, I found out the card is a Philips FMD1216ME MK3 Hybrid Tuner. I've been following a guide I found in the Ubuntu wiki ([http://hyams.webhop.net/mythtv/myth_ubuntu.html)](http://hyams.webhop.net/mythtv/myth_ubuntu.html)). I started having trouble with the instruction just above section 5.3. Im writing this sometime after doing this command for the first fime. but i think dmesg is giving me a different output.

This is the output of dmesg...
```

 ATAPI device hdb:
[4295605.265000]   Error: Not ready -- (Sense key=0x02)
[4295605.265000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295605.265000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295605.265000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295607.289000] ATAPI device hdb:
[4295607.289000]   Error: Not ready -- (Sense key=0x02)
[4295607.289000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295607.289000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295607.289000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295609.313000] ATAPI device hdb:
[4295609.313000]   Error: Not ready -- (Sense key=0x02)
[4295609.313000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295609.313000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295609.313000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295611.337000] ATAPI device hdb:
[4295611.337000]   Error: Not ready -- (Sense key=0x02)
[4295611.337000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295611.337000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295611.337000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295613.361000] ATAPI device hdb:
[4295613.361000]   Error: Not ready -- (Sense key=0x02)
[4295613.361000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295613.361000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295613.361000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295615.385000] ATAPI device hdb:
[4295615.385000]   Error: Not ready -- (Sense key=0x02)
[4295615.385000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295615.385000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295615.385000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295617.409000] ATAPI device hdb:
[4295617.409000]   Error: Not ready -- (Sense key=0x02)
[4295617.409000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295617.409000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295617.409000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295619.433000] ATAPI device hdb:
[4295619.433000]   Error: Not ready -- (Sense key=0x02)
[4295619.433000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295619.433000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295619.433000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295621.457000] ATAPI device hdb:
[4295621.457000]   Error: Not ready -- (Sense key=0x02)
[4295621.457000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295621.457000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295621.457000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295623.481000] ATAPI device hdb:
[4295623.481000]   Error: Not ready -- (Sense key=0x02)
[4295623.481000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295623.481000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295623.481000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295625.505000] ATAPI device hdb:
[4295625.505000]   Error: Not ready -- (Sense key=0x02)
[4295625.505000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295625.505000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295625.505000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295627.535000] ATAPI device hdb:
[4295627.535000]   Error: Not ready -- (Sense key=0x02)
[4295627.535000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295627.535000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295627.535000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295629.559000] ATAPI device hdb:
[4295629.559000]   Error: Not ready -- (Sense key=0x02)
[4295629.559000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295629.559000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295629.559000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295631.583000] ATAPI device hdb:
[4295631.583000]   Error: Not ready -- (Sense key=0x02)
[4295631.583000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295631.583000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295631.583000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295633.607000] ATAPI device hdb:
[4295633.607000]   Error: Not ready -- (Sense key=0x02)
[4295633.607000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295633.607000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295633.607000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295635.631000] ATAPI device hdb:
[4295635.631000]   Error: Not ready -- (Sense key=0x02)
[4295635.631000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295635.631000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295635.631000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295637.803000] ATAPI device hdb:
[4295637.803000]   Error: Not ready -- (Sense key=0x02)
[4295637.803000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295637.803000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295637.803000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295639.827000] ATAPI device hdb:
[4295639.827000]   Error: Not ready -- (Sense key=0x02)
[4295639.827000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295639.827000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295639.827000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295641.851000] ATAPI device hdb:
[4295641.851000]   Error: Not ready -- (Sense key=0x02)
[4295641.851000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295641.851000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295641.851000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295643.875000] ATAPI device hdb:
[4295643.875000]   Error: Not ready -- (Sense key=0x02)
[4295643.875000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295643.875000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295643.875000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295645.899000] ATAPI device hdb:
[4295645.899000]   Error: Not ready -- (Sense key=0x02)
[4295645.899000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295645.899000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295645.899000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295647.923000] ATAPI device hdb:
[4295647.923000]   Error: Not ready -- (Sense key=0x02)
[4295647.923000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295647.923000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295647.923000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295649.947000] ATAPI device hdb:
[4295649.947000]   Error: Not ready -- (Sense key=0x02)
[4295649.947000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295649.947000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295649.947000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295651.971000] ATAPI device hdb:
[4295651.971000]   Error: Not ready -- (Sense key=0x02)
[4295651.971000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295651.971000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295651.971000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295653.995000] ATAPI device hdb:
[4295653.995000]   Error: Not ready -- (Sense key=0x02)
[4295653.995000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295653.995000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295653.995000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295656.019000] ATAPI device hdb:
[4295656.019000]   Error: Not ready -- (Sense key=0x02)
[4295656.019000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295656.019000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295656.019000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295658.043000] ATAPI device hdb:
[4295658.043000]   Error: Not ready -- (Sense key=0x02)
[4295658.043000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295658.043000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295658.043000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295660.067000] ATAPI device hdb:
[4295660.067000]   Error: Not ready -- (Sense key=0x02)
[4295660.067000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295660.067000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295660.067000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295662.091000] ATAPI device hdb:
[4295662.091000]   Error: Not ready -- (Sense key=0x02)
[4295662.091000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295662.091000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295662.091000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295664.116000] ATAPI device hdb:
[4295664.116000]   Error: Not ready -- (Sense key=0x02)
[4295664.116000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295664.116000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295664.116000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295666.140000] ATAPI device hdb:
[4295666.140000]   Error: Not ready -- (Sense key=0x02)
[4295666.140000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295666.140000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295666.140000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295668.164000] ATAPI device hdb:
[4295668.164000]   Error: Not ready -- (Sense key=0x02)
[4295668.164000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295668.164000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295668.164000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295670.188000] ATAPI device hdb:
[4295670.188000]   Error: Not ready -- (Sense key=0x02)
[4295670.188000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295670.188000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295670.188000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295672.212000] ATAPI device hdb:
[4295672.212000]   Error: Not ready -- (Sense key=0x02)
[4295672.212000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295672.212000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295672.212000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295674.236000] ATAPI device hdb:
[4295674.236000]   Error: Not ready -- (Sense key=0x02)
[4295674.236000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295674.236000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295674.236000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295676.260000] ATAPI device hdb:
[4295676.260000]   Error: Not ready -- (Sense key=0x02)
[4295676.260000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295676.260000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295676.260000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295678.284000] ATAPI device hdb:
[4295678.284000]   Error: Not ready -- (Sense key=0x02)
[4295678.284000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295678.284000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295678.284000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295680.308000] ATAPI device hdb:
[4295680.308000]   Error: Not ready -- (Sense key=0x02)
[4295680.308000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295680.308000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295680.308000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295682.332000] ATAPI device hdb:
[4295682.332000]   Error: Not ready -- (Sense key=0x02)
[4295682.332000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295682.332000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295682.332000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295684.371000] ATAPI device hdb:
[4295684.371000]   Error: Not ready -- (Sense key=0x02)
[4295684.371000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295684.371000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295684.371000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295686.514000] ATAPI device hdb:
[4295686.514000]   Error: Not ready -- (Sense key=0x02)
[4295686.514000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295686.514000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295686.514000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295688.538000] ATAPI device hdb:
[4295688.538000]   Error: Not ready -- (Sense key=0x02)
[4295688.538000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295688.538000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295688.538000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295690.562000] ATAPI device hdb:
[4295690.562000]   Error: Not ready -- (Sense key=0x02)
[4295690.562000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295690.562000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295690.562000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295692.586000] ATAPI device hdb:
[4295692.586000]   Error: Not ready -- (Sense key=0x02)
[4295692.586000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295692.586000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295692.586000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295694.610000] ATAPI device hdb:
[4295694.610000]   Error: Not ready -- (Sense key=0x02)
[4295694.610000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295694.610000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295694.610000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295696.634000] ATAPI device hdb:
[4295696.634000]   Error: Not ready -- (Sense key=0x02)
[4295696.634000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295696.634000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295696.634000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295698.658000] ATAPI device hdb:
[4295698.658000]   Error: Not ready -- (Sense key=0x02)
[4295698.658000]   No reference position found (media may be upside down) -- (as c=0x06, ascq=0x00)
[4295698.658000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295698.658000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

```

How do i get to a possition where i can proceed with the guide?

---

### Post by CameronCalver on 2006-03-30
hey i would like a tv tuner how much did that cost

---

### Post by Michael Matthews on 2006-03-30
Has nothing to do with your tv card. These are cd/dvd error messages. Don't know what is generating this. Some startup software is trying to do something to your cd drive.

---

