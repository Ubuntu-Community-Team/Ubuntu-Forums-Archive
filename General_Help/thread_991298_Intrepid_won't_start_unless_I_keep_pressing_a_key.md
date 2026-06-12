---
title: "Intrepid won't start unless I keep pressing a key"
date: 2008-11-23
forum: General Help
---

### Post by Friccy on 2008-11-23
Hi!
I have just installed Intrepid after Hardy. I have made a clean install, formating the partition.
But, after GRUB and choosing Ubuntu, nothing happens, just a black screen.
If I press a key (any) and keep pressing it, Intrepid loads.
Can any of you help me with a cure for this?
Thanks!

---

### Post by __Ryan__ on 2008-11-23
Have you checked your system logs?

---

### Post by binbash on 2008-11-23
edit your grub and disable splash screen and checkout what is wrong

---

### Post by Friccy on 2008-11-24
> **__Ryan__ said:**
> Have you checked your system logs?

How do I do it and what shall I look for?
Today it started automatically after grub, but have loaded just half of it and than just freezed till I pressed a key.

---

### Post by __Ryan__ on 2008-11-24
Open a terminal and enter 

```
dmesg | less
```

Also binbash had a good suggestion about disabling the splash screen. 

Edit this file.

/boot/grub/menu.lst

At the end of your kernel line you will see 

```
kernel ... ro quiet splash
```

change to 

```
kernel ... ro quiet #splash
```

then reboot,  you will now see what is stalling on startup.

---

### Post by philinux on 2008-11-24
> **Friccy said:**
> Hi!
I have just installed Intrepid after Hardy. I have made a clean install, formating the partition.
But, after GRUB and choosing Ubuntu, nothing happens, just a black screen.
If I press a key (any) and keep pressing it, Intrepid loads.
Can any of you help me with a cure for this?
Thanks!

What are your pc scpecs? It can be hardware related.

---

### Post by Friccy on 2008-11-24
> **philinux said:**
> What are your pc scpecs? It can be hardware related.

It's a brand new HP Pavilion, AMD Turion 64X2, Nvidia graphics and 2 Gb Memory.

---

### Post by Friccy on 2008-11-24
> **__Ryan__ said:**
> Open a terminal and enter 

```
dmesg | less
```

Also binbash had a good suggestion about disabling the splash screen. 

Edit this file.

/boot/grub/menu.lst

At the end of your kernel line you will see 

```
kernel ... ro quiet splash
```

change to 

```
kernel ... ro quiet #splash
```

then reboot,  you will now see what is stalling on startup.

I have tried dmesg | less and still nothing. It keeps freezing at the boot. 
On other hand Text editor didn't allowed me to save the changes in the /boot/grub/menu.lst list. Is there any other way to edit and save it?

---

### Post by philinux on 2008-11-24
There was this bug
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/175227](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/175227)
That got fixed in Hardy.

Looks like it's a regression with intrepid. There are a couple of things to try within the bug report. 

I'd raise a new bug with your specific hardware. When it asks for a package that the bug is in use "linux" as it's a kernel related bug.

---

### Post by Archmage on 2008-11-24
> **Friccy said:**
> On other hand Text editor didn't allowed me to save the changes in the /boot/grub/menu.lst list. Is there any other way to edit and save it?

ALT+F2
```
gsudo gedit /boot/grub/menu.lst
```

---

### Post by Friccy on 2008-11-24
> **philinux said:**
> There was this bug
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/175227](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/175227)
That got fixed in Hardy.

Looks like it's a regression with intrepid. There are a couple of things to try within the bug report. 

I'd raise a new bug with your specific hardware. When it asks for a package that the bug is in use "linux" as it's a kernel related bug.

Hello!
It is the same problem like that topic said.
I will try to install again the Hardy and upgrade from it. I did it on my old desktop and runs perfectly.
If you have any other suggestion, please let me know.

---

### Post by walkerk on 2008-11-24
> **Friccy said:**
> Hello!
It is the same problem like that topic said.
I will try to install again the Hardy and upgrade from it. I did it on my old desktop and runs perfectly.
If you have any other suggestion, please let me know.

If you add the [ acpi=noirq ] parameter your system will boot. I have an HP and this is the relevant section of my grub menu.lst. Take not of the highlighted area.
```
sudo gedit /boot/grub/menu.lst
```
```

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1267e03e-41c4-42e0-8b60-e6cb32b98ba7 ro quiet splash acpi=noirq
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1267e03e-41c4-42e0-8b60-e6cb32b98ba7 ro single [COLOR="DarkOrange"]***acpi=noirq***[/COLOR]
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		2.6.27-7-generic Backup
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1267e03e-41c4-42e0-8b60-e6cb32b98ba7 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Friccy on 2008-11-24
I will try it!
You mean "take note on the ..." or be carefull and do not do the highlighted area?

---

### Post by walkerk on 2008-11-24
> **Friccy said:**
> I will try it!
You mean "take note on the ..." or be carefull and do not do the highlighted area?

Add it to your file. It should allow your kernel to boot w/out holding a key down. If not open that file back up and remove it. No harm.

---

### Post by tallquasimodo on 2008-11-24
I had the same problem and fixed it on the advice of a previous thread, but I seem to be having some issues from the lack of IRQ support. I'm on an HAP Pavillion too, and since my sound card burned out I've been running my headphones through a cheap USB headphone port.  Acpi=noirq makes it boot easily, but in combination with the new sound device my system won't allow sound through dosbox or virtualbox OSE, though sound and video playback work fine.

---

### Post by Friccy on 2008-11-25
You have pasted Acqi=noirq in both rows?
I am asking you because I have pasted it in both rows and after reboot, Ubuntu was working on low resolution.
I had to reinstall again to get back.

---

### Post by Friccy on 2008-11-25
> **walkerk said:**
> If you add the [ acpi=noirq ] parameter your system will boot. I have an HP and this is the relevant section of my grub menu.lst. Take not of the highlighted area.
```
sudo gedit /boot/grub/menu.lst
```
```

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1267e03e-41c4-42e0-8b60-e6cb32b98ba7 ro quiet splash acpi=noirq
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1267e03e-41c4-42e0-8b60-e6cb32b98ba7 ro single [COLOR="DarkOrange"]***acpi=noirq***[/COLOR]
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		2.6.27-7-generic Backup
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1267e03e-41c4-42e0-8b60-e6cb32b98ba7 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Too bad that it's not working on my laptop!
I have tried it and after a quick boot it turns into safe graphics mode.
Almost nothing can be seen afterwards.

---

### Post by Friccy on 2008-11-29
Something interesting happens now!
It stars booting but on half way it freezes.
When I shut down the system, it almost shuts down and when is almost at the end, freezes.
Everything resumes if I hit a key.
Is it a bug?
Shall I report it?
Can anybody help me?

---

### Post by Friccy on 2008-12-03
Please help me!
I am desperate! Ubuntu still don't want to start without pressing a key and I don't want to reinstall the old version. I have lots of programs already installed and don't want to loose them with formating the partition!
Thanks!

---

