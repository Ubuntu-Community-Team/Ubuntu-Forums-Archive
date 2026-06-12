---
title: "boot crash, the fix acpi=off turns off battery stats and suspend features."
date: 2009-12-28
forum: Hardware
---

### Post by sarthorks on 2009-12-28
Hello

I am running Hardy on my Lenovo laptop. When i turn my computer ON, when the splash screen comes, there is usually a sudden outburst of fan speed, and then the computer powers OFF. I have to keep repeating this to finally get my laptop to boot. 
Also, if i keep my laptop on SUSPEND for a long time, like more than an hour, when i open the lid, there is this CPU fan activity and the computer powers OFF suddenly.

After some searching, I came across this fix, where if i turn my acpi=off in /boot/grub/menu.lst, i can boot normally.

Here is my original /boot/grub/menu.lst
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
#splashimage=(hd0,1)/boot/grub/splashimages/celtics.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=vga=792 quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

And here is it AFTER i've added acpi=off,

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
#splashimage=(hd0,1)/boot/grub/splashimages/celtics.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=vga=792 quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash acpi=off
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```


I need help in:
a) Since turning acpi off turn off my battery stats as well as SUSPEND abilities, can someone tell me of some other fix for my booting woes?
b)If there is no other fix than acpi=off, can someone tell me a way to get both battery stats as well as suspend feature back with acpi still off?

---

### Post by sarthorks on 2009-12-28
bump. nobody??

---

### Post by sarthorks on 2009-12-28
I tried this from [SuspendHowTo]("https://help.ubuntu.com/community/SuspendHowto")

```

