---
title: "How to install ubuntu on HP 6720s 1,6ghz intel centrino dual core laptop?"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by baruch90 on 2007-11-27
Hello.
I have tried to install ubuntu on my laptop, but when I boot on the live cd, the screen turns black and a bug tells me that my computer is softly protected...

Am I able to install ubuntu without any missings, if yes.. how?
I am a beginner in linux, so please explain it very simple if possible.

Sincerely
Baruch90

---

### Post by dixon on 2007-11-30
Give more specs about your laptop, because I've got 6720s(T5470, FreeDOS) and today I installed ubuntu - gutsy gibbon, without any problem....

EDIT: You can try this :) Enter the setup(BIOS) while booting and disable the use of Native SATA.

---

### Post by baruch90 on 2007-12-01
Never mind, I've downloaded gutsy, and it works fine...
Thanks for the help!

---

### Post by baruch90 on 2007-12-03
I have installet ubuntu, but the internet(wire) won't function as it did, when I ran the live cd. Ubuntu complains about the fact that the driver of the wirelesscard is restrictive. How did you connect to the internet after installing ubuntu?

---

### Post by dixon on 2007-12-04
There are some problems with ethernet connection on this laptop. There're two ways how to solve this
1) boot with parameter pci=noacpi
2) upgrade bios to version F.03 (windows is needed for this operation)

The second way is better, but you need windows....

About the wireless just enable the restricted driver....

---

### Post by baruch90 on 2007-12-07
How do I write the command pci=noacpi, so that it will be permanently activated after each reboot. I've tried to do it like this:
Entering the terminal
writing: gksudo gedit /boot/grub/menu.lst
Where after the file open and is completely empty. 
I add the sentence: pci=noacpi and save the changes.
Then I reboot and enter the desktop still without wired internet access?

Please explain me in details, how I should use the command pci=noacpi.

Why is it better to change the bios into F.03? I have found a file, which should be capable of changing the bios called sp36906.exe?

I do not have vista anymore, but I have Windows Me on a cd, if that's an option for the bios update? Can I update the bios with any windows distro or only with vista. I have vista as iso files, if that is necessary, but then I will have to use 10 empty cd's, to burn it down. 

Sincerely Baruch90

---

### Post by dixon on 2007-12-07
2) I think you can upgrade your bios from any Windows. I've upgraded the bios in WindowsXP.

1) /boot/grub/menu.lst can't be empty.
Somewhere at the bottom of the file you should have something like this
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1990f41b-6c99-4644-8c64-8230116a901f ro quiet splash locale=sk_SK pci=noacpi
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```The pci=noacpi comes to the end of the kernel line...

---

