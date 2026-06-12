---
title: "enable drivers in kernel"
date: 2014-05-23
forum: Hardware
---

### Post by greenjah on 2014-05-23
Hi,
Can someone help me, please ?
I've compiled and installed 3.12 kernel but forgot to enable video drivers. My /boot/config has:

# Multimedia core support
#
# CONFIG_MEDIA_CAMERA_SUPPORT is not set
# CONFIG_MEDIA_ANALOG_TV_SUPPORT is not set
# CONFIG_MEDIA_DIGITAL_TV_SUPPORT is not set
# CONFIG_MEDIA_RADIO_SUPPORT is not set
# CONFIG_MEDIA_RC_SUPPORT is not set
# CONFIG_VIDEO_ADV_DEBUG is not set
# CONFIG_VIDEO_FIXED_MINOR_RANGES is not set
# CONFIG_TTPCI_EEPROM is not set

if I understand correctly, my integrated video camera cannot work because the parameters about are not set. 
How can I enable them without recompiling the current kernel ?
Or if it is not possible to enable them - how to recompile current kernel with the same configuration and just to enable the parameters above ?

---

### Post by Doug S on 2014-05-24
You will have to re-compile.
You should have a config file in your build directory. It is hidden with a leading ".", i.e. ".config". Example:```
doug@s15:~/temp-k-git-3.10rc4/linux$ [COLOR=#ff0000]ls -l -a .con*[/COLOR]
-rw-rw-r-- 1 doug doug 168986 May  7 11:46 .config
-rw-r--r-- 1 doug doug 162039 Jul 23  2013 .config-3.11.0-031100rc2-generic
-rw-rw-r-- 1 doug doug 160573 Jul 16  2013 .config.3.11.nohz
-rw-rw-r-- 1 doug doug 160580 Jul 16  2013 .config.3.11.rc1
-rw-r--r-- 1 doug doug 164086 Jan 20 15:56 .config-3.13.0-031300-generic
-rw-r--r-- 1 doug doug 166001 Mar 31 15:09 .config-3.14.0-031400-generic
-rw-rw-r-- 1 doug doug 165939 Feb 20 11:44 .config-3.14.rc1
-rw-rw-r-- 1 doug doug 166015 Feb 20 11:50 .config-3.14.rc3
-rw-rw-r-- 1 doug doug 157917 Jul 14  2013 .config.nohzfull
-rw-rw-r-- 1 doug doug 168934 Apr 27 23:53 .config.old
-rw-rw-r-- 1 doug doug 157900 Jul 14  2013 .config.original
-rw-r--r-- 1 doug doug 162068 Jul 16  2013 .config.ubuntu
-rw-rw-r-- 1 doug doug 162023 Jul 17  2013 .config.ubuntu.fixed
```Save a backup of the original file and then edit it for what you want. When you compile the kernel, I suggest you use a localized version name. You didn't mention what build method you are using, on my system, for a localized version name, I do (and because I always time the compile):```
time make -j8 deb-pkg LOCALVERSION=-doug2
```

---

### Post by greenjah on 2014-05-24
I've compiled my current kernel with the following commands:
- download 3.12 kernel
> make cloneconfig
> make menuconfig
> export CONCURRENCY_LEVEL=3
> fakeroot make-kpkg --append-to-version "-customkernel" --revision "1" --initrd kernel_image kernel_headers
> dpkg -i linux-image-3.12.0-customkernel.deb linux-headers-3.12.0-customkernel.deb

My system has .config files at:
> find / -name .config
/usr/src/linux-3.12.19/debian/linux-headers-3.12.19-customkernel/usr/src/linux-headers-3.12.19-customkernel/.config
/usr/src/linux-3.12.19/.config
/usr/src/linux-headers-3.2.0-4-amd64/.config
/usr/src/linux-headers-3.12.19-customkernel/.config
/root/.config

Could you describe which .config file should I use and which commands should to be executed for recompile kernel ?

Thanks

---

### Post by Doug S on 2014-05-25
I have not used methods similar to what you are doing for a few years now, so I am not sure, but I think this one:```
/usr/src/linux-3.12.19/.config
```for this:> and which commands should to be executed for recompile kernel ?You listed the commands yourself, so I don't understand the question.

---

