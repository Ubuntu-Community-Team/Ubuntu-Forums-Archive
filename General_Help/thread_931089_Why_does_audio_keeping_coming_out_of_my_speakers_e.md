---
title: "Why does audio keeping coming out of my speakers even though I plugin my headphones?"
date: 2008-09-26
forum: General Help
---

### Post by riahc3 on 2008-09-26
Why does audio keeping coming out of my speakers even though I plug in my headphones? How can I fix this?

I have a Realtek ALC268 @ Intel 82801HBM ICH8M - High Definition Audio Controller

---

### Post by riahc3 on 2008-09-29
Bumping up...

---

### Post by lavinog on 2008-09-29
I think i remember on one of my computers there is a setting in the mixer for disabling the headphone switch.
I am not at that computer right now, but I can check to see if messing with that causes the same thing.

---

### Post by riahc3 on 2008-09-29
That tip doesnt help me too much....

---

### Post by drs305 on 2008-09-29
If you are on a laptop, double-click on the speaker icon/volume control and look at the 'Switches' tab. If you have a checkbox for 'External Amplifier', deselect it.

If you don't have volume control on the panel, right click on the panel and add "volume control".

This won't enable auto-shutoff but it will turn off the speaker when you don't want it to emit sound.

---

### Post by riahc3 on 2008-10-01
> **drs305 said:**
> If you are on a laptop, double-click on the speaker icon/volume control and look at the 'Switches' tab. If you have a checkbox for 'External Amplifier', deselect it.

If you don't have volume control on the panel, right click on the panel and add "volume control".

This won't enable auto-shutoff but it will turn off the speaker when you don't want it to emit sound.

Ill try this but auto-shutoff would be nice.

---

### Post by Nick Lake on 2008-10-01
I think you have to enable "jacksense". I had the same problem and this was the solution for me - but can't exactly remember what I did. - sorry :(

---

### Post by Yellow Pasque on 2008-10-01
Perhaps alsa-base is not configured correctly or jack sensing doesn't work on your model. [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)
Upgrading ALSA to the latest release might help too if the above does not work. [http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104)

---

### Post by riahc3 on 2008-10-01
> **Temüjin said:**
> Perhaps alsa-base is not configured correctly or jack sensing doesn't work on your model. [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)
Upgrading ALSA to the latest release might help too if the above does not work. [http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104)

The first solution pretty much worked but it still have a small issue; If I disconnect the headphones, then reconnect it sorta breaks and again goes thru the speakers.

My question is that there is also submodels between each codec so how do i set those? I wanna set it to AL268 then to the dell model. How do I go thru that line?

And Im gonna try the second solution now.

---

### Post by riahc3 on 2008-10-01
The second solution seems to have fixed all issues :) Thanks.

---

### Post by riahc3 on 2008-10-01
Some popping issues when I went out of VLC; I went back into VLC and they fixed themselves.

Alot of unsolved questions here.

---

