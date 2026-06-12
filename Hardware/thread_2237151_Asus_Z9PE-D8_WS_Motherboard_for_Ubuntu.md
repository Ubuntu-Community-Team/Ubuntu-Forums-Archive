---
title: "Asus Z9PE-D8 WS Motherboard for Ubuntu?"
date: 2014-07-31
forum: Hardware
---

### Post by cjsmall on 2014-07-31
In the past, a few other users have asked about the compatibility of some of this hardware without receiving any feedback.  I'll give it another try.  :-)

I'm considering building a server/workstation system to run Xubuntu 14.04 with KVM virtualization that will support Windows 7 and possibly other Linux sessions.  The initial hardware configuration will consist of:

Asus Z9PE-D8 WS Motherboard
(2) Xeon E5-2630 v2 CPUs
(2) Dynatron R17 Fan Coolers
Corsair HX850 Watt Power Supply
32 GB 1600 MHz EEC Registered RAM
(2) Sandisk Extreme PRO 960 GB SSD (Raid 1 Mirrored)
(2) Seagate ST3000VN000 3TB NAS Drive (Raid 1 Mirrored)
Nvidia Quadro K4000 GPU
Pioneer BDR-209DBK Blu-Ray/CD/DVD Burner
Rosewill RDCR-11003 3.5" USB3 Flash Card Reader/Writer
Cooler Master Cosmos II Case

It looks like there are system builders out there that will install Ubuntu onto this type of equipment.  Is anyone running a Ubuntu system using any of these components?  Any comments on potential compatibility issues?  Thanks.

---

### Post by cjsmall on 2014-08-01
Nobody running Ubuntu on Xeon E5-2600 chips or using an Asus Z9PE-D8 WS Motherboard?  

Help a fella out!  :-)

---

### Post by tomkk on 2014-08-16
I do, with two 2690 xeons :)

Glad to see that you go down the ECC route, anyway some gotchas: 
- be aware that you actually can get 1866 ecc rams ... so might be good to invest your self there.
- from my experience - disable all the oprom (specially for storage) since those are complete cr*p and make you disks disconnect after few hours of usage or when you pump half terabyte through Marvell sata controller (this controller sucks big time)
- if you got ram that mother board does not recognize in terms of timings straigh away - you're in big trouble, timings that you can set are not all timming that are actually configurable, had this problem with corsair rams ... again a lot of time waisted and data corrupted. And yeah, mother board will NEVER discover what real ram frequency should be so you will have to set it manually.
- in bios - if you don't know what some setting does - leave it alone or disable it !
- don't use on board raid - it's a joke not a raid, you're better of with btrfs !!! or even storing your data on DVD's and leaving those in the sun ;)
- I never got a uefi to work stabily ... but this was some time ago so maybe with newest bios it will actually run OK but I got no time to tinker with asus ineptitude. 
- make sure you have a really good quality PSU ... I mean a really really good quality and 1200W or more otherwise you will have a stability issues. Also ASUS specifies that you need a specific version of ATX 2.xx PSU ... I ignored that and was trying to make system run stability for 3 weak, gave up, went for proper version one but under powered - system run more stable but still was crashing then got my self a 1200W Corsair and it runs ok.
- ensure you got a good flow of air through your case, south bridge gets a lot of beating up with 2 cpu's pumping data through it - under a really proper load it will get red hot and crash (again personal experience).
- built in sound card under linux causes more issues than getting a second job in car wash and investing into a nice sound card like soundblaster etc. 


So bottom line - congrats on buying your self a fantastic bit of kit that got infinite power, zero support from asus and virtually nobody using it so no kernel bugs will be fixed any time soon ;)

---

### Post by tomkk on 2014-08-16
OK, not I've noticed your requirements and concerns (or read again your post):
- mate your single CPU will eat 300 WAT for good morning ... you got not much left for anything else :)
- if it comes to virtualization - it works great ... and silently corupts your data :) (from my experience) jsut be aware that his is a power horse work station, Asus has no market in people running virtual machines on workstations ... folks do it on servers and there they concentrate their debugging powers ... if you want to buy dual lga 2011 mobo of a server class, go with supermicro !!! they now what they are doing and they don't release a half baked bios like asus does.


Now, I'm pretty sure that I'm biased on this, but since I own a second dual cpu mobo from asus I can pretty much state that those mother boards are designed by some pretty awesome hardware engineers and then passed on to bunch of cretins to write bios and oprom ... I mean - two years it took them to give bios version that doen't crash when you set acpi to auto :( previous generation (lga 771 I guess) had to have firewire disabled otherwise it would crash in linux / windows ... and asus replaced it twice so it was not a hardware problem.

So as long as you use it as a power horse - ie two cpu, boat load of ram, a lot of pcie, a lot of discs and NO BELLS AND WHISTLES - you should be 90% fine .............. (disabling rs232 seems to provide some extra stability .. how bad is that !!!).

---

### Post by cjsmall on 2014-08-17
Tomkk:

Thanks you for the replies.  I've got the hardware built.  Now on to the BIOS and installing the OS.  I appreciate the tips regarding the BIOS subsystems.  I do plan to avoid the hardware RAID and so far there have been no issues with memory timing.  I did stick with the 1600 MHz RAM since the Intel spec sheet for the E5-2630 v2 indicates that this is the maximum speed supported and articles that I read on the subject seem to indicate that the system performance difference tends to be relatively small for this particular issue.

Regarding power usage, I read a TweakTown review of a similar system system using two E5-2670 chips that draw 115 W each.  Their system was overclocked and only pulled 422 watts total.  The E5-2630 v2 only draw 80 W each, so I think I should be OK, but I'll keep an eye on the power usage.

I'm sorry to hear about the poor ASUS MB support.  I guess I'll see what my experience is since I'm committed now!

Regards.

---

