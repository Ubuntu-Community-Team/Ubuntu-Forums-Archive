---
title: "WINE issues on ubuntu 7.10"
date: 2008-07-19
forum: General Help
---

### Post by marconicotera on 2008-07-19
As per title i installed WINE on ubuntu 7.10 it seem fine but when i try to run an .exe file for installing a windows prog  it gives me that error:

"ducsetup.exe" cannot be opened
no application suitable for automatic installation
is available for handling this kind of file.

the same prog is opened on ubuntu 8.04 but i don't want to upgrade to 8.04.

Any idea ??????

---

### Post by Taxman415a on 2008-07-19
If I recall correctly 7.10 just doesn't integrate Wine as well as 8.04 does. From the error you're getting I'm assuming you're trying to double click on the file. Instead try right clicking on it and open with wine. If that doesn't work, open a terminal, navigate to where the file you want to run with wine is located and type 
```
wine ducsetup.exe
```

---

