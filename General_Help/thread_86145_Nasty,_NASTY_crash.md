---
title: "Nasty, NASTY crash"
date: 2005-11-04
forum: General Help
---

### Post by skybum on 2005-11-04
Hi everyone,

I just had my OS go down, and thought I would report it to see if anyone else has had this problem.  It happened when I clicked on a link in firefox: the program instantly died.  I tried to restart it from the Gnome-panel, and got a message to the effect of "cannot start child process of Gnome-panel (input / output error)".  I tried launching a terminal to see what was going on, and got the same error.  Any click anywhere on the Gnome-panel produced this message, and after a few clicks, all my desktop items disappeared.  So I had no choice but to reboot the system.

Looking at my logs afterwards, I became somewhat concerned, because my mail.log had a single entry in it at the time of the crash:

localhost postfix/master[6583] daemon started -- version 2.2.4, configuration /etc/postfix

This worried me because I've previously encountered an exceedingly nasty worm which uses postfix to propigate itself.  Fortunately, after the crash, postfix does not seem to be running, which I hope means that the worm isn't in my system.  Anyhow, aside from that, there were no notable log entries at all.

Has anyone else encountered this crash?

---

### Post by Saiboogu on 2005-11-04
I occasionally have Firefox die on me when I select a link - just click & "poof," its gone. Usually on pages that contain embedded media. Haven't bothered with much troubleshooting because its gotten much better lately (updated to 1.5). Never had the other symptoms, though - sounds like something much bigger going on in your case. Anything in your syslog for that time, other than the postfix message you found in the mail.log?

The vanishing icons before your reboot reminds me of a nasty HDD crash I witnessed while in Windows once, but if everything works fine after a reboot I'd imagine that isn't your case.

---

