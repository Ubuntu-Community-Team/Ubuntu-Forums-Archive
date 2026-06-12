---
title: "[SOLVED] Evolution window settings lost on log-out"
date: 2008-08-29
forum: General Help
---

### Post by the real omni on 2008-08-29
Hi,

I use Evolution for its calendar, but I don't use any of the other features (mail, contacts, memos, or tasks). 

I like to have Evolution open to the Calendars page by default, and I've stretched the height of the month-view calendar on the left pane so it shows the current month and the next month as well.

The problem is that it seems to lose the window settings when I log out then log back in (regardless of whether it was a reboot).

This means every single time I log in and use Evolution for the first time in the session, I have to re-configure the window settings to be the way I like.

Is this a bug in evolution, or do I specifically have to choose an option like "remember window settings" somewhere?

---

### Post by the real omni on 2008-09-23
bump

---

### Post by hggdh on 2008-09-23
Well... you *should* be able to create a new view on the calendar (while in calendar mode, select View/Current View/Define Views, then *create* a new view, and edit as you wish).

With that said and out of the way... it does not seem to be working. I have just tested on Evolution 2.22.3.1 (Hardy), 2.24.0 (Intrepid), and 2.25.1 (trunk), and none of them have the "Edit" button working.

I am right now checking upstream to see if it is a known issue.

More later.

---

### Post by hggdh on 2008-09-23
re-statement: resizing the panels (so that the left-side panel will show two months, side-by-side) is working, at least on Hardy (2.22.3.1), and Intrepid (2.24.0),and trunk (2.25.0), at least for me.

Still, one cannot edit the view as I pointed out on my previous email.

What version of Evolution are you running? On a terminal, issue 'dpkg -l evolution\*', and paste the output here.

---

### Post by the real omni on 2008-09-23
> **hggdh said:**
> re-statement: resizing the panels (so that the left-side panel will show two months, side-by-side) is working, at least on Hardy (2.22.3.1), and Intrepid (2.24.0),and trunk (2.25.0), at least for me.

Still, one cannot edit the view as I pointed out on my previous email.

What version of Evolution are you running? On a terminal, issue 'dpkg -l evolution\*', and paste the output here.

Well I have no trouble showing the two months in the view, and the problem seems to have fixed itself.

I'm using 2.22.3.1 and now when I load evo, the left pane shows both months (as it was when I left it upon closing).

I suppose I should have checked that before bumping the thread ;)

Whatever it was, it seems to have been addressed by recent updates.

So, now that I've figured out how to bypass tray alerts and just bring up the alert dialog, and now that evo is remembering its window states, I can now say with complete confidence that Evolution rocks the kasbah and is officially THE BEST calendar suite available for any OS.

Props to the evo devs!!!

---

