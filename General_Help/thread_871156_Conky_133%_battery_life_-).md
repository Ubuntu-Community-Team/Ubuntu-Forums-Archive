---
title: "Conky: 133% battery life :-)"
date: 2008-07-26
forum: General Help
---

### Post by Stefanie on 2008-07-26
Conky displays 133% battery life instead of 100% when working on AC power. When working on battery power the number seems to be correct, though. Any ideas? 
I use the $battery_percent variable, this is the relevant part of my .conkyrc:

```
Battery ${font Andale Mono:size=9}${execi 45 acpi -b | cut -c36-39}${alignr}${battery_percent}%
$battery_bar
```

---

### Post by Tomone on 2008-08-22
I know that in my conky config file I use an argument for those variables.
${battery_percent BAT1}% and 
${battery_bar BAT1}
Without an argument they default to BAT0. Hopefully that fixes your problem.

---

### Post by brettbender on 2009-02-27
This is a bug in Conky 1.6.1, fixed in more recent prerelease / source.

Conky computes battery percentage as:

  remaining_capacity / last_full_charge

But when you're on AC and charged up, some laptops (like my Dell D830) lie about remaining capacity, reporting it as the full value designed for the battery.

```

cat /sys/class/power_supply/BAT0/uevent
...
POWER_SUPPLY_CHARGE_FULL_DESIGN=7800000
POWER_SUPPLY_CHARGE_FULL=5592000
POWER_SUPPLY_CHARGE_NOW=7800000
...

```

The fix is to go download and build a prerelease version of Conky, or patch the deb package to cap battery percentage at 100.

If you go the latter route...

Install the build dependencies, grab the source package, and cd into the source directory.

```

sudo apt-get build-dep conky
apt-get source conky  
cd conky-1.6.1

```

Now edit src/linux.c and add the line indicated below:

```
***************
*** 2002,2007 ****
--- 1955,1961 ----
        /* compute the battery percentage */
        last_battery_perct[idx] =
                (int) (((float) remaining_capacity / acpi_design_capacity[idx]) * 100);
+       if (last_battery_perct[idx] > 100) last_battery_perct[idx] = 100;
        return last_battery_perct[idx];
  }

```

Save your edit, build, and install the package:

```

dpkg-buildpackage -rfakeroot -uc -b
cd ..
sudo dpkg -i conky_1.6.1*.deb

```

---

