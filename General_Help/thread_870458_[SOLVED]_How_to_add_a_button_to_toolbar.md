---
title: "[SOLVED] How to add a button to toolbar?"
date: 2008-07-25
forum: General Help
---

### Post by muskedear on 2008-07-25
Good day,

I would like to add a button to my toolbar at the bottom of my desktop, for example a restart or shutdown button.  I have done this in Windows Vista via shortcuts that execute the following commands:

shutdown.exe /s
shutdown.exe /r 

and then dragged the shortcuts from the desktop to the toolbar and changed the icons.

What is the equivalent procedure in Ubuntu?

Thanks.

---

### Post by ad_267 on 2008-07-25
You can right click on the panel and select "Add to panel" and then select Quit.

If you want it to shutdown or restart immediately then the command is "shutdown now" to shutdown and "shutdown -r now" to restart. You have to run these as root though but running "gksu shutdown now" would just be annoying as you have to put in your password so you would want to make it so any user can run shutdown for this to work.

---

### Post by ad_267 on 2008-07-25
Found this that explains how to make it so you can run shutdown without entering a password. Then you can use "sudo shutdown now" and "sudo shutdown -r now"

[http://linux.byexamples.com/archives/315/how-to-shutdown-and-reboot-without-sudo-password/](http://linux.byexamples.com/archives/315/how-to-shutdown-and-reboot-without-sudo-password/)

---

### Post by muskedear on 2008-07-25
> **ad_267 said:**
> You can right click on the panel and select "Add to panel" and then select Quit.

If you want it to shutdown or restart immediately then the command is "shutdown now" to shutdown and "shutdown -r now" to restart. You have to run these as root though but running "gksu shutdown now" would just be annoying as you have to put in your password so you would want to make it so any user can run shutdown for this to work.

Thanks.  Right-clicking and adding quit to the panel adds the entire subpanel.  I am looking for a way to have direct buttons to shutdown and restart.  Any suggestions?  How do you link, say the command "shutdown -r now" to a button?

---

### Post by ad_267 on 2008-07-25
Under "Add to panel" select Custom Application Launcher and for the command set "sudo shutdown now" and "sudo shutdown now -r".

Before you can use that you will have to edit /etc/sudoers as explained in the link I posted.

---

### Post by steveneddy on 2008-07-26
> **ad_267 said:**
> Under "Add to panel" select Custom Application Launcher and for the command set "sudo shutdown now" and "sudo shutdown now -r".

Before you can use that you will have to edit /etc/sudoers as explained in the link I posted.

That's the way I do it, too.

---

### Post by muskedear on 2008-07-26
> **ad_267 said:**
> Under "Add to panel" select Custom Application Launcher and for the command set "sudo shutdown now" and "sudo shutdown now -r".

Before you can use that you will have to edit /etc/sudoers as explained in the link I posted.

That works.  Thanks again for posting your reply.

---

