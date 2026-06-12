---
title: "problem with nvidia geforce 930m apfter upgrade"
date: 2018-01-02
forum: Hardware
---

### Post by fbio7 on 2018-01-02
OS: Ubuntu 14.04.1 LTS
Kernel 4.4.0-104
Notebook Dell Inspiron 15

After Upgrade my nvidia geforce 930m doesn't work and show the message low graphic mode. The system install nvidia 384.90 and this was the problem. what is the driver compatibility for this distro and kernel? Somebody have similar problem with ? 

data for comand lshw -C display
```

  *-display UNCLAIMED
       description: 3D controller
       product: GM108M [GeForce 930M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:d3000000-d307ffff

```

---

### Post by Bashing-om on 2018-01-02
fbio7; Hello -

You have no driver loaded per that output .
A quick stab at it - try:
Make sure secure boot is disabled in bios  -
```

sudo apt update
sudo apt full-upgrade
sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf 
sudo ubuntu-drivers autoinstall

```

Re-boot to see the effect .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by fbio7 on 2018-01-03
Hi Bashing-on 

I don't want to upgrade my distro of 14.04 to another. I only want to get my system up to date. I purge the nvidia drive and now I can login using the nouveau display drive but I can't use the performance mode of my card. I want to install a nvidia package compatible with this version that I am using and I don't know what was the previous drive that I was using before this update.

I tried install the ppa from the site [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) but the drivers doen't work, maybe I did something wrong in the process. 

thanks for helping.
Fábio

---

### Post by Bashing-om on 2018-01-03
fbio7; Welp ;

full-upgrade has nothing to do with a release upgrade to next - it just installs "new" software for the current install release/

Nothing wrong in using our PPA for the nvidia driver.

show us now what is installed:
```

cat /etc/apt/sources.list.d/*.list
dpkg -l | grep -i nvidia
lsmod | grep nvidia
sudo lshw -C display

```

[INDENT][INDENT]should be 
[INDENT][INDENT][INDENT]nothing but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by fbio7 on 2018-01-05
Hi Bashing-on

Thanks for help. follow the information:

```

Inspiron-5557:~$ cat /etc/apt/sources.list.d/*.list
deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu trusty main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu trusty main
deb http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu trusty main
deb http://dell.archive.canonical.com/updates/ trusty-dell-csmb-vivid-skl public
deb-src http://dell.archive.canonical.com/updates/ trusty-dell-csmb-vivid-skl public
deb http://dell.archive.canonical.com/updates/ trusty-dell public
deb-src http://dell.archive.canonical.com/updates/ trusty-dell public
deb http://oem.archive.canonical.com/updates/ trusty-oem public
deb-src http://oem.archive.canonical.com/updates/ trusty-oem public
deb http://oem.archive.canonical.com/updates/ trusty-oem-sp1 public
deb-src http://oem.archive.canonical.com/updates/ trusty-oem-sp1 public
deb http://ppa.launchpad.net/videolan/master-daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/videolan/master-daily/ubuntu trusty main
deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu trusty main

```

```

Inspiron-5557:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-340  

```

 ```
 
    Inspiron-5557:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Sky Lake Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:125 memory:d4000000-d4ffffff memory:b0000000-bfffffff ioport:f000(size=64)
  *-display UNCLAIMED
       description: 3D controller
       product: GM108M [GeForce 930M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d00000
            

```

---

### Post by Bashing-om on 2018-01-05
fbio7;' Still -

No graphic's driver installed .

Post back the results :
```

sudo apt update
sudo apt full-upgrade

```
See what might prevent you obtaining the nvidia proprietary driver .

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by sccman on 2018-01-05
You could manually install the nVidia drivers through their website or through the repositories:

```
sudo apt install nvidia-384
```

---

### Post by fbio7 on 2018-01-06
Hi..follow the codes 

