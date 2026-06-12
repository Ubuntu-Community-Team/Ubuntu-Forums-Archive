---
title: "Help Me Battery Probleeem!!"
date: 2008-10-02
forum: General Help
---

### Post by titico on 2008-10-02
Hello guys

I have a sony vaio laptop with a NON original battery...

I can work perfectly with battery power, but when i shut down the computer i have to unplug the battery and use the AC power adapter to startup the laptop...

Can you help me solve this issue?

Thanks

---

### Post by intimatewipe on 2008-10-02
that is a hardware prob mate,cheap is not allways the best option,if your not getting the bios up then your having probs with the battery or the charger .

---

### Post by titico on 2008-10-02
Its not that...
I've read somewhere that Sony has some background programs to prevent users to use non original batteries and buy an original 350$ battery...

So, maybe knows how to change that...
its a specific sony vaio problem... I solved it in windows by deleting some files...But here i can't fin a solution!

=]

---

### Post by Calmatory on 2008-10-02
So the machine works under Windows but not under Linux?

What model is it, and what battery is it? What files did you have to delete under Windows?

---

### Post by Kuroyume on 2008-10-02
what kernel are you using? (type uname -a on a terminal anmd copy the output here)

There is a bug in the original Hardy kernel that causes this behaviour. Enabling all software repositories on System->Preferences->Software Sources and downloading the latest kernel should fix it if that is the bug that is affecting you.

Also, editing your GRUB to boot without the "quiet" option should fix it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137)

That is the report for the bug in question.

---

### Post by titico on 2008-10-02
It works always...But the battery does not work properly in ubuntu...In Windows it works cause i deleted a file called "ISBMgr.exe" and is in Program Files/Sony/ISB Utility/.

My laptop model is Sony Vaio Vgn-C220E.
The battery is a non original Li-Ion battery from battery tech.

---

### Post by intimatewipe on 2008-10-02
that makes no sense,even if sony had put some software in windows it won't effect a linux install,maybe its in the bios but then deleting files in your OS should not have an effect on that.I recently put ubuntu on a sony vaio pcg z1xp and it worked fine,if sony had a link up where software in the OS looked at the bios boot info and rejected
it if all was not as expected then again it should not effect a linux install????

---

### Post by Calmatory on 2008-10-02
Sounds odd that deleting an .exe file fixes it, as I doubt Sony has injected any executing daemons to linux boot.

However, what happens if you try to boot with AC and battery attached? The laptop starts, but does not load the operating system? Does it load Windows?

---

### Post by intimatewipe on 2008-10-02
found this

---

### Post by intimatewipe on 2008-10-02
try again,how could this affect linux???if its not there then you don@t need to delete it:confused:

---

### Post by Kuroyume on 2008-10-02
it's probably the bug i pointed you to... i have a Vaio VGN-C240Fe, which is basically the same hardware with minor variations, and i had the exact same issue. Upgrading to the latest kernel solved it.

If you don't want to do that, you can edit the /boot/grub/menu.lst and remove the "quiet" word wherever it appears.

Finally, you can also boot in recovery mode, and select start a regbular session at the prompt.

---

### Post by titico on 2008-10-02
Ok.

1. I'm not telling that deleting and .exe file would do something in linux, i was just pointing what i've done to solve the problem with that OS.

2. If I try to boot with both cable and Ac adapter, the computer does not turn on at all... I have to remove the battery...

3. I'm using ubuntu 7.10 version, i'll try to update kernel and delete "quiet" and then i'll post it here

---

### Post by Calmatory on 2008-10-02
> **titico said:**
> Ok.

1. I'm not telling that deleting and .exe file would do something in linux, i was just pointing what i've done to solve the problem with that OS.

2. If I try to boot with both cable and Ac adapter, the computer does not turn on at all... I have to remove the battery...

3. I'm using ubuntu 7.10 version, i'll try to update kernel and delete "quiet" and then i'll post it here

If the computer does not turn on at all, and if that is your problem, then the problem can not be operating system related by any way.

---

### Post by titico on 2008-10-02
yes but there must be a way to solve it...

Using windows i solved it by deleting that file...
Hope in ubuntu it is easy too :P

---

### Post by titico on 2008-10-02
about the kernel 

Output
```

Linux ubuntu 2.6.22-15generic #1 SMP Wed Aug 20 18:39:13 UTC 2008 i686 GNU/Linux
```

---

### Post by Calmatory on 2008-10-02
> **titico said:**
> yes but there must be a way to solve it...

Using windows i solved it by deleting that file...
Hope in ubuntu it is easy too :PAre you saying that before you deleted the file, the computer couldn't be started(it did not turn on) if the battery was plugged and the machine was on AC? And after you deleted the file, the computer started up fine even when the battery was plugged and the computer was on AC?

---

### Post by titico on 2008-10-02
Yes!
I read some articles and all the problem is that Sony install some stuff to deny you the use of non original batteries!!! So you have to buy an expensive sony battery!

---

### Post by titico on 2008-10-04
Well i'll keep googling and trying to solve the problem...

If anyone can give me a hand it will be nice! =]

---

