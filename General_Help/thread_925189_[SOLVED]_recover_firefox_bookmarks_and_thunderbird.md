---
title: "[SOLVED] recover firefox bookmarks and thunderbird address book"
date: 2008-09-20
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-09-20
Hi all,
I did something stupid the other day and crashed my laptop. OK, sort of my own fault, so I don't complain. I had Kubuntu 7.10 running with KDE3.5, Firefox 2.x (latest version) and Thunderbird 2.x. Now I have Hardy (8.04) with KDE4.1 with Firefox 3 and instead of Thunderbird I'm using Kontact for emails, etc. 

So, here is my problem. I have a recent backup of the complete /home but not specific backup of exported Firefox bookmarks and Thunderbird address book.
Is there a way to recover those things easily from that backup? Specially considering that I have newer DE and newer/different apps? Or do I need a 7.10/KDE3/Firefox2 to recover the bookmarks and then export them and import in the new browser?
How about the address book, is that working cross application? I suspect not.

In any case, how would I move forward about that? Where do I potentially find the bookmarks and address book in the backup. I have a 7.10/KDE3 installation available. So, that would not be the issue. But how am I doing that?

Anyone able to help me out?

---

### Post by Predator106 on 2008-09-20
Yes, I believe what you're looking for would be in /home/shaun/.mozilla/firefox, shaun being my username. There should be some good stuff in there, you may have to sift through the couple folders that are there.

As for thunderbird... dunno, I use gmail :) so I guess it would be in that same folder, or maybe a 'thunderbird' folder, I have no idea.

---

### Post by Linux&amp;Gsus on 2008-09-20
Cool, thanks. I'll look through that tomorrow/later. It's 3AM, I'm shocked, well, and _slightly_ sleepy...
Any ideas if I can simply copy Firefox2 bookmarks over to Firefox3?

Cheers.

---

### Post by cariboo on 2008-09-20
Look in yor backup for **.mozilla** and **.mozilla-thunderbird** copy them ti the new directories and just edit the repective ini files to point to the directories you just copied.

Jim

---

### Post by Predator106 on 2008-09-22
Uhm, not sure if FF will recognize that it was from 2.0, it may expect everything that resides in that folder to be 3.0. In other words, you may have to install 2.0 and then import them from 3.0, etc.

I recommend installation of the 'Foxmarks' add-on for Firefox. It has saved me a from a vast amount of troubles.

---

### Post by stickmangumby on 2008-09-22
Copying my profile directly from FF2 to FF3 worked for me. I think when you first launch after copying it will determine which Add-ons are valid, and prompt you to upgrade or remove those that are for version 2.x.

---

### Post by Linux&amp;Gsus on 2008-09-23
Thanks all, I just love that forum here. It took me a bit longer, didn't had the time earlier. But it worked liked a breeze.
Actually I discovered a bookmarks.html in the Firefox folder and a abook.something for Thunderbird. So, instead of messing around with ini files I just copied these ones over, no problem.

For the address book, of course, I needed to export it in Thunderbird and import it in Kontact. I don't think they're using the same kind of files, so I didn't try to mess around. ;)

Thanks again for all your help.

Edit: Thanks also for the hint with Foxmarks. I heard of that earlier but I don't like the idea of having my bookmarks stored in "some" place online. You know, I'm one of those paranoid people... ;) I also don't use things like delicious, etc.
If there only would be something to make that happen between computers in a local network or to store at a place of own choice. :(

---

