---
title: "My machine is redlining while idle."
date: 2011-12-07
forum: Hardware
---

### Post by gardengxc on 2011-12-07
I've got a phenom 2 hexcore @3.2ghz but no matter the load it says it's running at 100% on all 6 cores. I can just be looking at my desktop and still 100% all 6 cores. Running Ubuntu 10.10.

Further the system monitor when under the processes tab says "load average for the past 1, 5, 15 minutes:6.12, 6.21, 6.26", but resources still says 100%.

---

### Post by typhoon_tip on 2011-12-07
Can you install the temperature indicator and check cores temperature ? Just to make sure is a bug on sys monitor or something else that makes the cores... over-revving !

---

### Post by gardengxc on 2011-12-07
It says no thermal monitor support. I know my MOBo has sensors however.

---

### Post by typhoon_tip on 2011-12-07
> **gardengxc said:**
> It says no thermal monitor support. I know my MOBo has sensors however.

Do this:
```
sudo apt-get install lm-sensors
```

Reboot, and then:
```
sensors
```

Let us know the temperature after a while that is running.

---

### Post by Mark Phelps on 2011-12-07
Before you run "sensors", you have to run "sudo sensors-detect" to configure them.  Reply Yes to all the prompts and let it install the modules.  You will then have to reboot to configure them.

Once you reboot, THEN run "sensors" to see what it displays.

---

### Post by gardengxc on 2011-12-07
Never mind. I backed up everything that was important after I saw I didn't have the problem on a live cd and then I did a fresh install of 11.10.

---

