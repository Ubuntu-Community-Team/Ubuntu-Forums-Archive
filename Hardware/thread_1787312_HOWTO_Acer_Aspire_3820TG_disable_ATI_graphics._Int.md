---
title: "HOWTO: Acer Aspire 3820TG disable ATI graphics. Intel-only mode"
date: 2011-06-21
forum: Hardware
---

### Post by Prikolchik on 2011-06-21
**Acer 3820TG: How to disable ATI graphics in the BIOS. Unlock Intel-only graphics mode** (by prikolchik)
[SIZE="3"]
**_Intro:_**[/SIZE]
Acer 3820TG has switchable graphics ATI and Intel. A few months back, there were many people having problems with both graphics cards running at the same time. There were people who wanted to run in Intel-only graphics mode, and do that they would either use vga_switcheroo or a small program that makes ACPI calls and disables the unused ATI graphics card.

Even right now I see many people asking for help with this issue. I found a simple and quick way to disable unused ATI card in the BIOS. It involves either using a tool to unlock hidden menu in the BIOS or flashing to a modified BIOS with unlocked hidden menu.

Here I present you a way to disable ATI graphics on **hardware** level in the BIOS.

Many thanks to: [kizwan]("http://forum.notebookreview.com/member.php?u=230695") @ [NBR]("http://forum.notebookreview.com") who discovered this method.

[SIZE="3"]**_Description:_**[/SIZE]
Apparently, Acer included a hidden BIOS menu that allows you to completely disable ATI graphics. This menu is not accessible by default -- it is hidden. There are two ways you can enable this menu. One way is to use **SYMCMOS.exe** tool (requires no BIOS flashing and is safe). The other way to do it is flash to a modified BIOS created by [kizwan]("http://forum.notebookreview.com/member.php?u=230695") that has the hidden menu permanently unlocked.

I suggest reading about both methods. Use the one that suits you best.

Note: First method might work with other Acer laptops that have Intel/ATI switchable graphics and Phoenix BIOS. Second method is specifically for 3820 TG/TGZ/TZ

[SIZE="3"]_**Method 1 (easy): Using [B]SYMCMOS.exe** tool to unlock hidden menu[/B]_ [/SIZE]
Pros:
 - easiest and safe
Cons:
 - is NOT permanent. If you reset BIOS to default, the unlocked menu is gone

The idea is to change a BIOS setting in NVRAM using a simple DOS program.

Here is how you do it:
_*Step 1.*_ Create bootable USB flash drive:

_Windows_: use [HP Disk Storage Format Tool]("http://www.mediafire.com/?e2912vln5v25jpy") to format the flash drive

_Linux_: use **GParted** (or another tool) to format the flash drive to FAT/FAT32 and set the **boot** flag to true (select partition, right click and check flags).

Copy [MS DOS files]("http://www.mediafire.com/?2d8afhf0mp7pchy") (you need to copy only 3 files: COMMAND.COM, IO.SYS, MSDOS.SYS) to the flash drive.


_*Step 2.*_ Download [SYMCMOS.exe]("ftp://ftp.supermicro.com/utility/Phoenix_bios_utility/SYMCMOS.EXE") ([mirror]("http://www.mediafire.com/?locc1v1bgvb4r4s")) and save it to the root of the formatted flash drive.


_*Step 3.*_ Connect flash drive, restart computer, and right after the POST press F12 to access the boot menu. If it does not come up, press Ctrl+Alt+Del to reboot computer and try again. It might also be disabled in the BIOS. In that case, press F2 and find "F12 boot menu" and set it to "Enabled". Press F10 and to save the changes. Try F12 again.


_*Step 4.*_ Once you boot from flash drive, you should see something like:
```
C:>\
```
This is DOS command prompt. Now dump BIOS settings from NVRAM into a file called **Default.txt**:
```
symcmos -v2 -lDefault.txt
```
NOTE: It is _**lowercase L**_ in front of **Default.txt**

Reboot computer via power button, or press Ctrl+C.


_*Step 5.*_ Turn on computer, boot into operating system.
In the root of the flash drive you should see **Default.txt**. Open **Default.txt** file with Notepad (Windows) or gedit (Linux). Locate the (**0141**) change the value next to it from **0000** to **0001**. After you made the changes, save it to a new file, let say **NEW.txt**. Make sure you save the **NEW.txt** file on the flash drive.


_*Step 6.*_ Reboot computer and boot from USB flash drive again.

Now write new BIOS settings to NVRAM:
```
symcmos -v2 -uNEW.txt
```

Once the tool completes, reboot your computer.


_*Step 7.*_ Please see **Accessing unlocked menu and changing graphics** at the end of this post.

References: [kizwan]("http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-72.html#post6763651")'s original post

[SIZE="3"]_**Method 2 (advanced): Flashing to the modified BIOS that has menu unlocked by default**_[/SIZE]
[COLOR="Red"]**_WARNING: THERE IS A CHANCE YOU WILL PERMANENTLY DAMAGE YOUR COMPUTER. PROCEED AT YOUR OWN RISK!_**[/COLOR]
Pros:
 - permanent. Will stay even if BIOS settings are reset to default
Cons:
 - relatively hard
 - there is a chance that you brick your computer. It is still possible to recover via [this method (BIOS recovery)]("http://forum.notebookreview.com/7016499-post8674.html") though

_Note: Read Method 1 to learn how to create a bootable flash drive and boot from it._

**_Step 1._** If your BIOS is NOT v1.19, then download unmodified Acer BIOS from the support website and flash to it. You can do it by extracting the archive to a directory **acer** (for example) on your flash drive, then boot from it and type C:\acer\Flash.bat. It will flash the BIOS.

