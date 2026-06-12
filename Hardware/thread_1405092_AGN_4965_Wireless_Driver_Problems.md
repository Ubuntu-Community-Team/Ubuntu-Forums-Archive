---
title: "AGN 4965 Wireless Driver Problems"
date: 2010-02-12
forum: Hardware
---

### Post by CJay554 on 2010-02-12
I've seen this all over the forums, each have their own problems with this wireless card... sadly i am stuck with this as well. 

I have a Dell Latitude D630C with the Intel AGN 4965 Wireless.
Right now i have the iwlagn driver loaded, when i try to load iwl4965 it loads the iwlagn (makes me think they are connected)

Either way, my symptoms are like this:  

I start computer, wireless works peachy for a few minutes, until i start using the connection.

Sometimes it works for a long time sometimes for a short time, but it still dosconnects. 

When i try to reconnect it tries to establish a connection but ends up hanging at 

My next step is to rmmod and to modprobe the driver back into play.
While doing rmmod (turning off the card in a sense) dmesg outputs "
Mac in deep sleep" over and over and over again, the computer hangs for about 2-4 minutes and the driver turns off and all is fine. 

A modprobe iwl4965 puts the driver up and running, then i can connect again.

This driver is hella buggy, does anyone have ANY idea what i can do to fix this? I mean, i don't want a work around like many have done (setting rmmod and modprobe in a script then toggle by a keypress) i would like a complete fix because this laptop i am trying to configure is going to be owned by a friend that wants to move from Windows Vista to Ubuntu, and she is a simple user i would like this to be as flawless as possible... But it would be shamefull if i come back empty handed...

---

### Post by PatrickVogeli on 2010-02-12
have you tried if installing the linux-backports-modules-wireless-karmic-generic solves the problem?

---

### Post by CJay554 on 2010-02-12
Thanks for the reply, i installed the backport package via terminal, restarted the computer, but i still have the same symptoms, also it be helpful to mention im running 9.10. 

What i have seen is alot of people actually working out of the box with this wireless card.. which confuses me, maybe there are multiple versions?

---

### Post by Jack_Simth on 2010-02-12
> **PatrickVogeli said:**
> have you tried if installing the linux-backports-modules-wireless-karmic-generic solves the problem?
Hmm... I've got a [somewhat similar]("http://ubuntuforums.org/showthread.php?t=1404788") problem as the OP - I just ran:

sudo apt-get install linux-backports-modules-wireless-karmic-generic

Then rebooted, and now have my netbook moving a big chunk of data as a test.

Edit: And so far so good - I'm up to 570 MiB downloaded successfully, when I couldn't top 160 MiB before.... lets see if it gets through all 20 GiB....

Edit 2: Oh, hey, that's interesting - the network stats loop after a while on the "total received" - huh.  I'm up to ten GiB....

---

### Post by CJay554 on 2010-02-13
Well our cards are different, but im glad this may have worked for you jack =)

im still dissapointed at the driver that intel themselves have provided... It is said that this problem happens in windows too, just not as often, very rarely... But it still persists on both system. This is definately a driver problem for both systems.. I just wish it would work better on ubuntu so it would be usable... :sad:

---

### Post by Jack_Simth on 2010-02-13
> **CJay554 said:**
> Well our cards are different, but im glad this may have worked for you jack =)

Mind you, the post I put in the Wireless Networking forum didn't attract anything more than a "please fix the formatting", but your similar problem here took care of it.  C'est la vie.
> **CJay554 said:**
> 
im still dissapointed at the driver that intel themselves have provided... It is said that this problem happens in windows too, just not as often, very rarely... But it still persists on both system. This is definately a driver problem for both systems.. I just wish it would work better on ubuntu so it would be usable... :sad:
If an issue persists with multiple operating systems, using both the manufacturer's drivers and the generic drivers, I'd be inclined to think it's the hardware, rather than the software.  But that's just my paranoia saying a guy in business for the money doesn't want to admit that his product isn't totally solid when there's other guys out there in business for the money who's product is noticeably more solid....

Silly paranoid me.

---

### Post by CJay554 on 2010-02-13
>  But that's just my paranoia saying a guy in business for the money doesn't want to admit that his product isn't totally solid when there's other guys out there in business for the money who's product is noticeably more solid....

Silly paranoid me.

I'll drink to that :/

but as far as i know this driver si fine in windows and if i explain this to the new user going to use ubuntu all she knows is that it works in windows and doesn't work in ubuntu, so the transfer there is off. But im hoping something happens to fix this issue =(

---

### Post by CJay554 on 2010-02-15
anyone? =( bump

---

### Post by CJay554 on 2010-02-23
Bump, a bit more information:

iwlagn: Mac in deep sleep!
occurs constantly for a few minutes when i attempt to shut down. When i do **rmmod iwlagn** computer hangs for a few seconds/minutes and comes back to life. This happens when flipping the wifi switch as well.

Backports don't solve this, updated drivers from intel do not solve this, ucodes do not solve this.. Im running out of optoins...

---

