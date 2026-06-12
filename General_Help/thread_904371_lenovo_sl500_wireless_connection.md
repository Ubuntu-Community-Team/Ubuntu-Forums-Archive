---
title: "lenovo sl500 wireless connection"
date: 2008-08-29
forum: General Help
---

### Post by bigall on 2008-08-29
Hi, I have just brought a Lenovo sl500 laptop. It has Vista Home premium on it, but I want to run ubuntu on it(I already have it installed on a older ibm thinkpad t43) Anyway, I have loaded the boot cd and it loads ok, but I can't enable the wireless network.  It is a "Intel wireless WiFi link 5100"?:confused: don't know if it makes a difference?

Has anyone got any suggestions to the card working???

Any help would be appreciated.

---

### Post by jonian_g on 2008-08-29
If it doesn't work out of the box then you have to use ndiswrapper.
But ubuntu has to be installed and not running from the livecd to do that.

---

### Post by asten on 2008-09-26
I recently bought a Lenovo SL400, the same as SL500 but smaller screen. You don't have to use ndiswrapper, there is a driver available. If you go to [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) it says at the top of the page that after kernel version 2.6.26 the driver for the 5000 series is included in the kernel.

I compiled the 2.6.27-rc6 kernel from kernel.org and with this it worked automagically, network manager found networks and was able to connect. If you don't like compiling kernels then you can instead use Ubuntu 8.10 which already has the newer kernel, but as for now that version is still in alpha stage so it might not be that stable and things might stop working after upgrades and such (sound stopped working for me).

I chose to use Vista until a stable version of Ubuntu 8.10 comes out maybe in october?

You will also find that the brightness control of the backlight is not working that good and the volume buttons are not working at all. To get the wired network to work you need to compile and use another driver than what comes with ubuntu. Also the intel video drivers in 8.04 are too old for the intel X4500 video card so you might not be able to play movies at all (computer freezed for me). In 8.10 they use newer drivers which works much better.



Last post in this thread has a fix for wired network:
[http://ubuntuforums.org/showthread.php?t=582453](http://ubuntuforums.org/showthread.php?t=582453)

You might want to disable the annoying beep sounds
[http://www.thinkwiki.org/wiki/How_to_disable_the_pc_speaker_(beep](http://www.thinkwiki.org/wiki/How_to_disable_the_pc_speaker_(beep)!)

If you hear the hard drive making clicking sounds, here is a fix
[http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)

/Andreas

---

### Post by mgribov on 2008-10-28
The only way I got my wireless (intel hardware) on sl400 to work is compile my own kernel.

I followed instructions at [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Here is the relevant part of my .config:
CONFIG_IWLWIFI=m
CONFIG_IWLWIFI_LEDS=y
CONFIG_IWLWIFI_RFKILL=y

For some reason, I also had to manually enable Intel HD sound:
CONFIG_SND_HDA_INTEL=m
# CONFIG_SND_HDA_HWDEP is not set
CONFIG_SND_HDA_CODEC_REALTEK=y
CONFIG_SND_HDA_CODEC_ANALOG=y
CONFIG_SND_HDA_CODEC_SIGMATEL=y
CONFIG_SND_HDA_CODEC_VIA=y
CONFIG_SND_HDA_CODEC_ATIHDMI=y
CONFIG_SND_HDA_CODEC_CONEXANT=y
CONFIG_SND_HDA_CODEC_CMEDIA=y
CONFIG_SND_HDA_CODEC_SI3054=y
CONFIG_SND_HDA_GENERIC=y

I made kernel .deb packages and posted them at 
[http://www.neuropunks.org/ubuntu-lenovo-sl400-wifi](http://www.neuropunks.org/ubuntu-lenovo-sl400-wifi) 
if you want to skip compiling yourself - just make sure you have SL400 with Intel - not Atheros wifi. I also posted my .config file there if you want to use it as source for the compile.
Obviously, now you are running not supported kernel, so keep that in mind with updates, etc.

My relevant hardware below:

max@nomad:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:c5:ce:3e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.10.64 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

root@nomad:/usr/src/linux# lshw -C Sound
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by tubbygweilo on 2008-12-16
Bigall,
I also have a Sl500 with Intel WiFi Link 5100 and it works right out of the box on Ubuntu 8.10 64bit. 

```
jqpwork@ubuntu810:~$ uname -a
Linux ubuntu810 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

```

Do things now work with the latest 8.10 or are you still having problems?

---

