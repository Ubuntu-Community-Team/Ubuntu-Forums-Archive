---
title: "overriding fortiguard ; an ultrasurf for ubuntu ?"
date: 2008-07-29
forum: General Help
---

### Post by dexter.deepak on 2008-07-29
i am about to go to my college, and our network administrator is pretty smart guy...so much that he has banned all the forums too...including ubuntu forums :(
he uses fortiguard / fortigate , which as i have heard, can only be overridden by ultrasurf ....in my college,we have rare linux-users, and i am going to suffer a lot...coz i have no windows (nor i want to have).and ultrasurf  is only available for windows.

so i want any other variant, as strong as ultrasurf for ubuntu.

maybe i can run ultrasurf through wine, but i cant test it at my home, and when i am in college, maybe its too late by then !!

---

### Post by Potatoj316 on 2008-07-29
you could set up an SSH port foreword to your home network, or use a VPN (vpn is probably easier) but both accomplish the same thing.  they make it as if you were attached to your home network and surfing the web from there.  You also can see all the attached computers by their internal IP addresses and access their shared files/printers.  (print on their printers to confuse them)

---

### Post by dexter.deepak on 2008-07-29
thanks for the quick reply. i have got a time of 5 days for the solution...and unluckily i have a zero experience in practical networking.

i actually dont understand the "home network"
the solution you gave probably wants me to have another computer running internet (and also it should be outside my "banned" network).
but i have no such option...i am in a hostel much away from my home,and there's noone who would like to start his computer on my every request.

maybe i got this all wrong..i have never used ssh / vpn before....if it can still help me, please let me know it.

---

### Post by Potatoj316 on 2008-07-29
nope thats pretty much correct.  Ive never used ssh port forwording, or VPN.  

The problems that arise are: You would need to know the other person's IP address (which probably changes randomly) and you would have to be able to get through their router. (router port forword, its easy but their internal IP probably changes as well which makes it more difficult)

you would need to install a VPN server on a computer outside the network you want out of.  Or have an SSH server on the network you want out of.

---

### Post by dexter.deepak on 2008-07-29
can you please make a list of the requisites.
this is the list what i feel like :
1. my pc ( with no extra server or anything )
2. another pc, which is completely outside my college network, with a seperate internet connection...and it should also have a VPN/SSH server installed.
3. the ip of that remote pc, i should be dynamically updated regarding the remote ip.

anything else ?
and what role does "their router" play ??

---

### Post by dexter.deepak on 2008-07-29
i am still not very clear about how ssh/vpn works.its mainly because i dont know how to connect to any computer on the internet.
i have a vary little netwoking knowledge, and here's what i think.
my college has been assigned an ip address over the internet, say 
117.197.18.135
and inside my college network, i am given a local address of 
192.168.0.2

a friend of mine is in another college somewhere, and he's facing no bans.
again, his college has been given a global ip say,
117.197.20.124
and his local address, inside his college network is say, again
192.168.0.2

i ask him to install a VPN/SSH sever over his computer, say at port 3306.
i can ask him to call me everytime he gets a different local/global ip change.

but how do i connect my pc to his ?? what address should i try ?

---

### Post by Potatoj316 on 2008-07-30
it can probably be easier than that.  You will have to have a computer to install a server on that is either directly connected to the internet or behind a router they can control.  (they probably cant control the college's switches) that way you can tell the router to forword incoming requests on the ssh port (22 i think) to the computer running the ssh server.  (vpn would probably be easier, im just using ssh as an example because I know more about it).  Then if the router suports a dynamic DNS (it probably does) you can create a free dynamic subdomain at dyndns.org and configure the router to automaticaly update that subdomain.  so you can use the domain to connect instead of the IP.  

You need:
1. a computer outside the blocked network that has a direct connection or is behind a router you can control (preferably running linux)
2. an account on dyndns.org (if the computer is behind a router and the router supports DDNS)

---

### Post by hittudiv on 2008-09-14
yea..hav a similar prob..
hav some stupid limitations like 5mb download limit and no orkut.. by squid proxy
that proxy is the only way for net in the campus...

we used ultra surf in window..and i shifted to ubuntu...cant find an alternative..

am using ultra in innotek virtual box (xp) :D

hav a btr soln?

---

