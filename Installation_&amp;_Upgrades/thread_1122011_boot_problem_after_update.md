---
title: "boot problem after update"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by gerrit on 2009-04-10
8.04 won´t boot after security updates, doesn´t do anything at all anymore....


After update manager installed some security updates yesterday evening I had to reboot. I do not know which updates it were, but it were not many (system was already almost up to date) I did shut the system down and booted again today... (well, tried to..)

Nothing happens: After a few seconds a black screens tells me: "Starting up..."
That´s all, nothing I can do, it will stay that way for over an hour.
Ran the IDE check in the BIOS, but the drive appeared to be OK

It looks like the update corrupted something inside the box, but I really do not know were to start looking now; don´t even know how I can even look into the system now it won´t boot. (yes, I´m a simple computer user: OpenOffice, Firefox, ...)

Using a HP/Compaq 2.4GHz, 1GB which I bought as an occasion one year ago with 8.04 pre-installed. Always worked fine until this morning... and never had any problems with updates before. 

Any clue what´s causing the problem and what I can do?

---

### Post by meierfra. on 2009-04-10
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the  RESULTS.txt file to your next post (use the code tags).

---

### Post by gerrit on 2009-04-11
Thanks for answer and wow, that LiveCD works! 

I did as you suggested and attach the file "results.txt" to this post
the file is acadabra to me, but I guess it will give you a clue what is going on.

regards

---

### Post by meierfra. on 2009-04-11
> I guess it will give you a clue what is going on.
Well, not really. According the RESULTS everything seems to be in perfect order. 

So lets just try a couple of things and see whether we can get some more clues.

1.  Is there any chance that your Bios are set to boot your 4GB (flash?) drive? If yes, set the Bios to boot from main hard drive.

2.  Reinstall grub:

Boot from the LiveCD, open a terminal and type

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/sda
``` 

3. Edit menu.lst so that the grub menu appears at boot up:

```
gksudo gedit /mnt/boot/grub/menu.lst
```

Change 

hiddenmenu

  to 

#hiddenmenu

and 

timeout 3 

  to 

timeout 10

Save the file and reboot.

Hopefully, the grub menu will appear. Then select Ubuntu at grub menu.

---

### Post by gerrit on 2009-04-14
Yes! this makes a difference!

I get a list now with kernel modules I can choose to boot. The last one (top of the list: kernel2.6.24-23-generic) does not boot. It blanks the screen saying "starting up..." for hours. Also this version´s "recovery mode" does not work. I guess this is the version that has been installed during the last upgrade.

The previous one (2.6.24-22) works OK and boots fine (only says "starting up" for a second or so and than really starts up like in the old days before the upgrade)

Is my latest kernel corrupt? or is it possible that my machine is not compatible with this kernel? (it is a HP/compaq, and I was told HP is pretty compatible with Linux)
I´ve got other even older kernels  (21, 19 and 16) that come from previous upgrades that went flawlessly.

regards, Gerrit

---

### Post by meierfra. on 2009-04-14
> Is my latest kernel corrupt? 

Probably not. But you might completely remove it and then reinstall it with synaptics.

>  is it possible that my machine is not compatible with this kernel?

That would be my guess. As long as your old kernel is working, you can just wait and maybe the next kernel will work again.

---

### Post by gerrit on 2009-04-14
Can you indicate how how I can remove the latest version of the kernel and how to reinstall it with synapsis?

And, if I encounter the same problems with the next upgrade, do I just have to perform the same sequence of commands you just taught me in your previous post? (I copied and pasted them in a small doc in order to remember them for the next time...)

regards, Gerrit

---

### Post by meierfra. on 2009-04-14
> [QUOTE]Is my latest kernel corrupt?
Probably not. [/QUOTE]
I changed my mind. Since you are getting nothing but "starting up" it actually seems likely that the kernel is corrupted.

> how I can remove the latest version of the kernel and how to reinstall it with synapsis?

Open  Synaptics via "System->Administration-> Synaptic Package Manager

Type "linux-generic" in the search box.
Wait  a couple of seconds. The top item should be "linux-generic"
RightClick  "linux-generic" and select "Mark for Complete Removal"
Click on Apply.
After "linux-generic" was removed:
RightClick  "linux-generic"  again and select "Mark for Installation"
Click Apply.


> do I just have to perform the same sequence of commands you just taught me in your previous post?
Actually you won't have to do anything. The grub menu should still appear and you should be able to boot from the older kernel.

---

### Post by gerrit on 2009-04-15
Completely removed the package *linux-generic* and installed it again afterward. Does not make a difference, so guess I´ll have to stick to the older kernel until a newer version comes available.

One last question: If I remove "*linux-generic*" without reinstalling it, will I get a working system "like it was before" with the older version (22) as the default bootable kernel, or will I end up with no system at all?

Thanks for all your kind help!
Gerrit

---

### Post by meierfra. on 2009-04-15
> If I remove "linux-generic" without reinstalling it, will I get a working system "like it was before"

Yes.  But I don't recommend this. I'm not sure but if you remove "linux-generic" you probably won't get anymore kernel updates.

Instead, I recommend to edit menu.lst:

```
gksudo gedit /boot/grub/menu.lst
```

Change 
```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a7178d2d-b51f-4629-b5a0-80e717c6531c ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a7178d2d-b51f-4629-b5a0-80e717c6531c ro single
initrd		/boot/initrd.img-2.6.24-23-generic

```


to

```
#title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a7178d2d-b51f-4629-b5a0-80e717c6531c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-23-generic
#quiet

#title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a7178d2d-b51f-4629-b5a0-80e717c6531c ro single
#initrd		/boot/initrd.img-2.6.24-23-generic

```


If you want, you can also change

"timeout 10" back to "timeout 3"
and
"hiddenmenu" to "#hiddenmenu"

(If needed, you can still get the Grub menu by pressing "Esc" during the "321" countdown at boot up)

---

### Post by gerrit on 2009-04-16
Yes, it works like it did before now, automatically booting with the working kernel.
I understand menu.lst tells grub what actions to take, and this way it now simply disregards the latest update.

Thanks a lot for your help and patient explanation!
Gerrit

---

