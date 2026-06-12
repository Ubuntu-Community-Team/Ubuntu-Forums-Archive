---
title: "Nvidia driver 331 on Ubuntu 13.10 with dual Nvidia GPUs"
date: 2014-01-05
forum: Hardware
---

### Post by marcus.pearlman on 2014-01-05
I started to post with the intent to ask a question, but I think I just solved my problem and wish to enlighten the masses.  I  installed the latest Nvidia 331.xx drivers on Ubuntu 13.10 with:[INDENT]sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331

[/INDENT]
and my graphics went to crap.  The error was: “The system is running in low-graphics mode”. Reverting to the Nvidia-current drivers did not solve this issue!  I tried everything here: [http://ozkaya84.wordpress.com/2013/03/30/how-to-fix-the-system-is-running-in-low-graphics-mode-error/](http://ozkaya84.wordpress.com/2013/03/30/how-to-fix-the-system-is-running-in-low-graphics-mode-error/) and nothing worked.  I ended up re-installing the OS and trying again.  When I installed nvidia-331 this time, I noticed that it installed bumblebee.  At this point, after working 5 hours on this problem, I knew that this was a dual integrated graphics, nvidia graphics program.  On a hunch I uninstalled bumblebee:[INDENT]sudo apt-get --purge remove bumblebee
sudo reboot[/INDENT]
And wouldn't you know, my graphics worked again.  Screw bumblebee!!  Hopefully this saves someone some time.

---

### Post by sandrix2 on 2014-01-11
Thank you very helpful,timesaver

---

### Post by Thomas_Li on 2014-01-21
A big thanks, took me ages to find this, but just a few seconds to fix the problem.

---

### Post by xannaxprozaxx on 2014-01-23
according to [http://askubuntu.com/a/403329](http://askubuntu.com/a/403329) and [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1265570](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1265570)
you also have to remove /etc/modprobe.d/bumblebee.conf

---

### Post by Conzar on 2014-01-23
THANK YOU SO MUCH!!!!  This problem is with all nvidia drivers (nvidia-current ie 309, 313, 319, 331).  And it exists in Ubuntu 12.04 and 13.10.  I actually re-installed my system (was 12.04) to 13.10 thinking that it would fix the problem (it did not).  So it seems that bumblebee has majority broken ALL nvidia drivers (even the binary install package from nvidia is broken).  This is really an unacceptible bug ... how did this get past QA????

Thanks again marcus!!

---

### Post by mathewtwilkins on 2014-01-30
Thank you so much. Worked like a charm. Took me a couple of days to straighten this out.

---

### Post by lucas-exbrayat on 2014-01-31
Thank you so much ! Works for me, finally after 4 hours ... :)

---

### Post by machinanoctua on 2014-03-18
just found your post this worked great literally fixed everything that was wrong thank you !

---

### Post by pwabrahams on 2014-03-21
I too am running Kubuntu 13.10 with nvidia-331 installed.  Following the suggestions here I purged bumblebee and verified that all its files are gone:
```
sudo updatedb
locate bumblebee
```and indeed there are no bumblebee files left.

But I still cannot get resolution better than 1024x768.  (I want 1280x1024.) I determined this by going to the Display section of System Settings and looking at the resolutions offered there (you need to click on the arrows icon to see them).  1024x768 was the top of the list.

Earlier posts in this thread didn't clarify what actual resolutions people have been able to get, except that they're not low.

---

### Post by ludvig-blomkvist on 2014-04-10
Why is there a :mad: emotion in the code? Can not for the life of me figure out how it is supposed do be... Can not get it to work. Can any one give me "sudo add-apt-repository ppa:mad:org-edgers/ppa" this code whith out the emotion in the middle? ;p

---

### Post by ionut-mihaescu on 2014-04-23
> **ludvig-blomkvist said:**
> Why is there a :mad: emotion in the code? Can not for the life of me figure out how it is supposed do be... Can not get it to work. Can any one give me "sudo add-apt-repository ppa:mad:org-edgers/ppa" this code whith out the emotion in the middle? ;p

Try this:   [COLOR=#111111]sudo add-apt-repository ppa: xorg-edgers/ppa 

Remove the space after ppa:

[/COLOR]

---

### Post by dbea on 2014-11-12
> **marcus.pearlman said:**
> I started to post with the intent to ask a question, but I think I just solved my problem and wish to enlighten the masses.  I  installed the latest Nvidia 331.xx drivers on Ubuntu 13.10 with:[INDENT]sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331

[/INDENT]
and my graphics went to crap.  The error was: “The system is running in low-graphics mode”. Reverting to the Nvidia-current drivers did not solve this issue!  I tried everything here: [http://ozkaya84.wordpress.com/2013/03/30/how-to-fix-the-system-is-running-in-low-graphics-mode-error/](http://ozkaya84.wordpress.com/2013/03/30/how-to-fix-the-system-is-running-in-low-graphics-mode-error/) and nothing worked.  I ended up re-installing the OS and trying again.  When I installed nvidia-331 this time, I noticed that it installed bumblebee.  At this point, after working 5 hours on this problem, I knew that this was a dual integrated graphics, nvidia graphics program.  On a hunch I uninstalled bumblebee:[INDENT]sudo apt-get --purge remove bumblebee
sudo reboot[/INDENT]
And wouldn't you know, my graphics worked again.  Screw bumblebee!!  Hopefully this saves someone some time.

THANK YOU VERY MUCH!!!!! It was bumblebee!!!!!! 
Bumblebee made the laptop to use intel or nvidia but not both.

---

### Post by marcus.pearlman on 2015-03-22
> **ludvig-blomkvist said:**
> Why is there a :mad: emotion in the code? Can not for the life of me figure out how it is supposed do be... Can not get it to work. Can any one give me "sudo add-apt-repository ppa:mad:org-edgers/ppa" this code whith out the emotion in the middle? ;p

HAHA! This is so funny. :) Sorry about that but I guess that particular string is an emoticon. Next time ill post code like this verbatim.

---

