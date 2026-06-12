---
title: "My system will not boot"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by Midnight Dragon on 2008-03-09
Hi, I wasn't exactly sure where to post this. Since I have Ubuntu installed on my laptop I will ask here.

I've had Ubuntu 7.10 installed on my Toshiba Satellite A45-S150 laptop for about a week now. It's been quite a pleasant experience and it runs very well on this old machine. But now it has a problem booting. I haven't made any serious systemwide changes, and the last thing I did before shutting it down was install theme extras and login windows from the terminal. Now it won't start up, it just shows a black screen.

I decided to try booting to recovery mode, but it tells me that the "fsck" failed and that it "must be done manually."

Does anyone know what's wrong? I've used Linux before but I'm still a bit uneducated when it comes to problems such as these. Thanks a lot.

---

### Post by Ozzz on 2008-03-09
fsck is a file system checker program.

Run fsck.ext2 on the root partition, or other partition that failed during boot. So, if your root partition is on /dev/sda1 and it fails, run

```
fsck.ext2 /dev/sda1
```

---

### Post by Midnight Dragon on 2008-03-09
Thanks, I typed this in recovery mode. It went through a lot of fixes that I had to type Y for, then it rebooted and the screen went blank like before. So I tried it again and this time I didn't have to type it, it just did the fsck on its own, then rebooted again. But it still wouldn't boot up.

I don't know what happened. My laptop still refuses to boot. Is there anything else that can be done to solve this problem? Thanks.

---

### Post by r3d33m3r on 2008-03-10
Im having a similar problem. My laptop crashed while starting up the game World Of Warcraft for the first time. I had to force power off the laptop manually as it wouldnt respond to anything. Now when I restart my laptop, it just goes blank, after saying 'loading please wait', I am about to try the fsck method right now to see if that helps.

---

### Post by Midnight Dragon on 2008-03-10
> **r3d33m3r said:**
> Im having a similar problem. My laptop crashed while starting up the game World Of Warcraft for the first time. I had to force power off the laptop manually as it wouldnt respond to anything. Now when I restart my laptop, it just goes blank, after saying 'loading please wait', I am about to try the fsck method right now to see if that helps.

So I'm not the only one? Wow, hope fsck works on your machine. I'm still hoping for a solution to my problem.

---

