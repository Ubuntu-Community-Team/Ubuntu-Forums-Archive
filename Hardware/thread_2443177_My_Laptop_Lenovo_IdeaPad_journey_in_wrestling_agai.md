---
title: "My Laptop Lenovo IdeaPad journey in wrestling against BIOS/UEFI issues."
date: 2020-05-12
forum: Hardware
---

### Post by mortalkorona on 2020-05-12
[I]

This **setup & install journal** will be linked to my [COLOR=#8b4513]**LAPTOP COMPATIBILITY**[/COLOR] post found here:[/I][URL="https://ubuntuforums.org/showthread.php?t=1543006&page=179"]
https://ubuntuforums.org/showthread.php?t=1543006&page=179[/URL]


**1) Version:** Ubuntu 20.04 LTS (Focal Fossa)[B][B]

2) Laptop Maker:[/B][/B] Lenovo[B][B][B]

3) Laptop Model:[/B][/B][/B] IdeaPad s400u

**[COLOR=#008000]It works![/COLOR]**


---------------------------------------------------------------------------------------------------------


[SIZE=4][B]Background story
[/B][/SIZE]
I started learning how to use Linux around 2005 using Ubuntu and Debian. Things went smooth for a couple of years then I tried Linux Mint and Lubuntu. Then around 2015 when I discovered that there was this new thing called UEFI. I could no longer manage to install any Linux distros as easily as before on machines that I previously had done several Linux installs on.

Not having the time and energy to deal with **UEFI** that stopped me from even booting into the LiveCD/USB. I then just dropped everything about Linux and only played on my Windows machine. 5 years later all my Linux machines became deprecated and unusable which forced me into facing the UEFI boot issues once again.

Long story short it took me around 2 days straight to wrestle against the **BIOS/UEFI issues** trying to make the **LiveCD/USB boot**. Finally I understood how to work with UEFI and how to configure the BIOS settings to make things just start. That's why I wanted to write this journal for anybody else facing the same struggles.

To simplify things this is how I like to imagine it, even though it might not be the correct way to describe things.

* **BIOS** = [COLOR=#8b4513]**BIOS 1.0**[/COLOR]
* **UEFI**  = **[COLOR=#8b4513]BIOS 2.0[/COLOR]**


---------------------------------------------------------------------------------------------------------


[SIZE=4][B]Pre-install procedures
[/B][/SIZE]
Here are some tutorials and links that are good to follow before trying to boot the Ubuntu **LiveCD/USB** on your laptop.

[COLOR=#8b4513]*** Ubuntu download folders**[/COLOR][URL="https://releases.ubuntu.com/"]
https://releases.ubuntu.com/[/URL]


[COLOR=#8b4513]*** Verify checksums and signatures for ISO file**[/COLOR]
   To make sure download was not corrupted or have been hacked.
[https://ubuntu.com/tutorials/tutorial-how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-how-to-verify-ubuntu#1-overview)


[COLOR=#8b4513]*** Create a LiveCD/USB stick**
[/COLOR]   There are many ways to do this procedure but this was the way I preferred and chose to use.
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)


---------------------------------------------------------------------------------------------------------


[SIZE=4][B]Reboot into BIOS/UEFI setup screen
[/B][/SIZE]
Every computer's BIOS screen will basically look different but perhaps me listing my ***secret Coca Cola ingredients*** will help you adapt your settings as close to the truth as possible.

**Step 0.)**
During reboot screen hold **Fn** key and press **F2** key several times to enter into BIOS setup screen.
[COLOR=#ff0000]*The keys for booting into "BIOS setup" screen will differ between models and manufacturers!*[/COLOR]


[COLOR=#0000ff][SIZE=3]BIOS - Configuration tab[/SIZE][/COLOR]

[LIST]
[*]Wireless LAN = **Enabled**
[*]SATA Controller Mode = **RAID**
[*]PXE Boot to LAN = Disabled
[*]Power Beep = Disabled
[*]Intel Virtual Technology = Disabled
[*]BIOS Back Flash = Disabled
[*]Intel(R) AT Support = Disabled
[*]System Hotkey Mode = Disabled
[/LIST]

If your BIOS settings doesn't have **RAID** as an option then choose **AHCI** or something similar close to it. Read the explanation in this Microsoft article for better understanding.

***What does AHCI Mode, IDE Mode, RAID Mode, & SATA Mean in the BIOS settings***
[https://answers.microsoft.com/en-us/windows/forum/windows_8-hardware/what-does-ahci-mode-ide-mode-raid-mode-sata-mean/d622d5cd-41c4-4b84-90ef-cea69aa47089](https://answers.microsoft.com/en-us/windows/forum/windows_8-hardware/what-does-ahci-mode-ide-mode-raid-mode-sata-mean/d622d5cd-41c4-4b84-90ef-cea69aa47089)



[COLOR=#0000FF][SIZE=3]BIOS - Security tab[/SIZE][/COLOR]

[LIST]
[*]Secure Boot = **Disabled**
[/LIST]


[COLOR=#0000FF][SIZE=3]BIOS - Boot tab[/SIZE][/COLOR]

[LIST]
[*]Boot Mode = **UEFI**
[*]USB Boot = **Enabled**
[/LIST]


[COLOR=#0000FF][SIZE=3]BIOS - Exit tab[/SIZE][/COLOR]

[LIST]
[*]OS Optimized Defaults = **[Win8 64bit]**
[/LIST]


[COLOR=#0000FF][SIZE=3]BIOS - Exit Saving Changes[/SIZE][/COLOR]

[LIST]
[*]This should enable your Ubuntu LiveCD/USB stick to boot without UEFI issues.
[/LIST]


---------------------------------------------------------------------------------------------------------

**Step 1.)**
During reboot screen hold **Fn** key and press **F12** key several times to enter the [COLOR=#0000ff]**"Boot Option Menu"**[/COLOR].
[COLOR=#ff0000]*The keys for booting into "Boot Option Menu" screen will differ between models and manufacturers!*[/COLOR]


[B]Step 2.)
[/B]Select [COLOR=#0000ff]**"EFI USB Device ..."**[/COLOR].


[B]Step 3.) Installation type (screen)
[/B]At the installation type screen select **[COLOR=#daa520]"Something else"[/COLOR]** option.


---------------------------------------------------------------------------------------------------------


[SIZE=4][B]Gparted (screen)
[/B][/SIZE]
[COLOR=#ff0000]Warning this procedure will erase everything on all of your hard drives!!!

[/COLOR]My Lenovo IdeaPad model consist of 2 disks. [COLOR=#ff0000]You shouldn't delete the hidden partitions that Windows 8 uses for factory resets.[/COLOR] Keeping Win 8 factory reset partitions is your only way to upgrade BIOS in the future, if you need to do it. But in this case you won't need to upgrade BIOS. I burned my Windows revert bridges by deleting mine years ago. [COLOR=#ff0000]Lenovo doesn't provide BIOS upgrade ISO files for this specific model![/COLOR] :(

[COLOR=#8b4513]*  20 GB SSD disk[/COLOR] = **/dev/sda**
[COLOR=#8b4513]* 500 GB HD disk[/COLOR] = **/dev/sdb**


[B]Step 4.)
[/B]Select [COLOR=#0000ff]**/dev/sda**[/COLOR] and click [COLOR=#daa520]**"New partition Table"**[/COLOR].


[B]Step 5.)
[/B]Select [COLOR=#0000FF]**/dev/sdb**[/COLOR] and click [COLOR=#DAA520]**"New partition Table"**[/COLOR].


[B]Step 6.)
[/B]Create a 550 MB **"EFI system partition"** for [COLOR=#0000FF]**/dev/sda**[/COLOR].


[B]Step 7.)
[/B]Create a 4124 MB **"swap area"** for [COLOR=#0000FF]**/dev/sda **[/COLOR]because my Laptop has 4 GB RAM memory.


[B]Step 8.)
[/B]The rest of the SSD disk ([COLOR=#0000ff]**/dev/sda**[/COLOR]) I reserved for the [COLOR=#daa520]**"Mount point"**[/COLOR]:[COLOR=#0000ff]**/ **[/COLOR].


[B]Step 9.)
[/B]The HD disk ([COLOR=#0000ff]**/dev/sdb**[/COLOR]) I reserved for the [COLOR=#daa520]**"Mount point"**[/COLOR]:[COLOR=#0000ff]**/home **[/COLOR].


[B]Step 10.) Device for boot loader installation:
[/B]Select the partition where your mount point is [COLOR=#0000ff]**/**[/COLOR] . In this case [COLOR=#0000ff]**/dev/sda3**[/COLOR].


gg, you have won the BIOS/UEFI game!

---

