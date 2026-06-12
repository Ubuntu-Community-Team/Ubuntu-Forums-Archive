---
title: "Ubuntu on HP255 G3 with dual boot"
date: 2015-08-27
forum: Hardware
---

### Post by Naggobot on 2015-08-27
I had some troubles and pains with getting the dual boot to work in HG255 G3 laptop.  I outline what I did in case it helps someone.

Warning! Do not just follow these instructions, understand what you do. Read all relevant links and instructions. Messing up this will break your system. 
Do not just copy the commands from posts. Also this post just outlines what I did and is not meant as step by step instruction. 
There may be errors since all in all it took two evenings of googling and testing to get the dual boot working.  

Also check my last thoughts from bottom before starting. It may save you time and trouble. 

Please note that this is HP Laptop specific stuff and other devices may be a bit more easy. 

1. Install Ubuntu according to instructions in [http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/). I wanted to keep the secure
 boot enabled so I modified this a bit, I just skipped step 5. The you can execute the command 
```
bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
```

but it probably does nothing. Worth testing though. 

2. Since with previous the system still boots in Windows check the Ubuntu installation by pressing ESC during boot up. 
Select F9 and you can select Ubuntu. Once Ubuntu works you can follow the instructions in 

[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and-Software/Changing-Boot-Order-on-Dual-Boot-Windows-8-and-Ubuntu/td-p/2503733](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and-Software/Changing-Boot-Order-on-Dual-Boot-Windows-8-and-Ubuntu/td-p/2503733)

see sixth post on first page. Notice that this instruction is written for non secure boot. For secure boot you will want 
to replace shimx64.efi instead of grubx64.efi  

Do not execute step 7. Bios will overwrite any changes you make to the boot order. Ubuntu needs to be in slot 0002. 
0001 might work but I did not test it. Verify that your Ubuntu boot manager is in slot 0002 with 

```
sudo efibootmgr -v
```

Then delete the entries 0 and 1
(Writing this I must realize that this might not be necessary)

```
sudo efibootmgr -b 0000 -B 
```

```
sudo efibootmgr -b 0000 -B 
```
At this point it is probably a good idea to do the last step as instructed. I messed this up and I had tofollow instructions from 
[http://askubuntu.com/questions/551592/how-to-permanantly-change-boot-order-in-uefi-os-manger-list](http://askubuntu.com/questions/551592/how-to-permanantly-change-boot-order-in-uefi-os-manger-list)

From there you can find instructions on how to create a new Grub entry. You will need to have windows as grub entry. 

Now the system should boot to Ubuntu and there should be a grub entry for windows. You should test the grub entry for 
Ubuntu first and then for windows. If your system works same as mine and you have followed the instructions correctly 
both ubuntu boot and windows boot should work. 

Problem is that if you boot to windows the Grub will appear only once. Next task is to fix this. For this instructions can be found from 
[https://bbs.archlinux.org/viewtopic.php?id=166629](https://bbs.archlinux.org/viewtopic.php?id=166629)

Use Esc and F9 again to boot to Ubuntu and disable Windows entry. It should be 0000. Verify this first with efibootmgr. 

```
# efibootmgr -A -b 0000
```

After this the system should boot to Grub even after you boot to Windows. 


After thought
Instead all previous hazzle it might be worth trying to disable the windows related 
entries with out actually renaming any windows boot files. Logically it should work. 
If someone tries this please comment.

---

### Post by Naggobot on 2015-09-13
Even though everything worked fine I ended up returning this to shop. Performance was abysmal both in Windows and in Ubuntu. Not recommended.

---

