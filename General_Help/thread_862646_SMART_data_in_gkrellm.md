---
title: "SMART data in gkrellm?"
date: 2008-07-17
forum: General Help
---

### Post by kerryhall on 2008-07-17
Does anyone know how to script smartctl diagnostics to run every 5 minutes or so, and have the results displayed in gkrellm? If so, how to do it?

Or does anyone know of any gui for SMART monitoring? If so, what is it?

If no for both of these, how can i suggest both of these as features?

Thanks!

---

### Post by kerryhall on 2008-10-01
Bump.

---

### Post by kerryhall on 2008-10-13
Bump.

---

### Post by kerryhall on 2008-10-16
Bump.

---

### Post by kerryhall on 2008-10-22
Bump.

---

### Post by kerryhall on 2008-11-04
Bump.

---

### Post by loomsen on 2008-11-04
I don't use gkrellm, but you can easily run a command and parse it's output either directly into gkrellm or, like I do for instance, have a crontab and let it do for you.

For instance, I run 
```

docter[~] sudo smartctl -A /dev/sda | grep -i load|grep -i retry
223 Load_Retry_Count        0x0032   098   098   000    Old_age   Always       -       2441
docter[~] 

```

Now that doesn't look too good in any of the programs, yet is very useful for monitoring, espc hence I'm suffering from high_load_cycle_count problems. Or I did more likely. So, running this code above would be pretty useful every 30 mins to have a long time look at it.

So my cron cmd looks like this:
```
date;sudo smartctl -A /dev/sda | grep -i load|grep -i retry >> ~/.hdd-health

```
This will append the output of the command to the contents of .hdd-health with the date. A basic system log file actually.
```
docter[~] date;sudo smartctl -A /dev/sda | grep -i load|grep -i retry
Wed Nov  5 03:35:26 CET 2008
223 Load_Retry_Count        0x0032   098   098   000    Old_age   Always       -       2441

```

For more infos on cron see 
man cron

Now, this still doesn't look very well on your desktop. But smartctl also shows the temperature in its whole output, so let's get this info:

```

docter[~] sudo smartctl -A /dev/sda | grep -i temp |cut -d "-" -f2
       35 (Lifetime Min/Max 15/47)
docter[~] sudo smartctl -A /dev/sda | grep -i temp |cut -d "-" -f2 | cut -d"(" -f1
       35 
docter[~] 

```

If you set up another cronjob with above command and append sth like:
```
sudo smartctl -A /dev/sda | grep -i temp |cut -d "-" -f2 | cut -d"(" -f1 > ~/.hdd-temp

``` cron will override files contents every time.
So a simple cat ~/.hdd-temp will always show you a number like above, which then can easily be formatted to fit into everything else.

This way you can easily get only the value you really want.

I have cron writing this to another file which I then just parse through conky. If you can run commands in gkrell you may as well simply take the whole command and paste it as the command to be run. But you should set up a group for smartctl then so that you grant yourself access, otherwise you'll have to enter your password...

Oh, and the best thing about it, other than hddtemp for instance this causes no IO on the disk.

---

### Post by kerryhall on 2009-02-18
Fantastic! I will definitely give this a try. :)

---

