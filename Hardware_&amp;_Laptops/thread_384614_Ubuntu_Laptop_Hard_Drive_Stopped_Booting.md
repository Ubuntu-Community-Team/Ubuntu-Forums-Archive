---
title: "Ubuntu Laptop Hard Drive Stopped Booting"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by jimmywet on 2007-03-14
I used the live CD to install Ubuntu to an seperate hard drive for my IBM T41 laptop.  Everything is good and I am lovin' the Ubuntu.  I removed the CD bay and placed the Ubuntu hard drive in its place and returned the "normal" hard drive to the "normal" position to use the bios to switch hard drives and their seperate OS's, as I try to move to Ubuntu more and more.

I am sure you know what happened, it will not boot in the second Hard Drive postion.  Since I am new to Linux, I have discovered that I need to identify the new hard drive position HD0 to HD1, so it can boot properly, but I can not find exactly where to make that change, or how.  I read that you should not make that change with a graphical interface and it also sounds like there may be several places to edit.

I can already see there may be times I want to put it back in the primary possition, for example to use the CD/DVD, but those are rare (Plus that requires tools to change, where the second position does not.  Could I use Grub Commands to make the switch easier and eliminate the start-up script?  There has to be an easy way.

Please help me out!

Jim

---

### Post by matburton on 2007-03-14
Hey,

I take it what you mean is that when you move the hard disk then grub can't boot ubuntu because it can't find it.

To edit where your hard drive is you want to edit the grub menu:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst

```

In there you can change where grub will try and boot ubuntu from. I'm not grub expert and someone may come up with a better solution but you could simply make another entry for each position your hard disk could be in.

e.g.
```

title		Ubuntu on HD0
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu on HD1
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

Hmmm don't trust the snippet above completely, it's an idea for what you could do.
That seems a messy solution as well, I hope someone comes up with a better way of doing this.

---

### Post by jimmywet on 2007-03-19
Thanks matburton,

I tried that and several variations and it still will not boot in the second position.  Must be other adjustments that have to be made.

I have also tried to use a spare USB Drive as the ubuntu Live CD to install again, while it is in the correct position, but I can not get that to even run....  :( 

Thanks again and hopefully someone will have another idea....


Jim

---

### Post by DonFunBuBai on 2007-03-25
I had the same problem before. I think it happens to everyone atleast once. I now found the solution to it. Believe it or not if you find that your bootup process is stuck ie, the bootup looks like it's not reading from hard drive, do the following

press ctrl + Alt + Del once, remember, only once. You'll see the process bar will resume and start reading again

whenever this happens to me, I do this and it works 9 out of 10 times

---

### Post by Madmoose on 2007-03-25
Do you have LoJack installed?  I was having the same problem with my laptop removing the MBR, but then found out it was LoJack that was doing it. 


I never found out how to stop LoJack from doing it, so I don't' have it Ubuntu installed on my laptop anymore.
You can check out here: [No here]("http://www.users.bigpond.net.au/hermanzone/p18.htm") to unintall Ubuntu, and some easy MBR fixes.

---

