---
title: "Load_Cycle_Count problem with 9.10"
date: 2009-11-06
forum: Hardware
---

### Post by Bjalf on 2009-11-06
So, I installed 9.10 on my Aopen 1557 laptop.

I used the alternate CD, and installed CLI only. So far, so good. Well, except that it insisted on using the second monitor for the install. Even when I yanked the cable to the second monitor before boot.

Anyway, after installing *pm-utils* and *smartmontools* I see that "sudo smartctl -a /dev/sda | grep Load_Cycle_Count" returns a rapidly increasing **Load_Cycle_Count** value. What a pleasant surprise! I thought that this crap was fixed by now?

So I installed the [Unofficial Ugly Load_Cycle_Count Fix for Hardy (and later Ubuntu versions)]("http://ubuntuforums.org/showthread.php?p=5031047#post5031047") , and suddenly ... nothing happened. Load_Cycle_Count still increasing like there's no tomorrow. How nice. This fix worked on the previous 8.04 full install. Why is it not working on 9.10 CLI install?

What's more, every 5-10 seconds the computer hangs while running *smartctl*, and then spews some crap about "Exeption Emask yadda yadda yadda". ](*,)   I don't care! Shut up and just work!

Now, see, this is why I'm still using windoze for my 10+ PC's after dabbling in Linux since **Red Hat 5.1** (1998 ). I really, really want to dump windoze and convert to ubuntu. But I can't, because it **just doesn't work**. Every darned time I install ubuntu (or any other variant of linux), I am disappointed.

I hate windows. But it works ...   :mad:

---

### Post by s3MA00RRNY on 2009-11-06
Add the following line to /etc/rc.local:

```
hdparm -S 120 -B 128 /dev/sda
```

That may or may not help you. I actually never had a Load Cycle problem, but I put that in "just in case."

---

### Post by s3MA00RRNY on 2009-11-06
This problem is the fault of the hardware manufacturers, not the OS. Windows, though, is aware of this poor design and hacks around it automatically. Ubuntu doesn't because the problem should not exist. But it does and it's annoying that no one has got around to fixing it.

---

### Post by robert321 on 2009-11-06
I had exactly the same problem. I think the old scripts ain't working anymore because Upstart is playing a big role now in Ubuntu. Which is event based.

So I started to search for the event and the solution:

[LIST]
[*]I found the event battery which call the script [FONT=Courier New]battery.sh[/FONT] in [FONT=Courier New]/etc/acpi/[/FONT]
[*]The script call the program pm-powersave.
[*]The man page told me that pm-powersave will execute the scripts inside: /[FONT=Courier New]usr/lib/pm-utils/power.d/[/FONT]
[*]The script [FONT=Courier New]95hdparm-apm[/FONT] looked promising.
[*]Inside the script hdparm is executed: [FONT=Courier New]hdparm -B $level $dev[/FONT]
[*]The level is however not configured in the script itself, but in a separate hdparm functions file.
[*]These functions can be found at: [FONT=Courier New]/usr/lib/pm-utils/hdparm-functions[/FONT]
[*]At the end of the file you can change the default -B values. One with the power cord attached and one without. Default they are 254 and 128. So i changed 128 to 200.
[/LIST]
**[FONT=Courier New]/usr/lib/pm-utils/hdparm-functions[/FONT]**
```

            if hdparm_is_on_battery; then
                OPTION="200"
            else
                OPTION="254"
            fi
```It works!.. When you plug and unplug the power cord you can monitor with the command[FONT=Courier New] hdparm -B /dev/sda[/FONT] to see that the APM value indeed changes. I also did a suspend and the value was still at 200. Of course I also checked the load_cycle count value and it kept stable.

I still have to do a cold boot without the power cord attached to see if that also works (I'm going to do that now)

**Update: The cold boot also gave me a positive result :D**. I also find this solution much more clean than the scripts you had to "install"

---

### Post by Bjalf on 2009-11-07
> **robert321 said:**
> **Update: The cold boot also gave me a positive result :D**. I also find this solution much more clean than the scripts you had to "install"
Well, it was an "ugly fix", indeed  :-)

Anyway, after sleeping on it, it is halfway solved. The alternate CLI install does indeed increase the **Load_Cycle_Count** value like mad. But after looking for [FONT=Courier New]/etc/acpi/[/FONT] and not finding it, the solution turned out to be quite simple: just install *acpi-support*.
```
sudo aptitude install --without-recommends acpi-support smartmontools
```That froze the **Load_Cycle_Count** value.

So, if you install an alternate CLI only on a system with laptop hard disks, install *acpi-support* right away.


My other disk/hang problem is unsolved, rendering the 9.10 system unusable for now. Now to google for "HSM violation"  (sigh)

I need a drink ...

---

### Post by d11 on 2009-11-23
Thanks Robert I was a little worry about this problem.
any solution worked for me until now.

this is the best solution.  I am very glad.

---

### Post by benma on 2009-11-27
How about Dell inspiron 11z (dual core)?
is there such a problem (harddrive Load_Cycle_Count issue)?
the HD there is Seagate st9320325as, here's a link:

[http://www.seagate.com/ww/v/index.jsp?name=st9320325as-momentus-5400.6-sata-3gb-320gb-hd&vgnextoid=31a9e0f933140210VgnVCM1000001a48090aRCRD&locale=en-US](http://www.seagate.com/ww/v/index.jsp?name=st9320325as-momentus-5400.6-sata-3gb-320gb-hd&vgnextoid=31a9e0f933140210VgnVCM1000001a48090aRCRD&locale=en-US)

---

### Post by amokoura on 2009-12-02
> **robert321 said:**
> 
**[FONT=Courier New]/usr/lib/pm-utils/hdparm-functions[/FONT]**```

            if hdparm_is_on_battery; then
                OPTION="200"
            else
                OPTION="254"
            fi
```
It works for me too, thank you very much!

I have a Samsung NC10. Every time the hard disk parked, it had a clicking sound. It happened so often that it got annoying.

---

### Post by nonperson on 2009-12-16
> **amokoura said:**
> 
I have a Samsung NC10. Every time the hard disk parked, it had a clicking sound. It happened so often that it got annoying.

Thank heavens a fellow NC10 owner has found something that works.

It has been driving me batty. The only way I could get it stop was to follow this [suggestion.]("http://ubuntuforums.org/showpost.php?p=8269392&postcount=326")

BTW it didn't work for Mint 8. I don't know if I can be bothered to re-install Mint just to see if this fix works.

I am sorry forum experts but I am not convinced that this is an entirely hardware problem.

---

### Post by acascianelli on 2010-01-06
> **robert321 said:**
> ...
**[FONT=Courier New]/usr/lib/pm-utils/hdparm-functions[/FONT]**
```

            if hdparm_is_on_battery; then
                OPTION="200"
            else
                OPTION="254"
            fi
```...

Thank you.  I was having this problem on my Asus 1005HA.

---

