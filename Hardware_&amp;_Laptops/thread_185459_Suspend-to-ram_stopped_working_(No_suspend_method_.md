---
title: "Suspend-to-ram stopped working (No suspend method found)"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by michux on 2006-05-31
After last update (I'm using testing Dapper) suspend-to-ram stopped working. I investigated the problem by killing gnome-power-manager starting it with **gnome-power-manager --no-daemon --verbose**

Here is the log I get after pressing the suspend button on my keyboard:

```
[suspend_button_pressed] gpm-manager.c:1131 (00:43:59):  suspend button pressed
[manager_policy_do] gpm-manager.c:683 (00:43:59):        policy: /apps/gnome-power-manager/action_button_suspend
[gpm_manager_is_policy_timout_valid] gpm-manager.c:204 (00:43:59):       gpm_manager_is_policy_timeout_valid: check-foreground-console returned with 0

[manager_policy_do] gpm-manager.c:701 (00:43:59):        *ACTION* Suspend
[manager_do_we_screensave] gpm-manager.c:622 (00:43:59):         Using custom locking settings (1)
[gpm_screensaver_lock] gpm-screensaver.c:164 (00:43:59):         doing gnome-screensaver lock
[gpm_syslog] gpm-debug.c:117 (00:44:01):         Saving to syslog: Suspending computer because the suspend button has been pressed
*** WARNING ***
[gpm_hal_handle_error] gpm-hal.c:225 (00:44:01):         [B]suspend failed
(No suspend method found)[/B]

```

Any idea what might be wrong?

Thanks in adcance for your support!

---

### Post by Maavin on 2007-11-15
I'm aware, that this answer is a bit late, but I had the same problem on 7.10 (2.6.22-14-generic x86_64 on Thinkpad X61s /w UMTS option)

It turned out to be a really stupid "error"...

I installed Oracle and created "/etc/redhat-release" to satisfy the oracle installer...

therefore the gnome-power-manager also thought it was running on redhat and did not find a suitable suspend method...

I felt a bit silly...

just for better searching : No suspend method found

---

### Post by priekopa on 2008-01-20
same "stupid mistake" here :) ... your post was just salvation maavin ...

---

