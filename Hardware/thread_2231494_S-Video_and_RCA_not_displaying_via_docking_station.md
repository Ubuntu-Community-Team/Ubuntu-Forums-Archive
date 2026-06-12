---
title: "S-Video and RCA not displaying via docking station"
date: 2014-06-26
forum: Hardware
---

### Post by quadrplax on 2014-06-26
Looks like this question has taken me all the way to asking on the forums. I have an HP EliteBook 6930p with an EN488AA docking station. There is no video coming out of either the S-Video or yellow composite ports. I have the docking station connected to the proper power cable (was a problem earlier): the lights come on and most ports work. I've tested the VGA, PS/2, and USB ports and they work. I know it's not a problem with the TV/VCR because I tried connecting it to multiple devices. Ubuntu didn't even recognize when I plugged/unplugged the cables at all. The BiOS doesn't show up at all on the TV either, and Fn+F4 (what they suggested trying in their troubleshooting guide) didn't do anything. Anyone have any idea what's wrong?

[Off topic note to admins: 2-letter tags should be allowed, I couldn't put "HP"]

Edit: Also know that it's not the cable or cable type: I tried S-Video to S-Video, S-Video to RCA, and RCA to RCA

---

### Post by quadrplax on 2014-06-27
Well, here we go again:
Bump #1

---

### Post by quadrplax on 2014-06-28
Bump #2...

---

### Post by quadrplax on 2014-06-30
Bump #3

---

### Post by quadrplax on 2014-07-01
Bump #4

---

### Post by quadrplax on 2014-07-02
Bump #5

---

### Post by sudodus on 2014-07-02
> **quadrplax said:**
> Looks like this question has taken me all the way to asking on the forums. I have an HP EliteBook 6930p with an EN488AA docking station. There is no video coming out of either the S-Video or yellow composite ports. I have the docking station connected to the proper power cable (was a problem earlier): the lights come on and most ports work. I've tested the VGA, PS/2, and USB ports and they work. I know it's not a problem with the TV/VCR because I tried connecting it to multiple devices. Ubuntu didn't even recognize when I plugged/unplugged the cables at all. The BiOS doesn't show up at all on the TV either, and Fn+F4 (what they suggested trying in their troubleshooting guide) didn't do anything. Anyone have any idea what's wrong?

[Off topic note to admins: 2-letter tags should be allowed, I couldn't put "HP"]

Edit: Also know that it's not the cable or cable type: I tried S-Video to S-Video, S-Video to RCA, and RCA to RCA

It seems nobody knows how to help you. Anyway, I can start this process by asking a few questions. Maybe someone can answer at least one of them and give some hints how to continue.

- Is your BIOS up to date (or can you install a newer and debugged version)?

- Should the BIOS screen show up via S-video and RCA?

- Can you check somehow if the docking station is OK using another operating system, for example Windows?

---

### Post by quadrplax on 2014-07-02
Yay, a response!
- I've never updated a BiOS before, this one says it  was ROM Date 12/15/08, suggesting it has never been updated, "68PCD  Ver. F.0E". I don't care if the BiOS shows up or not though.
- I don't know, the Dell BiOS on my old computer does, but this is HP so maybe not.
-  No, if I had a copy of Windows to use then I wouldn't be using Linux. I  might be able to do what I did with my old Windows XP install --  install it on another machine, but have it only work for 30 days. Do you  guys think that's worth the effort?  The only "portable OS" I have is  Ubuntu 12.04, which would probably have the same results. 

Considering  they recommend using Fn+F4 to make it work, it could be that  the ports don't act like a normal additional monitor port. It may be  some special drivers which would hopefully be available on Linux

---

### Post by sudodus on 2014-07-02
- Updating the BIOS might not only make its menus show, but more important, it might help the full OS use S-video and RCA via the docking station.

- Installing Windows XP (without all the upgrading) is an hour or two. It might be worth it, to test if you can send video via those ports of the docking station. If Windows fails, it might be a hardware error (or a buggy BIOS).

- Depending on the graphics chip/card it might be worthwhile to test an installed system of Ubuntu and a proprietary graphics driver. With Intel graphics it should be enough to test with a live session (I think).

Recently I tried S-video in an old IBM Thinkpad T42. It worked out of the box with Lubuntu 14.04 LTS. I used the built in graphics driver, no proprietary driver. But I could not help the original poster. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229607"]No s-video display on Radeon VIVO
[/URL]

---

### Post by quadrplax on 2014-07-02
If you look at [their page for drives]("http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/psi/swdHome?sp4ts.oid=3688870&ac.admitted=1404325833782.876444892.199480143") it lists all modern versions of Windows, but no Linux. I'll try picking my current OS (I work off a Windows 7 desktop for the most part) and try making a Live USB with that, see how that goes. [This]("http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/psi/swdHome/?sp4ts.oid=3688870&spf_p.tpst=swdMain&spf_p.prp_swdMain=wsrp-navigationalState%3DswEnvOID%253D4058%257CswLang%253D%257Caction%253DlistDriver&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken#BIOS") is the BiOS drivers, looks like I should probably try version F.19 because it says "Windows" in version F.20. The two middle versions appear to be identical, so I guess I'll just take the top one. It says (ATI Video Controller), so that's a good sign.

EDIT: I don't see how to run the BiOS updater...
After running the exe file, it extracts SP49258.cva, WSSP49258.rtf and Rom.CAB
The rtf file says to
>        1. Download the SoftPaq .EXE file to a temporary, empty directory on your
          hard drive.
       2. Copy the SoftPaq to the file store.

I don't have a SoftPaq.EXE file anyehere...
Rom.CAB contains:
efibios.sig, Rom.bin, Rom.sig, ver.sig, and ver.txt

Am I supposed to download the ROMPaq version of the BiOS instead? I guess in the meantime I can try XP

EDIT2: While in a 12.04.4 Live CD, resizing partitions for the XP install, an Additional Drivers dialog popped up, showing two "Video driver for the AMD graphics accelerators". These never showed up in the main 14.04 install. Curious, I tried to activate one, and it said the installation failed, and referred me to "/var/log/jockey.log". The other seemingly identical driver had the same results. Here is jockey.log:
```
2014-07-02 18:55:31,953 DEBUG: Comparing 3.11.0-15 with 
2014-07-02 18:55:32,216 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c>
2014-07-02 18:55:32,581 DEBUG: reading modalias file /lib/modules/3.11.0-15-generic/modules.alias
2014-07-02 18:55:32,708 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2014-07-02 18:55:32,709 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2014-07-02 18:55:32,760 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2014-07-02 18:55:32,771 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2014-07-02 18:55:32,785 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2014-07-02 18:55:32,786 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2014-07-02 18:55:32,786 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2014-07-02 18:55:32,794 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2014-07-02 18:55:33,119 DEBUG: Could not instantiate Handler subclass __builtin__.CdvDriver from name CdvDriver
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/cdv.py", line 29, in __init__
    rationale=_('This driver is required to fully utilise the 3D '
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:33,120 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2014-07-02 18:55:33,145 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 214, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package linux-firmware-nonfree does not exist
2014-07-02 18:55:33,146 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2014-07-02 18:55:33,151 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12

2014-07-02 18:55:33,446 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverExperimental12 from name FglrxDriverExperimental12
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/fglrx.py", line 275, in __init__
    FglrxDriver.__init__(self, backend, 'fglrx-experimental-12')
  File "/usr/share/jockey/handlers/fglrx.py", line 42, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:33,449 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2014-07-02 18:55:33,748 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/fglrx.py", line 267, in __init__
    FglrxDriver.__init__(self, backend, 'fglrx-updates')
  File "/usr/share/jockey/handlers/fglrx.py", line 42, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:33,752 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2014-07-02 18:55:34,067 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/fglrx.py", line 271, in __init__
    FglrxDriver.__init__(self, backend, 'fglrx-experimental-9')
  File "/usr/share/jockey/handlers/fglrx.py", line 42, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:34,070 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2014-07-02 18:55:34,385 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverHybrid from name FglrxDriverHybrid
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/fglrx.py", line 191, in __init__
    FglrxDriver.__init__(self, backend, package)
  File "/usr/share/jockey/handlers/fglrx.py", line 42, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:34,388 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2014-07-02 18:55:34,693 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriver from name FglrxDriver
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/fglrx.py", line 42, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:34,696 WARNING: modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13

2014-07-02 18:55:34,988 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverExperimental13 from name FglrxDriverExperimental13
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/fglrx.py", line 279, in __init__
    FglrxDriverHybrid.__init__(self, backend, 'fglrx-experimental-13')
  File "/usr/share/jockey/handlers/fglrx.py", line 191, in __init__
    FglrxDriver.__init__(self, backend, package)
  File "/usr/share/jockey/handlers/fglrx.py", line 42, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:34,988 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2014-07-02 18:55:34,993 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2014-07-02 18:55:34,994 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2014-07-02 18:55:34,994 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2014-07-02 18:55:34,994 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2014-07-02 18:55:35,004 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304

2014-07-02 18:55:35,293 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver304 from name NvidiaDriver304
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 299, in __init__
    _NvidiaDriverBase.__init__(self, backend, '304')
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:35,296 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates

2014-07-02 18:55:35,591 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver304Updates from name NvidiaDriver304Updates
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 303, in __init__
    _NvidiaDriverBase.__init__(self, backend, '304-updates')
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:35,595 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2014-07-02 18:55:35,887 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 311, in __init__
    _NvidiaDriverBase.__init__(self, backend, 'experimental-304')
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:35,890 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2014-07-02 18:55:36,177 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 315, in __init__
    _NvidiaDriverBase.__init__(self, backend, 'current')
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:36,180 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2014-07-02 18:55:36,467 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 319, in __init__
    _NvidiaDriverBase.__init__(self, backend, 'current-updates')
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:36,470 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319

2014-07-02 18:55:36,760 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver319 from name NvidiaDriver319
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 291, in __init__
    _NvidiaDriverHybridBase.__init__(self, backend, '319')
  File "/usr/share/jockey/handlers/nvidia.py", line 210, in __init__
    _NvidiaDriverBase.__init__(self, backend, version)
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:36,763 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2014-07-02 18:55:37,052 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 323, in __init__
    _NvidiaDriverBase.__init__(self, backend, '173')
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:37,055 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2014-07-02 18:55:37,347 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 327, in __init__
    _NvidiaDriverBase.__init__(self, backend, '173-updates')
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:37,350 WARNING: modinfo for module nvidia_331 failed: ERROR: modinfo: could not find module nvidia_331

2014-07-02 18:55:37,642 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver331 from name NvidiaDriver331
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 283, in __init__
    _NvidiaDriverHybridBase.__init__(self, backend, '331')
  File "/usr/share/jockey/handlers/nvidia.py", line 210, in __init__
    _NvidiaDriverBase.__init__(self, backend, version)
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:37,645 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2014-07-02 18:55:37,936 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 307, in __init__
    _NvidiaDriverBase.__init__(self, backend, 'experimental-310')
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:37,940 WARNING: modinfo for module nvidia_319_updates failed: ERROR: modinfo: could not find module nvidia_319_updates

2014-07-02 18:55:38,253 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver319Updates from name NvidiaDriver319Updates
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 295, in __init__
    _NvidiaDriverHybridBase.__init__(self, backend, '319-updates')
  File "/usr/share/jockey/handlers/nvidia.py", line 210, in __init__
    _NvidiaDriverBase.__init__(self, backend, version)
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:38,260 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2014-07-02 18:55:38,569 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 331, in __init__
    _NvidiaDriverBase.__init__(self, backend, '96')
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:38,572 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2014-07-02 18:55:38,879 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 346, in __init__
    _NvidiaDriverBase.__init__(self, backend, '96-updates')
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:38,883 WARNING: modinfo for module nvidia_331_updates failed: ERROR: modinfo: could not find module nvidia_331_updates

2014-07-02 18:55:39,193 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver331Updates from name NvidiaDriver331Updates
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 287, in __init__
    _NvidiaDriverHybridBase.__init__(self, backend, '331-updates')
  File "/usr/share/jockey/handlers/nvidia.py", line 210, in __init__
    _NvidiaDriverBase.__init__(self, backend, version)
  File "/usr/share/jockey/handlers/nvidia.py", line 47, in __init__
    rationale=rationale)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:39,194 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2014-07-02 18:55:39,199 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2014-07-02 18:55:39,563 DEBUG: Could not instantiate Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 971, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/pvr-omap4.py", line 105, in __init__
    rationale=_('This driver is required to fully utilise the 3D '
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 87, in __init__
    fake_apt_cache=fake_apt_cache)
  File "/usr/lib/python2.7/dist-packages/jockey/xorg_driver.py", line 316, in _supports_hybrid_gfx
    int(OSLib.inst.current_xorg_video_abi().split('-')[-1]))
AttributeError: 'NoneType' object has no attribute 'split'
2014-07-02 18:55:39,564 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2014-07-02 18:55:39,577 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2014-07-02 18:55:39,587 DEBUG: Software modem not available
2014-07-02 18:55:39,588 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2014-07-02 18:55:39,596 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2014-07-02 18:55:39,596 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2014-07-02 18:55:39,614 DEBUG: VMWare Client Tools not available
2014-07-02 18:55:39,614 DEBUG: all custom handlers loaded
2014-07-02 18:55:39,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:LNXCPU:')
2014-07-02 18:55:39,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2014-07-02 18:55:40,019 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-07-02 18:55:40,092 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,093 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-07-02 18:55:40,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0C0F:')
2014-07-02 18:55:40,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2014-07-02 18:55:40,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0303:')
2014-07-02 18:55:40,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030DCbc08sc05i00')
2014-07-02 18:55:40,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2014-07-02 18:55:40,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2014-07-02 18:55:40,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'platform:lis3lv02d')
2014-07-02 18:55:40,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2014-07-02 18:55:40,103 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-07-02 18:55:40,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,103 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2014-07-02 18:55:40,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'usb:v08FFp2810d1703dcFFdscFFdpFFicFFiscFFipFFin00')
2014-07-02 18:55:40,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0311dc09dsc00dp00ic09isc00ip00in00')
2014-07-02 18:55:40,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:IFX0102:PNP0C31:')
2014-07-02 18:55:40,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2014-07-02 18:55:40,122 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-07-02 18:55:40,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,122 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-07-02 18:55:40,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'platform:regulatory')
2014-07-02 18:55:40,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:8F1F6435-9F42-42C8-BADC-0E9424F20C9A')
2014-07-02 18:55:40,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2014-07-02 18:55:40,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:INT0800:')
2014-07-02 18:55:40,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'platform:eisa')
2014-07-02 18:55:40,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d0000292Dsv0000103Csd000030DCbc01sc01i85')
2014-07-02 18:55:40,128 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_acpi'}
2014-07-02 18:55:40,129 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_acpi', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'platform:iTCO_wdt')
2014-07-02 18:55:40,130 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2014-07-02 18:55:40,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:2D114B49-2DFB-4130-B8FE-4A3C09E75133')
2014-07-02 18:55:40,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:322F2028-0F84-4901-988E-015176049E2D')
2014-07-02 18:55:40,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2014-07-02 18:55:40,141 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2014-07-02 18:55:40,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,142 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2014-07-02 18:55:40,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd000030DCbc04sc03i00')
2014-07-02 18:55:40,150 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2014-07-02 18:55:40,150 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,150 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2014-07-02 18:55:40,151 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,151 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:HPQ0006:')
2014-07-02 18:55:40,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0A08:PNP0A03:')
2014-07-02 18:55:40,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0A06:')
2014-07-02 18:55:40,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0200:')
2014-07-02 18:55:40,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00004236sv00008086sd00001011bc02sc80i00')
2014-07-02 18:55:40,163 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi'}
2014-07-02 18:55:40,163 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0000:')
2014-07-02 18:55:40,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2014-07-02 18:55:40,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pcmcia:m0000c0000fFEfn00pfn00paD9F522EDpbB8DD2C87pc00000000pd00000000')
2014-07-02 18:55:40,437 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_pcmcia'}
2014-07-02 18:55:40,437 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_pcmcia', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2014-07-02 18:55:40,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2014-07-02 18:55:40,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2014-07-02 18:55:40,438 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2014-07-02 18:55:40,438 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2014-07-02 18:55:40,438 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-07-02 18:55:40,438 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,438 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-07-02 18:55:40,438 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030DCbc0Csc00i10')
2014-07-02 18:55:40,439 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2014-07-02 18:55:40,439 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:DF4E63B6-3BBC-4858-9737-C74F82F821F3')
2014-07-02 18:55:40,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00001002d000095C4sv0000103Csd000030DCbc03sc00i00')
2014-07-02 18:55:40,787 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2014-07-02 18:55:40,790 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2014-07-02 18:55:40,804 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2014-07-02 18:55:40,804 DEBUG: got handler kmod:fglrx_updates([KernelModuleHandler, nonfree, disabled] Video driver for the AMD graphics accelerators)
2014-07-02 18:55:40,805 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2014-07-02 18:55:40,807 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2014-07-02 18:55:40,821 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2014-07-02 18:55:40,821 DEBUG: got handler kmod:fglrx([KernelModuleHandler, nonfree, disabled] Video driver for the AMD graphics accelerators)
2014-07-02 18:55:40,821 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2014-07-02 18:55:40,821 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr68PCDVer.F.0E:bd12/15/2008:svnHewlett-Packard:pnHPEliteBook6930p:pvrF.0E:rvnHewlett-Packard:rn30DC:rvrKBCVersion87.22:cvnHewlett-Packard:ct10:cvr:')
2014-07-02 18:55:40,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:8F1F6436-9F42-42C8-BADC-0E9424F20C9A')
2014-07-02 18:55:40,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d000010F5sv0000103Csd000030DCbc02sc00i00')
2014-07-02 18:55:40,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000e'}
2014-07-02 18:55:40,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000e', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:988D08E3-68F4-4C35-AF3E-6A1B8106F83C')
2014-07-02 18:55:40,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2014-07-02 18:55:40,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-07-02 18:55:40,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2014-07-02 18:55:40,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2014-07-02 18:55:40,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-07-02 18:55:40,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2014-07-02 18:55:40,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0311dc09dsc00dp00ic09isc00ip00in00')
2014-07-02 18:55:40,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'usb:v090Cp1000d1100dc00dsc00dp00ic08isc06ip50in00')
2014-07-02 18:55:40,841 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2014-07-02 18:55:40,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2014-07-02 18:55:40,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00001180d00000476sv0000103Csd000030DCbc06sc07i00')
2014-07-02 18:55:40,841 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket'}
2014-07-02 18:55:40,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,841 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket'}
2014-07-02 18:55:40,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2014-07-02 18:55:40,842 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-07-02 18:55:40,842 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,842 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-07-02 18:55:40,842 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002A44sv0000103Csd000030DCbc07sc80i00')
2014-07-02 18:55:40,846 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei_me'}
2014-07-02 18:55:40,846 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei_me', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,846 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2014-07-02 18:55:40,846 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2014-07-02 18:55:40,846 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd000030DCbc06sc00i00')
2014-07-02 18:55:40,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0100:')
2014-07-02 18:55:40,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:LNXPOWER:')
2014-07-02 18:55:40,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002917sv0000103Csd000030DCbc06sc01i00')
2014-07-02 18:55:40,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2014-07-02 18:55:40,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2014-07-02 18:55:40,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:7391A661-223A-47DB-A77A-7BE84C60822D')
2014-07-02 18:55:40,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002A46sv0000103Csd000030DCbc01sc01i85')
2014-07-02 18:55:40,858 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_acpi'}
2014-07-02 18:55:40,858 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_acpi', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,858 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:1F4C91EB-DC5C-460B-951D-C7CB9B4B8D5E')
2014-07-02 18:55:40,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'pci:v00008086d00002928sv0000103Csd000030DCbc01sc01i8a')
2014-07-02 18:55:40,862 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_acpi'}
2014-07-02 18:55:40,862 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_acpi', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'platform:pcspkr')
2014-07-02 18:55:40,863 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2014-07-02 18:55:40,863 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,863 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2014-07-02 18:55:40,863 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:SYN0147:SYN0100:SYN0002:PNP0F13:')
2014-07-02 18:55:40,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2014-07-02 18:55:40,864 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2014-07-02 18:55:40,864 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:0017:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003D,0066,0068,006B,006C,006D,0072,0075,007C,0080,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0093,00C0,00E7,0100,0101,0102')
2014-07-02 18:55:40,873 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2014-07-02 18:55:40,873 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,873 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2014-07-02 18:55:40,874 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,874 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2014-07-02 18:55:40,874 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:14EA9746-CE1F-4098-A0E0-7045CB4DA745')
2014-07-02 18:55:40,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2014-07-02 18:55:40,874 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-07-02 18:55:40,874 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,874 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-07-02 18:55:40,874 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:8232DE3D-663D-4327-A8F4-E293ADB9BF05')
2014-07-02 18:55:40,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'acpi:PNP0401:')
2014-07-02 18:55:40,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2014-07-02 18:55:40,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1A9,1D1,ram4,l0,1,2,sfw')
2014-07-02 18:55:40,875 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-07-02 18:55:40,875 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,875 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-07-02 18:55:40,875 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2014-07-02 18:55:40,875 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-07-02 18:55:40,875 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-07-02 18:55:40,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9748b0c> about HardwareID('modalias', 'wmi:2B814318-4BE8-4707-9D84-A190A859B5D0')
2014-07-02 18:55:40,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:LNXCPU:')
2014-07-02 18:55:40,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0C0F:')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0C04:')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0303:')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030DCbc08sc05i00')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'platform:lis3lv02d')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'usb:v08FFp2810d1703dcFFdscFFdpFFicFFiscFFipFFin00')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'usb:v1D6Bp0002d0311dc09dsc00dp00ic09isc00ip00in00')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:IFX0102:PNP0C31:')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'platform:regulatory')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:8F1F6435-9F42-42C8-BADC-0E9424F20C9A')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:INT0800:')
2014-07-02 18:55:40,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'platform:eisa')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d0000292Dsv0000103Csd000030DCbc01sc01i85')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'platform:iTCO_wdt')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:2D114B49-2DFB-4130-B8FE-4A3C09E75133')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:322F2028-0F84-4901-988E-015176049E2D')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd000030DCbc04sc03i00')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:HPQ0006:')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0A08:PNP0A03:')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd000030DCbc0Csc03i00')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0A06:')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0200:')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00004236sv00008086sd00001011bc02sc80i00')
2014-07-02 18:55:40,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0000:')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pcmcia:m0000c0000fFEfn00pfn00paD9F522EDpbB8DD2C87pc00000000pd00000000')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0C02:')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030DCbc0Csc00i10')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:DF4E63B6-3BBC-4858-9737-C74F82F821F3')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00001002d000095C4sv0000103Csd000030DCbc03sc00i00')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr68PCDVer.F.0E:bd12/15/2008:svnHewlett-Packard:pnHPEliteBook6930p:pvrF.0E:rvnHewlett-Packard:rn30DC:rvrKBCVersion87.22:cvnHewlett-Packard:ct10:cvr:')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:8F1F6436-9F42-42C8-BADC-0E9424F20C9A')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d000010F5sv0000103Csd000030DCbc02sc00i00')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:988D08E3-68F4-4C35-AF3E-6A1B8106F83C')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0C32:')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'usb:v1D6Bp0001d0311dc09dsc00dp00ic09isc00ip00in00')
2014-07-02 18:55:40,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'usb:v090Cp1000d1100dc00dsc00dp00ic08isc06ip50in00')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00001180d00000476sv0000103Csd000030DCbc06sc07i00')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002A44sv0000103Csd000030DCbc07sc80i00')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0B00:')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd000030DCbc06sc00i00')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0100:')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:LNXPOWER:')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002917sv0000103Csd000030DCbc06sc01i00')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:7391A661-223A-47DB-A77A-7BE84C60822D')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002A46sv0000103Csd000030DCbc01sc01i85')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:1F4C91EB-DC5C-460B-951D-C7CB9B4B8D5E')
2014-07-02 18:55:40,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'pci:v00008086d00002928sv0000103Csd000030DCbc01sc01i8a')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'platform:pcspkr')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:SYN0147:SYN0100:SYN0002:PNP0F13:')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:0017:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003D,0066,0068,006B,006C,006D,0072,0075,007C,0080,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0093,00C0,00E7,0100,0101,0102')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:14EA9746-CE1F-4098-A0E0-7045CB4DA745')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:8232DE3D-663D-4327-A8F4-E293ADB9BF05')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'acpi:PNP0401:')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1A9,1D1,ram4,l0,1,2,sfw')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2014-07-02 18:55:40,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9748b2c> about HardwareID('modalias', 'wmi:2B814318-4BE8-4707-9D84-A190A859B5D0')
2014-07-02 18:55:40,902 DEBUG: handler kmod:fglrx previously unseen
2014-07-02 18:55:40,902 DEBUG: handler kmod:fglrx_updates previously unseen
2014-07-02 18:55:40,902 DEBUG: writing back check cache /var/cache/jockey/check
2014-07-02 18:57:46,812 DEBUG: Installing package: fglrx
2014-07-02 18:57:46,951 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6572L> 0.000000
2014-07-02 18:57:46,954 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6572L> 0.000000
2014-07-02 18:57:47,022 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6572L> 0.000002
2014-07-02 18:57:47,022 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6572L> 0.000002
2014-07-02 18:57:47,028 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6572L> 0.000003
2014-07-02 18:57:47,029 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6572L> 0.000003
2014-07-02 18:57:47,036 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6572L> 0.000005
2014-07-02 18:57:47,036 ERROR: Package fetching failed: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-23_3.2.0-23.36_all.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-23-generic_3.2.0-23.36_i386.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.2.0.23.25_i386.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx_8.960-0ubuntu1_i386.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.960-0ubuntu1_i386.deb Could not resolve 'archive.ubuntu.com'

2014-07-02 18:57:47,171 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2014-07-02 18:57:47,172 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2014-07-02 18:58:49,432 DEBUG: Installing package: fglrx-updates
2014-07-02 18:58:49,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12334L> 0.000000
2014-07-02 18:58:49,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12334L> 0.000000
2014-07-02 18:58:49,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12334L> 0.000002
2014-07-02 18:58:49,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12334L> 0.000002
2014-07-02 18:58:49,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12334L> 0.000003
2014-07-02 18:58:49,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12334L> 0.000003
2014-07-02 18:58:49,641 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12334L> 0.000005
2014-07-02 18:58:49,642 ERROR: Package fetching failed: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-23_3.2.0-23.36_all.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-23-generic_3.2.0-23.36_i386.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.2.0.23.25_i386.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer-updates/fglrx-updates_8.960-0ubuntu1_i386.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer-updates/fglrx-amdcccle-updates_8.960-0ubuntu1_i386.deb Could not resolve 'archive.ubuntu.com'

2014-07-02 18:58:49,779 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2014-07-02 18:58:49,780 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver


```

---

### Post by sudodus on 2014-07-02
Windows is made such that it does not boot from USB.

If there is an ATI graphics chip/card, and you are lucky, it might work with Ubuntu 12.04 LTS and a proprietary driver. But many old cards are no longer supported with linux drivers by ATI/Radeon/AMD.

---

### Post by quadrplax on 2014-07-02
I know that, I'm installing XP to a hard drive partition. The computer itself has 14.04, but I needed to downgrade my Live CD to 12.04 to get it to boot on an old computer, and have not had a reason to move it back up to 14.04 yet. Come to think of it, I don't know what graphics card the computer has. I will check when XP is done.

---

### Post by sudodus on 2014-07-02
> **quadrplax said:**
> ...
EDIT: I don't see how to run the BiOS updater...
After running the exe file, it extracts SP49258.cva, WSSP49258.rtf and Rom.CAB
The rtf file says to

I don't have a SoftPaq.EXE file anyehere...
Rom.CAB contains:
efibios.sig, Rom.bin, Rom.sig, ver.sig, and ver.txt

Am I supposed to download the ROMPaq version of the BiOS instead? I guess in the meantime I can try XP

It might work better once Windows is running. Otherwise you might need some kind of DOS to flash the BIOS.
> 
EDIT2: While in a 12.04.4 Live CD, resizing partitions for the XP install, an Additional Drivers dialog popped up, showing two "Video driver for the AMD graphics accelerators". These never showed up in the main 14.04 install. Curious, I tried to activate one, and it said the installation failed, and referred me to "/var/log/jockey.log". The other seemingly identical driver had the same results. 

I'm not good at reading such logs. Maybe the 'Video driver for the AMD graphics accelerators' will work better in an ***installed*** 12.04 system (after rebooting).

---

### Post by quadrplax on 2014-07-02
Ok, XP finished. I can't set the resolution to anything but 800x600 and 1024x768. XP does not know what the display driver is and calls it "VgaSave" of type "Non-Plug and Play Drivers". I tried looking in System Info and Device Manger a bit, could not find any specific graphics driver anywhere. There's also a chance it's integrated, as I said I don't know.

---

### Post by sudodus on 2014-07-02
And what about S-video and RCA with Windows?

---

### Post by quadrplax on 2014-07-02
Well I guess I should test that, but I highly doubt it will work since XP doesn't even know what graphics card it has or let me adjust the resolution above 1024x768...OK yeah, didn't work as expected. For the video driver thing, are you saying I also need to put Ubuntu _12_.04 on the laptop, it has 14.04 right now. This laptop is going to have so many operating systems on it...lol. I would try to update the BiOS from windows. The problem is, what am I supposed to do? It doesn't look like any of those files are executable.

---

### Post by sudodus on 2014-07-02
I think it is more likely that S-video and RCA will work with 12.04 LTS, since it is identifying the graphics chip and offering proprietary drivers for it, which I think was not the case with 14.04 LTS.

But if there is something else that makes 14.04 LTS better, and you prefer it instead of 12.04 LTS ...

Anyway, I suggest that you keep Windows at least long enough to try to install a new BIOS (and after that check if S-video and RCA will work). If you can't find a better graphics driver, I'd suggest that you remove Windows after that exercise. Read whatever documentation you can find about the BIOS updating: among the files you have downloaded, at the website, where you found it, or browse the internet to find some description, explanation or tutorial. Maybe you should simply find the correct image file and flash it. That image file is not an exe file, but the tool to select and flash it might be an exe file or a batch file (bat).

-o-

We must also consider the possibility that there is some bad hardware that stops S-video and RCA from working.

---

### Post by quadrplax on 2014-07-02
Ok, I'm trying to find out what display driver I need, but I can't find  what graphics card the laptop has anywhere in XP. I'm going to repair  GRUB and poke around for it in Ubuntu.

Edit: Dumb reason the driver installation failed before: I wasn't connected to the internet before. *facepalm* The driver installation still failed though, it just made some progress on downloading now, about halfway. On the other hand, now I can't seem to re-install GRUB. If I do "sudo grub-install /dev/sda" it says
```
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
```
I tried the yannubuntu/boot-repair, but it failes on the "sudo sed" command
Does the LiveCD need to be the same version as the installed OS?

EDIT: Got grub working, but it says two or three "error: file not found" messages followed by "press any key to continue" before booting to Ubuntu. This is what Ubuntu calls my graphics: "Gallium 0.4 on AMD RV620", and lspci yields:
```
VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470]
```

---

### Post by squakie on 2014-07-02
If you have an internet connection while booted in Ubuntu, do the following:

sudo apt-get remove fglrx <press enter>

If it says not found it's ok.

sudo apt-get install fglrx-updates <press enter>

I believe your video card is support in the updates driver.  The install should fix that.

After you have done that install, try your dock again.

---

### Post by squakie on 2014-07-03
Also, just boot up ubuntu - including from a live media - then:

open a terminal window via ctrl/alt/F1

log in with your normal userid and password - note that nothing is echoed to the screen when you enter your password

type:

lspci | grep VGA <press enter>

Post the output back here.  That is your video adapter.

---

### Post by quadrplax on 2014-07-03
Ok, I did the fglrx thing and rebooted. Upon rebooting, for a split second it showed a ttyX terminal, then went to normal login screen, only it was at a very low resolution. When I tried to log in, the log in box disappeared and it just stayed on the screen showing my logon screen/desktop background. I could access the Ctrl+Alt+F1 terminal, and could log in there. I tried "xrandr" and it said "Can't open display". The lspci command gave me the same results as before however.

---

### Post by squakie on 2014-07-03
Hummmmmmm.........

If you haven't already, do back to that text screen and do the following:

sudo apt-get remove fglrx-updates <press enter>

that will back out that driver.  I'm a little surprised that didn't work.  Sorry.

Also - you didn't post back the output from the lspci | grep VGA

I'm thinking at this point you should just follow what sudodus recommended.  I really though this was going to work

BTW - did you ever install just the fglrx (not fglrx-updates) driver?

---

### Post by quadrplax on 2014-07-03
As I said, this is the lspci from a previous post, it's still the same:
> VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470]
I only ran the commands you asked me to run, so no, I didn't install fglrx. Seeing that you were saying "<press enter>" I assumed you were telling me exactly what to do. After removing the updates I could get normal resolutions and log in properly, so now I can connect to the internet to download or whatever.

---

### Post by squakie on 2014-07-03
Have you read [this]("http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html") ?  It includes 14.04.

---

### Post by quadrplax on 2014-07-03
That article doesn't say how to install the drivers and can't seem to find my xorg.conf file anywhere or create one with "Xorg -configure"

---

### Post by quadrplax on 2014-07-04
I did "sudo apt-get install fglrx" and it did the can't log in low resolution thing still too (I removed it already)

---

### Post by squakie on 2014-07-04
Do what the online man page  I pointed you to says.  You need to:

- use the package manager and check that the following is installed:

xserver-xorg-video-radeon

If it isn't - install it.  This IS the AMD/ATI Radeon driver for your chipset.  If you read the start of that online man page, it says so.

Next:

via a terminal:

ls /etc/X11/xorg.conf

Does it exist??  If so:

[COLOR=#b22222][B]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-original
[/B][/COLOR]

[COLOR=#ff0000]**EDIT:  REVISED INSTRUCTIONS:**[/COLOR][COLOR=#b22222][B]

sudo gedit /etc/X11/xorg.conf

make the entire file look like this:

Section "Device"
    Identifier  "Card0"
    Driver      "radeon"
EndSection

Save the file and then reboot.

What I don't know at this time:

- if there are any other requirements in that section to identify the device - like pci-id
- all the other options mentioned in the online man page I linked to[/B][/COLOR][COLOR=#000000]
I'm not sure if that syntax is correct by any means, but try it.  Also, check in /usr/share/xorg.conf.d folder and see if there is a file beginning with 20- that sounds like your video.  If there is, use sudo gedit to edit that file and change/add the [/COLOR]**[COLOR=#b22222]Driver "radeon" [/COLOR]**[COLOR=#000000]  , then sudo rm /etc/X11/xorg.conf and reboot.

It make take more work to get this to work, as I haven't messed with xorg.conf for several releases now.  Hang in there - we'll all find some way to hopefully make this work.[/COLOR]

---

### Post by quadrplax on 2014-07-04
Give me a break, I'm not much of an Ubuntu guy and haven't ever used the  online manual. Anyway, the package is already installed. No,   /etc/X11/xorg.conf does not exist. I rebooted with the settings you  suggested (not connected to the docking station, if that matters).  "xrandr" shows a DVI-0, and there is no DVI port on the laptop itself,  only the docking station, so that's a good sign.I tried adding
```
ForceTVOut "true"
```
This  made there be nothing on the laptop or TV screen after the "ubuntu"  screen, bad sign. Had to edit xorg.conf with a LiveUSB to fix it. While  in there, it asked me for the AMD Drivers again, and again it failed.

It  could be that HP used something non-standard for the S-Video and RCA  ports, requiring their special modified version of the driver to work.  In the XP install, I tried to install the AMD provided driver and it  failed. The HP one only works for Vista+, which makes since because  that's what this laptop was designed for and originally came with.

---

### Post by sudodus on 2014-07-04
> **quadrplax said:**
> Give me a break, ...

It  could be that HP used something non-standard for the S-Video and RCA  ports, requiring their special modified version of the driver to work.  In the XP install, I tried to install the AMD provided driver and it  failed. The HP one only works for Vista+, which makes since because  that's what this laptop was designed for and originally came with.

You may be right about something non-standard. Anyway, you have tried hard, and deserve a break. Maybe some good idea will pop up ...

---

### Post by squakie on 2014-07-04
Yep - I'm out of ideas from the net and from the Ubuntu online man pages.  Was just trying to help.  Sorry I couldn't.

I wish you the best in finding someone to help you get this working.  There are many, many other options mentioned on that online man page that go in xorg.conf for your card, but I don't have a clue about any of them as I've never used them.

Sorry I couldn help.

BTW - I suspect the problems with the ports is probably because they are on the dock.  The PC should see these as "normal" outputs via the connect bus (unless of course you are connecting to the dock via USB - that would be more challenging), but perhaps there is something in the config that somehow needs to be set for external devices.  My thought:  device 0 should be the one on your PC.  Perhaps the other ports are actually considered other devices, and as such would need their own section in xorg.conf - like the one I had you enter, but for the next device - perhaps "card1".  Just a suspicion.  I don't have anything like that to play with to see how it's done or I'd do it until it worked and then let you know.

---

### Post by squakie on 2014-07-04
I found an older thread in another tech support forum that might apply.  Someone couldn't get the outputs on the same model docking station.  While they would appear to use Windows, I believe the problem is hardware related, in particular that model docking station.  Here is a post from that thread:

[TABLE="class: tborder, align: center"]
[TR]
[TD="class: thead"][IMG]http://www.techsupportforum.com/forums/images/sk/statusicon_2/post_old.gif[/IMG] 			12-07-2008, 08:23 PM 			 			 		[/TD]
 		[TD="class: thead, align: right"] 			  			#[**2**]("http://www.techsupportforum.com/forums/f25/dual-monitors-off-hp-docking-station-304729.html#post1844644") 			 		[/TD]
 	 [/TR]
 [TR]
 	[TD="class: userarea, width: 150"]  			 				 				[Iain_Fenwick]("http://www.techsupportforum.com/forums/members/iain_fenwick-448827.html") 				 				 			
  			Registered Member
 			 			  			     			 				 
				Join Date: Dec 2008
 				 				 				 					Posts: 1 				
                                  					**OS**: vista sp1 				
  
 
  				 				 				 				 				    
 			
  	[/TD]
 	 	[TD="class: alt1"] 	 		 		 			 			 				 	 			
 			[HR][/HR] 			 		  		 		 			 			Hi istravis,

this will not work, to run two multiple monitors off a [hp notebook]("http://www.ebay.com/sch/Consumer-Electronics-/293/i.html?_nkw=hp+notebook"), you require:
1, notebook with dedicated graphics card eg ati or nivida chip
2, [hp advanced docking station]("http://rover.ebay.com/rover/1/711-53200-19255-0/1?toolid=10029&campid=CAMPAIGNID&customid=CUSTOMID&catId=58058&type=2&ext=191216017992&item=191216017992")? this used to be the case could have changed.

I have had the same problem with hp tech support in the past, 
1, what i would suggest in your case is a matrox dual head to go for  high resolutions and good quality , this uses your graphic memory of the  notebook and fools the notebook in to thinking it has one monitor.
2,usb to vga converter for a lower quality picture, these usually have only 8MB of [graphics memory]("http://viglink.pgpartner.com/rd.php?r=501&m=1130857511&q=n&rdgt=1404394623&it=1404826623&et=1404999423&priceret=371.04&pg=%7E%7E3&k=46609a5d408c95482d0074b4d172c8e4&source=feed&url=http%3A%2F%2Fwww%2Ememory4less%2Ecom%2Fm4l%5Fitemdetail%2Easpx%3Fitemid%3D1453863317%26partno%3D454311%2D001%26rid%3D1&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E"),

Unfortunatly HP are now no longer supporting dual [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]external [/FONT][/COLOR][COLOR=blue !important][FONT=inherit !important]monitors[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.techsupportforum.com/forums/#") i led to beleave. but i dont trust anything till i do it myself. 		

------------------------------------------------------






I don't know, but it sounds like a hardware/BIOS/whatever incompatibility between the laptop and that particular docking station.

 		  		  		  [/TD]
[/TR]
[/TABLE]

---

### Post by squakie on 2014-07-04
Jeez, I kind of messed that up and couldn't edit it.

I don't know if this has anything to do with your problem or not, but it sounds like the problem you are having.

Again, sorry I couldn't be of help - I really was just trying to help you, not make a mess for you.

I do wish you the best with this endeavor.  If I see something else while on the net I'll remember this post and post back.

---

### Post by quadrplax on 2014-07-05
So you're thinking that the laptop doesn't support the ports on the docking station? I think the docking station is designed to work with multiple laptops so that could be the case. It could be an Ubuntu thing, or need the official HP drivers (Win Vista+). I thought of something though: Whenever I re-install XP on my old computer, it never wants a product key anymore, probably saves that data on the motherboard somehow or something. This laptop originally had Windows Vista on it. I think that maybe I could try and find my Dad's Vista installation CD and see how that goes. The thing that worries me is that he has Vista Home and it may not have came with the same version. I'll play with that some I guess. Like you've said, I want to take a break from this project for now too, and work on another one, but I'll probably revisit this later. Thanks for trying to help squakie and sudodus.

---

### Post by sudodus on 2014-07-05
You are welcome :-)

---

