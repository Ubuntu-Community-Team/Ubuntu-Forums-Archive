---
title: "Editing files via FTP"
date: 2005-11-06
forum: General Help
---

### Post by DjKritical on 2005-11-06
Heya,

I have FTP access to my development webserver... 

All I wanna do is edit my php files (plain text) over ftp..

I've found a few options but I'm stuck.. I'm very open to suggestions at this stage

**(Option 1) FTPFS AKA LUFS**

Mounting the FTP locally sounds great! I've installed the lufs-utils package but I get an error saying the kernal module wasn't loaded?.. Anyone know how to load the LUFS kernal module?

**(Option 2) EMACS**

Apparently this 20th century looking text editor can do the job.. just a couple of minor problems with this program,

1:  It's not user friendly
2:  It's very text based

Does anyone have an option 3 or 4?...

Or can anyone point me in the right direction for LUFS or EMACS?...

I'd be eternally greatful :mrgreen: 

(There is no way I would ever go back to windows Ubuntu rawks)

---

### Post by bryan986 on 2005-11-06
Just use nautilus to access your ftp

---

### Post by nightfly on 2005-11-06
You can use nautilus to access FTP resources, no additional packages are needed for this.

Click on Places from the top menu, click on 'Connect to Server'
You will see a dialog box. 
Choose 'FTP (with login)' as the Service type.
Type in the domain of your server in the Server field.
The other fields are optional and can be left blank (default values will be used) i suggest you put in atleast the username and a name for your connection.

Click on 'Connect'. 
After that, an icon for your connection will appear on your desktop pertaining to your new connection. It will stay there until you unmount it.

To access the ftp resource simply double click that icon. Nautilus will prompt for your password. Once the ftp connection is mounted, you can access the files on that resource, copy, move, drag and drop the files as if they were local files on your desktop.

---

### Post by DjKritical on 2005-11-06
Hmm I hadn't really considered that option

Thanks!

:D

---

### Post by nightfly on 2005-11-06
i forgot to mention that you might not be able to edit PHP files on the server directly. This is due to gedit.

 In this case you will have to copy the files to somewhere and edit and then upload back (by dragging them onto their location).

---

### Post by DjKritical on 2005-11-06
Hmm is there any way to directly edit them on the server?... that's what I'm really trying to do... I have lots of files which need small adjustments..

Open
Edit
Save

Instead of

Drag
Open
Edit
Save
Drag

---

### Post by NiN on 2005-11-06
try out screem.

It's a nice web editor with gnome-vfs support...

---

### Post by endersshadow on 2005-11-06
I use gFTP and I love it.

```
sudo apt-get install gftp
```

:-D

---

### Post by DjKritical on 2005-11-06
I use gftp aswell.. I didn't think you could edit files using gftp?

---

### Post by bryan986 on 2005-11-06
[QUOTE=DjKritical]I use gftp aswell.. I didn't think you could edit files using gftp?[/QUOTE]

In FTP->Options enter gedit for the editor box, then right click on any file and choose edit

---

### Post by auburn on 2005-11-11
wow. I didn't know you could edit in gftp either, bryan. I'll try that. Generally I use nvu for editing and publishing online.

---

