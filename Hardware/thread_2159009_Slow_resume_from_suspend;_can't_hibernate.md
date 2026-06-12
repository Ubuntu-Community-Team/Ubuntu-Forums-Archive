---
title: "Slow resume from suspend; can't hibernate"
date: 2013-07-01
forum: Hardware
---

### Post by iNate71 on 2013-07-01
I have an HP Envy Spectre 14 and on Ubuntu, it takes forever to resume from suspend. I have 8GB of RAM and a SS drive--on Windows 7 it takes seconds. I can't seem to find the cause of the issue. I would like to point out though, before I go to sleep, I close my laptop. Occasionally, when I wake up the next morning the laptop's logo on the lid is lit up--this means it's running. I'll open my laptop and it will resume almost instantly. However, when this particular scenario occurs, the laptop is running; (i.e., the fan is working hard, the computer sounds like it's doing some intensive tasks, blah blah blah). I don't know how to replicate that though--it just happens sometimes.

While I'm at it, I can't hibernate Linux. I can hibernate Windows, but not Linux. I'm in Linux almost all the time and would like the ability to hibernate--I know it has something to do with partioning the drives; does it have to do with the Swap Space? Currently, my swap space has about 300mb invested.


All help is appreciated. :)

---

### Post by ajgreeny on 2013-07-01
I have no idea about the suspend problem, but as far as hibernation is concerned, it was disabled in 12.04? and later versions, but it is easy to enable it.
See [http://askubuntu.com/questions/94754/how-to-enable-hibernation](http://askubuntu.com/questions/94754/how-to-enable-hibernation) for details.

I don't know what you mean by "Currently, my swap space has about 300mb invested." but in order to hibernate you need swap space at least as large as your ram, ie 4GB ram needs at least 4GB swap partition.

---

### Post by iNate71 on 2013-07-01
My current swap space size is 300mb, because at the time--I didn't know what that was used for.

---

### Post by ajgreeny on 2013-07-01
OK, so to enable hibernation you will need to follow my previous post and the link to askubuntu, and also increase your swap size to 8GB, same as your ram, which you can only safely do with a live CD/USB and gparted.  Backup everything first, just in case.

---

### Post by iNate71 on 2013-07-02
> **ajgreeny said:**
> OK, so to enable hibernation you will need to follow my previous post and the link to askubuntu, and also increase your swap size to 8GB, same as your ram, which you can only safely do with a live CD/USB and gparted. Backup everything first, just in case.

So I increased my Swap space size to 8GB. I followed the tutorial on how to set up hibernation--however, my computer already had that file configured properly. when I type "sudo pm-hibernate", the computer screen goes black like it's about to hibernate, but then resumes back to what I was doing. It stops hibernating.

---

### Post by stelladeli on 2013-07-02
Hello iNate71, I have an HP Pavilion dv7 with 2GB of RAM and swap space equal to size of RAM. I also experience the same issues. "Suspending" leaves the laptop fan making way too much noise as if I'm working on several tasks and hibernation always fails. Plus all these are not present in Windows.

About the constant "fan noise", from what I've gathered it's due to my graphics AMD Mobility Radeon HD 4650. Ubuntu 12.10 comes with xorg 1.13 and breaks Catalyst 12.9, while AMD has dropped the support for Radeon HD 4000, HD 3000 or HD 2000 graphics cards, leaving a major overheating problem behind. In an attempt to avoid further problems canonical decided to set the power managment profile to "default" with the fan always running.

That leaves me with the question "What graphics do you have?" to see if your problem fits the above description.

As for the hibernation failure, I'm currently on the hunt for a solution too.

---

### Post by Toz on 2013-07-02
Just to put my piece in, there is a log file that might yield some helpful information: /var/log/pm-suspend.log. Please post it back via:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is being generated.

Also helpful might be any error messages dumped into syslog. They can be viewed via:
```
cat /var/log/syslog | grep PM:
```
...feel free to post those back as well.

As for the fan running when the system is suspended, there is a good chance that the system is not in fact suspended, though the screen may be blanked out. Hopefully the log files from above can help identify what is happening.

And one final note, alot of suspend issues are solved by using the proprietary drivers, if they are available. The following command:
```
sudo lspci -vnn | grep -A15 VGA
```
...will identify your video card(s) and they loaded drivers.

---

### Post by stelladeli on 2013-07-02
Toz, your insight is greatly appreciated.

iNate71 also see this thread [http://ubuntuforums.org/showthread.php?t=2107061](http://ubuntuforums.org/showthread.php?t=2107061)

---

### Post by iNate71 on 2013-07-02
> **stelladeli said:**
> Hello iNate71, I have an HP Pavilion dv7 with 2GB of RAM and swap space equal to size of RAM. I also experience the same issues. "Suspending" leaves the laptop fan making way too much noise as if I'm working on several tasks and hibernation always fails. Plus all these are not present in Windows.

About the constant "fan noise", from what I've gathered it's due to my graphics AMD Mobility Radeon HD 4650. Ubuntu 12.10 comes with xorg 1.13 and breaks Catalyst 12.9, while AMD has dropped the support for Radeon HD 4000, HD 3000 or HD 2000 graphics cards, leaving a major overheating problem behind. In an attempt to avoid further problems canonical decided to set the power managment profile to "default" with the fan always running.

That leaves me with the question "What graphics do you have?" to see if your problem fits the above description.

As for the hibernation failure, I'm currently on the hunt for a solution too.

I have Intel's integrated HD 3000 graphics. Whatever is associated with the Ivybridge processing line. I can't remember.

> **Toz said:**
> Just to put my piece in, there is a log file that might yield some helpful information: /var/log/pm-suspend.log. Please post it back via:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is being generated.

Also helpful might be any error messages dumped into syslog. They can be viewed via:
```
cat /var/log/syslog | grep PM:
```
...feel free to post those back as well.

As for the fan running when the system is suspended, there is a good chance that the system is not in fact suspended, though the screen may be blanked out. Hopefully the log files from above can help identify what is happening.

And one final note, alot of suspend issues are solved by using the proprietary drivers, if they are available. The following command:
```
sudo lspci -vnn | grep -A15 VGA
```
...will identify your video card(s) and they loaded drivers.
Pastebinit log:
[http://pastebin.com/9yfwFZJv](http://pastebin.com/9yfwFZJv)

Syslog:
[http://pastebin.com/76YGRaHW](http://pastebin.com/76YGRaHW)

Drivers/cards:
[http://pastebin.com/WyrE36Lp](http://pastebin.com/WyrE36Lp)


Thank you so much for helping me out.

---

### Post by Toz on 2013-07-03
@iNate71, from your log files, I don't see the system ever staying suspended. It looks like it goes into suspend mode but then wakes up right away.

Can you try the following to get cleaner information:

1. Make clean log files:
```
sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
sudo mv /var/log/syslog /var/log/syslog.BAK
```

2. Initiate a suspend:
```
sudo pm-suspend
```

3. Let the system suspend then wait for about 2 minutes. Then, initiate a resume.

4. When the system has resumed, can you please post back the **/var/log/pm-suspend.log** and **/var/log/syslog log** files?

And also, from your original post, how long exactly is "takes forever to resume from suspend"?

---

### Post by iNate71 on 2013-07-03
> **Toz said:**
> @iNate71, from your log files, I don't see the system ever staying suspended. It looks like it goes into suspend mode but then wakes up right away.

Can you try the following to get cleaner information:

1. Make clean log files:
```
sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
sudo mv /var/log/syslog /var/log/syslog.BAK
```

2. Initiate a suspend:
```
sudo pm-suspend
```

3. Let the system suspend then wait for about 2 minutes. Then, initiate a resume.

4. When the system has resumed, can you please post back the **/var/log/pm-suspend.log** and **/var/log/syslog log** files?

And also, from your original post, how long exactly is "takes forever to resume from suspend"?

From a suspension, it takes about 30-45 seconds. On Windows 7, it takes about 5 seconds.

I tried using those commands, but when I get to step 4, it says the file doesn't exist.

---

### Post by Toz on 2013-07-03
> **iNate71 said:**
> I tried using those commands, but when I get to step 4, it says the file doesn't exist.

The commands to run are:
```
pastebinit /var/log/pm-suspend.log
```
...post back the link that is generated, and:
```
cat /var/log/syslog | grep PM:
```
...and post back the results that are displayed.

---

### Post by iNate71 on 2013-07-04
> **Toz said:**
> The commands to run are:
```
pastebinit /var/log/pm-suspend.log
```
...post back the link that is generated, and:
```
cat /var/log/syslog | grep PM:
```
...and post back the results that are displayed.

[http://pastebin.com/Mpeztfci](http://pastebin.com/Mpeztfci)

That was the first one. I typed in the second one, and it didn't work. Said the file didn't exist.

---

### Post by Toz on 2013-07-04
> **iNate71 said:**
> [http://pastebin.com/Mpeztfci](http://pastebin.com/Mpeztfci)

That was the first one. I typed in the second one, and it didn't work. Said the file didn't exist.

Hmmm. Lets try this again with a small change (I'd really like to see the two log files together):

1. Make clean log files:
```

sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
sudo touch /var/log/syslog
```

2. Initiate a suspend:
```

sudo pm-suspend
```

3. Let the system suspend then wait for about 2 minutes. Then, initiate a resume.

4. When the system has resumed, can you please post back:
```
pastebinit /var/log/pm-suspend.log
```
...and 
```
cat /var/log/syslog | grep PM:
```

---

### Post by iNate71 on 2013-07-04
> **Toz said:**
> Hmmm. Lets try this again with a small change (I'd really like to see the two log files together):

1. Make clean log files:
```

sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
sudo touch /var/log/syslog
```

2. Initiate a suspend:
```

sudo pm-suspend
```

3. Let the system suspend then wait for about 2 minutes. Then, initiate a resume.

4. When the system has resumed, can you please post back:
```
pastebinit /var/log/pm-suspend.log
```
...and 
```
cat /var/log/syslog | grep PM:
```

[URL="http://pastebin.com/QF3f70Zc"]http://pastebin.com/QF3f70Zc
[/URL]
The last line returned nothing. I typed it in, then it returned a new line to type a new command. :(

---

### Post by Toz on 2013-07-04
> **iNate71 said:**
> The last line returned nothing. I typed it in, then it returned a new line to type a new command. :(
That is very odd. Can you try one more time with these instructions (slightly modified again)?

1. Make clean log files:
```

sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
sudo chown syslog:adm /var/log/syslog
```

2. Initiate a suspend:
```
sudo pm-suspend
```

3. Let the system suspend then wait for about 2 minutes. Then, initiate a resume.

4. When the system has resumed, can you please post back:
```
pastebinit /var/log/pm-suspend.log
```
...and
```
cat /var/log/syslog | grep PM:
```

Hopefully this time we'll get something.

---

### Post by iNate71 on 2013-07-04
> **Toz said:**
> That is very odd. Can you try one more time with these instructions (slightly modified again)?

1. Make clean log files:
```

sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
sudo chown syslog:adm /var/log/syslog
```

2. Initiate a suspend:
```
sudo pm-suspend
```

3. Let the system suspend then wait for about 2 minutes. Then, initiate a resume.

4. When the system has resumed, can you please post back:
```
pastebinit /var/log/pm-suspend.log
```
...and
```
cat /var/log/syslog | grep PM:
```

Hopefully this time we'll get something.


Well, I don't know what else to do. I tried the command again. Still nothing.

---

### Post by Toz on 2013-07-05
> **iNate71 said:**
> Well, I don't know what else to do. I tried the command again. Still nothing.
```
ls -l /var/log/syslog
```
...and
```
sudo service rsyslog restart
```
...then
```
pastebinit /var/log/syslog
```

---

### Post by iNate71 on 2013-07-05
> **Toz said:**
> ```
ls -l /var/log/syslog
```
...and
```
sudo service rsyslog restart
```
...then
```
pastebinit /var/log/syslog
```


PM-Suspend log
[http://pastebin.com/Q8G3mpGz](http://pastebin.com/Q8G3mpGz)

Syslog
[http://pastebin.com/kXtKeBCi](http://pastebin.com/kXtKeBCi)

---

### Post by Toz on 2013-07-05
Good its working again.

From your pm-suspend.log file, resume takes 1 second, Not bad, except thats not what you're seeing.
```

Fri Jul  5 11:00:22 EDT 2013: Awake.
Fri Jul  5 11:00:22 EDT 2013: Running hooks for resume
.....
Fri Jul  5 11:00:23 EDT 2013: Finished.
```
> From a suspension, it takes about 30-45 seconds. On Windows 7, it takes about 5 seconds.
When you say 30-45 seconds, are you timing just the resume part, or is this the whole suspend/resume cycle?



One other thing that I'm noticing is that from your syslog file, there are a boat load of acpi errors:
> Jul  5 11:00:22 Coder kernel: [63222.714716] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
Jul  5 11:00:22 Coder kernel: [63222.714729] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802138779b0), AE_NOT_FOUND (20120320/psparse-536)
Jul  5 11:00:22 Coder kernel: [63222.715281] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
Jul  5 11:00:22 Coder kernel: [63222.715294] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802138779b0), AE_NOT_FOUND (20120320/psparse-536)

Can you post back the results of this command to show which kernel parameters you are using?
```
cat /proc/cmdline
```

---

### Post by iNate71 on 2013-07-13
> **Toz said:**
> Good its working again.

From your pm-suspend.log file, resume takes 1 second, Not bad, except thats not what you're seeing.
```

Fri Jul  5 11:00:22 EDT 2013: Awake.
Fri Jul  5 11:00:22 EDT 2013: Running hooks for resume
.....
Fri Jul  5 11:00:23 EDT 2013: Finished.
```

When you say 30-45 seconds, are you timing just the resume part, or is this the whole suspend/resume cycle?



One other thing that I'm noticing is that from your syslog file, there are a boat load of acpi errors:


Can you post back the results of this command to show which kernel parameters you are using?
```
cat /proc/cmdline
```


Here is the line you're looking for: ```
BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=438a922f-7bee-4639-8f9d-46c0a0c75115 ro quiet splash vt.handoff=7
```

Also, it takes about 25 seconds from the moment I'm attempting the resume. From the moment I attempt to resume on Windows 7, it takes about 3-5 seconds.

---

### Post by Toz on 2013-07-14
What video card do you have and what driver are you using? This should help:
```
sudo lspci -vnn | grep -A15 VGA
```

---

### Post by iNate71 on 2013-07-15
> **Toz said:**
> What video card do you have and what driver are you using? This should help:
```
sudo lspci -vnn | grep -A15 VGA
```

```
inate@Coder ~ $ sudo lspci -vnn | grep -A15 VGA[sudo] password for inate: 
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:1893]
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f6400000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915


00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: Hewlett-Packard Company Device [103c:1893]
    Flags: bus master, medium devsel, latency 0, IRQ 43
inate@Coder ~ $ 

```

---

### Post by Toz on 2013-07-15
Is it just that the screen stays off, or is the whole system unresponsive during that 25 seconds of resume? Can you go to, and get, a text tty (Ctrl+Alt+F1) anytime during the 25 seconds of resume?

---

### Post by iNate71 on 2013-07-19
> **Toz said:**
> Is it just that the screen stays off, or is the whole system unresponsive during that 25 seconds of resume? Can you go to, and get, a text tty (Ctrl+Alt+F1) anytime during the 25 seconds of resume?

I cannot.

---

### Post by Toz on 2013-07-19
Can you post your entire syslog log file so I can have a look to see if there is anything else there that might indicate why the delay?
```
pastebinit /var/log/syslog
```

---

### Post by iNate71 on 2013-07-20
> **Toz said:**
> Can you post your entire syslog log file so I can have a look to see if there is anything else there that might indicate why the delay?
```
pastebinit /var/log/syslog
```


I feel like the reason of the slow delay is because I can't hibernate. Wouldn't both states save to the same place? I know when you hibernate, it's all saved to the RAM--but if that were the case, I could hibernate easily. I can't even hibernate--when I do, the screen goes black for about 3 seconds, then resumes back to whatever I was doing before I initiated the command.

---

### Post by Toz on 2013-07-20
Actually no. Suspend saves to RAM whereas Hibernate saves to disk (swap). 

It might be a good idea to create a bug report on launchpad for your issue.

---

