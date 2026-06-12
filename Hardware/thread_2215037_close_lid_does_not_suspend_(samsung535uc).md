---
title: "close lid does not suspend (samsung535uc)"
date: 2014-04-04
forum: Hardware
---

### Post by Farinet on 2014-04-04
As the title says: Close lid does not suspend. To get suspend working i had to install the latest Catalyst driver, but it only works if i choose suspend either from the logout menu or from the (xfce) powermanagement icon which comes by default with lubuntu. I looked into /etc/systemd/logind.conf where all statements are outcommented by default. I uncommented 'HandleLidSwitch=suspend' and 'LidSwitchIgnoreInhibited=yes' but to no extent.

Beneath some infos about my system (which are given by "inxi -F"; the mac adresses and the hostname are edited by me):

```
System:    Host: noname Kernel: 3.11.0-19-generic x86_64 (64 bit) Desktop: LXDE (Openbox 3.5.2) 
           Distro: Ubuntu 13.10 saucy 
Machine:   System: SAMSUNG product: 535U3C v: P01RAG
           Mobo: SAMSUNG model: SAMSUNG_NP1234567890 v: SEC_SW__1234567890ABCD
           Bios: American Megatrends v: P01RAG.N43.120612.LEO date: 06/12/2012
CPU:       Dual core AMD A6-4455M APU with Radeon HD Graphics (-MCP-) cache: 4096 KB 
           Clock Speeds: 1: 1300 MHz 2: 1300 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Trinity [Radeon HD 7500G]
           Display Server: X.Org 1.14.5 drivers: ati,fglrx (unloaded: fbdev,vesa,radeon)
           Resolution: 1366x768@60.1hz
           GLX Renderer: AMD Radeon HD 7500G GLX Version: 4.3.12798 - CPC 13.35.1005
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel 
           Card-2 Advanced Micro Devices [AMD/ATI] Trinity HDMI Audio Controller driver: snd_hda_intel 
           Sound: Advanced Linux Sound Architecture v: k3.11.0-19-generic
Network:   Card-1: Qualcomm Atheros AR9462 Wireless Network Adapter driver: ath9k 
           IF: wlan0 state: up mac: 00:00:00:00:00:00
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
           IF: eth0 state: down mac: 00:00:00:00:00:00
           Card-3: Atheros 
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 500.1GB (13.4% used) 1: id: /dev/sda model: Hitachi_HTS54505 size: 500.1GB
Partition: ID: / size: 108G used: 63G (62%) fs: ext4 
           ID: swap-1 size: 8.01GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 59.4C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 159 Uptime: 23 min Memory: 1134.5/7380.9MB Client: Shell (bash) inxi: 2.1.13 

```

Thanks a lot in advance for any help.

---

### Post by Lars Noodén on 2014-04-04
Have you looked into the settings for what the XFCE Power Manager does when the laptop lid is closed?  On one version of Lubuntu, I had to manually set it to 'suspend' because the default was other than what I needed.

---

### Post by Farinet on 2014-04-04
Yes, i did (if the settings you mean are those accessible by the gui of  xfce powermanagement). They are set to suspend on close lid (either  working with powersupply or with battery).

PS. The  powermanagement (suspend & hibernate) are a long story with this  machine (as well as with the G4 powerbook) ;-) :-( Hibernate still does  not work for me, fortunately suspend now with the new fglrx driver does.

---

### Post by Farinet on 2014-04-04
Meanwhile, i looked around a bit and i found this in /etc/acpi/events:

fglrx-lid-aticonfig
```
# /etc/acpi/events/fglrx-lid-aticonfig
# Called when the user opens or closes the laptop lid
# 

event=button[ /]lid
action=/etc/acpi/fglrx-powermode.sh

```

and the referred to fglrx-powermode.sh
```
#!/bin/bash 

. /etc/default/xorg-driver-fglrx
if [ x$FGLRX_ACPI_SWITCH_POWERSTATES != xtrue ]; then
  exit;
fi

getXuser() {
        user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`
        if [ x"$user" = x"" ]; then
                user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`
        fi
        if [ x"$user" != x"" ]; then
                userhome=`getent passwd $user | cut -d: -f6`
                export XAUTHORITY=$userhome/.Xauthority
        else
                export XAUTHORITY=""
        fi
}

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]; then
 lid_closed=1
else
 lid_closed=0
fi

grep -q off-line /proc/acpi/ac_adapter/*/state 
if [ $? = 0 ]; then
   on_dc=1
else
   on_dc=0
fi



if [ ${lid_closed} -eq 1 -o ${on_dc} -eq 1 ]; then
    echo "fglrx: setting low power"
    for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"        
        powermode=`/usr/bin/aticonfig --lsp | grep -m1 low | cut -b 3-3`
        if [ x"$powermode" != x"" ]; then
            su $user -c "/usr/bin/aticonfig --set-powerstate=$powermode --effective=now" &>/dev/null
        fi
    fi
    done
else
    echo "fglrx: setting default powermode"
    for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"
        powermode=`/usr/bin/aticonfig --lsp | grep -m1 default | cut -b 3-3`
        if [ x"$powermode" != x"" ]; then
            su $user -c "/usr/bin/aticonfig --set-powerstate=$powermode --effective=now" &>/dev/null
        fi
    fi
    done
fi

```

Now, it's beyond my capabilities to really check the code, but, guessing in the dark: Would it be possible, that these scripts a) overrule xfce powermanagement settings and, that they do not point to suspend on close-lid?

Thanks a lot in advance for your patience!

---

