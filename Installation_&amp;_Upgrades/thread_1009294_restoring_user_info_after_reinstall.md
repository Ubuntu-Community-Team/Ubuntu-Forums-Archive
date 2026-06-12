---
title: "restoring user info after reinstall"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by clarknova on 2008-12-12
I like to keep /home on its own partition, that way my stuff is still there should I need to reinstall the system. The reinstall wipes out my user info (/etc/passwd, /etc/group...) but I have to create a user during the install process anyway, and re-creating my wife's account with her existing home directory is no big deal.

On a system with a large number of users, however, this <i>is</i> a big deal. If you do it on the command line you have to add each user, create a default password, add them to the appropriate groups, make sure they own their home directory (because their uid and gid have usually changed from the old system), then give the user his new password, listen to him complain that his password has changed, then change his password again later because he didn't bother changing it to something he could remember.

And that's if you are capable of doing the above on cli. Some of my staff are not. Re-adding a user is even more complicated in the gui. The system won't let you add them with the default home directory because it already exists, so you have to create a tmp folder in their home directory. I'm not even sure how to change a user's home directory after the account has been created. Hopefully it can be done from the Users and Groups control panel (I'm not at a linux station at the moment), because trying to manually edit /etc/passwd has proven to be a nightmare lately.

Which brings me to my next point. I thought I could just copy passwd, group, shadow, and gshadow from the /etc directory from old system to new and all my uids, gids and passwords would be preserved. No. I tried doing that a while back and found the system after a day or so would revert back to some backup file that I hadn't edited.

If memory serves me, those backup files were named passwd-, group-, shadow-, and gshadow-, also in the /etc directory. Copying my hand edited files to the backup files fixed the reverting problem and preserved my carried-forward user data on the new system. At least I thought I had done this with success in the past.

So I tried this recently after fresh installing 8.10 on a sytem that was formerly 8.04. Mayhem. Sometimes my Users and Groups control panel showed no users on the system. Sometimes I couldn't open the control panel at all, I just got an error. Sometimes the X server wouldn't start on boot. Sometimes my /etc/passwd file became blank and I had no valid users. I tried many times with many variations in method to reinstall the system and restore user, group and password info, and every time it failed in a different manner.

I'm sorry if this reads like a rant, because that's not my intention. It's just that I've spent a lot of time trying a lot of different things that don't work, so I'm trying to explain the situation.

What I really would like to know is whether there is a sane, community-sanctioned method of restoring user, group, and password data to a system that has been installed fresh.

Thanks for looking.

db

---

