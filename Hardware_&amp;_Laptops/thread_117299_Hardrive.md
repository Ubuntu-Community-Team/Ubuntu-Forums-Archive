---
title: "Hardrive"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by gman2004 on 2006-01-14
I looks like I loosing my C drive. I have windows xp and ubuntu booting from there. I want to reinstall windows so I can retrieve some data. What is going to happen to ubuntu? Ubuntu is located on another disk. Is there a way of going through this pain as painless as possible?

---

### Post by gosh on 2006-01-14
Because you probably have seperate partitions for Windows XP and Ubuntu a fresh installation of XP will work.

But what exactly are you problems? You might not need to reinstall.

---

### Post by gman2004 on 2006-01-14
I can't log on to windows. I tried every logon option and keeps on rebooting

---

### Post by gman2004 on 2006-01-14
I reinstall windows and I can't multiboot. Do I have to re-install ubuntu? If I have to, Do I loose the data on my drive?

---

### Post by handy on 2006-01-15
You have to reinstall GRUB, if you search the forums you will find very good instruction.

So, basically no, you do not have to reinstall Ubuntu. :KS

I searched for you, the link below is short & sweet, but have a look at the link it sugests too, between those two you are quickly out of trouble... :KS 

[http://ubuntuforums.org/showthread.php?t=114332](http://ubuntuforums.org/showthread.php?t=114332)

---

### Post by mips on 2006-01-15
Why dont you just boot into ubuntu, mount the windows drive and recover the data from ubuntu ???

---

### Post by gman2004 on 2006-01-16
**_handy_** thank you, I followed the link and I'm going through to find the solution. The only problem I have (I don't know if it is normal) is that windows does not see my ubuntu harddrive.
**_mips_**, thanks; I did that and I reinstalled windows, but as you understand I have to reistall windows for my kids.

---

### Post by handy on 2006-01-16
That's normal!

A good reason to have a fat32 partition somewhere so if you need to make something easily available to windoze, you just put it across from Ubuntu (linux) to the fat32 part'!

All the best...

---

### Post by gman2004 on 2006-01-29
I tried every single method discribed at the forums. I tried last the first at [http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

I don't know what I really did, But I have my[FONT=Arial Black] UBUNTU[FONT=Verdana] running again:). Thank you all for a job very well done:KS. 
If I didn't need windows for my kids and a work application I wiil definetly never use windows=D>=D>[/FONT]
[/FONT]

---

