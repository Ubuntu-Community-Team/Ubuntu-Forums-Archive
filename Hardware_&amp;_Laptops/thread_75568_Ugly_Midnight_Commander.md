---
title: "Ugly Midnight Commander"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by markthecarp on 2005-10-13
Hi All I posted this last night but it got lost in the forum shuffle.

Midnight Commander, links and lynx display terribly at the console. Virtual console is more correct. I'm doing a Ctr-Alt-F1 and logging in to get to the first virtual console. From there I can Alt-F[1-6] between virtual consoles. I get back to my running X session with Ctr-Alt-F7. I find these apps useful when my Xorg config is broken and server installs with no X at all. The command "mc" will start Midnight Commander.

Yeah it's a bit old school but this stuff really is handy when X is broken. I'm getting the same ugliness on three machines, two hoary>dist-upgrade>breezy and one still hoary.

I've tried changing the console font to no avail.

What other information would be helpful?

Should I post this on another forum?

-mark

---

### Post by Xen2oo6 on 2005-10-18
-- move up --

---

### Post by markthecarp on 2005-10-20
Well I thank you. That was helpful. 

Seriously, on a server box there's no reason to have X installed. It's quite nice to have console apps display correctly on such a box. 

-mark

---

### Post by sunshinerecorder on 2005-10-26
The Problem with the ugly Midnight Commander disappears when you switch from Unicode ("UTF8") to the standard ISO encoding. To do this you have to do the following steps:
% dpkg-reconfigure locales
Here you have to select a non UTF8-Locale in the "Locales to be generated" section (for example "en_US ISO-8859-1"). In the next step you choose one of the new generated locales without UTF8 as your standard.
The last step was to modify /etc/console-tools/config and change the SCREEN_FONT value to SCREEN_FONT=lat0-sun16.

OK, it's not the nicest way to fix this problem but in my case it works.

Christian

---

### Post by HunterCo on 2005-11-22
[QUOTE=sunshinerecorder]The Problem with the ugly Midnight Commander disappears when you switch from Unicode ("UTF8") to the standard ISO encoding. To do this you have to do the following steps:
% dpkg-reconfigure locales
Here you have to select a non UTF8-Locale in the "Locales to be generated" section (for example "en_US ISO-8859-1"). In the next step you choose one of the new generated locales without UTF8 as your standard.
The last step was to modify /etc/console-tools/config and change the SCREEN_FONT value to SCREEN_FONT=lat0-sun16.

OK, it's not the nicest way to fix this problem but in my case it works.

Christian[/QUOTE]
Ah.... it's fixed. Thanks, cause I was having this problem on a few of my machines. Odd that it hasn't been brough up more often, but perhaps there aren't a lot of people out there that use MC.

---

### Post by mckemie on 2005-12-04
[QUOTE=markthecarp]Well I thank you. That was helpful. 

Seriously, on a server box there's no reason to have X installed. It's quite nice to have console apps display correctly on such a box. 

-mark[/QUOTE]

I haven't found any X app that is anywhere near as useful as mc; I use it in xterms as well as vcs.

I have encountered the "ugly mc" problem and was looking for the fix.  Thanks!

---

### Post by deerfieldtech on 2005-12-04
The mc in breezy backports fixes this issue (at least it did for me). It is a known mc limitation, the inablity to handle UTF-8.

If you don't want to get mc from backports, another workaround is to type the command 'unicode_stop' at the command line. It will work then, but you'll have to type this every time you log into a new TTY.

-P

---

### Post by mckemie on 2006-10-03
Well, this problem seems to be in Dapper still.  :-(

Worse, the fixes above seem not to work.  Suggestions?

---

### Post by rootchick on 2006-12-07
Running 'unicode_start' before running mc worked for me.  dpkg-reconfigure didn't let me reconfigure, it just updated the utf8 locales.

---

### Post by fakie_flip on 2007-06-06
What works in Feisty? So far nothing has. This is what my mc looks like and finch.

[http://img183.imageshack.us/img183/9026/hpim1001bh8.jpg](http://img183.imageshack.us/img183/9026/hpim1001bh8.jpg)

[http://img183.imageshack.us/img183/9010/hpim1007zv2.jpg](http://img183.imageshack.us/img183/9010/hpim1007zv2.jpg)

---

### Post by fakie_flip on 2007-06-06
For anyone wondering how to fix this problem in Feisty, look at the thread I started.

[http://ubuntuforums.org/showthread.php?t=465676](http://ubuntuforums.org/showthread.php?t=465676)

---

