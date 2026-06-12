---
title: "how to upload via ftp"
date: 2005-11-26
forum: General Help
---

### Post by missmoondog on 2005-11-26
i've installed a couple different ftp apps and i've been able to download the stuff from my website to have them locally stored on the computer. how the heck do i upload using any of these programs though? there is no split window, like i'm used to for drag and drop. double clicking a file just opnes it up in the browser. all i see is the regular files within the folder. help!!

thank you

---

### Post by nagilum on 2005-11-26
Would've been helpful if you mentioned any of the program names or asked for a specific one. Anyhow, you can use Nautilus to upload to FTP sites. On your Desktop go to 'Places->Connect to Server...' and select 'FTP (with login)'. Specify the host, your username and password and Nautilus will connect to that site, letting you browse (and modify) it like a local folder.

---

### Post by m0biu5 on 2005-11-26
I've found that is the best way to upload. I really wish there were a good ftp program with a gui. =/

---

### Post by hav0x on 2005-11-26
gFTP?

---

### Post by missmoondog on 2005-11-27
Oops! Yes, gFTP is the one I'm trying at the moment.

---

### Post by missmoondog on 2005-11-27
[QUOTE=nagilum]Would've been helpful if you mentioned any of the program names or asked for a specific one. Anyhow, you can use Nautilus to upload to FTP sites. On your Desktop go to 'Places->Connect to Server...' and select 'FTP (with login)'. Specify the host, your username and password and Nautilus will connect to that site, letting you browse (and modify) it like a local folder.[/QUOTE]

I've been able to figure out that much, as far as editing and connecting, but where/how do I actually do the upload?

---

### Post by nagilum on 2005-11-27
The browser window opened behaves like any other, you can use copy/paste or drag+drop to copy files to or from this window.

---

### Post by missmoondog on 2005-11-27
i don't follow you. i know the browser window opens and behaves like any other, but how/where do i copy/paste or drag/drop, to get the images/text/etc up to my server on my isp? there isn't 2 seperate window panes to drag anything into. such as when using a windows based ftp like cuteftp, ws_ftp, or aceftp.

---

### Post by nagilum on 2005-11-27
Of course you have to open a second window and browse your local files in it...

---

### Post by Bachstelze on 2005-11-27
Yep, it's like copying your files on a floppy disk, but it will go on the FTP.

---

### Post by m0biu5 on 2005-11-27
I wonder if Wine would work out with those windows ftp clients; you should be able to google it.

---

### Post by missmoondog on 2005-11-27
dang, that was to simple. worked like a charm. 

thanks y'all!!

---

### Post by aysiu on 2005-11-27
[QUOTE=m0biu5]I wonder if Wine would work out with those windows ftp clients; you should be able to google it.[/QUOTE] I know Filezilla works with Wine.

---

### Post by hav0x on 2005-11-28
FTP and nautilus dont mix here.
After i close the window and do the unmount thingie on the desktop the connection remains [ESTABLISHEH] for quite a while and then gos to [CLOSE_WAIT] *ad eternum*. Tried it with both a public FTP and a standard user/pwd one. same thing one both.
It just dont feel safe. :???:

---

### Post by missmoondog on 2005-11-29
now this is weird. on 2 other machines i've done this ftp thing on, they have a side window open where i can just go from folder to folder within that window. this machine, i have to open 2 seperate windows, file browser and ftp. how come this ubuntu can't ever behave the same way twice in a row hardly? :???:

---

