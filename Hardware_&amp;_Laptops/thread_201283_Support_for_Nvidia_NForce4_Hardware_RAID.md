---
title: "Support for Nvidia NForce4 Hardware RAID?"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by ZeusABJ on 2006-06-21
Now that I've got my partition scheme figured out I'd like to find the best method to "span" my two brand new Seagate 320GB drives together into one massive 640GB drive for partitioning. I have a DFI NF4 SLI-DR Motherboard, with RAID controllers built in (one Silicon Image controller and one Nvidia NForce4 RAID controller). My original plan was to try and implement hardware RAID-0 with one of those controllers. Now I'm wondering if my kernel has driver support for this sort of thing. So that brings me to my questions regarding RAID support in Ubuntu:

   1. Does anyone know if hardware RAID for either of those controllers will work in Ubuntu?
   2. If hardware RAID is not an option is there a way to "span" two drives together so they appear as one?
   3. Assuming the answer to question #2 is “yes”, will such spanning result in any kind of performance degradation?


Thanks in advance for any advice anyone can offer!

[COLOR="Red"]UPDATE![/COLOR]
These guides helped me (if anyone else is dealing with this issue):

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[https://help.ubuntu.com/community/In...tion/LVMOnRaid](https://help.ubuntu.com/community/In...tion/LVMOnRaid)

---

### Post by ZeusABJ on 2006-06-22
Well, I guess no one here knows how to do this. Lucky for me after a *LOT* of digging online I found the solution:

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

I also noticed that I'm not the only person asking this question on these forums. Many of those threads have not received any replies so if one of the MOD's makes this a sticky or something that should take care of any future posts on this matter.

---

### Post by rsk on 2006-06-22
Was just wondering how to do this with the same mobo, thanks for following up.

---

### Post by ZeusABJ on 2006-06-22
[QUOTE=rsk]Was just wondering how to do this with the same mobo, thanks for following up.[/QUOTE]

Yeah it works but it can be a little flaky. I did more research and learned that dmraid is a lot more stable if your distro is running the 2.6.17.1 kernel. Unfortunately I've never changed out a kernel before and it sounds a little extensive. Anyone know if Ubuntu supports the 2.6.17.1 kernel and how hard it is to upgrade to it?

---

### Post by rsk on 2006-06-22
[quote=ZeusABJ]Yeah it works but it can be a little flaky. I did more research and learned that dmraid is a lot more stable if your distro is running the 2.6.17.1 kernel. Unfortunately I've never changed out a kernel before and it sounds a little extensive. Anyone know if Ubuntu supports the 2.6.17.1 kernel and how hard it is to upgrade to it?[/quote]

Hmm, that's a little disheartening considering that 2.17 just got out the door and SATA RAID has been on these motherboards for almost 3 years now. At this stage if it's still "a little flaky" my guess is that it's either better to step back to soft raid in the kernel and let the CPU do everything or scrap it all together.

Have you considered moving to straight SoftRAID and not messing with FakeRAID? From what I read, the CPU is doing everything anyway, it's just FakeRAID "fakes" like the controller is doing hardware raid to give the same impression Windows does when you use the IDE driver, but SoftRAID makes no attempt at convering up the fact that the CPU is doing all the work.

---

### Post by ZeusABJ on 2006-06-22
[QUOTE=rsk]Hmm, that's a little disheartening considering that 2.17 just got out the door and SATA RAID has been on these motherboards for almost 3 years now. At this stage if it's still "a little flaky" my guess is that it's either better to step back to soft raid in the kernel and let the CPU do everything or scrap it all together.

Have you considered moving to straight SoftRAID and not messing with FakeRAID? From what I read, the CPU is doing everything anyway, it's just FakeRAID "fakes" like the controller is doing hardware raid to give the same impression Windows does when you use the IDE driver, but SoftRAID makes no attempt at convering up the fact that the CPU is doing all the work.[/QUOTE]

I have no idea what my options are!!! I'm only following that guide because it’s the only thing I can find on the matter. If this "SoftRAID" will do the trick, please tell me how to use it. I can't seem to find any way to make GPartED span or RAID my disks together. Is there a guide for using SoftRAID?

[COLOR="Red"]UPDATE![/COLOR]
These guides helped me (if anyone else is dealing with this issue):

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[https://help.ubuntu.com/community/In...tion/LVMOnRaid](https://help.ubuntu.com/community/In...tion/LVMOnRaid)

---

