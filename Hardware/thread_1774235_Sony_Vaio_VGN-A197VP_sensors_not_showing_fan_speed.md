---
title: "Sony Vaio VGN-A197VP sensors not showing fan speed"
date: 2011-06-03
forum: Hardware
---

### Post by pookieman123 on 2011-06-03
Hi

New here, but spent a bit of time trying to get to the bottom of this and no luck. Basically my laptop VGN-197VP is a few years old, I've XP on it and also 11.04, using grub.

The fan speed in XP is barely audible - but in 11.04 it's noisy, I just want to slow it down as it's not needed. Thing is 'sensors' shows this:

> acpitz-virtual-0
Adapter: Virtual device
temp1:       +61.0°C  (crit = +100.0°C)         
When I do sensors-detect I get this:

 > sudo sensors-detect
# sensors-detect revision 5861 (2010-09-21 17:21:05 +0200)
# System: Sony Corporation VGN-A197VP(GB) (laptop)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801DB ICH4
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: Radeon i2c bit bus DVI_DDC (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: Radeon i2c bit bus VGA_DDC (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: Radeon i2c hw bus MM_I2C (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x0b
Probing for `Smart Battery'...                              Success!
    (confidence 5, driver `sbs')
Client found at address 0x18
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM64'...                No
Probing for `SMSC EMC1403'...                               No
Probing for `SMSC EMC1404'...                               No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x19
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM95231'...             No
Probing for `National Semiconductor LM95241'...             No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x1a
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x1b
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x1c
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x1d
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x1e
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x1f
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x28
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x29
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x2a
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments TMP421'...                   No
Probing for `National Semiconductor LM95231'...             No
Probing for `National Semiconductor LM95241'...             No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC EMC1403'...                               No
Probing for `SMSC EMC1404'...                               No
Client found at address 0x2b
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `National Semiconductor LM95231'...             No
Probing for `National Semiconductor LM95241'...             No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x2c
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85'...                No
Probing for `National Semiconductor LM96000 or PC8374L'...  No
Probing for `Analog Devices ADM1027'...                     No
Probing for `Analog Devices ADT7460 or ADT7463'...          No
Probing for `SMSC EMC6D100 or EMC6D101'...                  No
Probing for `SMSC EMC6D102'...                              No
Probing for `SMSC EMC6D103'...                              No
Probing for `Winbond WPCD377I'...                           No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Analog Devices ADT7490'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `Analog Devices ADM1024'...                     No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83791D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Nuvoton W83795G/ADG'...                        No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Genesys Logic GL518SM'...                      No
Probing for `Genesys Logic GL520SM'...                      No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Philips NE1619'...                             No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `ITE IT8712F'...                                No
Probing for `ALi M5879'...                                  No
Probing for `SMSC LPC47M15x/192/292/997'...                 No
Probing for `SMSC DME1737'...                               No
Probing for `SMSC SCH5027D-NW'...                           No
Probing for `Winbond W83791SD'...                           No
Client found at address 0x2d
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85'...                No
Probing for `National Semiconductor LM96000 or PC8374L'...  No
Probing for `Analog Devices ADM1027'...                     No
Probing for `Analog Devices ADT7460 or ADT7463'...          No
Probing for `SMSC EMC6D100 or EMC6D101'...                  No
Probing for `SMSC EMC6D102'...                              No
Probing for `SMSC EMC6D103'...                              No
Probing for `Winbond WPCD377I'...                           No
Probing for `Analog Devices ADT7473'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Analog Devices ADT7490'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `Analog Devices ADM1024'...                     No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83783S'...                            No
Probing for `Winbond W83791D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Nuvoton W83795G/ADG'...                        No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L784R/AR/G'...                      No
Probing for `Winbond W83L785R/G'...                         No
Probing for `Genesys Logic GL518SM'...                      No
Probing for `Genesys Logic GL520SM'...                      No
Probing for `Genesys Logic GL525SM'...                      No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Philips NE1619'...                             No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `VIA VT1211 (I2C)'...                           No
Probing for `ITE IT8712F'...                                No
Probing for `ALi M5879'...                                  No
Probing for `SMSC LPC47M15x/192/292/997'...                 No
Probing for `SMSC DME1737'...                               No
Probing for `SMSC SCH5027D-NW'...                           No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Winbond W83791SD'...                           No
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85'...                No
Probing for `National Semiconductor LM96000 or PC8374L'...  No
Probing for `Analog Devices ADM1027'...                     No
Probing for `Analog Devices ADT7460 or ADT7463'...          No
Probing for `SMSC EMC6D100 or EMC6D101'...                  No
Probing for `SMSC EMC6D102'...                              No
Probing for `SMSC EMC6D103'...                              No
Probing for `Winbond WPCD377I'...                           No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     No
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Analog Devices ADT7490'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `Analog Devices ADM1024'...                     No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83791D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Nuvoton W83795G/ADG'...                        No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `Texas Instruments THMC51'...                   No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC DME1737'...                               No
Probing for `SMSC SCH5027D-NW'...                           No
Probing for `SMSC EMC2103'...                               No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Winbond W83791SD'...                           No
Client found at address 0x2f
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83791D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Nuvoton W83795G/ADG'...                        No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `Fintek custom power control IC'...             No
Probing for `Winbond W83791SD'...                           No
Client found at address 0x48
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x49
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7481'...                     No
Client found at address 0x4c
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Analog Devices ADT7466'...                     No
Probing for `Andigilog aSC7511'...                          No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `National Semiconductor LM90'...                No
Probing for `National Semiconductor LM89/LM99'...           No
Probing for `National Semiconductor LM86'...                No
Probing for `Analog Devices ADM1032'...                     No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6657/MAX6658/MAX6659'...              No
Probing for `Maxim MAX6648/MAX6649/MAX6692'...              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Winbond W83L771W/G'...                         No
Probing for `Winbond W83L771AWG/ASG'...                     No
Probing for `Texas Instruments TMP401'...                   No
Probing for `Texas Instruments TMP411'...                   No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP422'...                   No
Probing for `Texas Instruments TMP423'...                   No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM63'...                No
Probing for `Fintek F75363SG'...                            No
Probing for `National Semiconductor LM73'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7461'...                     No
Probing for `Analog Devices ADT7481'...                     No
Probing for `Fintek F75383S/M'...                           No
Probing for `SMSC EMC1403'...                               No
Probing for `SMSC EMC1404'...                               No
Client found at address 0x4d
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `National Semiconductor LM89/LM99'...           No
Probing for `Analog Devices ADM1032'...                     No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6659'...                              No
Probing for `Maxim MAX6646'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments TMP411'...                   No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP422'...                   No
Probing for `Texas Instruments TMP423'...                   No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM73'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7461'...                     No
Probing for `Fintek F75384S/M'...                           No
Probing for `SMSC EMC1403'...                               No
Probing for `SMSC EMC1404'...                               No
Client found at address 0x4e
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6659'...                              No
Probing for `Maxim MAX6647'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments TMP411'...                   No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP422'...                   No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM64'...                No
Probing for `National Semiconductor LM73'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Fintek F75121R/F75122R/RG (VID+GPIO)'...       No
Probing for `Fintek F75111R/RG/N (GPIO)'...                 No
Probing for `ITE IT8201R/IT8203R/IT8206R/IT8266R'...        No
Client found at address 0x4f
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP422'...                   No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x58
Probing for `Analog Devices ADT7462'...                     No
Probing for `Andigilog aSC7512'...                          No
Client found at address 0x5c
Probing for `Analog Devices ADT7462'...                     No
Client found at address 0x73
Probing for `FSC Poseidon I'...                             No
Probing for `FSC Poseidon II'...                            No
Probing for `FSC Scylla'...                                 No
Probing for `FSC Hermes'...                                 No
Probing for `FSC Heimdal'...                                No
Probing for `FSC Heracles'...                               No
Probing for `FSC Hades'...                                  No
Probing for `FSC Syleus'...                                 No
Client found at address 0x77
Probing for `Asus Mozart-2'...                              No

Next adapter: Radeon i2c bit bus MONID (i2c-3)
Do you want to scan it? (YES/no/selectively): y

Next adapter: SMBus I801 adapter at 0540 (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `sbs':
  * Bus `Radeon i2c hw bus MM_I2C'
    Busdriver `UNKNOWN', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)

Warning: the required module sbs is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

so now what I've been googling trying various things but no luck. I really want to get to the bottom of this. I know the laptop is old but 11.04 has given it another lease of life, is there anyway I can get the fans under control??

thanks in advance for replying with any suggestions.

---

### Post by Lamukra on 2011-10-01
Same trouble and I have no luck with that yet

---

