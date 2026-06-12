---
title: "Problem - Evolution connection to Exchange 2003 via OWA"
date: 2008-09-25
forum: General Help
---

### Post by jgolightly on 2008-09-25
Good evening,

I am currently running a fresh install of Ubuntu 8.04 HH.  I setup Evolution to connect to my company's Exchange 2003 server via OWA and, after a few snags during initial synchronization, it appears on the surface to load and synchronize correctly each time I open Evolution.  My trouble is occasionally when I attempt to synchronize (after initial load), open a new message or send a new e-mail, at which point the application hangs and crashes.  The "Checking for new mail" or "Retrieving Message" or "Refreshing folder" routine starts and then continues indefinitely.  Evolution is interactive until I try to do something that requires server communication or attempt to interrupt the synchronize action (including closing Evolution normally), then it stops responding, and eventually greys out.  I can Force Quit the program, however I then have to restart Ubuntu in order for Evolution to restart correctly.

I should apologize in advance: until this past Sunday, I hadn't touched a Linux terminal in around 8-10 years, and I am very, very new to Ubuntu.  That being said, I've been soaking up as much information on it as I can and am very, very happy with it.  This is just one issue keeping me from using this machine as a serious work machine, rather than just a project at home.

Thanks for any help.


Jim

---

### Post by jgolightly on 2008-09-30
Is a bump kosher? :X

Still having the same trouble.  I tried disabling and throttling my GAL queries and I had the same problem.

---

### Post by Aenima99x on 2008-09-30
I've been using the same setup for a couple months now and after the initial pains, it's been working good. A couple things I noticed right away that gave me problems were that it just would not authenticate correctly when I had it set to secure password, so I had to use plaintext. Also,the other important setting is to make sure you have the correct GC (Global Catalog) server set. I also have my GAL responses limited to 500. Hope this helps.

---

### Post by jgolightly on 2008-10-04
Is there any way to verify if my global catalog setting is working or not?  I opened up port 3268 on my company's firewall and forwarded it to the active directory server, but I'm still having the same trouble with Evolution.  Just now, for instance, it opened and updated my exchange mailbox just fine.  I let it sit for about 60 seconds and then I attempted to open a message from yesterday.  The message window opened but it's empty and it's currently running three actions at the bottom of the Evolution main window: "Retrieving message", "Retrieving message" again, and "Refreshing folder".  It's been sitting that way for around 10 minutes now.  If I close the message window, Evolution will hang and require a forced quit.

I've read in several other places that this is a problem a number of users are having.  In those threads, it's typically attributed to the global address list, autocompletion, and automatic contact creation upon reply.  I've tried turning my GAL queries off, autocompletion off, and automatic contact creation off, but I'm still running into the same issue.  Typically, the threads I read end up dead without a solution.

Anyone else having this problem that's had better luck?

---

### Post by jgolightly on 2008-10-04
Update, with some success:

After continuing to adjust and test the settings of Evolution, I finally changed the "Limit number of GAL responses:" to 1, since it can't be set to 0.  I also made sure Autocomplete was turned off entirely.  I've had Evolution running for several hours now.  I did have one crash when I turned on the preview pane, which I can live without (I'll try it again when I'm feeling a bit more lucky).  I have received and sent new e-mails and added/uploaded tasks to the Exchange server, which have almost correctly shown up on my Microsoft Outlook tasks list (the task itself arrives, but the due date was set to "None", when I had set it to 10/6/08 via Evolution).

Not perfect yet, but usable.  Now I'm gonna start the task of figuring out which feature was crashing Evolution: GAL, Autocompletion, or both.

EDIT: 2 hours later- I've encountered two more crashes... The first crash occurred after I tried to synchronize with the Exchange server after sending an e-mail.  From what I've read, that's a pretty common bug that's being worked on, hopefully I can find a workaround.  The other crash occurred after I sent an e-mail from my XP/Outlook workstation with an attachment.  The next time Evolution tried to synchronize with the Exchange server, it crashed.

Overall, operation is much better so far with GAL queries restricted and autocompletion off.  Still working out some other problems, though.

---

### Post by n00blar on 2008-10-08
I don't mean to hijack your thread, but I want to use Evolution as well, but I don't know if I can use Evolution from my home PC to access my Exchange server at work.

For now I've been accessing my Exchange server via OWA from FF, but I don't know if Evolution will even be able to access Exchange the way Outlook does when Outlook is configured to use RPS over HTTP.

---

