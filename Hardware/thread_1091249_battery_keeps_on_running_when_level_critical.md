---
title: "battery keeps on running when level critical"
date: 2009-03-09
forum: Hardware
---

### Post by toffifeemann on 2009-03-09
hello everyone,
im fairly new to ubuntu and this forum so im hoping i can provide all the info u need, i have just bought a ibm t40, it was used but the seller promised me a battery runtime of around 4 hours, now i knew that it might be less in ubuntu but this is very strange...
here's my info
present:                 yes
design capacity:         71280 mWh
last full capacity:      16220 mWh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 811 mWh
design capacity low:     200 mWh
capacity granularity 1:  1 mWh
capacity granularity 2:  1 mWh
model number:            IBM-93P5003
serial number:            2237
battery type:            LION
OEM info:                SONY
now i dont want to believe that my battery is that much down the hill already, since it runs with gnome-powermanager smoothly for about 1,5hrs then it starts beeping and tells me that the battery is critical, as the laptop calms down again it keeps running smoothly for another hour or so, telling me that the battery is critical
now im wondering how i can make the powermanager understand how long my battery realy lasts
any suggestions, keep in mind that im a noob 
thanks already

---

### Post by toffifeemann on 2009-03-09
oh also when it's charging, it stays at 98 or 98.5% for about 30 minutes before setting it on 100

---

### Post by KuriKai on 2009-03-09
I have the same problem with my laptop dell latitude c400

---

### Post by mrufino1 on 2009-03-09
Hi, Got your PM, I just figured I'd make it public so others can benefit too- try discharging the battery all the way then charge to 100% with the computer powered down- that helped me, I think I may have let it discharge all the way again after charging it to 100%. I think the power manager has to "guess" at how the battery is working based on the info it gets, this seems to recalibrate it. If there is a correct technical explanation from someone, please offer it, as mine was not! I do know I had this problem on my t41 and then it did not happen again after I did this. I think an update at the time caused it to freak out. I do get the reported run time and charge now. I had forgotten about this until I got the PM, so thanks for alerting people again.

---

### Post by toffifeemann on 2009-03-18
well this comes a bit late since my laptop was in repair for something else...
thanks for the comment mrufino but it didnt help me,
so any other ideas how to make ubuntu 8.10 reestimate the battery runtime?
would be quite cool to know how much longer to expect...

---

