---
title: "[Fix] Thinkpad suspend freeze (resume failure)"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by lbharti on 2008-02-08
I tried everything, but for long time failed to get a fail-proof suspend. It is important for me to suspend my computer every half an hour and get it back running, but it would freeze every second or third time. 

To make it work, all I needed to do was to add thinkpad_acpi to the list of modules to be removed before and loaded after resume. It works like a charm now, without unexpected freezes.

Here is the edited part of my /etc/default/acpi-support :
[COLOR="Navy"]
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES="thinkpad_acpi"[/COLOR]
:guitar:

Note: I have thinkpad x61, but it should work on other ones too, because thinkpad_acpi has some experimental portions.
[COLOR="Red"]Please follow my second post, this solution is flawed.[/COLOR]

---

### Post by Whiffle on 2008-02-08
Which thinkpad do you have?

---

### Post by lbharti on 2008-02-09
After every attempt to make the default suspend system work, I have shifted to hibernate-ram for my suspend functionality. 

There have not been any problems with the default hibernate functionality, which has been successful one hundred percent, but suspend seems to be affected with too many things, such as an invalid service, USB ports, experimental thinkpad acpi module, invalid modules after a kernel update etc. 

Hibernate-ram works flawlessly since I installed it yesterday, and gave me a resume back even after eight hours of standby.  I still use the default hibernate functionality, and it does not seem to be affected by the use of hibernate-ram. In eight hours, my battery reduced from 77% to 67%.

Steps to install hibernate-ram:

[COLOR="DarkBlue"]>sudo -H -s[/COLOR]

>apt-get install hibernate

>cd /etc/hibernate

I did not find any problems with ipw3945 module which is blacklisted. It will cause hibernate-ram to stop suspend. To disable it :
[COLOR="DarkBlue"]
>nano blacklisted-modules[/COLOR]

and find and comment out ipw3945 at the bottom of the file.

[COLOR="DarkGreen"]#ipw3945[/COLOR]

save the file by pressing ctrl+O, exit by pressing ctrl+x.

To take care of the black screen after resume:
[COLOR="DarkBlue"]>nano common.conf[/COLOR]

add the following line at the end:
[COLOR="DarkGreen"]SwitchToTextModeOnResume yes[/COLOR]

save and exit.
Now try :

[COLOR="DarkBlue"]>hibernate-ram[/COLOR]

It should work. 

To replace the default suspend function on the system :

[COLOR="DarkBlue"]>cd /usr/lib/hal/scripts[/COLOR]

Make a back up of the default suspend script :

[COLOR="DarkBlue"]>cp hal-system-power-suspend hal-system-power-suspend.ori
>echo " " > hal-system-power-suspend
>nano hal-system-power-suspend[/COLOR]

and type :
[COLOR="DarkGreen"]
#!/bin/sh
/usr/sbin/hibernate-ram[/COLOR]

save the file and exit.

You may need to reboot the system for it to work flawlessly.

---

### Post by lbharti on 2008-02-15
It seems even this option does not give a one hundred percent resume, but I have seen that pressing the ThinkVantage button continuously brings the system back. 

After observing this, I switched back to the original suspend system. I found out that pressing the ThinkVantage button recovers this as well, and also after two or three resumes like this, it resumes every time without pressing the button. I wonder why.

---

