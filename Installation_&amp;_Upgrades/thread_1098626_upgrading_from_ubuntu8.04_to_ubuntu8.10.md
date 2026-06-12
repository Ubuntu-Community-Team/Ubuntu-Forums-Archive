---
title: "upgrading from ubuntu8.04 to ubuntu8.10"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by iam_newhere on 2009-03-17
hi, i am a newbie in the ubuntu environment and communtiy.
i just recently installed a ubuntu8.04 using wubi to dual boot to my vista.
turned out to be great with some issues, webcam and wine to play warcraft3 tft. 
but anyways here's my question. is it better to upgrade to ubuntu8.10 or to just stay on ubuntu8.04 performance and security wise and everything else considered?

thanks! appreciate your much needed advice!:D

---

### Post by raghavendran_te on 2009-03-17
I would say going to ubuntu 8.10 is good. Generally updates fix up problems, enhance the securities and so on. If your intention is just to play games, 8.04 should be more than enough.

---

### Post by FrostDust on 2009-03-17
In general, you're not missing out on anything critical, but it's still worth it. Being an LTS, there's nothing wrong with sticking with 8.04 unless you're eyeing a new feature/program.

This is a good list of the new things included:
[http://www.ubuntu.com/testing/intrepid/beta#New%20Features%20since%20Ubuntu%208.04](http://www.ubuntu.com/testing/intrepid/beta#New%20Features%20since%20Ubuntu%208.04)

Also, here are some of the bugs in the new version:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

One of the bigger issues to be concerned with is, because a new version of Xorg is used in 8.10, some older video cards are no longer supported under the binary drivers, and are switched to using the open-source drivers when upgrading. This equates to not being able to use Compiz, or get high performance for 3D games. Check the second link to see if your card is listed.

---

### Post by iam_newhere on 2009-03-17
wow! thanks! i dont think my intel GMA 950 and intel 82945G can handle ubuntu8.10.

---

### Post by FrostDust on 2009-03-17
> **iam_newhere said:**
> wow! thanks! i dont think my intel GMA 950 and intel 82945G can handle ubuntu8.10.

From that thing I linked before, it looks like my caveat about not supporting Compiz only applies to older cards from ATI and NVidia; it only mentions Intel 830 & 845 cards as being incompatible. It doesn't mention anything about the Intel 950, so your setup should be fine under 8.10.

---

### Post by iam_newhere on 2009-03-17
oh okay. sorrry im just a beginner. 

to frostdust: what version of ubuntu are you using?

---

### Post by Therion on 2009-03-17
> **iam_newhere said:**
> ... is it better to upgrade to ubuntu8.10 or to just stay on ubuntu8.04 performance and security wise and everything else considered?

thanks! appreciate your much needed advice!:D
Not trying to throw a wrench in the works but Jaunty is due out in just a couple weeks and from what I have experienced with it over the past month or so, it's going to be one heckuva a good release.  Might be worth waiting for.

---

### Post by iam_newhere on 2009-03-17
> **Therion said:**
> Not trying to throw a wrench in the works but Jaunty is due out in just a couple weeks and from what I have experienced with it over the past month or so, it's going to be one heckuva a good release.  Might be worth waiting for.

is it possible then to skip ubuntu8.10? i mean can i upgrade from ubuntu8.04 to ubuntu9.04?
thanks.

---

### Post by avtolle on 2009-03-17
> **iam_newhere said:**
> is it possible then to skip ubuntu8.10? i mean can i upgrade from ubuntu8.04 to ubuntu9.04?
thanks.
You will need to do a fresh install of 9.04. That means downloading the iso, burning it as an image to cd, and then installing it to the partition where 8.04 is presently. Should you want to do a "network" install, then you would first need to upgrade to 8.10 then to 9.04.

OOPS: Just reread your first post where you discuss installing via Wubi. In that case, AFAIK, you would need to do a "network install", which means, as noted above, you would first need to download and totally update 8.10, then go to 9.04. Otherwise, you would need to install Ubuntu on its own partition(s) to create the traditional dual boot case.

---

### Post by FrostDust on 2009-03-17
> **iam_newhere said:**
> oh okay. sorrry im just a beginner. 

to frostdust: what version of ubuntu are you using?

8.04. The problem I mentioned is the one I'm having. I have an Nvidia Geforce FX 5200, which isn't supported by the new binary nvidia driver that the new version of Xorg in 8.10 uses. If there's some way to upgrade to 8.10 without changing Xorg, then I'd be golden.

---

### Post by iam_newhere on 2009-03-17
> **avtolle said:**
> You will need to do a fresh install of 9.04. That means downloading the iso, burning it as an image to cd, and then installing it to the partition where 8.04 is presently. Should you want to do a "network" install, then you would first need to upgrade to 8.10 then to 9.04.

OOPS: Just reread your first post where you discuss installing via Wubi. In that case, AFAIK, you would need to do a "network install", which means, as noted above, you would first need to download and totally update 8.10, then go to 9.04. Otherwise, you would need to install Ubuntu on its own partition(s) to create the traditional dual boot case.

so do i have to do a fresh install or a network install?

im really really sorry for asking too many questions im just confused.

thanks again!

---

### Post by iam_newhere on 2009-03-17
and btw i found this site for doing a network install:
[https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations](https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations)

what method should i choose?

---

