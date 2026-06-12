---
title: "anybody using galaxium.."
date: 2008-12-01
forum: General Help
---

### Post by jittopjose on 2008-12-01
hello friends... 
i have seen one new IM called galaxium which used c# and mono. anybody using it?.. can i get some reviews about it. i want to use gtalk and yahoo chat. is it possible in it?... how can i inatall it in ubuntu hardy?.....
thank in advance
jittos....

---

### Post by ibutho on 2008-12-01
I used it for a while 9out of curiosity really) and I found it to be very good. The development versions include support for gtalk, but the last time I used it, there was no support for Yahoo.

---

### Post by jittopjose on 2008-12-01
thank you friend...
Is it in continuous development?... i saw that, its last updated on jul 2008... thats why i asked...
is there any way to voice chat with gtalk client in it? any idea?

---

### Post by ibutho on 2008-12-01
I don't know any Linux IM clients that do voice chat on gtalk. Yes Galaxium is under continous development.

---

### Post by jittopjose on 2008-12-01
thank you friend...
let me install it from ppa...

---

### Post by priegog on 2008-12-01
Empathy does voice chat over gtalk. And shortly it is expected to do the same for MSN, Y!, etc... Hence, the talk during development to make it default in Intrepid. It may happen for Jaunty, and almost certainly for Jaunty+1 IMO

---

### Post by jittopjose on 2008-12-01
i have installed latest version of empathy in my hardy from ppa. but when i call somebody have windows gtalk client, they can hear my voice... i cant hear what they are saying... i couldnt find a solution... and also all my friends who are online are not listed in empathy... so there is some difference in number of online friends when i login in empathy and pidgin.... thats why i am looking for a new IM..
i tried many IMs like sip-ckommunication etc... in all these... text chat is possible... but no voice chat... 
in sip-communicator, it says that some plugins are missing... i have downloaded those... but i dont know how to apply... didnt get any support from anywhere....
i couldnt find a good working voip to talk to gtalk client...

---

### Post by ibutho on 2008-12-01
Thanks for the info. I tried empathy for a very brief period in Fedora 10 preview, so I didn't check out all of the features.

---

### Post by jittopjose on 2008-12-01
i dont know whether these problems are appear only to me.... many say that they can voice chat with gtalk users using empathy... but in my case its failed...

---

### Post by priegog on 2008-12-01
> **jittopjose said:**
> i dont know whether these problems are appear only to me.... many say that they can voice chat with gtalk users using empathy... but in my case its failed...

May I suggest upgrading to Intrepid? I think the older versions of libjingle/pulseaudio/whatever in hardy might be the reason for your failed experiment. Particularly Pulseaudio has been cleaned up a lot in Intrepid. 
Just my 2 cents

---

### Post by jittopjose on 2008-12-01
yea.. am also thinking about an upgrade... but i have setup all my favorite programs in hardy now.. like netbeans for php...all the desktop tweaks..all.. more over i have enabled lots more ppa repositories... i dont know whether it conflicts with new version
so i fear an upgrade may break everything... that why i hesitate to upgrade...

---

### Post by jittopjose on 2008-12-01
i saw, hardy and intrepid uses same version of libjingle...  but pulseaudio got an upgrade...

---

### Post by priegog on 2008-12-01
> **jittopjose said:**
> yea.. am also thinking about an upgrade... but i have setup all my favorite programs in hardy now.. like netbeans for php...all the desktop tweaks..all.. more over i have enabled lots more ppa repositories... i dont know whether it conflicts with new version
so i fear an upgrade may break everything... that why i hesitate to upgrade...

Well if you've got that all setupand don't wish to revisit everything then it's probably not worth it to upgrade just for the gtalk voice-chat. I meant it as an "easy fix", but if you dig deep enough surely you can solve those issues in hardy. 
Having said that, an upgrade is not such a horrible thing. Specially if you have a separate /home partition. And most of your ppa repos's will either become useless (having the new version of the programs in intrepid) or having an updated repo for intrepid. Just a matter of revisiting all those webpages and doing it again. 
About the desktop settings and all... it should all stay put as long as you do an upgrade, or alternatively, if you do a clean reinstall BUT with a separate /home partition.

---

### Post by jittopjose on 2008-12-01
yea.... i dont have a separate /home partition...
everything works well in hardy... except this voice chat... that why i gave up the idea of upgrading... i used to upgrade once in an year....
currently i am trying to tweak hard to get empathy to work in this installation itself...
moreover i am an asp.net/C# developer... so am curious about that galaxium IM development which is written using C# and Mono.

---

### Post by priegog on 2008-12-01
Well, regardless of if you upgrade or not, I STRONGLY suggest you make a separate /home; it will make things SO much easier for you in the future. I checked out galaxium and it seems ok, maybe it'll be right up there with pidgin and kopete in the future. best of luck.

---

### Post by directhex on 2008-12-01
galaxium packages should arrive in Jaunty at some point.

directhex@mortos:~$ head -1 Projects/pkg-cli-apps/packages/galaxium/trunk/debian/changelog 
galaxium (0.7.4.1-1) unstable; urgency=low

---

### Post by jittopjose on 2008-12-01
how to use gtalk with galaxium.... any idea how to configure?

---

### Post by directhex on 2008-12-01
> **jittopjose said:**
> how to use gtalk with galaxium.... any idea how to configure?

Google talk is a XMPP/Jabber service, so in theory just set it up as such

---

### Post by jittopjose on 2008-12-01
i gabe my gmail id including  @gmail  and password... it says authenticating etc... but none of my buddies are appear in the window... i dont know what happend...

---

### Post by priegog on 2008-12-02
You have to add more than just your email and password. see here [http://www.google.com/support/talk/bin/answer.py?answer=24073&cbid=1bv35mges83ni&src=cb&lev=answer](http://www.google.com/support/talk/bin/answer.py?answer=24073&cbid=1bv35mges83ni&src=cb&lev=answer)

---

