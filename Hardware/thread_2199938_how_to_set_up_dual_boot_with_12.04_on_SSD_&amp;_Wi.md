---
title: "how to set up dual boot with 12.04 on SSD &amp; Win 7 on HDD?"
date: 2014-01-16
forum: Hardware
---

### Post by Odyssey1942 on 2014-01-16
Got my wife a new HP computer preinstalled with Win8. She is a longtime (generally) happy Windows user, but gets so frustrated with 8 she occasionally shouts at the computer and now wants to try Ubunutu. 

Since she will be trying it out, thought it might be a good idea to put 12.04 onto a SSD to give her a fast user experience, which I have done, apparently successfully (at least so far.) One thing that I learned in preparing for the install is that one should disconnect their HDD so as to avoid Ubuntu putting some of the installed files onto the existing HDD. Can't remember why this is the case or which files, but that stuck in my head. Hope I got that right.

So now I need to hook the HDD back up and make the system dual boot. I think that there is a grub update process which will accomplish this. But this is a bit above my level of experience. I have done a considerable amount of googling with a lot of near misses, but without learning how to do it. Any assistance with the appropriate steps gratefully received.

---

### Post by robsoles on 2014-01-16
Assuming you are booting from the drive with Ubuntu on it, with of course the WIndows drive as a secondary, the following worked last time I needed it to;```
sudo update-grub
```Once that completes restart the machine and see if it picked up the Windows boot info from the second drive.

Best case scenario Windows boots with correct drive assignments, worst case scenario the people making grub have changed it so a different command needs to be used and a middle (not good) case scenario would be that Windows partway boots but has bad drive assignment and complains that 'C:\windows\blah' doesn't exist because it is assigned as D: or something.

My money is on the best case scenario :)

(tho I only ever bet about $1 on such things)

---

### Post by ajgreeny on 2014-01-16
When you hook up the old HDD you may find that the system boots to that and not to ubuntu, as boot priority device setting may still be for the Windows disk.  You can probably quickly sort that out by hitting whatever key is needed for changing boot priority when you see the manufacturer's logo on screen.

Once booted into Ubuntu run command ```
sudo update-grub
``` and it should add windows to the grub menu.

---

### Post by oldfred on 2014-01-16
Did you install Ubuntu in UEFI mode? With gpt partitions?

The sudo update-grub does not work with UEFI systems except 13.10 or later. Grub still was creating BIOS boot for Windows when it should create UEFI boot.

Maybe best to see details.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Odyssey1942 on 2014-01-16
Here is my history since Robsoles. Upon seeing his, I immediately ran the code and tried rebooting. No cigar.

Had to take the Missus to dinner.

Got back to see both ajgreeny and oldFred replies:

Here is Boot Info:

