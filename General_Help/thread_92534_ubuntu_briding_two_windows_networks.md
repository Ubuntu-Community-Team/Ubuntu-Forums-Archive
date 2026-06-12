---
title: "ubuntu briding two windows networks"
date: 2005-11-19
forum: General Help
---

### Post by moglenstar on 2005-11-19
[IMG]http://img510.exs.cx/img510/879/network4rr.gif[/IMG]

i'm having a problem trying to make my upstairs network (192.168.0.x) see my downstairs network (192.168.123.x) through my ubuntu server.

through iptables ive set my ubuntu server up so that i can access the internet which is downstairs, and that works fine (from all computers)

the problem is, from the ubuntu server, browsing the local network i can see computers in 192.168.123.x  that being the downstairs computer, but i cant see any computers in 192.168.0.x

from computers in 192.168.0.x i cant see any computers in 192.168.123.x and visa versa..

im hoping to set this up somehow similar to how i had it with windows on (now ubuntu) server, where both "networks" are called "HOME" and i could see all of the computers from all of the computers

(ie seeing main pc from dads pc etc)


ip addresses

server (green side) 192.168.0.1
main pc 192.168.0.2
spare pc 192.168.0.3

server (red side) 192.168.123.114
dads pc 192.168.123.144
router 192.168.123.254

any help *connecting* the two networks (for network fileshares, atleast) would be appreciated.

---

### Post by suRoot on 2005-11-19
Why add all this complexity to a simple home network?  Is there any particular reason for having these machines on two subnets?

To answer your question more specifically, you can "see" machines on a windows network thanks to NetBIOS.  NetBIOS basically works by sending broadcast packets to the local network.  The problem here is that you have two separate LAN segments, subnets, and NetBIOS packets do not cross those physical network boundaries.  You can make it work, and this article [http://www.linuxplanet.com/linuxplanet/tutorials/1159/1/]("http://www.linuxplanet.com/linuxplanet/tutorials/1159/1/") should point you in the right direction.  It's your network & run it however you like, but this seems like a far more complex setup than it need to be.

---

### Post by moglenstar on 2005-11-20
well, the reason i have two subnets is because the red portion of my network (192.168.123.x) is all downstairs on the ground floor of my house, where the internet connection comes in .. 

the longest red line on the diagram, going from router to ubuntu server is in real life a very long network cable that runs outside of my house, up the wall, and then into the roof to my attic where the green network is..

the ubuntu server is there because its the only way i can get the long cable shared onto all of the computers in green (192.168.0.x) as a nat, i guess..


so the internet goes:

modem > router > dads pc, server > switch > main pc, spare pc

i dont have the hardware available currently to set it up differently, but eventually i plan to replace the server and the switch with a second router..


edit:

as soon as i finish settings up my server again (ups cut out for some reason, and now ubuntu doesnt want to load) ill give that link you linked a read, thanks :)

---

