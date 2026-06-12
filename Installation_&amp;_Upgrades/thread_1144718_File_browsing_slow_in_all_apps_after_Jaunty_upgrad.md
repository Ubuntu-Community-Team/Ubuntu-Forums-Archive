---
title: "File browsing slow in all apps after Jaunty upgrade"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by cdeobald on 2009-05-01
Since I upgraded from 32-bit Intrepid to 32-bit Jaunty any application which attempts to bring up a file browse dialog box (eg. to open or save a file) stalls for approximately 20 seconds before the browse window appears.  This is not limited to Firefox.  The behaviour is exactly the same in Inkscape, GIMP, Open Office and other applications.

When I bring up the System monitor, it reports CPU usage between 50 and 100%, even though, at present, the only applications I have running are Firefox (to post this thread), Handbrake (which is paused), and the system monitor itself.  While Firefox shows occasional spikes, the largest consumer of CPU cycles appears to be the system monitor itself, and the CPU usage reported under the "processes" tab comes nowhere near to totaling the consumption reported in the "resources" tab.

This behaviour first appeared immediately after the upgrade, which, otherwise, went without a hitch.

My system is a Dell Dimension C521 with 4GB of RAM and a 350GB HD with 133 GB free.  I have an ATI Radeon HD 2400 Pro video card; all Compiz visual effects are currently turned off.  (I had to do turn these off so video would run smoothly again.)

I have read some comments about similar lags, but I have yet to find a suggestion of a cause or solution.

---

### Post by Wardje on 2009-05-01
Had it too, reboot seemed to have solved it (not sure how long it will last, reboot only a few minutes ago)

---

### Post by cdeobald on 2009-05-01
> **Wardje said:**
> Had it too, reboot seemed to have solved it (not sure how long it will last, reboot only a few minutes ago)

Perhaps I should have said that this is persistent behaviour.  Unfortunately, I don't think a  re-boot will provide a long-term solution.

---

### Post by _haz on 2009-05-02
I am unfortunately experiencing the exact same behaviour you describe with 32 bit jaunty upgraded from intrepid. Unfortunate since the experience for many seems to be improved performance, but on this particular installation the upgrade has been a definite step backwards. Does anyone have any thoughts on where to start looking to track down the cause?

Edit: I should also mention this behaviour is persistent since the upgrade, reboot, different apps etc make no difference.

---

### Post by kingaaronj on 2009-05-03
Hey guys!  I found a solution here towards the end of the thread: [http://ubuntuforums.org/showthread.php?t=811795&highlight=save+open+slow]("http://ubuntuforums.org/showthread.php?t=811795&highlight=save+open+slow")

Turns out that the "tracker" package is goofed.  So run this from a terminal:

```
sudo apt-get purge tracker && sudo apt-get install tracker
```

I logged out and logged back in afterwards for good measure, but supposedly it's an instant fix.

Credit goes to [Miata-MS]("http://ubuntuforums.org/member.php?u=709283")

---

### Post by cdeobald on 2009-05-03
Thanks.  That did it.  It even worked without logging out.

---

### Post by cwmoser on 2009-06-07
I tried the ...

```
sudo apt-get purge tracker && sudo apt-get install tracker

```

... and it speeds up Internet browsing but then later Internet browsing slows down.  Like this it not a permanent fix.

Any ideas????

Thanks

Carl

---

### Post by cdeobald on 2009-06-07
I believe that your issue is different that the one being discussed in this thread.  The thread is about browsing for files *locally* on the computer, not *Internet* browsing.  The solution provided here takes care of a 30-second lag in the appearance of any *file save* or *file open* dialogue box.

You may find a solution in another discussion thread.  I'm sorry I can't help much with the amount of information you've given regarding your Internet browsing issue.

---

