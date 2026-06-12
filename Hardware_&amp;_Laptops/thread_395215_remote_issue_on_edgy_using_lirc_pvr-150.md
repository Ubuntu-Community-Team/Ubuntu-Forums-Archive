---
title: "remote issue on edgy using lirc pvr-150"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by lawson23 on 2007-03-27
Followed the Mythtv Server Edgy guide
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend#head-efc7a1a32622b1ba4359ea774469c0a5fc97ee74](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend#head-efc7a1a32622b1ba4359ea774469c0a5fc97ee74)
Then tried getting my remote working from my pvr-150,
I followed a standard guide to LIRC (don't remember where mythtv or something) then tried another mythtv guide specific to edgy and then this guide: 
[https://help.ubuntu.com/community/Install_Lirc_Edgy#head-94847261cd47d6aa8cf70283f0e2ac4c6884de82](https://help.ubuntu.com/community/Install_Lirc_Edgy#head-94847261cd47d6aa8cf70283f0e2ac4c6884de82)


root@SERVERNAME:/# /etc/init.d/lirc start
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.


dmesg gives:
[17179591.368000] lirc_dev: IR Remote Control driver registered, at major 61
[17179591.368000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179591.536000] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[17179591.536000] lirc_dev: lirc_register_plugin: sample_rate: 10
root@SERV3R1:~# 17179591.368000] lirc_dev: IR Remote Control driver registered, at major 61
-bash: 17179591.368000]: command not found
root@SERV3R1:~# [17179591.368000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
-bash: [17179591.368000]: command not found

---

### Post by majoridiot on 2007-03-27
are you building for remote only or remote and irblaster?

please post a copy of /etc/lirc/hardware.conf

---

### Post by lawson23 on 2007-03-28
This is not to use the IR-Blaster it is only for the remote.  I will post the hardware.conf later when I can get to it.

---

### Post by lawson23 on 2007-03-28
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_ic2"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
```

---

### Post by majoridiot on 2007-03-28
the i2c driver has issues in edgy... did you build it from the 3rd party packages as that page suggests?

as an alternative, you can follow the pvr-150 w/blaster instructions, build the modules from that
package, skip the firmware and codeset step and it will work fine for your remote... just be sure to use
the lirc.conf.hauppauge for your remote.  if you later want to use the blaster, all you need to do is
grab the firmware and codesets you want.

i can confirm this works 100% as i built it only two nights ago for the same hardware following those
instructions.

what is the result of:
```
$ dmesg | grep lirc
```

---

### Post by lawson23 on 2007-03-28
dmesg | grep lirc                                               
[17179591.368000] lirc_dev: IR Remote Control driver registered, at major 61
[17179591.368000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179591.536000] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[17179591.536000] lirc_dev: lirc_register_plugin: sample_rate: 10

I think it has something to do with the previous versions I tried installing.  The first install from the guide which I can't remember which one I used went perfectly except when tested the remote I didn't get output on the screen so then I found some other guides tried them and they would fail just as this guide did.

---

### Post by Rictus on 2007-04-29
Umm, I only happend to notice this because I'm looking for answers for my own remote problem, but I see a typo in your hardware.conf file.
 
> # If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_ic2"

 
Shouldn't Modules be "lirc_i2c" not ic2?

---

### Post by majoridiot on 2007-04-29
> **Rictus said:**
> Umm, I only happend to notice this because I'm looking for answers for my own remote problem, but I see a typo in your hardware.conf file.
 

 
Shouldn't Modules be "lirc_i2c" not ic2?

yup.  it sure should. :)

---

### Post by lawson23 on 2007-06-08
About 4 weeks ago I scrapped my edgy install and went with feisty Fawn 7.04.  I have not attempted my remote setup yet in 7.04.  Sorry for the delayed response.

I do have some questions though and don't know if I should start a new post.  For now I'm going to keep it here.
Looking at this guide:
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

It states that:
NOTE: Some i2c remotes are supported directly by the kernel. If you are using a remote that would have used the i2c driver, check out the Managed I2C devices link below to use this instead.

Does the PVR-150 with the gray remote with the 4 colored buttons at the bottom fall into the Managed I2C list?

---

### Post by amoore on 2007-06-13
> 

Does the PVR-150 with the gray remote with the 4 colored buttons at the bottom fall into the Managed I2C list?

I'm having similar problems too. Why is Mythtv so difficult.......

---

