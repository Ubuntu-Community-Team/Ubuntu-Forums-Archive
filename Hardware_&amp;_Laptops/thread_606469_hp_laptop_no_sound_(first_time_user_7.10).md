---
title: "hp laptop no sound (first time user 7.10)"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by spinny on 2007-11-08
Hey Guys i bought a Hp9614ca laptop from the future shop in canada and vista pissed me off so much i wanted to give this a go. The problem... no sound!

I did some reading and found there is issues with hp laptops, but i was wondering if anyone has figured anything out???

I am a newbie with ubuntu, and i REALLY want to make the switch, but living without sound is no good! I am also a little older (born in the 60's) so please go easy on me.

Thanks once again

jim

---

### Post by spinny on 2007-11-09
anyone?

---

### Post by gunashekar on 2007-11-09
spinny, 
I had the same problems. I found several options i can try right here on this forum. I learned that the best way to find answers is to use the search engine on this foum or better google . 
To cut a long story short, the solution that worked for me (on my HP compax V6000 series laptop) was to ugprade the sound drivers to the latest version from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) . Your laptop may need a different solution and there are threads to help you  if you search. 
Alternatively you could log on to IRC #alsa chatroom and ask for help from the community. (ALSA stands for Advanced Linux Sound Architecture - the stuff that makes sound work ) 
Dont think this is a smartass reply. I am just sharing what i learned about linux and life that the best solution is right under your nose and you and only you have to make an effort to find it.
By the way , dont worry so much about your age. I am probably older than you and have no trouble leaning new things every day. 
Regards and good luck

---

### Post by spinny on 2007-11-10
hey thanks for the reply... i have done some searching, and have tried a couple of solutions that i saw was recommended. unfortunately either i messed it up or they did not work, i do not know. Like i said i am new to ubuntu, and i am getting up to speed on the lingo slowly.

I will try to learn more, but i need some one to walk me through helping me out till i get my feet on the ground. (i would love to watch a bunch of the ubuntu video's on youtube to help me learn more) i am a visual learner, and being in my 40's it gets harder to pick up something new. I sense Linux is the wave of the future, and i strive to learn, i just need a kick start. 

Thanks for all your help, and any that might be forth coming.

peace

---

### Post by spinny on 2007-11-10
i believe the term is ....

"bump"

lol
Hp9614ca

---

### Post by spinny on 2007-11-11
Well i guess it is time to say goodbye to ubuntu for now.... 

Just can not stand having no sound!

DAMN.... back to vista.

---

### Post by fpscott on 2008-02-23
What worked for me with my HP Pavilion DV9700 laptop, and also for a friend with a Dell laptop with the same problem, was to open terminal and type the following line. You'll be asked for your root password. After this finishes installing, reboot your computer, and you should have sound. Good luck!

sudo apt-get install linux-backports-modules-generic

Frank

---

### Post by konungursvia on 2008-02-24
Do you have the Azalia card spinny? If so, it may help to install the alsa backports.

---

### Post by wandalalakers on 2008-02-24
I have a Dell D620 laptop and I can't hear any sound.
I did hear sound when Ubuntu 7.10 was installed on my laptop.
After reformatting my laptop and putting Kubuntu on it, I have no sound.
I wonder what would happen if I used to sudo apt-get command to convert kubuntu to ubuntu?

---

### Post by Wayfarer247 on 2008-02-24
I have an HP dv9700 also, and that solution didn't work.  I tried:
> 
sudo apt-get install linux-backports-modules-generic

What else can I check that may be wrong?  Eg:  If the system is auto controlling my sound.  A great step by step guide to getting this to work would be very helpful.  I'm pretty knowledgeable about linux, this is my second install, so i can do some stuff.  Help would be great!

---

### Post by superprash2003 on 2008-02-25
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by wandalalakers on 2008-03-05
> **fpscott said:**
> What worked for me with my HP Pavilion DV9700 laptop, and also for a friend with a Dell laptop with the same problem, was to open terminal and type the following line. You'll be asked for your root password. After this finishes installing, reboot your computer, and you should have sound. Good luck!

sudo apt-get install linux-backports-modules-generic

Frank

I did the above and I still don't have sound.
I have a Dell D620.

---

