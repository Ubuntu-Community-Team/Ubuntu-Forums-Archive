---
title: "does anyone know what the chip manufacturer of my ram chips is"
date: 2023-07-16
forum: Hardware
---

### Post by bjlockie on 2023-07-16
Does anyone know what the chip manufacturer of my ram chips is

[HTML]$ sudo dmidecode --type memory
Module Manufacturer ID: Bank 5, Hex 0xCD[/HTML]

---

### Post by mIk3_08 on 2023-07-17
Does the brand doesn't manufacture their own RAM chips? Like for example: Kingstone, It says every chip is kingstone. I just saw it in my memory module. Every chip is mark with the brand name. 
And as I run the command its say in the "Part Number" is the brand name. 
Regards and cheers.

---

### Post by Autodave on 2023-07-17
Why are you trying to find out this info?  Have you looked on the chip(s) itself?

---

### Post by TheFu on 2023-07-17
When I use dmidecode, I see about 30 lines of output for each memory stick installed.  Some of the lines say this:
```
        Manufacturer: **G Skill Intl**
        Serial Number: 00000000
        Asset Tag: Not Specified
        Part Number: **F4-3200C16-16GVK**
        Rank: 2
        Configured Memory Speed: **3200 MT/s**
```

Which tells me the speed, model number and vendor.  Lacking that, you'll need to physically look at the chips and possibly use a magnifying glass to read them.  If they aren't clearly marked, I'd suspect low quality probably made in China by a 3rd tier fabricator.  Reputable chip makers proudly stamp their part numbers.

BTW, my G.Skill RAM has this line too:
```
Module Manufacturer ID: Bank 5, Hex 0xCD
```
 but the other lines nearby are all "unknown".

I have 2 sticks (2 x 8GB) on my desk and the heat sinks all cover the actual RAM chips, so I can't see that part number.

---