Code for update
```

Inspiron-5557:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://archive.canonical.com trusty InRelease                              
Get:1 http://us.archive.ubuntu.com trusty-security InRelease [65,9 kB]         
Hit http://dl.google.com stable Release.gpg                                    
Ign http://dell.archive.canonical.com trusty-dell-csmb-vivid-skl InRelease     
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://dl.google.com stable Release                                        
Ign http://oem.archive.canonical.com trusty-oem-sp1 InRelease                  
Hit http://archive.canonical.com trusty Release                                
Ign http://dell.archive.canonical.com trusty-dell InRelease                    
Ign http://oem.archive.canonical.com trusty-oem InRelease                      
Hit http://dl.google.com stable/main amd64 Packages                            
Get:2 http://us.archive.ubuntu.com trusty-updates InRelease [65,9 kB]          
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://dell.archive.canonical.com trusty-dell-csmb-vivid-skl Release.gpg   
Hit http://oem.archive.canonical.com trusty-oem-sp1 Release.gpg                
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://dell.archive.canonical.com trusty-dell Release.gpg                  
Hit http://oem.archive.canonical.com trusty-oem Release.gpg                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Get:3 http://us.archive.ubuntu.com trusty-security/main Sources [147 kB]       
Hit http://dell.archive.canonical.com trusty-dell-csmb-vivid-skl Release       
Hit http://oem.archive.canonical.com trusty-oem-sp1 Release                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dell.archive.canonical.com trusty-dell Release                      
Hit http://oem.archive.canonical.com trusty-oem Release                        
Get:4 http://us.archive.ubuntu.com trusty-security/restricted Sources [4.931 B]
Get:5 http://us.archive.ubuntu.com trusty-security/universe Sources [67,2 kB]  
Hit http://dell.archive.canonical.com trusty-dell-csmb-vivid-skl/public Sources
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://oem.archive.canonical.com trusty-oem-sp1/public Sources             
Get:6 http://us.archive.ubuntu.com trusty-security/multiverse Sources [3.182 B]
Hit http://dell.archive.canonical.com trusty-dell-csmb-vivid-skl/public amd64 Packages
Hit http://oem.archive.canonical.com trusty-oem-sp1/public amd64 Packages      
Get:7 http://us.archive.ubuntu.com trusty-security/main amd64 Packages [697 kB]
Hit http://dell.archive.canonical.com trusty-dell-csmb-vivid-skl/public i386 Packages
Hit http://oem.archive.canonical.com trusty-oem-sp1/public i386 Packages       
Ign http://dl.google.com stable/main Translation-en_US                         
Get:8 http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages [14,1 kB]
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-pt                            
Get:9 http://us.archive.ubuntu.com trusty-security/universe amd64 Packages [199 kB]
Ign http://dl.google.com stable/main Translation-pt_BR                         
Get:10 http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages [4.800 B]
Get:11 http://us.archive.ubuntu.com trusty-security/main i386 Packages [641 kB]
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://dell.archive.canonical.com trusty-dell/public Sources               
Hit http://oem.archive.canonical.com trusty-oem/public Sources                 
Hit http://dell.archive.canonical.com trusty-dell/public amd64 Packages        
Hit http://oem.archive.canonical.com trusty-oem/public amd64 Packages          
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://dell.archive.canonical.com trusty-dell/public i386 Packages         
Hit http://oem.archive.canonical.com trusty-oem/public i386 Packages           
Get:12 http://us.archive.ubuntu.com trusty-security/restricted i386 Packages [13,9 kB]
Get:13 http://us.archive.ubuntu.com trusty-security/universe i386 Packages [195 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:14 http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages [4.958 B]
Get:15 http://us.archive.ubuntu.com trusty-security/main Translation-en [375 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:16 http://us.archive.ubuntu.com trusty-security/multiverse Translation-en [2.564 B]
Get:17 http://us.archive.ubuntu.com trusty-security/restricted Translation-en [3.542 B]
Get:18 http://us.archive.ubuntu.com trusty-security/universe Translation-en [113 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:19 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [437 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [14,8 kB]
Get:21 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [1.046 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:22 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [17,2 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:23 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [435 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [15,3 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:25 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [987 kB] 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release                                    
Get:26 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [17,0 kB]
Ign http://dell.archive.canonical.com trusty-dell-csmb-vivid-skl/public Translation-en_US
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:27 http://us.archive.ubuntu.com trusty-updates/main Translation-en [516 kB]
Ign http://dell.archive.canonical.com trusty-dell-csmb-vivid-skl/public Translation-en
Ign http://dell.archive.canonical.com trusty-dell-csmb-vivid-skl/public Translation-pt
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://dell.archive.canonical.com trusty-dell-csmb-vivid-skl/public Translation-pt_BR
Ign http://dell.archive.canonical.com trusty-dell/public Translation-en_US     
Ign http://dell.archive.canonical.com trusty-dell/public Translation-en        
Ign http://oem.archive.canonical.com trusty-oem-sp1/public Translation-en_US   
Ign http://dell.archive.canonical.com trusty-dell/public Translation-pt        
Ign http://oem.archive.canonical.com trusty-oem-sp1/public Translation-en      
Ign http://dell.archive.canonical.com trusty-dell/public Translation-pt_BR     
Ign http://oem.archive.canonical.com trusty-oem-sp1/public Translation-pt      
Get:28 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [7.755 B]
Ign http://oem.archive.canonical.com trusty-oem-sp1/public Translation-pt_BR   
Get:29 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [4.031 B]
Ign http://oem.archive.canonical.com trusty-oem/public Translation-en_US       
Get:30 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [236 kB]
Ign http://oem.archive.canonical.com trusty-oem/public Translation-en          
Ign http://oem.archive.canonical.com trusty-oem/public Translation-pt          
Ign http://oem.archive.canonical.com trusty-oem/public Translation-pt_BR       
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/main Translation-pt             
Hit http://us.archive.ubuntu.com trusty/main Translation-pt_BR                 
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-pt              
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-pt_BR           
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-pt              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-pt_BR           
Ign http://ppa.launchpad.net trusty/main Translation-pt                        
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-pt_BR                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-pt                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-pt_BR             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 6.351 kB in 22s (281 kB/s)                                             
Reading package lists... Done

```

Code for the full upgrade
```

Inspiron-5557:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms grub-pc-bin libjansson4 libllvm3.6 libllvm3.6:i386 libvdpau1
  libxnvctrl0 linux-image-extra-3.19.0-79-generic
  linux-image-extra-4.4.0-66-generic linux-signed-image-3.19.0-79-generic
  linux-signed-image-4.4.0-66-generic screen-resolution-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I will login in root mode(only text without lightmdm service) and try to install the driver 384 again. 

thanks guys.

---

### Post by Bashing-om on 2018-01-06
fbio7; Ho kay ..

Looks good .. now I would run:
```

