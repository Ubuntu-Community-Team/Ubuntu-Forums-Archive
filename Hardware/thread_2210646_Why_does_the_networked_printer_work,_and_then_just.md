---
title: "Why does the networked printer work, and then just stop working?"
date: 2014-03-11
forum: Hardware
---

### Post by Gustav_Toppa on 2014-03-11
I'm perplexed because I have been printing to the Ethernet networked printer since about November of last year, and the same thing keeps happening, time and time and time again.
While I print daily from the Windows laptop on the same network to the networked printer on 192.168.1.116, I don't print often from the Ubuntu 13.10 laptop - but, almost invariably, when I try to print from the laptop to that same networked printer, I have to set up the network printing, again. (*and again, and again, and again, and again, ad infinitum*).

That is, the Ubuntu networked printing works just fine, after I set it up using the default Ubuntu "printers" widget.
Then, I do nothing for, oh, about a week or three.

Then, when I want to print from Ubuntu to the networked printer again, nothing happens.
No overt error. Just no paper results.
The windows machine on the same network happily prints with aplomb so it's not likely to be the printer.
But the Linux printer will only print soon after I set it up. 
Then it goes dumb.

I then type "printer" in the dashboard search, and click on the "printers" icon, and I set it up yet again, for all the defaults for an HP LaserJet 2100 printer.
Then I can print. Until next time.

*NOTE: The printer is a _wired printer with a static IP address_ (of 192.168.1.116). There is an Ethernet cat5 patch cable going directly from the home broadband router to the HP LJ2100 printer.*

My question?
** What on earth is changing to kill networked printing in between duplicate printing setups?**
[ATTACH=CONFIG]251060[/ATTACH]

---

### Post by tgalati4 on 2014-03-11
Look in /var/log/cups for errors.  If you do any kernel updates, sometimes the printers need to be deleted and recreated.  This sounds like it is happening more often than that.  Did you install the printer through *hp-toolbox*?

Open a terminal:

```
hp-toolbox
```

Sometimes the printer needs to be awake to accept prints.  You can check the printer status through *hp-toolbox* or *hp-info*.

---

### Post by Gustav_Toppa on 2014-03-11
> **tgalati4 said:**
> Look in /var/log/cups for errors.  

Thanks to the pointer for errors. 
That cups log directory is chock full of something.
```

$ ls -ltr /var/log/cups
total 76
-rw-r----- 1 root adm  185 Dec 21 06:55 error_log.7.gz
-rw-r----- 1 root adm  185 Dec 22 07:46 error_log.6.gz
-rw-r----- 1 root adm  184 Dec 23 08:01 error_log.5.gz
-rw-r----- 1 root adm  226 Dec 24 23:07 error_log.4.gz
-rw-r----- 1 root adm  185 Dec 25 07:56 error_log.3.gz
-rw-r----- 1 root adm  184 Dec 26 08:02 error_log.2.gz
-rw-r----- 1 root adm  230 Feb  5 09:35 access_log.7.gz
-rw-r----- 1 root adm  330 Feb  5 13:28 access_log.6.gz
-rw-r----- 1 root adm  205 Feb  7 17:04 access_log.5.gz
-rw-r----- 1 root adm  273 Feb 10 18:22 access_log.4.gz
-rw-r----- 1 root adm  146 Feb 17 16:07 access_log.3.gz
-rw-r----- 1 root adm  176 Feb 25 04:44 error_log.1.gz
-rw-r----- 1 root adm  148 Feb 25 06:34 access_log.2.gz
-rw-r----- 1 root adm  146 Mar  7 23:12 access_log.1.gz
-rw-r----- 1 root adm  493 Mar 11 18:20 page_log
-rw-r----- 1 root adm 3034 Mar 11 18:40 access_log
-rw-r----- 1 root adm 9217 Mar 11 18:45 error_log

```

At the moment, there are no errors in the error_log simply because I set up the printer again, so it's working (but it wasn't working prior to that just an hour ago).
It printed about 5 jobs that I hand't known were "stuck", but I see them at the top of the error_log file:
```

$ head error_log
W [11/Mar/2014:18:16:36 -0700] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Hewlett-Packard-HP-LaserJet-2100-Series-Gray..' already exists
E [11/Mar/2014:18:16:36 -0700] Hewlett-Packard-HP-LaserJet-2100-Series: File "/usr/lib/cups/backend/hp" not available: No such file or directory
E [11/Mar/2014:18:16:36 -0700] [Job 4] Stopping job because the sheduler could not execute the backend.
E [11/Mar/2014:18:16:48 -0700] Hewlett-Packard-HP-LaserJet-2100-Series: File "/usr/lib/cups/backend/hp" not available: No such file or directory
E [11/Mar/2014:18:16:48 -0700] [Job 5] Stopping job because the sheduler could not execute the backend.
E [11/Mar/2014:18:16:48 -0700] Hewlett-Packard-HP-LaserJet-2100-Series: File "/usr/lib/cups/backend/hp" not available: No such file or directory
E [11/Mar/2014:18:16:48 -0700] [Job 6] Stopping job because the sheduler could not execute the backend.
E [11/Mar/2014:18:16:52 -0700] Hewlett-Packard-HP-LaserJet-2100-Series: File "/usr/lib/cups/backend/hp" not available: No such file or directory
E [11/Mar/2014:18:16:52 -0700] [Job 7] Stopping job because the sheduler could not execute the backend.
E [11/Mar/2014:18:16:54 -0700] Hewlett-Packard-HP-LaserJet-2100-Series: File "/usr/lib/cups/backend/hp" not available: No such file or directory
E [11/Mar/2014:18:16:54 -0700] [Job 8] Stopping job because the sheduler could not execute the backend.
E [11/Mar/2014:18:17:00 -0700] Hewlett-Packard-HP-LaserJet-2100-Series: File "/usr/lib/cups/backend/hp" not available: No such file or directory
E [11/Mar/2014:18:17:00 -0700] [Job 9] Stopping job because the sheduler could not execute the backend.
E [11/Mar/2014:18:17:15 -0700] Hewlett-Packard-HP-LaserJet-2100-Series: File "/usr/lib/cups/backend/hp" not available: No such file or directory
E [11/Mar/2014:18:17:15 -0700] [Job 10] Stopping job because the sheduler could not execute the backend.
W [11/Mar/2014:18:17:44 -0700] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Hewlett-Packard-HP-LaserJet-2100-Series-Gray..' already exists

```

