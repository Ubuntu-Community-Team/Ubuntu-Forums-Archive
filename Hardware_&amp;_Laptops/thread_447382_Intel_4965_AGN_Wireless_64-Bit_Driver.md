---
title: "Intel 4965 AGN Wireless 64-Bit Driver"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by venom986 on 2007-05-17
So, after two to three days of fighting to get my wireless working on my Dell 640m with the Intel 4965 miniPCI card in it, I have succeeded.

I have followed the various other posts and HOWTOs on using ndiswrapper with the Intel windows drivers.  I had had no luck until I stumbled across mention of someone trying to get another card to work under 64-bit drivers (I have Core 2 Duo and am running the amd64/eh64t Ubuntu).  I had tried before to install the 64-bit intel driver with ndiswrapper but got error messages.

After some digging and diffing, it turns out that the NETw4x64.INF file from Intel is missing a
header that ndiswrapper wants to see when you install the driver.  If you sdiff NETw4x64.INF with NETw4k32.INF you will see where the header is missing. 

```

;*****************************************
;Device
;-----------------------------------------

;*****************************************
;Device XP64
;-----------------------------------------
[Device.NTamd64.5.2]

; GEN_4965_AGN_C
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_C_XP64_MOW1    ,   PCI\
VEN_8086&DEV_422D&SUBSYS_11008086 ; MOW1

```

 Just edit it into the NETw4x64.INF file and then follow the usual ndiswrapper -i NETwx64.INF etc.

```

;*****************************************
;Device
;-----------------------------------------

;*****************************************
;Device XP64
;-----------------------------------------
[Device.NTamd64.5.2]

[COLOR="Blue"][Device][/COLOR]
; GEN_4965_AGN_C
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_C_XP64_MOW1    ,   PCI\
VEN_8086&DEV_422D&SUBSYS_11008086 ; MOW1

```

YAY!!

---

### Post by axos88 on 2007-07-14
I think there is a typo there. the [Devices] entry should come before the [Devices.WHAT.EVER.TEXT]. (that's how it is in the 32bit version)

Anyhow, i've tried it both ways, and it didn't work for me

---

### Post by Tessian on 2008-01-16
This worked for me! Thanks!!

Now I can't get the wireless to show up as a device AT ALL... but at least now ndiswrapper -l shows present and working.  I did ndiswrapper -m and it says it binded me... but still only eth0 listed.

---

