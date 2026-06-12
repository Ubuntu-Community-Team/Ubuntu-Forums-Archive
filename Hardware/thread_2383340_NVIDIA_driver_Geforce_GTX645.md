---
title: "NVIDIA driver Geforce GTX645"
date: 2018-01-23
forum: Hardware
---

### Post by coby28 on 2018-01-23
Hello,

We're often playing the video game second life and we have just installed Ubuntu on the computer. Our video card is NVIDIA driver Geforce GTX645 but we're having difficulties to use it now :icon_frown:

When checking System setting, Settings -> Additional Drivers, we're are using X.org Xserver - nouveau display. 
We tried to change into the available options NVIDIA binary driver version 384.111 and legacy driver version 304.135 without result. The change is possible but after the pc reboot and entering our psw, the screen stays black when trying both options.

Is there maybe another way to solve this problem?

Thx

---

### Post by Bashing-om on 2018-01-23
coby28; Hello - Welcome to the forum .

Support depends on several factors .
what release is this
```

lsb_release -a

```
what kernel are you running :
```

uname -r

```
Did the driver load ?
```

sudo lshw -C display

```
Is there now a driver conflict ?
```

dpkg -l | grep -i nvidia*

```
What does the gpu-manager have to say about the matter :
```

cat /var/log/gpu-manager.log

```

Once these are known we can develop a course of possible action.

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by SeijiSensei on 2018-01-23
One common suggestion is to add "nomodeset" to the list of boot options.

When you see the menu of boot choices, highlight the one you normally boot and press e.  You'll be able to edit the command that boots up Linux.  Move the cursor to the end of the line, add a space and the word "nomodeset", then hit enter to continue booting.  Any better?

---

### Post by coby28 on 2018-01-23
what release is this?
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

what kernel are you running :
4.13.0-31-generic

Did the driver load ?
*-display               
       description: VGA compatible controller
       product: GK106 [GeForce GTX 645 OEM]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:27 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff

Is there now a driver conflict ?
no results when entering dpkg -l | grep -i nvidia* in the terminal

What does the gpu-manager have to say about the matter :
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.13.0-31-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.13.0-31-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? no
Vendor/Device Id: 10de:11c4
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "nouveau"
Found "/dev/dri/card0", driven by "nouveau"
output 0:
    card0-HDMI-A-1
Number of connected outputs for /dev/dri/card0: 1
Skipping "/dev/dri/card0", driven by "nouveau"
Does it require offloading? no
I couldn't open /var/lib/ubuntu-drivers-common/last_gfx_boot for reading.
Create /var/lib/ubuntu-drivers-common/last_gfx_boot for the 1st time
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? Yes
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? no
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? no
Is prime egl available? no
System configuration has changed
Single card detected
Kernel Module is not loaded
Nothing to do
No change - nothing to do

---

### Post by Bashing-om on 2018-01-23
coby28; Hummm ...

Surprised - all above looks Kosher - that "Additional Drivers" gave no joy .

For gaming one does want the proprietary driver .
Let's try from terminal and see if the system reports any error.
1st is to ensure the system is fully updated:
```

sudo apt update
sudo apt full-upgrade

```
reboot - just in case new packaging was installed in prep for the nest step.

