---
title: "[SOLVED] apt-get upgrades"
date: 2008-11-21
forum: General Help
---

### Post by notsomeone on 2008-11-21
I have always relied on the update notifier to tell me when new uprades are ready, and I install them right away, but it has not been working for a couple of weeks at least.
And using `apt-get upgrade` doesn't really work. I have tried that a few times and I only get speeds of about 25 KB/s until the connection just quits.
And I tried Adept Manager this evening. It crashed on the second package I tried to update. I have 47 more packages to upgrade.
Do I have some kind of serious problem or what?

---

### Post by SuperSonic4 on 2008-11-21
It could be your internet connection crapping out or it could be a bad package.

On another note you said you use adept but have put ubuntu in the title =S

---

### Post by notsomeone on 2008-11-21
Oh sorry. I don't think there is a way to edit my title to Kubuntu now.

Yeah, I do believe it is the internet connection. My guess is it has something to do with trying to use a proxy. If it is using my proxy (Privoxy/Tor), I do not know how to make it stop.

---

### Post by notsomeone on 2008-11-22
Still hoping for some help on this.
The 25KB/s download speed that I estimated in my original post was way too high. That was like the top speed that it spikes at for a second.
I just installed a new program using apt-get and this is how fast it was:

Fetched 121kB in 13min11s (153B/s)

---

### Post by Sef on 2008-11-22
1) What version of kubuntu do you have?  

2) So you can add programs, but not update?

3) What messages do you get if you type ```
kdesu apt-get update && kdese apt-get upgrade
```

---

### Post by notsomeone on 2008-11-22
1. I have 8.04

3. Running those commands now. I usually use 'sudo', not kdesu, so the output looks a little different, and it doesn't show me the progress report.With sudo it shows me the speed and percentage complete.

Now I get something like:

$ kdesu apt-get upgrade
Reading package lists...

Building dependency tree...

Reading state information...

The following packages will be upgraded:
...(47 packages) ...

47 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 48.5MB/105MB of archives.
After this operation, 397kB disk space will be freed.
Do you want to continue [Y/n]?

So I typed 'y', and I assume it is doing something.

2. I could do upgrades and installs, only very slowly. See where it says I only need to get 48.5MB. I guess that is because it still has the files that I downloaded over the past few days, before the connection died.

---

### Post by frankleeee on 2008-11-22
> **notsomeone said:**
> Oh sorry. I don't think there is a way to edit my title to Kubuntu now.

Yeah, I do believe it is the internet connection. My guess is it has something to do with trying to use a proxy. If it is using my proxy (Privoxy/Tor), I do not know how to make it stop.

Turn off (Privoxy/Tor) and try again it is probably your problem, or a server. If you open the add-ons in FF you can click on disable for (Privoxy/Tor) probably.

---

### Post by notsomeone on 2008-11-22
Edit #2: No, the problem was not actually Squid. It was just a coincidence that updates started working slightly better. But still very slow.
I just got it really fixed today. The problem was that the repo server was insanely slow. I followed these steps to use a different server:
Go to Start Menu
System > Software Sources > Download From: Other > Select Best Server.
It picked out the best server and I just downloaded 51MB of updates in 5 minutes. That would have taken over five hours last week.
I hope that tip can help somebody else.

Edit #1: Thank you all very much for your replies. I am really a bad sysadmin. I installed Squid a while ago, and never really got it working, and forgot about it. I've just turned it off and the speeds have increased.
Sorry to be a bother.

---

