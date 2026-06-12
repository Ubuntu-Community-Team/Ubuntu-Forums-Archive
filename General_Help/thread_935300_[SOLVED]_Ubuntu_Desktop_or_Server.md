---
title: "[SOLVED] Ubuntu Desktop or Server?"
date: 2008-10-01
forum: General Help
---

### Post by drmoqu on 2008-10-01
Hi,

I am seeking advice about whether to set up a sever OS or a desktop OS. To help you help me, here is some basic info:

Proposed machine: Intel P3 machine, 384MB RAM, 40GB HD, currently running Win 2k. Will be adding a 1TB HD.

Purpose of linux machine:

We currently have a a file server that runs a version of linux called GuardianOS (Snapserver). The SnapServer houses all of our data and the backup plan we had in place cannot yet be implemented with our new 2 office configuration. Hence I desperately need a backup solution. The catch for us is that the SnapServer allows some long filenames which cause backup programs on Windows machine to crash. Since the Snapserver is a linux enviroment, I am hopeful that a linux machine can run a backup with out such difficulty. At the very least I should be able to just cp our files.

The Question:

Considering the primary purpose of backing up a single network drive and the unknown about future needs (we still have to find a way for our 2 offices to talk to each other). Which version of Ubuntu should I install? Desktop or Server?

Thank you in advance.

-Dr Q

---

### Post by rsambuca on 2008-10-01
On that machine I would just do a minimal server installation and then you can add a lightweight Window Manager later if you wish.

---

### Post by HermanAB on 2008-10-01
I usually install a desktop GUI, then run the server in level 3 (/etc/inittab).  That way, if I am doing maintenance and wants a GUI program such as gedit or nautilus, then I can run it over SSH.

Cheers,

Herman

---

### Post by CREEPING DEATH on 2008-10-01
> **drmoqu said:**
> Proposed machine: Intel P3 machine, 384MB RAM, 40GB HD, currently running Win 2k. Will be adding a 1TB HD.

You need to google the mother board and see if it will address >128GB hard drives, it might not.
System is enough to run Ubuntu Desktop - my mother's machine is a PIII-600 with 384 MB and I installed 8.04 from the LiveCD.  However, sounds like you just need a server with Samba.

CD

---

### Post by drmoqu on 2008-10-01
Thanks CD. I may not be able to add a large disk as I had hoped. 40GB may be my limit according the specs. Looks like the motherboard has an IDE controller on board.

I would like to add one piece of additional information. I am not very LINUX literate so I am a concerned about using non-GUI interface. It's not that I am not comfortable with a command line interface, it's more that I don't know many of the commands.

Does that change anyone's recommendations?

---

### Post by drmoqu on 2008-10-01
> **HermanAB said:**
> I usually install a desktop GUI, then run the server in level 3 (/etc/inittab).  That way, if I am doing maintenance and wants a GUI program such as gedit or nautilus, then I can run it over SSH.

Cheers,

Herman

Thanks Herman but should I be concerned about my lack of LINUX knowledge when I don't really know how I would "run a server in level 3". Or is that something I could learn from online resources?

---

### Post by TeXtonyx on 2008-10-01
"I would like to add one piece of additional information. I am not very LINUX literate so I am a concerned about using non-GUI interface. It's not that I am not comfortable with a command line interface, it's more that I don't know many of the commands... Should I be concerned about my lack of LINUX knowledge when I don't really know how I would "run a server in level 3". Or is that something I could learn from online resources?"

[http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)
This has an Introduction to Linux, System Admin Guide, Network Admin Guide, and
GNU/Linux Command-Line Tools Summary in a variety of formats, free.

---

### Post by drmoqu on 2008-10-02
Cool. Thank you.

I decided in the end to install the desktop version. Since it is my first serious foray into Linux, I decide to make things a bit easier with the GUI. If I need the power of the server, I will do it down the road.

So thanks for all your assistance.

---

