---
title: "Laptop Hard Drive spin up and spin down"
date: 2008-12-02
forum: Hardware
---

### Post by chadeldridge on 2008-12-02
On almost a constant basis (every 10 seconds) my laptop hdd is spinning up and then down ... sleeping for 10 seconds and then spinning back up.  I  am running laptop_mode but at this point have disabled all the hdd power management features, although its still happening.  Any ideas?

I should mention that it is only happening on battery mode, not on AC power.

---

### Post by mitchellcipriano on 2008-12-02
That is the way it is supposed to work. The HDD spins down to save power, but the file system spins it up for journaling. It only does this on battery as a compromise to save power on battery, but reduce the wear on the HDD when on AC.

---

### Post by loomsen on 2008-12-03
Hello.

So I assume you have laptop-mode installed. I do, and if I don't configure it, I'm suffering from this problem as well. Not too frequent, but it still hurts.

So, with laptop-mode(l-m from now on) installed, edit your l-m conf:
```
sudo nano /etc/laptop-mode/laptop-mode.conf
```

And as you say it happens only on battery, LM and BAT are the attributes we're looking for.
One of the first options is enable l-m on BAT. If you wanna take the easy way, do this, tho I wouldn't recommend it. Spinning your drives head down during battery life is essential, assuming you're on BAT cause your laptop is carried around or so, just not standing still.

So, let's continue, the next interesting options imho are:
LM_BATT_MAX_LOST_WORK_SECONDS=600
LM_AC_MAX_LOST_WORK_SECONDS=300

CONTROL_READAHEAD=1

LM_READAHEAD=3072
NOLM_READAHEAD=1024

USE_RELATIME=1

Tho this is sth you may consider up to your preferences, this is not causing your load_retry...

Now we're getting closer:

CONTROL_HD_IDLE_TIMEOUT=1

LM_AC_HD_IDLE_TIMEOUT_SECONDS=720
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=70
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200

This is rather important, but still not the option causing load_retry.
NOTE: You may adjust all options to your prefs so far...

Now the next values to specify are the PowerManagement options.
THIS IS CAUSING YOUR LOAD_RETRYs

So, enabling laptop-mode to
CONTROL_HD_POWERMGT=1

and specifying values to use:
BATT_HD_POWERMGMT=200
LM_AC_HD_POWERMGMT=220
NOLM_AC_HD_POWERMGMT=245

[color=red]NOTE: The range of possible values is 128 - 254
Some HDs work with a value of 255 too, which represents a wildcard, however mine doesn't. So here's the section to play with, you may have to adjust it over time, but once you found your prefered settings, you're basically done.[/code]

I used to backup the original file and adjust these values over and over again.
As mentioned, values between 128 and 254, while 254 is the highest=most aggressive value. 
This will cause your harddrive to avoid any attempt to spin down.
128 is the most soft value, usually only of use if you're using your laptop while riding a horse or so, however this is the most secure value while in L-M.

Then a couple of options you may make up values again, and one rather important value:
LM_DIRTY_BACKGROUND_RATIO=3
NOLM_DIRTY_BACKGROUND_RATIO=10

Again, these are MY settings I found out to work for ME and MY laptop. But at least you know where to look for them now, I hope :)

Oh, and the very last option:
LM_SECONDS_BEFORE_SYNC=60


Now edit your hdparm.conf and adjust the values to avoid conflicts.
```
sudo nano /etc/hdparm.conf
```

And set the values according to the ones you just specified. I.e. if you enabled PowerManagement in l-m.conf, disable it in hdparm.conf et vice versa.

Usually I'd recommend choosing either or, depending on your actual time on battery. If you're using your laptop as a desktop replacement most of the time anyway you might want to use hdparms values rather than l-m-tools.
I'd configure them both, hdparm.conf for major home usage, and l-m.conf for university or so. Then, before starting off to school, just replace hdparm with the default and l-m with your configured. back home switch back using hdparm and disabling l-m again.

Just for instance... GL.

---

### Post by chadeldridge on 2008-12-03
Thank you very much .. i will get to editing those options again .. my problem may be that i already have all those set and then have conflicting ones in hdparm.conf ... never really thought to look there.

---

### Post by Valde_91 on 2008-12-07
Hi! Same problem here! I set my laptop-mode.conf to spin down my drive after 1 minute, but my drive spins downs after 5-10 seconds, then spins up for 10 seconds, then after 10 sec down, then up, ...

Further when my battery is critical my machine doesn't hibernate, but goes out of power.

I use ubuntu since 6.10. With 7.04 and 7.10 no problems, my drive spins down after 1 minute, hibernating on critical battery worked fine. Then since 8.04, I start having this problems. Now with 8.10 is even worse because I don't understand where to set the parameters: the parameters set in laptop-mode.conf are clearly ignored. My hdparm.conf have no lines that aren't comments, i.e all lines there begin with #.
 
I can't set properly my laptop on battery, so I had some overconsumption and I worse my HD dies yesterday during one cycle of spinning up-down-up. Now I have a new HD, and frankly I want to be sure that this one will not die soon.

So every advice is welcomed!

Thanks all!
Valde_91

---

