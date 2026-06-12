---
title: "Firefox hangs continually"
date: 2008-10-17
forum: General Help
---

### Post by linucks42 on 2008-10-17
Hi,

I've had the problem with Firefox hanging for between 2-30 seconds every time I initiate a new action every since I installed Kubuntu on my eee pc.

Opening a new tab, scrolling, selecting from options in a menu, clicking on a link, actually much pretty much anything causes firefox to freeze for a few seconds.

As you might imagine this is intensely annoying.

The hang is firefox-specific, as there is no notable increase in cpu usage while firefox is hanging and other applications continue to be responsive.

I've disabled all the plugins and the behaviour is the same.

I've tried using konqueror instead, and although this has it's own problems (e.g. I can't view my gmail account or log into my web-based outlook mail) it doesn't exhibit the same 'stuttering' behaviour.

Can anyone suggest what might be causing this?

Further details on my setup are below.

Many thanks!

Jens

Firefox: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3
Kubuntu 8.04
KDE 4.1.2

---

### Post by emil on 2008-10-27
Hi,

I had the exact same problem with Firefox 3, used to hang several seconds between any user actions. Driving me crazy!

Found the solution on the forum though:
[http://ubuntuforums.org/showthread.php?t=900154]("http://ubuntuforums.org/showthread.php?t=900154")

Disable all disk-caches and problem goes away.

/Emil

---

### Post by linucks42 on 2008-10-29
Hi Emil,

Thanks for the response.

Just to clarify things in case anyone else is following this, I understand your suggestion to be that I type "about:config" in the Firefox status bar to bring up the config editor and change the boolean "browser.cache.disk.enable" value to "false".

In the end I uninstalled firefox-3.0 and installed firefox 2, and was using that with no problems.

Following your email I reinstalled firefox 3.0 and was going to follow your suggestion, but have actually found that things appear to be working o.k. at the moment.

When it was failing, I ran firefox under gdb, and it always seemed to be hanging in a call within the xul-runner library. When I re-installed firefox, it seemed to have updated xul-runner, so I can only guess that this update fixed the problem.

Thanks again for your advice,

Jens

---

### Post by sag47 on 2010-06-08
I have this problem too.  My firefox hangs on any website which runs any type of JavaScript.  I'm running Firefox 3.6.3 on Kubuntu 10.04 LTS.

Disabled all my add-ons and plugins.
Using the default theme.
Set browser.cache.disk.enable = false
Set network.http.pipelining = false
Disabled loading images.
Disabled JavaScript (the problem was resolved after disabling the JavaScript engine for all websites)

I even vacuumed all of my databases using sqlite3 from the terminal (which is what the newer firefox versions are using in their databases).
```
for x in `find ~ -type f -name *.sqlite* | grep firefox`;do echo "$x";sqlite3 $x VACUUM;done
```

None of that seems to work.  I can't just run my browser with JavaScript disabled permanently on all websites.  I downloaded Firefox 3.6.4 beta and installed it into /opt/ and still running into the same problem (starting it via terminal using /opt/firefox/firefox.

Any ideas anybody?  Here's some more sysinfo about my distro...
```
$ cat /etc/issue
Ubuntu 10.04 LTS \n \l

$ uname -a
Linux megaman 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
```

Hardware:
Intel Core i7-920 2.66GHz
6GB DDR3 1066 (PC3 8500) Triple Channel
nVidia GeForce GT 240 1GB 128bit GDDR3 (using proprietary nVidia driver in Kubuntu)

Running firefox from the terminal does not output any exceptions or errors.
I can reproduce the problem when loading the following websites every time.
[http://www.newegg.com/](http://www.newegg.com/) (Firefox hangs ~40s each time I load the main page)
[http://www.yahoo.com/](http://www.yahoo.com/) (Firefox hangs ~45s each time I load the main page)

I press Ctrl+T when it starts hanging and when it finishes its hang it opens a new tab (that's how I timed it).

I'm sure there are many others but I've just been using those two as test sites for the issue.  There's no good reason Firefox should be freezing on my system.

I've been looking for a solution for a couple of weeks now so I decided enough is enough and filed a bug.
[https://bugzilla.mozilla.org/show_bug.cgi?id=570792](https://bugzilla.mozilla.org/show_bug.cgi?id=570792)

---

