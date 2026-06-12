---
title: "After upgrade, &quot;About Ubuntu&quot; no longer knows its version"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by ajaygautam on 2008-12-30
System -> About Ubuntu used to display the version of ubuntu.

I upgraded over the weekend.

System -> About Ubuntu no longer displays version information.

All it says is:
"Thank you for your interest in Ubuntu  - the  - released in ."

Screen shot attached.

Should I file this as bug report?

PS: I *am* able to confirm version from command line:
```

$ cat /etc/issue
Ubuntu 8.10 \n \l


```

What should I do so that About Ubuntu also shows version information.

Ajay

---

### Post by hansdown on 2008-12-30
Hi ajaygautam.

Have you tried this?

[http://www.howtodude.net/howto/view.article.php/429](http://www.howtodude.net/howto/view.article.php/429)

---

### Post by stderr on 2008-12-30
A problem with one of the language packs maybe? I heard of someone else with this issue; I know they had the language set to US English. What is the output of 

```
locale
```

I'm running "en_GB.UTF-8" on Ibex, not experiencing the same issue.

---

### Post by ajaygautam on 2008-12-30
> **hansdown said:**
> Hi ajaygautam.

Have you tried this?

[http://www.howtodude.net/howto/view.article.php/429](http://www.howtodude.net/howto/view.article.php/429)

Yes, I know about uname, but the issue is not finding out which version I am on.

The issue is that About Ubuntu does not know.

Thanks

Ajay

---

### Post by ajaygautam on 2008-12-30
> **stderr said:**
> A problem with one of the language packs maybe? I heard of someone else with this issue; I know they had the language set to US English. What is the output of 

```
locale
```

I'm running "en_GB.UTF-8" on Ibex, not experiencing the same issue.

I get:
```

$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

It seems ok. Any other suggestions?

Thanks

Ajay

---

### Post by stderr on 2008-12-30
Yeah, his output was the same as yours, we never got to the bottom of it though. The difference in locale was just something obvious that we could grab onto to help debug, but we just got lost searching through language packages, and I couldn't be bothered to look at the Yelp source/find the relevant help files etc.

I was just trying to find a bug report on the issue and bumped into [this]("https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/292109"), which looks pretty similar, and still unsolved, but they also suspect the en_US language packs with Yelp, GNOME's help browser.

Unless someone posts in a while with something other than US English that does the same thing :) In fact, I wonder if changing locales (somehow) and rebooting might work?

---

### Post by cariboo on 2008-12-30
Have a look at my screenshot, check System-->Administration-->System Monitor and see what it says.

Jim

---

### Post by ajaygautam on 2009-01-10
> **cariboo907 said:**
> Have a look at my screenshot, check System-->Administration-->System Monitor and see what it says.

Jim

Yes. System Monitor shows the correct details: (ubuntu version, hardware info etc.). I did not know about System Monitor actually showing system details (Damn, windows is SO ingrained into my psyche).

The issue / mystery still remains: why is About Ubuntu not showing version information.

---

