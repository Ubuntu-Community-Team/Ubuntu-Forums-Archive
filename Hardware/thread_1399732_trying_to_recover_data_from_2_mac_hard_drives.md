---
title: "trying to recover data from 2 mac hard drives"
date: 2010-02-06
forum: Hardware
---

### Post by elektros75 on 2010-02-06
i have a friend who's kid changed the password on his ibook g4, so he decided it would be prudent to take the laptop apart to get at the hard drive and look st it. what he didn't know is that Mac hard drives can't be viewed in a windows environment and he tried to view it in his other mac (external adapter) and he cant access his files  

i told him i'd give it a look and as root i can see the files, but cannot access them as they are set to read only 

1] i ran the following code 
Code:      sudo chown -R username:usergroup /media/drivename
 in otherwords...
Code:      sudo chown -R patrick:patrick /media/Wow!  

I've also tried this on my desktop, which has Linux Mint 8 installed dualboot to windows, and even in root it still comes up as read only and ownership doesn't change  I've been taking some courses (vtc video tutorials) so i'm gettin a hang of the terminal, and the code above i was given because i has initially having issues with my own bad partitioning skills :\  

gettin on with it, all i can do is look at them, i can't copy or move them, change permissions or anything  is there anything i can do for him or is he just s.o.l. :?:  

2] also there is another hard drive named "Mac HD" ( ie; /media/Mac HD ), how do i make it so i dont constantly get an error saying that there is no folder named Mac, and no folder named HD?

 thanks for any help possible

 Patrick

---

### Post by mörgæs on 2010-02-06
I don't know anything in particular about Macs, but here is a general help for data recovery:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

