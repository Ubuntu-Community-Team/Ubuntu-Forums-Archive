---
title: "Run script on hibernate/standby resume and AC/battery state change"
date: 2008-07-30
forum: General Help
---

### Post by jb_ on 2008-07-30
After the Win XP install on my laptop getting completely owned by a virus which I can't even figure out how it got on there I've decided to go full time Ubuntu on my laptop.

Everything is fantastic except a few issues:

I would like to know how I can run a script or command on resume from hibernate or standby. This is so I can disable APM on my lappys hdd because it has faulty firmware. It's the Hitachi piece of crap that has probably be discussed many times before, basically sometimes it decides to park it's head after each and every read or write, putting seek times through the roof. I put hdparm -B 255 /dev/sda in my rc.local to fix the drive at boot, just need to do it on resume now.

Second issue, not really an issue but I thought I might throw it out there incase someone knows the answer... when I resume from hibernate gpm tells me my machine failed to hibernate, but all my programs are still running, so it seems to work. 

And lastly, my battery life is around 4.5 hours without Compiz running and around 3 hours with it running. I'm looking for a reliable way to run commands when the power switches from AC to battery and visa versa. It would also need to work when it's running on AC, put into sleep/hibernate then switched to battery and woken. Same goes for booting on battery, it would need to have Compiz disabled.

Any help would be much appreciated, help me get away from Windows! :)

---

### Post by jb_ on 2008-07-31
I found [this](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14), even though it reportedly doesn't work in 8.04 it seems to be working for me.

Now I just need to find a way to disable Compiz on battery.

Edit: No it's not working, drive is still parking it's head excessively.

---

### Post by derrick81787 on 2008-07-31
> **jb_ said:**
> I found [this](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14), even though it reportedly doesn't work in 8.04 it seems to be working for me.

Now I just need to find a way to disable Compiz on battery.

Edit: No it's not working, drive is still parking it's head excessively.

It's very similar to this, except just a different directory. Unfortunately, I'm at work on Windows right now.  I think that you want to look in /etc/pm.  There you should find a folder called sleep.d and one called power.d.  I could be wrong on the /etc/pm, but I think this is correct.

Executable scripts that are placed in /etc/pm/power.d are ran any time a laptop switches power states (eg. goes from ac to battery power and vice-versa.) /etc/pm/sleep.d happens when it goes to and from sleep mode.

Running "metacity --replace" will disable compiz, and "compiz --replace" will re-enable it again.

For example, if you name this script 98-handle-compiz.sh, make it executable, and place it in /etc/pm/power.d, it should enable/disable compiz depending on the power state of your laptop.

```
#!/bin/sh
if on_ac_power; then
   compiz --replace
else
   metacity --replace
fi

```

You'll have to make this script executable by running:

```
chmod +x 98-handle-compiz.sh
```

This should work. Before copying it to /etc/pm/power.d, you could try simply executing it from the command line while on battery power to see if it disables compiz, but it should. Unfortunately, I can't test it out at the moment since I'm currently stuck on Windows.

I hope this has helped.

- Derrick

---

### Post by macksgarage on 2008-11-09
Thanks for the excellent information.  I used this info to adjust the refresh rate automatically when switching power states.  Compiz can set the refresh rate, and AFAIK this is more effective than disabling compiz entirely on battery power.  It mimics a setting that was available in the ATI control panel on XP to dump the refresh rate on battery, which gains an hour+ of battery life on my thinkpad t40 with hi-cap battery.

Install this script in /etc/pm/power.d, make executable, etc. . . and replace all instances of 'username' with the user who is logged in and running compiz. The reason for the 'su' stuff is that gconf settings are user specific and otherwise it will change the settings for root, not what we want.  You can adjust the target refresh rates as well. 60 on ac is laptop screen default. 10 on battery is a little jerky but smooth enough to work without irritation. any value from 1-60 is effective and could make sense, values over 60 are greater than the screens refresh rate, I don't know the effect cause I haven't tried it.  To make this work you will also have to open compiz settings manager > general options > display settings and unclick 'Detect Refresh Rate'.

```

#!/bin/sh
if on_ac_power; then
        su - username -c "gconftool --type=int --set /apps/compiz/general/screen0/options/refresh_rate 60"

        else

        su - username -c "gconftool --type=int --set /apps/compiz/general/screen0/options/refresh_rate 10"

fi



```

NOTE: I did this on Debian Sid 11/08 but as it was all based on the information for ubuntu previously posted by derrick81787 I see no reason why it won't work on Ubuntu.

---

