---
title: "Disk attached to router missing files.Disco conectado a router faltan archivos"
date: 2017-07-21
forum: Hardware
---

### Post by padaenriqueidey on 2017-07-21
Hello. You see, I have done the following. I connected an external hard drive to my Comtrend AR-5315u router and did not see all the files and folders it contains. If I connect it to my pc with ubuntu 14.04 you will see all the folders and files. To get into the disk when connected to the router I go to Files-Connect with a server-examine-comtrend-usb1_1, and from there I can do whatever I want with the files and folders that are seen, which are not all. Also say that I entered the router and I put a password to access the disk from the browser and could only see the files and folders, in this case if that was everything. What do I have to do to see everything and do what I want when I go through Files-Connect to a server-examine-comtrend-usb1_1?
Greetings.
Thank you.

[COLOR=#212121][FONT=arial]Hello. You see, I have done the

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Hola, buenas. Vereís he hecho lo siguiente. He conectado un disco duro externo a mi router Comtrend AR-5315u y no se ven todos los archivos y carpetas que contiene. Si lo conecto a mi pc con ubuntu 14.04 se ven todas las carpetas y archivos. Para entrar en el disco cuando está conectado al router voy a Archivos-Conectarse con un servidor-examinar-comtrend-usb1_1, y a partir de ahí puedo hacer lo que quiera con los archivos y carpetas que se ven, que no son todos y todas. También decir que entré en el router y le puse una contraseña para acceder al disco desde el navegador y solo podía ver los archivos y carpetas, en este caso si que estaba todo. ¿Qué he de hacer para verlo todo y hacer lo que quiera al entrar por Archivos-Conectarse con un servidor-examinar-comtrend-usb1_1?[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Saludos.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Gracias.[/FONT][/COLOR]

---

### Post by johndough2 on 2017-07-22
Hi

The thing that comes to mind is that Ubuntu is fully mounting, and handling all the partition types and files.  EG: NTFS, ext4 and reiserfs etc.  

The router, and I assume you do actually mean the router directly, may have different access permissions or capabilities.

I am unsure about the arrangement as my router has no facility to have a Hard Disk plugged into it. It is a switch with 4 ethernet ports and a router out to my ISP.  It does not have a USB to accept HDD caddies.

So am I misunderstanding something??

---

### Post by efflandt on 2017-07-23
Is there documentation anywhere that lists specific details about capabilities of your router's USB port. All I could find so far was a data sheet that says it includes "USB 2.0 Host" port. What file systems and formatting are on the drive and are the files shown or not based on partition type, or specific file types that are shown or not.

My Motorola DSL gateway (wireless/router/modem) has a USB port that was not supported until a more recent firmware update. Not sure what file systems it supports for USB storage, but it does not do file sharing on the network. The only way I can store or retrieve files on it so far (tested with FAT32 memory stick) is to log into the router with a web browser to upload/download files using the web browser.

---

### Post by padaenriqueidey on 2017-07-23
Hello. The solution is that the external hard drive connected to the router has the ntfs file system.
Greetings.

---

