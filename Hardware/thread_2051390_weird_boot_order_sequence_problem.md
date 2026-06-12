---
title: "weird boot order sequence problem"
date: 2012-09-01
forum: Hardware
---

### Post by bucket_brigade on 2012-09-01
I have installed Ubuntu 12.04 on lenovo thinkpad edge 330. Before this I was able to go to BIOS and set the boot order sequence. Now the same window in BIOS only contains "1. ubuntu" in it. Thus I cannot boot from USB or any other device anymore. How is this possible?

---

### Post by oldfred on 2012-09-01
Welcome to the forums. Is this a UEFI system? How did you install Ubuntu?

If you have the liveCDUSB or can boot into Ubuntu run the BootInfo report and post link it creates:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by bucket_brigade on 2012-09-01
Yes this is a UEFI system. It has an option in BIOS startup settings called "legacy", however using it makes no practical difference. The only difference is that if I specify it should use legacy only it will not be able to find any bootable device even if one is present.

[http://paste.ubuntu.com/1180513/](http://paste.ubuntu.com/1180513/)

---

### Post by oldfred on 2012-09-01
You are not seeing any Windows because you have no Windows. When you installed Ubuntu it should have given you several choices and the overwrite entire drive and erase everything should have told you it would erase everything. I have not installed UEFI so I do not know if it is all correct.

It looks like you have two installs of Ubuntu, one efi on sdb and one BIOS on sda. Your 16GB sda looks like one of the new Intel Smart Response systems.

 Intel Smart Response Technology & Dell XPS, yours may be similar?
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

Did you backup Windows before install? I also do not see a recovery partition. If you do not have backups, you will have to contact vendor for a new install disk.

---

### Post by bucket_brigade on 2012-09-02
I don't want to see Windows, I know I wiped it out. The problem is I am not happy with my Ubuntu installation. I installed in on my 500gb hdd but now I think it may be better to install it on the SSD and mount the HDD on the /home directory. But now I cannot boot from USB (this laptop has no laser disk drive). Is there some way I can boot Ubuntu installation?

---

### Post by typhoon_tip on 2012-09-02
After you create a startup disk correctly in USB, insert the USB into the slot and reboot the PC in Bios, it should see the external HDD ! But only if is valid and connected.

If not, when the PC is pre-booting, pressing F12 or another key (some systems F2) will bring up the boot menu, which will allow you to temporary choose a boot device.

---

### Post by bucket_brigade on 2012-09-02
That is exactly the problem. After I installed ubuntu from a USB stick it no longer sees any other bootable devices. The BIOS window for boot order only has "ubuntu" in it. I suppose it could be that after discovering a UEFI bootable disk or something it does not allow to boot the old way.

---

### Post by oldfred on 2012-09-02
Do not know that much about booting from a UEFI menu, and every vendor is different. Do you have a one time boot key. My BIOS system has f12 as a one time choice to boot CD, USB or which ever hard drive that is not the default.

---

### Post by bucket_brigade on 2012-09-02
Pressing F12 brings up a screen where you can choose what to boot from, however, as I said, after installing Ubuntu that screen only contains "ubuntu" in it. It used to list various other options before that.

---

### Post by oldfred on 2012-09-02
Did USB flash get overwritten? BIOS/UEFI will only show bootable devices, so if flash is not now bootable it will not show it.

Can you turn UEFI off and see if in BIOS mode it shows USB?

---

### Post by bucket_brigade on 2012-09-02
BIOS used to show all devices and allowed to specify boot order. The flash is still bootable, I tried on another laptop. All that disabling UEFI achieves is that I cannot boot anything at all.

---

### Post by bucket_brigade on 2012-09-02
I guess I should try simply pulling the HDD with the UEFI partition out and see if this does anything.

---

