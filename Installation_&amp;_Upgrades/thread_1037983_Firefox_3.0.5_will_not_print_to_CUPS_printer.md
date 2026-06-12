---
title: "Firefox 3.0.5 will not print to CUPS printer"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by maclenin on 2009-01-12
I just happened upon this (perhaps not only) Firefox 3.0.5 printing issue a few days ago, and after having upgraded my HP 6910p laptop from Feisty to Intrepid.

Essentially, I cannot print from Firefox 3.0.5 via CUPS 1.3.9 to my networked HP 1320 printer. Most other applications (including Thuderbird 2.0.0.19) print to the printer without issue.

The other non-printing applications I've tested are Evince (which will not print to the printer) and GIMP (which will not print to the printer).

I receive no error prompt from Firefox when trying to print to the printer - and the document does not print.
I receive no error prompt from GIMP when trying to print to the printer - and the document does not print.

When trying to print from Evince, I receive this prompt...

> Failed to print document
Can't prompt for authorization

...and this CUPS error_log message is common to the printing issues in Firefox and Evince and GIMP:

> E [12/Jan/2009:09:39:16 -0500] Print-Job: Unauthorized

A (closely-related) bug report has been submitted to [_launchpad_]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/226227").

I had no issues printing in Feisty (with a nearly identical - but for Intrepid - configuration).
I did install [_hplip_]("http://hplipopensource.com/hplip-web/index.html") in Feisty (which I did not do in Intrepid). However, I think hplip - the HP printer driver - is incorporated into ubuntu by default and therefore does not need to be re-installed? Is this correct?

Any thoughts?

---

### Post by bbrg548 on 2009-01-15
I'm having a similar issue. I noticed it a few weeks ago, but haven't had time to do anything with it.

When I try to print from Firefox (3.0.5 now, but I had the same issue with the previous version I had, which I think was 3.0.3), I get the print dialog box, but it's blank. The dialog box won't close, and Firefox locks up. Other programs work, but I have to force-quit Firefox.


Firefox info from the "about" screen is:
Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.0.5) Gecko/2008120121 Firefox/3.0.5

I'm on an HP Pavilion dv9500, AMD Turion 64x2 processor.
Ubuntu 8.04 Hardy Heron
Kernel (per Conky) is 2.6.24-22-generic
cupsys is 1.3.7-1ubuntu3.2

---

### Post by cariboo on 2009-01-16
have either of you logged into cups, to see what the error log says? To do so open your browser and in the address bar type:

```
http://localhost:631
```

Jim

---

### Post by maclenin on 2009-01-16
**cariboo907:**

I have posted a snippet from the CUPS "error_log" in my initial post (above), as well as selections from the CUPS "error_log" and CUPS "access_log" in my post at [_launchpad_]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/226227").

Thanks for any ideas!

---

### Post by bbrg548 on 2009-01-18
> **cariboo907 said:**
> have either of you logged into cups, to see what the error log says? To do so open your browser and in the address bar type:

```
http://localhost:631
```

Jim

I assume you mean to do this in Firefox? When I do, I don't get anything, it just keeps trying to load.

-Jake

---

### Post by maclenin on 2009-01-19
> **bbrg548 said:**
> I assume you mean to do this in Firefox? When I do, I don't get anything, it just keeps trying to load.

-Jake

**bbrg548:**

Just to make certain you are entering the localhost address correctly - i.e. with no spaces and such - copy and paste the following into your Firefox search bar...

```
http://localhost:631/
```

...this should open the CUPS home page - assuming CUPS is installed.

Also, you can check to see whether your CUPS service is (installed) running using the following command in your terminal...

```
service cups status
```

...you should see something similar to:

> Status of Common Unix Printing System: cupsd is running.

If nothing appears, take a look at the Synaptic Package Manager (Applications - System - Synaptic Package Manager) to see whether CUPS is marked as installed.

As for the "lead" printing issue - ideas from anyone re: "Unauthorized" printing are still welcome!

---