sudo apt autoremove

```
as the package manager advises. ( get rid of " bbswitch-dkms " ).

Now we try again - from the normal user account ( clt+alt+F2 if required ) :
```

sudo apt purge nvidia
sudo rm /etc/X11/Xorg.conf ## if it should exist, if needed will be re-created
sudo ubuntu-drivers autoinstall

```
where autoinstall chooses the 387 version driver from the PPA - I will not be surprised .

[INDENT][INDENT]should workie great
[/INDENT][/INDENT]

---

### Post by tokyobadger on 2018-01-06
@Bashing-om: you might need to guide fbio7 on how to remove any attempted manual installs (downloaded from nvidia)
[quote="fbio7"]I will login in root mode(only text without lightmdm service) and try to install the driver 384 again.[/quote]
Smells like a manual install attempt to me

---

### Post by Bashing-om on 2018-01-06
@tokyobadger
That is a thought !

@fbio7L
what shows:
```

sudo find / -name "NVIDIA-Linux-*"

```
give find time to search .

[INDENT][INDENT]I say again
[INDENT][INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by fbio7 on 2018-01-06
Hi Guys..follow the codes. 

**sudo find / -name "NVIDIA-Linux-*"**
```

Inspiron-5557:~$ sudo find / -name "NVIDIA-Linux-*"
[sudo] password for x: 
Inspiron-5557:~$ 

```
doesn't found anything.

**sudo ubuntu-drivers autoinstall**
```

Inspiron-5557:~$ sudo ubuntu-drivers autoinstall
[sudo] password for x: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bbswitch-dkms libcuda1-387 libjansson4 libvdpau1 libxnvctrl0
  nvidia-opencl-icd-387 nvidia-prime nvidia-settings screen-resolution-extra
Suggested packages:
  bumblebee
Recommended packages:
  vdpau-driver-all vdpau-driver
The following NEW packages will be installed:
  bbswitch-dkms libcuda1-387 libjansson4 libvdpau1 libxnvctrl0 nvidia-387
  nvidia-opencl-icd-387 nvidia-prime nvidia-settings screen-resolution-extra
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 81,2 MB/82,2 MB of archives.
After this operation, 374 MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libvdpau1 nvidia-387 libcuda1-387 libxnvctrl0 nvidia-opencl-icd-387
  nvidia-settings
E: There are problems and -y was used without --force-yes

```


**sudo apt-get install nvidia-384**
```

Inspiron-5557:~$ sudo apt-get install nvidia-384
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bbswitch-dkms libcuda1-384 libjansson4 libvdpau1 libxnvctrl0
  nvidia-opencl-icd-384 nvidia-prime nvidia-settings screen-resolution-extra
Suggested packages:
  bumblebee
Recommended packages:
  vdpau-driver-all vdpau-driver
The following NEW packages will be installed:
  bbswitch-dkms libcuda1-384 libjansson4 libvdpau1 libxnvctrl0 nvidia-384
  nvidia-opencl-icd-384 nvidia-prime nvidia-settings screen-resolution-extra
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 47,5 kB/81,3 MB of archives.
After this operation, 360 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by Bashing-om on 2018-01-06
fbio7; Ouch -

> 
WARNING: The following packages cannot be authenticated!
  libvdpau1 nvidia-387 libcuda1-387 libxnvctrl0 nvidia-opencl-icd-387
  nvidia-settings
[color=red]E: There are problems and -y was used without --force-yes[/color]


can not imagine what is going on in the package management system to generate this condition.

Reboot at this time .. did the driver install ?
After the reboot, what shows:
```

sudo lshw -C display

```


sometimes to wonder
[INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT]

---

### Post by tokyobadger on 2018-01-06
Try
```
sudo apt-key update
sudo apt-get update
sudo ubuntu-drivers autoinstall
```

---

### Post by fbio7 on 2018-01-06
Hi ..I restart and try again.

**sudo ubuntu-drivers autoinstall**
```

Inspiron-5557:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bbswitch-dkms libcuda1-387 libjansson4 libvdpau1 libxnvctrl0
  nvidia-opencl-icd-387 nvidia-prime nvidia-settings screen-resolution-extra
Suggested packages:
  bumblebee
Recommended packages:
  vdpau-driver-all vdpau-driver
The following NEW packages will be installed:
  bbswitch-dkms libcuda1-387 libjansson4 libvdpau1 libxnvctrl0 nvidia-387
  nvidia-opencl-icd-387 nvidia-prime nvidia-settings screen-resolution-extra
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 81,2 MB/82,2 MB of archives.
After this operation, 374 MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libvdpau1 nvidia-387 libcuda1-387 libxnvctrl0 nvidia-opencl-icd-387
  nvidia-settings
E: There are problems and -y was used without --force-yes

```

what do you think if I install it direct using the command sudo apt-get install nvidia-387 ?

