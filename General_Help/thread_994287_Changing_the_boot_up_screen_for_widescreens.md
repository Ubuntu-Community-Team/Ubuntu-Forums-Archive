---
title: "Changing the boot up screen for widescreens?"
date: 2008-11-26
forum: General Help
---

### Post by Psyphre on 2008-11-26
I want to change the boot up splash screen from the generic ubuntu to a custom screen.

I downloaded startup manager (gui for usplash?) but unfortunately it only has 4:3 resolutions and not widescreens.

I found a thread on how to get widescreen boot up splash screens here:
[http://ubuntuforums.org/showthread.php?t=622018](http://ubuntuforums.org/showthread.php?t=622018)
But since its old, I cannot reply in it :(

The solution there seems to have worked for alot of people but unfortunately it does not for me:

----------------------------------------------------

sudo apt-get install hwinfo
sudo hwinfo --framebuffer

Look for your optimal resolution in 24bits.
Write down the corresponding mode #.

sudo gedit /boot/grub/menu.lst

Look for the following line:
# defoptions=quiet splash

Change the vga parameter like this:
# defoptions=quiet splash vga=0x0369
(0x0369 is for 24-bit 1680x1050 in my laptop)

Save, and run the following command:
sudo update-grub

Edit the following file:
sudo gedit /etc/usplash.conf

Change to your resolution, save, and run the following command:
sudo dpkg-reconfigure usplash

----------------------------------------------------

With me when i type in "sudo hwinfo --framebuffer" I get absolutely nothing. No output whatsoever, which surely cant be right can it?

Just wondering if anyone else has had experience in doing this?

Thanks in advance.

PS: my graphics card is an nVidia 7900gs.

---

### Post by binbash on 2008-11-26
Read my howto.The example there is for widescreen @ intrepid

[http://ubuntuforums.org/showthread.php?t=980301](http://ubuntuforums.org/showthread.php?t=980301)

---

### Post by Psyphre on 2008-11-26
oh wow thats a really quick reply. Thanks I'll read it.

edit: I took a look and unfortunately it isnt the same issue as what I have. I am using hardy and my splash screens do change the issue is that I cant get them into widescreen :(

---

### Post by binbash on 2008-11-26
Ok sorry i got your problem now : )

This is my sample for /boot/grub/menu.lst

## ## End Default Options ##

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            520f5484-4708-45aa-996c-4dd2cbc76ac6
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=520f5484-4708-45aa-996c-4dd2cbc76ac6 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            520f5484-4708-45aa-996c-4dd2cbc76ac6
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=520f5484-4708-45aa-996c-4dd2cbc76ac6 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            520f5484-4708-45aa-996c-4dd2cbc76ac6
kernel          /boot/memtest86+.bin


You will add vga=0x0369 after ro quiet splash (for my example grub)

PS : vga=0x0369 is for 24-bit 1680x1050 , there is nothing wrong there.


EDIT : Same with your problem here : [https://answers.launchpad.net/ubuntu/+question/42500](https://answers.launchpad.net/ubuntu/+question/42500)

a HOWTO from dreamlinux forums : 

[http://dreamlinuxforums.org/index.php/topic,1807.msg11543.html#msg11543](http://dreamlinuxforums.org/index.php/topic,1807.msg11543.html#msg11543)

---

### Post by Psyphre on 2008-11-27
Regarding your first post, I just found out I have that problem with my laptop (using intrepid). Your guide worked perfectly thank you very much.

Now back to my desktop, I tried using vga=0369 but unfortunately it says it is not supported when I tried booting up :(
I  guess nvidia 7900 cards dont support it.

---

