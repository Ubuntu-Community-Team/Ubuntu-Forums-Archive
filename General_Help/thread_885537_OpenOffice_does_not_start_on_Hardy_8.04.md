---
title: "OpenOffice does not start on Hardy 8.04"
date: 2008-08-10
forum: General Help
---

### Post by R8N on 2008-08-10
I am new to Ubuntu and Linux (installed Ubuntu 8.04 48 hours ago) and have a problem. I have tried to look through the forum to see if someone has had the same problem before but had no luck. If I missed an important thread I would be grateful for a link or some directions.

My problem:

When I try to start OpenOffice from the menu I see the splash screen for about half a second and then nothing. If I use the terminal and type soffice of soffice -writer this is what I get:

R8N:~$ sudo soffice 
/usr/lib/openoffice/program/soffice.bin: relocation error: /usr/lib/openoffice/program/libfwi680li.so: symbol _ZN4cppu18&#65533;PropertySetHelper16setPropertyValueERKN3rtl8OUStringERKN3com3sun4star3uno3AnyE, version UDK_3_0_0 not defined in file libuno_cppuhelpergcc3.so.3 with link time reference

I need some ideas what to do here. Are there someone that has experienced similar problems or have any idea what I can do?

I have tried to rename the .openoffice.org2 folder but that didn't help. 

Any ideas?

Thanks in advance.

---

### Post by phorgan1 on 2008-08-29
> **R8N said:**
> I am new to Ubuntu and Linux (installed Ubuntu 8.04 48 hours ago) and have a problem. I have tried to look through the forum to see if someone has had the same problem before but had no luck. If I missed an important thread I would be grateful for a link or some directions.

My problem:

When I try to start OpenOffice from the menu I see the splash screen for about half a second and then nothing. If I use the terminal and type soffice of soffice -writer this is what I get:

R8N:~$ sudo soffice 
/usr/lib/openoffice/program/soffice.bin: relocation error: /usr/lib/openoffice/program/libfwi680li.so: symbol _ZN4cppu18&#65533;PropertySetHelper16setPropertyValueERKN3rtl8OUStringERKN3com3sun4star3uno3AnyE, version UDK_3_0_0 not defined in file libuno_cppuhelpergcc3.so.3 with link time reference

I need some ideas what to do here. Are there someone that has experienced similar problems or have any idea what I can do?

I have tried to rename the .openoffice.org2 folder but that didn't help. 

Any ideas?

Thanks in advance.

I'm having exactly the same problem in Hardy.  I've used openoffice for years!  Everything's always worked fine but some update in the last couple of weeks has screwed the pooch.  I get a glimpse of the splash screen, then it's gone.  Running from the command line gets no output.  I did apt-get remove "openoffice*", went into Synaptic and reinstalled the core and the things I wanted, but the behavior is unchanged. Any openoffice application fails to run. HELP!!!

Patrick

---

### Post by kellemes on 2008-08-29
Hi guys, is this thread helping?
[http://ubuntuforums.org/showthread.php?t=627035]("http://ubuntuforums.org/showthread.php?t=627035")

---

### Post by phorgan1 on 2008-08-29
> **kellemes said:**
> Hi guys, is this thread helping?
[http://ubuntuforums.org/showthread.php?t=627035]("http://ubuntuforums.org/showthread.php?t=627035")

No, nothing helped.  In another [thread]("http://ubuntuforums.org/showthread.php?t=904671&highlight=openoffice") I give a stack backtrace for the seg fault that's happening when I try to run soffice.bin.

Patrick

---

### Post by cooke77 on 2008-08-29
Did you check...to see if your ISO (linux) had any 'faults' before you installed it?
48 hours ago..says 'you did not'.
Is your Ubuntu a 'Live-CD', or is it one you downloaded and 'burnt' to a CD?
Either way, you should check beforehand.....to see if there are any faults with it.
The fact that you can't use OpenOffice indicates that's where the fault is.
If the Ubuntu 'distro' you're using is free...of faults...OpenOffice should have worked, from the very start.
Without the neccessary 'update' process that does folow...when you installed.
Depending on 'how' you installed, maybe an Uninstall is required.
Then, a re-install.
So that you can check the CD you're using is 'free'..of faults.
Quickest 'work-around' I know of.

---

