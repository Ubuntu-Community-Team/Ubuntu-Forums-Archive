---
title: "FIXED: ACPI fan and negative-temperature problems"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by kamalmostafa on 2007-11-26
I had but _have solved_ the problems with Ubuntu Feisty and Gutsy mishandling the CPU fan and reporting incorrect negative CPU temperatures on my eMachines system. The problems were caused by a buggy ACPI DSDT on my eMachines T2245.   Happily, I was able to fix the problems in the DSDT, so now the CPU temperature is reported correctly and the fan works properly.  If you are having either or both of the problems I describe below, this article may help you fix your ACPI DSDT as well...

The ACPI problems on my eMachines T2245 system were as follows:

1. The CPU fan never switched off.

2. Ubuntu read incorrect negative CPU temperature and thermal trip points, reporting values in the range of -270 degrees Celsius, e.g.:
```
/proc/acpi/thermal_zone/THRM/temperature
    temperature:             -270 C

/proc/acpi/thermal_zone/THRM/trip_points
    critical (S5):           -264 C
    passive:                 -273 C: tc1=0 tc2=0 tsp=600 devices=CPU0 
    active[0]:               -267 C: devices=FAN1 
```

Both problems were caused by faulty ACPI DSDT code.   It is clear that the same buggy DSDT code exists in other eMachines models, and similar bugs probably exist in other manufacturers DSDT's as well.


**Modifying and replacing the ACPI DSDT**

This excellent article explains how to extract, disassemble, modify, recompile, and install the ACPI DSDT:
[INDENT][_HOWTO: Fix Common ACPI Problems (DSDT, ECDT, etc.)_]("http://forums.gentoo.org/viewtopic.php?t=122145")[/INDENT]

It turns out that Ubuntu Gutsy (and Feisty I think) already have all the kernel support built-in to make the DSDT-replacement process relatively easy.

I recommend that you first do a dry-run to test the DSDT-replacement procedure before actually trying to modify the DSDT.   Here is the basic procedure I used:

```

mkdir acpi-mod
cd acpi-mod

sudo cat /proc/acpi/dsdt > DSDT.dat     # extract the current ACPI DSDT
iasl -d DSDT.dat                        # disassemble to create DSDT.dsl
cp DSDT.dsl DSDT.dsl.orig

```

At this point, you can edit DSDT.dsl to fix bugs.  Or for the first dry-run, don't edit it -- just try recompiling it as-is to verify that you can install it and boot up again without any problems.   Either way, the next steps are to recompile and install a new DSDT so that the system will load it at boot time:

```

iasl DSDT.dsl                           # recompile to create DSDT.aml

... check for errors/warnings; edit DSDT.dsl and recompile again as needed ...

sudo cp DSDT.aml /etc/initramfs-tools/  # install our modified DSDT.aml
sudo update-initramfs -u                # rebuild the boot-ramdisk with it inside

```

Now reboot the system.  Once its up again run "dmesg | grep DSDT" and verify that you now get this line in the output, which indicates that the system did load your (modified) DSDT:

```
dmesg | grep DSDT
     ... look for: ...          ACPI: Table DSDT replaced by host OS
```

If anything goes haywire and you can't get booted up again, boot with "acpi=off" on the kernel boot line to prevent the system from using any ACPI at all, then try editing DSDT.dsl further.  Or, to revert back to using the original built-in DSDT, remove /etc/initramfs-tools/DSDT.aml and then rebuild the boot-ramdisk (update-initramfs -u) again.

**Fixing temperature and fan problems in the DSDT**

Now that you have verified that you can install a new DSDT, its time to try modifying your DSDT.dsl...

The problem with my CPU temperature being reported in the -270 degree Celsius range occurs because the buggy DSDT in my eMachines system incorrectly returns the temperature in Celsius instead of in tenths-of-degrees-Kelvin as the ACPI spec requires.   Linux then converts the already-Celsius value to Celsius again, resulting in the bogus temperature value.

If you have the same problem, edit your DSDT.dsl as follows:   Find your "ThermalZone" section, and add the "KELV" Method to it (see code below).  Then examine each of the "Methods" (routines) that return a temperature value:  _TMP, _CRT, _AC0, and _PSV.   Change all the Return() statements in each of those Methods to convert the return value to tenths-of-degrees-Kelvin using the KELV Method.   Here are the changes I made to my DSDT.dsl -- yours may look somewhat different:

