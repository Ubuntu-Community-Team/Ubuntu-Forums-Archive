---
title: "Export kmail contacts to blackberry bold"
date: 2009-03-08
forum: Hardware
---

### Post by walter_j on 2009-03-08
I'm trying to export my kmail contacts to blackberry bold and am at a dead end. I tried barrybackup, but get a error 1 - unexpected response and crash. I've given up trying to sync with the barry and will use xp to transfer data. Wine won't run the blackberry desktop manager - it crashes at the very first install screen.

I exported kmail contacts to CSV and tried to import into Outlook, but Outlook ignores the CSV. I tried export contacts to a vcard file from Evolution but outlook ignores that too.

Imcidentally, while trying to install opensync evolution plugin, I get an error in dependency kcal2b - uninstallable. I suppose it doesn't matter since the blackberry bold doesn't play nice with linux.

Is there a way to transfer my kmail contacts to the BB Bold?

---

### Post by walter_j on 2009-03-09
I found a way to import kmail contacts into outlook.

1. export kmail contacts as csv
2. import csv file into excel
3. shorten field names (dbase 3 limits field names to 12 characters)
4. Make sure each column is wide enough to fit everything in the column (drag the column until everything fits in the column). dbase fields are fixed length, so if you don't make it wide enough, it cuts off text wider than the field.
5. save as dbf. dos uses 8 characters in file name + 2 character extension
6. import into outlook. map fields of dbf to the outlook fields

I will sync outlook contacts with blackberry next (i hope).

---

