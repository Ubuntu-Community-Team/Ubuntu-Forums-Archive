---
title: "Thunderbird stalling"
date: 2008-09-15
forum: General Help
---

### Post by reader4 on 2008-09-15
Hardy 64-bit.  This started a couple of days ago... whenever I start Thunderbird and begin to type a new message, the app slows way down (not a freeze, but the words I type take up to a minute to appear) and CPU use is nearly 100%.  Anyone else experiencing this? Constantly having to kill the app is why I switched from Evolution to Thunderbird in the first place! The first time it happened, I used 'killall evolution' by mistake - old habit.  I'll try testing it a bit before looking at bugs, but just wanted to find out if I was the only one having trouble...

---

### Post by Sycron on 2008-09-15
Which application is using so much CPU ? You can see that with *htop*.

Install it:```
sudo apt-get install htop
```
And run it:```
htop
```
Tell us which process is so angry...

---

### Post by macvr on 2008-09-16
> **reader4 said:**
> Hardy 64-bit.  This started a couple of days ago... whenever I start Thunderbird and begin to type a new message, the app slows way down (not a freeze, but the words I type take up to a minute to appear) and CPU use is nearly 100%.  Anyone else experiencing this? Constantly having to kill the app is why I switched from Evolution to Thunderbird in the first place! The first time it happened, I used 'killall evolution' by mistake - old habit.  I'll try testing it a bit before looking at bugs, but just wanted to find out if I was the only one having trouble...

i'm also experiencing the same prob... in hardy x86
for me also started recently , i get it at random ,probably more while receiving mail with attachments

i'v checked in system monitor ,when it froze, that"**[COLOR="Red"]thunderbird-bin[/COLOR]**" was using the CPU to the max

will also report back with the above sugggestion...

---

### Post by reader4 on 2008-09-16
Sorry I didn't specify more clearly... thunderbird-bin is taking up ~100% CPU.

macvr, do you have the Send Later extension? 

In my case, disabling the Send Later extension seems to have resolved my problem.

---

### Post by macvr on 2008-09-16
> **reader4 said:**
> Sorry I didn't specify more clearly... thunderbird-bin is taking up ~100% CPU.

macvr, do you have the Send Later extension? 

In my case, disabling the Send Later extension seems to have resolved my problem.

nope...

i have webmail 1.3.2,webmail-yahoo, webmail-hotmail...

[COLOR="Blue"]is there anyway to see the past SYNAPTIC update history?[/COLOR]
i think that thunderbird was updated around a week back, i think that,that particular update messed up thunderbird[not very sure,thats y i want to check update log]

---

### Post by macvr on 2008-09-17
i think i'v found a pattern...
it freezes when typing a mail, while recieving a mail simultaneously at the same time!

---

### Post by Sycron on 2008-09-19
It may be a BUG. You can report it to launchpad.com, BUG section.

---

### Post by macvr on 2008-09-19
aaaaaaaaaaahhhh..... stupid bugs!!!!

thats 1 thing i hate about ubuntu..... too many bugs... ok...few bugs!!!

it gets difficult to use for noobs like me

---

### Post by Antonio Tavares on 2010-07-17
> **macvr said:**
> aaaaaaaaaaahhhh..... stupid bugs!!!!

thats 1 thing i hate about ubuntu..... too many bugs... ok...few bugs!!!

it gets difficult to use for noobs like me

I'm having the same problem on Ubuntu 10.04, and I'm also feeling it is getting closer and closer to Windows. But I say that because apart from the ocasional game or sincronizing the TomTom GPS or my Samsung Wave, I'm not using Windows on my desktop since a couple of years, otherwise I'm sure I would be stumbling with worse problems, like my clients do (I work on IT).

---

