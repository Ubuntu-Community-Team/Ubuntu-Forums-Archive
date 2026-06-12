---
title: "Neverending printing... I'm running out of paper!"
date: 2005-11-19
forum: General Help
---

### Post by HunterCo on 2005-11-19
Okay, my most recent frustration is printing. I know that I can print just fine with the hardware I've got in another distro using KDE and the foomatic gui, so there is something I've just done wrong in Gnome I think.

So, this is the hardware I have:
Linksys PSUS4 Print Server
HP PSC 1310 USB Printer

The print server is at address: 192.168.10.101
The printer is setup on queue: L1

I setup the printer under System -> Administration -> Printing. It's a network printer, using remote CUPS (maybe this is the problem- I think I used remote LPD before) and even when I send a test page (or print from any program) it just loops. The page prints until I turn off the printer and disconnect the print server and cancel the print job. Happens on two different computers. I'm sure I'll fix the problem myself by switching to remote LPD, but just in case that's not the issue, I thought I'd post here to see if anyone else knows what might be going on.

I appreciate the help!

---

### Post by jwd45244 on 2005-11-19
sudo lpq
then
sudo lprm <print job numb> ...

---

### Post by HunterCo on 2005-11-19
[QUOTE=jwd45244]sudo lpq
then
sudo lprm <print job numb> ...[/QUOTE]
This cancels the print jobs... which I can do already.
What I need to know is why my print jobs go into a neverending loop, continuing to print the document over and over again until I manually stop it.

---

### Post by HunterCo on 2005-11-19
Okay.

Well, like I said, I figured out what I did. It was related to defining the print server as a Remote CUPS Server as opposed to a Remote LPD Server. I removed the CUPS printer and set it up identically using remote LPD and it works like a champ- in only printing documents once, that is!

BTW: Although the print queue commands suggested to me (lpq and lprm) didn't fix my issue, they were a handy little thing to keep. I was accessing the print queue/jobs through a gui, but I like using the CLI when I can get away with it. Thanks jwd45244! ;)

---

### Post by jwd45244 on 2005-11-25
Glad to have been some assistance

---

