---
title: "qemu too slow?? or just bad configuration??"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by towsonu2003 on 2006-02-26
I set up qemu from source with kqemuaccelerator module. But it is sooo slow (XP installation took ~6 hours), and it takes 100% cpu almost always... And this cpu usage is also common with firefox in javascript pages (digg.com especially)

Is it something with qemu, or is my configuration of this laptop here is wrong? 

This is a pavilion zv5120us
Intel Celeron 2.80GHz (using linux-686)
Ati Radeon Mobility 9000 IGP (using ati driver, proprietary was bad)
1GB RAM

What am I doing wrong? Any pointers, any type of help is appreciated (such as: do you enabled this, do you have that, what about this etc etc etc)

thanks in advance :)

---

### Post by towsonu2003 on 2006-02-27
bump (did I post it to the wrong place?)

---

### Post by aysiu on 2006-02-27
As I understand it, Qemu is an emulator. Don't emulators always run more slowly than native speeds?

---

### Post by towsonu2003 on 2006-02-27
they do run slower, but this was way slow. my only prior experience is with the Amiga emulator (playing kick off @), which is slightly slower but have no problems with cpu...

having no prior experience, I have no idea whether it is supposed to be so slow or is it my computer configuration... especially because of this 100% cpu usage... I launch IE, it peaks to 90% during launch. Browsing eats 80-90% of cpu until page loads etc. Briefly, anything I do under the emulated windows xp (includes launching notepad.exe or command.com) takes 80-100% cpu until processing is done (e.g. program is launched and ready and / or command executed and ready for new command). 

I also tried installing ubuntu (server) under qemu. It was weird: during the install process, cpu was always 100%. I couldn't even finish the process bc of the cpu heat (I got scared and shut it down).

---

### Post by shof2k on 2006-02-28
I think there is a known issue with XP installation.  I compiled qemu with the accelerator and XP installation took close to 5 hours, but booting into xp using qemu takes a few mins.

Is there a way to verify the accelerator is working? (I suppose I could modprobe -r it out and see what difference it makes).  

On a slight tangent, anyone know how to get qemu to share your network connection when you're behind a NAT router?  The user doc says that qemu emulates its own DHCP server and address but I don't know how to link this to my own network. (net -user does nothing)

---

### Post by george_apan on 2006-02-28
towsonu2003: I think you probably didn't compile qemu with the accelerator module. Maybe you got an error during the compile that you didn't notice.

shof2k: I'm not certain but I think that if you don't have the accelerator module installed you don't get a -no-kqemu switch with qemu. Just run qemu with no options to see if the switch is available.

In any case I found it easier to just use vmware player which is free for running virtual machines.

---

### Post by towsonu2003 on 2006-03-01
[QUOTE=shof2k]I think there is a known issue with XP installation.  I compiled qemu with the accelerator and XP installation took close to 5 hours, but booting into xp using qemu takes a few mins.[/quote] hmmm so the install time and the boot time are ok (same with my qemu)... what about your cpu usage?? is it 100% with even launching IE (during launch, until it's ready)? I use conky (very fun) to monitor stuff, but "top" in the terminal would do the trick :)
[quote=shof2k]
Is there a way to verify the accelerator is working? (I suppose I could modprobe -r it out and see what difference it makes).  [/quote]
Two ways I know of. 
1. Don't create that weird node thing and launch qemu. it will complain about accelerator module not being enabled
2. lsmod | grep qemu before launching and you'll see that it is not used ( 0 ), and lsmod | grep qemu while running qemu and you'll se that the module is in use ( 2 )
[QUOTE=shof2k]
On a slight tangent, anyone know how to get qemu to share your network connection when you're behind a NAT router?  The user doc says that qemu emulates its own DHCP server and address but I don't know how to link this to my own network. (net -user does nothing)[/QUOTE]
When I don't give it any options about the network, it connects "out of the box". I think that's one of the new features? No need to worry about firewall I think, because it acts like a kind of a browser or something. It's like firefox is accessing the web
[quote=george_apan]
towsonu2003: I think you probably didn't compile qemu with the accelerator module. Maybe you got an error during the compile that you didn't notice.
[/quote] testing with the ways I mentioned above, accelerator seems to be enabled. I am sure there were no error, because it took me 4-5 hours to compile (to many failures) so I ended up learning how to see whether there is a problem... 
[quote=george_apan]
In any case I found it easier to just use vmware player which is free for running virtual machines.[/quote]
No windows XP available in vmware player and I believe you can't use any install cd with it either. Well, even in qemu, you got 30 days until it tells you to f*** off (activation not possible as Install CD is HP's and check for my own hardware as opposed to that of the emulator). 

If only I could be sure that my cpu is not acting because of wrong out-of-the-box configuration....

---

### Post by towsonu2003 on 2006-03-19
bump

---

