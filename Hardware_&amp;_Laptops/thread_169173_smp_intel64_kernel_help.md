---
title: "smp intel64 kernel help"
date: 2006-05-02
forum: Hardware &amp; Laptops
---

### Post by debiandude on 2006-05-02
Hi 

I am running 2 x 3.2 duel intel xeons and installed ubuntu breezy.
So far I have setup 2 x 200gig raid 1 useing software when i installed ubuntu and this works fine.I have all so installed squid and set this up and this also works fine.

But I am useing an amd64 kernel that came on the cd so I am only useing one cpu.

I have installed a intel smp 64 kernel with help form a freind.
I can boot it and it works but I then loose network and my raid 1.

I am not sure what to do, I am still new to this.
Thanks

---

### Post by christhemonkey on 2006-05-02
I think you will need to recompile your kernel with your network card and raid enabled in your config.

There might be a package in the repositories for dual intel 64, 
EDIT:there isn't.

But really just wanted to say wow nice box :D

---

### Post by debiandude on 2006-05-02
how do i do that? ](*,) 
this is what i have installed
[http://packages.ubuntu.com/breezy/base/kernel-image-2.6.11-9-em64t-p4-smp](http://packages.ubuntu.com/breezy/base/kernel-image-2.6.11-9-em64t-p4-smp)
and it works fine just need the raid and network working :???:

thanks 
yeah box is cool just running on one cpu at the moment

---

### Post by christhemonkey on 2006-05-02
ok, if you have that kernel and it does not have networking or raid, you should file a bug report.
The kernel shouldnt affect if you have things setup correctly (like you said you did with one core)
Apart for if you have particular drivers that needed to be compiled against your kernel (only ones i can think of are graphics card drivers)

What network card do you have?

Whilst booting does it churn out any errors?
If so type ```
dmesg
``` to view the kernels output (you may want to pipe it to less)

Hope we can get this working for you!

---

### Post by debiandude on 2006-05-02
2 x nics'

eth1: Yukon Gigabit Ethernet 10/100/1000Base-T Adapter
eth2: Intel(R) PRO/1000 

I am useing the Yukon Gigabit Ethernet at the moment.

I dont think its churning out errors...
It just fails to start the raid and the network.(thats all i can see)
Graphics works fine too.

:-?

---

### Post by christhemonkey on 2006-05-02
If you go into the networking dialog box thing (on system menu)
Does it list your devices (eth0 and eth1)?
If so it means they are probably detected and have the drivers loaded ok.
I have never used raid so im sorry cant help you there!


I have to go to school now as well, good luck with your problem.
If its not been fixed by tonight, il be back on trying to help.

---

### Post by debiandude on 2006-05-02
only the unpluged nic is found

eth0 is gone when the smp 64 kernel is booted

---

### Post by debiandude on 2006-05-02
ok its working :-k 
i used the synaptic package manager and added Xeon smp 64.
it works.

just boots really slowly.

---

### Post by christhemonkey on 2006-05-02
You can use use initNG to significantly reduce your boot up time, or just remove unwanted services.

InitNG howto:
[https://wiki.ubuntu.com/InitNG](https://wiki.ubuntu.com/InitNG)

Getting rid of unwanted services:
[http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

---

### Post by debiandude on 2006-05-03
hi,

well all i did was update,installed a double layer DVD writer(as the 4.5gig is a relic)
now it boots faster :confused: network works, raid 1 works and 64 smp works, hp is also working fine,ubuntu is picking up 4 cpu's :mrgreen:

now all i need to learn is how to bridge two nic's ;) 

thanks

---

### Post by mips on 2006-05-03
[QUOTE=debiandude]
now all i need to learn is how to bridge two nic's ;) 
[/QUOTE]


Please elaborate on the above.

Do you want the network to see both nics as one interface ?
Do you want bridge 2 seperate LANs at layer 2 ???
Do you want to route traffic between two seperate LANs at layer 3 ?

---

