---
title: "Ubuntu on external USB drive, cannot mount internal drive"
date: 2009-11-28
forum: Hardware
---

### Post by RRFarFar on 2009-11-28
Hi, everybody
I have returned to ubuntu after missing 9.04))))

I installed Ubuntu on external usb (used ext4), which has also ntfs partition. Now Ubuntu boots when I change setting in BIOS (boot from USB), but it cannot see ntfs partition of internal drive, where Windows is. Ubuntu perfectly sees ntfs which is on external usb drive, but it cannot mount the other one. Any hints why? 
Gparted see sbd(external) normally, but sda(internal) is detected as unreadable with boot flag, and the only thing I can do is format it.
Can anyone help to mount this ntfs partition?
Thx in advance

---

### Post by mikeac72 on 2009-11-28
You installed it on a USB drive! As in a thumb drive? 8/ Or an external hard drive?

Try to boot Windows first, and if it doesn't work, the insternal hard drive is messed up somehow, and you will need to clean install windows, which will allow Linux to see the internal hard drive.  Maybe GParted is corrupted?

---

### Post by RRFarFar on 2009-11-28
> **mikeac72 said:**
> You installed it on a USB drive! As in a thumb drive? 8/ Or an external hard drive?

Try to boot Windows first, and if it doesn't work, the insternal hard drive is messed up somehow, and you will need to clean install windows, which will allow Linux to see the internal hard drive.  Maybe GParted is corrupted?

Thanks very much for your answer.

Windows is booting normally, when BIOS setting is not set to boot from usb or when usb drive is not plugged in. What I want is to enable Ubuntu to browser and of course read/write my ntfs partition which totally occcupies internal harddrive of my laptop. Ubuntu is installed on external harddrive which also has one ntfs partition there. 
The problem is that Ubuntu perfectly mounts external ntfs partition, but completely refuses to mount ntfs partition from internal drive where Windows is.

I installed Ubuntu normally without any special tricks.

---

### Post by adalal on 2009-11-28
> **RRFarFar said:**
> Thanks very much for your answer.

Windows is booting normally, when BIOS setting is not set to boot from usb or when usb drive is not plugged in. What I want is to enable Ubuntu to browser and of course read/write my ntfs partition which totally occcupies internal harddrive of my laptop. Ubuntu is installed on external harddrive which also has one ntfs partition there. 
The problem is that Ubuntu perfectly mounts external ntfs partition, but completely refuses to mount ntfs partition from internal drive where Windows is.

I installed Ubuntu normally without any special tricks.

Does the Windows go through a clean shut down? if not, the Windows partition isn't really unmounted properly, and Ubuntu will kick up a fuss about mounting the NTFS partition. What error do you get on attmpting to mount the internal when running Ubuntu off the external HD?

---

### Post by RRFarFar on 2009-11-29
> **adalal said:**
> Does the Windows go through a clean shut down? if not, the Windows partition isn't really unmounted properly, and Ubuntu will kick up a fuss about mounting the NTFS partition. What error do you get on attmpting to mount the internal when running Ubuntu off the external HD?

Well, I dont get any specific error. Ubuntu simply cannot see internal ntfs partition. 
Another funny thing is that when I fully shutdown Windows, after that laptop boots and I can see Grub menu from external USB (of course whenever it is plugged in). But if I do restart, there is no Grub menu, and laptop boots to Windows, despite USB with Ubuntu being plugged in at boot.
Strange isn't it?

So whenever I want to go to Ubuntu, I need to do full shutdown of Windows.

Also I checked windows ntfs partition for errors, which took a while. No matter that, Ubuntu cannot see it. If I try to list uuid of partitions - it ignores internal hard drive, and Gparted says it is corrupted.

---

### Post by RRFarFar on 2009-11-29
Guys, I am very sorry I never mentioned one thing. My Windows XP partition is encrypted with TRUECRYPT which prompts for password at boot. I guess this is the problem.
I used testdisk in ubuntu to see partition and maybe repait structure, but this is useless in my case. Testdisk cannot see any partitions on my internal disk.
Please advice anybody, I am very willing to fix this issue

---

### Post by RRFarFar on 2009-11-29
I think I solved the issue, which might have been nonexistent by the way))))
So windows ntfs partition was encrypted using Truecrypt, so in order to access under ubuntu one have to install Truecrypt)))))) As simple as that)))))))))
My stupidity shows that truecrypt is actually working you wont be able to access hard drive unless you know the password.
Thanks to everybody)))
Good luck to others

---

