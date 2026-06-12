---
title: "PCMCIA /Hotplug / IRQ Hell!!"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by Seer on 2005-06-22
Instead of steering a useful thread elsewhere offtopic - I'll consolidate my problem here:


> 
OK Here is a new one for yas... I thinK!!!!

Card is the (using latest winxp drivers) Belkin F5D8000 pre-n PCMIA in a PCI Bracket type card (thats a hotplug thing right???) Every thing appears to go swimmingly until the very last part....

A message from that bastard dmesg (he is always bringing me bad news!)


Quote:
ndiswrapper version 1.2 loaded (preempt=yes,smp=no)
ndiswrapper: driver netani (Belkin Software, Inc.,08/11/2004, 1.2.0.68) loaded
PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 19
PCI: Unable to reserve mem region #1:fffea000@fa020000 for device 0000:03:00.0
ndiswrapper (ndiswrapper_add_pci_device:198): couldn't request PCI regions: fffffff0
ndiswrapper: probe of 0000:03:00.0 failed with error -16
PCI: Failed to allocate mem resource #1:80000@fa080000 for 0000:03:00.0
PCI: Failed to allocate mem resource #0:20000@fa020000 for 0000:03:00.0  



For the love of god someone help me :) Its taken me days just to get this far!!! ] (*,)
__________________
^^^^^^^^^^^^^^^^^^^^^^^^^^^
ALL HAIL THE Lin00bie KNOWN AS ME :D 

--------------------------------------------------------------------------------
Last edited by Seer : Yesterday at 11:02 PM.  
        

Seer is Online: 
Join Date: Jun 2005
Location: Manchester, UK
Posts: 12    Re: HOW TO: Configure wireless cards with Broadcom chipsets 

--------------------------------------------------------------------------------

I may have found the source of my problem in a pretty obscure place - I am just not sure how to adapt the instructions to Ubuntu....

I found out this was the Rioch Rl5c475 PCI adapter from the Device Manager, and then I have read alll kinds of problems with other brands of cards using this too. Then I stumbled on this:


Quote:
[http://vprmatrixlinux.theeggbeater.net/](http://vprmatrixlinux.theeggbeater.net/)

Networking
802.11b Wireless Networking
The internal chipset is Mini PCI Orinoco (Ricoh Rl5c475). After working with this I found the following site that shows you how to setup the Ricoh Rl5c475

It is supported via the orinoco driver in PCMCIA-CS. The trick is the chipset is connected via the pci bus to a PCMCIA slot.

Short Install Instructions:
1) compile and install 2.4.x without PCMCIA support but with Wireless LAN support (just Wireless LAN support, none of the drivers under that option)
2) compile and install latest pcmcia-cs (Gentoo: emerge pcmcia-cs)
3) compile and install latest wireless-tools (Gentoo: emerge wireless-tools)
4) edit your pcmcia options so that your socket driver is i82365 and your PCIC_OPTS="irq_mode=0" (use only PCI IRQs) in /etc/conf.d/pcmcia
5) reboot
6) the Ricoh Rl5c475 will be recognized as eth1  




So far I have checked for latest version of pcmcia-cs and wireless tools via synaptic.
Problem is I cannot find 4) edit your pcmcia options so that your socket driver is i82365 and your PCIC_OPTS="irq_mode=0" (use only PCI IRQs) in /etc/conf.d/pcmcia

I know its a different NIC actually in the adapter but the problem is apparently due to the kernel trying to assign the same IRQ twice and is present in both 2.4 and 2.6??
__________________
^^^^^^^^^^^^^^^^^^^^^^^^^^^
ALL HAIL THE Lin00bie KNOWN AS ME :D  


Seer is Online: 
Join Date: Jun 2005
Location: Manchester, UK
Posts: 12    Re: HOW TO: Configure wireless cards with Broadcom chipsets 

--------------------------------------------------------------------------------

Well - the closest I could find was /etc/default/pcmcia which has the exact same layout.... so I followed the instructions (bearing in mind they were for the 2.4 kernel) and produced a file like so:


Quote:
# Defaults for pcmcia (sourced by /etc/init.d/pcmcia)
PCMCIA=yes
PCIC=i82365
PCIC_OPTS="irq_mode=0"
CORE_OPTS=
CARDMGR_OPTS=  



Reboot and no joy ... so then I went and looked at /etc/init.d/pcmcia as referenced at the top of the file and found this little snippet...


Quote:
# Treat i82365 specially, as many people with yenta_socket
# incorrectly has PCIC set to i82365 for historical reasons
if [ "$PCIC" = i82365 ]; then
if ! bridge_module_loaded ; then
# On 2.6 kernels, we must not load any other bridge
# modules than the right one
if cardbus_bridge_present ; then
[ "$VERBOSE" != no ] && log_warning_msg "Using yenta_socket instead of $PCIC"
load_module yenta_socket || failed_to_load yenta_socket  



