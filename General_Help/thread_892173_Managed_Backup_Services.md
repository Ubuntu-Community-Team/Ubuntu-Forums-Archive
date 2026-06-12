---
title: "Managed Backup Services"
date: 2008-08-16
forum: General Help
---

### Post by purple_minion on 2008-08-16
Hello everyone, looking for some advice on software selection.  I am currently going to be starting a small computer repair business and would like to offer some kind of a managed backup service for clients.  I am toying with the idea of hosting my own instead of using an on-line service such as Mozy or SOS for a few reasons.  I know there exists commercial versions of these kinds of programs but they are a little too high in cost for a start up company so I am looking for free/cheap software.  I plan on using a Linux server in a locked room/closet with high speed Internet connection that the other companies can remotely connect to and upload critical data. I am assuming they will need some kind of a windows client as that's what everyone uses (unfortunately).  I have tried RESTORE but it's still a little early in the game however it seems promising. I have looked into such things as BACULA, DAR, AMANDA etc.  Does anyone have any suggestions or experience in this area? I thought maybe the simplest idea would be an ftp server and using a client like Cobian, or perhaps Acronis or Shadow Protect since they can access FTP IIRC.  I suppose I would have to monitor their disk usage manual or simply setup some kind of script to mail an alert or something more automatic. Any help would be appreciated in this confusing sea of options.

---

### Post by tamoneya on 2008-08-16
Personally I use cobain + FTP but it is more for personal use.  It has worked without any problems and I really dont have to watch disk space all that much because cobain can delete backups that are too old.  Also cobain is able to email you if there are any errors.  That way problems dont go unnoticed.

---

### Post by purple_minion on 2008-08-16
> **tamoneya said:**
> Personally I use cobain + FTP but it is more for personal use.  It has worked without any problems and I really dont have to watch disk space all that much because cobain can delete backups that are too old.  Also cobain is able to email you if there are any errors.  That way problems dont go unnoticed.

Thanks tamoneya, I would have to monitor storage as that is how you  usually sell it based on amount of space rented. I would want to charge someone more to store 10GB instead of 100MB as they are taking up more hardware and bandwidth and so should pay appropriately.

These would most likely be smaller business's that have a few computers and maybe a server with the odd home user thrown in as well. It just seems there is no middle ground, it's free and no features or outragiously expensive for enterprise's. Perhaps I will have to go with someone like SOS...

---

### Post by joeinbend on 2009-03-16
I realize this post is old, but here's my two cents anyway :)

I second the motion to use Cobian. You can set it up to run silently, it will connect back to your server via FTP, will allow you to break into specified file size chunks and encrypt (helping your liability on the topic of the customers' data being breached), and will notify you of the status of the backups (always notify, or only notify on errors). Also, it is open source (the Black Moon version is), so if you need to open it up to make some changes, you can. I think this would allow you to make a great commercially-viable backup solution!

Also, one GREAT feature, since you are talking about doing this on a commercial level, is the ability to have multiple simultaneous backup destinations. So this would allow you to easily have a "disaster recovery" secondary backup FTP location. You would just input a second FTP destination, where you have a second FTP server physically located elsewhere, in the event of a physical disaster at your primary datacenter (aka, under your stairs in your house!!)

Hope this helps

---

