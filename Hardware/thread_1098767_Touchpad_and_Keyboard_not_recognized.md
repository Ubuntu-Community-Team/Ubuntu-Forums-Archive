---
title: "Touchpad and Keyboard not recognized"
date: 2009-03-17
forum: Hardware
---

### Post by phamtieugiao on 2009-03-17
Touchpad and Keyboard of laptop NEC Versa E6500 do not work.

I have been waiting for several version of Ubuntu from 7.10 to 8.10. But none of them works. No update on the driver for this laptop model.

I am so dissappointed :(. Version 8.10 works great on my laptop except the touchpad and the keyboard :(.

I know the problem is of the Linux kernel becuz a lot of other distributions (e.g. PCLOS, Mandriva, Fedora, SuSE, etc.) did not work too. So it is no point to post this thread here. Ubuntu developers themselves cannot fix this problem. It is up to the Linux kernel developers. :(

I even tried PC-BSD, freeBSD, Open Solaris. On those OSes, keyboard and touchpad works fine, but other drivers are so terrible.

I am still hopelessly waiting for the next version to fix the problem :( :( :( Why is it so difficult for me to look for an Opensource OS solution!

---

### Post by neolaw on 2009-05-14
> **phamtieugiao said:**
> Touchpad and Keyboard of laptop NEC Versa E6500 do not work.

I have been waiting for several version of Ubuntu from 7.10 to 8.10. But none of them works. No update on the driver for this laptop model.

I am so dissappointed :(. Version 8.10 works great on my laptop except the touchpad and the keyboard :(.

I know the problem is of the Linux kernel becuz a lot of other distributions (e.g. PCLOS, Mandriva, Fedora, SuSE, etc.) did not work too. So it is no point to post this thread here. Ubuntu developers themselves cannot fix this problem. It is up to the Linux kernel developers. :(

I even tried PC-BSD, freeBSD, Open Solaris. On those OSes, keyboard and touchpad works fine, but other drivers are so terrible.

I am still hopelessly waiting for the next version to fix the problem :( :( :( Why is it so difficult for me to look for an Opensource OS solution!

Yes, I recently bought an NEC Versa E6510. Ubuntu 8.04 doesn't have compatible driver for its graphic card (NVIDIA GeForce 9600M GS). I waited until Ubuntu 9.04. Now OS installation is done, thanks to my USB keyboard and mouse. 

The touchpad and keyboard is still freezing.

I've tried changing the locale to French (not work).

I've tried puting i8024 reset option when booting (far from work)

Dear developers, We are waiting. We thank you. But we are waiting.

---

### Post by wisnu999 on 2009-06-08
Have same problem with NEC versa E6500

I have tried some H*ckintosh distro and it have same problem with linux but I notice in kaliway 10.5.2 touchpad is work but keyboard is freezing

---

### Post by ysnobr on 2009-11-23
Hi,
I am also an owner of NEC Versa E6500.

After installing Ubuntu 9.10, I am not able to use the laptop's keyboard and touchpad.

I was able to connect a USB mouse and log in to the system using the virtual keyboard.

I tried to dig in there to see if there were some settings I could tweak to return keyboard and touchpad functionality.

Unfortunately, being a newbie at Ubuntu I did not really know what to look for.

Looking for some assistance from the experts here who may have an idea on how I can get the keyboard and touchpad to work.

I am eager to learn and use a new OS other than Windows.

Thanks!

---

### Post by alfach on 2009-11-23
hi guys, i also using nec versa E6500. I think it was bug in kernel. Cause i'm trying to use with other distro, same problem, and it also not working since older version ubuntu.

but, i trying to add : "i8042.noaux=1" in the following line in /boot/grub/menu.lst after splash

and after that my keyboard working, but for touchpad it still doesn't :(

and i also trying in the line of recovery mode, because sometimes it doesn't work in splash mode. So, this is my grub looks like :


```
title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		800d1810-eefb-43e3-8fac-f828dfb3b580
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=800d1810-eefb-43e3-8fac-f828dfb3b580 ro quiet splash i8042.noaux=1
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		800d1810-eefb-43e3-8fac-f828dfb3b580
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=800d1810-eefb-43e3-8fac-f828dfb3b580 ro  single i8042.noaux=1
initrd		/boot/initrd.img-2.6.31-14-generic
```

---

### Post by mjr1 on 2009-11-23
Hi, I have a similar problem with my Kogan Agora Pro netbook.  The keyboard is fine but the touch pad does not work.  Just installed 9.10.  Previously ran GOS which worked fine with the touchpad but refused to recognize an external hard drive.  Ubuntu has fixed that issue but now no touch pad...very frustrating!

---

### Post by ysnobr on 2009-12-01
hi, alfach,
may i ask how you got the keyboard to work?
sorry, i am still a linux newbie, and not sure how to do this.

thanks...

---

### Post by phamtieugiao on 2009-12-26
> **alfach said:**
> hi guys, i also using nec versa E6500. I think it was bug in kernel. Cause i'm trying to use with other distro, same problem, and it also not working since older version ubuntu.

but, i trying to add : "i8042.noaux=1" in the following line in /boot/grub/menu.lst after splash

and after that my keyboard working, but for touchpad it still doesn't :(

and i also trying in the line of recovery mode, because sometimes it doesn't work in splash mode. So, this is my grub looks like :


```
title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		800d1810-eefb-43e3-8fac-f828dfb3b580
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=800d1810-eefb-43e3-8fac-f828dfb3b580 ro quiet splash i8042.noaux=1
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		800d1810-eefb-43e3-8fac-f828dfb3b580
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=800d1810-eefb-43e3-8fac-f828dfb3b580 ro  single i8042.noaux=1
initrd		/boot/initrd.img-2.6.31-14-generic
```

I did add i8042.noaux=1 to the menu.lst like you said, and, cannot believe it, the keyboard works finally. Thanks a billion, you saved my Ubuntu ^^!
The only chunk is to get the touchpad working! Hope someone will find out how soon!

---

### Post by Sergey Kulikov on 2010-01-02
How do I apply this solution in Ubuntu 9.10? If I understand it correctly, grub got updated to grub2. As a result /boot/grub/menu.lst file is no longer there for editing. So what do I need to edit to get the keyboard working. The touchpad issue is not as important to me because I carry my usb mouse with me everywhere. Thanks for the help in advance.

---

### Post by neolaw on 2010-03-10
I will try with live CD and tell you the story shortly.

---

### Post by neolaw on 2010-03-14
> **neolaw said:**
> I will try with live CD and tell you the story shortly.

Not working.

---

### Post by Fitra Nugraha on 2010-05-22
problem about keyboard was resolved on ubuntu 10.4 (lucid) but touch-pad still freeze :(

---

### Post by damouille on 2010-11-01
Any news on Touch-pad? I use Maverick 10.10 and can't get the touch pad working.

---

