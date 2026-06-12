---
title: "RAD 7.5.4 doesn't start on Karmic Koala"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by asif.mkhan on 2009-11-09
I upgraded to 9.10 a couple of weeks a ago and installed RAD 7.5.4. The installation went smooth, but it doesn't start. I had installed the RAD 7.5 on Jaunty and it used to work fine, so it has to be something in upgrade that is failing.

The workbench seems to be loading fine, but then fails with the message.

/home/xxx/IBM/rationalsdp/workspace/.metadata/.log

The error log doesn't say much, I have attached it below in case it is helpful.

!SESSION 2009-11-06 10:45:39.493 -----------------------------------------------
eclipse.buildId=unknown
java.fullversion=J2RE 1.6.0 IBM J9 2.4 Linux x86-32 jvmxi3260sr5ifx-20090821_41076 (JIT enabled, AOT enabled)
J9VM - 20090821_041076_lHdSMr
JIT  - r9_20090518_2017
GC   - 20090417_AA
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.ui.workbench 4 0 2009-11-06 10:45:50.689
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(Unknown Source)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(Unknown Source)
	at org.eclipse.swt.widgets.EventTable.sendEvent(Unknown Source)
	at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
	at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
	at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
	at org.eclipse.swt.widgets.Widget.release(Unknown Source)

---

### Post by alexander. on 2009-11-11
Hi!

I had the same issue with RSA 7.5.4 and found the workaround at [http://employees.org/~abhinav/blog/2009/10/getting-eclipse-3-4-x-working-on-ubuntu-karmic-beta/]("http://employees.org/%7Eabhinav/blog/2009/10/getting-eclipse-3-4-x-working-on-ubuntu-karmic-beta/") :

'To get this working, just add the following to **eclipse.ini** on a separate line:[INDENT]-Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner
[/INDENT]Where /usr/lib/xulrunner is the location of version 1.9'


It worked for me fine :D

---

### Post by hamidoo on 2009-12-06
it just works!
much appreciated alex :)
cheers

---

### Post by yogig on 2012-11-06
Thanks a bunch, Alex. It worked like a charm! :KS

> **alexander. said:**
> Hi!

I had the same issue with RSA 7.5.4 and found the workaround at [http://employees.org/~abhinav/blog/2009/10/getting-eclipse-3-4-x-working-on-ubuntu-karmic-beta/]("http://employees.org/%7Eabhinav/blog/2009/10/getting-eclipse-3-4-x-working-on-ubuntu-karmic-beta/") :

'To get this working, just add the following to **eclipse.ini** on a separate line:[INDENT]-Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner
[/INDENT]Where /usr/lib/xulrunner is the location version 1.9'


It worked for me fine :D

---

### Post by wildmanne39 on 2012-11-06
Old thread closed.

---

