---
title: "Creative Sound Blaster Z in Ubuntu 18.04"
date: 2018-05-30
forum: Hardware
---

### Post by li-la-lars on 2018-05-30
Hello everyone,

I recently bought a Sound Blaster Z card without chekcing the compatibilty first... At first glance it seemed to be incompatible. There were many old threads from people not getting it to work. In my system the card is displayed in the menu and can be selected as sound output, but it won't generate any sound. (It works under windows btw.)

HOWEVER, after some searching I found that someone developed a driver recently ([https://forums.creative.com/showthread.php?t=742256]("http://forums.creative.com/showthread.php?t=742256")) and I became hopeful, that I might get it to work.

Because I haven't compiled a kernel before, and espacially have not applied a kernel patch: Can someone lead the way how to do it?

And a more general question: If this sould be successfull, do i need to apply that patch again and again, everytime there is an update? Because that seems like a lot of work, and it might be better to simply return the card. Is there a chance that the driver will be included in the kernel in the future? Wouldn't it be easier to make a linux-headers package? (Sorry for the dumb questions, I'm new to this topic.)

I don't know if it is any help, but here someone made it work on archlinux ([https://bbs.archlinux.org/viewtopic.php?id=236364](https://bbs.archlinux.org/viewtopic.php?id=236364))...

Thanks

---

### Post by jeremy31 on 2018-06-01
You would need to download the kernel source after enabling the source repositories in Software and Updates ```
apt-get source linux-modules-extra-$(uname -r)
```
Then apply the patch- I am sure you can find something on the internet about using patch files.  Once the patch is applied change directory into the one where the patch was applied and then I normally right click and chose "open in terminal" then
```
cp /usr/src/linux-headers-$(uname -r)/.config .
cp /usr/src/linux-headers-$(uname -r)/Module.symvers .
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
```
Then I just copy the kernel module(s) I need  to the correct place in /lib/modules/$(uname -r)/kernel/sound/pci/hda/, then I do ```
sudo depmod -a
```
To refresh the module alias list.

After checking your link, the patch isn't a patch filed but a patched version of the module c code and it does compile in the 4.15 kernel and needs to be put in /snd/pci/hda/ of the kernel source 

You would have to recompile for newer kernels but that would just be to switch into the kernel source code directory and
```
make -C /lib/modules/$(uname -r)/build M=$(pwd) clean
cp /usr/src/linux-headers-$(uname -r)/.config .
cp /usr/src/linux-headers-$(uname -r)/Module.symvers .
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
```
Then copy the new modules into the new kernels /lib/modules/$(uname -r)/kernel/sound/pci/hda/ do the sudo depmod -a and reboot

If someone was serious about it they could probably make this dkms so it compiled just after a new kernel was installed and not have to do it manually

---

