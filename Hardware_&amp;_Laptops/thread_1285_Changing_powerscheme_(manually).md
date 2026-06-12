---
title: "Changing powerscheme (manually)"
date: 2004-10-19
forum: Hardware &amp; Laptops
---

### Post by knappen on 2004-10-19
I have installed Ubuntu on my laptop and loving it. However, my fan goes wild and the laptop gets really hot. On Mandrake, Suse etc, you can manually select what powerscheme to run when you are using the battery or using external power.

What I want to do is to have it set to powersave all the time. I will never use the performance scheme.

Anyone got a clue?

Greetings from down under!  :roll:

---

### Post by Yellowlawnchair on 2004-10-20
what kind of laptop?  I've got a gateway solo 1400 and it does the same thing.

---

### Post by knappen on 2004-10-20
It is an ARIMA W720-K7.

AMD XP2600
512MB
IPW2200 54g mini pci wireless 
15.4" widescreen

---

### Post by knappen on 2004-10-20
I have looked everywhere.

I am lost...

---

### Post by knappen on 2004-10-21
I hope that powermanagement will be better in the final release. Now I get about 30 minutes out of my battery, previously I got more than 2 hours.

---

### Post by knappen on 2004-10-22
Please, does anyone know how to change the settings so that my CPU automatically throttles down when not working?

---

### Post by Rancoras on 2004-10-22
I don't know much about ACPI, but a quick google yileded this page.  See if you can adapt anything in there to ubuntu.