next after comming up from the re-boot:
```

sudo ubuntu-drivers autoinstall

```
where the expectation is the installation of the 384 version driver.
The 384 is what nvidia does recommend:
[http://www.nvidia.com/download/driverResults.aspx/128737/en-us](http://www.nvidia.com/download/driverResults.aspx/128737/en-us)


[INDENT][INDENT]maybe YeS
[/INDENT][/INDENT]

---

### Post by coby28 on 2018-01-23
Done!

                        Reading state information... Done
 All packages are up to date.
  
After the reboot, the sudo ubuntu-drivers autoinstall has been done, and now there's this message:
                        Package information
 
 
 Configuring Secure Boot &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474;                                                                           &#9474;  
  &#9474; Your system has UEFI Secure Boot enabled.                                    
  &#9474;                                                                              
  &#9474; UEFI Secure Boot is not compatible with the use of third-party drivers.      
  &#9474;                                                                              
  &#9474; The system will assist you in toggling UEFI Secure Boot. To ensure that      
  &#9474; this change is being made by you as an authorized user, and not by an        
  &#9474; attacker, you must choose a password now and then use the same password      
  &#9474; after reboot to confirm the change.                                          
  &#9474;                                                                              
  &#9474; If you choose to proceed but do not confirm the password upon reboot,        
  &#9474; Ubuntu will still be able to boot on your system but the Secure Boot         
  &#9474; state will not be changed.                                                   
  &#9474;                                                                              
  &#9474; If Secure Boot remains enabled on your system, your system may  
  &#9474; boot but any hardware that requires third-party drivers to work              
  &#9474; correctly may not be usable.                                                 
  &#9474;                                                                              
  &#9474;                                  <Ok>

and then

 If Secure Boot remains enabled on your system, your system may still   &#9474; 
   &#9474; boot but any hardware that requires third-party drivers to work        &#9474; 
   &#9474; correctly may not be usable.                                           &#9474; 
   &#9474;                                                                        &#9474; 
   &#9474; Disable UEFI Secure Boot?                                              &#9474; 
   &#9474;                                                                        &#9474; 
   &#9474;                   <Yes>                      <No>

---

### Post by Bashing-om on 2018-01-23
coby28' Ouch - Yepper .

> 
Your system has UEFI Secure Boot enabled. 


EFI system ! Uh Huh .. got to disable secure boot in the firmware (bios) settings . That possibility plumb slipped my mind.

disable secure boot and run "autoinstall"  once again.

[INDENT][INDENT]how now ?
[/INDENT][/INDENT]

---

### Post by coby28 on 2018-01-23
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libllvm4.0
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and now a restart?

---

### Post by coby28 on 2018-01-23
oh now i see the 'NVIDIA X server settings' symbol in search!

---

### Post by Bashing-om on 2018-01-23
coby28; Great ,

And now Second Life performs ?

All good now in your 'buntu world ?

[INDENT]good things do happen
[/INDENT]

---

### Post by coby28 on 2018-01-23
*sighs* unfortunately not. We restarted our computer and the screen quality was not good when the login screen shows up. After entering our psw nothing happens, Ubuntu seems to start but then the login screen comes back. We're doing a fresh Ubuntu installation now.

---

### Post by coby28 on 2018-01-24
I think this &#9474; Disable UEFI Secure Boot?                                              &#9474; 
   &#9474;                                                                        &#9474; 
   &#9474;                   <Yes>                      <No> message is causing the problem. We selected "yes" and are requested to add a password. 

All looks ok and during the restart the login screen shows up, the screen quality is not so good anymore, we enter our ubuntu password => it seems Ubuntu is going to start but then immediately the login screen comes back and we're stuck.
Each time when we enter our password, immediately the same screen shows up.

Can someone please check? We don't know what to do anymore, the only solution is to do a complete re-install to use our pc :(

---

### Post by Bashing-om on 2018-01-24
coby28; Yukkie ---

These things happen :(

What machine is this ? As It is a UEFI what mode did you install in - EFI or legacy ? - what mode are you now booting into ? They must match .. dual booting ?  
as to "secure boot" requiring a password .. got me; I can not advise in that respect . But secure boot must be disabled to allow the installation of 3rd party softwares .

UEFI does complicate the equation .
See:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
[http://www.rodsbooks.com/linux-uefi/#oops](http://www.rodsbooks.com/linux-uefi/#oops) <- Linux on UEFI:A Quick Installation Guide


we try and make
[INDENT][INDENT]this happen
[/INDENT][/INDENT]

---

### Post by coby28 on 2018-01-24
Found it!!!!! :-)

We opened the booting menu again and we had to disable "secure boot" manually. After the restart, we could change the driver via the system settings and when logged in again, the nvidia driver is shown correctly.

Thank you very much

---

### Post by mörgæs on 2018-01-24
Good, please mark the thread solved.

---

