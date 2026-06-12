---
title: "Asus laptop TP300L Brightness keys backlight grub acpi 14.04 configuration"
date: 2014-11-20
forum: Hardware
---

### Post by tximikel on 2014-11-20
Hi Linux community! i solved a problem with my laptop brightness keys in Ubuntu 14.04, a share you my solution ;)

1) First i've followed steps detailed [in this article]("http://itsfoss.com/fix-brightness-ubuntu-1310/")

[LIST]
[*]Then i've reboot the system but keys don't run :( 
[/LIST]

2) Following i've edited grub configuration file:
[LIST]
[*]Edit grub configuration file
[LIST]
[*]sudo gedit /etc/default/grub 
[/LIST]
  
[*]Change the original line and update content adding new options
[LIST]
[*]Original line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
[*]New options: acpi_osi= acpi_backlight=intel 
[*]Updated line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= acpi_backlight=intel" 
[/LIST]
  
[*]Update the grub configuration
[LIST]
[*]sudo update-grub
[/LIST]
  
[*]Reboot and then the brightness keys Fn+F5 and Fn+F6 run ok :) 
[/LIST]

3) Following a set of useful commands to check that backlight keys are running fine/bad:
[LIST]
[*]Check the backlight interfaces and their setting values
[LIST]
[*]Command: for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; done 
[*]Output: /sys/class/backlight/acpi_video0
5
10
/sys/class/backlight/intel_backlight
391
937 
[/LIST]
  
[*]Check that keys are listen by acpi
[LIST]
[*]Command: acpi_listen
[LIST]
[*]Pressing Fn + F5 (darker) 
[*]Output: video/brightnessdown BRTDN 00000087 00000000 K
 PNP0C14:00 000000ff 00000000 
[*]Pressing Fn + F6 (lighter) 
[*]Output:  PNP0C14:00 000000ff 00000000
video/brightnessup BRTUP 00000086 00000000 K 
[*]Pressing Fn + F2 (disable/enable wifi) 
[*]Output: button/wlan WLAN 00000080 00000000 K
 PNP0C14:00 000000ff 00000000 
[/LIST]
    
[/LIST]
  
[*]See backlight in Xorg window system log
[LIST]
[*]cat /var/log/Xorg.0.log | grep backlight
[LIST]
[*]Output: [    18.039] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=e9cf65c8-867f-4bf4-9c2d-a3ed64760b01 ro quiet splash acpi_osi= acpi_backlight=intel vt.handoff=7
[    18.637] (**) intel(0): Option "Backlight" "intel_backlight"
[    18.637] (**) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1 
[/LIST]
    
[/LIST]
  
[*]Install and use xbacklight command
[LIST]
[*]sudo apt-get install xbacklight 
[*]See current setting value:
[LIST]
[*]Command: xbacklight 
[*]Output: 41.72892 
[/LIST]
  
[*]Set lighter
[LIST]
[*]Command: xbacklight +25 
[/LIST]
  
[*]Set darker
[LIST]
[*]Command: xbacklight -25 
[/LIST]
    
[/LIST]
    
[/LIST]

I hope i help you solving the problem :) 
happy sharing!

---

