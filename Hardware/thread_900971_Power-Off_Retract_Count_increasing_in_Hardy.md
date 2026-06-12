---
title: "Power-Off_Retract_Count increasing in Hardy"
date: 2008-08-25
forum: Hardware
---

### Post by VerdammtMirFälltNichtsEin on 2008-08-25
Hi,

I have tried to fix the following problem without any success for some time 

[B]Problem description:
[LIST]
[*] *Power-Off_Retract_Count* increases with each shutdown (not with restart)
[*] Windows XP does not cause an increase of *Power- Off_Retract_Count* so it can't be a bios problem.
[/LIST]
[/B]

**System:**
Laptop: Dell Latitude D830 (Bios A13)
Hard drive: Seagate ST9160823AS 
OS: Kubuntu Hardy 8.04 (Kernel 2.6.24)

[B]Questions:
[LIST=1]
[*] Can anyone reproduce the issue?
[*] Is there a bug-fix known (mind comment on older bug-fix by Martin Koßler)?
[/LIST]
[/B]

Any help or comments are appreciated. I have attached a bit of background below to make the post self-contained.
Thanks,
Alex

~~~~~~~~~~~~~~~~~~~~~ **Background:** ~~~~~~~~~~~~~~~~~~~~~
*Power-Off_Retract_Count* counts the number of times the heads are loaded off the hard disk as an *emergency retraction to a power cutoff*. 

In order to find out, if you are affected type 
[LIST]
[*] execute the shell command (requires the 700kb large smartmontools package)
```
 sudo smartctl -A -d ata /dev/sda  | grep Power-Off_Retract_Count 
```
    you should get something like: 
    ```
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       [COLOR="Red"]693 [/COLOR]
```
    the [COLOR="Red"]last number[/COLOR] identifies the number of times the hard drive was not put into parking position before it was powered off 
[*] shutdown the computer (important: a restart won't do it, since the power supply for the hard drive is not switched off)
[*] execute again ```
 smartctl -A -d ata /dev/sda  | grep Power-Off_Retract_Count 
```
[*] if the last number increased by one than your hard used its emergency power off feature
[/LIST]

Powering off the hard drive without putting it in parking position will decrease the lifetime (and might cause data loss).

**Comment on previous fix by [Martin Koßler]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60")** (not working in Hardy):
since the *stop_on_shutdown* interface is not present at kernel 2.6.24 the fix doesn't apply to Ubuntu Hardy (and neither to Kubuntu & Xubuntu)

---

