---
title: "Simple-scan works in clean install but not in current system"
date: 2014-01-10
forum: Hardware
---

### Post by Diskdoc on 2014-01-10
Hi!

I have a curious problem. **Simple-scan** doesn't work with my scanner anymore. It used to, at some point. My theory was that something is wrong with configs/permissions so I installed the same version of Ubuntu (13.04) with all the updates in Virtualbox and gave it access to the scanner - works like a charm.

But not my "own" system, noo.. It doesn't even work if I run simple-scan as root - the scanner makes a little noise as if starting but then nothing happens. I **checked permissions on /dev/usb/lp0**..looks the same as in Virtualbox. In **/etc/groups** I **belonged to pretty much the same groups**.

**sane-find-scanner** turns up finding nothing. Running it with sudo gives some weird **"could not fetch string descriptor: Pipe error"** errors. On Virtualbox, running as user the result is the same (nothing found). Running with sudo just gives the same nothing found result, the Pipe errors are not coming up!

**xsane** just seems to hang, looking for devices. On Virtualbox, it quickly finds the scanner.

Can anyone help me debug this and find out what's wrong? I'd prefer fixing this by locating the error than by reinstalling Ubuntu.

*edit*

I just realised the Virtualbox installation was running 13.04. Will upgrade and try again.

---

### Post by kurt18947 on 2014-01-10
I cannot give specific advice but had a similar problem a couple years ago with Xsane.  My solution to my problem was to delete a .sane config file in the user's home directory.  The file was then automatically rebuilt with default settings and all was well.

---

### Post by IsmAvatar on 2014-01-10
Having the exact same issue that I posted here:
[http://ubuntuforums.org/showthread.php?t=2198658](http://ubuntuforums.org/showthread.php?t=2198658)
Did not find a .sane config file in my home directory.

$ pwd && ls -a | grep sane
/home/ismavatar
$

---

### Post by Diskdoc on 2014-01-10
Well, I installed 13.10 in Virtualbox but the result is the same as before - that is, the fresh installation scans perfectly. I removed the .sane directory in my real system but it didn't make a difference. In simple-scan the scanner is shown when looking at the simple-scan preferences in Virtualbox, but not so in my real install.

---

### Post by Diskdoc on 2014-01-10
I tried starting simple-scan with the -d parameter and here is the result:

For the virtualbox installation:

[I]"diskdoc@diskdoc-VirtualBox:~$ simple-scan -d
[+0,00s] DEBUG: simple-scan.vala:582: Starting Simple Scan 3.10.0, PID=2248
[+0,00s] DEBUG: Connecting to session manager
[+0,14s] WARNING: g_object_set_valist: invalid object type 'GtkAdjustment' for value type 'GtkWidget'
[+0,15s] DEBUG: ui.vala:1513: Restoring window to 600x400 pixels
[+0,16s] DEBUG: autosave-manager.vala:332: Adding an autosave for a new page
[+0,20s] DEBUG: autosave-manager.vala:332: Adding an autosave for a new page
[+0,28s] DEBUG: scanner.vala:1431: sane_init () -> SANE_STATUS_GOOD
[+0,29s] DEBUG: scanner.vala:1437: SANE version 1.0.23
[+0,29s] DEBUG: scanner.vala:1498: Requesting redetection of scan devices
[+0,29s] DEBUG: scanner.vala:776: Processing request
[+0,38s] DEBUG: autosave-manager.vala:383: Updating the autosave for a page
[+3,15s] DEBUG: scanner.vala:338: sane_get_devices () -> SANE_STATUS_GOOD
[+3,15s] DEBUG: scanner.vala:350: Device: name="epson2:libusb:001:004" vendor="Epson" model="CX5000" type="flatbed scanner"
[+10,73s] DEBUG: autosave-manager.vala:189: Clean exit; deleting autosave records
[+10,79s] DEBUG: scanner.vala:1571: Stopping scan thread
[+10,79s] DEBUG: scanner.vala:776: Processing request
[+10,83s] DEBUG: scanner.vala:1582: sane_exit ()"[/I]

For my system:

[I]"diskdoc@sector7:~$ simple-scan -d
[+0,03s] DEBUG: simple-scan.vala:582: Starting Simple Scan 3.10.0, PID=18611
[+0,03s] DEBUG: Connecting to session manager
[+2,26s] WARNING: g_object_set_valist: invalid object type 'GtkAdjustment' for value type 'GtkWidget'
[+2,27s] DEBUG: ui.vala:1513: Restoring window to 600x400 pixels
[+2,37s] DEBUG: autosave-manager.vala:332: Adding an autosave for a new page
[+2,66s] DEBUG: autosave-manager.vala:332: Adding an autosave for a new page
[+3,30s] DEBUG: autosave-manager.vala:383: Updating the autosave for a page
[+3,36s] DEBUG: scanner.vala:1431: sane_init () -> SANE_STATUS_GOOD
[+3,36s] DEBUG: scanner.vala:1437: SANE version 1.0.23
[+3,36s] DEBUG: scanner.vala:1498: Requesting redetection of scan devices
[+3,36s] DEBUG: scanner.vala:776: Processing request
[+27,53s] DEBUG: autosave-manager.vala:189: Clean exit; deleting autosave records
[+27,78s] DEBUG: scanner.vala:1571: Stopping scan thread"[/I]

(I exited simple-scan myself since it didn't detect anything)

---

### Post by Diskdoc on 2014-01-10
Tried reinstalling libusb* and libsane*..didn't help. I get the feeling it might be some kind of permission-problem..but if so, why doesn't it work when running simple-scan as root?

Maybe the next step is trying to understand what scanner.vala does? Can anyone help me with that?

[https://github.com/mnagel/simple-scan/blob/master/src/scanner.vala]("https://github.com/mnagel/simple-scan/blob/master/src/scanner.vala")

*later*

I checked the permissions and ownership on the usb device that comes up, it matches with that on Virtualbox.

Also tested scanimage -T. Works in Virtualbox, not in system.

One difference between these two is that Virtualbox installation is 32-bit, system 64-bit.. Could it matter?

---

### Post by Diskdoc on 2014-01-11
Tried > apt-get install --reinstall --purge xsane simple-scan libgusb2 libusb-0.1-4 libusb-0.1-4:i386 libusb-1.0-0 libusb-1.0-0:i386 libusbmuxd2 libsane libsane-common sane-utils xsane-common
 but didn't help.

---

### Post by Diskdoc on 2014-01-12
Tried 64-bit version in Virtualbox, finding the scanner worked like a charm so it's not a 32/64-bit issue.

---

### Post by Diskdoc on 2014-01-13
I solved it!! For whatever reason, purging and reinstalling packages didn't reinstall them properly. Only when I did:

> sudo apt-get -o DPkg::Options::="--force-confmiss" --reinstall install libsane

and on simple-scan, libusb-1.0-0, libusb-0.1-4 have I finally solved the problem. PHEW! Tough one.

---

