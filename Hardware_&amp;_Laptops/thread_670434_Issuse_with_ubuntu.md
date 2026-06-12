---
title: "Issuse with ubuntu"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by Whiteice on 2008-01-17
I have a HP dv6324us laptop. Long story short I got ride of vista that was on it and I recently had PCLINUXOS installed. I have always wanted to use ubuntu but have always had problems with the installation. I have just installed ubuntu on my laptop and first issue I am having is a black screen when I go to boot. I tried adding noapic nolapic irqpoll to the kernel boot. But that hardly works and most the time it just loads about a 1/8 the bar when booting. But when it does work when I shut down my system it freezes.

1. Ubuntu freezes
2. Ubuntu freezes on shutdown

can anyone help me out?

---

### Post by theophile on 2008-01-17
Which version of Ubuntu are you trying to use? There were reports that 7.04 caused these problems but 7.10 solved them.

---

### Post by Whiteice on 2008-01-17
6 i beleive

---

### Post by theophile on 2008-01-17
God Lord, man, use the latest version!

---

### Post by Whiteice on 2008-01-17
Tried the same thing happened. I got to the desktop once out of almost 20 tries. This was just the only one i had lying around. I was hopeing that the problem was possably solved.

---

### Post by Pandemic187 on 2008-01-17
Yeah, unless you're using LTS, there's no reason to use 6.

---

### Post by Whiteice on 2008-01-17
LTS? All I know is i download it last year and it was in my cd binder. I was hunting through it one day decided to install ubuntu. DL'ed the lastest version which was gutsy tried to install and got a black screen. Decided to go with PClinux for awhile. Got feed up with it and tried to install my old ubuntu disk because gutsy was nowhere to be found.

---

### Post by theophile on 2008-01-17
Use the Gutsy LiveCD before trying to troubleshoot an old version.

---

### Post by Whiteice on 2008-01-17
I tried it with nosplash i beleive. Still i got nothin.

---

### Post by theophile on 2008-01-17
Are you saying the kernel doesn't even post? Sounds like you have a bad CD.

---

### Post by Whiteice on 2008-01-18
OK Just found my gutsy disk. I tried to install and got a blank screen. So then i went and changed the boot to no splash nodma nopica. That worked. I got into the os and installed ubuntu. But when i reboot I have to enter the no splash nodma nopica every time i boot. Is there a way to fix that.

---

### Post by Whiteice on 2008-01-18
Don’t mean to double post but for anyone else out there with the same problem as me. Here’s the solution.

First off you need to boot into ubuntu. But every time it boots it freezes. To get past this when the grub loader appears hit the escape key to get into the kernel boot editor. Then select kernel and hit e to edit it. You will see something like this

root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet splash

delete quiet splash

add right after ro

noapic nolapic irqpoll nodma nopica

so it looks like this 

root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro noapic nolapic irqpoll nodma nopica

then hit enter and b to boot

you will see the ubuntu bar and right beneath it will be text of what you system is doing.

if done correctly you should then be taken to the login screen.

once I ubuntu type this command in terminal (under applications accessories)

gksudo gedit /boot/grub/menu.lst

it may ask for password if not just continue

a new window will appear

scroll down to the entry that says something like this

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

where is says

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet

replace the quiet splash just like before then save and reboot.

if down correctly your system should boot fine.

If anyone as any questions feel free to pm me.


thanks to all who had helped me with this problem.:KS

---

