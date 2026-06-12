---
title: "Firefox 3 history lost, navigation greyed out because disk full"
date: 2008-10-16
forum: General Help
---

### Post by gja on 2008-10-16
I wanted to mention a really annoying bug in Hardy.

On my Dell D600 I managed to fill up the entire disk /dev/sda1.
This caused Firefox to loose all my bookmarks and history. Also the navigation buttons in FF were greyed out and the search window didn't work.
Luckily, typing in a search phrase in the address bar did work.

The problem seems to be simply that the disk is full. It took me too long to find out what folders were exactly on which physical partition (guess I'm not that good at linux after all), but after freeing up some space on /dev/sda1 it seems to be ok.

Anyone else had this issue?

---

### Post by cariboo on 2008-10-16
Are you really sure your bookmarks are missing" have a look in ~/.mozilla. I use Foxmarks, a Firefox add-on, to syncronize my bookmarks between the various computers I use, it works great, and I never loose my bookmarks.

Jim

---

### Post by Bablefish on 2008-10-16
Even though Firefox 3 came out some time ago people are STILL having problems with it. And it does not matter what your OS is, the problems are the same. My suggestion is switch to either and older version of Firefox or go with Opera. They do have a .deb file you can download.

---

### Post by gja on 2008-10-16
> Are you really sure your bookmarks are missing

Well, you make me doubt that.
My first attempts led me to reinstall FF3, so maybe I erased them myself unknowingly. I wouldn't have been smart enough to retrieve them without that suggestion anyway, I'm afraid.

Hopefully this thread can help others.

---

### Post by oldsoundguy on 2008-10-16
> **cariboo907 said:**
> Are you really sure your bookmarks are missing" have a look in ~/.mozilla. I use Foxmarks, a Firefox add-on, to synchronize my bookmarks between the various computers I use, it works great, and I never loose my bookmarks.

Jim

Foxmarks is a GREAT program!  I can sync between four Linux computers and two Windows computers all working on my network Using FF and have the same bookmarks in ALL with just a click.  (can even migrate them to IE on the Windows machines!) (you DO know that those are stored ON LINE, do you not?)

Back to the OP .. see if you can either increase the default file size you are using for FF or CLEAN IT OUT now and then. That should stop the "disk full" error. 

Or go to the tools> clear private data.  Doing that, however will CLEAR it all as to the browser history.

OR .. you can take some time and go to history> show all history> and select and delete individual items.  That will garner some more disk space.

For those that constantly bounce from URL to URL, the latter list can and will get HUGE unless you put some limitations on it.

---

### Post by zvacet on 2008-10-16
@ **gja**

> On my Dell D600 I managed to fill up the entire disk /dev/sda1.

You can make some space with this commands

```
sudo apt-get clean
sudo apt-get autoclean
```

---

### Post by winman15 on 2008-10-17
Just had the same issue with buttons being greayed out. Fixed it by going to my "Home" folder, pressing crtl+h to show hidden files and then deleteing the .mozilla folder.  Restart FF and you should be good to go.  Hope that helps anyone with the same issue.

---

### Post by Elfy on 2008-10-17
That won't help if you want to keep bookmarks etc :)

---

### Post by divmediat on 2012-02-21
Happend to me also, yesterday, on firefox 10. disk full > bookmarks gone.

resolution: go to your profile directory and remove places.sqlite*, this will erase your bookmarks and history and firefox will automatically restore your latest working backup on startup. (usually this is only 1 day old)

---

