---
title: "cannot install wubi pacakage on samsung q45"
date: 2008-10-30
forum: General Help
---

### Post by br3athe on 2008-10-30
i have tried to install wubi xubuntu and kde on my samsung q45 
i download all the packages and it reboots but hangs a certain way through booting up again 
does anyone have any suggestions , xubuntu is coming up in the boot menu , but again it hangs when booting , anyone been able to successgully install a wubi package on samsung q45 ?
( i do not want to do a 'proper' install at the moment ... 
thanks

---

### Post by ago on 2008-10-30
I have the same machine...

1) Press esc at boot after Ubuntu
2) Select the ACPI option
3) Press "E" to edit that option
4) Press "E" to edit the line that starts with "kernel "
5) Delete "noapic nolapic" (but leave acpi=off)
6) Press enter and then "B" boot

Now it should install. Once installed boot into ubuntu then cut and paste the following in a terminal

echo "blacklist video" | sudo tee -a /etc/modprobe/samsung-q45
sudo -i sed s:acpi=off:: /boot/grub/menu.lst

---

### Post by br3athe on 2008-11-02
hi 
thanks 
I got ubuntu installed
however when I pu this into a terminal

echo "blacklist video" | sudo tee -a /etc/modprobe/samsung-q45
sudo -i sed s:acpi=off:: /boot/grub/menu.lst

I get /etc/modprobe/samsung-q45: No such file or directory 


looking at the folders there is modprobe.d
so i modified to this folder name 
then the next linne -i sed... 
i get :/bin/sed : cannot execute binary file 

do you have any ideas ? thanks for your help , appreciated

---

### Post by br3athe on 2008-11-02
by the way , I ended up installing ubuntu 8.10 , what do you have on your q45 , I dont mind starting again and going with the distro that you have working or recommend , thanks

---

### Post by ago on 2008-11-03
Sorry, my bad


echo "blacklist video" | sudo tee -a /etc/modprobe**.d**/samsung-q45
sudo sed **-i** s:acpi=off:: /boot/grub/menu.lst

---

