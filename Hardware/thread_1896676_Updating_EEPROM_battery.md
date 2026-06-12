---
title: "Updating EEPROM battery"
date: 2011-12-17
forum: Hardware
---

### Post by andradx on 2011-12-17
Hi! I have an LG E500, whose battery was at 63% of capacity (100% 4800mAh), so I decided to had it replaced. So I purchased six 4200mAh cells instead of 2400mAh cells, cracked open the battery, replaced the cells, checked the voltage and cell-to-cell connection, assembled the battery again and inserted into the battery socket.

Needless to say, it did not work, as the EEPROM holds data regarding the capacity of the battery regarding the last charge and the design charge. Those values need to be zeroed and updated. I've browsed the web for tools for that purpose and came across some commercial tools that are $150~200 dollars (I can get a nine cell battery for less than that), but not a free tool. From the information I gathered, there's two ways to do it.

1. Get some software that writes to EEPROMS or work my way with I2C until I get the results, which may well compromise other EEPROMS (that I have no knowledge of) in my computer. Some read commands map to write commands in different EEPROMS.

2. Take the battery chip and connect it to an EEPROM system, which is available at work, but I don't know how to do it or what to do with it.


If anyone has experience in handling battery EEPROM rewrite, any help given would be most appreciated.

Regards.

---

### Post by andradx on 2011-12-21
Let me please rephrase the previous post. It didn't work because as the case was shut one of the connectors broke itself. Its welded now and up and running.

However, since the last full charge was at a mere 34Wh of the original 55Wh, now my 6 cell 4200mAh will only charge to 34Wh.


Any help? Please?

---

### Post by postadelmaga on 2012-06-09
Not easy to manage battery EEPROM reset.
It depends of many factor and involves reverse engine the EEPROM data.

To read data you need to open the battery, remove the EEPROM and read it with apposite hardware device ( you could use also arduino :)
But at this point you will have to to undestand the data and correct it ... probably would be a good idea dump the data when the battery is new and the use this data when it loose capacity. 

This is problem is part of our "capitalist" system:
factory want to produce produce and sell sell, this is how our economy works, so they produce stuff with this kind of tricks ...

p.s.
If you open the battery and remove the eeprom you can manually charge the battery ...
another 'solution' is to remove the cell and use it for other purpose as e-bicicle

---

