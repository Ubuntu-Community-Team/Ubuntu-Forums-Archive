---
title: "Almost installed; however, ..."
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by billy_deckert on 2009-02-21
Greetings, I have just recently decided to join the open source Linux community for a number of reason that I will go into later and in the propper form.

I have acquired two partail machines and other assorted parts on Freecycle, and I have managed to find enough for one full machine.
I have download and burned a 8.10 cd and have partitioned and installed ubuntu, almost...

During the boot up from the cd to run the live cd I had to adjust the boot settings. I played around and found that using the "noapci" setting allowed me to boot up and get ubuntu installed. On the boot up help page it said that if you have to adjust the boot settings that after installation you would have to edit a file called /boot/grub/menu.lst and here lies the problem. I don't see that file. I have found example files, but I am not sure if those files are showing commented out examples and I am not fully sure of the formate of the menu.lst file.

I hope that someone else has had and resolved this problem, or has the knowledge assist me.

Thanks in advance,

Billy

---

### Post by Partyboi2 on 2009-02-21
Open a terminal (Applications>Accessories>Terminal) and type
```
gksu gedit /boot/grub/menu.lst
``` This should open your menu.lst where you make the changes to.
Then look for this section:
> ## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro

and add noapci to the end of 
```
# kopt=root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro
```
so it would look like
```
# kopt=root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro [COLOR=Red]noapci[/COLOR]
```
and save the changes. Then back in the terminal
```
sudo update-grub
```

---

### Post by billy_deckert on 2009-02-21
I am closer.
I found the line you mentioned; however the editer will not let me save. I beleave this is because I booted with the cd, applied the noapci , and used try with out changing option.
The file seems to be owned by root and I am logged in as ubuntu and I am having trouble figuring out howto log in as root to edit the file

If I do not use the cd I end up not getting to the gui to load and I am at a ash prompt with a very limited command set

---

### Post by Partyboi2 on 2009-02-22
Don't boot the live cd, instead boot into your installation, boot the machine and when you see something like "grub loading..." press "Esc" this will take you to the grub menu, then press "e" to edit then highlight the line starting with "kernel" and press "e" again then at the end of the line add noapci and press "enter" then finally "b" to boot. This should boot into your installation and get you to the Desktop where you can follow what I posted previously to make the boot option permanent.

---

### Post by billy_deckert on 2009-02-22
I have tried a few variation of what you have instructed and I seem to have a different issue. Here is how my booting seems to go:

<power on>

checks the primary cpu (pentum III), and notices the second cpu
memory check
checks for primary IDE
Finds the primary hard drive

<screen blanks>

Boor from (hd0,0) ext3   75073484-30cb-424c-8353-40a80591082d
Starting up ...
[    2.334724] irq 9: nobody cared (try booting with "irqpoll" option)
[    2.335100] handlers:
[    2.335147] [<c0277448>] (acpi_irq+0x0/0x28)
[    2.335289] Diabling IRQ #9
Loading, please wait...

<screen blanks>
<Ubuntu loading screen with bar sweeping back and forth>
<screen blanks>

Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system waith long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/75073484-30cb-424c-8353-40a80591082d does not exist. Dropping to shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for list of built-in commmands.

(initramfs) 



a few more observation that may assist you in helping me:

When I boot with the CD the "/boot/grub/menu.lst" file I find has a full path of "/media/disk/boot/grub/menu.lst"


Thank you for your help. I has been a while since I have done a fresh install and set up, and it was with dos or windows 98.

---

### Post by Partyboi2 on 2009-02-22
Just after it says
> Finds the primary hard drive You should be able to press ESC a few time to get to the grub menu screen (See screenshot below)

Another way you could probably make the changes is by booting the Live cd and make the changes to /media/boot/grub/menu.lst. 
[FONT=monospace]
[/FONT]```
gksu gedit /media/boot/grub/menu.lst
```and make the changes. I would also suggest adding rootdelay=120 as well to see if you get past the>  ALERT! /dev/disk/by-uuid/75073484-30cb-424c-8353-40a80591082d does not exist. Dropping to shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for list of built-in commmands. So the section in /media/grub/menu.lst should look something like
```
## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro [COLOR=Red]noapci rootdelay=120[/COLOR]
```

---

### Post by billy_deckert on 2009-02-23
Got it!!!!

My first break through was in realizing that I was mis-typing/mis-spelling the flag I needed to use.
I was trying to use noapci and I needed noapic

with that in hand I was able to use the "esc" at the grub loading stage. With the correct flag I was able to boot all the way. Then with a bit of poking around I was then able to follow your first reply and edit the file (with the correct flag).

I restarted the machine and booted completely.


I appreciate your help and your willingness to bare with my, for a lack of a better word, noobness. :p

---

### Post by Partyboi2 on 2009-02-24
Happy to help, good to see you solved it. :)

---