```

                 ThermalZone (THRM)
                 {
[COLOR="Green"]+                       /*
+                        * The ACPI spec requires that ThermalZone temperatures
+                        * be returned in tenths-of-Kelvin-degrees.  But this
+                        * machine's temperature sensor provides the current
+                        * CPU temperature in degrees Celsius.  This routine
+                        * makes the necessary conversion.
+                        */
+                   Method (KELV, 1, NotSerialized)
+                   {
+                       /* Celsius to Kelvin: K = C + 273.15 */
+                       Store (Arg0, Local1)
+                       Multiply (Local1, 10, Local1)
+                       Add (Local1, 2732, Local1)
+                       Return (Local1)
+                   }
+[/COLOR]
                     Method (_TMP, 0, NotSerialized)
                     {
                         Store (\_SB.PCI0.SMBS.SBRB (0x5A, 0x26), Local0)
                         Store (Local0, DBGP)
                         If (LGreater (Local0, 0x7F))
                         {
                             Store (0x01, Local0)
                         }
 
[COLOR="Red"]-                        Return (Local0)[/COLOR]
[COLOR="Green"]+                       /* Return temperature as (Kelvin * 10) */
+                        Return ( KELV(Local0) )[/COLOR]
                     }
 
                     Method (_CRT, 0, NotSerialized)
                     {
[COLOR="Red"]-                        Return (\CCRT)[/COLOR]
[COLOR="Green"]+                        Return ( KELV(\CCRT) )[/COLOR]
                     }
 
                     Method (_AC0, 0, NotSerialized)
                     {
                         If (FNON)
                         {
[COLOR="Red"]-                            Return (\CAC0)[/COLOR]
[COLOR="Green"]+                           /* Return temperature as (Kelvin * 10) */
+                            Return ( KELV(\CAC0) )[/COLOR]
                         }
                         Else
                         {
[COLOR="Red"]-                            Return (\CAC1)[/COLOR]
[COLOR="Green"]+                           /* Return temperature as (Kelvin * 10) */
+                            Return ( KELV(\CAC1) )[/COLOR]
                         }

```

Those changes fixed my CPU temperature and trip points, but there was also a problem with the fan-status Method -- it always returned "0x01" indicating that the fan was always "on", which causes the trip points temperature control system to not work correctly.


Examine your DSDT.dsl for the "PowerResource" block corresponding to your fan.  If the _STA "status" Method contains just a Return(1) statement, then it will need to be fixed.   Here is mine, along with the change I applied to make the _STA Method return a sensible value.  (For my case, I noticed that the "FNON" variable was already being set by the _ON and _OFF Methods.  You will need to examine your _ON and _OFF Methods to look for some variable which is being set -- it may be called something different).

```

                 PowerResource (FN01, 0x00, 0x0000)
                 {
                     Method (_STA, 0, NotSerialized)
                     {
[COLOR="Red"]-                        Return (0x01)[/COLOR]
[COLOR="Green"]+                       /*
+                        * Return actual fan status 'FNON', which gets set
+                        * by the _ON and _OFF methods.
+                        */
+                       Return (\_TZ.THRM.FNON)[/COLOR]
                     }

```

It also turned out that the "FNON" variable was not being initialized properly.  I added this code to the _INI Method in order to make sure the system knows that the CPU fan is already on at boot time.   (Furthermore, I find that switching the fan right back off at boot time works fine, so I do that too.  If doing so causes your system to have any trouble booting, you can comment that line out).  Here is the code to be inserted:

```

             Method (_INI, 0, NotSerialized)
             {
[COLOR="Green"]+                   /*
+                    * The CPU fan is always running at boot time, so
+                    * initialize 'FNON' (fan status) to 1.
+                    */
+               Store (0x01, \_TZ.THRM.FNON)
+
+                   /*
+                    * Optional: Force the fan OFF immediately at boot time.
+                    * (Comment this line out to just leave the fan running
+                    * at boot time until the ACPI system decides to turn it
+                    * off due to the thermal trip points settings.
+                    */
+               \_TZ.FN01._OFF ()[/COLOR]

```

And that's it.  With those changes applied to my DSDT.dsl, my temperature readings are all correct, and the fan switches on and off properly as it crosses the trip points.


**Problems not yet resolved**

Whenever I use a recompiled and initramfs-loaded DSDT.dsl (even without making any changes to it), ACPI no longer recognizes that my CPU supports "throttling states".  This line appears when I use the default DSDT, but does not appear when I load a recompiled one:

```

dmesg | grep ACPI
    ...
[COLOR="Red"]    ACPI: Processor [CPU0] (supports 8 throttling states)[/COLOR]
    ...

```

Setting the trip points and manually turning the fan on and off by writing to /proc/acpi both still do not work, probably due to additional missing code in my DSDT.

If I make any further progress on these unresolved issues, I will follow-up to this post.

 -Kamal Mostafa

---

