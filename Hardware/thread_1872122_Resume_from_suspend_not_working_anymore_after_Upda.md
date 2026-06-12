---
title: "Resume from suspend not working anymore after Update to 11.10 (acpi_sleep=nonvs)"
date: 2011-10-30
forum: Hardware
---

### Post by Neocult on 2011-10-30
Hi there,

the update to 11.10 runs quite smoothly on every laptop, but on my Sony Vaio SR-21M Ihave a suspend issue I could not fix. In all previous versions of Ubuntu I just add acpi_sleep=nonvs in /etc/default/grub to get suspend mode working properly. But not anymore.

The only error I could find in pm-suspend.log was:
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

But I personally think that is not the issue. I tried the suspend mode from a freshly Ubuntu from Thumbdrive, but then it is a complete restart of the computer instead of resuming.

I hope someone have ideas or further instructions how to handle this. Thank you in advance.

Best regards,
Neocult

---

### Post by Toz on 2011-11-04
What exactly happens when you try to resume - shutdown? blank screen? reboot? blinking LEDs? Can you Ctrl+Alt+F1 and get a text screen? If so, what happens when you Ctrl+Alt+F7 to go back to the GUI?

Perhaps you could post the full contents of your pm-suspend.log file along with the results of:
```
cat /var/log/syslog* | grep PM:
```

---

### Post by o771 on 2011-11-05
I have what appears to be the same problem as the base note, on a clean install of 11.10 on a Samsung X360. From the initial installation, suspend/resume worked perfectly. Then resume stopped working. I'd accepted a bunch of updates in the time between when it last worked and when I noticed it was broken, but none of them looked obviously suspicious. 

The symptoms are:

1. Suspend appears to work correctly, with the usual LED behaviour.
2. When resume is initiated using the power switch, I get a black back-lit screen.
3. The system doesn't respond to any key combinations I've tried (incl. Ctrl+Alt+F1)
4. The only thing it responds to is the power switch, and a reboot.
5. I've also tried leaving it for a few minutes to see if it comes back, but it doesn't.

The full pm-suspend.log is too big to upload, but it does have messages  from when resume was working, and after it stopped. When it was working,  a typical sequence of entries around suspend/resume looked like this:

...
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Nov  3 09:12:13 GMT 2011: performing suspend
Thu Nov  3 13:03:14 GMT 2011: Awake.
Thu Nov  3 13:03:14 GMT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
...

After it stopped working, "performing suspend" is never followed by an 'Awake' entry. E.g.:

...
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Nov  5 21:10:34 GMT 2011: performing suspend
<EOF>

Whatever is supposed to invoke the resume actions doesn't seem to be doing so.

Entries from syslog are:

