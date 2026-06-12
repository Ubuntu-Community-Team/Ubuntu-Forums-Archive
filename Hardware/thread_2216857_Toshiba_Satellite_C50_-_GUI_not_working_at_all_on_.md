---
title: "Toshiba Satellite C50 - GUI not working at all on Ubuntu 12.04 LTS"
date: 2014-04-14
forum: Hardware
---

### Post by michalkotowski on 2014-04-14
[LEFT][COLOR=#333333][FONT=UbuntuRegular]I bought a new laptop Toshiba Satellite C50-A-1JQ and I'm unable to run any GUI under Ubuntu 12.04 LTS or 13.04 (the same happens for booting from LiveUSB and for an installed system).[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]After booting the screen goes black (as if it turned off) and I can't do anything, but I guess the system loads normally (I still hear the standard Ubuntu splash screen sound). By including "nomodeset" parameter in Grub I'm able to run the system in tty command line, but any attempt to run unity, startx etc. fails (I get error messages indicating that no screen was found).[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]The laptop uses Intel HD Graphics and I suspect (I'm not sure though) that this might be an issue with graphics driver, but couldn't find anything helpful on the internet (I looked at almost all possible threads relating to this type of issue and most people claim that either including "nomodeset" or "acpi_osi=linux" in Grub should work or that the default drivers should be OK, but neither works for me).[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]Any help would be much appreciated.[/FONT][/COLOR][/LEFT]

---

### Post by sudodus on 2014-04-14
Welcome to the Ubuntu Forums :-)

I agree that it is probably an issue with graphics driver. I suggest that you try all the available boot options (not only "nomodeset" or "acpi_osi=linux" ), maybe even more than one each time. (Try from the live DVD/USB drives)

- Do you know the model version number of the graphics chip?

Using the boot option text, you can probably run the computer in text mode, and install or edit files.

-o-

Sometimes you need the very newest version of Ubuntu to run a brand new computer. Ubuntu 13.04 has actually passed end of life. The newest current version is 13.10. In about a week the next version, 14.04 LTS will be released. And I suggest that you try both of these versions. They come with new drivers for new hardware.

---

### Post by oldfred on 2014-04-14
Agree that 14.04 will probably be the better choice. Lots of updates.

Some possibly similar Toshiba
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
> Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