[http://paste.ubuntu.com/6765816/](http://paste.ubuntu.com/6765816/)

---------------

ADDITIONAL INFORMATION

Did quite a bit of reading on what UEFI is so I could try to answer accurately. Still not positive, but if I understand it, Win * uses UEFI natively. Unsure whether I installed 12.04 under UEFI except that:

there is a /sys/firmware/efi which I understand is an indication that 12.04 was installed under UEFI, and

when I reboot and try to go into the BIOS setup, the first thing that comes up is a blue box with white borders and dividers (which I associate with Windows, rightly or wrongly) which reads:

STARTUP MENU
-------------------------
Continue Startup
System Information
Change Language
-------------------------
Diagnostics (F2)
Boot Menu (F9)
Computer Setup (F10)
System Recovery (F12)
Utilities
Run UEFI application

Now if I choose "Boot Menu" it shows the following:

Boot Order:
>UEFI Boot Sources:
----Windows Boot Sources
----ubuntu
----USB Floppy/CD
----USB H.D.
----UEFI IPV4 Network Card
----UEFI IPV6 Network Card
(So the 6 items above are subitems under the heading ">UEFI Boot Sources:" indicating all of the 6 are "UEFI")

 By selecting ubuntu and as soon as the grub menu shows, quickly clicking on the top line (Ubunut 12.04), it will boot into 12.04.

But if I am too slow or do nothing, it will boot into Win 8.

However, if I choose "Computer Setup"/Storage/Boot Order, and select: "Ubuntu" from this list:

    Windows Boot Manager
    ubuntu
    USB Floppy/CD
    USB H.D.
    UEFI IPV4 Network Card
    UEFI IPV6 Network Card
    Legacy Boot Sources: Disable (this line is greyed out)

it goes straight into Win 8, ignoring my selection of ubuntu

Finally, when I reboot from Ubuntu, it ignores my BIOS request (ESC key) and reboots into Win 8. Only when I reboot from Win 8, will the top mentioned "Startup Menu" come up.

Perhaps none of this other than the Boot Info is useful, but thought I would give all the information I have found.

In any case, thank you for the guidance, and I hope that the "Boot Info" will provide useful information. Sure is a lot there.

Still unsure how to answer" With gpt partitions?", but will work on it while you are reading the above. Perhaps the Boot Info will give the answer.

---

### Post by oldfred on 2014-01-17
If you have Windows in UEFI, you have to have gpt partitions. Gpt partitioning is a newer partitioning type over the 30+ year old MBR(msdos) partitioning and must be used with UEFI. 

It says you installed 12.04.4, but you have 12.04.3 kernel & grub. But the grub menu Windows entries are the old BIOS type that will not work with UEFI. Boot-Repair can add a correct entry, but it adds all efi files in efi partiiton. And HP has many utility efi files so all those will get added also. You can later remove those entries from 25_custom or just manually add one entry your self.
If Boot-Repair suggests a "buggy" UEFI repair say no. That is only for the systems where vendor's modify UEFI so ubuntu entry does not work at all.

Not sure why you get different boot results from the different choices to boot. But Windows tries to keep itself as default.

 UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)


 grub2's os-prober creates wrong style (BIOS) chain boot entry Fixed with 13.10
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

Above bug report has instructions on adding the boot stanza to correctly boot Windows in UEFI mode from grub menu. Boot-Repair auto adds that type of entry, but adds all the others with your system.
Detailed instructions on editing 25_custom to remove extra entires in link in my signature if desired.

---

### Post by Odyssey1942 on 2014-01-17
Good morning OldFred,

Thank you most sincerely for your detailed guidance. Frankly, I am way over my head here and am only just trying to get Ubuntu installed on an SSD on my wife's computer, alongside the original Win 8 install on the hdd so she can get back to using it, and am under a certain amount of pressure from her to get this done.

In my experience, sometimes it is easier to go to plan B than to fix plan A. While my curiosity and genuine interest would lead me to do all of the research and reading to fully understand all of this, I cannot predict how long this might take me, so considering her needs, think it prudent to consider alternatives.

Firstly, I should mention that I installed 12.04 (64bit) from a download made a couple of months ago, and so wonder if a re-download today might bring a 12.04.4 kernel & grub, and if so, might this help avoid the current problem?

Secondly, I installed 12.04 onto the SSD with the HDD disconnected, and so am unsure if the HP BIOS caused it to install under UEFI. (I do not remember making any choices during the install, and for certain did not go into the BIOS (UEFI?, not sure whether to call it BIOS or UEFI now) to choose UEFI). Would this account for the difficulties?

So in the interest of getting her computer back to her, hopefully with Ubuntu for her to try, and hopefully on an 
SSD, with a dual boot for the Windows programs that she uses that don't work on Linux, is there an alternative install method that I might use to sidestep my current problem?

I hate to ask for a quick fix here, but trust you will sympathize with my situation. Thanks.

P.S. I might add that my handle could appropriately have been OldBob, and the old grey cells are a good deal less sharp than many decades ago. Learning this stuff is much more challenging for me in these later years.

---

### Post by oldfred on 2014-01-17
It installed in UEFI. And how you boot installer is how it installs. You you booted the installer in UEFI mode and that is more correct as if you had installed in BIOS mode, you could not easily dual boot.

Can you not boot the Windows entry in UEFI? Do you have a one time boot key that also gives the same boot choices of both Windows or Ubuntu? Often f12 but varies by vendor.

