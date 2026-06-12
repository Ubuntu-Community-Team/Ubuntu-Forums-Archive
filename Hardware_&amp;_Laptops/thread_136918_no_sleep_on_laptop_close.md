---
title: "no sleep on laptop close"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by olsonar on 2006-02-26
i have an HP dv4000 laptop, and when I close the lid, it doesn't do anything, even though I have it set to sleep in my power preferences. sleep works fine if I activate it manually. Any ideas on how to fix this?

---

### Post by wrtrdood on 2006-02-27
Did you edit the /etc/default/acpi-support file and uncomment ACPI_SLEEP=true line?

---

### Post by olsonar on 2006-02-27
Yes, and sleep works fine when selected from the log out options.

---

### Post by wrtrdood on 2006-03-01
Sounds like it's not picking up the LID event.  Seems I had some trouble with that at one time and I ended up editing the scripts to write out some log messages to see what was happening where.  Might have to do that.

BIOS settings can sometimes be a problem too.

---

### Post by olsonar on 2006-03-02
any specific suggestions? I'm pretty new to linux.

---

### Post by wrtrdood on 2006-03-02
Gotta look at this when I get home.  I'll try to come up with some specific suggestions.

---

### Post by wrtrdood on 2006-03-03
Check /var/log/acpid for a LID event being detected.  Something like:

[Thu Mar  2 06:09:23 2006] received event "button/lid LID 00000080 00000001"
[Thu Mar  2 06:09:23 2006] notifying client 6074[111:111] [Thu Mar  2 06:09:23 2006] executing action "/etc/acpi/lid.sh"

This verifies that the lid action is being seen.  Then look at /etc/acpi/lid.sh and check this section:


grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
            . /usr/share/acpi-support/screenblank
            . /etc/acpi/sleep.sh
        fi
    done



If I recall correctly, I added the sleep.sh line to mine.  If yours does not 
have this line, add it and try again.

---

### Post by olsonar on 2006-03-03
There's nothing ih the log file. I added the the line anyway, and it still doesn't work. So it seems ACPI isn't registering when i close my lid. any ideas how to fix this?

---

### Post by wrtrdood on 2006-03-05
Ok.  This is really odd.  I hope it works for you.

FIrst, I discovered that since I was still running KDM, the klaptop daemon was apparently doing all the work, masking the action of the ACPI scripts.  I've since disable KDM which caused the lid close function to stop working.  To troubleshoot this I simply added a line like this to the /etc/acpi/lid.sh script:

echo "Lid close detected. "

Now it works.  Try that and see what you get.  I stuck it in right after the

if [ $? = 0 ]
then

at the top of the script.  It should also put a message in the log file.  BTW - when you say nothing in the log file you mean there's nothing at all like what I posted above?  That's odd.  You might want to check dmesg for ACPI entries and verify that there's a /proc/acpi with information in the directory to be sure ACPI is actually running (although from your first post I would think this is all good.)

---

### Post by wrtrdood on 2006-03-05
Naw.  I think I found the problem -- at least the one I'm running into.  It has something to do with the xauth stuff, I think.  Try commenting out the if and fi lines containing $XAUTHORITY and see if it works then.  I'm still researching the issue.

---

