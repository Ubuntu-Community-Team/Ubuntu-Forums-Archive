---
title: "[SOLVED] slow resume using pm-utils suspend, use s2ram?"
date: 2008-07-07
forum: Hardware
---

### Post by balak on 2008-07-07
Hi All,

I have an averatec 2150 running ubuntu hardy 8.04 (fully updated) amd64.

```
uname -a : Linux  2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

```

I have been able to both suspend and hibernate on this laptop in hardy. Yay!!

However, I never use the suspend because the resume takes so much time that is useless to suspend. Yesterday I sat down and noted the time taken:

[B]Regular suspend: 7s
Resume from suspend: 115s (1min 55s!!!!!!!!)

Regular Hibernate: 42s
Resume from Hibernate: 58s

Hibernate after suspending: 3min 8s
Resuming from hibernate after suspending: 1min 5s
[/B]

In my laptop, its faster to resume from hibernate than from suspend!! Also, suspend screws up something in my settings since the next hibernate takes a long time (almost 4 times more).

Any ideas on what could be going wrong? I have attached the dmesgs for each of these events.

```

dpkg -l | grep pm-utils
ii  pm-utils                                   0.99.2-3ubuntu10                                   utilities and scripts for power management
dpkg -l | grep uswsusp
ii  uswsusp                                    0.7-1.1                                            tools to use userspace software suspend prov

```

I then installed uswsusp from debian (not hardy) since I really wanted to try s2ram.
Using s2ram (from a terminal), I can suspend and resume in 5s though it doesn't get me back to a locked screensaver like regular resume.
s2disk takes 47s to hibernate and 36s to resume - still faster than regular hibernate.

I am thinking that I will change the hal scripts to point to s2ram/s2disk rather than the regular pm-utils.

Sorry for the long post! If anybody can help me debug this issue, that'll be great. I am willing to get as much data as required to address this.

thanks much!

---

### Post by balak on 2008-07-25
bump!

---

### Post by balak on 2008-07-28
Looks like this thread will be only updated by me ;)

I think I have found a solution to my suspend issue. I found out that '/etc/acpi/sleep.sh force' works perfectly fine on my laptop. However,the hal scripts call pm-utils by default. So I replaced one line in /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux.

First backup the original file:
```
$cd /usr/lib/hal/scripts/linux
      $sudo cp hal-system-power-suspend-linux hal-system-power-suspend-linux.back

```

Then open the file in gedit
```
$gedit hal-system-power-suspend-linux

```

Modify the line which says (around line 73)
> /usr/sbin/pm-suspend $QUIRKS

with 
> /etc/acpi/sleep.sh force


---

### Post by caffeinetooth on 2008-08-06
.

---

### Post by balak on 2008-08-07
> **caffeinetooth said:**
> Hey there,

Just to let you know that this worked perfectly for me on my brand new Sony Vaio VGN-CR510D with Hardy.... that is until 4 resumes later when it stopped working altogether.

Bah.

Did you do an update ? Recently, there was an update to 'hal' which must have overwritten all the changes you made.

Check if your changes are still present. If not, you'll have to redo the steps again.

---

