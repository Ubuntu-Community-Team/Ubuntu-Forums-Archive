---
title: "Laptop freezes - cause unknown?"
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by DenniiZ on 2005-07-12
Hey ya'll

I have a laptop (fujitsu-siemens amilo D) for 3 months now, and sinds 2 days I have Linux Ubuntu on it, on a partition of 15 GB. But when I was working in Ubuntu, after some time it freezes, just like that, for no reason. Because I liked it so much to work in linux, I haven't worked in my windows XP on the laptop so I didn't know if it would freeze up there to. But it did, just now... I don't know what the reason is, so can anyone help me pls?

Greetz DenniiZ !

*edit: I've just loged in to linux and i was working for like 3 minutes and it freezed... I turned off my laptop and again tried... 5 minutes and freezed !

---

### Post by leezer3 on 2005-07-12
Hi there,
Really, we need a lot more info before we can help you :)
This would be helpful:
*Does it only do this on AC/ battery power or both?
*Does it unstick itself if you wait?
*Does this happen when you try to open an app or what?

-Leezer-

---

### Post by DenniiZ on 2005-07-12
1 Does it only do this on AC/ battery power or both?
2 Does it unstick itself if you wait?
3 Does this happen when you try to open an app or what?

1) Normaly on AC with the battery fully loded, but I tried to do it with only the battery but he also freezes.

2) I've waited for 10 minutes, it doesn't change...

3) It happens when I just start up and do nothing except maybe move my mouse :d
    It has also happend when I was using only Firefox and also when I used Gaim.

I've added an output txt file of dmesg.

Greetz !

---

### Post by leezer3 on 2005-07-12
[QUOTE=DMESG][fglrx:_r6x_CheckAGPCommand] *ERROR* query for AGP device capabilities failed
[fglrx:firegl_unlock] *ERROR* Process 6623 using kernel context 0[/QUOTE]
These stand out from a quick ferret in the log. 
I take it that you are using an ATI Radeon vid card, so have a go at updating the drivers (Search for fglrx in Synaptic and have a look on the ATI site) & see what this brings you.

Hope this helps

-Leezer-

---

### Post by DenniiZ on 2005-07-12
but I think I did that yesterday... I'll go and try it again.
I will post the dmesg again if he freezes up again.
Greetz and Thx !

---

### Post by DenniiZ on 2005-07-12
OK I just searched for fglvx and found 4 things and 1 was installed. So I installed the other 3, and re-installed the other one. 

Now we'll wait and see.. :d

---

### Post by DenniiZ on 2005-07-12
:( He did it again... he lasted for 20 minutes and freezed, i was just surfing on firefox.
I just rebooted and did dmesg - I attached the file
So now what?

greetz

---

### Post by leezer3 on 2005-07-12
[QUOTE=DenniiZ]:( He did it again... he lasted for 20 minutes and freezed, i was just surfing on firefox.
I just rebooted and did dmesg - I attached the file
So now what?

greetz[/QUOTE]
 I'm afraid I dunno then :(
The error I mentioned previously is still in the log, but one of the problems is that this dmesg is from *before* the problem occurs. Obviously, there must be a log somewhere of past events, but I'm afraid I don't know where :(

Final thought- Your vid card model isn't a Radeon X series is it?- These are known to have problems at the mo.

Sorry to be of no more use, but my ATI (Mobility Radeon 9000 works perfectly)

-Leezer-

---

### Post by DenniiZ on 2005-07-12
hhm, thx, then i'm gonna erease linux from my laptop.. I have a new computer AMD 64bit in 3 weaks I'll put in on there :d
My videocard is: ATI Mobility Radeon 9600 Series AGP (128MB)

Greetz

---

### Post by mlord on 2005-07-18
Ubuntu uses the linux-2.6 kernel.  Newer centrino laptops use a chipset that in linux-2.6 requries use of the libata drivers, rather than the tried & true IDE subsystem which I co-authored.  Libata works well, though, but has a fatal race condition in the SCSI error handling code.

So.. if your laptop has the modern centrino chipset (ICH6M), *and* an IDE hard disk and IDE (ATAPI) optical drive, then it is probably using the libata "ata_piix" driver in the kernel.  If that is the case, your system *will* lock up regularly whenever the optical drive has no disc in it.

Just still a non-blank disc in the CD/DVD drive and let it run for a day or two, and see if that "cures" the lockups.  There's a kernel patch available for this as well, but it has not appeared in any official kernel yet.  Anyone who wants to pick it up can grab it from my webspace here:  [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)

---

### Post by s_p_a_r_k_y on 2005-07-19
I actually have a similar problem, however my laptop only locks up when I am running on battery. I have an AMD64 chip, but am running in 32bit mode. When I used ubuntu64, I don't remember it locking up, however in 32 mode it will lock up usually after about 20 minutes or less of use in Gnome. Often I'm not doing anything intensive, just writing some code in nano or gedit. I have gone though the syslog and messages but don't seem to find much of anything in there as I believe the system locks up and isn't able to write anything to the logs. Any help would be appreciated. I'm running
2.6.10-5-686
and have fglrx for the mobility radeon 9700...
any help at all?

---

