---
title: "How can I access GPIO with physical address?"
date: 2016-11-23
forum: Hardware
---

### Post by danielwuboy on 2016-11-23
[COLOR=#242729][FONT=Arial]I have a requirement that is accessing GPIO with ubuntu 14.04LTS.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Below information is my device information:[/FONT][/COLOR]

[LIST]
[*]OS:Ubuntu 14.04 LTS 64bits
[*]CPU:Intel® Celeron(R) CPU J1900 @ 1.99GHz × 4
[/LIST]
[COLOR=#242729][FONT=Arial]And bleow link is datasheet and driver code[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][code and datasheet here.]("https://mega.nz/#F!XgolnSaC!1VAqlEkcIa95YsjE6x_xfA")[/FONT][/COLOR]
[HR][/HR][COLOR=#242729][FONT=Arial]First I checked the ich chip is it8785, and GPIO port is 32 to 39. PIN of port GPIO 32 is 117, so I type the command:[/FONT][/COLOR][INDENT]```
echo 32 > /sys/class/gpio/export
```[/INDENT]
[COLOR=#242729][FONT=Arial]and[/FONT][/COLOR][INDENT]```
echo 117 > /sys/class/gpio/export
```[/INDENT]
[COLOR=#242729][FONT=Arial]but both show the error "bash - echo: write error: invalid argument"[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I don't have any idea for this, so I contect with manufacturer.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]They told me that if i want access GPIO, I must direct access CPU address like :
[/FONT][/COLOR][HR][/HR]GPIO PORT   Adderss
32          0xfed0e388
33          0xfed0e368
34          0xfed0e318
35          0xfed0e378
36          0xfed0e308
37          0xfed0e398
38          0xfed0e328
39          0xfed0e3A8

[HR][/HR][COLOR=#242729][FONT=Arial]I googled for a while, quantity of data are rarly. It's thanksful for any advice.[/FONT][/COLOR]

---

