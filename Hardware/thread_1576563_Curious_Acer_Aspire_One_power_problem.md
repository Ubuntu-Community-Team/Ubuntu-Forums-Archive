---
title: "Curious Acer Aspire One power problem"
date: 2010-09-17
forum: Hardware
---

### Post by brookster on 2010-09-17
I'm *really *not a Linux expert, so bear with me.

I have a refurbished Aspire One A110 netbook (ZD5), which I use for web browsing and Skype. It's currently running happily on Xubuntu 9.04, with the most up-to-date BIOS version.

Problem is that I'm unable to upgrade because any Ubuntu or Xubuntu version beyond 9.04 won't run on battery power. Unplugging the AC cable (even on a full battery) causes the screen to go blank and I'm unable to recover without resetting the computer. (This also happened with the default Linpus installation it arrived with.)

However, 8.04, 8.10 and 9.04 all work perfectly well on battery power, as does booting into the BIOS. Other (slightly older) Linux distros have also been stable. Therefore, I'm assuming this is something to do with the kernel, but I've been unable to find any reference to this problem. Can anyone help?

---

### Post by dougalkerr on 2010-09-17
Just so that you don't feel lonely coz it looks like a lot of people aren't around just now. It does sound like a kernel problem other wise I would have suggested the BIOS but, because you have upgraded that it is doubtful especially since you say everything works fine with older systems.

If it was my Netbook and it didn't work well from the start I would have been straight back with it. Didn't you ask the retailer?

Fingers crossed someone comes back to you.

---

### Post by brookster on 2010-09-18
> **dougalkerr said:**
> 

If it was my Netbook and it didn't work well from the start I would have been straight back with it. Didn't you ask the retailer?

Fingers crossed someone comes back to you.

Fair point, but I'm in Germany and it came from the UK. As I only paid £100 for it, paying all that postage wouldn't have made much sense. And it works perfectly well with certain distros.

---

### Post by hans12345 on 2010-09-29
I can confirm the problem. Same symptoms when I went from 9.04 to 10.

Hans

A110 SSD

---

### Post by brookster on 2010-11-06
I've tentatively booted into Ubuntu 10.10 on the AA1 and it appears to have fixed the problem. I'm going to replace Xubuntu 9.04 with 10.10 and see if that also works.

---

### Post by brookster on 2010-11-08
And the answer is &#8230; yes it did. Then the OS downloaded all the system updates and it started powering off again.

Harummpph.

---

### Post by P4man on 2010-11-08
You could try this:

Press Alt-F2,  launch gconf-editor.
Navigate to :
Apps / gnome-power-manager / general.

De-select the option "use_time_for_policy".

---

### Post by brookster on 2011-04-09
Resurrecting an old thread here, but the 2.6.35-28 kernel has finally fixed this problem. My old netbook is now running from battery on Lubuntu 10.10 with no problems. (I find the performance of Lubuntu noticeably better than Xubuntu).

Obviously very happy about this, as previously the only OS that worked properly was Xubuntu 9.04!

---

