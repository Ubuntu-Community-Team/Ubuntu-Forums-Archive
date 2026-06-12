---
title: "Jaunty sticking at &quot;Starting Up&quot;"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by shayguitarra on 2009-04-24
Hi,

There seem to be variations of this problem throughout this forum, with different characteristics. So apologies if it's starting to become repetitive.

First off, I am using an ati graphics card that was using the fglrx driver and decided to continue with the upgrade after receiving the warning, thinking I would just use the open source driver. So if that makes me an idiot, then I'm an idiot! Also, I have an nvidia card that I can replace it with.

Did the automatic upgrade through adept. Everything went fine. Upon restart it gets as far as 'starting up' and halts.
I have tried the three different kernel versions.
I tried replacing the graphics card with another ati, and also the nvidia one to no effect.
With the original graphics card reinstalled I tried recovery mode on the three different kernels. It stalls at "PCI (lots of zeroes) HTI MSI mapping". I can't be more precise as I'm writing this from memory on my work pc, but I'm guessing that this is in some way related to my pci express slots, one of which contains the graphics card.
If I try recovery mode a few times it does eventually get past this and bring me into the options menu, but I'm not sure what, if anything I should do to fix the problem. However if I resume normal boot it completes without a problem. It works fine although there are certain graphics issues. But I was kind of expecting that.

So any suggestions? Is there something I can do to fix this? Or should I just back up everything I need and try a clean install of Jaunty from the cd? Any help appreciated. :confused:

---

### Post by shayguitarra on 2009-04-24
After much wailing and gnashing of teeth I seem to have stumbled on a solution of sorts. I entered edit mode on the first kernel and the top line was 'root  (hd0,0)'. I pressed Delete and then Boot and after running through a few checks my pc boots as normal.

Does what I have done here make more sense of my problem? And if so how do I make it permanent so I don't have to edit each time I boot? Or have I inadvertently done something really crazy?

PS I did this using my nvidia 9500GT card not my ati, and the proprietary drivers (173 and 180) still don't work so I'm using the open source ones at present. So far so good with them.

---

### Post by ronparent on 2009-04-24
I haven'tbeen able to get as far as you have. But regarding your boot/grub problem, just **sudo gedit /boot/grub/menu.lst**, and you can edit and make your change permanent by then saving.

---

### Post by shayguitarra on 2009-04-24
Thanks a lot. Hope you get sorted out soon.

---

### Post by shayguitarra on 2009-04-24
OK, now I'm officially confused.

This solution has stopped working, and I'm back to the hanging at Starting Up... behaviour. I am lost as to why this has happened. The behaviour seems completely random. I am not changing anything, it is simply the case that under the same conditions each time sometimes it works and most times not. So it really is not a workable solution.

But, and this is where my confusion comes in, I can now boot normally (nvidia graphics card, not ati) using kernel 2.2.24-22. I get the ubuntu logo as it loads instead of kubuntu but it goes to the kde login window and is working fine. I have tried rebooting four times now without a problem. I am assuming nothing however.

---

### Post by kenfeyl on 2009-04-25
I had the same problem myself -- sticking at "Starting up" for the latest kernel. The diagnostics seemed to indicate that it was getting stuck after trying to load ACPI -- adding "acpi=off" to the kernel boot line (second line in "e" mode) fixed it, and now my laptop boots Ubuntu normally. Make the change permanent by editing menu.lst as described above.

---

### Post by Monsieur Gonzalez on 2009-04-25
Can you try to boot without the bootsplash? That way, you'd be able to check what's going on, where the boot process stops. You have to enter the failsafe mode at startup in grub's menu.

---

### Post by shayguitarra on 2009-04-25
Hi, 

Thanks for the suggestions.

@kenfeyl I tried adding acpi=off and it did get past 'starting up...' but then it told me it wanted to boot in low graphics mode, which I let it do. At which point it seemed to run through a few process and the screen went blank and stayed that way.

@Monsieur Gonzalez Is failsafe mode the same as recovery mode? If so it's stopping at PCI (0000.00.00) Starting HTI MSI mapping. (My motherboard is MSI). If not if you could let me know how to enter it.

Before I started booting to the old kernel it would sporadically go past this point in recovery mode and boot up properly but I had no idea when or why it would do it.

---

### Post by Monsieur Gonzalez on 2009-04-26
I meant recovery mode, yes. Do you know the exact model of your motherboard?

---

### Post by shayguitarra on 2009-04-26
It's the K9N SLI Platinum. It's about two years old if that helps.

---

### Post by pomalin on 2009-04-26
Can you watch my bug report open since 15/03.
Perhaps you have the same problem.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268")

---

### Post by shayguitarra on 2009-04-26
Problem seems almost identical. I'll add my voice to the thread. Thanks for spotting this.

---

