---
title: "random restarts"
date: 2008-10-10
forum: General Help
---

### Post by Buster95 on 2008-10-10
Using Hardy 8.04 on a desktop.

Experiencing random restarts. Two happened today. the first with my daughter was using Firefox 3.0.3. The second was while I was reading posts to this forum (using FF 3.0.3 again).

Yesterday, I also experienced two restarts. The first while using GIMP 2.6, GRAMPS 3.0.2-1 and FF 3.0.3; the second while using Open Office 2.4 Writer only. No browser or other application was open.

I'd attach the /var/log/messages and /var/log/syslog outputs, except that they are very long and I don't know how to insert a large paste into a window within this post.

I'm not sure what to look for and would appreciate some guidance.

---

### Post by Buster95 on 2008-10-16
Still happening every few days.
two uninvited restarts within the last hour. The first was with Open office Writer and no other program or browser running. It got about halfway through the restart and restarted again. It's now been running OK for an hour.

Here is a paste of a few line of the log outputs around the time of the first restart at 11:42:05. The second restart didn't seem to register on the log.

/var/log/syslog

Oct 17 11:30:36 HOME-DESKTOP NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 17 11:30:36 HOME-DESKTOP NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct 17 11:30:38 HOME-DESKTOP hald: mounted /dev/sdb5 on behalf of uid 1000 
Oct 17 11:34:25 HOME-DESKTOP ntpd[5357]: synchronized to 91.189.94.4, stratum 2 
Oct 17 11:34:25 HOME-DESKTOP ntpd[5357]: kernel time sync status change 0001 
Oct 17 11:42:05 HOME-DESKTOP syslogd 1.5.0#1ubuntu1: restart. 
Oct 17 11:42:05 HOME-DESKTOP kernel: Inspecting /boot/System.map-2.6.24-21-generic
.... etc, etc - no warnings or errors.



/var/log/messages

Oct 17 11:30:11 HOME-DESKTOP kernel: [   43.316448] [drm] Initialized drm 1.1.0 20060810 
Oct 17 11:30:11 HOME-DESKTOP kernel: [   43.318894] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16 
Oct 17 11:30:11 HOME-DESKTOP kernel: [   43.318959] [drm] Initialized i915 1.6.0 20060119 on minor 0 
Oct 17 11:42:05 HOME-DESKTOP syslogd 1.5.0#1ubuntu1: restart. 
Oct 17 11:42:05 HOME-DESKTOP kernel: Inspecting /boot/System.map-2.6.24-21-generic

.... etc, etc nothing dodgy here either


Have I got a hardware problem?

What should I be looking for?

Cheers

---

### Post by firfin on 2008-10-23
Hi ,
I am experiencing similar problems. Although in my case it probably isnt a hardware problem as I'm dualbooting the system and windows doesn't experience spontaneous random restarts. It happens when working on it and also when it's going into idle.
Nothing in my syslog or messages to indicate a problem either.

Any other clues on where to look?

I checked here: but that wasn't very useful unfortunately.
[http://ubuntuforums.org/showthread.php?t=403635&highlight=spontaneous+reboot](http://ubuntuforums.org/showthread.php?t=403635&highlight=spontaneous+reboot)

---

### Post by Buster95 on 2008-10-23
In my case, the restarts seem to be entirely random. Haven't experienced one after two hours running today.

I had also previously dug up the post you referred to. However, it's primarily focused on hardware malfunction. My desktop is a bog-standard commercial unit that I have never tampered with. It has been running well for a year or so and the random restart issue only raised its ugly head a few weeks ago.

While a component failure in the bowels of the machine is entirely possible, it seems to me a lot less likely than some unsavoury interaction with recent synaptic updates (I load them all up).

Like you, I'm hoping for some ideas from some of the gurus on this forum, for some insights on where to look.

Cheers

---

### Post by Buster95 on 2008-10-26
More information:

The most recent restart seemed to be associated with a cron event. This time, Firefox was running (but nothing else).
The pasted extracts from the logs follow.

/var/log/messages

[COLOR="Red"]Oct 27 08:53:40 HOME-DESKTOP syslogd 1.5.0#1ubuntu1: restart.[/COLOR] 
Oct 27 09:08:34 HOME-DESKTOP -- MARK -- 
Oct 27 09:28:34 HOME-DESKTOP -- MARK -- 
Oct 27 09:48:34 HOME-DESKTOP -- MARK -- 
Oct 27 10:08:34 HOME-DESKTOP -- MARK -- 
[COLOR="Red"]Oct 27 10:25:16 HOME-DESKTOP syslogd 1.5.0#1ubuntu1: restart.[/COLOR] 
Oct 27 10:25:17 HOME-DESKTOP kernel: Inspecting /boot/System.map-2.6.24-21-generic
... etc, etc

/var/log/syslog

[COLOR="Red"]Oct 27 08:45:33 HOME-DESKTOP syslogd 1.5.0#1ubuntu1: restart. [/COLOR]
Oct 27 08:45:33 HOME-DESKTOP anacron[5711]: Job `cron.daily' terminated 
Oct 27 08:45:33 HOME-DESKTOP anacron[5711]: Job `cron.weekly' started 
Oct 27 08:45:33 HOME-DESKTOP anacron[6939]: Updated timestamp for job `cron.weekly' to 2008-10-27 
[COLOR="Red"]Oct 27 08:53:40 HOME-DESKTOP syslogd 1.5.0#1ubuntu1: restart. [/COLOR]
Oct 27 08:53:40 HOME-DESKTOP anacron[5711]: Job `cron.weekly' terminated 
Oct 27 08:53:40 HOME-DESKTOP anacron[5711]: Normal exit (2 jobs run) 
Oct 27 09:08:34 HOME-DESKTOP -- MARK -- 
Oct 27 09:17:01 HOME-DESKTOP /USR/SBIN/CRON[7537]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly) 
Oct 27 09:28:34 HOME-DESKTOP -- MARK -- 
Oct 27 09:32:24 HOME-DESKTOP gdm[7721]: WARNING: Login sound requested on non-local display or the play software cannot be run or the sound does not exist. 
Oct 27 09:48:34 HOME-DESKTOP -- MARK -- 
Oct 27 10:08:34 HOME-DESKTOP -- MARK -- 
Oct 27 10:17:01 HOME-DESKTOP /USR/SBIN/CRON[9227]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly) 
[COLOR="Red"]Oct 27 10:25:16 HOME-DESKTOP syslogd 1.5.0#1ubuntu1: restart. [/COLOR]
Oct 27 10:25:17 HOME-DESKTOP kernel: Inspecting /boot/System.map-2.6.24-21-generic

The /var/log/messages file didn't retain the first restart record, but it is captured in the syslog file. The 4 "MARK" records appear to be at exactly 20 minute intervals with the restart occurring 20 minutes after the last.
The /var/log/syslog record seems to be associating a cron event to the failures, but other than that, there are no errors or failures recorded.

Can anybody help me interpret this better? I'm rather puzzled.

---

