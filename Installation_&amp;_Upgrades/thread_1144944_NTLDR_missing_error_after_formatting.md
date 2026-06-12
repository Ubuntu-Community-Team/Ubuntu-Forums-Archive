---
title: "NTLDR missing error after formatting"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by lukegre@gmail.com on 2009-05-01
Recently ran into trouble when I tried to format my PC.
Was dual booting with Windows XP (on 1st primary partition) and Ubuntu (on 2nd primary partition). Also had a third primary partition where i stored all my documents.
I formatted the two OS partitions and tried to install Windows XP sp3. The computer rebooted as soon as I tried to enter bios if i rebooted. However, this did not happen if I powered down.
Didn't get very far using XP install CD. So decided to use Kubuntu live CD. Worked!! and installed Kubuntu. When i restarted noticed that the GRUB screen was the same as before I formatted.
How do I restore this so I can install windows XP again.

Was wondering if there are any 'workflow' orientated photo editing programs (similar to adobe lightroom or photoshop bridge). This is the major factor keeping me from swithing fully to a linux os.

---

### Post by zeex on 2009-05-01
> **lukegre@gmail.com said:**
> Recently ran into trouble when I tried to format my PC.
Was dual booting with Windows XP (on 1st primary partition) and Ubuntu (on 2nd primary partition). Also had a third primary partition where i stored all my documents.
I formatted the two OS partitions and tried to install Windows XP sp3. The computer rebooted as soon as I tried to enter bios if i rebooted. However, this did not happen if I powered down.
Didn't get very far using XP install CD. So decided to use Kubuntu live CD. Worked!! and installed Kubuntu. When i restarted noticed that the GRUB screen was the same as before I formatted.
How do I restore this so I can install windows XP again.

Was wondering if there are any 'workflow' orientated photo editing programs (similar to adobe lightroom or photoshop bridge). This is the major factor keeping me from swithing fully to a linux os.

Hi, 

You are saying you 've Kubuntu installed in your system. I am hoping you are able to use the third partition in Kubuntu. 

> When i restarted noticed that the GRUB screen was the same as before I formatted.
Does this mean you only had option for booking into Kubuntu and no option for Windows. 

If you want to reinstall windows it should be easy. Simply install on the first partiton , right where it was. It'll update the MBR so what 'll happen is you won't see grub after windows installation (That's why it's always recommended that install windows first). It would directly boot into windows. To again use Kubuntu you'll have to reinstall the grub. 

Here is what you do. boot from the live CD. on the terminal.


```
**$** sudo grub
```
This 'll take you to grub prompt. 

```
**grub>** find /boot/grub/stage1
``` 
It ‘ll give you something like …. (hdX,Y) example (hd0,1) 

```

**grub>** root (hd0,1)
**grub> **setup (hd0)
**grub> **quit

```

Reboot and reboot the CD. The grub will have both options now. Windows and Kubuntu.

---

### Post by lukegre@gmail.com on 2009-05-01
Hi, thanks for the reply. After i installed kubuntu the GRUB menu showed the three Kubuntu startup options and then one for windows XP. 

Tried installing windows first but gives me a NTLDR error again. Also had a look on my 3rd partition (documents) and had windows startup files on it (NTLDR, boot.ini, and NTDETECT.COM).
A reply from another forum said it might be the MBR that hasn't changed. Don't know much about this though. 

If I were to format the entire drive (all partitions) would this solve the MBR problem or is there an easier way. At least i can access my info via Kubuntu/Ubuntu!

---

### Post by zeex on 2009-05-01
> **lukegre@gmail.com said:**
> Hi, thanks for the reply. After i installed kubuntu the GRUB menu showed the three Kubuntu startup options and then one for windows XP. 

Tried installing windows first but gives me a NTLDR error again. Also had a look on my 3rd partition (documents) and had windows startup files on it (NTLDR, boot.ini, and NTDETECT.COM).
A reply from another forum said it might be the MBR that hasn't changed. Don't know much about this though. 

If I were to format the entire drive (all partitions) would this solve the MBR problem or is there an easier way. At least i can access my info via Kubuntu/Ubuntu!

Hi, 

Well atleast you can access your files. That's good. Please answer these. 

1) You 've 3 partitions. 3rd one has documents. Where is XP and Kubuntu, I mean partitions?
2) Have you tried installing windows again? If yes, Was the installation successfull without error ? and when you boot you get NTLDR missing. 

The way i advised you earlier was to install a fresh copy of XP. What i want to know is have you formatted windows XP partition or _is it same as it was before NTLDR error_ ? 

NTLDR error can be fixed if your installed windows OS is fine and you have XP installation disk. 

Let me know these. I 'll guide you from there. 

:)

---

### Post by lukegre@gmail.com on 2009-05-01
I tried to install XP first on the 1st partition, this gave me the NTLDR error. The error occurs even before the installation is complete just after copying files accross and has to restart again - so installation never fully completes. 
Then tried to install Kbuntu on the second partition, this worked. The grub now had XP as a booting option, despite the setup never being completed.
On finishing the installation for Ubuntu the 3rd documents partition had the windows boot files.

---

### Post by zeex on 2009-05-01
> **lukegre@gmail.com said:**
> I tried to install XP first on the 1st partition, this gave me the NTLDR error. The error occurs even before the installation is complete just after copying files accross and has to restart again - so installation never fully completes. 
Then tried to install Kbuntu on the second partition, this worked. The grub now had XP as a booting option, despite the setup never being completed.
On finishing the installation for Ubuntu the 3rd documents partition had the windows boot files.

Hi, 

How did the 3rd partition got the boot files. This is a little confusing. Tell me if i'm wrong You 've 3 partitions. You have windows on 1st , Kubuntu on 2nd and documents on 3rd. 

During your XP installation did you format the C: drive before XP installer starts to copy files. If you did that means your installed copy of windows is gone which basically means we can't go to recovery now. 

Can you describe your XP installation process. See if i'm right. 

1) You boot with XP bootable CD.
2) CD copies basic files and comes to a screen where you choose to do a fresh install. 
3) It takes you to a partition table where you can see the previous installled copy of windows. 
4) You choose the same partition to install Xp. It warns you that already a windows exist but you go ahead format the drive 
5) After formatiing setup starts to copy files and then reboot.
6) You get NTLDR missing error msg . 

This is how I'm looking at things. let me know how you tried to installed XP.

::* I'm trying to trace your steps cuz I still don't understand if you tried to install XP on 1st partition. how did boot files ended up in 3rd partition.*

---

### Post by lukegre@gmail.com on 2009-05-01
> **zeex said:**
> 

::* I'm trying to trace your steps cuz I still don't understand if you tried to install XP on 1st partition. how did boot files ended up in 3rd partition.*

I have no idea how these files ended up on the 3rd drive. given up... backing up and formatting. thanks for all the help tho.

---

### Post by ezsit on 2009-05-01
If you want to overwrite your MBR, from a Linux liveCD, I would suggest the gparted CD or the Parted Magic CD since they are small and easily and quickly downloaded and booted. Use the gparted partition editor and under the menus there is an option to create a new partition table. This should clear the MBR. It will also erase the old partition table so only do this if there are no partitions who still need to access on the hard drive. After you reboot, the Windows XP installation will see an unpartitioned drive and you will need to create the Windows partition.

---

### Post by zeex on 2009-05-01
> **lukegre@gmail.com said:**
> I have no idea how these files ended up on the 3rd drive. given up... backing up and formatting. thanks for all the help tho.

Hi, 

I hope your system is working now. Just one question do you 've 2 separate hard disk or single hard disk.

I'm trying to understand the reason.

---