```

**sudo apt-get install nvidia-387**
Inspiron-5557:~$ sudo apt-get install nvidia-387
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bbswitch-dkms libcuda1-387 libjansson4 libvdpau1 libxnvctrl0
  nvidia-opencl-icd-387 nvidia-prime nvidia-settings screen-resolution-extra
Suggested packages:
  bumblebee
Recommended packages:
  vdpau-driver-all vdpau-driver
The following NEW packages will be installed:
  bbswitch-dkms libcuda1-387 libjansson4 libvdpau1 libxnvctrl0 nvidia-387
  nvidia-opencl-icd-387 nvidia-prime nvidia-settings screen-resolution-extra
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 81,2 MB/82,2 MB of archives.
After this operation, 374 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by tokyobadger on 2018-01-06
At this point (unless anyone else comes along soon to resolve the authentication warning topic) I would say give it a try (you can always purge again).

From what can I see in your replies to Bashing-om's advice, your system is "clean" of any previous nvidia installs. The only thing I see possibly happening is that you get the authentication warning again.

Let's see.

---

### Post by Bashing-om on 2018-01-06
fbio7;

+1 to tokyobadger' s advise to run:
```

sudo apt-key update

```
Post this output.

Also be aware there can be only ONE nvidia driver version install .. only ONE .

autoinstall is reliable to install the nvidia driver; allowing apt-get install nvidia-387 ro complete might cause a driver conflict . And then the driver will not be able to load.

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by fbio7 on 2018-01-06
Hi guys...

I shutdown my system and have a break, after sometime I turn on my notebook and did the follow steps to install nvidia-387 with success. 
[/CODE]
sudo apt-key update
sudo apt-get update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall
[/CODE]

so when the system try to restart show the black screen with a message again: low graphic mode.....:(. For login I went to advanced options and run the previous kernel 4.4.0-93

[ATTACH=CONFIG]278082[/ATTACH]



**follow the codes with the results**
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
[/CODE]

```

Inspiron-5557:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

Inspiron-5557:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bbswitch-dkms libcuda1-387 libjansson4 libvdpau1 libxnvctrl0
  nvidia-opencl-icd-387 nvidia-prime nvidia-settings screen-resolution-extra
Suggested packages:
  bumblebee
Recommended packages:
  vdpau-driver-all vdpau-driver