To enable APM on a system:

    * edit your /etc/modules file and add apm to the list of modules.
    * edit the defoptions line of your /boot/grub/menu.lst file so that it ends with acpi=off, and then sudo update-grub to update the GRUB configuration.
    * Add the modules shpchp and pciehp to the end of the /etc/modprobe.d/blacklist file (they don't work w/APM).
    * Finally, reboot the computer. If your system supports APM, everything should be set up. 

```

But I don't have the battery-stats yet, and I will check after submitting this post if the computer still hangs on pressing the power button or not. Besides, typing 
```

apm

```
on the terminal still gives this error:
```

No APM support in kernel

```
Why is that? Heven't I enabled apm?

---

### Post by sarthorks on 2009-12-28
No luck, no suspend feature yet. 

I added apm=on at the end of
```

root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash acpi=off

```
in menu.lst,

but still **no** signs of improvement *at all*.

Still no one? What is wrong? Nobody knows how to deal with this? I'm quite new to linux, and I don't know what to do.

---

### Post by sarthorks on 2009-12-28
C'mon guys is there *nothing* that can be done?

---

### Post by sarthorks on 2009-12-29
I can't believe no-one's helping.

---

### Post by sarthorks on 2009-12-30
Although battery-stats are disabled with acpi=off, the physical BATTERY LED on my laptop is still functional: when the battery is full, it is yellow in colour, and when the battery crosses a certain stage, the colour changes to red, and as the battery discharges more, it starts blinking more and more often. 

If acpi is off, how is this battery indicator working? Is it not controlled by acpi?

Also, when i was booting (with lots of difficulty as the system would power off at booting again and again) with acpi NOT off, using lmsensors, the core-temperature would be around 45 degrees celsius, once i had used the computer for a while, and would stay there. With acpi=off, the core-temperatures are around 31 deg. C all the time. Does that mean that my acpi wasn't working properly?

---

### Post by sarthorks on 2009-12-30
OKAY, so i made acpi=force in
```

/boot/vmlinuz-2.6.24-26-generic root=UUID=d1714898-11b7-4830-9a54-142371e9a82b ro vga=792 quiet splash acpi=force

```

Now it is booting properly, but using lmsensors, the coretemperature has crossed all previous limits i had seen before and it is at around 50 deg. Celsius. I hope thats not a cause for worry.

---

### Post by sarthorks on 2009-12-30
Oh no, its still NOT booting properly. Same old problem, without acpi=off and with acpi=force, but this was expected.

I really dont know what to do, cant anyone help?

---

### Post by sarthorks on 2009-12-31
All right this seems to be a reasonable fix:

In my /var/kern.log, when i boot, i get a message which asks me to check if booting with acpi_osi=Linux works better or not.

Well, i tried that, so that the end of the grub line read
```

 ro vga=792 quiet splash acpi_osi=Linux

```
.
Now, it gives me a problem sometimes only if I have suspended my laptop for like 1-2 hrs. Then the laptop powers off on resume. And then it will cause a lot of trouble in booting, as menitoned in the earlier posts.

Thats still troubling me. Otherwise, booting is fine, andd suspends less than an hour are also fine. I'm still waiting for someone to shed some light.
Anyone?

---

### Post by mabonvin on 2010-01-20
Nice monologue :popcorn:. Is someone purposely deleting all replies? ;)

---

### Post by amillionsheep on 2010-01-28
I just want to say I was experiencing something similar to this with my Acer AspireOne D250.
 
I left it idle (plugged in) all night and when I checked it in the morning it was off. I have it set to never suspend/hibernate while plugged in.
 
I it on and it imediately turned back off. The only way I could get it to come back on was to remove the battery, boot without battery, shutdown, put battery back in, and boot with both battery and charger connected. Also, I have found that regardless of my power settings the computer still loses netaccess/suspends or whatever after 5+ minutes of idle on ac power.
 
What could have caused this?

---

### Post by sarthorks on 2010-02-02
mabonvin : no, no one else was posting.

---

### Post by sarthorks on 2010-02-02
> **amillionsheep said:**
> I just want to say I was experiencing something similar to this with my Acer AspireOne D250.
 
I left it idle (plugged in) all night and when I checked it in the morning it was off. I have it set to never suspend/hibernate while plugged in.
 
I it on and it imediately turned back off. The only way I could get it to come back on was to remove the battery, boot without battery, shutdown, put battery back in, and boot with both battery and charger connected. Also, I have found that regardless of my power settings the computer still loses netaccess/suspends or whatever after 5+ minutes of idle on ac power.
 
What could have caused this?
try with acpi=off in your grub, as explained in the earlier posts. Or read your kernel.log carefully for any error messages, around the time when your computer acted weirdly.

---

### Post by sarthorks on 2010-02-04
Okay, so here's the latest on my acpi woes - after weeks of testing, i have some lead into the issues, although i need help from you all.

I boot with ```
acpi_osi=Linux
``` in /boot/grub/menu.lst.

Restarting the laptop, or resuming from hibernation or suspend all work fine, as long as it has not been like almost half-a-day since the laptop was on and working. If it has been like a long time since i used my computer, at the splash screen loading, the fan shows a sudden outburst of activity and then the computer powers off suddenly, if i'm resuming from a hibernation and if i'm just resuming from suspend to memory, the computer just goes off, after i hear a sudden fan outburst. This happens a second time as well, and only at the third power on does the splash screen goes through (no fan outburst this time) and i can log in. 
The same is the issue when I'm using a LiveUSB booting (into karmic).

If however, at the start I press ESC at the grub menu option, and select MemTest86, and run it till at least like half-way through the second test, there is no fan issue at the splash screen once I have canceled the memtest at the 2nd test (by pressing ESC), regardless of when did i last turn my laptop on.

I'm really clueless what exactly is running a memtest86 for a few seconds doing to my laptop which is overcoming the problems i'm facing while doing a "cold" powering on, after like 12 hours.

I have checked the core temperatures using lmsensors, and they go maximum upto around 46 deg C if i've been using my laptop for quite some time, and right after powering on my laptop after a long time shutdown or suspend, (when i am able to boot in after the inevitable power off), the temperatures are around 10-16 deg C.

Can anyone help me diagnose my problem? I will be happy to paste all the necessary outputs.

Thanks in advance.

---

### Post by sarthorks on 2010-02-04
> **sarthorks said:**
> 

If however, at the start I press ESC at the grub menu option, and select MemTest86, and run it till at least like half-way through the second test, there is no fan issue at the splash screen once I have canceled the memtest at the 2nd test (by pressing ESC), regardless of when did i last turn my laptop on.

I'm really clueless what exactly is running a memtest86 for a few seconds doing to my laptop which is overcoming the problems i'm facing while doing a "cold" powering on, after like 12 hours.

I have checked the core temperatures using lmsensors, and they go maximum upto around 46 deg C if i've been using my laptop for quite some time, and right after powering on my laptop after a long time shutdown or suspend, (when i am able to boot in after the inevitable power off), the temperatures are around 10-16 deg C.


Well, i actually noticed that whenever I ran memtest86 at the start for a few seconds (till halfway through the second test), my core-temperatures (using lmsensors) were shooting up and reaching the critical value of 85deg C once i had logged in, and pretty soon. Does that mean that running memtest86 turned off the fans, and as with acpi=off, it sort of gave me a "temporary" relief and allowed me to boot in (although it was obviously at the cost of critical core-temperature values in no time)?

So it definitely points to an issue with the fan. 
I have two questions: 
1)why is running memtest86 for a few seconds before booting switching off my fan?
2)why is switching off my fan allowing me to boot in at the first attempt?
3)why does a power on after a long time cause shut-off at the splash screen a couple of times? (and why do i hear all the sudden outburst of fan, which i don't hear when the boot goes through succesfully to the login screen?) - however, A POINT TO BE NOTED : after my core-temperatures had shot up to 82deg C thanks to memtest86, i RESTARTed my laptop, and now, again from the BIOS screen onwards, and even through the splash screen loading, i heard a loud fan (quite possibly cooling off the system) and no doubt, at start-up, lmsensors showed a 46deg C. (Normally, on powering on, there is only a very little fan burst, and obviously whenever the splash screen "drama" unfolds, there is that OUTBURST of fan at the splash loading.)
Incidently my /proc/acpi/fan folder is empty. However, all this had never been an issue for like the last one and a half-years.

---

### Post by schulwitz on 2012-06-24
For those who have the same problem (i.e. no battery meter or shutdown ability when acpi=off) here's a solution.

Edit your Grub 2 linux boot script from terminal:
> sudo gedit /etc/grub.d/10_linux

Find the line that reads:
```
GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT"
```
and make it
```
GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT pci=noacpi"
```

Save changes and exit.
Then update your grub.cfg file by typing:
> sudo update-grub2
then
> sudo reboot

If setting "pci=noacpi" didn't work, try the other ACPI boot options specified at [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI).

---

### Post by overdrank on 2012-06-24
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

