---
title: "HP Battery ACPI giving wrong stats / plugged in is 100 % and when removed suddenly 9"
date: 2017-02-02
forum: Hardware
---

### Post by aviwad on 2017-02-02
[COLOR=#111111][FONT=Ubuntu]SPECS HP laptop - 13 inch 13-a201tu Ubuntu Gnome 16.10 running Gnome Wayland.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My HP laptop ( 13-a201tu) is a 13 inch two in one convertible x360. it was updated in bios from F.24 to F.35 and since then everything hs gone downhill. I was dual booting Arch Linux (Apricity ) and Windows 10. since updating the bios, booting Linux (later reformated hard drive with only ubuntu) gave blank screen, and from legacy mode, I saw the problem. Sleep / Resume not supported by ACPI. so I put in kernel options[/FONT][/COLOR]
    acpi_backlight=vendor acpi_osi="!Windows 2009" acpi_osi="!Windows 2012" acpi_osi="!Windows 2013" acpi_osi="Linux" acpi_osi=Linux
[COLOR=#111111][FONT=Ubuntu]The problem was, that now after I extracted the DSDT table of this new bios (to see what all OS versions were detected, so I knew what to disable/enable) I still got a recurring battery problem.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]EXAMPLE - battery is actually charged 100%, but while my laptop was on, so when I disconnect the charger, suddenly charge becomes 9%, then goes down to 1% and stays there for 4 hours. then because of critical battery option, Gnome Ubuntu shuts down thinking battery low when the battery is actually close to 30 %. so downgrading bios is almost impossible (even HP service center couldn't do it) but two options remain.[/FONT][/COLOR]

[LIST=1]
[*]try to solve why this is happening, maybe extract the original dsdt from F.24 bios, and replace file.
[*]disable ubuntu from knowing the battery exists
[/LIST]
[COLOR=#111111][FONT=Ubuntu]the third option was to disable critial battery action and Upower.conf but, even then, the notifications are annoying, and the fan randomly starts running high. any help would be appreciated. thank you.[/FONT][/COLOR]

---

