---
title: "Is there a cleaner for Ubuntu ?"
date: 2008-09-02
forum: General Help
---

### Post by sowhat12345 on 2008-09-02
I know that there is not a cleaner (like ccleaner for widndows) and it is not important for Ubuntu (and also for the other linux systems) but I wont to delete all the recent documents and the history from Ubuntu. For example the terminal has saved all the commands which I have writed until now . I could not clear them. Maybe all players has saved the my history ! Or if had an error viewer? how can I clear them ? Is there a simple way to do ?
(If not .. I'm going to install wine and than ccleaner :):) )

---

### Post by SunnyRabbiera on 2008-09-02
ccleaner would not work that well.
I am sure there is a way to clean your history in the terminal though I am unsure how to do it.

---

### Post by brian_p on 2008-09-02
> **sowhat12345 said:**
>  For example the terminal has saved all the commands which I have writed until now . I could not clear them.

```
rm .bash_history
```

---

### Post by Sinkingships7 on 2008-09-02
Places -> Recent Documents -> Clear Recent Documents

That will get rid of any video player history and whatnot.

---

### Post by kpkeerthi on 2008-09-02
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

In addition, be sure to clean up ~/.thumbnails where nautilus caches icons. This folder tends to grow in size over time. A good strategy is to keep the icons that were accessed more frequently and delete the rest. The below command will clean out everything that were not accessed in the last 7 days:
```
find ~/.thumbnails -iname "*png" -atime +7 -exec rm '{}' ';'
```
(You may want to add this to your crontab)

The other place you might want to check is your ~/.config to remove applications settings of the application that you no longer have installed.

---

### Post by bobyy on 2008-09-02
Hy

 maybe if you want to clean the bash hist. it is enought to insert this in a cron job 
[HTML]>.bash_hitory[/HTML] 
it will clean the bash file

---

