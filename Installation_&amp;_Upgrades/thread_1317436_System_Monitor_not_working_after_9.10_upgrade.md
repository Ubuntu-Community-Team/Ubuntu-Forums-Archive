---
title: "System Monitor not working after 9.10 upgrade"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by pdugas on 2009-11-06
Hi,

I upgraded to release 9.10 and now system monitor does not work. When I invoke it from the administration icon, nothing happens. The first time I invoked it, there was an error message  (which I did not record). I just tried to re-invoke it. Now I no longer get an error message - it just spins for a few seconds then nothing.  I tried to re-install the gnome system monitor package but to no effect. I have not noticed anything else not working.

Environment:
- Ubuntu R9.10 installed via the upgrade feature. 
- Running as guest in Virtual box with Windows host
- Problem started with upgrade to R9.10
- Also have Kubuntu 9.10 running in Virtual Box with system monitor working but that was a clean install

Any suggestions on how to get it working will be appreciated.

Thanks .......... Paul

---

### Post by fabianspiteri on 2009-11-06
Running gnome-system-monitor from terminal could give you some indication from the output. I always do that as a first step.

Fabian

---

### Post by pdugas on 2009-11-06
Hi fabianspiteri,

I'm not that proficient in using the CLI.  How would I do that?


....... Paul

---

### Post by fabianspiteri on 2009-11-07
Hi,

Hit ALT+F2 and type gnome-terminal and hit enter.

In the terminal type gnome-system-monitor and hit enter. You will get an output in the terminal.

Fabian

---

### Post by pdugas on 2009-11-08
Hi,

Here is the response from entering the command in terminal:


>> paul@paul-desktop2:~$ gnome-system-monitor
>>
>> ** (gnome-system-monitor:3482): WARNING **: SELinux was found but is >> not enabled.
>>
>>
>> GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to >> class after it was derived
>> aborting...
>> Aborted (core dumped)


When I try to report the problem I get the following:

>> The problem cannot be reported:
>>
>> The program crashed on an assertion failure, but the message could >> not be retrieved. Apport does not support reporting these crashes."


.............. Paul

---

### Post by murflaw7424 on 2009-11-08
I receive the same error message.  I was able to access system monitor and then created a keyboard shortcut, after reboot it will not open and gives me that error message.

---

### Post by fabianspiteri on 2009-11-09
This is most probably directly related to this : [http://ubuntuforums.org/showthread.php?t=1312466](http://ubuntuforums.org/showthread.php?t=1312466)

Fabian

---

### Post by pdugas on 2009-11-09
Thanks fabianspiteri.  That is the issue .......... Paul

---

### Post by fabianspiteri on 2009-11-10
You're welcome :)

Fabian

---