kevin@mutter:~$ cat /var/log/syslog* | grep PM:
Nov  5 20:39:01 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Nov  5 20:39:01 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  5 20:39:01 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Nov  5 20:39:01 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Nov  5 20:39:01 mutter kernel: [    0.166107] PM: Registering ACPI NVS region at bdb54000 (307200 bytes)
Nov  5 20:39:01 mutter kernel: [    0.934914] PM: Hibernation image not present or could not be loaded.
Nov  5 21:02:21 mutter kernel: [ 1403.706455] PM: Syncing filesystems ... done.
Nov  5 21:02:21 mutter kernel: [ 1403.716373] PM: Preparing system for mem sleep
Nov  5 21:04:11 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Nov  5 21:04:11 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  5 21:04:11 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Nov  5 21:04:11 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Nov  5 21:04:11 mutter kernel: [    0.166111] PM: Registering ACPI NVS region at bdb54000 (307200 bytes)
Nov  5 21:04:11 mutter kernel: [    0.943216] PM: Hibernation image not present or could not be loaded.
Nov  5 21:06:26 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Nov  5 21:06:26 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  5 21:06:26 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Nov  5 21:06:26 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Nov  5 21:06:26 mutter kernel: [    0.162112] PM: Registering ACPI NVS region at bdb54000 (307200 bytes)
Nov  5 21:06:26 mutter kernel: [    0.935125] PM: Hibernation image not present or could not be loaded.
Nov  5 21:10:34 mutter kernel: [  250.930804] PM: Syncing filesystems ... done.
Nov  5 21:10:34 mutter kernel: [  250.948051] PM: Preparing system for mem sleep
Nov  5 21:12:06 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Nov  5 21:12:06 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  5 21:12:06 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Nov  5 21:12:06 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Nov  5 21:12:06 mutter kernel: [    0.162112] PM: Registering ACPI NVS region at bdb54000 (307200 bytes)
Nov  5 21:12:06 mutter kernel: [    0.939234] PM: Hibernation image not present or could not be loaded.
Nov  4 15:35:12 mutter kernel: [14259.973750] PM: Syncing filesystems ... done.
Nov  4 15:35:12 mutter kernel: [14260.053024] PM: Preparing system for mem sleep
Nov  4 15:42:50 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Nov  4 15:42:50 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  4 15:42:50 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Nov  4 15:42:50 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Nov  4 15:42:50 mutter kernel: [    0.162110] PM: Registering ACPI NVS region at bdb54000 (307200 bytes)
Nov  4 15:42:50 mutter kernel: [    0.923232] PM: Hibernation image not present or could not be loaded.
Nov  4 21:48:56 mutter kernel: [21973.386183] PM: Syncing filesystems ... done.
Nov  4 21:48:56 mutter kernel: [21973.417403] PM: Preparing system for mem sleep
Nov  4 21:54:01 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Nov  4 21:54:01 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  4 21:54:01 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Nov  4 21:54:01 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Nov  4 21:54:01 mutter kernel: [    0.162109] PM: Registering ACPI NVS region at bdb54000 (307200 bytes)
Nov  4 21:54:01 mutter kernel: [    0.930884] PM: Hibernation image not present or could not be loaded.
Nov  4 21:58:45 mutter kernel: [  293.212418] PM: Syncing filesystems ... done.
Nov  4 21:58:45 mutter kernel: [  293.217916] PM: Preparing system for mem sleep
Nov  4 22:00:44 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Nov  4 22:00:44 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  4 22:00:44 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Nov  4 22:00:44 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Nov  4 22:00:44 mutter kernel: [    0.162108] PM: Registering ACPI NVS region at bdb54000 (307200 bytes)
Nov  4 22:00:44 mutter kernel: [    0.930881] PM: Hibernation image not present or could not be loaded.
Nov  4 22:01:16 mutter kernel: [   38.236112] PM: Syncing filesystems ... done.
Nov  4 22:01:16 mutter kernel: [   38.244054] PM: Preparing system for mem sleep
Nov  4 22:02:30 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Nov  4 22:02:30 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  4 22:02:30 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Nov  4 22:02:30 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Nov  4 22:02:30 mutter kernel: [    0.162107] PM: Registering ACPI NVS region at bdb54000 (307200 bytes)
Nov  4 22:02:30 mutter kernel: [    0.935260] PM: Hibernation image not present or could not be loaded.
Nov  4 22:51:32 mutter kernel: [ 2947.401945] PM: Syncing filesystems ... done.
Nov  4 22:51:32 mutter kernel: [ 2947.408269] PM: Preparing system for mem sleep
Nov  5 15:33:54 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Nov  5 15:33:54 mutter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  5 15:33:54 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Nov  5 15:33:54 mutter kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Nov  5 15:33:54 mutter kernel: [    0.162113] PM: Registering ACPI NVS region at bdb54000 (307200 bytes)
Nov  5 15:33:54 mutter kernel: [    0.939038] PM: Hibernation image not present or could not be loaded.
kevin@mutter:~$

I'd welcome any ideas. Not having suspend/resume is a real pain.

---

### Post by Toz on 2011-11-06
@o771, What video card do you have? Are you using the proprietary driver? 