The following NEW packages will be installed:
  bbswitch-dkms libcuda1-387 libjansson4 libvdpau1 libxnvctrl0 nvidia-387
  nvidia-opencl-icd-387 nvidia-prime nvidia-settings screen-resolution-extra
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 81,2 MB/82,2 MB of archives.
After this operation, 374 MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libjansson4 amd64 2.5-2 [25,2 kB]
Get:2 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/ trusty/main nvidia-387 amd64 387.34-0ubuntu0~gpu14.04.2 [74,3 MB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/main bbswitch-dkms amd64 0.7-2ubuntu1 [10,9 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty/main screen-resolution-extra all 0.17.1 [11,4 kB]
Get:5 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/ trusty/main libcuda1-387 amd64 387.34-0ubuntu0~gpu14.04.2 [3.395 kB]
Get:6 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/ trusty/main nvidia-opencl-icd-387 amd64 387.34-0ubuntu0~gpu14.04.2 [3.489 kB]
Fetched 81,2 MB in 2min 49s (478 kB/s)                                         
Selecting previously unselected package libjansson4:amd64.
(Reading database ... 582271 files and directories currently installed.)
Preparing to unpack .../libjansson4_2.5-2_amd64.deb ...
Unpacking libjansson4:amd64 (2.5-2) ...
Selecting previously unselected package libvdpau1:amd64.
Preparing to unpack .../libvdpau1_1.1.1-3ubuntu1~gpu14.04.1_amd64.deb ...
Unpacking libvdpau1:amd64 (1.1.1-3ubuntu1~gpu14.04.1) ...
Selecting previously unselected package nvidia-387.
Preparing to unpack .../nvidia-387_387.34-0ubuntu0~gpu14.04.2_amd64.deb ...
Unpacking nvidia-387 (387.34-0ubuntu0~gpu14.04.2) ...
Selecting previously unselected package libcuda1-387.
Preparing to unpack .../libcuda1-387_387.34-0ubuntu0~gpu14.04.2_amd64.deb ...
Unpacking libcuda1-387 (387.34-0ubuntu0~gpu14.04.2) ...
Selecting previously unselected package libxnvctrl0.
Preparing to unpack .../libxnvctrl0_387.22-0ubuntu0~gpu14.04.1_amd64.deb ...
Unpacking libxnvctrl0 (387.22-0ubuntu0~gpu14.04.1) ...
Selecting previously unselected package nvidia-opencl-icd-387.
Preparing to unpack .../nvidia-opencl-icd-387_387.34-0ubuntu0~gpu14.04.2_amd64.deb ...
Unpacking nvidia-opencl-icd-387 (387.34-0ubuntu0~gpu14.04.2) ...
Selecting previously unselected package bbswitch-dkms.
Preparing to unpack .../bbswitch-dkms_0.7-2ubuntu1_amd64.deb ...
Unpacking bbswitch-dkms (0.7-2ubuntu1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.6.2.1_amd64.deb ...
Unpacking nvidia-prime (0.6.2.1) ...
Selecting previously unselected package screen-resolution-extra.
Preparing to unpack .../screen-resolution-extra_0.17.1_all.deb ...
Unpacking screen-resolution-extra (0.17.1) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_387.22-0ubuntu0~gpu14.04.1_amd64.deb ...
Unpacking nvidia-settings (387.22-0ubuntu0~gpu14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils (0.22-1ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Setting up libjansson4:amd64 (2.5-2) ...
Setting up libvdpau1:amd64 (1.1.1-3ubuntu1~gpu14.04.1) ...
Setting up nvidia-387 (387.34-0ubuntu0~gpu14.04.2) ...
update-alternatives: using /usr/lib/nvidia-387/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-387/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-387/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-387/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-387/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
/sbin/ldconfig.real: /usr/lib/nvidia-387/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-387/libEGL.so.1 is not a symbolic link

update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-387
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Adding system user `nvidia-persistenced' (UID 117) ...
Adding new group `nvidia-persistenced' (GID 126) ...
Adding new user `nvidia-persistenced' (UID 117) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-387-387.34 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-104-generic
Building for architecture x86_64
Building initial module for 4.4.0-104-generic
Done.

nvidia_387:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-104-generic/updates/dkms/

nvidia_387_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-104-generic/updates/dkms/

nvidia_387_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-104-generic/updates/dkms/

nvidia_387_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-104-generic/updates/dkms/

depmod..........

DKMS: install completed.
Setting up libcuda1-387 (387.34-0ubuntu0~gpu14.04.2) ...
Setting up libxnvctrl0 (387.22-0ubuntu0~gpu14.04.1) ...
Setting up nvidia-opencl-icd-387 (387.34-0ubuntu0~gpu14.04.2) ...
Setting up bbswitch-dkms (0.7-2ubuntu1) ...
Loading new bbswitch-0.7 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-104-generic
Building initial module for 4.4.0-104-generic
Done.

bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-104-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up nvidia-prime (0.6.2.1) ...
nvidia-prime start/running, process 10327
Setting up screen-resolution-extra (0.17.1) ...
Setting up nvidia-settings (387.22-0ubuntu0~gpu14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.13) ...
/sbin/ldconfig.real: /usr/lib/nvidia-387/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-387/libEGL.so.1 is not a symbolic link

Processing triggers for initramfs-tools (0.103ubuntu4.10) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-104-generic
Processing triggers for shim-signed (1.32~14.04.2+0.9+1474479173.6c180c6-1ubuntu1) ...
Secure Boot not enabled on this system.
Processing triggers for ureadahead (0.100.0-16) ...

```

---

### Post by Bashing-om on 2018-01-06
fbio7; Hey ,,,

And all looks good now ?

for the warning;
> 
/usr/lib32/nvidia-387/libEGL.so.1 is not a symbolic link

see:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860)
to reset the symbolic links .


[INDENT][INDENT]my bit to try and help[/INDENT][/INDENT]

---

### Post by tokyobadger on 2018-01-06
@fbio7: can you show us the output of lsmod | grep nvidia

---

### Post by tokyobadger on 2018-01-06
@Bashing-om: any thoughts on /etc/default/grub? Namely nomodeset and rd.driver.blacklist=nouveau given that this appears to be 14.04.1 (x64?)

---

### Post by Bashing-om on 2018-01-06
@tokyobadger; Well ...

I have not seen any evidence that nomodeset is in effect. ( but maybe issues with the Intel chip set )
When there are suspected annomolles in the X layer, there is the log file that relates a lot of info.
```

cat /var/log/Xorg.0.log

```
Issues managing the driver:
```

cat /var/log/gpu-manager.log

```

[INDENT][INDENT]I try not to cross these bridges 'til I come to them [/INDENT][/INDENT]

---

### Post by fbio7 on 2018-01-07
Hi...
> **Bashing-om said:**
> fbio7; Hey ,,,
And all looks good now ?


Unfortunately, It isn't working. When the system try to run the graphic mode that show the message "low graphic mode". I did the command Ctrl+Alt+F2 and save the log files 

Follow the log files.
cat /var/log/gpu-manager.log
```

log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.4.0-104-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-104-generic/updates/dkms
Found nvidia module: nvidia_387.ko
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:1916
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1346
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "i915_bpo"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "i915_bpo"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "i915_bpo"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Found "/dev/dri/card0", driven by "i915_bpo"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-387/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/nvidia-387/ld.so.conf
Is nvidia enabled? yes
Is nvidia egl enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is mesa egl enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no
Intel IGP detected
Intel hybrid system
Nvidia driver version 387.34 detected
Invalid /sys/class/dmi/id/product_version=""
/sys/class/dmi/id/product_name="Inspiron 5557"
1st try: bbswitch without quirks
Loading bbswitch with "load_state=-1 unload_state=1" parameters
2nd try: bbswitch with quirks
Loading bbswitch with "load_state=-1 unload_state=1 skip_optimus_dsm=1" parameters
Warning: can't load bbswitch, switching between GPUs won't work
intel_matches: 1, nvidia_matches: 1, intel_set: 1, nvidia_set: 1 x_options_matches: 4, accel_method_matches: 1
No need to modify xorg.conf. Path: /etc/X11/xorg.conf
No need to change the current bbswitch status

```

cat /var/log/Xorg.0.log

```
[    27.785] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[    27.785] X Protocol Version 11, Revision 0
[    27.785] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[    27.785] Current Operating System: Linux fabio-Inspiron-5557 4.4.0-104-generic #127~14.04.1-Ubuntu SMP Mon Dec 11 12:44:15 UTC 2017 x86_64
[    27.785] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-104-generic.efi.signed root=UUID=f8030880-1de5-4176-9fda-f98160720c71 ro quiet splash vt.handoff=7
[    27.785] Build Date: 13 October 2017  02:07:47PM
[    27.785] xorg-server 2:1.18.3-1ubuntu2.3~trusty4 (For technical support please see http://www.ubuntu.com/support) 
[    27.785] Current version of pixman: 0.30.2
[    27.785]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    27.785] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.785] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan  7 11:45:10 2018
[    27.785] (==) Using config file: "/etc/X11/xorg.conf"
[    27.785] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.785] (==) ServerLayout "layout"
[    27.785] (**) |-->Screen "nvidia" (0)
[    27.785] (**) |   |-->Monitor "<default monitor>"
[    27.785] (**) |   |-->Device "nvidia"
[    27.785] (**) |   |-->GPUDevice "nvidia"
[    27.785] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[    27.785] (**) |-->Inactive Device "intel"
[    27.785] (==) Automatically adding devices
[    27.785] (==) Automatically enabling devices
[    27.785] (==) Automatically adding GPU devices
[    27.785] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    27.785] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.785]     Entry deleted from font path.
[    27.785] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.785]     Entry deleted from font path.
[    27.785] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.785]     Entry deleted from font path.
[    27.785] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.785]     Entry deleted from font path.
[    27.785] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.785]     Entry deleted from font path.
[    27.785] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    27.785] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.785] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.785] (II) Loader magic: 0x559ac0094d00
[    27.785] (II) Module ABI versions:
[    27.785]     X.Org ANSI C Emulation: 0.4
[    27.785]     X.Org Video Driver: 20.0
[    27.785]     X.Org XInput driver : 22.1
[    27.785]     X.Org Server Extension : 9.0
[    27.786] (++) using VT number 7

[    27.786] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    27.786] (II) xfree86: Adding drm device (/dev/dri/card0)
[    27.787] (II) xfree86: Adding drm device (/dev/dri/card1)
[    27.788] (--) PCI:*(0:0:2:0) 8086:1916:1028:070a rev 7, Mem @ 0xd4000000/16777216, 0xb0000000/268435456, I/O @ 0x0000f000/64
[    27.788] (--) PCI: (0:1:0:0) 10de:1346:1028:070a rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    27.788] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    27.788] (II) "glx" will be loaded by default.
[    27.788] (II) LoadModule: "glx"
[    27.788] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    27.791] (II) Module glx: vendor="NVIDIA Corporation"
[    27.791]     compiled for 4.0.2, module version = 1.0.0
[    27.791]     Module class: X.Org Server Extension
[    27.791] (II) NVIDIA GLX Module  387.34  Tue Nov 21 02:04:31 PST 2017
[    27.791] (II) LoadModule: "nvidia"
[    27.791] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    27.792] (II) Module nvidia: vendor="NVIDIA Corporation"
[    27.792]     compiled for 4.0.2, module version = 1.0.0
[    27.792]     Module class: X.Org Video Driver
[    27.792] (II) LoadModule: "modesetting"
[    27.792] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    27.792] (II) Module modesetting: vendor="X.Org Foundation"
[    27.792]     compiled for 1.18.3, module version = 1.18.3
[    27.792]     Module class: X.Org Video Driver
[    27.792]     ABI class: X.Org Video Driver, version 20.0
[    27.792] (II) NVIDIA dlloader X Driver  387.34  Tue Nov 21 01:38:22 PST 2017
[    27.792] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    27.792] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    27.793] (II) Loading sub module "fb"
[    27.793] (II) LoadModule: "fb"
[    27.794] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.794] (II) Module fb: vendor="X.Org Foundation"
[    27.794]     compiled for 1.18.3, module version = 1.0.0
[    27.794]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.794] (II) Loading sub module "wfb"
[    27.794] (II) LoadModule: "wfb"
[    27.794] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    27.794] (II) Module wfb: vendor="X.Org Foundation"
[    27.794]     compiled for 1.18.3, module version = 1.0.0
[    27.794]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.794] (II) Loading sub module "ramdac"
[    27.794] (II) LoadModule: "ramdac"
[    27.794] (II) Module "ramdac" already built-in
[    27.794] (II) modeset(G0): using drv /dev/dri/card0
[    27.794] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[    27.794] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    27.794] (==) NVIDIA(0): RGB weight 888
[    27.794] (==) NVIDIA(0): Default visual is TrueColor
[    27.794] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    27.794] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    27.794] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    27.794] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    27.794] (**) NVIDIA(0): Enabling 2D acceleration
[    27.797] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[    27.797] (EE) NVIDIA(GPU-0):     check your system's kernel log for additional error
[    27.797] (EE) NVIDIA(GPU-0):     messages and refer to Chapter 8: Common Problems in the
[    27.797] (EE) NVIDIA(GPU-0):     README for additional information.
[    27.797] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA graphics device!
[    27.797] (EE) NVIDIA(0): Failing initialization of X screen 0
[    27.797] (II) UnloadModule: "nvidia"
[    27.797] (II) UnloadSubModule: "wfb"
[    27.797] (II) UnloadSubModule: "fb"
[    27.797] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[    27.797] (**) modeset(G0): Option "AccelMethod" "None"
[    27.797] (==) modeset(G0): RGB weight 888
[    27.797] (==) modeset(G0): Default visual is TrueColor
[    27.797] (**) modeset(G0): glamor disabled
[    27.797] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[    27.798] (II) modeset(G0): Output eDP-1 has no monitor section
[    27.924] (II) modeset(G0): Output HDMI-1 has no monitor section
[    27.924] (II) modeset(G0): EDID for output eDP-1
[    27.924] (II) modeset(G0): Manufacturer: LGD  Model: 456  Serial#: 0
[    27.924] (II) modeset(G0): Year: 2014  Week: 0
[    27.924] (II) modeset(G0): EDID Version: 1.4
[    27.924] (II) modeset(G0): Digital Display Input
[    27.924] (II) modeset(G0): 6 bits per channel
[    27.924] (II) modeset(G0): Digital interface is DisplayPort
[    27.924] (II) modeset(G0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    27.924] (II) modeset(G0): Gamma: 2.20
[    27.924] (II) modeset(G0): No DPMS capabilities specified
[    27.924] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    27.924] (II) modeset(G0): First detailed timing is preferred mode
[    27.924] (II) modeset(G0): Preferred mode is native pixel format and refresh rate
[    27.924] (II) modeset(G0): redX: 0.578 redY: 0.344   greenX: 0.337 greenY: 0.571
[    27.924] (II) modeset(G0): blueX: 0.159 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    27.924] (II) modeset(G0): Manufacturer's mask: 0
[    27.924] (II) modeset(G0): Supported detailed timing:
[    27.924] (II) modeset(G0): clock: 76.3 MHz   Image Size:  344 x 194 mm
[    27.924] (II) modeset(G0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1610 h_border: 0
[    27.924] (II) modeset(G0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    27.924] (II) modeset(G0): Supported detailed timing:
[    27.924] (II) modeset(G0): clock: 61.0 MHz   Image Size:  344 x 194 mm
[    27.924] (II) modeset(G0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1610 h_border: 0
[    27.924] (II) modeset(G0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    27.924] (II) modeset(G0):  DCR74\80156WHB
[    27.924] (II) modeset(G0): Unknown vendor-specific block 0
[    27.924] (II) modeset(G0): EDID (in hex):
[    27.924] (II) modeset(G0):     00ffffffffffff0030e4560400000000
[    27.924] (II) modeset(G0):     00180104952213780a05f59458569228
[    27.924] (II) modeset(G0):     1e505400000001010101010101010101
[    27.924] (II) modeset(G0):     010101010101d01d56f4500016303020
[    27.924] (II) modeset(G0):     350058c21000001ad91756f450001630
[    27.924] (II) modeset(G0):     3020350058c21000001a000000fe0044
[    27.924] (II) modeset(G0):     43523734803135365748420a00000000
[    27.924] (II) modeset(G0):     00004131940010000009010a20200085
[    27.924] (II) modeset(G0): Printing probed modes for output eDP-1
[    27.924] (II) modeset(G0): Modeline "1366x768"x60.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    27.924] (II) modeset(G0): Modeline "1366x768"x48.0   61.05  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (37.9 kHz e)
[    27.924] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    27.924] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    27.924] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    27.924] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    27.924] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    27.924] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    27.924] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    27.924] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    27.924] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    27.924] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    27.924] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    27.924] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    27.924] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    27.924] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    27.924] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    27.924] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    27.924] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    27.924] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    27.924] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    27.924] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    27.924] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    27.924] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    27.924] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    27.924] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    27.924] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    27.924] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    27.924] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    28.052] (II) modeset(G0): EDID for output HDMI-1
[    28.052] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    28.052] (==) modeset(G0): DPI set to (96, 96)
[    28.052] (II) Loading sub module "fb"
[    28.052] (II) LoadModule: "fb"
[    28.052] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.052] (II) Module fb: vendor="X.Org Foundation"
[    28.052]     compiled for 1.18.3, module version = 1.0.0
[    28.052]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.052] (II) Loading sub module "shadow"
[    28.052] (II) LoadModule: "shadow"
[    28.052] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    28.052] (II) Module shadow: vendor="X.Org Foundation"
[    28.052]     compiled for 1.18.3, module version = 1.1.0
[    28.052]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.052] (EE) Screen(s) found, but none have a usable configuration.
[    28.052] (EE) 
Fatal server error:
[    28.052] (EE) no screens found(EE) 
[    28.052] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    28.052] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    28.052] (EE) 
[    28.054] (EE) Server terminated with error (1). Closing log file.


```

```

lsmod | grep nvidia

nvidia_drm             45056  0 
nvidia_modeset        897024  1 nvidia_drm
nvidia              13971456  1 nvidia_modeset
drm_kms_helper        151552  2 i915_bpo,nvidia_drm
drm                   360448  4 i915_bpo,drm_kms_helper,nvidia_drm


```

thanks for the tips and attention.

---

### Post by Bashing-om on 2018-01-07
fbio7; Yukkie -

What in the world is going on here ?
from the gpu-manager log:
> 
Is prime enabled? [color=red]no[/color]

Invalid /sys/class/dmi/id/product_version=""
/sys/class/dmi/id/product_name="Inspiron 5557"

Warning: can't load bbswitch, switching between GPUs won't work


And X is also screaming
> 
 27.797] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[    27.797] (EE) NVIDIA(GPU-0):     check your system's kernel log for additional error
[    27.797] (EE) NVIDIA(GPU-0):     messages and refer to Chapter 8: Common Problems in the
[    27.797] (EE) NVIDIA(GPU-0):     README for additional information.
[    27.797] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA graphics device!
[    27.797] (EE) NVIDIA(0): Failing initialization of X screen 0

28.052]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.052] (EE) Screen(s) found, but none have a usable configuration.
[    28.052] (EE) 
Fatal server error:
[    28.052] (EE) no screens found(EE) 
[    28.052] (EE)

28.054] (EE) Server terminated with error (1). Closing log file.


