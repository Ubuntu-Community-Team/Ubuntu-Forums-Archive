---
title: "how to delete bad installations in wine?"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by rock it on 2009-09-06
Hi,
Could anyone tell me if there is a way of manually deleting installed programs in wine. I installed steam but various things went wrong and to make a long story short some stuff got messed up. I tried reinstalling it and its not working. Is there a way of manually deleting program files on wine. Also is there a way of manually deleting files on xubuntu aswell beacause that could come in handy aswell?

thanks in advance.

---

### Post by makariolewis on 2009-09-06
If you need to completely wipe wine, all you have to do is delete your ~/.wine folder to start over. As far as manually removing individual programs, the best thing you can do is try to search ~/.wine for an uninstall file for whatever program you wish to uninstall.

---

### Post by joelgsf on 2009-09-06
Under "Applications" menu item you shall find the "Wine" item, which opens to several sub-menu itens, one of which is "Uninstall Wine software", which, in turn, allows you to remove whatever you may have installed (if registered by Windows).

---

### Post by steele64e on 2009-09-06
If you need to delete the program manually you can do so by going into your home directory, looking for the .wine folder (must have veiw hidden folders enabled) , then inside will be a folder called Drive-C or something. Just go into the program folder and delete the unwanted program's folder. Hope I helped:)

---

