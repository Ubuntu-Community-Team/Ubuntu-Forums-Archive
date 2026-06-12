---
title: "help after updates"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by vonzipper27 on 2009-02-12
ok, so, I am really new to all this, but I like it alot so far. I have an issue though. I ran updates today, and it said that i had to reboot, i did, and when it boots the screen is jacked up on the top, and does not change. you can hear the computer boot as normal, plays the little song and all that, but the screen is frozen. When I reboot and hit escape, I can choose the option to load the .7 version instead of the .11 and it all comes up and works fine then. Is there (and i am sure there is) a way to get that .11 one out of there so I do not have to hit escape every time i boot? I want to thank you in advance!

---

### Post by Partyboi2 on 2009-02-14
One way is to edit your /boot/grub/menu.lst so that it boots the '.7' kernel automatically.
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)
If you want you can also adjust the time before it boots the default choice.
[http://users.bigpond.net.au/hermanzone/p15.htm#timer](http://users.bigpond.net.au/hermanzone/p15.htm#timer)

If you get stuck post your grub menu.lst
```
cat /boot/grub/menu.lst
```

---

### Post by vonzipper27 on 2009-02-14
its not about it dual booting. My problem is that the version ending in .11 locks up my screen, so after i see the bios screen I hit esc, and select the .7 version to boot from. Any help?

---

### Post by Partyboi2 on 2009-02-14
You can change the "default" setting in your grub menu to effect which kernel is booted into at startup. It does not matter if you are dual booting or single booting. (that above link refers to dual boot but works the same for single boot)
One option is to change "default" from "0" to "saved' this means that grub will remember whatever menu entry you selected at boot last time and means that you do not have to re-edit you menu.lst each time there is a kernel upgrade. 

Another option is to change "default 0" in your menu.lst to the number that corresponds to the kernel entry in the grub menu.lst. These start from 0 when counting. You need to look for this section in your /boot/grub/menu.lst (yours will not be exactly the same as below)


```

## ## End Default Options ##

title        Ubuntu jaunty (development branch), kernel 2.6.28-7-generic
uuid        ff13903a-c958-47a0-8292-f482063226ee
kernel        /boot/vmlinuz-2.6.28-7-generic root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro quiet splash 
initrd        /boot/initrd.img-2.6.28-7-generic
quiet

title        Ubuntu jaunty (development branch), kernel 2.6.28-7-generic (recovery mode)
uuid        ff13903a-c958-47a0-8292-f482063226ee
kernel        /boot/vmlinuz-2.6.28-7-generic root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro  single
initrd        /boot/initrd.img-2.6.28-7-generic

title        Ubuntu jaunty (development branch), kernel 2.6.28-6-generic
uuid        ff13903a-c958-47a0-8292-f482063226ee
kernel        /boot/vmlinuz-2.6.28-6-generic root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro quiet splash 
initrd        /boot/initrd.img-2.6.28-6-generic
quiet

title        Ubuntu jaunty (development branch), kernel 2.6.28-6-generic (recovery mode)
uuid        ff13903a-c958-47a0-8292-f482063226ee
kernel        /boot/vmlinuz-2.6.28-6-generic root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro  single
initrd        /boot/initrd.img-2.6.28-6-generic

title        Ubuntu jaunty (development branch), memtest86+
uuid        ff13903a-c958-47a0-8292-f482063226ee
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```So if I was wanting to set "Ubuntu jaunty (development branch), kernel 2.6.28-6-generic" as my default to boot into I would start from 0 and count
```
0 = Ubuntu jaunty (development branch), kernel 2.6.28-7-generic
1 = Ubuntu jaunty (development branch), kernel 2.6.28-7-generic (recovery mode)
2 = Ubuntu jaunty (development branch), kernel 2.6.28-6-generic
3 = Ubuntu jaunty (development branch), kernel 2.6.28-6-generic (recovery mode)
```You can see "Ubuntu jaunty (development branch), kernel 2.6.28-6-generic" is number 2 so I would change "Default 0" to "Default 2"
The only thing with this option is that when there is a kernel upgrade you would need to change the default setting again.
After you have saved the changes in a terminal update grub with
```
 sudo update-grub
```

---

