---
title: "Sound Problems: Dell Inspiron 1525"
date: 2008-07-27
forum: General Help
---

### Post by Thyssenkrupp on 2008-07-27
I have recently bought a Dell Inspiron 1525, and have set up a dual boot Vista+8.04.

Since this, the sound on my laptop has stopped working, unless it is through headphones.

Aanyways, there are no outstanding restricted drivers present when ubuntu is running the hardware managment.

I have updated the drivers using Vista.

Ideas??

---

### Post by Thyssenkrupp on 2008-07-27
:confused:Bump.


The speakers are playing sound, but at a very low volume, and real crackly.

Heeeelp???
:confused:

---

### Post by Dementius on 2008-07-28
Hi!

I'm also running Hardy on a Dell Inspiron 1525 along with the Vista thing.
Anyways i'm really new to Linux so i'm not sure if this will work but give it a try.

Open a terminal and type the following:

alsamixer

A small window should pop up with the master volume switches. Make sure all of them are at 100% (increase them with the up key).
This should to the trick. If not, open the Volume control from the taskbar icon and experiment with the settings. You could have accidentally swiched of the main speakers.

Hope this works!:KS

---

### Post by Shoadow56 on 2008-08-02
This worked for me, thank you sir!

---

### Post by Mihira on 2008-08-15
Yaaay!!

Worked for me too.

:D

---

### Post by talalism on 2008-09-26
> **Dementius said:**
> Hi!

I'm also running Hardy on a Dell Inspiron 1525 along with the Vista thing.
Anyways i'm really new to Linux so i'm not sure if this will work but give it a try.

Open a terminal and type the following:

alsamixer

A small window should pop up with the master volume switches. Make sure all of them are at 100% (increase them with the up key).
This should to the trick. If not, open the Volume control from the taskbar icon and experiment with the settings. You could have accidentally swiched of the main speakers.

Hope this works!:KS

thanks man this work with me :D

thanks you very much :D

---

### Post by riesengreen on 2008-11-19
Hi all:

I am using a Dell inspiron 1525 running Ubuntu 8.10 (I bought the computer preinstalled with 8.04 and updated myself).

My sound is weak! Sound quality seems fine, but there is no way that my speakers could possibly be this weak!

I opened alsamixer and made sure that my volume was at 100.

Any other ideas? I want to be able to :guitar:

Thanks!

Sorry that it took me so long to note this, but I upgraded to Intrepid Ibex and the sound is back!

---

### Post by louvois on 2008-12-02
Hello,
I have too a laptop Inspiron 1525 with Vista and Ubuntu 8.10 installed. The integrated speaker sound volume is low. I upgraded to the latest bios, but it remains unchanged.
I already checked alsamixer, nothing to do. Because the symptom is same on Windows Vista.

ps: The sound is clean with headset or external sound speakers.

Is it a hardware problem ? Thanks :popcorn:

---

### Post by jsschreck on 2008-12-20
Back in Oct. when Intrepid came out, I upgraded immediately. Sound "worked" except when I muted. Then a horrible cackling sound ensued. Has anyone else experienced this with your Inspiron 1525? Mine was an Ubuntu pre-install when purchased. I filed a bug report back when this was happening, though not much ever came of it. Since then I have gone back to 8.04 and I am really just waiting to hear if the mute/cackling has been fixed.

John Schreck

---

### Post by ezsurfer on 2009-07-20
From somewhere else on this site...

Right click the speaker on the status bar

Select Open Volume Control

Select preferences pushbutton

check the Front box

Turn up Front volume control to max


Worked excellently for me, now it's almost too loud, and crystal clear sound!


ezsurfer

---

### Post by R3p1h on 2011-05-14
Hi, I was looking hard to solve this problem, I am sure that you already fixed this problem
 
 but for the user that coming for search engine websites this is the solution
 
 [http://ubuntuforums.org/showpost.php...47&postcount=4]("http://ubuntuforums.org/showpost.php?p=8314847&postcount=4")
 
 work for me and I think work for anyone that have dell laptop inspiron.
 I have Dell Inspiron E1705 / 9400 in ubuntu 10.4

---

