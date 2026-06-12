---
title: "Auto restating problem"
date: 2011-11-06
forum: Hardware
---

### Post by admtuku on 2011-11-06
My toshiba laptop restarts suddenly if it's plugged in . I was using Windows 7.
But works well on battery and safe mode.  I started using safe mode and it has been about 3 months with safe mode.I can do almost everything without playing audio in safe mode. Now i installed Ubuntu 11.04 but it's shutting down suddenly (when plugged in) like it did on windows 7. 
Is there any safe mode option in ubuntu? I'm quite sure there's not any. So, is there any other way to run it ( like safe mode ) or is there any other version of linux that can work like safe mode ?

---

### Post by diasf on 2011-11-06
You most likely have a hardware issue.... is the laptop still under warranty?

---

### Post by sanderd17 on 2011-11-06
This can be a diffucult problem to solve.

When you go in Windows safe mode, it disables some drivers and startup programs.

Since you are talking about a difference between being plugged in and working on battery, I'm thinking of a power issue.

How does the shutdown goes? Is it just a beep and gone? Or do you see some text on the screen while shutting down?

In the second case, I would really want to see your kernel log. Can you upload the file /var/log/kernel.log?

And I would also want you to try some boot options (see my signature on how to set boot options). The option acpi=off disables all power and heating control, but it's good to try and see if it's better. You can't keep working on a computer with acpi=off for a long time though, some parts of your computer would die to fast with that option.

---

### Post by admtuku on 2011-11-06
[sanderd17]("http://ubuntuforums.org/member.php?u=742644") It shuts down without any message. Sometimes it freezes.

[diasf]("http://ubuntuforums.org/member.php?u=933718") It's almost 3 yrs old. So, No warranty :(

---

### Post by sanderd17 on 2011-11-06
Try acpi=off boot setting.

---

