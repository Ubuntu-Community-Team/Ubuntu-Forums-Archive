---
title: "[SOLVED] asus a6kt - Hibernate/resume problem"
date: 2008-07-27
forum: Hardware
---

### Post by pcolamar on 2008-07-27
Hi,
  I have tried all the suggestion I was able to find on our forums (s2disk, pm-hibernate, etc.) and no success in resuming.
Screen remains black.
Before I continue down the way ( checking some quirk, et similar) I wanted to check if somebody succeded with this laptop (Asus A6kt, similar to A6k and A6000)

Thanks

Palmer

---

### Post by t.rei on 2008-08-05
Having the a6000 here and am still looking for the solution.

*edit* It's the compiz/emerald, appearantly. turning it off it works. Well, this bites.

---

### Post by pcolamar on 2008-08-05
t.rei,
  I have somehow succeded.

That's more or less (sorry,  I did not write down all the steps though :(  ) what I did:


Verified that the swap is active and of the right size

Installed the packadge "hibernate" and "uswsusp" (I know it's redundand but it works) (see [http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855))

and used the command pm-hibernate following this thread ([http://en.opensuse.org/S2disk](http://en.opensuse.org/S2disk)).

Be carefull that when you resume it gives you a blank screen for 30 seconds at least. Do not switch (ctrl+alt+F1) on console during this 30+ seconds.

read also ([http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)) if you have UUID problem in resume

Regards

Palmer

---

### Post by t.rei on 2008-08-05
Well, Resuming taking 30 seconds does not sound to be a valid option really. 
Clicking compiz off before suspend and clicking once to get it back on after resume takes not even 2 seconds. 
I am currently thinking about getting this somehow to be automated. *wonders if thats a good idea*

One major drawback of my "solution" is all the windows being on one virtual  desktop after the switching. *sigh* This mixes my work with my "fun" windows - like xchat, banshee, gaim, ... Rather anoying but still alot faster to sort then 30 seconds. 

I really hope this is getting better at some time. Composite is - imho - required for an up-to-date Desktop. And I do love the Expose and the Scale-Plugin for everyday work.

*edit*
I have created two buttons - one to turn cvompiz off: "metacity --replace" and one to turn it on: "compiz --replace -c emerald". placed them as little icons in the panel for minimum space usage and good reaching.

---

