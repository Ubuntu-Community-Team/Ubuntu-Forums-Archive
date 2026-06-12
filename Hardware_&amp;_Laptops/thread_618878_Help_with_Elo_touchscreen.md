---
title: "Help with Elo touchscreen"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by shad0w_walker on 2007-11-20
For the last 2 days I have been trying to get the Elo touch screen in my ppc-123t (Panel PC, made by advantech) and today I got a step closer. I got output when running

```
cat /dev/ttys3
```

and touching the screen produced output. It turns out there was an IRQ conflict before, solved that now. However I have hit a new problem. When I configure X to use the touch screen it will produce a bunch of error messages like these:

```

Not at the specified rate or model 2310, will continue
Unable to ask Elographics touchscreen identification

```

I get a swarm of those messages and when trying to select the touchscreen pointer using xsetpointer I get informed the device cannot be accessed or is invalid, etc.

Any help or ideas would be appreciated, this is driving me nuts.

---

### Post by shad0w_walker on 2007-11-21
I have found out I have an accutouch e274 screen in the system if that helps at all.

---

### Post by shad0w_walker on 2007-11-23
Bump

---

### Post by shad0w_walker on 2007-12-29
Anyone? Dragged the machine out again and trying to get it going again.

---

### Post by ovoskeuiks on 2008-01-29
Option "debuglevel" "5"
This will allow you to see the communication between the touchscreen and the pc, you'll probably find it is not responding to requests for information from the computer.
I had an Elo Clone so I simply edited out the requests for information from the driver

---

### Post by shad0w_walker on 2008-01-29
Holy hell. A reply.

Thanks for the suggestion, I'll give it a try as soon as I get the chance. :)

---

### Post by ovoskeuiks on 2008-01-29
Yeah I had a highly unfun time trying to get this one working because of a lack of information on the web, so I'm keen to help anyone else who has problems.
Using the debug mode you'll be able to manually calibrate the screen as well but I'll tell you more about that when you get it going.
Mine is working almost perfectly except that the event queue for xorg seems to get swamped or something. Like I move my finger around and it works fine but then will stop or lag. But by pumping more events into the queue by either moving my finger more or the mouse the cursor then catches up with all movements I've made

Good Luck with getting it going

---

### Post by shad0w_walker on 2008-01-31
I don't know if the last 3 days have just been some kind of karma giving me good luck for screwing my life over or what but things have been going so damn right. I didn't need your advice after all (Just finished the normal config instructions and it just works) but I give my deepest thanks for the help anyway, I probably would have taken months to get around to trying it again without your beacon of hope.

---

### Post by ovoskeuiks on 2008-02-01
No worries mate, glad to hear it's all working

---

### Post by misko84 on 2008-03-08
hi,
i have the same problem with a ppc-153t. how did you solve it? where did you find the "normal config instructions"?

thanks in advance
misko

---

### Post by shad0w_walker on 2008-03-08
The normal instructions are for Redhat 9 and on the advantech website.

[http://support.advantech.com.tw/support/KnowledgeBaseSRDetail.aspx?SR_ID=1-LL1BP](http://support.advantech.com.tw/support/KnowledgeBaseSRDetail.aspx?SR_ID=1-LL1BP)  Those are instructions for the PPC-123T. I just followed them again and this time they worked. Not quite sure what was different to be honest. You may want to try it with a few different versions of Ubuntu (I used Xubuntu and tried with 7.04 and 7.10)

---

### Post by misko84 on 2008-03-14
so the instructions seem to be the same for the PPC-153T ([http://taiwan.advantech.com.tw/unzipfunc/Unzip/1-LX3JY/PPC153T.htm]("http://taiwan.advantech.com.tw/unzipfunc/Unzip/1-LX3JY/PPC153T.htm")).

I tried it once again, still the same problem. How did you solve the serial-reconfiguration? As described with a /etc/rc.serial or via setserial and /etc/serial.conf ? In both cases, could you please post the file? And could you give me your xorg.conf as well?

Which version of Xubuntu was finally working?

thanks in advance,
misko

---

### Post by misko84 on 2008-03-16
hi!

I finally tried it with Debian Etch, now it works. Maybe the elographics-driver in Gutsy Gibbon is buggy, or does 7.10 work for you? I`ll try it again with Hardy Heron, until then i'll stay with etch.

---

