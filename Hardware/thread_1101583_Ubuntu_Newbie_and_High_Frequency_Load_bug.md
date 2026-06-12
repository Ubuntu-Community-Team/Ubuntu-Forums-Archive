---
title: "Ubuntu Newbie and High Frequency Load bug"
date: 2009-03-20
forum: Hardware
---

### Post by offtheboxuser on 2009-03-20
Hi.I am newbie to Ubuntu which i've just installed on a hp pavillion 9700.
Now,as for this high frequency load cycle issue,My first attempt was to try Ubuntu Intrepid (8.10) because this version was supposed to require less steps in order to get over this problem which as far as i have understood it is only to enable laptop-mode in /etc/default/acpi-support which I already did.Ubuntu now reports being in laptop mode when unplugged from AC.

Now when laptop goes on battery mode, the load cycle still raises on a high rate which i know it's due to
"hdparm -B 128 $dev" in  /etc/acpi/{ac,battery,resume,start}.d/90-hdparm.sh which i learned it's still a bit aggresive with hard disk operation.

Then I proceeded to change it to "hdparm -B 200 $dev" in all those scripts when battery mode is detected and i found i still have high frequency of load/unload operations.

Questions:

Would it be ok to change to "hdparm -B 254 $dev" in battery mode in all 90-hdparm.sh scripts?

Would the above option be the same as to apply the "ugly fix"?

Does the ugly fix implies to disable laptop-mode?

Thank you for your responses,

p.s.: What a mess!.help me please i'm about to reinstall WinXP! :)

---

