---
title: "IBM Thinkpad X22 suspend / resume issues"
date: 2011-02-14
forum: Hardware
---

### Post by acy76 on 2011-02-14
Posting this so that it might aid others searching for help with this machine:

I've been running various Ubuntu derivatives on an old Thinkpad X22, including CrunchBang and lubuntu (my current favorite).

Under Crunchbang 9.04, suspend worked perfectly well, but sound was muted on resume and couldn't be revived using the volume buttons.

After upgrading to lubuntu (lightweight ubuntu - absolutely the best thing to ever happen to this old laptop) 10.10, I noticed that suspend was broken - the backlight was staying on even though the rest of the machine appeared to be off. Resume worked fine, although the sound was still muted.

In order to fix these issues, I added two scripts to the /etc/pm/sleep.d/ directory.

**Note that these must be made executable in order for them to work. Also, radeontool is not installed by default but can be found in the repositories.**

```
#!/bin/bash
#
# Fix: Unmute sound after suspend/hibernate
# /etc/pm/sleep.d/20_fix-sound

case "${1}" in
	resume|thaw)
	  amixer set Master off
	  amixer set PCM off
	  amixer set PCM on
	  amixer set Master on
	;;
esac
```


```
#!/bin/bash
#
# Fix: LCD backlight during suspend/hibernate
# /etc/pm/sleep.d/99_screen-fix

case "${1}" in
	hibernate|suspend)
	  radeontool light off
	thaw|resume)
	  radeontool light on
	;;
esac
```

The filenames I used are in the script comments; I am not sure whether the order of execution matters here (I believe the scripts are executed in order of their names, hence the numbers in the filenames), but this is how I've set it up on my X22 and it works great.

The only issue is that automatic screen dimming seems to be disabled after resuming from suspend, but this is a small price to pay.

I found the radeontool solution on the [ThinkWiki]("http://www.thinkwiki.org/wiki/Problem_with_high_power_drain_in_ACPI_sleep") (read about alternative approaches there); can't recall where I found the sound solution.

---

