---
title: "Crontab special entries"
date: 2008-07-17
forum: General Help
---

### Post by Krupski on 2008-07-17
Hi all,

I ran into some info concerning the crontab file. Specifically, there is a list of handy "shortcuts" as such:

```

Entry	        Description	        Equivalent To

@reboot 	Run once, at startup. 	None
@yearly 	Run once a year 	0 0 1 1 *
@annually 	(same as @yearly) 	0 0 1 1 *
@monthly 	Run once a month 	0 0 1 * *
@weekly 	Run once a week 	0 0 * * 0
@daily 	        Run once a day  	0 0 * * *
@midnight 	(same as @daily) 	0 0 * * *
@hourly 	Run once an hour 	0 * * * *

```

I tried '@reboot' in my crontab (Ubuntu Server 64 bit version 8.04.1) and it didn't work.

I know that cron IS working because I put a "once a minute" (* * * * *) test into crontab and *it* worked.

Are these "special" entries *supposed* to work in Ubuntu?

Thanks!

-- Roger

---

### Post by spupy on 2008-07-17
Read
```
man 5 crontab
```
Mine is mentioning these, but I am reading it on Gentoo. 
Instead of @reboot try @hourly. And check your syntax. Even, paste here your line with @reboot?

---

### Post by Krupski on 2008-07-17
> **spupy said:**
> Read
```
man 5 crontab
```
Mine is mentioning these, but I am reading it on Gentoo. 
Instead of @reboot try @hourly. And check your syntax. Even, paste here your line with @reboot?

Here's the line in crontab that doesn't seem to work:

```

# test
  @reboot                               root    /bin/echo Reboot $(/bin/date +%c) | sendmail xxxxxx@xxxxxxxx.com

```

(email is xxx'd out here of course)

In the mean time, I'll try hourly and see if *that* one works.

Thanks.

(edit to add): Just tried "@hourly". It worked. @reboot, however, does not.

---

