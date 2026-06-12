---
title: "thinkpad t400 problems"
date: 2011-02-24
forum: Hardware
---

### Post by Toffefe on 2011-02-24
Hi! I just bought a used t400, my first thinkpad, and I have some questions about running ubuntu 10.10 on it.

I've searched this forum for people with the same problems but most of  the threads is related to older versions of ubuntu. My problems are: 
* it wont suspend, today I also got an errormessage saying ubuntu cant  suspend and the "suspend" and "hibernate" button disappeared  from the  dropdown menu in the top right corner.
The battery wont last more than 30min, and when idle or typing in vim  the cpu stays between 55-65 C degrees. I read somewhere that sometimes  ubuntu would turn on the second gpu and use lots of power but is this  possible in ubuntu 10.10?
I've also seen lots of forums full of threads about the wireless card in  this laptop, so my question is, is there still bugs with it? today i  got timeouts and hangups when browsing through sites on a 10 Gbit/s  Internet connection.
There is even more problems like the fingerprint scanner doesnt work and  other stuff but for now my main concern is getting it to suspend and  maximising the batterylife/time.

By the way, it a 4gb, p8600 with 64bit os.
Last question, does anybody know of a good program to measure/display battery consumption?

Regards,
toffefe

---

### Post by Toffefe on 2011-03-03
Doesn't somebody know how to fix these things?
I fixed the battery problem by disabling switchable graphics in bios so the power consumption dropped from 30+W to about 15W.
But the real problem for me is the suspend issue. If i close the lid or use the keyboard hotkey to suspend ubuntu still runs and a window appear 
[B]/*
Failed to suspend[/B]

Computer failed to suspend.

Failure was reported as: Cannot suspend
*/
This is extremely annoying because now I have to close all programs and shut it down instead. Usually I suspend my laptop at least 10 times a day running from lectures to lectures++.
Can anyone help me?

Regards,
Toffefe

---

### Post by HankB on 2011-03-03
The best I can suggest is to check [http://www.thinkwiki.org/wiki/Category:T400](http://www.thinkwiki.org/wiki/Category:T400) for additional information.

I have a T500 and (IIRC) had to set up something to unload the WiFi driver to enable suspend/resume. (I presume you mean suspend and not hibernate.)

I do not have the power problems, but I also do not have the second graphics adapter.

At the moment I am here because since the kernel upgrade I installed yesterday, WiFi is nearly unusable, ranging from 30-45% packet loss reported by ping at best and no connection at worst. :(

I'm considering upgrading to 10.10 (from 10.04) to see if it solves this problem, but maybe I should be going the other direction. It seems like recent releases do not play well with my H/W.

I have a Netbook (Eee PC 901) that also used to run well, but since upgraded to 10.10, it no longer suspends.

Apologies for not providing a better answer.

---