It looks like they have just changed label of 12.04 to be 12.04.4, but actual update to that will not be available until early Feb.

---

### Post by Odyssey1942 on 2014-01-17
> Can you not boot the Windows entry in UEFI

Just to be sure I understand you, is UEFI and BIOS the same thing by different name and newer process? I.e., is the function of UEFI the same as BIOS is/was, but perhaps best for me to think of as an updated BIOS? Your confirmation will be appreciated as this will be much easier for me if I understand the terminology correctly.

If so, I cannot avoid booting into Windows using UEFI (assuming the above is correct). See below.

When powering the computer on and pressing the "Esc" key, the "Startup Menu" shows. From there I can hit F9 or arrow key down to Boot Menu, save & exit, what I think is called the Grub Menu (white letters on black background, reminds me of the Shell) comes up, but only for an instant. In order to select Ubuntu, which is the top item in the list, I must hit the Enter key very quickly, otherwise it boots into Win 8.

Or from the above mentioned "Startup Menu", I can press F10, or key down & select Computer Setup. It then goes to what I believe, but please correct me,  you are referring to UEFI. Going there and then selecting Ubuntu from the boot choices, the computer ignores my selection and goes straight into Win 8 (this is not the result I would expect and do not want.)

When rebooting from within either Ubuntu or Win 8 and as I tried to explain earlier, it either returns to Win 8 or offers up the "Startup Menu" mentioned above. While I can train her how to manage this, I don't want to put her off thinking that she is getting into something she doesn't understand. It needs to be a very simple process. 

So what I hope to achieve is, when either powering up or rebooting, that a screen comes up which offers you a choice between Ubuntu and Win 8 (believe this is the Grub Menu) and remains in place so that one has a reasonable opportunity to read the choices and make a informed selection.

---

### Post by oldfred on 2014-01-17
UEFI is the new BIOS, but it has a BIOS mode for backwards compatibility. It has a lot more features and its own memory storage to save settings.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    
 ExtremeTech article on what UEFI is,  from 2011 
[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)
Secure Boot
[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)

UEFI now is also a boot manager or something that lists bootable options. Grub is both a boot manager with its menu and a boot loader.
If you set ubuntu as the default boot option in UEFI then you should get grub menu for 10 sec.

But Windows does like to auto update UEFI to make itself boot first.

      
 UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)

---

### Post by Odyssey1942 on 2014-01-17
Success!

> If you set ubuntu as the default boot option in UEFI then you should get grub menu for 10 sec.

I thought I had already done that, but double checked to be sure and realized that I had not understood how to do it. Once I figured it out and set Ubuntu as priority, it went right into the grub menu on exit.

Thank you.

---

### Post by oldfred on 2014-01-17
Glad you got it working. :)

But remember what you did. I do not have UEFI but many are reporting that Windows likes to reset to make itself first so you may have to reset periodically.

---

### Post by Odyssey1942 on 2014-01-18
Good counsel. I have made notes in my linux folder, and of course I can always look back here.

You had mentioned:

> The sudo update-grub does not work with UEFI systems except 13.10 or later

Should I be watching for other issues that may be related to the fact that I am using 12.04, and if so, what might I notice, for example?

One other thing that I notice from an earlier post is those two items from the "Boot Order" menu, i.e.:

> ----UEFI IPV4 Network Card
----UEFI IPV6 Network Card

I understand that IPV4 addresses are a scarce and rapidly vanishing species and that we will all eventually be using IPV6 addresses. I don't understand what network cards have to do with boot order, so what is their significance in the Boot Order menu?

BTW, I don't mean to restrict the comments to OldFred, anyone's thoughts are welcomed.

Thanks.

---

### Post by oldfred on 2014-01-18
I do not know anything about it, but you can network boot. And then it depends on your network which version it is. You should have those last in the boot order, otherwise it may try to go to network first and have to time out.

There will be a new 12.04.4 version in early Feb. I expect that to include many updates. But I do not think you automatically get the new version. I installed 12.04 and am still running it with its updates and the old kernel. 
Each point revision now includes a new kernel and many other updates.

This includes 12.04.3, but either this page or a new one should be available for 12.04.4
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack)

---

