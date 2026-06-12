---
title: "X61 And Gutsy ( extremely hot cpu )"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by _SMD on 2007-12-29
Hi there.

I just bought X61 (7673A24), My Spec : Core 2 Duo 1.83Ghz, 80GB HDD, 1GB RAM. 

I've installed Gutsy Gibbon, and all works like a charm. But I've a serious problem that the palmrest (near the fingerprint scanner) runs quite hot. It doesn't like that with Windows Vista ( where my X61 comes with pre-installed vista ). Anyone know how to fix this? Thanks in advance.

---

### Post by w4ett on 2007-12-29
It might be a CPU Fan speed issue??  Review the post here:

[http://ubuntuforums.org/showthread.php?t=42737&highlight=lm+sensor+cpu+fan+speed](http://ubuntuforums.org/showthread.php?t=42737&highlight=lm+sensor+cpu+fan+speed)

and see if it might help you or at least point you in the right direction.

Good Luck!

---

### Post by _SMD on 2007-12-29
some people say it's wifi card problem. I don't if this is cause the issue.

---

### Post by w4ett on 2007-12-29
> **_SMD said:**
> some people say it's wifi card problem. I don't if this is cause the issue.
 IMO that is unlikely....your video chipset and CPU are the biggest generators of heat, aside from power supply circuitry.

---

### Post by fixture on 2007-12-30
see if you are running firefox when you experience the heat, I have a 2Ghz X61 and I have reached 86 degrees before, the problem seems to be that firefox was preventing the CPU from properly entering sleep modes. Apparently firefox was doing that because there were too many scripts running on some webpages. I just installed the no-script plugin, problem solved. Also, you can blackist uhci_hcd, that is the USB 1.1 module that generates a lot of cpu wakeups and therefore heat.

---

### Post by _SMD on 2007-12-30
thanks fixture. I'll try your suggestion.

---

### Post by 3rods on 2007-12-31
_SMD were you able to fix the issue?

I'm probably going to pick out an X61 today and was wondering how you liked ubuntu on it. 

Not to downplay the awesomeness of ubuntu, but from what I understand SUSE is "supposedly" certified on the X61 (and I think the T61p as well).

---

### Post by _SMD on 2007-12-31
> **3rods said:**
> _SMD were you able to fix the issue?

I'm probably going to pick out an X61 today and was wondering how you liked ubuntu on it. 

Not to downplay the awesomeness of ubuntu, but from what I understand SUSE is "supposedly" certified on the X61 (and I think the T61p as well).

No. The heat is still there. Ubuntu gutsy works great with X61. I tried with SUSE Enterprise, but installation process failed. I found other people also facing this problem, with [windows]("http://forums.lenovo.com/lnv/board/message?board.id=X_Series_Thinkpads&message.id=24") too. So, I think this is x61 issue. :( This is bad... ohh

---

### Post by fixture on 2008-01-01
3rods, go for the X61 you can't really do better

_SMD, are you familiar with powertop? can you give me an output from the powertop screen? ctrl+print screen will work just fine, or however you choose to take the screen shot

---

### Post by _SMD on 2008-01-01
fixture,

as attached. any suggestion to solve this problem would be greatly appreciated.

---

### Post by fixture on 2008-01-01
it's definitely not the problem I had, my system use to have the CPU in C0 all the time, how do you know that your fan is not defective?

---

### Post by _SMD on 2008-01-01
> **fixture said:**
> it's definitely not the problem I had, my system use to have the CPU in C0 all the time, how do you know that your fan is not defective?

i use ondemand setting. that's why mine is C3. anywhere are u using X61 too? how's yours? it's getting hot after 20-30 minutes?

---

### Post by fixture on 2008-01-01
_SMD, the CPU should be in C3 on a regular basis, ondemand, performance and other power governors only adjust the frequency and the ACPI C-states are not really related to the frequency. No matter how high of a freqency the CPU is flying at, the CPU should be spending most of its time in C2 and C3.

I do run a X61, the laptop runs around 50 centigrade. The thing is, you also have the same problem in Windows, have you checked your BIOS power settings? By the way, 100-600 wakeups are pretty normal, it should start heating your computer only in the 1000 range. So it's not really a Linux problem.

---

### Post by _SMD on 2008-01-01
> **fixture said:**
> _SMD, the CPU should be in C3 on a regular basis, ondemand, performance and other power governors only adjust the frequency and the ACPI C-states are not really related to the frequency. No matter how high of a freqency the CPU is flying at, the CPU should be spending most of its time in C2 and C3.

I do run a X61, the laptop runs around 50 centigrade. The thing is, you also have the same problem in Windows, have you checked your BIOS power settings? By the way, 100-600 wakeups are pretty normal, it should start heating your computer only in the 1000 range. So it's not really a Linux problem.

I see. ok another thing I would like to ask you since you're using gutsy on x61. How long is your battery life?

---

### Post by fixture on 2008-01-04
depends on what you are willing to give up to reduce the wakeups, when I keep compiz but lose wireless and wired on the 4 cell I get about 2:40. not sure about the 8 cell

---

### Post by _SMD on 2008-01-04
> **fixture said:**
> depends on what you are willing to give up to reduce the wakeups, when I keep compiz but lose wireless and wired on the 4 cell I get about 2:40. not sure about the 8 cell

I managed to get 5:30 battery life on the 8 cell.

---

### Post by mbsullivan on 2008-01-06
Hi,

From the powertop output, it looks like speedstep is working for you and everything else looks normal.  I too have an X61, though without a fingerprint reader.  I remember people complaining about the heat underneath the hand rests in reviews before I bought it, so I think it's probably just a hardware issue. 

If you want to check if the network card is causing the heat, switch the wifi off on the front of the laptop.  Does the surface get any cooler?

Also, we can monitor temperatures and make sure that your CPU fan is operating properly through the thinkpad_acpi file handles.  Go to /proc/acpi/ibm and look at the output of:

```
cat fan
```

and

```
cat temperature
```

Also, for just the CPU, give the output of:

```
cat /proc/acpi/thermal_zone/THM0/temperature
```

and

```
cat /proc/acpi/thermal_zone/THM0/temperature
```

Assuming that the fingerprint reader is on the bottom right-hand corner of the laptop, it's sandwiched right between the harddrive and the RAM, and on the opposite corner from the CPU, so my guess is it's not a CPU heat issue, anyway.  

With my laptop, I'm running a fan speed daemon which disables the CPU fan until the temperatures get very hot, so my CPU idles at fairly high temperatures.  The laptop is warm underneath my hands, but not uncomfortably so... how hot does yours get?  Is it unpleasant to leave your hand over the fingerprint reader?

Hope this helps... my guess is that there's not much you can do to reduce the heat.  Perhaps using laptop-mode to park your harddrive 99% of the time would keep it cooler underneath your hands.

Mike

---

### Post by subtex on 2008-01-08
seems there are a few threads here all about the same issue.

HAs anyone tried the Hardy release to see if this problem persists?  My X61t is super hot under the right palm. I"d love to see this fixed somehow.

--edited to say I just burned a cd of Hardy. Gonna get the Live CD up and running and see how the temps fare after 15 mins.

---

### Post by Vorl the Magnificent on 2008-05-20
I recently acquired a standard x61 with the 2.1ghz standard voltage processor and an Intel wi-fi card.  I'm running Hardy, and am also having the right-hand palmrest heat issue.  As has been suggested above, I suspect that this is simply a hardware issue.  It likely stems from the very small dimensions of this unit.  According to what I've read, there are palmrest heat issues with all models of the X61, including the low-voltage X61s (which is what caused me to get the cheaper X61, as battery life is essentially a non-issue for me, and the only thing that would compel me to buy a slower low-voltage processor is to reduce fan noise and palmrest heat).  I honestly didn't expect the palmrest heat to be a big deal, but it really is, because the palm doesn't simply rest on the palmrest; it rests there much of the time with a good bit of pressure and surface-to-surface contact contributing to the conduction of some serious heat into the hand.

The heat issue is actually addressed in the X61's package documentation.  The warnings in the manual direct the user to avoid using the keyboard for long periods of time (!) and to take frequent breaks to minimize the risk of skin burns (!!).

On forums specific to Lenovo laptops, some users have suggested that the heat buildup is due to the wifi card's occlusion of the right-hand air vent, which opens on the right-hand side of the keyboard.  I've experienced my X61 blowing cool air out of the fan vent even as the temperature of the right-hand palm rest remained warm, and I've never detected any airflow whatsoever -- in or out -- from the right-hand vent.  I would imagine that whatever the heat-generating component is, it's sitting there without ventilation under a dense, black, thermally conductive plastic.  I was initially concerned (because I'm predisposed to paranoia) that the wifi card might be so constructed as to inadvertently generate microwave emissions, which could be slowly cooking the right hand.  (To be honest, I'm still a bit troubled about this possibility, irrational as I suspect it to be).  After I switched off the wifi on the front of the laptop and the radio frequency in the BIOS, however, I noticed no detectable difference; so it's probably just some other hot little part in there combined with a lack of sufficient ventilation.

My solution has been to cut a section from a cheap, cloth-topped mousepad and place that over the offending area of the palmrest.  Because the rubber conducts heat, it's an imperfect solution; but far less heat reaches the palm with the mousepad cover than it does without it.  Ultimately, I think low-tech solutions are the way to go here, unless someone is brave enough to open the case, determine what's heating the hand and blocking the vent, and modify the thing to fix the problem.  That person isn't me.

To get back to thread-specific, Ubuntu-specific issues, though: one thing I noticed is that after I turned off the wifi radio frequency in my bios and later turned it back on, Ubuntu no longer seems to detect the card as a viable connection option.  The hardware detector application (I've forgotten what it's called, and am presently on a windows box) finds the card, but the network connection applet now only shows my wired connection and what I assume is a modem connection (?"lo"?).  Is there something under gconf-editor that I can tweak to get it to display the wireless again, or some service that I need to re-enable, or what?  Suggestions would be appreciated.

-VoTMagn.

---

