---
title: "Can I buy a wifi card that works with ubuntu for my sony viao laptop"
date: 2013-11-27
forum: Hardware
---

### Post by 2 legit 2 quit on 2013-11-27
Hello,

I have a sony viao vgn fz345d laptop that uses a intel pro/wireless 4965 agn wifi card. My wifi connection is always dropping and I have tried to fix it but no success. I am wondering if anybody knows if I can install a newer wifi card that will work on my laptop that is good for using with ubuntu 12.04 as the os? I called sony but they said the one that is installed is the only one they recommend but I want to know if its possible to install a different wifi card.
Thanks

---

### Post by Bashing-om on 2013-11-28
2 legit 2 quit; Hi !
Sure it is possible ! .. Opening up some lap tops though is not for the average person.
Have a look here at the certification catalog:
[http://www.ubuntu.com/certification/catalog/](http://www.ubuntu.com/certification/catalog/)
for a listing of known hardware to work well in ubuntu.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by 2 legit 2 quit on 2013-11-28
Thanks Bashing-om. I have already opened mine and am comfortable with changing the WiFi card.

---

### Post by Bashing-om on 2013-11-29
2 legit 2 quit;
As you are mechanically inclined, you are 3/4's of the way there.
Did the catalog suffice to answer your need ?

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2013-11-29
This YouTube link might help: [http://www.youtube.com/watch?v=YbHBx8P_ruI]("http://www.youtube.com/watch?v=YbHBx8P_ruI")

---

### Post by 2 legit 2 quit on 2014-03-22
i bought this wifi card: Intel Corporation Wireless 7260 (rev 73)

I am still getting dropped wifi. When i run the dmesg command i get this output:

```

[  527.491179] cfg80211: Calling CRDA for country: CA
[  527.496053] cfg80211: Regulatory domain changed to country: CA
[  527.496058] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  527.496061] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  527.496063] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  527.496066] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  527.496068] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  527.496071] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)

```

Is this related to why my wifi always dropping?

---

