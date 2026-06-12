---
title: "Installation &amp; Passwords"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by viral1991 on 2009-11-11
Hello, everyone.

I am having some problems with Ubuntu 9.10 & passwords.

Now, I had installed Ubuntu 8.04 on my PC. Then, I installed Windows XP on another drive. This replaced the GRUB booter. For some reason, I could not install GRUB again from the Live CD.

Then, I downloaded Ubuntu 9.10's ISO & burned it onto a CD. Now, when I select the Try Ubuntu or install Ubuntu, it asks me for a password. I don't exactly remember the password of 8.04. 

So, what can I do now? 

Thanks in advance. :)

---

### Post by MichealH on 2009-11-11
Go to your HDD and give me your /boot/grub/menu.lst and also type the output of fdisk -l (L not 1) in a terminal and post them here so we can look at it.

---

### Post by mikewhatever on 2009-11-11
> **viral1991 said:**
> .............

Now, I had installed Ubuntu 8.04 on my PC. Then, I installed Windows XP on another drive. This replaced the GRUB booter. For some reason, I could not install GRUB again from the Live CD.


What do you mean by 'couldn't reinstall'? What happened exactly?

> Then, I downloaded Ubuntu 9.10's ISO & burned it onto a CD. Now, when I select the Try Ubuntu or install Ubuntu, it asks me for a password. I don't exactly remember the password of 8.04. 

So, what can I do now? 

Thanks in advance. :)

That might be a bug, cause it shouldn't ask for passwords just to run the live cd. Also note that 9.10 has a completely different version of GRUB, as compared to 8.04.

---

### Post by viral1991 on 2009-11-11
> **MichealH said:**
> Go to your HDD and give me your /boot/grub/menu.lst and also type the output of fdisk -l (L not 1) in a terminal and post them here so we can look at it.

Thanks for the reply. :)

I have attached the requested file. As for the output, Ubuntu doesn't boot up, so can't open the Terminal.

---

### Post by viral1991 on 2009-11-11
> **mikewhatever said:**
> What do you mean by 'couldn't reinstall'? What happened exactly?



That might be a bug, cause it shouldn't ask for passwords just to run the live cd. Also note that 9.10 has a completely different version of GRUB, as compared to 8.04.

Thanks for the reply. :)

When I entered the 'root (hd0,?)' command, I got an error that the partition couldn't be mounted. (for all drives)

Does the GRUB includes the Live CD menu too? Or just the menu that shows up after Ubuntu's install?

---

### Post by viral1991 on 2009-11-13
I think, I could also format the drive on which 8.04 is installed, & then proceed with a clean install of 9.10.

But, as I cannot boot into Ubuntu currently, is there a way by which the drive can be formatted? :)

Thanks.

---

### Post by mikewhatever on 2009-11-14
> **viral1991 said:**
> Thanks for the reply. :)

When I entered the 'root (hd0,?)' command, I got an error that the partition couldn't be mounted. (for all drives)

You have to replace '?' with a number of the Ubuntu system partition. The partition (hd0,?) doesn't exist, so no wonder it couldn't be mounted.

> Does the GRUB includes the Live CD menu too? Or just the menu that shows up after Ubuntu's install?

No, no live cd menu.

---

### Post by viral1991 on 2009-11-14
> **mikewhatever said:**
> You have to replace '?' with a number of the Ubuntu system partition. The partition (hd0,?) doesn't exist, so no wonder it couldn't be mounted.



No, no live cd menu.

Yes, I replaced the ? with numbers of all the drives. But, none of the drives could be mounted. :)

---

### Post by mikewhatever on 2009-11-16
Interesting. Can you post the output of **sudo fdisk -l** , just to take a look at your partitions. Which of the live cd are you using to reinstall GRUB, 8.04 or 9.10?

---

### Post by viral1991 on 2009-11-17
> **mikewhatever said:**
> Interesting. Can you post the output of **sudo fdisk -l** , just to take a look at your partitions. Which of the live cd are you using to reinstall GRUB, 8.04 or 9.10?

I can't boot into Ubuntu, thus, can't use the command.

I used 8.04's CD. The 9,10 CD asks for a password, so can't boot. :)

---

### Post by mikewhatever on 2009-11-17
> **viral1991 said:**
> I can't boot into Ubuntu, thus, can't use the command.

I used 8.04's CD. The 9,10 CD asks for a password, so can't boot. :)

Well, what about the 8.04 live cd?

---

