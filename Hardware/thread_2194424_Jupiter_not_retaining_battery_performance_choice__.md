---
title: "Jupiter not retaining battery performance choice / Ubuntu 12.04.3 / HP6910P"
date: 2013-12-18
forum: Hardware
---

### Post by Scotsilv on 2013-12-18
Wanted simple no hassle battery life extension in HP6910P, where a brand new extended 9 cell battery is giving less than 2 hrs with wireless off and screen brightness all the way down.

Installed Jupiter with 12.04.3 with all current upgrades and 3.8.0-34-generic #49~precise1.  It seems to work - but - 

Jupiter will not retain state when switiching between battery and AC.  

1.  When on AC, the default is "power on demand"  
2.  If I then unplug and am on battery the  default is also "power on demand"  
3.  On battery if I select "power saving", that seems to work.  Mode is indicated in popup and in menu as CPU Mode: "Power saving."
4.  When I plug in again to AC, mode reverts from "power saving" to "power on demand". 
5.  Problem is, if I then unplug and am on battery again, instead of remembering my "power saving" choice, the mode stays at "power on demand."

Any ideas?  I don't want to use anything more complex that Jupiter, and I am sticking to 12.04.3 LTS.


-------------------

Note:

I installed a fix seen online at [http://askubuntu.com/questions/141921/jupiter-applet-default-setting;](http://askubuntu.com/questions/141921/jupiter-applet-default-setting;)
[I]
modify the line AC_DEVICE=$(ls /sys/class/power_supply | grep "ADP\|AC") 
replace ADP\|AC with the return of the command ls /sys/class/power_supply/[/I]

Which in my case became  grep "C1E7"

-------------------

---

