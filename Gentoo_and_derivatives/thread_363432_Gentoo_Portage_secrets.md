---
title: "Gentoo Portage secrets"
date: 2007-02-16
forum: Gentoo and derivatives
---

### Post by RAV TUX on 2007-02-16
I came across this article, I thought it may help those new to Gentoo/Sabayon:)

> **[B]Gentoo Portage secrets**[/B]

  Friday August 11, 2006 (08:01 AM GMT)
  By: [Aleksey Alekseyev]("mailt:%67%6f%74%6c%65%74%74%65%72%40%67%6d%61%69%6c%2e%63%6f%6d")
   Gentoo Linux is perhaps the most-used source-based Linux distribution. One secret to its success is the powerful and handy Portage package management system. While Gentoo comes with extensive documentation covering most aspects of using Portage, the techniques described in Gentoo's handbook and other documentation are not always the most effective ones. Here are some insider tips that can greatly increase your productivity. 
                                   document.write('<script type=&quot;text/javascript&quot; src=&quot;http://ad.doubleclick.net/adj/ostg.linux/mainpage_p6_imu;pg=article;logged_in=0;tile='+dfp_tile+';tpc=distrocenter;tpc=gentoo;tpc=news;ord='+dfp_ord+'?&quot;><\/script>');     dfp_tile++;  
          
        
 **Search faster** 
  Before you install a package, you usually look for it via Portage's search capabilities. Portage's emerge utility has --search and --searchdesc options, but using them is not enjoyable, because they take a long time to run. That's why we've seen the emergence of third-party search front ends for Portage, such as [esearch]("http://david-peter.de/esearch.html") and [eix]("http://dev.croup.de/proj/eix"). Their common idea is to use their own search indexes to speed up searches. When using either utility, you have to rebuild the index after updating the Portage tree, and after installing and uninstalling software. 
  Of the two, eix works faster and has more capabilities. You can get information on the utility from its man page or by invoking eix --help. To use eix to search for a package whose name contains foo, simply invoke eix foo. 
  Eix is a very flexible tool. It can give you more information on packages than esearch or emerge -s. It can search through different fields (e.g. package name, category, or description), it can search for regular expressions or wildcard patterns, or do fuzzy searches, and its output can be configured for use in scripts.
   **Optimizing traffic usage** 
  Updating your software can take a lot of network bandwidth. There are tools that help you decrease Portage's appetite. The most effective and well-known such tool is [Deltup]("http://deltup.sourceforge.net/"), which allows you to download deltas, or the differences between new and old versions of package source. That approach can save you up to 90% of the download size. The procedure for installing deltup is [described]("http://gentoo-wiki.com/HOWTO_Install_Deltup") in the Gentoo wiki. 
  Using Deltup has its drawbacks, however. Deltup will not resume fetching a delta if you lose a connection. Sometimes, the server generating the deltas is overloaded, and you must wait for a long time for it to generate your delta. Sometimes Deltup gets confused about which versions of packages you have. And, of course, generating a new package takes some CPU time. Still, Deltup should not break your system, so you should not be afraid to give it a try.
  KDE maintainers generate the deltas for their packages themselves. [This HOWTO]("http://gentoo-wiki.com/HOWTO_Update_KDE_without_downloading_full_sources") describes using these deltas in Gentoo. There was a period when Portage supported a kdexdeltas USE flag, so you did not need to patch your sources manually, but after KDE 3.5 this functionality was not updated, so the kdexdeltas flag will not give you any advantage these days. Note that if you receive errors that report "digest verification failed" when using manually updated KDE sources, you can still install new KDE packages by using the emerge --digest command. 
  You can use the power of deltas not only when updating source packages, but also when updating your Portage tree. Emerge-delta-webrsync allows you to download daily patches to the Portage tree, which is less traffic-consuming than using emerge --sync. Just invoke emerge emerge-delta-webrsync, and next time you need to sync your Portage tree, run emerge-delta-webrsync 
  The Gentoo wiki provides [more tips]("http://gentoo-wiki.com/TIP_Gentoo_for_dialup_users") for users with poor Internet connections.
  A new feature that came in Portage 2.1 can also help speed downloads. If you add the string parallel-fetch to the FEATURES variable in /etc/make.conf, emerge will download some packages' source code while compiling others that are in the queue. This reduces installation time, especially if you emerge many packages.
   **Faster package compilation** 
  Every time you install or update some software under Gentoo, you need to wait until its source is compiled. Portage supports a set of tools that try to decrease the compiling time of your packages.
  One of the ways to speed up compilation on a slow machine is to distribute the compiling task to another host. This is what [Distcc]("http://www.gentoo.org/doc/en/distcc.xml") aims to do. You can even use [Windows boxes]("http://gentoo-wiki.com/HOWTO_Distcc_server_on_Windows") to assist in the task.
   [Ccache]("http://gentoo-wiki.com/Ccache") makes it possible to speed up compilation of the same code by caching compilation results. Confcache is a similar tool for caching results of test configuration scripts (./configure). It appeared at the same time as Portage 2.1, and still lacks full documentation, but it has been [mentioned in the Gentoo Linux Newsletter]("http://www.gentoo.org/news/en/gwn/20060619-newsletter.xml#doc_chap5"). After spending some time in the unstable branch, it is now hardmasked, which means that confcache has some unresolved issues; if you try using the current confcache version (0.4.2) you will sometimes need to install some packages with the confcache feature turned off, or clean the confcache cache (rm -rf /var/tmp/confcache).
  All the tools mentioned in this section can be used for any compilation tasks. See the appropriate documentation for [Distcc]("http://distcc.samba.org/"), [ccache]("http://ccache.samba.org/"), and confcache (coming later).
   **Managing logs and configuration files** 
  Another new feature in Portage 2.1 is the new logging framework. Many packages show notices while you emerge them, but you may not see them if you do not watch the emerge process. Now you just need to turn on elog, by adding these lines to /etc/make.conf:
  # This sets what to log
 PORTAGE_ELOG_CLASSES="warn error log"
 # And this is how to do it
 PORTAGE_ELOG_SYSTEM="save"
  and creating the /var/log/portage/elog directory. Now, each package's emerge log will be saved in a separate file in the specified directory. You can find more info on configuring elog by inspecting the /etc/make.conf.example file. There are already GTK and QT [graphical front ends]("http://forums.gentoo.org/viewtopic-t-465493.html") for viewing these logs.
  After updating some packages you sometimes need to update their configuration files. The standard tool for this is etc-update, but there is a more handy and advanced utility -- [dispatch-conf]("http://gentoo-wiki.com/Dispatch-conf"). It automatically updates configuration files that have easy changes to comments, or that have not been changed between updates. It also allows you to redo any changes you made to configuration files by placing them into a version control system.
   **Would you like to know more?** 
  If these few brief tips have whetted your appetite, you can learn more about most aspects of Portage from its [handbook]("http://www.gentoo.org/doc/en/handbook/index.xml"), [official documentation]("http://www.gentoo.org/doc/en/index.xml"), and the [Gentoo wiki]("http://gentoo-wiki.com/Main_Page"). If you have any further questions, you may find an answer on the [Gentoo forums]("http://forums.gentoo.org/").
