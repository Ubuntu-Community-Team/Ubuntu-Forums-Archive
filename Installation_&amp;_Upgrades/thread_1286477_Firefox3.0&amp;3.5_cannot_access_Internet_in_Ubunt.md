---
title: "Firefox3.0&amp;3.5 cannot access Internet in Ubuntu9.04+Edubuntu, but other browsers can"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by aim@mail.nu on 2009-10-09
Dear Ubuntu Guru_s

I have install Ubuntu for possible more than 70 times since 8.10 and other variants, on perhaps 30+ computers and this is the first time ever I got this trouble. 

After successful installation of Ubuntu 9.04, I installed Edubuntu CD add on. Then I try to access Internet using Firefox (3.0 default installed).
I could not access any website. 

I could update and the auto update of Ubuntu worked fine.
I updated everything till it said your system is up to date.

After the completion of the on line update, I still fail to use Firefox to access Internet.

I uninstalled FireFox using synaptic to mark for complete removal of FireFox 3.0.

After that reinstalled Firfox 3.0 again with the same problems.
Then again use synaptic to complete removal of FF3.0 and this time shut down the computer.

After power up see nothing check on FF in any version both AdRemove Program and Synaptic.

I installed FF 3.5 which resulted in FF 3.0 and FF 3.5.
Still cannot access Internet.

So I decided to install Dillo, Seamonkey and Opera 10.
They could access internet immediately, no problems.

Special notes:
the defualt homepage is Welcome to Edubuntu 8.04 !
which is strange to have that.
I may means I install the wrong Edubuntu version to Ubuntu 9.04.
But that should not destroy FireFox access to the Internet fuction.

I have 2 options,
1. reinstall the 9.04 and make sure I use Edubuntu 9.04 after Ubuntu.
2. Help debug " if there is any bug on the present installed Ubuntu 9.04 & Edubuntu (suspect wrong CD of 8.04 in the name of Edubuntu 9.04)

Any Guru want to help of I should just Reinstall.

PS. I have install 9.04 more than 10 times on my this notebook and now flaws nor problems like this before.

Best Regards

---

### Post by prshah on 2009-10-09
> **aim@mail.nu said:**
> 
I could update and the auto update of Ubuntu worked fine.
I installed FF 3.5 which resulted in FF 3.0 and FF 3.5.
Still cannot access Internet.
So I decided to install Dillo, Seamonkey and Opera 10.
They could access internet immediately, no problems.


I hope you have checked that firefox is not in offline mode (File-Work Offline should be unchecked, unticked)

---

### Post by aim@mail.nu on 2009-10-09
the "work off line box" is unchecked.

That was the first thing I checked.

Thanks 

Any other things I got to check?

---

### Post by aim@mail.nu on 2009-10-16
I found the problems and fixed it.
and using it to wrote this post.

1.  What went wrong is the Proxy setting.

I did nothing to it. I left it as default but some how it was set to 
using Manual Proxy 192.168.5.1 port 8080
and using for all protocal.

May be when I install Edubuntu pack CD & Class Room features, immediately after I install Ubuntu 9.04, 
it may tricker the using of Proxy for class Room environment, ?? may be ??
====Please comment??===


2.  Some how though, I had used synaptic to mark for "Complete Removal",
but [B][U]it did not totally remove the configuration files.
[/U][/B]
After shut down and **_reinstall_** the Firefox it still set proxy to Manual Proxy 192.168.5.1 port 8080.

And I thought it will set to default that is No Proxy.
(As I have set it now)

So those who has the same problems, please check from the Firefox Menu Bar
>>Edit / Preference / Advance / Network / Connection => Setting / then>>
Choose No Proxy or what ever for your net work.

3. Is this a bug in Ubuntu's synaptic or Edubuntu Pack or what.
I had installed Edubuntu more than 15 system in our school, with no problems, but they were done after I access the net and update 9.04 before I install Edubuntu Cd, 
I will try to repeat the fresh installation and Edubuntu again, will report in next post.

bye for now.

---

