---
title: "Inspiron 5100 wont sleep when lid closed"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by tgm4883 on 2007-01-25
I have an Inspiron 5100 laptop and when I close the lid nothing happens.  I have tried both things listed in this thread.  [http://ubuntuforums.org/showthread.php?t=121720&highlight=laptop+close+lid](http://ubuntuforums.org/showthread.php?t=121720&highlight=laptop+close+lid)
I also have done a little testing but need some help.  If I manually type in (from /etc/acpi) ./sleep.sh nothing happens, ./sleepbtn.sh laptop goes into sleep mode, ./hibernate.sh laptop goes into hibernation

I can also click on the shutdown button and go to sleep or hibernation from there.  When my laptop is in sleep mode (from either typing it in or pressing shutdown then sleep) when I open the lid my laptop will resume.

So what I want to do is have the laptop go into sleep mode when I close the lid.

What I need to find out is if the computer even knows that I am shutting the lid.  How do I do that?  It knows when I am opening it, but it is an old laptop and perhaps it is broken.  In that case, how would I go about putting a button for sleep on the panel?

---

### Post by tgm4883 on 2007-01-26
bump

---

### Post by Argilo on 2007-02-08
I'm having precisely the same problem with my Inspiron 5100.  I've tried a few things but haven't managed to solve it.  Oh well, I guess I'll just have to keep suspending it manually for now.  Hopefully this will be fixed when the next release of Ubuntu comes out.

---

### Post by NeoChaosX on 2007-02-10
[This post](http://www.ubuntuforums.org/showpost.php?p=494858&postcount=6) will help you with this problem. Fixed it for my 5100.

---

### Post by Argilo on 2007-05-06
I just came up with a workaround for this problem.  Since the lid state (open/closed) is still reported correctly in /proc/acpi/butten/lid/LID/state, I made a cron job which checks every minute to see whether the lid is closed, and suspends the machine if it is.

Here's the script, which I put in /root/suspendhack.sh by doing "sudo gedit /root/suspendhack.sh":

```
grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]; then
        /etc/acpi/sleepbtn.sh
fi
```

Next I made the script executable by doing "sudo chmod 700 /root/suspendhack.sh".

Finally I added it to root's crontab by doing "sudo crontab -e" and appending the following line:

```
* * * * * /root/suspendhack.sh
```

Now when I closed the lid, the laptop will suspend within one minute.  Not a perfect solution, but good enough for me.

---

