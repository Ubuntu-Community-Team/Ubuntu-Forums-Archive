---
title: "Eclipse hangs on exit in futex"
date: 2008-11-10
forum: General Help
---

### Post by pshotton on 2008-11-10
Since installing Intrepid, my Eclipse session hangs on exit. All windows close normally but the process doesn't die. strace shows the following:

futex(0x9632b58, 0x80 /* FUTEX_??? */, 2

The only solution is to kill -9 the process; straight kill does not work.
I've done a clean install of Eclipse, new workspace, started with -clean option, but still no joy. If I run as root the process exits normally.

I'm also having problems with certain pop-up windows in Eclipse - probably unrelated but maybe not. Things like:

java.lang.ArrayIndexOutOfBoundsException: -1
        at org.eclipse.jface.viewers.AbstractTableViewer$VirtualManager.resolveElement(AbstractTableViewer.java:100)

and

org.eclipse.swt.SWTException: Failed to execute runnable (java.lang.ArrayIndexOutOfBoundsException: -1)
        at org.eclipse.swt.SWT.error(SWT.java:3777)

Anyone come across this?
Cheers
Phil

---

### Post by fharms on 2008-11-12
I had the exact same problem after I upgraded my Ubuntu to 8.10 64bit and Eclipse 3.4.1.

I found this bug that describe the problem and a workaround

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=240033](https://bugs.eclipse.org/bugs/show_bug.cgi?id=240033)

"I confirm that switching off the "Assistive Technologies" ((GNOME) Menu ->
System -> Preferences -> Assistive Technologies -> checkbox "Enable Assistive
Technologies") is a good workaround for this problem."

Cheers
Flemming

---

### Post by pshotton on 2008-11-12
Yep. Turning off Assistive Technologies does the trick. Eclipse is fine now. Not sure why AT was on in the first place - I must have enabled it accidentally while playing with all the new stuff in Intrepid.

Many thanks
Phil

---

### Post by acorrigan on 2009-07-27
it may be a workaround... but what about those of us who need AT enabled?

---

### Post by pmorch on 2011-01-04
This is still the case in Lucid. Today this did the trick for me.

---

### Post by Gatemaze on 2011-03-01
Really? Cause in my case they are already disabled and I am still getting these problems... all of the sudden after an update...

---

### Post by chromis on 2011-05-05
Having this issue on Natty 64bit and Eclipse 3.6.2...  hanging randomly and having to kill it ..seeing futex_wait_queue_me

---

### Post by baitisj on 2012-03-09
... and this issue still exists on Maverick with Eclipse 3.5.2-6ubuntu1. Thanks for posting information about the workaround. :KS

---

