---
title: "MBR of linux"
date: 2012-04-27
forum: Hardware
---

### Post by sherazi21st on 2012-04-27
hi all,
I am using windows and intending to use ubuntu along with it. Also I'm intending to restore my windows within a few weeks. What I want to ask you is, if I install ubuntu now (because I waiting for 12.04) and after few weeks when I restore windows which will erase my Master Boot Record (MBR), then tell me that how can I fix it without reinstalling ubuntu as it is present in my drive. I encounter this problem before and I had to  reinstall ubuntu again which erase all my setting of ubuntu and other things related to it. Plz help me in this regard.

---

### Post by grahammechanical on 2012-04-27
I am not sure if I am giving you correct information but I would advise that you install Ubuntu after you have done your restore of Windows.

I also think that Windows updates often remove the Grub menu from the MBR thus causing you lose access to Ubuntu. You do not need to re-install Ubuntu to solve this.

You can use the Ubuntu live CD to restore the Grub menu to the MBR. What the command is I do not know.

I invite others to give you more detailed information.

Regards.

---

### Post by coffeecat on 2012-04-27
@sherazi21st, if you install Windows and it overwrites the mbr, you certainly don't need to re-install Ubuntu. Re-installing Ubuntu's grub to the mbr is all that is needed and is fairly straightforward using the Ubuntu live CD or live USB. The easiest way is with Boot-Repair Graphical Tool, but you need to install it to the live session. See here:

[https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool](https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool)

If you don't mind a couple of terminal commands, the next easiest way is by copying the live CD files, as described here:

[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

The only remotely difficult part of that is identifying your Ubuntu root partition with the fdisk command. If you need help with that someone here will be able to.

Once you have re-installed grub and are able to boot into Ubuntu, you may need to regenerate the grub menu because the Windows menu entry will be for the previous version of Windows and the Windows partition UUID may have changed. That is easily done with:

```
sudo update-grub
```

---

