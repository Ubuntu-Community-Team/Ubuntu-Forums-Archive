---
title: "new battery doesn't charge!"
date: 2010-02-26
forum: Hardware
---

### Post by partofthething on 2010-02-26
I just got a new battery in the mail, but it's not charging in Ubuntu 9.10. 

For 5 minutes, things look good: 
```
$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1 mA
remaining capacity:      1130 mAh
present voltage:         12226 mV

```Then:

```
$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1 mA
remaining capacity:      1126 mAh
present voltage:         12200 mV
```But the capacity is 7200 mAh! Why is it going at 1 mA? Defective battery? 

Some background, this is a Dell 1505 from 2007 or so. The first battery died long ago and I got a new one. The second battery must have overheated or something because it got all warped and crazy looking (it was cheap). So if I ran for 20 minutes on battery, the computer would just shut off with no warning as the battery contacts became disconnected. So I got this third battery for $60 or so, and now this! 

So is it my laptop, or the battery? I tried the whole conditioning thing where I let the laptop run down to zero and then charge it. But it's not charging. ahh. 

Oh, but if I let it discharge for a few seconds and then plug it back in, I can get a few more mAh into it as the present rate increases back to full speed for a good 2 minutes. Should I just continue stair-stepping?

Thanks in advance for any advice/insight.

---

### Post by ajslay on 2010-02-26
hi, you might wanna theck the contacts to the battery on your laptop, they could be dirty or something? just a suggestion. i had a problem with a old dell latitude d600 and nothing would work to fix it until i bought an official dell OEM battery. then everything worked.. your battery might be defective or it might even be your ac adapter

---

