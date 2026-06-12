---
title: "No sensors were detected - Ubuntu 18.04.2 LTS"
date: 2019-05-26
forum: Hardware
---

### Post by shahafz on 2019-05-26
Hello, recently I started work with Ubuntu.
Today I tried to check my hardware temp, and I'm facing with this problem.. 
I did everything correctly - 
Thanks for help. 

[B]- sudo apt install lm-sensors

-- sudo sensors-detect

```
[/B][FONT=Verdana]sudo sensors-detect# sensors-detect revision 6284 (2015-05-31 14:00:33 +0200)[/FONT]
[FONT=Verdana]# System: Gigabyte Technology Co., Ltd. AB350M-D3H [Default string][/FONT]
[FONT=Verdana]# Board: Gigabyte Technology Co., Ltd. AB350M-D3H-CF[/FONT]
[FONT=Verdana]# Kernel: 4.18.0-20-generic x86_64[/FONT]
[FONT=Verdana]# Processor: AMD Ryzen 5 1600 Six-Core Processor (23/1/1)[/FONT]


[FONT=Verdana]This program will help you determine which kernel modules you need[/FONT]
[FONT=Verdana]to load to use lm_sensors most effectively. It is generally safe[/FONT]
[FONT=Verdana]and recommended to accept the default answers to all questions,[/FONT]
[FONT=Verdana]unless you know what you're doing.[/FONT]


[FONT=Verdana]Some south bridges, CPUs or memory controllers contain embedded sensors.[/FONT]
[FONT=Verdana]Do you want to scan for them? This is totally safe. (YES/no): yes[/FONT]
[FONT=Verdana]Silicon Integrated Systems SIS5595... No[/FONT]
[FONT=Verdana]VIA VT82C686 Integrated Sensors... No[/FONT]
[FONT=Verdana]VIA VT8231 Integrated Sensors... No[/FONT]
[FONT=Verdana]AMD K8 thermal sensors... No[/FONT]
[FONT=Verdana]AMD Family 10h thermal sensors... No[/FONT]
[FONT=Verdana]AMD Family 11h thermal sensors... No[/FONT]
[FONT=Verdana]AMD Family 12h and 14h thermal sensors... No[/FONT]
[FONT=Verdana]AMD Family 15h thermal sensors... No[/FONT]
[FONT=Verdana]AMD Family 16h thermal sensors... No[/FONT]
[FONT=Verdana]AMD Family 15h power sensors... No[/FONT]
[FONT=Verdana]AMD Family 16h power sensors... No[/FONT]
[FONT=Verdana]Intel digital thermal sensor... No[/FONT]
[FONT=Verdana]Intel AMB FB-DIMM thermal sensor... No[/FONT]
[FONT=Verdana]Intel 5500/5520/X58 thermal sensor... No[/FONT]
[FONT=Verdana]VIA C7 thermal sensor... No[/FONT]
[FONT=Verdana]VIA Nano thermal sensor... No[/FONT]


[FONT=Verdana]Some Super I/O chips contain embedded sensors. We have to write to[/FONT]
[FONT=Verdana]standard I/O ports to probe them. This is usually safe.[/FONT]
[FONT=Verdana]Do you want to scan for Super I/O sensors? (YES/no): y[/FONT]
[FONT=Verdana]Probing for Super-I/O at 0x2e/0x2f[/FONT]
[FONT=Verdana]Trying family `National Semiconductor/ITE'... No[/FONT]
[FONT=Verdana]Trying family `SMSC'... No[/FONT]
[FONT=Verdana]Trying family `VIA/Winbond/Nuvoton/Fintek'... No[/FONT]
[FONT=Verdana]Trying family `ITE'... Yes[/FONT]
[FONT=Verdana]Found unknown chip with ID 0x8686[/FONT]
[FONT=Verdana]Probing for Super-I/O at 0x4e/0x4f[/FONT]
[FONT=Verdana]Trying family `National Semiconductor/ITE'... No[/FONT]
[FONT=Verdana]Trying family `SMSC'... No[/FONT]
[FONT=Verdana]Trying family `VIA/Winbond/Nuvoton/Fintek'... No[/FONT]
[FONT=Verdana]Trying family `ITE'... Yes[/FONT]
[FONT=Verdana]Found unknown chip with ID 0x8733[/FONT]


[FONT=Verdana]Some systems (mainly servers) implement IPMI, a set of common interfaces[/FONT]
[FONT=Verdana]through which system health data may be retrieved, amongst other things.[/FONT]
[FONT=Verdana]We first try to get the information from SMBIOS. If we don't find it[/FONT]
[FONT=Verdana]there, we have to read from arbitrary I/O ports to probe for such[/FONT]
[FONT=Verdana]interfaces. This is normally safe. Do you want to scan for IPMI[/FONT]
[FONT=Verdana]interfaces? (YES/no): y[/FONT]
[FONT=Verdana]Probing for `IPMI BMC KCS' at 0xca0... No[/FONT]
[FONT=Verdana]Probing for `IPMI BMC SMIC' at 0xca8... No[/FONT]


[FONT=Verdana]Some hardware monitoring chips are accessible through the ISA I/O ports.[/FONT]
[FONT=Verdana]We have to write to arbitrary I/O ports to probe them. This is usually[/FONT]
[FONT=Verdana]safe though. Yes, you do have ISA I/O ports even if you do not have any[/FONT]
[FONT=Verdana]ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y[/FONT]
[FONT=Verdana]Probing for `National Semiconductor LM78' at 0x290... No[/FONT]
[FONT=Verdana]Probing for `National Semiconductor LM79' at 0x290... No[/FONT]
[FONT=Verdana]Probing for `Winbond W83781D' at 0x290... No[/FONT]
[FONT=Verdana]Probing for `Winbond W83782D' at 0x290... No[/FONT]


[FONT=Verdana]Lastly, we can probe the I2C/SMBus adapters for connected hardware[/FONT]
[FONT=Verdana]monitoring devices. This is the most risky part, and while it works[/FONT]
[FONT=Verdana]reasonably well on most systems, it has been reported to cause trouble[/FONT]
[FONT=Verdana]on some systems.[/FONT]
[FONT=Verdana]Do you want to probe the I2C/SMBus adapters now? (YES/no): y[/FONT]
[FONT=Verdana]Found unknown SMBus adapter 1022:790b at 0000:00:14.0.[/FONT]
[FONT=Verdana]Sorry, no supported PCI bus adapters found.[/FONT]


[FONT=Verdana]Next adapter: SMBus PIIX4 adapter port 0 at 0b00 (i2c-0)[/FONT]
[FONT=Verdana]Do you want to scan it? (YES/no/selectively): y[/FONT]
[FONT=Verdana]Client found at address 0x4f[/FONT]
[FONT=Verdana]Probing for `National Semiconductor LM75'... No[/FONT]
[FONT=Verdana]Probing for `National Semiconductor LM75A'... No[/FONT]
[FONT=Verdana]Probing for `Dallas Semiconductor DS75'... No[/FONT]
[FONT=Verdana]Probing for `Maxim MAX6642'... No[/FONT]
[FONT=Verdana]Probing for `Texas Instruments TMP421'... No[/FONT]
[FONT=Verdana]Probing for `Texas Instruments TMP422'... No[/FONT]
[FONT=Verdana]Probing for `Texas Instruments TMP435'... No[/FONT]
[FONT=Verdana]Probing for `Texas Instruments TMP441'... No[/FONT]
[FONT=Verdana]Probing for `Maxim MAX6633/MAX6634/MAX6635'... yNo[/FONT]
[FONT=Verdana]Probing for `NXP/Philips SA56004'... No[/FONT]
[FONT=Verdana]Client found at address 0x50[/FONT]
[FONT=Verdana]Probing for `Analog Devices ADM1033'... No[/FONT]
[FONT=Verdana]Probing for `Analog Devices ADM1034'... No[/FONT]
[FONT=Verdana]Probing for `SPD EEPROM'... No[/FONT]
[FONT=Verdana]Probing for `EDID EEPROM'... No[/FONT]


[FONT=Verdana]Next adapter: SMBus PIIX4 adapter port 2 at 0b00 (i2c-1)[/FONT]
[FONT=Verdana]Do you want to scan it? (YES/no/selectively): [/FONT]


[FONT=Verdana]Next adapter: SMBus PIIX4 adapter port 3 at 0b00 (i2c-2)[/FONT]
[FONT=Verdana]Do you want to scan it? (YES/no/selectively): y[/FONT]


[FONT=Verdana]Next adapter: SMBus PIIX4 adapter port 4 at 0b00 (i2c-3)[/FONT]
[FONT=Verdana]Do you want to scan it? (YES/no/selectively): y[/FONT]


[FONT=Verdana]Next adapter: NVIDIA i2c adapter 1 at 7:00.0 (i2c-4)[/FONT]
[FONT=Verdana]Do you want to scan it? (yes/NO/selectively): y[/FONT]


[FONT=Verdana]Next adapter: NVIDIA i2c adapter 2 at 7:00.0 (i2c-5)[/FONT]
[FONT=Verdana]Do you want to scan it? (yes/NO/selectively): y[/FONT]


[FONT=Verdana]Next adapter: NVIDIA i2c adapter 4 at 7:00.0 (i2c-6)[/FONT]
[FONT=Verdana]Do you want to scan it? (yes/NO/selectively): y[/FONT]
[FONT=Verdana]Client found at address 0x49[/FONT]
[FONT=Verdana]Probing for `National Semiconductor LM75'... No[/FONT]
[FONT=Verdana]Probing for `National Semiconductor LM75A'... No[/FONT]
[FONT=Verdana]Probing for `Dallas Semiconductor DS75'... No[/FONT]
[FONT=Verdana]Probing for `National Semiconductor LM77'... No[/FONT]
[FONT=Verdana]Probing for `Analog Devices ADT7410/ADT7420'... No[/FONT]
[FONT=Verdana]Probing for `Maxim MAX6642'... No[/FONT]
[FONT=Verdana]Probing for `Texas Instruments TMP435'... No[/FONT]
[FONT=Verdana]Probing for `National Semiconductor LM73'... No[/FONT]
[FONT=Verdana]Probing for `National Semiconductor LM92'... No[/FONT]
[FONT=Verdana]Probing for `National Semiconductor LM76'... No[/FONT]
[FONT=Verdana]Probing for `Maxim MAX6633/MAX6634/MAX6635'... No[/FONT]
[FONT=Verdana]Probing for `NXP/Philips SA56004'... No[/FONT]
[FONT=Verdana]Probing for `SMSC EMC1023'... No[/FONT]
[FONT=Verdana]Probing for `SMSC EMC1043'... No[/FONT]
[FONT=Verdana]Probing for `SMSC EMC1053'... No[/FONT]
[FONT=Verdana]Probing for `SMSC EMC1063'... No[/FONT]


[FONT=Verdana]Next adapter: NVIDIA i2c adapter 6 at 7:00.0 (i2c-7)[/FONT]
[FONT=Verdana]Do you want to scan it? (yes/NO/selectively): y[/FONT]


[FONT=Verdana]Next adapter: NVIDIA i2c adapter 7 at 7:00.0 (i2c-8)[/FONT]
[FONT=Verdana]Do you want to scan it? (yes/NO/selectively): y[/FONT]


[FONT=Verdana]Next adapter: NVIDIA i2c adapter 8 at 7:00.0 (i2c-9)[/FONT]
[FONT=Verdana]Do you want to scan it? (yes/NO/selectively): y[/FONT]


[FONT=Verdana]Next adapter: NVIDIA i2c adapter 9 at 7:00.0 (i2c-10)[/FONT]
[FONT=Verdana]Do you want to scan it? (yes/NO/selectively): y[/FONT]


[FONT=Verdana]Sorry, no sensors were detected.[/FONT]
[FONT=Verdana]Either your system has no sensors, or they are not supported, or[/FONT]
[FONT=Verdana]they are connected to an I2C or SMBus adapter that is not[/FONT]
[FONT=Verdana]supported. If you find out what chips are on your board, check[/FONT]
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)[FONT=Verdana] for driver status.[/FONT]
[B]
```
[/B]

---

### Post by CatKiller on 2019-05-26
From a quick search on your motherboard model number, it seems that it uses [this sensor chip](https://www.phoronix.com/scan.php?page=news_item&px=IT87-Linux-Driver-Axing).

---

