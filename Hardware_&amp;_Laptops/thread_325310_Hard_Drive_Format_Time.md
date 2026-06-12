---
title: "Hard Drive Format Time?"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by welders4linux on 2006-12-25
Hello ;o)

I am formatting a 160GB external Hard Drive via a USB 1.1 port ( I know I know)
Anyhow my question is how long is a reasonable time for this to take?

The light on the HDD access is lit on the unit, Cannot really hear anything going on as these drives are pretty quiet these days.

Anyhow there seems to be no real graphical movement in GParted, 0 of 1 operations completed.  @ what point would you figure Its not doing anything 1/2hr 1 hr??

thanks for your reply in advance?
AJ

---

### Post by budgie9 on 2006-12-25
160 Gb Should not take very long at all. I would suggest around 20 minutes or so, of course it depends on the M/B controller and the HD itself.
Why are you using the USB drive? Is there some particular reason for that.
Can  you not use a CD instead?

---

### Post by welders4linux on 2006-12-25
I have a hp pavilion xf255 XP 1.3Ghz,

Im using the external drive as a backup for a few machines we use.

thank you for your reply, I will have to find another avenue to format it

AJ

---

### Post by welders4linux on 2006-12-26
Just an update for future viewers of this thread.

I managed to partition and format in KNOPPIX.

My main concern now in Ubuntu is after I move (to the external drive) a few hundred megabytes my (external) Hdd light stays on....
  
  I figured the files may have been cached on the laptop and just slooowly moving over, but that was not the case.

  the only way I got things back to normal was to go into gnome partition and unmount the external drive....That didn't exactly do the trick as the status bar on "unmounting" seemed to be as stuck as the hard drive led.

  Its only when I quit gnome partition that the led seems to have some legitimate activity and then turns off.

Im sure there is a better way/explination.  And if anybody can enlighten me/this thread I would be a great help to myself and what seems to be people in like  situations..

(Ive seen other postings with like problems):confused:

---

### Post by welders4linux on 2006-12-31
Ok folks:

Again I am multiple posting in this thread in efforts to help those looking for the same Answers I am.

A: Ive upgraded to 6.10 (fresh install)
B: Had somewhat better success accessing the External HD but have found problems with multiple screens appearing for the USB Drive....Its auto mounting, over and over.

C: found the answer too that question here [http://ubuntuforums.org/showthread.php?t=327085](http://ubuntuforums.org/showthread.php?t=327085)

I have yet to move a very large file yet...will post back when I dare. :-? 

best regards
w4l

---

