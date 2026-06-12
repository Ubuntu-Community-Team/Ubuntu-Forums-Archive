---
title: "Ran updates - VMware Workstation won't open"
date: 2008-10-15
forum: General Help
---

### Post by adam1mc on 2008-10-15
I'm a complete NOOB so I apologize in advance for my lack of knowledge.

So I ran the updates this morning that appeared in my Ubuntu update manager.  After they were finished I was asked to reboot, so I did.

After opening the OS I attempted to load VMware Workstation but the application won't open.  It was working fine before the update.  

A little box is created in the task manager area at the bottom of the screen that says "Starting VMware Workstation" but after a few seconds that box disappears.  I can't click on the box and open a viewable window so I don't have or can't see any errors.

Can anyone help?

I need VM so I can get some work done.

---

### Post by howefield on 2008-10-15
Try starting it from terminal, it may give you a clue as to what is wrong.

If you are not sure what the command to run it is, drag the VMware icon from your menu to the desktop, right click and select properties. Third field down should be the run command.

In a terminal type gksudo command

Then post back with the error.

---

### Post by adam1mc on 2008-10-15
> **howefield said:**
> Try starting it from terminal, it may give you a clue as to what is wrong.

If you are not sure what the command to run it is, drag the VMware icon from your menu to the desktop, right click and select properties. Third field down should be the run command.

In a terminal type gksudo command

Then post back with the error.



Yeah I thought of that right after I posted the help question.  Running from Terminal I was prompted to re-run the configuration.

I ran the vmware-config.pl and re-setup the application.

It worked perfectly after that.

Thanks.

---

