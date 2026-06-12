---
title: "Cron job from USB drive"
date: 2011-01-07
forum: Hardware
---

### Post by ronbrooks on 2011-01-07
I want to copy files from my USB drive to my computer.  I have two drives one is a Memorex UFD drive and the other is Kingston drive.  Now when I set up the Cron job the only one that works is the Kingston drive. the Memorex UFD drive I get an error that there is no file of that name.  I think it was the space in the Memorex UFD that is giving me the trouble.  
Dose anyone know if this is the trouble and how to solve the problem. Oh the Memorex UFD works fine and it shows up on the desktop when I plug it in so it is not the drive. :confused:

---

### Post by IcarusR on 2011-01-07
> I think it was the space in the Memorex UFD that is giving me the trouble. 

You could change the drive label with gparted to 'Memorex' to eliminate the space as a possible cause.
Or wrapping the path in single quotes (') in your crontab may work.

---

### Post by ronbrooks on 2011-01-07
Thank You very much the single quote worked.  I know that I had to be missing something.  You are a life saver.

---

### Post by IcarusR on 2011-01-07
Glad to be of help.

---

