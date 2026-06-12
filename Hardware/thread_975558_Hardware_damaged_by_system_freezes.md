---
title: "Hardware damaged by system freezes"
date: 2008-11-08
forum: Hardware
---

### Post by Bödvar on 2008-11-08
Hello. Is there any evidence to suggest that when your system freezes and you have to turn the computer off and on without shutting down, that you can damage your hardware? Firefox has freezed my system a couple of times now, and I'm wondering whether it would be safer just to stop using it?

---

### Post by Bödvar on 2008-11-09
bump

Please, even an opinion is welcome. Thanks.

---

### Post by kostkon on 2008-11-09
> **Bödvar said:**
> Hello. Is there any evidence to suggest that when your system freezes and you have to turn the computer off and on without shutting down, that you can damage your hardware? Firefox has freezed my system a couple of times now, and I'm wondering whether it would be safer just to stop using it?
Don't think so. Of course reboots always put stress on hardware and I believe systems that reboot rarely last longer that systems that are rebooted very often. But this is just my feeling, there aren't any statistics to back this up (none I know of).

Do you actually mean that you are pressing the On/Off button of your PC and you hard reboot without Shutting Down Ubuntu? If that's the case, then there is the danger of damaging your filesystem and losing data or destroying Ubuntu altogether.

It seems to me that Firefox crashes X. When that happens instead of hard rebooting, you could try pressing ALT+CTRL+BACKSPACE to restart X. It will put you back on the login screen.

If it crashes your system in general (and not only X) the you could try doing the REISUB key combination. You can get more info about this [here]("http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php").

You could try reinstalling Firefox (better do a Complete Removal, but keep a backup of your profile before doing it). You could also check your system logs after the crash for any error messages. This will help you to get an idea of what is causing this. Also, check your graphics card and what driver you are using.

If nothing solves you problem, then there are other good options, like Epiphany, Opera, etc.

---

### Post by Bödvar on 2008-11-09
Thanks a lot for your help. How do I differentiate between the System and the X?

---

### Post by kostkon on 2008-11-09
> **Bödvar said:**
> Thanks a lot for your help. How do I differentiate between the System and the X?
When you get a crash try the CTRL+ALT+BACKSPACE combination. If this will recover your system and put you on the login screen then it means that X crashed. 

If it does not do anything, then it means that the crash is more serious. You should then try the REISUB solution.

Do you remember what type of pages make Firefox to crash. It may be a Flash related problem.

What version of Ubuntu are you using?

---

### Post by Bödvar on 2008-11-09
> **kostkon said:**
> When you get a crash try the CTRL+ALT+BACKSPACE combination. If this will recover your system and put you on the login screen then it means that X crashed. 

If it does not do anything, then it means that the crash is more serious. You should then try the REISUB solution.

Do you remember what type of pages make Firefox to crash. It may be a Flash related problem.

What version of Ubuntu are you using?
It's just random pages. Gmail, Ubuntuforum, Last.fm... Should I uninstall my Flash driver? I recently installed the non-free version, but I have had freeze troubles before that.

My Ubuntu version is 8.10

---

### Post by RadicalRaid on 2008-11-09
Seems like I'm having the same trouble over here. Only not sure that it's firefox. I don't know exactly how to check for apps that were causing trouble, seems like the system log in administration is no help. Otherwise I might have been able to pinpoint the troublemaker. I also use the hard reboot ( holding down the on/off for 5 seconds ), so I might as well give the REISUB way a try when it happens again ( and it most likely will ).

My guess though, from what I've seen with other Ubuntu users, is that it's probably in the videocard driver. My guess is that you are using the restricted drivers from nVidia or Ati?
Seems like they can be quite troublesome..

Please let me know when you find anything out, I'm really getting anoyed by this too.

---

### Post by RadicalRaid on 2008-11-09
Update:
I crashed in about 10 minutes after my post and found out the REISUB method didn't work for me. I've tried multiple key combinations just in case, but without success.
I really really love Ubuntu and the entire philosophy behind it, but this is just going to be bad for my new laptop.. Not something I want to risk..
I hope this gets updated soon, or better yet, fixed :).

---

### Post by RadicalRaid on 2008-11-09
Something I noticed:
Whenever my system fully crashes, the Caps-Lock light starts blinking. Don't know if it's any indication for something. I'm gonna look into it some more.

---

### Post by Bödvar on 2008-11-09
Thanks RadicalRaid for your input. I've found that ever since I installed the graphics card driver (which is restricted), I have not experienced a system freeze again. Maybe they updated the driver today, so try deactivating and redownloading it.

---

### Post by RadicalRaid on 2008-11-09
I did just that. I'll keep you posted!
Also, I did a harddisk check using the liveCD but no errors were found on my Ubuntu disk, so that's probably not it.

---

### Post by RadicalRaid on 2008-11-09
Unlucky.. Though it went fine for a lot more time than usual, it still crashed when I walked away from it for a couple of minutes.
Is it working for you?
Cheers!

---

### Post by Bödvar on 2008-11-09
My system has been up after I followed these steps for the better half of the  day! It's unbelieveable! And I'm using Firefox for browsing all different kinds of sites... haven't tried it with some addons yet... too afraid something happesn :/

---

