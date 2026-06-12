---
title: "Need kdialog options"
date: 2008-11-23
forum: General Help
---

### Post by vk_rams on 2008-11-23
Hi 

I want to write a shell script that using kdialog which sends a mail....
I need some help regarding file chooser in kdialog. And i am wondering when we input any thin kdialog --inputbox, where the input message can be stored is this stored in $? or some other

Please any body help on this....

~Vikram

---

### Post by vk_rams on 2008-11-23
Hey i got the answer for this. Only i need how can we get the value from kdialog --getopenfilename ~/Desktop

When we run the above command in terminal i am able to select some file and clicked on open. On the terminal it was displaying the full path of the selected path

I want to retrieve that file path in shell script. I tried below following line

myfilepath = kdialog --getopenfilename ~/Desktop

when i run this in shell script, it was showing command unknown

Please any body help on this?

~Vikram

---

### Post by vk_rams on 2008-11-23
I am writing this code in shell script file

file='kdialog --getopenfilename ~/Desktop'
$file

this opens the dialog box, after selecting that, i will get the following output

kbuildsycoca running...
ScimInputContextPlugin()
**/home/vikramt/first**
invalid length 24902
Failed to process 45 bytes from server
invalid length 24902
invalid length 24902
invalid length 24902
~ScimInputContextPlugin()

I need to get slected file path /home/vikramt/first in to some varialble say $filepath

Please please help on this.

---