### Post by unutbu on 2009-01-19
Regarding the "Failed to print document - can't prompt for authorization" error, according to [https://bugs.launchpad.net/libgtk/+bug/305030](https://bugs.launchpad.net/libgtk/+bug/305030)
> 
GTK+ developers confirm this is a known limitation that should be fixed at some point. Don't know when, though.

Work on the issue seems to be going on here:
[http://bugzilla.gnome.org/show_bug.cgi?id=384940](http://bugzilla.gnome.org/show_bug.cgi?id=384940)

---

### Post by maclenin on 2009-01-19
Thanks **unutbu**. Are you experiencing similar issues?

I also see the following CUPS error_log message...

> E [19/Jan/2009:13:12:28 -0500] [Job 23] Session setup failed: NT_STATUS_LOGON_FAILURE

...when I attempt to print test pages from CUPS. The test pages DO print despite the error.

Wondering whether all of these printing errors/anomalies are related to your GTK+ bug....

Just for on-going reference, these are the error-generating/non-printing applications/processes from within Intrepid 8.10 via CUPS 1.3.9 to a Windows 2000 workstation-attached HP 1320 printer:

1. Firefox 3.0.5
2. Evince 2.24.1
3. Gimp 2.6
4. Test page via CUPS 1.3.9

Thanks, again, for shedding a bit of light.

---

### Post by bbrg548 on 2009-01-21
> **maclenin said:**
> **bbrg548:**

Just to make certain you are entering the localhost address correctly - i.e. with no spaces and such - copy and paste the following into your Firefox search bar...

```
http://localhost:631/
```

...this should open the CUPS home page - assuming CUPS is installed.


Still the same.

> **maclenin said:**
> 
Also, you can check to see whether your CUPS service is (installed) running using the following command in your terminal...

```
service cups status
```



I get:

```
/usr/bin/service: 5: /etc/init.d/cups: not found
```

But when I check through the menus: System/Administration/Services - it shows "Printer service (cupsys)" as active.

> **maclenin said:**
> 

If nothing appears, take a look at the Synaptic Package Manager (Applications - System - Synaptic Package Manager) to see whether CUPS is marked as installed.


It looks like all the CUPS packages are installed. Additionally, Firefox is the *only* application I've found that I can't print from. I can print a test page, I've printed from OpenOffice, Thunderbird, and gedit, without any problems. :-k

-Jake

---

### Post by unutbu on 2009-01-21
maclenin, I'm not experiencing this issue myself. 

Using:```

% firefox --version
Mozilla Firefox 3.0.5, Copyright (c) 1998 - 2008 mozilla.org
% lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

```

---

### Post by tiggsy on 2009-01-24
It took weeks for me to finally get an answer to a corrupt cupsys upgrade, which had become a security issue in the meantime.

Now my printer won't print pdf from document viewer, though I can print from Open Office, and i can print test pages.

I need to print from pdf - it's step one of a course i'm doing. Tried this (can't see where I got it from) with results shown:

```
 service cups status
The program 'service' can be found in the following packages:
 * debian-helper-scripts
 * sysvconfig
Try: sudo apt-get install <selected package>
bash: service: command not found
tiggsy@tiggsys-desktop:~$ sudo apt-get install service
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package service

```

cups is installed 1.3.7-1ubuntu3.3 which is shown as the latest version.

the printer is the default (only) printer in Default Printer. Access control in Printing is set to "Allow printing for everyone except these users:" and there are no users in the list.

Although I have sent a pdf for print three times, it does not appear in the list shown at [http://localhost:631](http://localhost:631) under Jobs->Show All Jobs, although the test page does, and so does the page I printed from Open Office. So it looks as if the print command is not even reaching the printer.

SOLVED (so far as printing pdfs goes): I tried opening the pdf in Adobe Reader, and printed from there - it worked.!!

---

### Post by JackSpratt on 2009-02-15
Found this solution on the internet for this problem after looking everywhere, and it worked!

1. Turn root account on:
**sudo passwd root**

2. Change to the root user
**su**

3. Change to this directory
**cd /etc/gtk-2.0**

4. Create this file with these contents:
**cat > gtkrc** then type this **gtk-print-backends = "lpr,file"**

5. Hit enter then Ctrl+d to end the file and write it.

6. Disable root account:
**sudo passwd -l root**

Close and re-open firefox if it was open and then you should be able to print to "lpr" from it!

---

### Post by bbrg548 on 2009-02-15
This fixed it for me! Thanks!

> **JackSpratt said:**
> Found this solution on the internet for this problem after looking everywhere, and it worked!

1. Turn root account on:
**sudo passwd root**

2. Change to the root user
**su**

3. Change to this directory
**cd /etc/gtk-2.0**

4. Create this file with these contents:
**cat > gtkrc** then type this **gtk-print-backends = "lpr,file"**

5. Hit enter then Ctrl+d to end the file and write it.

6. Disable root account:
**sudo passwd -l root**

Close and re-open firefox if it was open and then you should be able to print to "lpr" from it!

---

### Post by maclenin on 2009-03-01
Thanks **JackSpratt**!

I had success implementing your suggestion...though in a slightly different fashion:

1. From the terminal change into the gtk-2.0 directory...
```
cd /etc/gtk-2.0
```

2. Use sudo (vs. "su" because you don't need to "disable" sudo after you invoke it - sudo times-out (by default) after 5 minutes of non-use) and a text editor (my editor of choice is "nano") to create the gtkrc file in the /etc/gtk-2.0 directory...
```
sudo nano gtkrc
```

3. Add the following to your newly-created gtkrc file...
```
gtk-print-backends="lpr,file"
```

4. Exit the text editor (by following the instructions along the bottom of the nano window, if nano is your choice) and save your newly-created gtkrc file.

5. Re-start your computer to incorporate the changes.

6. Happy printing!

Thanks, again, for the find!

P.S. A couple of contextual bits regarding JackSpratt's work-around and sudo (vs. su):

re: [_gtkrc_]("http://www.linuxquestions.org/questions/linux-desktop-74/firefox-3-cannot-print-to-cups-printer-655002/")
re: _[sudo (vs. su)]("https://help.ubuntu.com/community/RootSudo")_

---

### Post by bkline on 2009-05-29
[Ubuntu bug #283811]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/283811") may be related to your problem (I'm bitten, too).

---

### Post by maclenin on 2009-05-30
Thanks, **bkline**, for adding your discussion to the list! I had, actually, forgotten about the problem (as I have not been experiencing it of late - after having followed **JackSpratt**'s suggestion)! One quick note: I have a recently-installed Intrepid/CUPS arrangement on a desktop - and from which I have been able to print without issue (or need for a fix)...

...perhaps still a wee bit shy, but no longer bitten!

---

