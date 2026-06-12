---
title: "Sane works only with sudo"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2006-02-11
Hi, I hope somebody can help me:

My mother has an Brother MFC-8420 printer/copier/scanner. The printer works fine, now I want to get the scanner working. I installed the "brscan" backend from the Brother homepage, now the scanner is detected. It just spits out an I/O error. When I run scanimage on the console with sudo, the scanner works flawlessly, but the regular user seems to have no access to the scanner. Can somebody tell me how this permission problem can be solved?

Tom

---

### Post by Robgould on 2006-02-11
You need to change the file premissions.
 
sudo chmod 777 /your/file/path
 
 will give all users full rights to the file.
 
If you want to give all the rights recursively to all files in a folder
 
sudo chmod -R 777 /your/folder/path
 
hope this helps.

---

### Post by el3ktro on 2006-02-11
Hi,
thanks for this, but it's not that I don't have access to a file, I can't access the scanner. Seems to be some USB permission problem - and there's no device in /dev for the scanner, so I don't know where to go from here ...

Tom

---

### Post by Robgould on 2006-02-11
Sorry for the confusion.

---