Ouch !

See if we can finger this out.
Show us:
```

lsmod | grep i915
lsmod | grep i915_bpo
dpkg -l | grep -i nvidia
cat /etc/X11/Xorg.conf

```

A failure to communicate -
[INDENT][INDENT][INDENT]somewhere[/INDENT][/INDENT][/INDENT]

---

### Post by fbio7 on 2018-01-09
yeah...A lot of trouble with this "piii" card nvidia !!! 

I found an old file of my notebook(backup of my commands) that have the follow information**:**
```

[FONT=ubuntubeta][COLOR=#000000]comando: uname -r 

resultado:3.19.0-28-generi



Dados pasta /proc 3d
NVRM version: NVIDIA UNIX x86_64 Kernel Module  352.21  Tue Jun  9 21:53:31 PDT 2015
GCC version:  gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) 


Model:          GeForce 930M
IRQ:            135
GPU UUID:      GPU-deb41b29-843e-9aa2-17d4-46e4985e169a
Video BIOS:      82.08.4d.00.04
Bus Type:      PCIe
DMA Size:      40 bits
DMA Mask:      0xffffffffff
Bus Location:      0000:01:00.0
[/COLOR][/FONT]
```[FONT=ubuntubeta][COLOR=#000000]

[/COLOR][/FONT]**Ps: Now I'm in the 4.4.0-104 kernel and ubuntu 14.01.1**



```

lsmod | grep i915

i915_bpo             1306624  3 
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
drm_kms_helper        151552  2 i915_bpo,nvidia_drm
drm                   360448  4 i915_bpo,drm_kms_helper,nvidia_drm
video                  40960  3 i915_bpo,dell_wmi,dell_laptop

```

```

lsmod | grep i915_bpo

i915_bpo             1306624  3 
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
drm_kms_helper        151552  2 i915_bpo,nvidia_drm
drm                   360448  4 i915_bpo,drm_kms_helper,nvidia_drm
video                  40960  3 i915_bpo,dell_wmi,dell_laptop

```

In the dpkg code, why the "rc  libcuda1-340" for the 14.04.1 and the others for 14.04.2 ? What do you think about ?   
```

dpkg -l | grep -i nvidia

ii  bbswitch-dkms                                         0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-340                                          340.104-0ubuntu0~gpu14.04.1                         amd64        NVIDIA CUDA runtime library
ii  libcuda1-387                                          387.34-0ubuntu0~gpu14.04.2                          amd64        NVIDIA CUDA runtime library
ii  nvidia-387                                            387.34-0ubuntu0~gpu14.04.2                          amd64        NVIDIA binary driver - version 387.34
ii  nvidia-opencl-icd-387                                 387.34-0ubuntu0~gpu14.04.2                          amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2.1                                             amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       387.22-0ubuntu0~gpu14.04.1                          amd64        Tool for configuring the NVIDIA graphics driver

```


```

cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection


```

---

### Post by sccman on 2018-01-09
UNCLAIMED typically means there are no drivers associated with a device.

[https://ubuntuforums.org/showthread.php?t=1314693](https://ubuntuforums.org/showthread.php?t=1314693)

We know that your computer can detect your Geforce 930M and that you are able to install the nVidia drivers successfully. I also checked the nVidia drivers page and they support Geforce 930M, especially in 384.90. So the problem is that the computer can't associate the new drivers with the video card for whatever reason.

Are you blacklisting any nVidia drivers? Navigate to **/etc/modprobe.d/** and look in the directory for any files that have the words "**nvidia**" and "**blacklist**." Run **cat** on the file and paste the output here.

---

### Post by Bashing-om on 2018-01-10
fbio7; Well ..

Here is the thought:
your are booting :
> 
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-104-generic.efi.signed

on trusty (14.04) where this kernel is:
> 
trusty-updates (kernel): Generic Linux kernel image 
3.13.0.137.146: amd64 arm64 armhf i386 ppc64e


That do raise the question that you have the supporting X stack to support the 4.4 kernel .
Let us make it so !

The " vmlinuz-4.4.0-104-generic.efi.signed" indicates this a a EFI system, and as such will require that "secure boot" is disabled in the bios setting .

Once this is done let us consider to install the(H)ard(W)are (E)nablement stack ( HWE) :
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

we need to know how much to install, Do you run a multiarch desktop (for example, i386 and amd64 on amd64, for gaming or Wine), we may find you need a slightly more involved command, to integrate 32 bit softwares .

[INDENT][INDENT]looks reasonable to me
[/INDENT][/INDENT]

---

