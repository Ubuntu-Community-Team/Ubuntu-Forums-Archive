---
title: "update notification not working?"
date: 2008-11-08
forum: General Help
---

### Post by sderrick on 2008-11-08
The Update icon never appears in the upper panel when updates are available.

The Update Notifier is in the sessions list and is listed as a running process?

I tried removing and re-installing it and that didn't change the behavior.

help!

Scott

---

### Post by boddhisatva on 2008-11-17
Got the same problem. Have to update manually. 
No-one seems to reply to threads about this problem...

---

### Post by drs305 on 2008-11-17
The area on the panel where the icon normally appears when updates are available is called the 'Notification Area'. Make sure this is installed on your panel: Right click the panel, Add to Panel, 'Notification Area'.

---

### Post by boddhisatva on 2008-11-17
> **drs305 said:**
> The area on the panel where the icon normally appears when updates are available is called the 'Notification Area'. Make sure this is installed on your panel: Right click the panel, Add to Panel, 'Notification Area'.

Notification area is on - I've got Skype, IM, network status, and screenlets icons there. But the update icon never appears like it used to in Hardy. I made a fresh install of Intrepid and since then I don't think the notifier has appeared once.

---

### Post by icanfly0307 on 2008-11-17
> **boddhisatva said:**
> Notification area is on - I've got Skype, IM, network status, and screenlets icons there. But the update icon never appears like it used to in Hardy. I made a fresh install of Intrepid and since then I don't think the notifier has appeared once.

Maybe there aren't any updates available? Intrepid is pretty new so the development team might still be working on more updates.

---

### Post by boddhisatva on 2008-11-17
> **icanfly0307 said:**
> Maybe there aren't any updates available? Intrepid is pretty new so the development team might still be working on more updates.

There have been updates. I've had to check and install them manually.
The update notifier DEFINITELY ISN'T WORKING.

---

### Post by the_duality on 2008-11-17
Ditto here - I have to use sudo apt-get update every day to make sure I don't miss anything. And more often than not, I have missed something.

---

### Post by drs305 on 2008-11-17
While I was trying to research your problem I opened gconf-editor. I went to /apps/update-notifier. I have a listing for default_action and the value is 2. Oddly (to me at least) there is no explanation below about what that status means. But I'll just put it out there that I have this setting, the value is 2, and I get notified of potential updates.

---

### Post by boddhisatva on 2008-11-18
> **drs305 said:**
> While I was trying to research your problem I opened gconf-editor. I went to /apps/update-notifier. I have a listing for default_action and the value is 2. Oddly (to me at least) there is no explanation below about what that status means. But I'll just put it out there that I have this setting, the value is 2, and I get notified of potential updates.

Yeah, I forgot to mention I had also checked that key and there was no explanation, and it said something like "this key has no scheme" (I don't know the actual English phrasing as I'm translating from Polish) so I removed it. I've now put it back in with the value you mentioned (I don't remember what it was before I removed it). We'll see, although I suspect it may have been 2 as well.
Anyway, I'll let you know if it has changed anything.
Thanks

---

### Post by kostkon on 2008-11-18
Could you check for updates using the *Update Manager* (*System &#8594; Administration &#8594; Update Manager*)? Do you get any errors? Maybe there is a problem with your sources.list file.

---

### Post by boddhisatva on 2008-11-18
> **kostkon said:**
> Could you check for updates using the *Update Manager* (*System &#8594; Administration &#8594; Update Manager*)? Do you get any errors? Maybe there is a problem with your sources.list file.

I'm checking regularly and installing updates manually. No problem, the Update Manager is working fine. But even when I turn the Update Manager on, there is no icon on the panel.
Actually, there are some important updates at this very moment, but there is no notification (so changing values in gconf-editor hasn't helped either).

---

### Post by kostkon on 2008-11-22
Do you think that [this bug]("https://bugs.edge.launchpad.net/ubuntu/+source/update-notifier/+bug/135262") applies to your case? Try to do what comment #4 recommends.

---

### Post by boddhisatva on 2008-11-26
> **kostkon said:**
> Do you think that [this bug]("https://bugs.edge.launchpad.net/ubuntu/+source/update-notifier/+bug/135262") applies to your case? Try to do what comment #4 recommends.

Thanks for the link. I'm afraid it doesn't help - I removed the file, yet no notification appears, despite a long list of applications waiting for an update.

---

### Post by ZioLupo on 2009-01-30
The same problem here.
Notification area is on. Update are available. If I run manually ```
sudo apt-get update
``` everything is fine and then the "red exclamation mark" magically appear in the notification area.

I hate it!

---

### Post by boddhisatva on 2009-01-30
I also have Kubuntu installed, and there the icon appears all right. So it must be a Gnome problem.

---

### Post by kostkon on 2009-01-30
Do what is suggested [here]("http://ubuntuforums.org/showthread.php?p=6365984#post6365984"), i.e.:
First of all, do a
```
ls -l /etc/cron.daily/
```
and see if the *apt* script file has 755 permissions. 
The permissions for the *apt* file should be like this
```
-rwxr-xr-x
```
If not, do a
```
sudo chmod 755 /etc/cron.daily/apt
```
to give it execute permissions.

It should then work fine. You'll start getting update notifications again.

Hope that helps.

---

### Post by boddhisatva on 2009-01-31
Doesn't seem to help. I don't know enough about linux commands - where does it say how many permissions there are? I'm pasting the result of "ls -l /etc/cron.daily/" ("razem" means "altogether")

razem 48
-rwxr-xr-x 1 root root  311 2008-09-03 01:37 0anacron
-rwxr-xr-x 1 root root  219 2008-10-24 08:10 apport
-rwxr-xr-x 1 root root 7680 2008-08-14 18:55 apt
-rwxr-xr-x 1 root root  314 2008-09-02 14:50 aptitude
-rwxr-xr-x 1 root root  502 2007-12-12 14:59 bsdmainutils
-rwxr-xr-x 1 root root   89 2008-10-09 09:11 logrotate
-rwxr-xr-x 1 root root  954 2008-07-11 17:02 man-db
-rwxr-xr-x 1 root root  646 2008-06-26 16:17 mlocate
-rwxr-xr-x 1 root root 1154 2009-01-06 16:55 ntp
-rwxr-xr-x 1 root root 3349 2008-09-09 21:46 standard
-rwxr-xr-x 1 root root 1309 2008-08-30 02:40 sysklogd

---

### Post by yang on 2010-08-04
Also seeing this problem on 10.04. The suggestions on the thread so far weren't it for me. Anyone know where I should inspect to start debugging this issue?

---

### Post by sderrick on 2010-08-04
Interesting twist on the problem.

I'm running 10.04 on a laptop.

Garbled notification panel.  I switched my theme to Dust from the default of Ambiance.  No more garbled panel.  

The icons don't appear in the same order and shift positions at almost every reboot, but all the icons are present, recognizable and accessible.

Not the best work around but it does work.

I don't know if that is a valuable clue as to the problem or not.

Scott

---

