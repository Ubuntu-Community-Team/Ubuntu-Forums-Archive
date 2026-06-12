---
title: "[solved] setting multiple accounts on Ekiga"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by caue.rego on 2008-12-25
I just wanted to report my little experience on this issue.

I was using the default ubuntu 8.10 Ekiga (2.0.12) with my voipraider.com account with no issues. But then, since I couldn't make empathy or skype work with my MSI 163A's audio, I've decided to try using ekiga sip. Surprised I was my ekiga account wouldn't register.

So I did some google and ubuntuforums research, and still no clue. Finally I decided to try the good and old "try yourself".

In my preferences I had a sip outbound proxy set to sip.voipraider.com, which for some reason is not necessary to make voipraider work, as I've tried it out now without it. Just removing it, and everything seems to be fine.

Meanwhile my Network Settings still have the also unnecessary STUN configured to stun.voipraider.com, applied and working. That does not affect me registering with ekiga.net, so I left it configured as is.

All the testing had to be done, after changing each setting, by quitting Ekiga and reloading it.

So, hopefully, this report will be of some use to someone.

---

### Post by x-project on 2009-07-14
Hi, I just install Kubuntu and I can't get VoipRaider to work with Wine or CrossOver, I installed the Ubuntu desktop interface, and I have Ekiga. I tried setting it up your way but i didn't manage, can you please post a tutorial on how to run VoipRaider accounts on the Ekiga client.

---

### Post by caue.rego on 2009-07-16
Sorry, but I really can't get the time into making a tutorial or how-to. I couldn't even answer you until now, and I've got your message less than 1h after you posted it. I haven't even tried using my voipraider on Jaunty yet, since I've been using it with SIPhone on my iphone.

Anyway, it shouldn't be hard to set up just one account. You just have to configure the SIP, _leave the **outbound proxy** as **blank**_ and do as you wish with STUN. Everything is the same ( **sip.voipraider.com** ).

Maybe once you're done you could do a how to. ;)

Wish you luck.

---