I would try enabling extra debugging to see what comes up. In a terminal window, try this:
```
export PM_DEBUG=true
sudo pm-suspend
```
This will dump __alot__ of extra information into your pm-suspend.log file. You can post the log file to a place like pastebin via:
```
cat /var/log/pm-suspend.log | pastebinit
```
...and post back the link that is generated.

---

### Post by o771 on 2011-11-07
> **toz said:**
> what video card do you have? Are you using the proprietary driver? 

Mobile Intel® GM45 Express Chipset x86/MMX/SSE2. AFAIK, it's using the default driver. 

> i would try enabling extra debugging to see what comes up. In a terminal window, try this:```
export pm_debug=true
sudo pm-suspend
```this will dump __alot__ of extra information into your pm-suspend.log file.It didn't seem to be any more verbose than usual, but the result is at [http://paste.ubuntu.com/731157/](http://paste.ubuntu.com/731157/) But what's more curious is that suspend/resume done this way worked, and has continued to work subsequently, even when initiated by closing the lid. I've done a fresh reboot and I am now unable to reproduce the problem. (If it reoccurs, I'll be back... )

AFAIK, I haven't made any config changes. Though I'm fairly certain that something must have changed because telepathy has now stopped working, reporting: > There was an error while trying to connect to the Telepathy Account Manager. The error was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.I can't think how the two things could be related, but it's an interesting coincidence that suspend/resume seems to have started working at the same time empathy stopped.

Thanks for your help.

---

### Post by Toz on 2011-11-08
My bad. The commands should of have been:
```
export PM_DEBUG=true
sudo pm-suspend
```

Interesting indeed.

---

### Post by Walter Bux on 2011-12-23
> **Toz said:**
> My bad. The commands should of have been:
```
export PM_DEBUG=true
sudo pm-suspend
```Interesting indeed.

I am running LinuxMint 12 (Ubuntu Oneirc codebase), and I can confirm this interesting phenomenon. I had the same problem (blank screen with blinking cursor after resume), enabled debugging, and it's working now.

I have no explanation.

---

### Post by Walter Bux on 2011-12-30
Update: it stopped working, and repeating the mysterious setting of PM_DEBUG isn't doing it anymore.

Interestingly, tuxonice (external suspend-to-disk driver) stops working with suspend-to-ram. When I got s2ram back, Toi worked again, and when s2ram stopped working, Toi did, too.

---

### Post by matthisd on 2012-02-03
Hi!

I have exactly the same problem, also with tuxonice. Its very sporadic in that resume does not always hang, but about 50% of the time. I also see the error with wpa supplicant, which is very strange as I am using a Dell Desktop without a wireless card (!?).
I am also getting this right before the wpa error:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

Were you able to find a solution to the problem?

lg
Matthis

---

### Post by iainmcc on 2012-02-08
I have an Acer Aspire One netbook. Intel GME945 video, default driver, Broadcomm STA wireless proprietary driver.

Installed Xubuntu stuff over top of standard Ubuntu install, removed the hidden scrollbar things.

Yesterday, it gave me a blank screen on resume. Backlit, blank, power LED turned green, wifi led came on, HD blinked a few times.

Suspend for A short time is fine. If I leave it sleeping for a while, I get the blank screen thing.

Also, this morning, I turned the machine on, and went to do other stuff while it booted. I came back to find the machine on, but the screen was blank. The only keystroke that did anything meaningful was holding the power button for 4 seconds.

Perhaps this has more to do with a screen blanker than with suspend?

---

### Post by ohana on 2012-05-23
Same problem ON a Dell Latitude D600 running Ubuntu 12.04 LTS. Fresh install. 

The symptoms are identical: resume seems to execute perfectly, even with the LED functioning properly, and is confirmed by the lack of any errors in /var/log/pm-suspend.log other than NetworkManager which succeeded after a second try.

I am using a non-PAE kernel. 

Not giving up on this.

---

### Post by bamdad.khan on 2012-12-26
i'm on a hp g62 and i experience the same issues as the op, but only after my laptop has been in a suspended state for more than or about 20 minutes.

has *anyone* found any solution to this? i'm having this since oneiric, now i'm on 12.04..

---

