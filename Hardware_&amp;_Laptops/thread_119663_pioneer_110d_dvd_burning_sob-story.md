---
title: "pioneer 110d dvd burning sob-story"
date: 2006-01-20
forum: Hardware &amp; Laptops
---

### Post by nashife on 2006-01-20
Hello all.

I just had the unfortunate experience of believing that I had successfully backed up about 20gb of data to dvd, and discovering (after a reformat) that the dvds are actually COASTERS!

basically what happened is that when i first burned the discs in my earlier install, they remounted ok but with the little "lock" icons on all of the files... which I figured was normal (this was my first dvd burner).  Then when I switched out my hard drives, reformatted, reinstalled and tried to restore my data, I discovered that my dvds could not be even recognized by any drive on any machine at all! the only thing that would happen is that my dvd burner would believe the discs were blank dvds... not full of data! any other drive (including my ibook) would just spin and finally give up.

So, I did lots of googling, lots of asking questions in irc and on my buddy list (thank you to everyone who helped...i'm sure i was really annoying) and I also read this page: [https://wiki.ubuntu.com/CdDvdBurning](https://wiki.ubuntu.com/CdDvdBurning) and came to the conclusion that my dvd burner must be one of those that is not supported.  *sigh*

For the record, I've got a Pioneer 110D DVD RW drive. I have no way of knowing if this is the same reason, but in other pages it was stated that the Pioneer 109/108 had problems with the firmware that made it not work with cdrecord...  I can't find links to the pages that I read that in, however. (i'll keep looking and edit this if I find examples, but maybe i'm on crack and made that up)  If this is the problem, it would be nice to know.

Anyway, I am able to burn an iso using growisofs as per the instructions in the wiki page, so I hope that if anyone else has a Pioneer DVD burner and has the same problems, they will try that last suggestion at the bottom of the wiki page before they take a baseball bat to their dvd burner. :)

Lastly for my questions: is there anyone who does have a pioneer dvd burner and is able to get it to burn dvds in breezy using cdrecord/nautilus/gnomebaker etc?  If so, did you do something special to make it work?  All my google results have just been other people having problems with this burner, so I'm sure the information would benefit not just me.

Is there a compatible hardware list perhaps organized by hardware type? I'm browsing this sticky thread for now ([http://ubuntuforums.org/showthread.php?t=88639](http://ubuntuforums.org/showthread.php?t=88639)) but I'm wondering if there are other places that try to make lists of either 'not supported' hardware or 'most likely to be supported' hardware. I want to start looking for a new one, but I'd like to have a good idea of if it will work.

---

### Post by Madpilot on 2006-01-20
I've got a Pioneer DVR-109, previous model to yours, and it burns data & music CDs just fine but I haven't tried DVD-Rs with it yet.

I shall have to pick up a couple of DVD-Rs or DVD-RWs and experiment with the thing - thanks for the heads up!

---

### Post by nashife on 2006-01-20
[QUOTE=Madpilot]I've got a Pioneer DVR-109, previous model to yours, and it burns data & music CDs just fine but I haven't tried DVD-Rs with it yet.

I shall have to pick up a couple of DVD-Rs or DVD-RWs and experiment with the thing - thanks for the heads up![/QUOTE]

Yeah be sure you check if the dvds can be read on other drives, or another computer. I should have done that to test the discs.

If yours successfully burns dvds using the regular cdrecord/gnomebaker etc methods, please reply again! maybe there's a way to get mine working!

I also found in the hardware compatibility thread (link above) that 'handy' has a pioneer 110D, and apparently it works for them... i PMed handy to ask about it.

---

### Post by StefanoCole on 2006-01-20
nashife, you can check if pioneer made a firmware update for your burner. Years ago I had problems burning CDs with a CD burner (different brand, not pioneer) and a firmware update solved everything.

Good luck, Stefano

---

### Post by grte on 2006-01-20
I've also got a 110D.  There is a firmware update out there.  It must help, because mine works just fine.

In fact, you can find the update [here]("http://www.pioneerelectronics.com/pna/service/support/article/0,,2076_4249_277206650,00.html").

---

### Post by nashife on 2006-01-20
[QUOTE=grte]I've also got a 110D.  There is a firmware update out there.  It must help, because mine works just fine.

In fact, you can find the update [here]("http://www.pioneerelectronics.com/pna/service/support/article/0,,2076_4249_277206650,00.html").[/QUOTE]

Thank you for the link! Can the update be installed with wine? I've never been very successful with wine, but I'd rather not reinstall windows.

I'll give it a try. Thank you.

---

### Post by midwinter on 2006-01-30
I just found this thread after burning a number of coasters with my 110D. Argh.     I'm hesitant to try new firmware because the last firmware I used got rid of the nazi region junk on it... which I imagine still applies in linux but honestly have no idea.

---

### Post by skwid on 2006-01-30
Pioneer releases regular firmware upgrades for all of their drives.  It is very common and is safe from all of my experiences.  I have a 108 and it burns DVD's and CD's just fine with Breezy.

---

### Post by mred_wtfe on 2006-02-08
I've had a similar issue myself. I haven't yet upgraded the firmware but am in the process of trying the suggestion on [http://ubuntuforums.org/showthread.php?t=1969](http://ubuntuforums.org/showthread.php?t=1969) for burnproof being enabled.

Give it a go if you haven't yet, maybe it'll fix your problem.

---

### Post by mips on 2006-02-08
Even though a drive has been formatted does not mean all data is lost, you can still recover data in the sections that have not been overwritten.

---

