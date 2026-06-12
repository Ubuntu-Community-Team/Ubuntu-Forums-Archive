---
title: "Lenovo 3000 Y500 Touchpad not working"
date: 2010-10-20
forum: Hardware
---

### Post by asifsolkar on 2010-10-20
Hi Guys 

I recently installed Ubuntu 10.10 x86 , All the devices worked except my touchpad. 

I had this problem with earlier versions of ubuntu as well and the work around for that was put acpi=off in options.I did the same for ubuntu 10.10 but it did not work 

_Please note_ **acpi=off** option worked during installation , touchpad was working during installation , but after reboot it didn't work. I tried lots of options but didn't work. I am a windows user but i want to give ubuntu a serious try this time 

All you experts please help me detect my touchpad
touchpad company : Alps 

Thanks in advance

---

### Post by asifsolkar on 2010-10-26
Can any one help me out with this one please , stuck from quite long, Should i try any other distro ?

---

### Post by rubal on 2010-10-27
Hi

js edit your grub booting option by pressing 'e' at grub screen and add 'i8042.reset' at the end of line where u see 'quite splash'. Press ctrl+x to boot.

Your touchpad will be working and to make that change permanent 
open /etc/default/grub with text editor and add 'i8042.reset' with the line ending with 'quite splash'

save the file close the editor and open a terminal and run 

sudo update-grub

all that worked for me ...my keyboard and touchpad all working fine..tc.:P:P

---

### Post by asifsolkar on 2010-10-30
Rubal many thanks , it worked 


> **rubal said:**
> Hi

js edit your grub booting option by pressing 'e' at grub screen and add 'i8042.reset' at the end of line where u see 'quite splash'. Press ctrl+x to boot.

Your touchpad will be working and to make that change permanent 
open /etc/default/grub with text editor and add 'i8042.reset' with the line ending with 'quite splash'

save the file close the editor and open a terminal and run 

sudo update-grub

all that worked for me ...my keyboard and touchpad all working fine..tc.:P:P

---

### Post by udaychaitanya on 2011-01-23
thank you verymuch.you made my life happy.

---

### Post by JuJoJeZa on 2011-03-20
Hey guys
I am kinda new to the linux world running on my first ever Ubuntu 10.10 and it feels good :KS

I am trying to fix the same issue has you guys but have been googeling for hours now on how to js edit my grub file.

[INDENT]js edit your grub booting option by pressing 'e' at grub screen

[/INDENT]I am trying to open the file in vim but am unable to edit and have also donwloaded startup manager but no luck.

Could you please explain to me step-by-step how to get my Touchpad to work?

:D

---

### Post by San Manhas on 2011-04-13
yeah the "i8042.reset" trick worked well in ubuntu 9.10 but i tried it in 10.10 and it really disappointed me.
m using lenovo 3000 y500 and please someone help me out as my touchpad n keyboard both are not working.

---

### Post by Dishang on 2011-07-06
Plz hlp ....
Tell me in detail....
M having the same problem....!!!

---

### Post by jagdishdrblp on 2011-07-09
lenovo 3000 y 500 touchpad not working  please help
ubuntu latest version 11.04

---

### Post by lavankohsa on 2011-08-04
i am using only ubuntu in my laptop so there is no bootloader option my laptop. what should i do ??

---

### Post by montrealraaj on 2012-10-06
Hi All,
Thanks for all the the inputs the solution provided here definitely works.

For all the newbies like me, Here is the step by step procedure

1. Press cntrl+Alt+T

2.type "sudo gedit /etc/default/grub" (without quotes) and press enter.

3.When prompted for password Enter the admin password.

4 Add the line "i8042.reset" (with quotes) after the text "quiet splash"

After adding the the line in /etc/default/grub it should look like the following line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset"

5. Save the changes and close in order to return to the Terminal window.

6. type "sudo update-grub" (Without Quotes) and press enter.It should generate lines something like below

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-43-generic
Found initrd image: /boot/initrd.img-2.6.32-43-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

7. Restart Ubuntu.

Now the Touchpad and Keyboard should work after the restart.

Thanks and Regards,

Montrealraaj

---

