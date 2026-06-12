---
title: "Update Delay"
date: 2008-08-21
forum: General Help
---

### Post by Tteddo on 2008-08-21
I was wondering if there was a way to delay the update notification. The reason is, I have several customers using Ubuntu, but frequently on my machines there will be an update that breaks something (Not that I can't fix it in 30 seconds, but you know what I mean) I use all the time. If I could make it so a week or so goes by before my customers see an update, then I would know it would ok, because I update every day. In 2 cases what I am doing, which isn't good, is I installed Dapper and set it to not update ever, as I would lose time and money fixing random things.
Thanks!

---

### Post by Cheesehead on 2008-08-22
Option 1) (easy)

Right-click on the update-notifier icon in the system tray.
Select it to update weekly.

Option 2) (more fun)

Remove the packages update-notifier and update-notifier-common. This will remove the daemon, the notification icon in the system tray, and the background downloading of updates.
Replace them with a script that YOU initiate via ssh to download and install the updates in the background. 
Or a weekly/monthly cron job to download and then pop open Update Manager for them (that's what I do).

---

### Post by Tteddo on 2008-08-22
The problem is I want to shift the updates 2 weeks hence, so #1 won't work.
For example, if they update 1 week later, they will still get the updates that came out the day before. I want them to get the updates from 2 weeks ago.
Option 2 requires me to do something ;) so if something happens to me they are out of luck.

---

### Post by llebegue on 2008-08-22
What about setting your own repository that you would manage yourself and have your customers point to it for their updates ?

---

### Post by Tteddo on 2008-08-22
> **llebegue said:**
> What about setting your own repository that you would manage yourself and have your customers point to it for their updates ?
That would still require something from me that I would have to maintain, or at least pay attention to. Good idea though.

Maybe no one has thought of the possibility of time shifting the update mechanism?

I know that the way I am doing it now is bad, as they get no updates at all. But in my experience with my 3 Ubuntu machines and 1 Mythbuntu box things sometimes break on update, and since these people are trusting me to have a great experience without Windows I don't want to risk updating until the updates are out for a couple of weeks because it has also been my experience that any problems are taken care of really fast and then they would be safe.

---

