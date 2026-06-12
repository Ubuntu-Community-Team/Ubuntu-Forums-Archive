---
title: "Too many files ending with ~"
date: 2008-11-24
forum: General Help
---

### Post by anjanesh on 2008-11-24
Hi

I have too many files ending with ~ in my directory.
I think these get created with editing the gedit, but why aren't these deleted after done editing with gedit ?

Thanks

---

### Post by weemadarthur on 2008-11-24
These files are backup files created so that you still have a copy of the original file if you want to roll back any changes you made. You can safely delete them if you are sure you don't need them.

---

### Post by kerry_s on 2008-11-24
those are backup files, you can delete them if not needed.
you can change gedit doing it in the gedit preferences.

---

### Post by anjanesh on 2008-11-25
I do want the backup files - but how I set it backup all files to a particular folder ? Say /home/anjanesh/backups/gedit/ ?

---

### Post by kerry_s on 2008-11-25
been awhile since i used gedit, but i don't think you can set where to put the backup. look in the preferences, i could be wrong.

---

### Post by kpkeerthi on 2008-11-25
> **anjanesh said:**
> I do want the backup files - but how I set it backup all files to a particular folder ? Say /home/anjanesh/backups/gedit/ ?

You can turn off the backup option in gedit. But there is no option in gedit to save all backups to a specific folder.

You may however run a script to do it for you:
```

find ~ -name "*~" -type f -exec mv '{}' ~/backups/gedit

```
Put this script in your [crontab]("https://help.ubuntu.com/community/CronHowto") to run it periodically.

---

### Post by kerry_s on 2008-11-25
i should have thought of that, but i was busy trying to decipher "man fonts.conf" :) i finally got non-antialiased fonts for all text except bold and italic, it only took 2 hours. :( :lolflag:

---

### Post by anjanesh on 2008-12-19
Doesnt -exec work for all commands ?
```
find -type f -iname '*\.php' -exec chmod 644 '{}'\;
find: missing argument to `-exec'
```

---

### Post by dcstar on 2008-12-19
> **anjanesh said:**
> Doesnt -exec work for all commands ?
```
find -type f -iname **'***\.php' -exec chmod 644 **'**{}**'**\;
find: missing argument to `-exec'
```

You have unmatched "'" characters.

---

### Post by geirha on 2008-12-19
> **anjanesh said:**
> Doesnt -exec work for all commands ?
```
find -type f -iname '*\.php' -exec chmod 644 '{}'\;
find: missing argument to `-exec'
```

Put some space around \;
```
find -type f -iname "*\.php" -exec chmod 644 {} \;
```

---

