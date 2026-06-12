---
title: "disabling usb module / module newbie"
date: 2008-12-02
forum: General Help
---

### Post by 77bridge on 2008-12-02
Hi *,

I'm dealing with a bug where there appears to be no easy workaround and I am totally clueless about the subject matter- maybe someone can help here.  I'm running Ubuntu Gutsy with a vmware workstation XP guest machine upon which I've installed iTunes and my ultimate hope is to sync to my iPod from there.  (I know there are linux native alternatives to iTunes, but I'd like to get this working anyways)  Long story short: there seem to be usb driver issues where the virtual machine tries to claim the device but for one reason or another, it never successfully completes this.  Various discussions on vmware forums and elsewhere suggest that you can disable the usb driver (possibly 'usb-storage') on the host machine and that should work.  I've experimented with 'rmmod usb-storage', but 1) I didn't get any successful results and 2) I got different messages (sometimes successful, other times error) whenever I execute this command.

So here are some questions:
1) Why does the 'rmmod usb-storage' command produce different results when I execute it successively?
2) What is the mechanism that loads the usb drivers/modules in Linux and what events trigger this loading?
3) Is there a way (eg script, config, cmd) to toggle off (prevent them from loading under any circumstance) my usb drivers in Linux and then toggle them back on (allow them to load) again whenever I want? (I don't mind disabling all other usb devices temporarily to get my iPod to sync correctly)
4) Any good background information focused on this specific question? 

Thanks!!!!! 77b  :D

---

### Post by cariboo on 2008-12-02
> 1) Why does the 'rmmod usb-storage' command produce different results when I execute it successively?

When you use rmmod if the command executes sucessfully you shouldn't see anything. The only time you will get anything echoed back is if the command did not complete successfully.

For your usb problems, have a look here:

[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

Jim

---

### Post by 77bridge on 2008-12-02
> **cariboo907 said:**
> When you use rmmod if the command executes sucessfully you shouldn't see anything. The only time you will get anything echoed back is if the command did not complete successfully.

Sometimes it works, but I suspect the module is only temporarily getting removed/unloaded.  (per my earlier comments, I'm clueless  :) ) Is there a way to permanently block this module?

> **cariboo907 said:**
> 
For your usb problems, have a look here:
[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

Thanks- however this seems to only apply to VirtualBox rather than vmware workstation (which is what I am using)- or perhaps I'm missing something?

---

### Post by 77bridge on 2008-12-02
I think I can refine my question a little more now:

How can I blacklist the usb_storage (or usb-storage) module so that it does not start up when I plug in my iPod?

I've tried the approach described here: [ HOWTO: Prevent (blacklist) modules from loading  ]("http://http://ubuntuforums.org/showthread.php?t=166624") but that hasn't worked.

For example, when I restart and I execute: 'lsmod | grep usb' I get the following output:
usbhid                 32128  0
hid                    38784  1 usbhid
usbcore               146412  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd

That's ok.  Now when I plug in my iPod, I execute the same command and I get the following output:
usb_storage            73664  0
libusual               19108  1 usb_storage
usbhid                 32128  0
hid                    38784  1 usbhid
scsi_mod              151436  6 usb_storage,sbp2,sr_mod,sg,sd_mod,libata
usbcore               146412  7 usb_storage,libusual,uvcvideo,usbhid,ehci_hcd,uhci_hcd

usb_storage is the very first module listed, yet my /etc/modprobe.d/blacklist and /etc/modprobe.d/blacklist-custom files both have the following lines:
blacklist usb-storage
blacklist usb_storage

So that's my question: how can I actually blacklist usb_storage so that it doesn't start up when I plug in my iPod?

Thanks!!!

---

