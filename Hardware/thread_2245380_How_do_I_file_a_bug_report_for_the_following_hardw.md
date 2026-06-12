---
title: "How do I file a bug report for the following hardware in 14.04"
date: 2014-09-23
forum: Hardware
---

### Post by dave131 on 2014-09-23
Device:  Pinnacle Dazzle DVC100 USB video capture device

Symptoms:  In 13.10, the device showed as "video for linux 2" in VLC.  In 14.04 it shows a selection of camera, tv, etc., but no video for linux 2 device.  I can select video1 for input, but it doesn't work.  VLC sits at the red cone.  I suspect this is something in the changes for how USB plug-n-play devices are handled in 14.04 and the resulting changes to udev.  To try to prove this, I wiped my laptop and installed 12.04 and everything works fine - the device shows as "video fo linux 2" in VLC, I select video1 for input and it works fine.  It appears that the v4l2 release is the same based on what shows in the log file.  I would like to be able to stay with 14.04, but I'm "stuck" with 12.04 until this can work in 14.04.

Possible cause:  The changes in 14.04 for how USB hot plug devices are handled.  As an example, the changes messed up countless people and their use of the point and shoot digital cameras until a change was made.  This also had to do with changes made to UDEV - I believe in the rules for USB.

I would like to file a bug report, but everything I've been forwarded to for bug reports wants OS and software information, some sort of log files, etc., that I can't hardly generate when I have to be on one OS version, not both.  Never got this to work via a VM.  So, how does one file a bug report when all you can give is a description of the problem but can't provide all the documentation they require?

---

### Post by mastablasta on 2014-09-23
you can boot live session 14.04 and then go to Launchpad, sign up and report bug along all relevant data and possible any log files.

for more info read this:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

hardware bug is also mentioned.

---

### Post by dave131 on 2014-09-23
I'll give that a try tonight - thanks!

---

### Post by dave131 on 2014-09-25
Someone on the askubuntu  site gave me a "fix" for at least getting to run in 14.04.  However, the sound gets out of sync so it is noticable about a minute in and it gets progressively worse.  Over the course of a 1 1/2 hour movie it is so terrible that it is beyond be funny! ;)  So, unless someone can come with a solution for that I'll have to see if there are other options available.  So at least for now I don't need to file a bug report.  Thanks for posting the link for doing so - if I have something beyond "operator error" later I'll know what to do.

---

