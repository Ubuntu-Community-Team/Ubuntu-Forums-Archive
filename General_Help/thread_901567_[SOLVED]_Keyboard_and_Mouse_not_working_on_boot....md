---
title: "[SOLVED] Keyboard and Mouse not working on boot....."
date: 2008-08-26
forum: General Help
---

### Post by JabberWalkie on 2008-08-26
So, I have searched for this problem but nothing I found was exactly similar to this. When I boot up, my keyboard and mouse suddenly stop working. The lights turn off and there is no action whatsoever. This occurs AFTER I choose my OS in the grub boot menu. 

I am also running windows XP and my keyboard and mouse work fine there. So I don't think it is a hardware problem. This started to happen just recently; It used to work not too long ago. I don't remember changing anything, so to me this seems like a very strange problem.

I am running ubuntu Hardy...The thing I need help most with is determining if there are any error messages. When I run in recovery mode things wizz by so fast I can't read them....

Anyways, any help would be appreciated.

---

### Post by tech9 on 2008-08-26
> **JabberWalkie said:**
> So, I have searched for this problem but nothing I found was exactly similar to this. When I boot up, my keyboard and mouse suddenly stop working. The lights turn off and there is no action whatsoever. This occurs AFTER I choose my OS in the grub boot menu. 

I am also running windows XP and my keyboard and mouse work fine there. So I don't think it is a hardware problem. This started to happen just recently; It used to work not too long ago. I don't remember changing anything, so to me this seems like a very strange problem.

I am running ubuntu Hardy...The thing I need help most with is determining if there are any error messages. When I run in recovery mode things wizz by so fast I can't read them....

Anyways, any help would be appreciated.

is it both a usb keyboard and mouse...
I have found that I have had some problems with other distros in regards to this... I used a usb keyboard and the OS picked it up

---

### Post by JabberWalkie on 2008-08-26
Yeah, both the keyboard and Mouse are usb. Additionally, I have a USB splitter that is supposed to light up when it is operational, it fails to do this.

---

### Post by JabberWalkie on 2008-08-27
Ok, So I have used a live CD to grab some of the log files:

[/var/log/dmesg]("http://pastebin.com/f3a3de89f")
[/var/log/kern.log]("http://pastebin.com/f1d06db3")

I'm not sure what other log files I should include that will help diagnose the problem. So if anyone wants to see any others just ask.

---

### Post by JabberWalkie on 2008-08-30
Ok, it appears that my USB devices are just slow to respond. It takes a full 10 seconds after x starts for them to work. This never used to occur.....but I guess this "problem" is sort of solved....

---

