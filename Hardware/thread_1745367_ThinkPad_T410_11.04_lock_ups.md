---
title: "ThinkPad T410 11.04 lock ups"
date: 2011-05-01
forum: Hardware
---

### Post by simonjb on 2011-05-01
Hi All,

I installed Ubuntu 11.04 on my ThinkPad T410 today and I have been experiencing some lock ups -- the mouse pointer wouldn't move and the system wouldn't respond to keyboard (including SysRq commands.) I had to power down to restart the computer.

After a few lock ups and restarts, I tried disabling the wireless as an experiment to see if that might be the problem -- with a physical switch on the laptop. Looks like it might be the wireless: since disabling it, I haven't had any lock ups.

I'm wondering if it might be possible to get some pointers on further diagnosing and (hopefully!) solving the lock ups?

Is there a good way to determine if my problem definitely is the wireless? For example, if I can reproduce a lock up, is there a log somewhere that might give me some info? I tried looking at /var/log/syslog but didn't see anything that jumped out at me.

lspci reports:

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

I've upgraded the ThinkPad BIOS to the latest available version for the T410 (1.36)

Thanks very much,
Simon

---

### Post by cpbl on 2011-05-21
Hi. I hope your problems have improved with subsequent updates. I have several different causes of lockups now so I don' think I can shed light on this, in particular.

I'm just going to use the opportunity to gripe and warn fellow T410s users: as of May 21, do not upgrade to 11.04. According to my experience, it is nowhere near ready. The list of things that don't work any more, and the frequency with which I need to reboot because things have hung up in one way or another, is vastly worse than any other Ubuntu release. Everything was smooth for me in 10.10.  As a general rule, waiting several months after an upgrade for others to do the suffering before upgrading it yourself is probably wise, but in this case it's been a new low of usability.

---

### Post by cpbl on 2011-06-21
June 2011: After all the intervening updates, I continue to get lock ups under Natty on the T410s. It's pretty embarrassing. I haven't seen a pattern, either, except that it's often just or shortly  after awakening from sleep mode. 
(And various other erratic behaviour with windows, wireless, ...)

---

### Post by ming0 on 2011-07-05
Damn, wish I had taken the time to search about this... I'm on a T410s and see the same kinda things.... namely monitor blanks out: [http://ubuntuforums.org/showthread.php?t=1750567&highlight=external+monitor+black+switch+resolution](http://ubuntuforums.org/showthread.php?t=1750567&highlight=external+monitor+black+switch+resolution)

---

### Post by neotaruntius on 2011-07-13
Hi friends...

I'm very keen to try out 11.04 on my Thinkpad T410. Are your lockups temporary - as in, do they last a few seconds, are do all of them permanent and need reboots?

Also, and I think I'll get a biased poll on this because people without issues won't come here, but is there someone with 11.04 on T410 that is NOT facing this issue?

I guess, it would also be useful to ask which wireless card you're using on your Thinkpad...

Thanks...

---

### Post by ming0 on 2011-07-13
Just downgraded back to 10.10... 11.04 was a true nightmare for me (T-410s owner here). I don't recommend it at all!

---

### Post by neotaruntius on 2011-08-22
I have been using 11.04 on my Thinkpad T410 for 2 months now... and there are no lockups. The only issue I face on it is while changing back and forth from dual screen setup to a single screen setup. But ABSOLUTELY NO LOCKUPS. Please feel free to try 11.04 on your thinkpad. I think some people are getting unlucky and coming here :)

---

