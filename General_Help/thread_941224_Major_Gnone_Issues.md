---
title: "Major Gnone Issues"
date: 2008-10-07
forum: General Help
---

### Post by xhero0 on 2008-10-07
Ok I guess I did a SEVERE Bonehead move.....

Since I installed thunderbird as my mail client.... and I was running out of disk space I decided to remove evolution.....

Well after I restarted I can no longer see the task bars(with the menu system or the one on the bottom with the running apps....)

What I have done so far....

o    I have tried to use symantic(sp) to reinstall...but failed due to I guess the wireless services are attached to it also...
o    I have tried to gnone default failed same issue no task bar
o    I have grabbing evolution from my ubuntu cd and it still wants to get on the net... but once again no wireless....

I am running 8.o4 with all updates as far as I know

thank you ahead of time!

Joe M

---

### Post by Soupcan on 2008-10-07
You removed one one the libraries associated with Evolution, which is also, for some reason, an extremely important part of Gnome. I know there was a thread about this exact same thing just a few days ago. I don't know how to fix this, but I believe that the problem was solved in the other thread. Try using the forum search.

---

### Post by xhero0 on 2008-10-07
Ina matter of fact I did, and I indeed found a thread about it....I found this: (BTW: it is in text form soI can xfer it from my other machine to my now working again laptop)

kansasnoob

Fresh Brewed Ubuntu

 

Join Date: Apr 2008

Posts: 1,279

Thanks: 111

Thanked 143 Times in 137 Posts

	

Re: uninstalling evolution has removed my panel and bricked Ubuntu

Can you open the terminal by pressing Alt > F2?



If so the only thing I can think to do is:



Code:



sudo apt-get install --reinstall ubuntu-desktop



and then:



Code:



 sudo apt-get -f install



to resolve unmet dependencies.

kansasnoob is offline Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message Thanks

kansasnoob



Thank you Kansasnoob!!!:KS

Joe M

---

