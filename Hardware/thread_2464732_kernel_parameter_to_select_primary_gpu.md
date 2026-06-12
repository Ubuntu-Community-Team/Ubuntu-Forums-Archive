---
title: "kernel parameter to select primary gpu"
date: 2021-07-10
forum: Hardware
---

### Post by cryptearth on 2021-07-10
So, as there're a few information required for this topic, I post them upfront:

mainboard: ASUS Crosshair V Formula-Z
gpus: several different cards (doesn't really matter for the question itself)

Question: Are there any kernel options to change the main gpu if the bios/uefi doesn't have an option for it?

This question came up, as my mainboard, although it has 4 physical PCI-E x16 slots, only offers specific lane assignments. To spare you the needs for look it up in the manual itself, I'll post it here.
The board has, from top (nearest to cpu socket) to bottom these 4 pcie slots:

1. fully x16 - PEG slot meant for primary gpu
2. physical x16, electrical x8 - general purpose slot, meant for 3rd gpu in multi-gpu setup
3. physical x16, electrical x16, switches between electrical x16 or only x8 mode depending on if the previous slot is in use - general purpose slot, meant for 2nd gpu in multi-gpu setup
4. physical x16, electrical x4 - general purpose slot - not really meant to be used for a 4th gpu as there's not additional space between this slot and the above, hence it can only be used if there's a single-slot card installed in the above slot

Issue: The bios/uefi doesn't offer any seting to select the primary gpu, it always uses the first gpu found. So, if there's a gpu in the 1st, primary PEG slot, it uses it, no matter what type of gpu it is.
Just out of curiosity I tested what will happen if I not use the PEG slot at all but only populate the other slots: The system uses the first GPU it detects. So, if I only use slots 2 and 3 it still uses the card in slot 2, although that's only meant for a 3rd gpu as it's only x8 electrical. A gpu in slot 3 is only used if the two above are not used at all or if the don't have a gpu in them.

Why this is an issue: As I plan to add a storage controller in the 2nd slot, I'll populate slots 1-3: #1 gpu, #2 storage, #3 gpu.
Why 2 gpus? KVM. I also thought to ask this in the virtualization sub-forum - but as my question is more general I figured to post it here.
Now if I want to passthrough my main gpu I have to install it in another slot than #1. As I want to make use of full x16 (the board is only PCI-E 2.0) I put it into slot #3 and use just a rather simple one in the PEG slot.

If I now add my planed storage controller it'll force a lane split so both it and the 2nd gpu only get 8 lanes each, while the low-end gpu in the PEG slot wastes 12 lanes as it's only a x4 card. But if I switch the gpus around I can't passthrough my main gpu - at least not the way I tried.

So, the question above now comes up: Is there a kernel parameter I can set in grub so it switches over to another gpu if I install my main big beefy full x16 card in the PEG and the low-end one in one of the other slots so I can make use of full 16 lanes and not waste a bunch of them?
As for the KVM: Yes, I already read about the additional requirements to passthrough an already initialized card instead of a "cold" one (a card that's not yet initialized as it's excluded via the vfio drive) - but to get that solved I guess I'll add another thread in the virtualization sub-forum.

Sorry for this rather large post - it's my first time around here - but as mentioned at start: There's a bit of explanation required for my setup and my plans. I'm happy to already got the KVM running at all - it took me quite some work to get there. And although in the beginning it looked like a hardware limitation in fact it really was only a software limitation of the used distro (opensuse leap) - switching over to ubuntu already solved quite a lot of issues I wasn't able to fix using opensuse. So I hope to also fix this last step just with some neat software tricks.
I searched quite a lot about this very specific topic, but pretty much all I was able to dig up on the net either referred to change a seting in bios/uefi (which mine not support) or switch around the cards physical. No topic I read yet gone that deep into switch around the cards logical through kernel options.

---

### Post by MAFoElffen on 2021-07-11
<<Note to Moderators: This thread would be better dealt with, and get more exposure as moved to the Virtualization Section>>

Generically,.. (maybe best, because of the terminology you are using)

Some BIOS and UEFI BIOS settings do deal with what is the primary GPU. and further, the GPU preference order. That depends on the vendor of the board and the BIOS. I have have some hardware motherboards that have, while others don't.

You didn't mention bus and slot numbers, which when you get down to pass-throughs, then that becomes specific.Once KVM starts in the boot process, those specific pass-through deices are assigned as dedicated resources to the hypervisor and is no longer seen as resources to the host. Once that is done, then the host only see's what is left.

It all sorts itself out. It does. I am looking forward to talking to you about this more, a little less generically.

---

### Post by cryptearth on 2021-07-12
I appreciate your reply to that rather specific topic. May let me address it.
> **MAFoElffen said:**
> <<Note to Moderators: This thread would be better dealt with, and get more exposure as moved to the Virtualization Section>>
Well, although I agree with you it's a question along with my virtualization setup, in my opinion it's not specific to it. To switch around the preference order of extension cards isn't a virtualization topic but fit into general hardware no matter its overall use in a KVM setup. In fact: If I would haven't mentioned the reason "to use the correct card in a KVM" it won't has any relation to virtualization. Hence I chose the hardware sub-forum instead of the virtualization sub-forum to hopefully get more users to at least read my question. But it's up to the mods to maybe decide else otherwise.
> **MAFoElffen said:**
> Generically,.. (maybe best, because of the terminology you are using)

Some BIOS and UEFI BIOS settings do deal with what is the primary GPU. and further, the GPU preference order. That depends on the vendor of the board and the BIOS. I have have some hardware motherboards that have, while others don't.
Well, I've clearly mentioned that my specific hardware does not offer such option. It only offers an option to prioritize PCI cards over PCI-E ones, but as this board doesn't has any regular PCI slots let me quote a reply in the asus forums:
> It seems to result from laziness by the devs not removing it from the shared codebase also used by other boards which do offer PCI slots
Which to my knowledge is the non-Z variant Crosshair V Formula.
> **MAFoElffen said:**
> You didn't mention bus and slot numbers, which when you get down to pass-throughs, then that becomes specific.Once KVM starts in the boot process, those specific pass-through deices are assigned as dedicated resources to the hypervisor and is no longer seen as resources to the host. Once that is done, then the host only see's what is left.
Well, I explained the number and order of the slots this board has with their relevant details. I'm not sure what additional information you request.
> **MAFoElffen said:**
> It all sorts itself out. It does. I am looking forward to talking to you about this more, a little less generically.
I'm happy to talk about this topuc more in-depth as it's an ongoing project for about the past two years. So there's a lot I'm through and still a bit left to reach my final desired result.

---

### Post by cryptearth on 2021-07-16
[https://www.youtube.com/watch?v=mM7ntkiUoPkSo](https://www.youtube.com/watch?v=mM7ntkiUoPkSo), to get in a reply: I managed to get it working in a way to get the result I desired - although not using some kernel options but switching around the cards.

For some reason to use a nVidia gpu in a KVM it seems that a dump of the vbios is required. To get a dump a 2nd gpu is required (although I still have plans to try to do it without a 2nd gpu ... maybe that's possible, too). Also, I don't know why, to get the dump it's required to initialize the gpu by have it booted up by a kvm. Kind of counterintuitive but for some reason actually required. I tried without and it didn't worked. I tried again after init the gpu in a kvm and it worked.

So, to give a full reply in the same fashion of my initial post:

1) moved my secondary 1030 to the primary PEG slot and the primary 1650 to one of the other slots (in fact it doesn't matter for that step as the performance doesn't matter but only that the gpu is present - I guess it's also possible using a simple x1 slot with one of those crypto-miner x1-to-x16 adapters)
2) booted the host using the 1030 in the primary PEG and with the required vfio-pci.ids set to ignore the 1650
3) setup some random kvm - I used win10 as it's planed as the final guest os anyway
3a) I set up the kvm without passthrough to get the guest os running - then added the passthrough gpu - installed the driver - restarted - and got the known error43 - which, at this step, is perfectly fine and intended - all this temp kvm is for is to init the gpu
4) followed this YT guide: [https://www.youtube.com/watch?v=mM7ntkiUoPk](https://www.youtube.com/watch?v=mM7ntkiUoPk)
4a) to give you the short gist: after the gpu is initialized by the temp kvm it has to be unbound from the vfio-pci driver, enable access to the rom, dump it, disable the rom access again and rebind it to the vfio-pci driver - in commands this looks like this:
```
lspci -vecho "0000:nn:00.0"  /sys/bus/pci/drivers/vfio-pci/unbind
cd /sys/bus/pci/devices/0000:nn:00.0/
echo 1 > rom
cat rom > /usr/share/qemu/1650.bin
echo 0 > rom
echo "0000:nn:00.0" > /sys/bus/pci/drivers/vfio-pci/bind
```
4b) "nn" is the number of the pci device you get from the lspci command
4c) the dump location /usr/share/qemu is used cause it's in the app-armor profile (along with a few other paths)
5) the important part: added the dumped vbios to the passthrough by modifying the xml and adding
```
<rom file='/usr/share/qemu/1650.bin'/>
```
6) fixed the error43 by add a few lines to the XML - google help you on this
7) booted up the temp kvm again to check if the passthrough now works - NOPE!
7a) as I found on the net: it's required to unbind the used framebuffer (vesa-framebuffer in CSM mode - efi-framebuffer in uefi mode) (tried with video=efifb:off - but that doesn't work properly and makes unbind the framebuffer impossible) by
```
echo efi-framebuffer.0 > /sys/bus/platform/drivers/efi-framebuffer/unbind
```
8) moved the gpus back around (primary 1650 in PEG - secondary 1030 in one of the others - as it's only a x4 card anyway I put it into the bottom x4 slot)
9) booted up the host again - set up a clean KVM
10) FIN

It even works when I remove the 2nd gpu and boot up the kvm by SSH from my notebook (I'll try this way for the initial dump - should work, too).

Why it for some reason not worked right away? Well, I guess I made some mistake - but Ubuntu 21.04 doesn't really play nicely to play around with the hardware. I had to do a full clean re-install of the host OS. Also, as my uefi does something funky depend if CSM is enabled or disabled, and re-install is required anyway when switching between CSM and uefi mode, the issues solved themselfs by the clean re-install of the host os.

So, as I now have the gpu in the primary PEG slot and the secondary 1030 in the x4 slot I have the other two slots available for other cards. As the lsi 9207-8i is a x8 card anyway I plan to install it in the 2nd from top slot which is only a x8 slot anyway. And yes, I'm aware that my system is only a pci-e 2.0 one and the controller and my gpus are pci-e 3.0 cards - and that pci-e 4.0 is already a thing - but hey, if I get the money to upgrade at least I already have cards I can then use up to their full potential.

---

