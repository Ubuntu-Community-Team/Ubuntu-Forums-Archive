---
title: "Sony &quot;Motion View&quot; Camera support in Ubuntu 20.04"
date: 2021-01-14
forum: Hardware
---

### Post by hstoellinger on 2021-01-14
Hello Everybody,

I have been running Kubuntu 20.04 for quite a while and everything works like a charm - except the Motion Eye camera on my old Sony laptop. 
It is recognized but displays are "fuzzy" in applications such as zoom or skype. pertinent inxi -F output is the following:
> 
System:    Host: hslaptop Kernel: 5.4.0-52-generic x86_64 bits: 64 Console: tty 3 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:   Type: Laptop System: Sony product: VGN-AW11M_H v: C6010CXT serial: 28282369-5004308 
           Mobo: Sony model: VAIO serial: N/A BIOS: American Megatrends v: R0200Y2 date: 08/12/2008 
...
CPU:       Topology: Dual Core model: Intel Core2 Duo P8400 bits: 64 type: MCP L2 cache: 3072 KiB 
           Speed: 1596 MHz min/max: 1600/2267 MHz Core speeds (MHz): 1: 1596 2: 1596 
Graphics:  Device-1: NVIDIA G98M [GeForce 9300M GS] driver: nvidia v: 340.108 
           Display: server: X.Org 1.20.9 driver: nvidia unloaded: fbdev,modesetting,nouveau,vesa resolution: 1680x945~60Hz 
           OpenGL: renderer: GeForce 9300M GS/PCIe/SSE2 v: 3.3.0 NVIDIA 340.108 

After some "googling" a suggestion was to look at the post under [https://forums.linuxmint.com/viewtopic.php?t=314523](https://forums.linuxmint.com/viewtopic.php?t=314523).

However, trying to go through the procedure described there I got stuck in step (3) (i.e. sudo apt-get install r5u87x). I get the following error messages:
> 
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
r5u87x : Haengt ab von: module-init-tools ist aber nicht installierbar
E: Probleme koennen nicht korrigiert werden, Sie haben zurueckgehaltene defekte Pakete
Translated into English this means roughly:
The following packages have unfulfilled dependencies:
r5u87x: depends on: module-init-tools, but this is not installable
E: Problems could not be corrected, you have held-back, defect packages

"kmod" and the programs contained within module-init-tools (such as depmod, insmod, etc.,) are of course installed in my Kubuntu 20.04 LTS system. But it looks as if at least the "dependency" definitions in package r5u87x would have to be modified - provided that driver actually still works under
kernel 5.4 (installed under Kubuntu 20.04).
In any case - I wonder how to proceed. Any ideas would help a lot
Regards from Austria
H. Stoellinger

---

### Post by &amp;KyT$0P# on 2021-01-15
Does something from [this thread]("https://ubuntuforums.org/showthread.php?t=2443814") help?

---

### Post by hstoellinger on 2021-01-17
Thanks for trying to help. Well, I downloaded everything, ran make/make install successfully. However when I then tried to run 
the loader I got the following reply:
> 
sudo ./loader --reload
r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:183e
Warning: Failed to get microcode status.

Error: Failed to upload firmware to device: Broken pipe (code -32).


I see that there is an issue for exactly this problem. I don't seem to be able to access that issue on bitbuckt. Do you have an idea about how to solve this?
Thanks in advance for any hints.
Regards
H. Stoellinger

---

### Post by #&amp;thj^% on 2021-01-17
I remember now all the crap with the microcode on these camera's. (Around 2007-2009) I wish I had better news for you.

**The microcode file can also be uploaded to the device by its Windows driver, by booting first to a Windows installation that includes a driver, then rebooting to Linux.**  The microcode is stored in the device's volatile memory and must be reloaded after each cold boot.

The microcode upload process is very similar to the ez-usb devices, except that the Ricoh cameras have two additional commands that are required to complete the upload process.  R5U870 webcam devices also do not reset and report different USB IDs after their microcode has been loaded.

Do you have intel-microcode installed?
```
sudo dmesg | grep microcode
[sudo] password for me: 
[    0.994082] microcode: sig=0x806ec, pf=0x4, revision=0xde
[    0.994116] microcode: Microcode Update Driver: v2.2.

```
I'm not sure how to advise you any further.

---

### Post by hstoellinger on 2021-01-18
Thanks for the quick answer! I got rid of Windows on the system concerned. So - since I don't really want to go through the hassle of re-installing Windows (I think I still have a Vista CD hanging around somewhere) - I suppose I will have to live with the "fuzziness" of my webcam. Tough luck! 
In any case, sudo dmesg | grep microcode returns the following info:
> 
[    0.000000] microcode: microcode updated early to revision 0x60f, date = 2010-09-29
[    0.202716] MDS: Vulnerable: Clear CPU buffers attempted, no microcode
[    1.227738] microcode: sig=0x10676, pf=0x80, revision=0x60f
[    1.227911] microcode: Microcode Update Driver: v2.2.

Thanks for the moment; should I find out anything more, I will post it to you.
Regards from snowy Austria
H. Stoellinger

---