[http://www.linux.com/article.pl?sid=06/08/07/1952207](http://www.linux.com/article.pl?sid=06/08/07/1952207)

---

### Post by mysticrider92 on 2007-02-18
I am going to have to try some of that. The more I try to use Ubuntu, the more I want Gentoo back. :D

---

### Post by FyreBrand on 2007-02-26
Oh RAV-TUX once again you are a life saver.  I have had insane portage nightmares.  I don't understand masking, layman, and some other things.  Those refs should really help.

I was trying to configure and install a basic development LAMP stack.  I kept breaking everything and hosing up the system trying to get PHP to talk to MySQL.  Oh well.  Once school is over and have the time and luxury to experiment I will definitely give this another whirl.  3.3 should be out by then too. :)

---

### Post by zaratustra on 2007-02-26
if you want to unmask something, let say banshee media player... lets say that it is masked by keyword (~x86), and hardmaksed([M])... to unmask keywordmask
```
echo "media-sound/banshee" >> /etc/portage/package.keywords
```

to unmask the hardmask

```
echo "media-sound/banshee" >> /etc/portage/package.unmask
```

if you maybe want to mask a package which isn't masked by portage

```
echo "media-sound/banshee" >> /etc/portage/package.mask
```

if there are no mentioned files, create them

*** 

Layman is a small script which will add overlays to portage... Overlays are ebuilds which aren't in standard portage tree. In other words, layman is a script which helps you to break your system. Joking, but, if these overlay were stable, they would be in portage tree, so do not expect rock-solid apps. 


you can see here how is it used to merge beryl version which isn't in portage

[http://ubuntuforums.org/showpost.php?p=2206849&postcount=9](http://ubuntuforums.org/showpost.php?p=2206849&postcount=9)

---

