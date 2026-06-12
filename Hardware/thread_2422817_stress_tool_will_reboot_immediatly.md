---
title: "stress tool will reboot immediatly"
date: 2019-07-13
forum: Hardware
---

### Post by jms-1 on 2019-07-13
I think this might be some hardware problem but I'm not able to find any hint, perhaps someone knows. When starting the stress tool from the command line (actually the problem comes from some other scenario but I broke it down to this one) like stress -c 1 -t 10 it is executed as expected. stress -c 10 -t 10 will reboot IMMEDIATLY - no chance for overheat or anything. The real issue is with video encoding where indeed overheating may be the problem (around 90°C) but with stress this is definitly not the case.

Here is my hardware (with 18.04):
* Shuttle Barebone DH310
* Intel Core i7 8700 (6 Cores, 12 Threads)
* 32GB DDR4-2666 RAM
* 1TB Crucial MX300 SSD

I did some research on google but these came out unclear (to me!). It seems as if there may be a problem in the combination of (Shuttle, i7, Ubuntu).

Any tips?

Thanks in advance

Jochen

---

### Post by CatKiller on 2019-07-13
Instability under load that isn't thermal is generally power.

---

### Post by jms-1 on 2020-05-05
Although this is quite old I would like to give an update just FYI: I switched the 90W power supply to a 120W part and at least with stress it looks as good as it should. I suspect it's a power consumption peak when the system quickly goes under full load.

---

### Post by jms-1 on 2020-05-08
"Funny" stuff: yes, this DID resolve the stress problem but the spontanous shutdown still happens during normal operation! According to the Shuttle support the specific version of my DH310 misses a "RAM update" which may show the described symptoms with some type of DDR4 modules. Currently I'm testing my options to get over this.

---

### Post by VMC on 2020-05-08
Does the output of "sensors" show any thermal issues. I have a similar issue but could never locate the problem. I do know using SSD's it occures. If I use hard drives, I never have issues.

---

### Post by jms-1 on 2020-05-10
No, there are no thermal indicators (happens even far below 60°C). I'll try to replace the RAM modules tomorrow as suggested by the Shuttle support. We'll see what happens :-(

---

### Post by VMC on 2020-05-10
I ran your stress test, mine didn't fail, but it fails on its own. No indication. All thermal within range. Mine might be my power supply. I'm very interested in your findings.

---

### Post by jms-1 on 2020-05-11
:-) Using the RAM recommended by the Shuttle Support did change NOTHING - still crashing.

---

### Post by jms-1 on 2020-05-18
Interim: not really a solution but currently I need the system to be stable: I switched off "Turbo Boost" in the BIOS and had no unwanted reboot for a couple of days. stress no longer crashes the system - not really an information since I'm using the 120W power supply but in a short test the original 90W part now allows stress to run as well. So for single threaded applications I stuck to the 3.2GHz of my i7 instead of 4.6GHz, but but in most cases this is not an issuem - at least for me.

---

### Post by jms-1 on 2020-05-25
Currently it seems as if the Turbo Mode of the i7 8700 is responsible. What's your hardware?

---

### Post by VMC on 2020-05-25
Mines simple:
Intel i5 8th gen.
Intel Corporation UHD Graphics 630

---

### Post by jms-1 on 2020-05-30
Shuttle found that indeed the Turbo Mode of the i7 8700 may go well beyond the 90W provided by the power supply (they have measured around 120W). The last statement is that they will provide a BIOS fix which will allow normal operation with the stock power supply. Let's hope for the best... 

But overall: the effect seems to be due to the self protection inside the power supply and the behavior of the CPU when all cores are fired up in a very short time frame. In my experience this may happen at any time depending on what you do.

Did you try to switch the Turbo Mode off in the BIOS?

---

### Post by VMC on 2020-05-30
Didn't even consider Turbo Mode. I have to look. I think mine might be power supply issue also.

---

### Post by jms-1 on 2020-06-02
Shuttle provided me with a preliminary BIOS (which I guess will become 1.10 someday). First tests look good (90W stock power supply, active turbo mode, stress tool) but I think I'll observe 'til end of this week before I myself as well feel good with the fix :-)

---

### Post by VMC on 2020-06-02
I don't have turbo-boost in my bios. I did find that the power supply is most likely the culprit.

---

### Post by jms-1 on 2020-06-02
Do you have a Shuttle Barebone? If so which with what BIOS version - maybe the BIOS is too old. Does the i5-8xxx support turbo at all (I think so but I'm not sure). My setting is somewhere under CPU features.

---

### Post by VMC on 2020-06-02
I have Acer desktop.

---

