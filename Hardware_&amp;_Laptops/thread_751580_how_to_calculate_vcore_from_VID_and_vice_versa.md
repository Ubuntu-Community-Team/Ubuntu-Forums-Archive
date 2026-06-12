---
title: "how to calculate vcore from VID and vice versa"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by GordonFreeman on 2008-04-10
Hello everybody, 

after several hours of experimenting with phc and undervolting with it, I wanted to try the PHCtool because it can display voltages and not only the VIDs. But after starting it it says, that it does not support my T9300 and therefore can't display the voltage value(s). 

My problem is that the default VIDs are 41 34 30 27 23 19 (which are displayed in PHCtool and the phc_vids file), but I don't know how to translate these VIDs into voltages. At first I thought that they're just a decimal representation of the binary values in the VID table from the Intel manual but then 19 would correspond to 1,2625V and 41 to 0,98725V which is kind of meaningful, if not for the fact that 41 stands for the VID of the full speed state and 19 for the low speed state. 

I know stable vcores for every multiplicator setting, but I don't know how to apply them because I don't know how to translate them into VIDs, 

Does anybody of you know how to translate them? 


Thanks.

---

