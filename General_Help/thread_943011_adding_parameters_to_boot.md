---
title: "adding parameters to boot"
date: 2008-10-09
forum: General Help
---

### Post by nld2756 on 2008-10-09
hello, im a new linux user, ive have been using windows for a very long time and im very experianced with computers. In order for hardy heron to recognize my satas, i put the acpi=off noapic udev cdroot dodmraid in the boot parameters before i installed. After the install, i cant get back into my operating system even after troubleshooting numerous methods. I feel that this is caused by my bootup not recognizing my hardrives although i am not sure. As i said before im new and i dont know a lot about how linux works so i was asking where i go to edit the boot parameters in my bootup config so whenever i install, it will recognize my satas.

thanks for reading :D

---

### Post by spiderbatdad on 2008-10-09
/boot/grub/menu.lst

In this section:
```
## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=##'s ro **quiet splash **
initrd		/boot/initrd.img-2.6.27-6-generic
quiet

```at the end of the line beginning with the word "kernel." Generally, delete quiet splash, and replace with your boot options. I recommend reading the entire file to become familiar with its workings. Some people recommend setting your option in the kopt section. I have not had the same results, so i always use the kernel line in the debian automagic kernels section.
To edit the file:
```
sudo nano /boot/grub/menu.lst
```or ```
gksu gedit /boot/grub/menu.lst
```

SATA is often configured as ide with the parameter: all_generic_ide

---

### Post by nld2756 on 2008-10-09
this doesnt work because i have to restart to have access to have permission to change that file and everytime i restart, i cant even get back into ubuntu...

id just like to state that im not completely sure if i cant get in because of my hardrives.  whenever i load up ubuntu normally it goes threw the loading screen then goes to busy box, stops processings, and just sits there, same after loading from recovery mode. ive been trouble shooting differen ubuntu versions for a good 12 hours

---

### Post by nld2756 on 2008-10-09
edit

---

### Post by spiderbatdad on 2008-10-10
you can edit the kernel (for a one-time-only-boot) from the grub menu. Just highlight the kernel you want to boot with the up/down arrow key, press e, use the arrow key to move to the line that starts with the word kernel, press e again, go to the end of the line, delete quiet splash, replace with all_generic_ide (or whatever you want), hit enter, and press b

The symptom you described above is commonly caused by hard drive configuration error.

---

### Post by nld2756 on 2008-10-10
How do i get that boot parameter to stay? after changing it in the grub menu, it worked and i booted up fine. Even though, i still can change the menu.lst because of not having permission to change the file.

---

### Post by spiderbatdad on 2008-10-10
you must edit menu.lst as root...with the commands shown above...sudo nano, or gksu gedit.

---

### Post by nld2756 on 2008-10-10
thank you for all of your responses, it seems that im still a little lost about these fundemental commands and what each one stands for, are there any guides that i could go to that could help me out?

---

### Post by Sam on 2008-10-10
> **nld2756 said:**
> thank you for all of your responses, it seems that im still a little lost about these fundemental commands and what each one stands for, are there any guides that i could go to that could help me out?

[Ubuntu Cheat Sheet](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)
[Unix/Linux Command Cheat Sheet](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

---