[http://danplanet.com/acpi_scripts/](http://danplanet.com/acpi_scripts/)

---

### Post by knappen on 2004-10-22
Thanks for the link.

The weird thing is that in /proc/acpi/processor/CPU0/throttling it says that it is not supported. But AMD Mobile +2600 does support throttling.

Is this something that I can change manually?

---

### Post by Warnez on 2005-02-10
Hi! 

I think, that I've been havin' kinda the same problem.... You should try to update your CPU driver, to the AMD K7 PowerNow. There's also a "CPU Frequency Tool" you can try - works for me.. All of this and more you can find at : [http://www.e4allinc.info/dir1/motherboards/laptops/arima_W720_K7_downloads.htm](http://www.e4allinc.info/dir1/motherboards/laptops/arima_W720_K7_downloads.htm)

Do you have any links or what-so-ever 'bout Arima W720-K7 Mobo? I've haven't got any details when I bought it.. 

Good luck.. Warnez  :wink:

---

### Post by laue on 2005-05-06
hi, i have an amd xp-m, and i had the same problem when i installed ubuntu. I had frequency scaling working in gentoo, but when migrating to ubuntu cpufreq failed. 

I compared the ubuntu kernel with the kernel i had compiled in gentoo and came to the belief that the amd powernow and all the other acpi drivers should not be loaded as a module, but should be compiled into the kernel. 

Anyway it worked for me, so here's a (brief) howto if you've never compiled a kernel:

1. use synaptic to download the kernel sources (i use linux-source-2.6.11, but 2.6.10 should do fine as well)
These sources will be installed in /usr/src/linux-source-2.6.11.
If not already done, you should make a symlink called 'linux' to afore mentioned directory
=> ```
cd /usr/src
      sudo rm ./linux
      sudo ln -s ./linux-source-2.6.11 ./linux
      cd linux
```
      
2. now we are in the source directory of the kernel, where we can start building your new kernel.
=> sudo make menuconfig

3. You will either see a bleu environment (called ncurses), or the console will tell you to install a few additional packages (forgot which ones). If so, install them using synaptic and issue 'sudo make menuconfig' again.

4. Go to: Power management options (ACPI, APM) -> ACPI (Advanced 
                 Configuration and Power Interface) Support 
    Go to the 'processor' option and use spacebar to replace the <M> with <*>.     
    This will ensure the driver will be compiled into the kernel <*> instead of as a 
    module <M>

5. Go to: Power management options (ACPI, APM) -> CPU Frequency scaling
    - Make sure you enable 'AMD Mobile Athlon/Duron PowerNow!' and nothing else
    - replace all <M> with <*>
    - use userspace as the default governor

6. exit menuconfig, saving your configuration to the default location

7. Compile your kernel and modules, and install the modules:
    ```
make && make modules_install
```

8. Put the kernel into your /boot directory:
    ```

    sudo cp arch/i386/boot/bzImage /boot/kernel-2.6.11
    sudo cp .config /boot/config-2.6.11
    sudo cp System.map /boot/System.map-2.6.11
    
```

9. Change your grub menu so you can actually choose to use this kernel at boot       
    time
    [code]sudo gedit /boot/grub/menu.lst[code]
    In the bottom, you will find the entries for the older kernels. Copy one of them (_copy_, don't remove, so you can still boot your old kernels if something has gone wrong)

---

### Post by laue on 2005-05-06
hi, i have an amd xp-m, and i had the same problem when i installed ubuntu. I had frequency scaling working in gentoo, but when migrating to ubuntu cpufreq failed. 

When booting linux, it is stated with exclamationmarks that the amd xp 2000+ does _not_ support power support. I find it very disturbing as it might discourage people from using amd or ubuntu. 

I compared the ubuntu kernel with the kernel i had compiled in gentoo and came to the belief that the amd powernow and all the other acpi drivers should not be loaded as a module, but should be compiled into the kernel. 

Anyway it worked for me, so here's a (brief) howto if you've never compiled a kernel:

1. use synaptic to download the kernel sources (i use linux-source-2.6.11, but 2.6.10 should do fine as well)
These sources will be installed in /usr/src/linux-source-2.6.11.
If not already done, you should make a symlink called 'linux' to afore mentioned directory
=> ```
cd /usr/src
sudo rm ./linux
sudo ln -s ./linux-source-2.6.11 ./linux
cd linux
```
      
2. now we are in the source directory of the kernel, where we can start building your new kernel.
=> ```
sudo make menuconfig
```

3. You will either see a bleu environment (called ncurses), or the console will tell you to install a few additional packages (forgot which ones). If so, install them using synaptic and issue 'sudo make menuconfig' again.

4. Go to: Power management options (ACPI, APM) -> ACPI (Advanced 
                 Configuration and Power Interface) Support 
    Go to the 'processor' option and use spacebar to replace the <M> with <*>.     
    This will ensure the driver will be compiled into the kernel <*> instead of as a 
    module <M>

5. Go to: Power management options (ACPI, APM) -> CPU Frequency scaling
    - Make sure you enable 'AMD Mobile Athlon/Duron PowerNow!' and nothing else
    - replace all <M> with <*>
    - use userspace as the default governor

6. exit menuconfig, saving your configuration to the default location

7. Compile your kernel and modules, and install the modules:
    ```
make && make modules_install
```

8. Put the kernel into your /boot directory:
    ```
sudo cp arch/i386/boot/bzImage /boot/kernel-2.6.11
sudo cp .config /boot/config-2.6.11
sudo cp System.map /boot/System.map-2.6.11

```

9. Change your grub menu so you can actually choose to use this kernel at boot       
    time
    ```
sudo gedit /boot/grub/menu.lst
```
    In the bottom, you will find the entries for the older kernels. Copy one of them 
    (_copy_, don't remove, so you can still boot your old kernels if something has 
    gone wrong)
    Change the kernel entry to the new kernel path (as shown in red)
    Change the tiltle entry to whatever you would like to be displayed in the grub     
         menu at boot time (as shown in blue)
    example:
   
 copy and alter:```

title          [COLOR=Navy] Ubuntu, kernel 2.6.10-5-386[/COLOR]
root            (hd0,3)
kernel          [COLOR=Red]/boot/vmlinuz-2.6.10-5-386[/COLOR] root=/dev/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot
```

to: ```

title           [COLOR=Navy]Ubuntu, kernel 2.6.11-k7[/COLOR]
root            (hd0,3)
kernel          [COLOR=Red]/boot/kernel-2.6.11[/COLOR] root=/dev/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

```

Good luck!!!

Disclaimer: I do not garantee that the previous howto will work for you, nor that it is free of errors!

PS: Please add comments and corrections

---

