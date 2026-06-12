---
title: "Toshiba l300 fan is running constantly"
date: 2009-11-03
forum: Hardware
---

### Post by daleharvey on 2009-11-03
When I startup my laptop the fan is silent, however after around 10 minutes of use it turns on full and never stops

```
dale@dale-laptop:~/$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +38.0°C  (crit = +105.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +32.0°C                                    
Core0 Temp:  +31.0°C                                    
Core1 Temp:  +33.0°C                                    
Core1 Temp:  +30.0°C
```

I have tried putting 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\"" 
```

in /etc/default/grub (I have also tried every variant of quote)

and also tried the trick with 
```
dale@dale-laptop:~/$ echo "on" > sudo tee /proc/acpi/fan/FAN1/state
dale@dale-laptop:~/$ echo 3 > sudo tee /proc/acpi/fan/FAN1/state 
```

neither of which are working for me, this is a fresh install of 9.10

any ideas? worth mentioning my fan is now spitting out particularly cool air, cheers
Dale

---

### Post by hugohami on 2009-11-04
Hi,

I had the same problem on Toshiba L300 1B8 and this solved it for me:
[http://www.symbiosoft.net/?q=node/66](http://www.symbiosoft.net/?q=node/66)

Good luck.

---

### Post by daleharvey on 2009-11-05
as I mentioned I tried that (along with every variant of quotes that I could think of)

my current default looks like

```
dale@dale-laptop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

```

which generates this grub.cfg (I havent been forgetting to run update-grub)

```
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set d82c4471-133c-4f0f-8bea-d2bd2dd4591f
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=d82c4471-133c-4f0f-8bea-d2bd2dd4591f ro   quiet splash acpi_osi=Linux
        initrd  /boot/initrd.img-2.6.31-14-generic
}
```

but still the same problem

---