And bang went my hopes that this week old n00b had figured out something so detailed by himself lol!!!

Really I am going nuts now!!! Sorry for using this post like a journal of my actions but maybe some others with the same card but more knowledge can assist me !!
__________________
^^^^^^^^^^^^^^^^^^^^^^^^^^^
ALL HAIL THE Lin00bie KNOWN AS ME :D  
        

Seer is Online: 
Join Date: Jun 2005
Location: Manchester, UK
Posts: 12    Re: HOW TO: Configure wireless cards with Broadcom chipsets 

--------------------------------------------------------------------------------

I promise my last post... (I'm about to pass out  ) 

I have gone all round the houses reading the documentation and it seems whats needed is this.

You can exclude IRQ's that the Rioch gets assigned to using a file in the /etc/default/pcmcia directory - so in this case I excluded 19. 

Then I found out that this only excludes irqs for the PCI bridge itself and not for the actual card inserted into it. (the problem seeming to be that the machine is attempting to assign the same IRQ to both the PCI Socket and the card inserted into it) For this I presume I would need to exclude the IRQ 19 not with PCMCIA but with the hotplug module with something within the /etc/hotplug directory but I'll be buggered if I can find a file where this is possible.

So if anyone knows a way to exclude an IRQ for the PCMCIA Card that is inserted into the bracket.... I might be on a winner lol 

G'night!!
 

---

### Post by Seer on 2005-06-22
[QUOTE=Seer]Instead of steering a useful thread elsewhere offtopic - I'll consolidate my problem here:[/QUOTE]
 OK I did even more research and now think I am narrowing things down.... I am really just following my nose in a logical manner and hope someone with some knowledge can step in :D

1st I took out the card and rebooted then ran the following diagnostics and pulled out what I think is the relevant parts

**With No Card Inserted**
> 
Dmesg

Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:02:09.0[A] -> GSI 19 (level, low) -> IRQ 19
Yenta: CardBus bridge found at 0000:02:09.0 [0000:0000]
Yenta: ISA IRQ mask 0x0000, PCI irq 19
Socket status: 30000006

lspci -vv

0000:02:09.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at fa005000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: fa006000-fa007000 (prefetchable)
        Memory window 1: fa008000-fa009000
        I/O window 0: 0000a800-0000ac03
        I/O window 1: 0000b000-0000b403
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

cardctl status

Socket 0:
  no card

Now to me everything is looking perfect there right?? So the Rioch PCMCIA>PCI cardbus is happily sat there waiting to be inserted with a card???

Now I reboot with the NIC Card Inserted:

**With Card:**> 

Dmesg

ACPI: PCI interrupt 0000:02:09.0[A] -> GSI 19 (level, low) -> IRQ 19
Yenta: CardBus bridge found at 0000:02:09.0 [0000:0000]
Yenta: ISA IRQ mask 0x0000, PCI irq 19
Socket status: 30000820
PCI: Failed to allocate mem resource #1:80000@fa080000 for 0000:03:00.0
PCI: Failed to allocate mem resource #0:20000@fa020000 for 0000:03:00.0

lspci -vv

0000:02:09.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at fa005000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: fa006000-fa007000 (prefetchable)
        Memory window 1: fa008000-fa009000
        I/O window 0: 0000a800-0000ac03
        I/O window 1: 0000b000-0000b403
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
        16-bit legacy interface ports at 0001


0000:03:00.0 Ethernet controller: Unknown device 17cb:0001 (rev 01)
        Subsystem: Unknown device 17cb:0001
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 19
        Region 0: [virtual] Memory at fa020000 (32-bit, non-prefetchable) [disabled] [size=fffea000]
        Region 1: [virtual] Memory at fa080000 (32-bit, non-prefetchable) [disabled] [size=fff8a000]
        Capabilities: [40] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

cardctl status

Socket 0:
  3.3V CardBus card
  function 0: [ready]

Now my summation of this is that the card is detected, is sat there with power and ready to be used, but the kernel is unable to assign resources to it because it is trying to assign the same IRQ??? 

Now the knowledge folks really need to step in :) I have 40+ favourites on vaguely related topics around the web from all kinds of newsgroups and my brain is ready to implode!!!

---

### Post by Seer on 2005-06-24
Bumpity bump because I cant waste any more time on this....

I spent a good 10 solid hours reading crap everywhere for this and no further on :(

Linux is going to have to leave my machine if something so basic is such a biatch (this card PnP's in windows without even a driver install :/

---

### Post by Seer on 2005-06-27
last punt i promise - didnt get time to resinstall XP this weekend.... so a last gasp suggestion anyone???!

---

