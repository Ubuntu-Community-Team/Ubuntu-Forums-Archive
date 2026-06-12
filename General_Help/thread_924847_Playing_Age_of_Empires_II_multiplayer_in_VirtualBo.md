---
title: "Playing Age of Empires II multiplayer in VirtualBox"
date: 2008-09-20
forum: General Help
---

### Post by pytheas22 on 2008-09-20
I installed Age of Empires II (Conquerors) in VirtualBox (hosting Windows XP).  It works great in single player mode.  Unfortunately, I tried playing multiplayer via [igzones]("http://igzones.com/") and can't seem to join games (I can host games but no one else is able to join them).  The igzones client software itself seems to work fine, and I patched my AOE2 software to what it needs to be for online play.

This is what I've done so far to try to resolve the issue:

1. I noticed that the IP address of my virtual machine was 10.0.x.x, while the local IP on Ubuntu is 192.168.x.x, which I figured was a problem.  So I changed from NAT networking to host networking in VirtualBox and now have an IP in the virtual machine of 192.168.x.x (not the same IP as I have in Ubuntu, but on the same subnet).

2. I also thought that my router might be blocking ports, so I changed the port-forwarding settings to what they're supposed to be (according to a website I found).

3. I turned off the Windows firewall in the virtual machine and don't have any ports blocked by Ubuntu, so no software firewall should be at fault.

However I'm still unable to play multiplayer games, and suspect that some kind of networking issue lies at the heart of the problem.  I'm not sure what else I would need to change, however.

So essentially I was wondering if anyone else here has managed to play AOE2, or any similar game, inside VirtualBox from Ubuntu, and if so what you needed to do to make it possible.  Or if anyone has suggestions on where else to look to figure out the problem, I'd appreciate that as well.  Unfortunately AOE2 itself doesn't provide any debugging information to troubleshoot the inability to connect to network games.

Thanks in advance!

---

### Post by brycesteiner on 2008-11-13
Hello,

I have run in to the same problem. I can play on the computer just fine under VB 2.04, but if I try to play over a LAN with my kids, it doesn't work. Did you ever figure this out?

thanks,
Bryce

---

### Post by pytheas22 on 2008-11-13
Yes, I did get it working.  I needed to use host networking, which gives the virtual machine its own unique IP on my LAN.  I also had to configure my router to open the appropriate ports for play via the public Internet, but I don't think you should have to worry about this if you're only playing against people on your local network--just make sure that neither Windows firewall in your virtual machine nor Ubuntu is blocking any traffic (by default Ubuntu shouldn't have any ports closed; the firewall in Windows XP SP2 probably does, however).

There are instructions [here]("http://ubuntuforums.org/showthread.php?t=346185") on setting up host networking for VB.  They worked great for me, although I found that I had to run the commands again each time I restarted Ubuntu in order for the Internet connection in the VM to work.  Also, sometimes my Internet connection in Ubuntu broke after I closed the virtual machine, and I had to ifdown tap0 and br0 before it would work again--not sure why.  If you run into weird problems let me know and maybe I'll have suggestions.

---

### Post by crusader123 on 2010-10-09
I  was encountering the same problem,i was trying to play aoe2 on my xp  virtual box ,host os is ubuntu,and i couldnt see any other games.i  clicked on the link to set up host networking and i followed the  instructions given in that site.But now i have a new problem,i can see  games and join games ,but if i join a game ,then when the game  starts,aoe crashes.Can you tell any fix to this?
Thanks.

---

### Post by pytheas22 on 2010-10-09
> I was encountering the same problem,i was trying to play aoe2 on my xp virtual box ,host os is ubuntu,and i couldnt see any other games.i clicked on the link to set up host networking and i followed the instructions given in that site.But now i have a new problem,i can see games and join games ,but if i join a game ,then when the game starts,aoe crashes.Can you tell any fix to this

Unfortunately I haven't had time to play Age of Kings in VirtualBox or anywhere else in over a year, so I can't confirm that what worked for me in 2008 is still working now.  VirtualBox has also changed a lot since I wrote that post; for one, I think that virtual guests now use host networking by default, rather than NAT, so it's no longer necessary to change the networking configuration in VirtualBox.

It's hard to say what's wrong in your case, but I'd check to make sure that your virtual machine and Ubuntu have IP addresses on the same subnet.  Giving more memory to the virtual machine might also not hurt, in case that's what it's crashing.  Does Age of Kings work reliably in single-player mode?

---

### Post by crusader123 on 2010-10-09
thanks for replying.actually you are rite,i didnt check out the single player mode,even that crashes as soon as the game starts,so i guess it isnt network related,can u suggest anything to make it work?
thanks.

---

### Post by pytheas22 on 2010-10-09
Are you sure the copy of the game that you have works on a normal Windows machine?  If it's a cracked copy or something like that, that could be why it's crashing.

Also, which version of Windows are you running in VirtualBox and how much memory do you have allocated to it?  Do you have the 3D acceleration feature enabled in VirtualBox (if you do, try disabling it, as Age of Kings doesn't need it and it could be causing graphics problems).

---

