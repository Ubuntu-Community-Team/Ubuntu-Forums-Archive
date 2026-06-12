---
title: "No wireless on thinkpad T500"
date: 2008-11-01
forum: Hardware
---

### Post by velozoom on 2008-11-01
Running Hardy 64b on a T500.  (Let's not talk about how badly Intrepid hosed my video....upgrading isn't an option until the flgrx driver issue is fixed)  

I've downloaded the Vista driver directly from ibm.com and installed using ndiswrapper.  This is the only driver that works, according to ndisgtk, which installs the driver and shows "Hardware present: Yes."  I tried the XP driver but it's only 32 bit and ndiswrapper complains loudly about it.  

Despite ndiswrapper installing the windows driver, the system will not see the card.  The information in device manager is minimal and generic.  /etc/network/interfaces only shows lo and eth0.  iwconfig only shows "no wireless extensions for those two interfaces.  

I'm definitely not a 'nix expert and would appreeciate some pointers as to where to look.

partial output of dmesg
> [  181.690416] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  181.706538] usbcore: registered new interface driver ndiswrapper
[  192.254419] usbcore: deregistering interface driver ndiswrapper
[  192.269816] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  192.286387] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[  192.286412] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  192.286419] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  192.286426] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  192.286430] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  192.286435] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  192.286439] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  192.286444] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  192.286448] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  192.286454] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  192.286458] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  192.286463] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  192.286472] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[  192.286477] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[  192.286481] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[  192.286501] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  192.286507] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  192.286517] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  192.286521] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCopyFromNetBufferToNetBuffer'
[  192.286525] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  192.286529] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[  192.286534] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  192.286538] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[  192.286542] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  192.286546] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  192.286550] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  192.286555] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  192.286559] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  192.286563] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[  192.286567] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  192.286571] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[  192.286575] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[  192.286579] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[  192.286584] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[  192.286588] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[  192.286592] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  192.286597] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[  192.286603] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5v64'
[  192.289831] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5v64; check system log for messages from 'loadndisdriver'
[  192.294941] usbcore: registered new interface driver ndiswrapper



/var/log/sys simply shows the same info as the dmesg output above

---

### Post by velozoom on 2008-11-02
anyone?  I've been looking hard but haven't found a solution.

Cheers....

---

### Post by kngunn on 2009-01-22
velozoom --

Intrepid works great on the T500 except for occasional problems with locks due to wifi. (I'm NOT using NDIS).

The trick to the video is that the T500 has two video cards attached to one display.  From the BIOS disable the Intel card and the ATI drivers will work fine.

---

### Post by velozoom on 2009-01-22
thx kngunn.  actually sorted that a few weeks ago from a different thread on video issues.  once i was able to upgrade to 8.10, the wireless is working swimmingly

---

### Post by hessam on 2009-02-06
I just installed Intrepid on a Thinkpad T500. I updated it in hope of having Ubuntu detect my wireless but still nothing happened. I even installed **ndiswrapper** through synaptic, but still nothing. How did you guys get wireless to work on your T500s?

**System -> Administration -> Hardware Drivers** shows "Support for Atheros 802.11 wireless LAN cards". But when I type **iwconfig** it says:

> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

