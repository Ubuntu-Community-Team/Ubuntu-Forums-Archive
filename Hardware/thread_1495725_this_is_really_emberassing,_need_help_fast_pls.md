---
title: "this is really emberassing, need help fast pls"
date: 2010-05-28
forum: Hardware
---

### Post by LutraMan on 2010-05-28
I just convinced my mom that she should have linux instead of windows because it's better.
oh the embarrassment!
I installed 10.04 netbook version using DOK.
the installation went smoothly but on the 1st run ubuntu did not recognize the wireless. I connected using a wire and let it update. it seemed to fix the problem but today she used the computer and after a while closed the lid. when she opened it again it only showed the mouse on a black screen(!!!) brutal restart was required. I checked, it was not a one time thing, it happens every time I close the lid. also, the wireless is again no where to be found, and now I can't fix the problem.

it's a Compaq presario CQ61.
pls plz plzzzzz help me, B4 I turn out as a complete doosh.

---

### Post by oracle2b on 2010-05-28
you can try avoiding the lid problem by changing the close lid settings in system->preferences->power management.

---

### Post by oracle2b on 2010-05-28
Your wireless card could be a broadcom chipset so you might want to try etheir the proprietary driver or open source driver. System -> Administration -> hardware Drivers.

---

### Post by LutraMan on 2010-05-28
tnx I'll give it a shot.

but anything else pls about the other bugs, wireless?
if you need anymore details, please tell me what you need, I'll get it right away.

tnx for all help in advanced...

---

### Post by marcottebj on 2010-05-28
You said you had the wireless card working at one time before she closed the lid?

---

### Post by oracle2b on 2010-05-28
there may be a solution [here]("http://ubuntuforums.org/showthread.php?t=1341618&highlight=CQ61#5") or [here]("http://ubuntuforums.org/showthread.php?t=1240063#2").

---

### Post by kiddykoff on 2010-05-28
try running lshw and see what kind of wireless chipset you have. I've had a broadcom chip before and i've had to install a wrapper around a windows driver. I've changed laptops since, but i've heard that you can enable the wireless through system>administration>hardware

If it's not a broadcom chip i would try going into system>preferences>power management and disabling any power saving options.

also, next time run a live cd to see if everything is operational first.

---

### Post by LutraMan on 2010-05-28
alright, here is the thing.
I turned on network tools via administration, and told it to "look at" the wireless device (wlan0) witch surprisingly was there (not a driver problem, then) 10 secs later, wireless device started operating (weird!)

I went to the power setting and saw the when I close the lid, it goes to suspend, and changed it just to blank screen.

that fixed the lid problem.

now I can say that my problem is no longer critical. BUT(!) it is still a problem, since it just a workaround. if it was my computer I wouldn't care. but my mom is not a computer wiz. If I leave it like that, it will just come back to hunt me later. (and by "it" I mean my angry mom with a bug in her computer)

So I checked. manually told it to suspend. when it came back it asked me for a password. typed it in, told me it was wrong (it might have been really wrong) and then went blank.

CTRL-ALT-F2 got me to a terminal that just kept showing errors that if you tell me how I would copy here. right now I can't since it showed them too fast.

tnx for all your replies so far, and if you have any ideas about where to move on, anything at all, plz, feel free to contribute to the brainstorming.

---

### Post by adampyre on 2010-05-29
Are you having a suspend hibernate issue? I was having them with my laptop with 10.04, and finally found a fix. It's worth a shot. I just followed to instructions by John Dias a few down in the post: [http://ubuntuforums.org/showthread.php?t=1444822](http://ubuntuforums.org/showthread.php?t=1444822)

Follow his instructions exactly, then test hibernate and suspend. If that works for you, I'd go back into power management and set it so the netbook suspends upon lid being closed. 

LEt me know if that works for you.

---

### Post by LutraMan on 2010-05-30
Hi,

tried what John posted, it didn't worked.

I sent him a PM so he'll help me see that I've done it all right, but by his low activity profile, I doubt he'll see anytime soon.

pls, if you have anymore ideas about what might help, or how do I get relevant error logs from my computer, pls feel free.

tnx

---