**_Step 2._** If you running BIOS v1.19, then you can flash to **kizwan**'s modded BIOS. [Download it]("http://www.mediafire.com/?89bb9ipualgolzb") and extract it to the flash drive in directory **kizwan** (for example). Boot from USB drive using F12 boot menu and type ```
C:\kizwan\BIOS.bat
``` This should flash the modified BIOS.

**_Step 3._** If everything went well, you should now have a _permanently unlocked_ advanced menu in the BIOS. Please read **Accessing unlocked menu and changing graphics** at the end of this post.

If something went wrong and your computer no longer boots, then please try [BIOS recovery procedure]("http://forum.notebookreview.com/7016499-post8674.html")


[SIZE="3"]**_Resetting BIOS settings: If you change something wrong_**[/SIZE]
If you accidentally selected the wrong video card and no longer have picture on the screen or if you changed some BIOS setting and your computer no longer boots.

You can blindly reset to default BIOS settings. Here is a list of steps:
1. Make sure computer is off.
2. Turn computer on.
3. Get into BIOS with F2.
4. Press F9 + Enter (this will load setup defaults)
5. Press ESC + Enter + Enter (this will save the changes)
6. Your computer reboots and you are back!
This should work for Acer 3820/4820/5820

NOTE: If you used **SYMCMOS.exe**, then you will need to unlock the hidden menu again.

If this does not help, you can [reset the BIOS manually]("http://forum.notebookreview.com/7016423-post8665.html")


[SIZE="3"]_**Accessing unlocked menu and changing graphics**_[/SIZE]
Now is the fun part!

After unlocking the hidden menu with either Method 1 or Method 2, turn on computer and press F2 to enter into the BIOS setup. Using arrow keys, navigate to the Intel menu. 
[IMG]http://i54.tinypic.com/2v3shmt.jpg[/IMG]

Then navigate to **MCH Control Sub-menu** and change **Primary Displa**y from **Auto** to **IGD**. (NOTE: The Switchable option will disappear from the BIOS. Nothing to worry about). Press F10 to save settings and restart computer.
[IMG]http://i55.tinypic.com/28qtaih.jpg[/IMG]
This will disable ATI graphics and make your computer run in Intel-only mode :)

List of modes:
**Auto**: will automatically determine the graphics mode (Switchable)
**IGD**: Intel-only graphics mode. The "Switchable graphics" menu will disappear from the front page of the BIOS.
**PEG**: ATI-only mode. Intel graphics is disabled.
**PCI**: [COLOR="Red"]DO NOT SELECT THIS![/COLOR] You will not see anything on the screen any more. If you selected this by mistake, see above "**Resetting BIOS settings**"
**SG**: Switchable graphics. Both cards will be available and driver will determine which card will be active.

So, if you want to turn the ATI graphics back on, simply change MCH Control Sub-menu->Primary Display back to **Auto**. Save via F10 and restart.


Here is a nice confirmation:
_Windows_: ATI graphics is gone from Device Manager and there is no longer **Switch graphics** menu.
[IMG]http://i51.tinypic.com/2iifui9.png[/IMG]

_Linux_: ATI graphics is also gone:
```
$ lspci | grep -i graphics
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
```


Cheers!


PS: I apologize for including Windows information in the guide. I simply wanted to make this guide useful to everyone regardless of the operating system.

---

### Post by Pikachu84 on 2011-08-03
Thanks for this elaborate guide.

I am not running Ubuntu, but I am a normal Windows 7 slave... However I find it insanely annoying that every time I unplug and plug back in the computer, the graphics cards switches automatically. It causes almost any open program to not work properly.

Should I use this function to run on Intel graphics only? When I need to play or send video via HDMI I could reboot with ATI activated.  Or is there an easier way?

I know this is not the right forum, but it is the only place people discuss the deactivation of these graphics cards.

Thanks
Henrik

---

### Post by cRaZyBisCuiT on 2012-05-04
Hi! Thanks for the guide. I'm using a 4820TG and have some problems. Is it supposed to work?

```

symcmos -v2 -lDefault.txt
combineFiles (Oh, COMBINE.ROM)...
initEntry ...
search 'PDM' ... not Found!
pdmEntry = NULL!

```

Do you have any ideas?

---

### Post by darcode on 2012-07-26
Hi!
I've aswell an acer 4820tg, could you confirm this guide is working also with this model version?
It's so annoying the vga switching and I'd like only the integrated one....

---

### Post by Prikolchik on 2013-01-08
> **cRaZyBisCuiT said:**
> Hi! Thanks for the guide. I'm using a 4820TG and have some problems. Is it supposed to work?

Short answer: It won't work, don't even try.

Long answer: 4820TG/5820TG has an Insyde BIOS and this guide is for 3820TG which has a Phoenix BIOS. **symcmos** program is specific to the Phoenix BIOS and it simply will not work for Insyde BIOS on 4820TG/5820TG which is the behaviour you are getting.

If you want to disable Dedicated video on 4820TG/5820TG, then you need to flash a modified BIOS that has that functionality unlocked. There is no other way that I know of.

For a copy of the modified BIOS and instructions please see [Acer Aspire TimelineX 4820TG/5820TG Modded BIOS (Insyde)]("http://forum.notebookreview.com/acer/568951-acer-aspire-timelinex-4820tg-5820tg-modded-bios-insyde.html")

---

### Post by cRaZyBisCuiT on 2013-01-08
Evem though I asked that a long time ago I'd like to thank you. I'll have a look!

---

