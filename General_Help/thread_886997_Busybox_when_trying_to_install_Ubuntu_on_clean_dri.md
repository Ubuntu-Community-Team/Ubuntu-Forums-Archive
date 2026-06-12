---
title: "Busybox when trying to install Ubuntu on clean drive"
date: 2008-08-11
forum: General Help
---

### Post by .Quagmire. on 2008-08-11
I recently had Windows XP on a very old system that recieved a virus and then wouldnt boot past the XP load screen. 

Figured it was a good time to switch over to Ubuntu.

Got whatever I wanted of my original 40gb drive that came with the computer and put it on my 200gb drive via a external enclosure and another computer in my house.

Went to install Ubuntu onto the now formatted original 40 gb drive.

Now instead of going into the install questions it gives me a Busybox page listing this:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12, Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   116.057082] ata1.01: exception Emask 0x0 SAct 0x0 Serr 0x0 action 0x2 frozen
[   116.057144] ata1.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 dma 4096 in
[   116.057195] ata1.01: status { DRDY }

Now I ask you wizards of ubuntu... what the heck does all that mean...

I am completely new to ubuntu, so I need some help so I can have a computer again!

Computer is:

Old Gateway desktop (dont know the model)
1.8 P4
40gb original Wester Digital Harddrive
200gb internal Seagate Barracuda
256Mb DDR Ram (I know I need more!)

---

### Post by .Quagmire. on 2008-08-11
Bump please someone help me! Ive read it might be something to do with my drives... so im gonna go check the connections...

Some one tell me if im right!

---

### Post by starcannon on 2008-08-11
at busybox try entering
```
modprobe ide-generic
```

Press CTRL-D and continue booting.

If that does not work, then when you first boot the CD, choose to Verify the CD(I have the wording wrong, but you'll see the option in the menu) and make sure that your CD burned correctly.

GL let us know how it pans out.

---

