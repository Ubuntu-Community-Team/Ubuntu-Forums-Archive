---
title: "How connect to router via cable?"
date: 2008-07-16
forum: General Help
---

### Post by svaens on 2008-07-16
Silly question maybe, but how do I set it up?
I am running Ubuntu Hardy, and until now have never thought to connect my computer via the cable (since I first set it up on windows way back) until now. I've been using the wireless no problems, so i've not had a need to tether myself to the little black box. Until now. 

I have been having problems getting a bridge to work (that is another problem, I won't get into that much here), and I thought it could be since I was looking at the problem, and did a command :
brctl stl br0

This showed that my eth0 was disabled. 


```
eth0 (1)
 port id		8001			
state		       disabled
 designated root	8000.00080d9e5212	
path cost		 100
designated bridge	8000.00080d9e5212	
message age timer	   0.00
 designated port	8001			
forward delay timer	   0.00
 designated cost	   0			
hold timer		   0.00
 flags			

```

whether or not I am way misled here is actually besides the point. 
In any case, I decided to see if it is infact disabled, and attempted to simply plug it in, and connect myself to the network only via cable. 

So, I got out that old yellow cable, stuck it into the back of my toshiba notebook, and into one of the ethernet ports on my router.... and turned off the wireless.. 

suddenly,  I had no network whatsoever!

ok. So, i figured I maybe would have to configure something. However, what!?

It has been so long since i've used it (and that was on windows) and i've never used it on this notebook with linux, that I don't know what to expect. 

The light at the ethernet port at the back of my computer doesn't go on....  (i think there is supposed to be a light to indicate the ethernet is connected)..... what is going on?!!

Is this a hardware problem? A driver problem? A software problem? 

any ideas? 

thanks in advance!

---

### Post by knutschr on 2008-07-16
In terminal:
```
sudo pppoeconf
```

---

### Post by svaens on 2008-07-16
hey guys.. 
sorry..
actually... i think I didn't push the cable in ... hard enough. 
works now. 

still problems getting my host interface working (with bridge) ... doesn't work unless I stick this yellow cable in ...... 
but that is another issue, for another already existing thread. 
thanks anyway!

---

### Post by ellgor on 2008-07-17
Hi,

If your still having problems you could try this, switch the router off for a couple of minutes then power back up, it needs to forget what was last plugged in (for want of a technical explanation), hope this is of use.

Regards, Ellgor.

---

