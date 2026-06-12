---
title: "ssd - disk error, fixed by fsck, now what?..."
date: 2021-10-28
forum: Hardware
---

### Post by marchello_lippi2 on 2021-10-28
Hi all, I got disk error on my 5 years old ssd. 

Found this advise and it helped: [https://askubuntu.com/a/1191343](https://askubuntu.com/a/1191343)
> 
[COLOR=#373737][FONT=Verdana]*For 18.04 or newer... you MUST do it this way...*[/FONT][/COLOR]
[COLOR=#373737][FONT=Verdana][I]    boot to a Ubuntu Live DVD/USB
    open a terminal window by pressing Ctrl+Alt+T
    type sudo fdisk -l
    identify the /dev/sdXX device name for your "Linux Filesystem"
    type sudo fsck -f /dev/sdXX, replacing sdXX with the number you found earlier
    repeat the fsck command if there were errors
    type reboot[/I][/FONT][/COLOR]


How do I check my disk health in general? Would it be the best way to ask service guys about changing SSD ASAP? Actually this is my secondary notebook and I use it rarely, but it would be shame to take it out of city and see it died when it's needed.
Need your opinion. Thanks.

---

### Post by TheFu on 2021-10-28
SMART data is part of all storage used by the Govt - so all the name-brand ones provide it.  Use smartctl to run tests, wait for the tests to complete, then use smartctl to request a report.  There may be a BIOS setting that has to be enabled to allow access to SMART data. This can be automated to happen as often as you like.  However, any SSD that is 5 yrs old, I'd have really good backups to protect anything I don't want to lose.  In the SMART data, there should be around 200 things. You can look up what each means for the specific model involved.  Some are pseudo-standard, but if you see funny data for any raw value, that's worth looking up to understand exactly what it means.  

You can search these forums for **smartctl** commands.

It should be noted that storage can fail even when all the SMART data doesn't say it is failing.  Some huge cloudy storage providers with hundreds of thousands of storage units does statistical sampling and posts their results online.  If my memory is correct, about 22% of drive failures happen without any hints first.  OTOH, 78% do provide hints.

I've had 2 SSDs die ... both after 2-3 yrs.  At first, they became read-only, but a reboot + fsck could get them back into read-write mode.  About a month later, they became read-only and a few days later - no access to any data on the devices was possible.  There were some fields in the SMART data that told me the SSD was failing.  I was lucky.  Most people I know with dead SSDs had the storage just stop working. No warnings. They weren't monitoring any SMART data, however, so I don't know their personal experiences with SMART warnings.

---

### Post by rsteinmetz70112 on 2021-10-29
I had an SDD less than 2 years old simply stop working, no prior indication and nothing in the SMART data that looked hinkly before it failed.
A filesystem issues resolved by fsck may not mean anything about health of the disk. They are usually caused by an improper shutdown or some other software issue. 
Running smartctl will help but as TheFU says it cannot rule out an imminent failure. I'd make sure I had good backups and think about changing out the drive, replacing a 5 year old SDD should be relatively cheap.

---

