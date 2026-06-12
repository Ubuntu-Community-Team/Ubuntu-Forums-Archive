---
title: "evolution inbox wiped out"
date: 2008-08-17
forum: General Help
---

### Post by aadgj on 2008-08-17
I ran some AV software (avast) yesterday because I suspected someone emailed me something bad.  The AV didn't run smoothly at all, but it did seem to find a problem in a file that had 'Inbox' as part of the name.  Now when I open Evolution all the files in the Inbox are gone.  The files in the subfolders and Sent folders are still there.  Here's what's in the AV quarantine directory:

:~/.avast/chest$ ls -l
total 170908
-rw------- 1 myname myname 173919103 2008-08-16 20:05 000001

The ~/.evolution/mail/local/Inbox file is size 173934780, and has a newer timestamp.  I tried simply swapping out that file with the quarantined one, but it made no difference.  I also tried resetting the .ev-summary and .index files as I've seen for similar problems posted, but that also made no difference.  Since I've started working on this problem, I've received some other emails, and they stay in the inbox without problem.

It looks like the old inbox messages are still around somewhere, and I'm pretty sure that if there is a virus I can delete it from evolution without incident, but I need to get the list back.  If I lose today's email, that's fine, but I really don't want to lose all the pictures of my little niece I had in the inbox.  What do these files do?  Where are the messages supposed to be?  How can I restore them?

---

### Post by JBAGroup on 2009-11-10
I have a similar problem.  I was having trouble with getting KlamAV and ClamTK to work.  Ended up doing a scan that resulted in what appears to be a quarantine of my Inbox.  I had Evolution open when the scan was processing, so the list of messages were still visible, but, when I selected one, the content did not display.  Instead, a message displayed that said the Inbox was irecoveralby corrupted.  I decided to restart Evolution.  Then, the Inbox showed on the menu list in the left panel, but the content window said "there are no messages in this folder".  I'm scratching my head wondering where to look for it and how, if at all, it might be recovered.

---

### Post by JBAGroup on 2009-11-10
Well, I dont know if this is a good solution, but it got my Inbox back.

I found that KlamAV had parked the box in quarantine, tagging it with a condom virus.  :lolflag: Sorry, Email.Trojan-5, to be precise.

Under the Events tab of the KlamAV GUI, I found Options.  In options, I de-selected the scan folders containing e-mail option.
 
Back to the Quarantine tab, I attempted to restore the ~/.evolution/mail/local/inbox item only to have it error out because Evolution had already recreated a new one.

Using Terminal, I navigated to the ~/.evolution/mail and # mv Inbox Inbox.091110

Then went back to KlamAV and successfully restored the Inbox from Quarantine.

All is back.  Now I need to know how to eradicate the offending message from the Inbox.  Any hints?

---

