---
title: "Virtual Machine vs Wine??"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by GapToN on 2009-04-21
Hello guys,

So I'm thinking of installing Ubuntu and having a Virtual Machine and install Vista on it, or use Wine. I wonder which is more stable?

I'm experienced with Ubuntu and Windows, I just had not used a "pure Ubuntu" machine and dont know what problems will I run into.

I would love to have Windows Live Messenger (Pidgin does the job, but features important to me are missing) , and be able to play some PC games although I play only once or twice a month.

If I install a VM, Im probably looking at hooking one up to a separate monitor so I will have Vista on one side and Ubuntu on the other.

My questions about Wine is how does it work and would it be a better solution to installing a full VM?

Also, should I go for 32 or 64 in such case? I would like to retain the gaming performance, either in VM or WINE.

Thanks in advance for the input :)

---

### Post by Dr. C on 2009-04-21
If you are looking for full gaming performance then Wine is the way to go. Virtual machines VMware, Virtualbox etc have very limited limited 3D graphics support and it is mostly experimental. Wine has made much progress in supporting Windows games on GNU / Linux.  

There is also the commercial Codeweavers and the Propriety / Commercial Cedega for running Windows applications including games on GNU / Linux

---

### Post by rickbeton on 2009-04-21
I'm sure you have good reasons to prefer MS Live Messenger over Pidgin, but I really like the ability of Pigdin to talk MS, GoogleTalk etc. all in one app.

Some games are really well supported on Wine but unfortunately many are not. See [http://appdb.winehq.org/](http://appdb.winehq.org/)

:)

---

### Post by Marlonsm on 2009-04-21
If the application you want runs on Wine, use it, as it's the simplest one to use. (check Wine's site to see which applications are known to be supported)

If Wine doesn't run it, then try a VM.

But if you want to play heavier games, Dualbooting is still the best option.

---

### Post by Dougie187 on 2009-04-21
If you are looking to play games, the only real option out of those two is wine, as you can't do a lot of hardware acceleration through a virtual machine, so it won't work if the game is graphics intensive.

If you are just looking to run simple apps like MSN or IE, then a virtual machine will work fine.

If you want to run graphics intensive games then you should dual boot.

---

### Post by GapToN on 2009-04-21
So if I am to dual boot + VM for MSN
By logic it seems I will have to have two copies of Windows plus one Ubuntu installed, is that correct?

Is there any way to instal just one copy of Windows and use it both as a bootable OS and inside a VM? (guess not)

---

### Post by Marlonsm on 2009-04-21
Wait... Isn't there aMSN for Ubuntu? With it you won't need the VM.

But I've never used it, so IDK how close it is to the normal MSN.

---

### Post by Mark Phelps on 2009-04-21
Not a fan of Wine (readily admit that) -- so, before you invest a lot of time in that approach, suggest you check the CodeWeavers site below for the compatibility of the specific apps and games you want to run:

[http://www.codeweavers.com/compatibility/browse/name]("http://www.codeweavers.com/compatibility/browse/name")

---

### Post by riza hylviu on 2009-04-21
have you tried aMSN? it is almost as older msn versions, with more features than pidgin. for gaming i think the better choice is dual boot. Keep a minimal windows install only for gaming and the ubuntu for the rest. Vm and wine are not the perfect choices i thing because of huge limitations.

---

### Post by Bakon Jarser on 2009-04-21
> **GapToN said:**
> 

Is there any way to instal just one copy of Windows and use it both as a bootable OS and inside a VM? (guess not)

Yes, actually there is.

[http://ubuntuforums.org/showthread.php?t=984437](http://ubuntuforums.org/showthread.php?t=984437)

Edit:  Your probably going to want seemless mode too, since you are only going to be running MSN messenger.

[http://ubuntuforums.org/showthread.php?t=1125131](http://ubuntuforums.org/showthread.php?t=1125131)

---

### Post by GapToN on 2009-04-22
> **Bakon Jarser said:**
> Yes, actually there is.

[http://ubuntuforums.org/showthread.php?t=984437](http://ubuntuforums.org/showthread.php?t=984437)

Edit:  Your probably going to want seemless mode too, since you are only going to be running MSN messenger.

[http://ubuntuforums.org/showthread.php?t=1125131](http://ubuntuforums.org/showthread.php?t=1125131)

thanks alot I'll look into that and see if it works :D

---

### Post by mmstahlman on 2009-06-09
I did not see how old this thread is, but here is my suggestion...  
 
I am a new Ubuntu user (I fix WindowsXP / Vista for a living) and I use Wine for simple apps that Ubuntu does not have a good equivalent of and some games. 
 
It would make sense to me that you use wine for the smallest app - Windows Live Messenger when in Ubuntu, and then boot into Windows for the graphics intense games.  
 
This seems to me like it would be much easier than dual-booting and when you boot to Ubuntu trying to fire up your windows OS in a virtual box.  That shoulds like a hard setup / loads of booting issues if Windows is not "properly shutdown"
 
-Good Luck
 
Marcus

---

### Post by 00b00nt00 on 2009-06-09
For best compatibility and performance = Dual Boot

Compatibility = VirtualBox

Hangover = Wine

---

