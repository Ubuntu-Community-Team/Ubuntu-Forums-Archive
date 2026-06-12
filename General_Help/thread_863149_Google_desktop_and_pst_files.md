---
title: "Google desktop and pst files"
date: 2008-07-18
forum: General Help
---

### Post by swarrick on 2008-07-18
I've recently switched over to Ubuntu from Windows and have found the whole transition very easy.

Having said that, I am now missing a few key things that I had before under windows. Most importantly I no longer have instant access to my old email which was stored in outlook .pst files.

Under windows Google Desktop indexed .pst files so that I could use the superb search to find old emails going back in some cases ten years. The email appears as a page in the browser and clicking the address allows me to reply via GMail. 

Sadly under Ubuntu, Google Desktop seems unable to index my old pst files.

Indexing only takes place while outlook is open I believe under windows.

Does anyone know if it can be fooled into doing this under Ubuntu?

---

### Post by adam_kimber on 2008-07-18
From a little bit of reading the PST file email storage format is not easily openable by any Linux application. There are ways to convert them to a format that is compatible with Linux but these are fairly arkward and many require access to a windows box.

---

### Post by zingalala on 2008-12-10
I beg to differ but there is a pure Linux based tool that can convert .pst files (Both Outlook 2003 or older). This libpst or readpst port is one of (at least) three trunks of libpst project. Original trunk was at sourceforge, another truck is at kmail and this one is maintained at following site:
[http://www.five-ten-sg.com/libpst/](http://www.five-ten-sg.com/libpst/)

First two trunks of libpst only supports 32-bit pst files i.e. pre Outlook 2003. This trunk supports both pre and post Outlook 2003 formats i.e 32-bit or 64-bit.

The output format is mbox (Berkley mailbox) which is widely supported by most Linux e-mail clients. The command is simple to use.
readpast -r <pst file>

Optionally you can split each message in a separate file.

You will need to build libpst manually under Ubuntu though from source code.

---

### Post by bab1 on 2008-12-10
Or this web app:[http://labs.brotherli.ch/vcfconvert/]("http://labs.brotherli.ch/vcfconvert/")

---

