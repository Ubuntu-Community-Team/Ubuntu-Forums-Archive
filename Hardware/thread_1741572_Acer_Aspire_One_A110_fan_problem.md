---
title: "Acer Aspire One A110 fan problem"
date: 2011-04-28
forum: Hardware
---

### Post by Tootler on 2011-04-28
I'm having problems with my AAO fan control.

I have installed Maverick to replace the original Linpus and I cannot get the fan to switch off unless needed.

I followed the solution given in this thread

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=19702](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=19702)
com
It did not work - or at least it seems to work partially. The fan cycles on and off for a while before remaining permanently on but at reduced speed.

I found this thread:

[http://ubuntuforums.org/showthread.php?t=1424043&highlight=Acer+aspire+fan](http://ubuntuforums.org/showthread.php?t=1424043&highlight=Acer+aspire+fan)

After reading it I issued the command 

sudo modprobe acerhdf 

at the terminal. That has had no effect and the situation remains the same. There is a long process involving reinstalling the kernel, but that seems to be for a different model of Acer computer. Also it seems unnecessary to me a I only installed 10.10 yesterday, though it had been lying on my other computer for a couple of weeks, nevertheless the kernel should be pretty much up to date.

So now I am stuck.

Geoff

---

### Post by mörgæs on 2011-04-28
Have you tried a fresh install of 11.04?

---

### Post by Tootler on 2011-04-29
> **mörgæs said:**
> Have you tried a fresh install of 11.04?

It is a fresh install, albeit 10.10 rather than 11.04. I had downloaded it about 3 weeks ago (just before 11.04 came out) but had only just got round to installing. Dealing - or attempting to deal - with the fan issue was practically the first thing I tried.

Upgrading to 11.04 might be worth a try, though.

---

### Post by mörgæs on 2011-04-29
I would not recommend upgrading (if you mean online upgrading). A fresh install of 11.04 is a much better foundation for troubleshooting.

---

### Post by Tootler on 2011-04-29
> **mörgæs said:**
> I would not recommend upgrading (if you mean online upgrading). A fresh install of 11.04 is a much better foundation for troubleshooting.

What value would a fresh install of 11.04 given I only just made a fresh install of 10.10?

I have tried deleting the acerhdf.conf file just in case I had mistyped something and recreating it and that has had no effect. At the moment the fan is running but more slowly though the computer has been on for sometime so it is quite warm. I checked the temperature a few minutes ago and the temperature was 52 which is still below both fanon and fanoff temperatures.

Geoff

---

### Post by Tootler on 2011-04-29
I've managed to figure out what is happening but I don't know why it is happening nor how to fix it.

When I set up the file /etc/modprobe.d/acerhdf.conf, I followed the suggestion of making the parameters

options acerhdf interval=5 fanon=60000 fanoff=55000 kernelmode=1

I came across another set of parameters with and interval of 10 so I increased the interval to 10. As a result the fan comes on less often. 

It seems what is happening is that every time the system checks the temperature, the fan comes on then if the temperature is below the fanon temperature, the fan switches off again.

Clearly what should happen is that the fan should remain off until the fanon temperature is reached. How to make the system do this? Suggestions welcome.

Geoff

---

### Post by mörgæs on 2011-04-29
> **Tootler said:**
> What value would a fresh install of 11.04 given I only just made a fresh install of 10.10?


Someone might have fixed the problem during the development of 11.04!

---

### Post by Tootler on 2011-04-30
> **mörgæs said:**
> Someone might have fixed the problem during the development of 11.04!

In which case why not simply upgrade? Your earlier reasoning did not really make sense to me; after all if what you say is the case, upgrading will probably still install new versions of whichever software is causing the problem.

My earlier experience with upgrading vs fresh install suggest that new versions of the software providing core functions get replaced and it is the more cosmetic stuff that is left relatively unaltered.

Either way, I am still looking for suggestions as to ways to deal with the problem, preferably without having to upgrade, though I will almost certainly do that eventually, but I don't really want to just yet if I can avoid it.

---

### Post by mörgæs on 2011-04-30
In theory an online upgrade works, but in reality it is a risky process which often renders the system fubar. You can judge yourself by the number of posts concerning failed upgrades in the fora these days.

11.04 has the 2.6.38 kernel. It is not only cosmetics.

---

### Post by Tootler on 2011-05-01
> **mörgæs said:**
> In theory an online upgrade works, but in reality it is a risky process which often renders the system fubar. You can judge yourself by the number of posts concerning failed upgrades in the fora these days.

11.04 has the 2.6.38 kernel. It is not only cosmetics.

Fair comment, though using posts on fora to judge the overall success rate of online upgrading will overstate the problem as those who upgrade successfully will not be expected to seek help. So far I have managed to upgrade successfully without problems, including a "double" upgrade (9.04 via 9.10 to 10.04).

The clear message is to make sure that all your data is backed up and to have a disk/usb stick with 11.04 on before trying the online backup in case things go wrong.

---

### Post by Tootler on 2011-05-04
After some thought, I decided to go back to 10.04.

I had installed wine, but there was no launcher for setting up wine and running installed software on the LH panel. 

I had looked in the wine subforum here and in the forum at wineHQ and it appears this is an issue that needs sorting. Until that is sorted, I will stick with 10.04 as it is a LTS version and that suits me on the whole.

I think overall I would prefer to let the new unity desktop settle - there is also Gnome 3 imminent and I am sure there will be teething problems there. 

I will have to live with the fan problem, though I have minimised it by reducing the frequency that it checks the temperature to 30 sec and increased fanon and fanoff to 65000 and 60000 respectively.

---

### Post by mörgæs on 2011-05-04
Good, please mark the thread 'solved'.

By the way, have you tried installing the CPU monitor to the top panel? Using this you can lower the frequency and save some CPU heat.

---

### Post by Tootler on 2011-05-05
> **mörgæs said:**
> Good, please mark the thread 'solved'.

I don't think it's appropriate to mark the thread as 'solved'. I have not really solved the problem, rather taken steps to minimise its impact and it's always possible (though, I suspect, unlikely) that someone will come along with a proper solution. 

For that reason, I'd rather leave it open, if you don't mind.

> 
By the way, have you tried installing the CPU monitor to the top panel? Using this you can lower the frequency and save some CPU heat.

Thanks for the tip. I'll give it a try. I'll have to figure out how to do it in the desktop used in the netbook version of lucid. (Xfce, IIRC - certainly different from standard Gnome).

Cheers

Geoff

---

