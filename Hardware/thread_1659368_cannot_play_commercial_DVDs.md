---
title: "cannot play commercial DVDs"
date: 2011-01-03
forum: Hardware
---

### Post by jlh68 on 2011-01-03
I am using Ubuntu 10.10 64bit on my TimelineX laptop.  I have installed the restricted extras and followed the steps in the Ubuntu documentation.

I cannot get commercial DVDs to play.

OK, how do I fix it?

---

### Post by damphoud on 2011-01-03
Do you receive an error prompt? Does the DVD try to autoplay with 'Movie Player' when inserted?

---

### Post by jlh68 on 2011-01-04
Yes, it does try to auto play.  Disc spins and then I get a prompt that it cannot read source dvd.

---

### Post by I'mGeorge on 2011-01-04
try with vlc and if it doesn't works xbmc should do it

---

### Post by Grenage on 2011-01-04
> **jlh68 said:**
> Yes, it does try to auto play.  Disc spins and then I get a prompt that it cannot read source dvd.


That sounds more like a physical drive problem; does it read non-commercial CDs?

---

### Post by nomko on 2011-01-04
> **jlh68 said:**
> I am using Ubuntu 10.10 64bit on my TimelineX laptop. I have installed the restricted extras and followed the steps in the Ubuntu documentation.
 
I cannot get commercial DVDs to play.
 
OK, how do I fix it?
 
 
Good to mention that the problem occurs with comercial DVD's.
 
Did you try this:
**sudo /usr/share/doc/libdvdread4/install-css.sh**
 
 
Another solution is adding the repository for medibuntu: here's the manual [how-to about medibuntu]("https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs").

---

### Post by jlh68 on 2011-01-04
Added mediubuntu and I still get the attached message.

And yes I had previously used this: > sudo /usr/share/doc/libdvdread4/install-css.sh

I think I need to try Win7 to test the optical drive.  If the drive works with Win7 then it is in the Ubuntu system, if it does not work with Win7 then it is an Optical drive problem.

---

### Post by jlh68 on 2011-01-04
To **Grenage** the drive will play other DVDs and CD's, including some commercial like one on Air Force Aircraft. It is a DVD-Super Multi DL drive.

---

### Post by jlh68 on 2011-01-04
Additional information:  I am using a 64 bit OS.

---

### Post by jlh68 on 2011-01-04
OK some progress.  I went to my Win7 OS and tried it the drive would not work. It seems that the DVD drive had not been set to the DVD Region (1), so I set the region.  Then I was able to play the DVD.  I then shut down the player.  Then Win7 had to do some updates.  The updates did not complete correctly and the system locked up.  So I remembered the old "CTR+ALT+Delete" and then shut it down, then rebooted into Ubuntu. In Ubuntu I still could not get the DVD to play correctly, but I now got the audio in jerky sounds, with no audio.  Suspecting a DVD disc problem I tried two other commercial DVDs and both of then worked.  So now I will have to try other DVDs in the computer and to try the suspect DVD in my home theater DVD player to check it.

---

