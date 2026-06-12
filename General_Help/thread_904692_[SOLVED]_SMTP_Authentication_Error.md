---
title: "[SOLVED] SMTP Authentication Error"
date: 2008-08-29
forum: General Help
---

### Post by m_vrik on 2008-08-29
I using Hardy 8.04 and Evolution 2.22.  I set up a business yahoo mail account to forward to my personal email account.  In order to make it work I was told by AT&T technical support to change my smtp server on Evolution to the name of a yahoo server rather than the personal email account server. I was able to receive emails through the POP server and send via the yahoo SMTP server.  After stripping the OS from my laptop and reloading Ubuntu and restoring my Evolution data and settings with the evolution-backup.tar.gz backup file I can no longer send emails and keep getting a request for the yahoo SMTP server password with the following error message, "Unable to authenticate to SMTP server.  Bad authentication response from server."  Now, I want to delete this server setting from Evolution use my personal email SMTP server.  How can I delete this yahoo server from my Evolution settings.  I have tried deleting the email account under Preferences and changing the SMTP server host in the account all to no avail. What can I do?

---

### Post by cooke77 on 2008-08-29
What is your real ISP provider?
That's what should be entered, not Yahoo.
Look in Evolution...for your 'set-up' details.
You should be able to re-configure it, there. Back to your ISP/original E-mail Account.)
(Can you remember 'how' you set it up, the first? Just repeat that process.)
This should also allow you .....to delete that Yahoo 'set-up'..at the same time.

To check, send yourself a 'test e-mail'.
If it comes back, it is set up right.

---

### Post by m_vrik on 2008-08-29
cooke77,
My real isp is Time Warner Cable Roadrunner and their servers are pop-server.wi.rr.com and smtp-server.wi.rr.com.  I have gone into the Evolution email setup and deleted the old setup and then reestablished the email account with the above host server names. Still, I'm prompted for the Yahoo server password and then get the authentication error message.  It seems as if somewhere in Evolution there is the Yahoo server name that is still active.  I would delete it on change the necessary config file if I knew where it was.  Evolution has a slew of different files.

---

### Post by markbuntu on 2008-08-29
I gave up on trying to get that to work and now just forward all my att email to my gmail account and use evolution to get my gmail.

---

### Post by m_vrik on 2008-08-29
I figured out my problem.  In my Evolution setup under the Preferences tab and in the Email Account setup, I was using the user name and the domain name in the SMTP user name section.  When I only typed the user name portion of the ATT email account for the ATT SMTP host server which I had listed, the problem was solved and I could send emails.

---

