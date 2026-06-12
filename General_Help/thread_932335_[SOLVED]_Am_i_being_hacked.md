---
title: "[SOLVED] Am i being hacked?"
date: 2008-09-28
forum: General Help
---

### Post by Monotoko on 2008-09-28
Hiya guys, today firestarter has been giving me all sorts of blocked connections, one ever 10 mins or so from a load of differant IP addresses, i have attatched an image of it. (please ignore the state of my desktop atm :P)

The only one that i did authorize was the local one (192.168.1.178 ) on port 22, but who the heck are the others, and why are they trying to connect to me??

---

### Post by Malac on 2008-09-28
Try : 
```
sudo netstat | grep 58639
```It should tell you what is listening on or trying to open that port.

You may just be getting a random port scan. In Firestarter preferences make sure drop silently is checked.

Hope this helps.

---

### Post by spiderbatdad on 2008-09-28
looks like your isp in dubai?

---

### Post by Monotoko on 2008-09-28
Im getting worried now, i ran the netstat thing, but it hanged and got stuck, its been like that for 5 mins now.....

My ISP is Orange Broadband, in the UK.......

---

### Post by spiderbatdad on 2008-09-28
This is what I saw...maybe it isnt a reliable way to look up an ip

---

### Post by Monotoko on 2008-09-28
Your looking up the IP that was portscanning me, not me

---

### Post by mikewhatever on 2008-09-28
Do you have a p2p program, such as bittorent or amule configured to use port 58639? That may explain the nature of those connections, even when a p2p program isn't running.

---

### Post by Jeroensum on 2008-09-28
Got anything from netstat yet?

Else try:

netstat -tulpen | grep '58639'

You can also try to do a telnet to your localport to see if you get a banner of somesort.

telnet localhost '58639'

if it seems to hang press  CTRL ]  
you will get a telnet> prompt, then type quit.

If it seems to hang or you get a banner, there is something listening on that port. This still doesn't mean you're hacked, it could be a port from a P2P app or something else you've installled.

---

### Post by Monotoko on 2008-09-28
It brought up an advertisment for a porn site..........

---

### Post by Jeroensum on 2008-09-28
Whoops.

Try to check what program is using the port by running:
netstat -pant

This shoudl give you a name and/or pid. (process id, numerical)

Then check where the program lives with:
sudo updatedb
locate <program name>

Then kill the program by running:
sudo killall <program name>
or
sudo kill <pid>

Then remove the program by hand by using the info you got from locate and using sudo.

It's not uncommon but you sure need to be careful when running scripts you downloaded or installing binaries/debs from an untrusted source.
Also it's a good practise to keep your system up2date.

---

### Post by Monotoko on 2008-09-28
Thank you, that worked :)

No more ads :P

---

### Post by Jeroensum on 2008-09-28
Great :)

Now that we have eliminated the initial threat, it might be that there is still a residual piece of the virus/trojan/malware left on your system. To do a virus sweep, you can install clamav and avscan (graphical frontend) and to see if it could have been part of a rootkit you can install rkhunter and/or chrootkit and have them have a go. 
All of the above are in the repositories. :)

---