Then, when I set up the printer (again, for the umpteenth time), it worked just fine (and all the long stalled jobs printed which were spooled up weeks ago).

Here's a cat of the temporary "access_log" file when in the middle of a subsequent print (after setting up the printer for the umpteenth time):
```

$ cat access_log
localhost - - [11/Mar/2014:18:28:07 -0700] "POST / HTTP/1.1" 200 151 Cancel-Subscription successful-ok
localhost - - [11/Mar/2014:18:39:35 -0700] "POST /printers/Hewlett-Packard-HP-LaserJet-2100-Series HTTP/1.1" 200 447640 Print-Job successful-ok
localhost - - [11/Mar/2014:18:39:46 -0700] "POST / HTTP/1.1" 200 251 Create-Printer-Subscription successful-ok
localhost - - [11/Mar/2014:18:40:08 -0700] "POST /printers/Hewlett-Packard-HP-LaserJet-2100-Series HTTP/1.1" 200 278 Print-Job successful-ok
localhost - - [11/Mar/2014:18:40:52 -0700] "POST / HTTP/1.1" 200 151 Cancel-Subscription successful-ok
localhost - - [11/Mar/2014:19:11:23 -0700] "POST /printers/Hewlett-Packard-HP-LaserJet-2100-Series HTTP/1.1" 200 21066 Print-Job successful-ok

```


> **tgalati4 said:**
> Did you install the printer through *hp-toolbox*?
I have never heard of "hp-toolbox".
I installed the printer drivers so long ago that I don't remember how I did it, but I think I just used the Ubuntu dashboard printer icon and set it up by clicking on all the defaults for that printer.

I just checked. Hp-toolbox was never installed:
```

$ hp-toolbox
The program 'hp-toolbox' is currently not installed. You can install it by typing:
sudo apt-get install hplip-gui

```

So, I'll install it, and, hopefully, it might tell me something about WHY the printer setup chews itself up all the time.
[ATTACH=CONFIG]251063[/ATTACH]

---

### Post by varunendra on 2014-03-11
I'll bug out with just this one post, please see if this thread can help : [http://ubuntuforums.org/showthread.php?t=2208459](http://ubuntuforums.org/showthread.php?t=2208459)

---

### Post by Gustav_Toppa on 2014-03-12
> **varunendra said:**
> see if this thread can help : [http://ubuntuforums.org/showthread.php?t=2208459](http://ubuntuforums.org/showthread.php?t=2208459)

It does seem to be a somewhat similar issue - but not the same.

In that thread, the OP was having a problem that their wireless printer was dropping out from visibility such that it was "unable to be found" so they used a static URI to resolve the problem.
In my case, it's a networked printer (not a wireless printer) so it already has a static uri; and, it's found - but - it errors out with "/usr/lib/cups/backend/hp" No such file or directory.

Anyway, my current workaround is to re-install the printer drivers each time I want to print. 
That works. It's just inexplicable why I have to do that every few weeks when I want to print.

In the meantime, I'll see if installing and settings up the hp-toolbox solves the problem of the cups backend hp file constantly disappearing:
:[ATTACH=CONFIG]251064[/ATTACH]

---

### Post by Gustav_Toppa on 2014-03-12
The only anomaly I've noted, so far, after setting up the printer using the hp-toolbox, is that now there are TWO (duplicate) printers when I bring up the default Ubuntu 13.10 printers GUI:
1. The first printer I see was the one repeatedly set up using the default Ubuntu printer gui.
2. The second was set up using the recently suggested hp-toolbox gui.

I'll leave them both, for now, but the first seems to be "hung" with a "waiting for printer" message, while the second seems to work just fine (even though there is only one printer on the network).
[ATTACH=CONFIG]251065[/ATTACH][ATTACH=CONFIG]251066[/ATTACH]

---

### Post by kurt18947 on 2014-03-12
As I noted in the other thread, the default 'printers' app is  ....... limited (I'm being nice;)).  The old "system-config-printer" app is much more informative and useful.  If not installed by default, it's available in the repositories.  I have no experience with the HP printer tools so I'm no help there.

---

